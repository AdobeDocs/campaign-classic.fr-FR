---
solution: Campaign Classic
product: campaign
title: Protocole et paramètres du connecteur SMS
description: En savoir plus sur le connecteur SMS et comment le configurer.
audience: delivery
content-type: reference
topic-tags: configuring-channels
translation-type: tm+mt
source-git-commit: 8f45fcc57062e6f13bc674c72f53788483de93fb
workflow-type: tm+mt
source-wordcount: '8399'
ht-degree: 1%

---

# Protocole et paramètres du connecteur SMS {#sms-connector-protocol}

>[!NOTE]
>
>Dans ce document, toutes les références au protocole, aux noms de champs et aux valeurs se rapportent à la [spécification SMPP 3.4](https://smpp.org/SMPP_v3_4_Issue1_2.pdf).

## Présentation {#overview}

Les SMS peuvent se limiter à envoyer des SMS courts sans mise en forme, mais leur simplicité en fait un canal de communication précieux.

Il existe deux façons principales d&#39;envoyer un SMS :

* Envoyez-le manuellement à partir d&#39;un téléphone, la façon habituelle de communiquer directement entre les gens.
* Envoyez-le depuis Internet, la façon dont Adobe Campaign envoie des messages. Pour cela, vous avez besoin d&#39;un prestataire SMS qui connecte Internet au réseau mobile.
Adobe Campaign utilise le protocole SMPP pour envoyer des SMS à un prestataire.

Ce document vous guidera dans la connexion établie entre Adobe Campaign et un fournisseur SMPP.

Les fournisseurs SMPP peuvent parfois dévier des spécifications officielles, mais le connecteur SMS en Adobe Campaign offre de nombreuses options pour adapter son comportement pour qu&#39;il soit compatible avec la plupart des fournisseurs.

>[!IMPORTANT]
>
>La configuration d&#39;une connexion à un nouveau fournisseur peut nécessiter des compétences techniques, des connaissances en TCP, binaire, représentation hexadécimale et encodages de texte. Il faudra également une principale coopération avec le fournisseur.

### Types de SMS {#sms-types}

Lorsque vous envoyez des SMS de masse par l&#39;intermédiaire d&#39;un fournisseur de SMS, vous rencontrerez trois types de SMS différents :

* **SMS MT (Mobile arrêté)** : un SMS émis par Adobe Campaign vers les téléphones portables par l&#39;intermédiaire du fournisseur SMPP.

* **SMS MO (Mobile Originaire)** : un SMS envoyé par un téléphone mobile à Adobe Campaign par l&#39;intermédiaire du fournisseur SMPP.

* **SGS SR (Status Report) ou DR ou DLR (Diffusion Receive)** : un reçu de retour envoyé par le téléphone mobile à Adobe Campaign par l&#39;intermédiaire du fournisseur SMPP indiquant que le SMS a été reçu avec succès. Adobe Campaign peut également recevoir des SR indiquant que le message n&#39;a pas pu être remis, souvent avec une description de l&#39;erreur.

Vous devez faire la distinction entre les accusés de réception (PDU REEE, partie du protocole SMPP) et SR : SR est un type de SMS qui est envoyé par le réseau de bout en bout, alors qu&#39;un accusé de réception n&#39;est qu&#39;une confirmation qu&#39;un transfert a réussi.

Les accusés de réception et les demandes de service peuvent déclencher des erreurs, la distinction entre les deux facilitera le dépannage.

### Information portée par un SMS {#information-sms}

Un SMS contient plus d&#39;informations que du texte. Voici une liste de ce que vous pouvez vous attendre à trouver dans un SMS :

* Le texte, qui est limité à 140 octets, ce qui signifie entre 70 et 160 caractères selon le codage. Voir [Encodage du texte SMS](../../delivery/using/sms-protocol.md#sms-text-encoding) ci-dessous pour plus de détails et pour connaître les limites.

* Adresse du destinataire, parfois appelée `ADC` ou `MSISDN`. C&#39;est le numéro du mobile qui recevra le SMS.

* Adresse de l&#39;expéditeur, qui peut être appelée `oADC` ou parfois `sender id`. Il peut s&#39;agir d&#39;un numéro de téléphone utilisé au quotidien, d&#39;un code court envoyé par l&#39;intermédiaire d&#39;un fournisseur ou d&#39;un nom. Le nom est une fonction facultative, dans ce cas vous ne pouvez pas répondre au SMS.

* Indicateur qui indique si le message est un message Flash. Un message Flash est une fenêtre contextuelle qui n&#39;est pas stockée en mémoire.

* Indicateur indiquant si une SR est attendue ou non.

* Date de validité, après laquelle aucun équipement réseau n&#39;est autorisé à réessayer.

* Champ `data_coding` qui indique le codage du texte.

## Protocole SMPP {#smpp-protocol}

Adobe Campaign Classic prend en charge le protocole SMPP version 3.4. Il s&#39;agit d&#39;un protocole étendu qui permet d&#39;envoyer des SMS à un fournisseur (SMSC) et de recevoir des SMS ainsi que des reçus. Pour plus d&#39;informations à ce sujet, consultez la [documentation SMPP](https://smpp.org/SMPP_v3_4_Issue1_2.pdf).

L&#39;équipement réseau côté prestataire SMS est souvent appelé SMSC.

### Connexions SMPP {#smpp-connections}

Adobe Campaign se connecte à l&#39;équipement réseau du prestataire SMS via TCP. Le protocole SMPP définit des connexions TCP permanentes d&#39;Adobe Campaign au fournisseur. Les connexions TCP sont toujours initiées par Adobe Campaign, même pour recevoir des messages.
SMPP ouvre 1 ou 2 connexions TCP, selon son mode. Toutes les connexions sont toujours initiées par Adobe Campaign.

Le protocole SMPP peut fonctionner en deux modes :

* **Transmitter+récepteur (ou TX+RX)** : deux connexions TCP distinctes sont utilisées pour la transmission et la réception de messages.
* **Transcepteur (ou TRX)** : une connexion TCP unique est utilisée pour transmettre et recevoir des messages.

>[!NOTE]
>
> Adobe Campaign Classic ne prend en charge que le mode TX+RX. Cette limitation est due à son architecture technique.

### PDU SMPP {#smpp-pdu}

Les unités de transmission SMPP (&quot;paquets&quot;) sont appelées PDUs. Une PDU **PDU** contient une commande, un état, un numéro de séquence et des données.

Chaque unité d&#39;alimentation doit être reconnue par une `SMPP RESP PDU` (réponse synchrone). Les demandes peuvent être acheminées : l&#39;expéditeur peut envoyer de nombreuses commandes sans attendre `RESP`, le nombre de requêtes pouvant être pipeliné à tout moment est appelé la fenêtre. `RESP PDU` peut arriver dans n&#39;importe quel ordre, sans rapport avec l&#39;ordre de leur PDU initiateur correspondant.

Dans le mode séparé **Transmetteur+récepteur**, la connexion utilisée dépend du type de message transmis. La connexion de l&#39;émetteur est utilisée pour MT, et la connexion du récepteur est utilisée pour MO et SR. Les requêtes et réponses pour chaque type de message sont envoyées via la même connexion TCP.

Par exemple, lors de l’envoi d’un MT, la connexion de l’émetteur est utilisée et le `RESP` qui reconnaît le MT est également envoyé par l’intermédiaire du canal de l’émetteur. Lorsque vous recevez un MO (ou un SR), la connexion du récepteur est utilisée pour recevoir le MO et pour envoyer le `RESP` qui reconnaît le MO.

![](assets/sms_protocol_1.png)

Dans Adobe Campaign Classic, pour lier SR à leur MT correspondante, un identifiant est renvoyé par le SMSC avec les étapes `SUBMIT_SM_RESP` et `DELIVER_SM`. L&#39;identifiant est stocké dans le champ `providerId` de la table `nms::providerMsgId` et est lié à `broadLogId` et `deliveryId`. Cette opération de correspondance est effectuée par le processus SMS lors de l&#39;écriture dans la base de données.

Une `SUBMIT_SM_RESP PDU` réussite déclenche l’état du message &quot;envoyé&quot; dans le journal d’envoi tandis qu’une `DELIVER_SM (SR) PDU` réussie déclenche l’état du message &quot;reçu&quot;.

### Aspects liés à la sécurité {#security-aspects}

Le protocole lui-même n&#39;est pas chiffré. La plupart des fournisseurs implémentent une variante d’IP sur la liste autorisée, de sorte que les adresses IP du serveur Adobe Campaign doivent être déclarées au fournisseur.

Adobe Campaign prend en charge la transmission d’un identifiant et d’un mot de passe lors de la phase de liaison. Il soutient également le SMPP plutôt que le TLS. Il convient de noter que des certificats sont requis pour assurer une sécurité adéquate. Bien que le connecteur SMPP permette de contourner les contrôles de certificats, il ne doit être utilisé que pour les tests, car TLS sans certificat offre un niveau de sécurité nettement inférieur.

Le connecteur utilise les certificats par défaut fournis par la bibliothèque système `openssl`. En général, il est fourni par le répertoire `/etc/ssl/certs` sur Debian. Ce répertoire est fourni par le package &quot;ca-certificates&quot; par défaut, mais il peut être personnalisé.

### Informations sur chaque type d&#39;unité d&#39;alimentation {#information-pdu}

Chaque type de PDU possède des champs distincts qui contiennent des éléments d&#39;information différents. Ces PDU sont détaillées dans la [spécification SMPP 3.4](https://smpp.org/SMPP_v3_4_Issue1_2.pdf).

Chaque section ci-dessous décrit la PDU et sa réponse synchrone (`*_RESP PDU`). Toutes les unités d&#39;alimentation doivent être reconnues par un `RESP` correspondant, c&#39;est une partie obligatoire de la spécification.

Les PDU peuvent comporter des champs facultatifs. Seuls les champs les plus courants sont décrits ici. Pour plus d&#39;informations, consultez la [spécification SMPP 3.4](https://smpp.org/SMPP_v3_4_Issue1_2.pdf).

**BIND_TRANSMITTER / BIND_RECEIVER / BIND_TRANSCEIVER**

Cette PDU est utilisée pour initier une connexion à la SMSC. **Les modes de transmission**, de  **** réception et de  **** transfert ne modifient que le type de SMS autorisé à être transféré sur ce lien, en particulier :

| Mode | Types de SMS autorisés |
|:-:|:-:|
| Émetteur | MT |
| Destinataire | MO + SR |
| Transceiver | MT + MO + SR |

Champs visibles dans un `BIND_* PDU` :

* **system_id** : Connexion utilisée pour l&#39;authentification. Défini dans le compte externe.

* **password** : Mot de passe utilisé pour l’authentification. Défini dans le compte externe.

* **system_type** : Obligatoire pour certains fournisseurs. Défini dans le compte externe, disponible dans toutes les versions. Souvent, il fait la distinction entre différents types de contrats, canaux, pays, etc.

* **addr_** tonand  **addr_npi** : Requis par certains fournisseurs. Défini par les paramètres `Bind TON` et `Bind NPI` dans le compte externe.

* **address_range** : Requis par certains fournisseurs. La plupart du temps, il s&#39;agit d&#39;une liste de codes à raccourcis autorisés sur cette connexion. Défini dans le compte externe.

`BIND_*_RESP` n’a pas de champ spécifique, il confirme si la connexion a réussi ou non.

#### UNBIND {#unbind}

Cette PDU doit être envoyée par le système avant de se déconnecter. Il doit attendre la PDU `UNBIND_RESP` correspondante avant de fermer la connexion.

La conformité SMSC ne doit pas fermer la connexion, la connexion TCP est contrôlée par le connecteur Adobe Campaign.

#### SUBMIT_SM {#submit-sm}

Cette PDU envoie un MT à la SMSC. Sa réponse PDU donne l&#39;ID du MT.

Champs visibles dans une PDU `SUBMIT_SM` :

* **service_type** : requis par certains fournisseurs. Défini dans les propriétés de la diffusion.

* **source_addr_** tonand  **source_addr_npi** : indique le type d&#39;adresse source transmise. La signification de ces champs est normalisée, mais comme certains fournisseurs les utilisent différemment, vous devriez demander au fournisseur sa valeur correcte. Défini dans le compte externe.

* **source_addr** : l&#39;adresse source / oADC du MT. Il sera affiché sur le téléphone mobile. Définie dans le compte externe et la diffusion, la valeur de la diffusion prévaut sur la valeur du compte externe.

* **dest_addr_** tonand  **dest_addr_npi** : indique le type d&#39;adresse de destination transmise (format local ou international, par exemple). La signification de ces champs est normalisée, mais comme certains fournisseurs les utilisent différemment, vous devriez demander au fournisseur sa valeur correcte. Défini dans le compte externe.

* **destination_addr** : adresse du destinataire, numéro de téléphone ou MSISDN.

* **esm_class** : permet de déterminer si UDH est utilisé ou non dans le champ de texte. Activé automatiquement par le connecteur pour scinder SMS si le mode `message_payload` n&#39;est pas utilisé.

* **priority_flag** : priorité de ce message sur les autres. Cela est lié à la priorité de la diffusion elle-même.

* **valid_period** : horodatage après lequel aucune nouvelle tentative ne doit être effectuée. Défini dans la diffusion elle-même.

* **registered_diffusion** : indique si un SR est demandé ou non. Adobe Campaign définit toujours cet indicateur, à l’exception des réponses automatiques. Pour les messages en plusieurs parties, l&#39;indicateur n&#39;est défini que pour la première partie. Toutes les versions ont le même comportement.

* **data_coding** : indique le codage utilisé dans le champ de texte. Voir la section [Encodage du texte SMS](../../delivery/using/sms-protocol.md#sms-text-encoding) pour plus d&#39;informations.

* **short_message** : texte du message. Si UDH est utilisé, il contient également l’en-tête UHD.

Adobe Campaign prend en charge les champs facultatifs suivants :

* **dest_addr_subunit** : utilisé pour spécifier la cible du SMS : flash, mobile ou carte SIM. Défini dans les propriétés de la diffusion.

* **message_payload** : lorsqu&#39;il est activé dans le compte externe, de longs messages sont envoyés dans une seule unité de distribution de données et le texte est transmis dans ce champ plutôt que dans le  `short_message` champ.

#### SUBMIT_SM_RESP {#submit-sm-resp}

Cette PDU contiendra l&#39;ID du MT. Ceci est utile pour établir une correspondance avec la SR entrante.

>[!IMPORTANT]
>
>De nombreux fournisseurs transmettent l&#39;ID MT au format hexadécimal. Assurez-vous de définir correctement le format **ID dans l’accusé de réception MT** dans le compte externe.

Certains fournisseurs envoient `SUBMIT_SM_RESP` après l&#39;envoi de la SR. Pour tenir compte de ce comportement, Adobe Campaign attend 30 secondes avant de répondre **ID de message non valide** à un SR avec un ID inconnu.

#### DELIVER_SM {#delivery-sm}

Cette PDU est envoyée par la SMSC à Adobe Campaign. Il contient un MO ou une SR.

La plupart des champs ont la même signification que leur contrepartie `SUBMIT_SM`. Voici la liste des champs utiles :

* **source_addr** : adresse source du MO/SR. Il s&#39;agit généralement d&#39;un numéro de téléphone.

* **destination_addr** : code court qui a reçu l’MO ou la SR.

* **esm_class** : était utilisé pour déterminer si la PDU est un MO ou un SR.

* **short_message** : texte du message. Pour la SR, il s&#39;agit des données décrites à l&#39;appendice B de la spécification du protocole SMPP. Voir [Gestion des erreurs SR](../../delivery/using/sms-protocol.md#sr-error-management) pour plus de détails.

Adobe Campaign peut lire l&#39;ID de message dans le champ facultatif `receipted_message_id` avec une configuration particulière.

#### DELIVER_SM_RESP {#deliver-sm-resp}

Cette PDU est envoyée par Adobe Campaign pour reconnaître SR et MO.

Adobe Campaign Classic reconnaît SR et MO une fois qu&#39;ils ont été insérés dans la base de données. Certaines erreurs de traitement peuvent se produire même si une PDU `DELIVER_SM_RESP` réussie a été envoyée. Cette limitation est due à l&#39;architecture logicielle de Adobe Campaign Classic.

#### ENQUIRE_LINK {#enquire-links}

Cette PDU n&#39;est utilisée que pour vérifier que la connexion est active. Sa fréquence doit être définie en fonction des besoins du fournisseur.

Les 60 secondes par défaut doivent correspondre à la plupart des configurations définies dans le compte externe.

#### ENQUIRE_LINK_RESP {#enquire-links-resp}

Cette PDU reconnaît que la connexion est vivante.

### SGS en plusieurs parties (SGS long) {#multipart}

Les SMS en plusieurs parties, ou les SMS longs, sont des SMS envoyés en plusieurs parties. En raison des limitations techniques du protocole de réseau mobile, un SMS ne peut pas dépasser 140 octets ou doit être fractionné. Consultez la section [Encodage du texte SMS](../../delivery/using/sms-protocol.md#sms-text-encoding) pour en savoir plus sur le nombre de caractères pouvant tenir dans un SMS.

Chaque partie d&#39;un long message est un SMS individuel. Ces pièces se déplacent indépendamment sur le réseau et sont assemblées par le téléphone mobile récepteur. Pour gérer les Reprises et les problèmes de connectivité, Adobe Campaign envoie ces pièces dans l&#39;ordre inverse et ne demande une SR que sur la première partie du message, la dernière envoyée. Puisque le téléphone portable n&#39;affiche un message que lors de la réception de sa première partie, les Reprises sur d&#39;autres parties ne produisent pas de duplicata sur le téléphone portable.

Le nombre maximal de SMS par message peut être défini par diffusion à l&#39;aide du paramètre **Nombre maximal de SMS par message** dans le **Modèle de diffusion**. Les messages qui dépassent cette limite échouent lors de l&#39;envoi d&#39;un SMS avec un motif d&#39;échec trop long.

Il y a deux façons d&#39;envoyer des SMS longs :

* **UDH** : la méthode par défaut et recommandée pour envoyer des messages longs. Dans ce mode, le connecteur divise le message en plusieurs `SUBMIT_SM PDU`s avec les informations UDH. Ce protocole est celui utilisé par les téléphones portables eux-mêmes. Cela signifie que Adobe Campaign a le plus grand contrôle sur la génération de messages, ce qui lui permet de calculer exactement combien de pièces ont été envoyées et comment elles ont été fractionnées.

* **message_payload** : la façon d&#39;envoyer tout le long message en un seul  `SUBMIT_SM PDU`. Le fournisseur devra le fractionner, ce qui signifie qu&#39;il est impossible pour Adobe Campaign de savoir exactement combien de pièces ont été envoyées. Certains fournisseurs exigent ce mode, mais nous vous conseillons de ne l&#39;utiliser que s&#39;ils ne prennent pas en charge l&#39;UDH.

Voir la description des champs `esm_class`, `short_message` et `message_payload` de la PDU [SUBMIT_SM](../../delivery/using/sms-protocol.md#information-pdu) pour plus d&#39;informations sur le protocole et les formats.

### plafonnement du débit et fenêtrage {#throughput-capping}

La plupart des fournisseurs exigent une limite de débit pour chaque connexion SMPP. Pour ce faire, il est possible d&#39;établir un certain nombre de SGS dans le compte externe. Notez que le ralentissement du débit se produit par connexion, le débit effectif total est la limite par connexion multipliée par le nombre total de connexions. Ceci est détaillé dans la section [Connexions simultanées](../../delivery/using/sms-protocol.md#connection-settings).

Pour atteindre le débit maximal possible, vous devez affiner la fenêtre d&#39;envoi maximale. La fenêtre d&#39;envoi est le nombre de `SUBMIT_SM PDU`s qui peuvent être envoyées sans attendre un `SUBMIT_SM_RESP`. Pour plus d&#39;informations, consultez la section [Paramètres de la fenêtre d&#39;envoi](../../delivery/using/sms-protocol.md#throughput-timeouts).

### Gestion des SR et des erreurs (&quot;Annexe B&quot;) {#sr-error-management}

Le protocole SMPP définit des erreurs synchrones standard dans `RESP PDU`s, mais il ne définit pas de codes d&#39;erreur pour SR. Chaque fournisseur utilise ses propres codes d’erreur avec leur signification.

Une recommandation est faite dans la section de l&#39;annexe B de la [spécification du protocole SMPP](https://smpp.org/SMPP_v3_4_Issue1_2.pdf) (page 167), mais cela ne liste pas les codes d&#39;erreur réels ni leur signification.

Pour s&#39;adapter à la gestion des erreurs, le système de messagerie à large log d&#39;Adobe Campaign a été exploité pour fournir correctement les erreurs et leur sévérité (hard, soft, etc.).

Comme mentionné ci-dessus, il existe deux types d&#39;erreurs :

* réponses synchrones dans le `SUBMIT_SM_RESP` qui surviennent immédiatement après l’envoi du message à la SMSC
* reçus qui peuvent s’afficher beaucoup plus tard lorsque le mobile a reçu le message ou lorsque le message a expiré. Dans ce cas, l&#39;erreur se trouve dans une SR.

Lorsqu&#39;une SR est reçue, l&#39;état et l&#39;erreur se trouvent dans son champ `short_message` (exemple pour les mises en oeuvre conformes à l&#39;annexe B). Le champ `short_message` de l&#39;unité d&#39;alimentation est souvent appelé le champ **texte**, car il contient du texte en MT. En cas de SR, il contient des informations techniques ainsi qu&#39;un sous-champ nommé **Texte**. Ces deux champs sont différents et `short_message` contient en fait le champ **Texte** et d&#39;autres informations.

Les connecteurs Adobe Campaign Classic (à l’exception de l’option SMPP étendu) utilisent un comportement codé en dur qui dépend du fournisseur sélectionné. Le SMPP générique ne fait que distinguer la réussite de l&#39;erreur, sans aucun détail. Le journal des diffusions peut contenir certaines informations qui ne sont pas garanties.

#### Format de champ de texte SR {#sr-text-field-format}

La spécification recommande d&#39;utiliser ce format pour le champ de texte SR. Il s’agit d’une liste de sous-champs séparés par des espaces et dotés de deux points pour séparer le nom du champ et sa valeur. Les noms de champ ne sont pas sensibles à la casse.

Exemple d’un champ de texte SR correspondant à la recommandation Annexe B :

```
id:1234567890 sub:001 dlvrd:001 submit date:1608011415 done date:1608011417 stat:DELIVRD err:000 Text:Hello Adobe world
```

Le champ id correspond à l’ID reçu dans `SUBMIT_SM_RESP PDU`, c’est-à-dire la reconnaissance de la valeur MT.

`sub` et  `dlvrd` sont censés compter la quantité de pièces livrées et de messages livrés, mais ceci n&#39;est pas utilisé par Adobe Campaign puisque le système de publication à grande vitesse donne une information meilleure et plus intégrée.

`submit date` et  `done date` les champs sont des horodatages indicatifs du moment où le MT a été envoyé et du moment où le SR a été envoyé par le mobile. Vous pouvez vous attendre à des problèmes de fuseaux horaires ou même à des horodatages incorrects donnés par les mobiles avec un jeu de dates incorrect.

Le champ stat est important car il indique l’état du message. Le seul état important est `DELIVRD`, `UNDELIV` et `REJECTD`. L&#39;état `DELIVRD` indique une réussite, les deux autres indiquent une erreur. D&#39;autres valeurs sont possibles, mais il s&#39;agit généralement de notifications intermédiaires, par exemple le MT a atteint l&#39;opérateur de téléphonie mobile, mais pas le téléphone mobile. Ces notifications intermédiaires sont ignorées par Adobe Campaign.

Le champ d’erreur contient le code d’erreur propre au fournisseur. Le fournisseur doit fournir un tableau des codes d&#39;erreur possibles ainsi que leur signification pour pouvoir interpréter cette valeur.

Enfin, le champ de texte contient généralement le début du texte du MT. Adobe Campaign n&#39;en tient pas compte et certains fournisseurs ne le transmettent pas pour éviter les fuites d&#39;informations d&#39;identification personnelle et la consommation de bande passante du réseau. Il peut être utilisé lors du dépannage pour repérer plus facilement la SR correspondant à un test MT en lisant ce champ.

### Exemple de traitement SR dans Adobe Campaign Classic Extended générique SMPP {#sr-processing}

Cet exemple montre comment afficher le cas d&#39;une mise en oeuvre suivant la recommandation Annexe B, les valeurs par défaut dans le compte externe et un SMS MT réussi.

```
id:1234567890 sub:001 dlvrd:001 submit date:1608011415 done date:1608011417 stat:DELIVRD err:000 Text:Hello Adobe world
```

Tout d’abord, l’expression régex `id extraction` est appliquée pour extraire l’identifiant et le rapprocher avec le MT correspondant.

Ensuite, les champs `status extraction` regex et `error code extraction` regex sont appliqués pour extraire ces champs et sont ajoutés à la chaîne.

Le message du journal large est créé à l’aide de ces informations et la chaîne d’origine non modifiée est ajoutée à titre de référence :

```
SR ExampleProvider DELIVRD 000|MESSAGE=id:1234567890 sub:001 dlvrd:001 submit date:1608011415 done date:1608011417 stat:DELIVRD err:000 Text:Hello Adobe world
```

Le message est alors normalisé, supprimant la partie MESSAGE pour pouvoir faire correspondre plusieurs messages avec le même état et le même code d&#39;erreur.

```
SR ExampleProvider DELIVRD 000|#MESSAGE#
```

Si le message n&#39;est pas déjà configuré dans le tableau des messages à grande diffusion, une nouvelle entrée est créée, en utilisant le message entier comme **firstText** et le message normalisé. Ensuite, le connecteur utilise les variables success et `error` regex pour déterminer s’il s’agissait d’une réussite ou d’un échec :

* S&#39;il correspond à l&#39;regex `success`, il sera considéré comme une réussite.

* S’il correspond à l’expression regex `error`, le message est qualifié d’erreur.

* Si aucune de ces deux correspondances regex ne correspond, la SR est ignorée. Il peut s’agir d’une notification intermédiaire, qui n’est pas gérée par Adobe Campaign.

Par défaut, toutes les erreurs sont configurées en tant qu’erreurs logicielles. Cela signifie que les erreurs dures doivent être corrigées à la main.

### Encodage du texte SMS {#sms-text-encoding}

**toujours contacter le fournisseur SMSC en cas de problèmes de codage**. Seuls les fournisseurs SMSC ont une connaissance du codage qu&#39;ils prennent en charge et des règles spéciales qui peuvent s&#39;appliquer en raison de limitations de leur plateforme technique.

Les messages SMS utilisent un encodage spécial de 7 bits, souvent appelé encodage GSM7.

Dans le protocole SMPP, le texte GSM7 sera étendu à 8 bits par caractère pour faciliter le dépannage. La SMSC le compresse en 7 bits par caractère avant de l&#39;envoyer au mobile. Cela signifie que le champ `short_message` du SMS peut comporter jusqu&#39;à 160 octets dans le cadre SMPP, alors qu&#39;il est limité à 140 octets lorsqu&#39;il est envoyé sur le réseau mobile.

En cas de problème de codage, voici quelques éléments importants à vérifier :

* Assurez-vous de connaître les caractères qui font partie de l’encodage. GSM7 ne prend pas entièrement en charge les marques ou accents diacritiques. Surtout en français, où é et è font partie de GSM7, mais ê, â ou ï ne le sont pas. Il en va de même pour l&#39;espagnol.

* Le C avec cédille (ç) n&#39;est présent que dans les majuscules de l&#39;alphabet GSM7, mais certains téléphones le rendent en minuscules ou en minuscules. La recommandation générale est d&#39;éviter complètement la cédille ou de passer à l&#39;UCS-2.

* **N&#39;utilisez pas ASCII dans** SMS, sauf si le fournisseur SMSC le demande explicitement. Ce codage réduit l’espace car il comporte des caractères 8 bits et une couverture inférieure à celle de GSM7. Ce codage peut être requis pour les réseaux CDMA utilisés en Amérique du Nord.

* Latin-1 n’est pas toujours pris en charge. Vérifiez la compatibilité avec votre fournisseur SMSC avant de tenter d’utiliser Latin-1.

* Les tables de changement de langue nationales ne sont pas prises en charge par le connecteur Adobe Campaign. Vous devez utiliser UCS-2 ou autre `data_coding` à la place.

* UCS-2 et UTF-16 sont souvent mélangés par téléphone. Ceci est un problème lors de l’utilisation d’émoticônes et d’autres caractères non présents dans UCS-2.

* La plupart des téléphones ne contiennent pas de glyphes de police pour tous les caractères UCS-2. Les smartphones ont tendance à être en mesure d&#39;afficher des caractères rares assez facilement, mais les téléphones de fonction ont généralement un support limité à ce qui est utile dans la langue maternelle du pays dans lequel ils ont été achetés. Si vous voulez utiliser emoji ou ASCII-art, testez-le sur un large éventail de téléphones avant de l&#39;envoyer. La prévisualisation Adobe Campaign ne simule pas les glyphes manquants et affiche les symboles disponibles dans le navigateur Web.

Le champ `data_coding` indique le codage utilisé. Un problème majeur est que la valeur 0 signifie le codage SMSC par défaut dans la spécification, qui fait généralement référence à GSM7. Vérifiez auprès du partenaire SMSC quel encodage est associé à `data_coding` = 0 que Adobe Campaign ne prend en charge que. D&#39;autres valeurs `data_coding` tendent à suivre la spécification, mais la seule façon de s&#39;assurer est de vérifier auprès du fournisseur SMSC.

La taille maximale d’un message dépend de son codage. Ce tableau récapitule toutes les informations pertinentes :

| Encodage | Data_coding usuel | Taille du message (caractères) | Taille de partie pour SMS multipartie | Caractères disponibles |
|:-:|:-:|:-:|:-:|:-:|
| GSM 7 | 0 | 160 | 152 | Jeu de caractères de base GSM7 + extension (les caractères étendus prennent 2 caractères) |
| Latin-1 | 3 | 140 | 134 | ISO-8859-1 |
| UCS-2 <br>UTF-16 | 8 | 70 | 67 | Unicode (varie d’un téléphone à l’autre) |

## Paramètres de compte externe SMPP {#SMPP-parameters-external}

Chaque mise en oeuvre du protocole SMPP comporte de nombreuses variantes. Pour améliorer la compatibilité et l&#39;adaptabilité, de nombreux paramètres sont disponibles pour modifier le comportement du connecteur SMPP. Cette section décrit chaque paramètre et ses effets sur le connecteur.

### Paramètres généraux et routage {#general-parameters-routing}

**Limiter les instances MTA pour ce compte**

Il est possible de définir une limite au nombre d’instances MTA autorisées à se connecter au fournisseur SMPP. Si cette option est cochée, vous pouvez spécifier le nombre maximum d’accords multimédias à utiliser.

Cette option permet un contrôle plus précis du nombre de connexions, voir [Connexions simultanées](../../delivery/using/sms-protocol.md#connection-settings).

Si vous définissez une valeur supérieure au nombre d’ATM en cours d’exécution, toutes les ATM s’exécuteront normalement : cette option n’est qu’une limite et ne peut pas générer d’autres MTA.

Si vous devez contrôler précisément le nombre de connexions, par exemple les besoins du fournisseur, il est recommandé de toujours définir cette option même si le déploiement actuel comporte le nombre approprié de MTA en cours d’exécution. Si d&#39;autres MTA sont ajoutées par la suite, la limite de connexion reste respectée.

### Paramètres de connexion {#connection-settings}

#### Nom de l&#39;implémentation du SMSC {#smsc-implementation-name}

Définit le nom de l’implémentation SMSC. Il doit être défini sur le nom de votre fournisseur. Contactez l&#39;administrateur ou l&#39;équipe de délivrabilité pour savoir quoi ajouter dans ce champ. Le rôle de ce champ est décrit dans la section [Gestion des erreurs SR](../../delivery/using/sms-protocol.md#sr-error-management).

#### Serveur {#server}

Nom DNS ou adresse IP du serveur auquel se connecter.

#### Port {#port}

Port TCP auquel se connecter.

#### Compte {#account}

Connexion de la connexion. Transmis dans le champ `system_id` de la PDU BIND.

#### Mot de passe {#password}

Mot de passe de la connexion SMPP. Transmis dans le champ du mot de passe de la PDU BIND.

#### Type de système {#system-type}

Valeur transmise dans le champ `system_id` de la PDU BIND. Certains fournisseurs ont besoin d&#39;une valeur spécifique ici.

#### Nombre de connexions enfant MTA {#number-mta-child}

Dans Adobe Campaign Classic, il définit le nombre de connexions par enfant MTA.

Le connecteur SMPP Adobe Campaign Classic Extended peut contrôler le nombre de connexions par enfant MTA. Pour contrôler la limite globale des connexions, vous devrez limiter le nombre de processus enfant MTA, ce qui signifie souvent disposer d&#39;une plateforme de midsourcing dédiée pour les SMS.

Pour Adobe Campaign Classic, il peut y avoir un nombre différent de connexions de récepteurs et d&#39;émetteurs :

* **Connexions de l’émetteur = Nombre de connexions enfant MTA * Nombre de processus enfant MTA * Nombre de MTA (si la réponse automatique est définie) + Nombre de connexions enfant MTA**

Comme nous l&#39;avons suggéré plus haut, le processus SMS Adobe Campaign Classic ouvre plus de connexions d&#39;émetteur si la réponse automatique est activée. Ces connexions supplémentaires sont utilisées pour envoyer les réponses automatiques.

* **Connexions du destinataire = Nombre de connexions enfants MTA**

Si vous configurez des réponses automatiques, le processus SMS ouvrira des paires émetteur/récepteur, augmentant ainsi le nombre de connexions d&#39;émetteur. Si vous n&#39;avez pas configuré de réponse automatique, elle n&#39;ouvrira que les connexions de réception.

#### Activer TLS via SMPP {#enable-TLS}

Utilisez TLS pour vous connecter au fournisseur. La connexion sera cryptée. La connexion TLS est gérée par la bibliothèque OpenSSL tout ce qui est applicable à OpenSSL sera vrai pour cette connexion.

#### Activer les traces SMPP en mode verbeux dans le fichier de log {#enable-verbose-log-file}

Ce paramètre permet de vider tout le trafic SMPP dans les fichiers journaux. Il est souvent nécessaire d’ajuster les paramètres lors de la configuration initiale. Ceci doit être activé lors du dépannage du connecteur et comparé au trafic vu par le fournisseur.

Dans Adobe Campaign Classic, la sortie du journal se trouve dans le journal MTA pour le trafic lié aux MT et dans le journal SMS pour le trafic lié aux MO et SR.

### Paramètre de connexion du destinataire {#receiver-connection}

Cette section est uniquement visible en mode **émetteur+récepteur** séparé.

#### Utiliser des paramètres différents pour le récepteur {#receiver-parameters}

Lorsque la case est désactivée, les mêmes paramètres sont utilisés pour l’émetteur et le récepteur.

Lorsque la case est cochée, les paramètres de la section **Paramètres de connexion** s&#39;appliquent à l&#39;émetteur et les paramètres de la **connexion du destinataire** s&#39;appliquent au destinataire.

**Serveur du destinataire, port, compte, mot de passe, type de système**

Ces paramètres s&#39;appliquent au récepteur en mode émetteur+récepteur. Ils fonctionnent comme la partie transmetteur, voir ci-dessus pour plus de détails.

### Paramètres du canal SMPP {#smpp-channel-settings}

#### Autoriser la translitération des caractères {#allow-character-transliteration}

La translittération est le processus de recherche de caractères équivalents à ceux qui sont manquants. Par exemple, le caractère français &quot;ê&quot; (avec un accent circonflexe) est absent de l&#39;encodage GSM, mais il peut être remplacé par &quot;e&quot; sans nuire à la lisibilité.

Si cette case n’est pas cochée, le codage du texte échoue s’il ne peut pas coder la chaîne telle quelle.

Si cette case est cochée, le codage de texte tentera de convertir la chaîne en une version approximative plutôt que d’échouer. Si certains caractères n’ont pas d’équivalent en codage de cible, le codage de texte échoue.

Pour obtenir une explication plus générale du processus de codage, consultez la section [Définir un mappage spécifique du paramètre d’encodage](../../delivery/using/sms-protocol.md#SMSC-specifics).

#### Stocker les MO entrants dans la base de données {#incoming-mo-storing}

Lorsqu&#39;elle est activée, le système d&#39;exploitation entrante est stocké dans la table inSMS de la base de données. Ce tableau peut être interrogé à l’aide de l’activité requête de tout flux de travail.

Adobe Campaign Classic stocke toujours tous les MO dans la base de données inSMS afin que cette option ne soit pas disponible.

#### Activer les mises à jour des KPI en temps réel pendant le traitement du SR (rapport d&#39;état){#real-time-kpi}

Lorsqu&#39;ils sont activés, les indicateurs de performance clés sont mis à jour en temps réel sur la page de diffusion principale lors de la réception d&#39;une SR d&#39;erreur.

L&#39;inconvénient peut être de faibles performances en raison de la contention de base de données qu&#39;elle génère. Si cette option est désactivée, les statistiques sont mises à jour par le flux de travaux **syncfromexec**, qui s’exécute toutes les 20 minutes.

Adobe Campaign Classic dispose d’un mécanisme entièrement différent pour les indicateurs de performance clés. Cette option n’est donc pas disponible.

#### Numéro source {#source-number}

Définit l’adresse source par défaut des messages. Ce paramètre ne s’applique que si le numéro de la source a été laissé vide dans la diffusion.

Par défaut, le champ du numéro de source n’est pas transmis. Le fournisseur le remplace donc par le code court.

Ceci active la fonction de remplacement de l’adresse de l’expéditeur/du code ADC.

#### Numéro court {#short-code}

Indique le code court principal du compte. Si plusieurs codes courts sont utilisés pour ce compte ou si le code court est inconnu, laissez ce champ vide.

La spécification d’un code court s’avère utile pour deux fonctionnalités :

* La prévisualisation affiche le code court si aucun numéro de source n&#39;est fourni. Il reflétera le comportement réel sur les téléphones portables.

* Le paramètre de liste bloquée de la fonction de réponse automatique envoie uniquement à la quarantaine de l’utilisateur un code court spécifique.

#### Source TON/NPI, destination TON/NPI {#ton-npi}

La TON (Type de numéro) et l&#39;IVP (Indicateur de plan de numérotation) sont décrites à la section 5.2.5 de la spécification [SMPP 3.4](https://smpp.org/SMPP_v3_4_Issue1_2.pdf) (page 117). Ces valeurs doivent être définies en fonction des besoins du fournisseur.

Ils sont transmis tels quels dans les champs `source_addr_ton`, `source_addr_npi`, `dest_addr_ton` et `dest_addr_npi` de `SUBMIT_SM PDU`.

#### Service type {#service-type}

Ce champ est transmis tel quel dans le champ `service_type` de `SUBMIT_SM PDU`. Définissez cette variable en fonction des besoins du fournisseur.

### Débit et timeouts {#throughput-timeouts}

Ces paramètres contrôlent tous les aspects du timing du canal SMPP. Certains fournisseurs ont besoin d&#39;un contrôle très précis du taux de message, des délais de fenêtre et des délais de réessai. Ces paramètres doivent être définis sur des valeurs correspondant à la capacité du fournisseur et aux conditions indiquées dans le contrat.

#### Fenêtre d&#39;émission {#sending-window}

La fenêtre est le nombre de `SUBMIT_SM PDU`s qui peuvent être envoyées sans attendre une correspondance `SUBMIT_SM_RESP`.

Exemple de transmission avec une fenêtre maximale de 4 :

![](assets/sms_protocol_2.png)

La fenêtre permet d&#39;augmenter le débit lorsque la liaison réseau présente une latence élevée.  La valeur de la fenêtre doit être au moins le nombre de SMS/s multiplié par la latence du lien.
en secondes afin que le connecteur n&#39;attende jamais un `SUBMIT_SM_RESP` avant d&#39;envoyer le message suivant.
Si la fenêtre est trop grande, vous pouvez envoyer plus de messages de duplicata en cas de problème de connexion. En outre, la plupart des fournisseurs ont une limite très stricte pour la fenêtre et refusent les messages qui dépassent la limite.

Comment calculer la formule optimale de la fenêtre d&#39;envoi :

* Mesurez la latence maximale entre `SUBMIT_SM` et `SUBMIT_SM_RESP`.

* Multiplier cette valeur en secondes jusqu’au débit maximal MT. Cela donnera la valeur optimale de la fenêtre d&#39;envoi.

Exemple : Si 300 SMS/s sont définis dans le débit maximal MT et qu&#39;il y a une latence de 100 ms entre `SUBMIT_SM` et `SUBMIT_SM_RESP` en moyenne, la valeur optimale sera `300×0.1 = 30`.

#### Débit max de MT {#max-mt-throughput}

Nombre maximal de MT par seconde et par connexion. Ce paramètre est strictement appliqué, la MTA n’affichera jamais de messages plus rapidement que cette limite. Il est utile pour les fournisseurs qui nécessitent un ralentissement précis.

Pour connaître la limite de débit totale, multipliez ce nombre par le nombre total de connexions, comme indiqué dans la formule ci-dessus.

0 signifie pas de limite, la MTA enverra MT aussi vite que possible.

Il est généralement recommandé de maintenir ce paramètre en dessous de 1000, puisqu&#39;il est impossible de garantir un débit précis au-dessus de ce nombre, à moins que l&#39;architecture finale ne soit correctement comparée et que le fournisseur SMPP ait été spécifiquement demandé. Il peut être préférable d&#39;augmenter le nombre de connexions au-dessus de 1000 MT/s.

#### Temps avant reconnexion {#time-reconnection}

Lorsque la connexion TCP est perdue, le connecteur attend ce nombre de secondes avant d&#39;essayer d&#39;établir une connexion.

#### Délai d&#39;expiration des MT {#expiration-period}

Délai entre `SUBMIT_SM` et `SUBMIT_SM_RESP` correspondant. Si `RESP` n&#39;est pas reçu à temps, le message sera considéré comme ayant échoué et la stratégie de nouvelle tentative globale de l&#39;ATM s&#39;appliquera.

#### Délai d&#39;attente maximal d&#39;un bind {#bind-timeout}

Délai entre la tentative de connexion TCP et la réponse `BIND_*_RESP`. Lorsqu’elle expire, la connexion est fermée par le connecteur Adobe Campaign et il faudra attendre le temps avant de se reconnecter avant de réessayer.

#### Période d&#39;enquire_link {#enquire-link-period}

`enquire_link` est un type spécial de PDU envoyé pour maintenir la connexion en vie. Cette période est en secondes. Le connecteur de campagne n&#39;envoie `enquire_link` que lorsque la connexion est inactive pour économiser la bande passante. Si aucun REEE n&#39;est reçu après deux fois cette période, la connexion est considérée comme étant morte et un processus de reconnexion est déclenché.

### Spécificités des SMSC {#SMSC-specifics}

Ces paramètres sont des paramètres avancés qui adaptent le connecteur Adobe Campaign à la plupart des particularités d&#39;implémentation SMPP.

**Définir un mappage spécifique de codages**

Voir la section [Encodage de texte SMS](../../delivery/using/sms-protocol.md#sms-text-encoding) pour plus d’informations sur l’encodage de texte.

Ce paramètre vous permet de définir un mappage de codage personnalisé différent de la spécification. Vous pourrez déclarer une liste de codages, ainsi que leur valeur `data_coding`.

La MTA tentera de coder en utilisant le premier codage de la liste. Si elle échoue, elle essaiera d&#39;utiliser le prochain codage sur la liste, etc. Si aucun codage ne peut être utilisé pour coder le message, une erreur se produit. Une fois le codage trouvé, la MTA crée la balise `SUBMIT_SM PDU` avec le texte codé et le champ `data_coding` défini avec la valeur spécifiée dans le tableau.

L’ordre des éléments du tableau est important : les codages sont des tentatives de haut en bas. Placez le codage le moins cher ou le plus recommandé en haut de la liste, puis choisissez des encodages de plus en plus chers.

Veuillez noter que UCS-2 n&#39;échouera jamais car il peut coder tous les caractères pris en charge en Adobe Campaign et que la longueur maximale d&#39;un SMS UCS-2 est beaucoup plus petite : 70 caractères uniquement.

Vous pouvez également utiliser ce paramètre pour forcer l’utilisation d’un codage spécifique en ne déclarant que 1 ligne dans la table de mappage.

Le mappage par défaut utilisé lorsque la case à cocher n’est pas cochée est équivalent au tableau suivant :

| data_coding | Encodage |
|---|---|
| 0 | GSM |
| 9 | UCS-2 |

Cela signifie que l&#39;ATM tentera d&#39;encoder le message dans GSM. S&#39;il réussit, il l&#39;enverra avec `data_coding` défini sur 0.

Si le message ne peut pas être codé dans GSM, il sera codé dans UCS-2 et défini `data_coding` sur 8.

#### Activer message_payload {#enable-message-payload}

Lorsqu&#39;elle n&#39;est pas cochée, les SMS longs sont divisés par l&#39;ATM et envoyés dans plusieurs `SUBMIT_SM PDU`s avec l&#39;UDH. Le message sera recomposé par le téléphone mobile suivant les données UDH.

Si cette option est cochée, un SMS long est envoyé dans une PDU SUBMIT_SM, plaçant le texte dans le champ message_payload facultatif. Voir la [spécification SMPP](../../delivery/using/sms-protocol.md#ACS-SMPP-connector) pour plus d&#39;informations à ce sujet.

Si cette fonction est activée, Adobe Campaign ne pourra pas comptabiliser les parties SMS individuellement : tous les messages seront comptés comme envoyés en une seule partie.

#### Envoyez le numéro de téléphone complet {#send-full-phone-number}

Si cette case n’est pas cochée, seuls les chiffres du numéro de téléphone sont envoyés au fournisseur (`destination_addr` champ du champ `SUBMIT_SM`). Il s’agit du comportement par défaut puisque l’indicateur de nombre international, généralement un préfixe +, est remplacé par les champs TON et NPI dans SMPP.

Si cette case est cochée, le numéro de téléphone est envoyé tel quel, sans prétraitement ni espaces potentiels, + préfixe ou signes dièse/hachage/étoile.

Cette fonctionnalité a également un effet sur le comportement de la fonction de liste bloquée de réponse automatique : lorsque la case n&#39;est pas cochée, un préfixe + est ajouté aux numéros de téléphone insérés dans la table de quarantaine afin de compenser la suppression du préfixe + du numéro de téléphone par le protocole SMPP lui-même.

#### Ignorer la vérification du certificat TLS {#skip-tls}

Lorsque TLS est activé, ignorez toutes les vérifications de certificat.

Lorsqu&#39;elle est cochée, la connexion n&#39;est plus sécurisée, elle ne doit pas être activée en production.

Il peut être utile à des fins de débogage ou de test.

#### Liaison TON/NPI {#bind-ton-npi}

TON (Type de numéro) et NPI (Indicateur de plan de numérotation) décrits à la section 5.2.5 de la [spécification SMPP 3.4](https://smpp.org/SMPP_v3_4_Issue1_2.pdf) (page 117). Ces valeurs doivent être définies selon les besoins du fournisseur.

Ils sont transmis tel quel dans les champs `addr_ton` et `addr_npi` de la PDU BIND.

#### Plage d&#39;adresses {#address-range}

Envoyé tel quel dans le champ address_range de la PDU BIND. Cette valeur doit être définie selon les besoins du fournisseur.

#### Nombre d&#39;acquittements d&#39;identifiant invalides {#invalid-id}

Limite le nombre de **ID de message non valide** `DELIVER_SM_RESP` pouvant être envoyé pour une seule SR.

**Cette valeur ne doit être utilisée qu’à des fins de dépannage en tant que** solution de contournement et définie sur 0 dans des conditions normales.

Exemple Fox, lorsque vous définissez sur 2 :

* Le fournisseur envoie un SR (`DELIVER_SM`) avec l’ID &quot;1234&quot;.

* L&#39;ID &quot;1234&quot; est introuvable dans la base de données.

* Le connecteur comptabilise 1 erreur **ID non valide** pour cet ID, de sorte qu&#39;il envoie `DELIVER_SM_RESP` avec le code d&#39;erreur &quot;ID de message non valide&quot; (comportement normal).

* Le fournisseur Reprises la même SR avec l’ID &quot;1234&quot;.

* L&#39;ID &quot;1234&quot; est toujours introuvable dans la base de données.

* Le connecteur comptabilise 2 **erreur d&#39;ID** non valide pour cet ID, de sorte qu&#39;il envoie `DELIVER_SM_RESP` &quot;OK&quot;, même s&#39;il n&#39;a pas été traité correctement.

* Cette fonctionnalité est destinée à vider les tampons SR côté fournisseur lorsque des blocs SR non valides sont légitimes pour que les messages ne puissent pas être traités.

La définition de ce champ sur 0 désactive le mécanisme où **ID de message non valide** est toujours renvoyé, c&#39;est un comportement normal.

Si ce champ est défini sur 1, le connecteur répond toujours &quot;OK&quot;, même si l’ID n’est pas valide. Cette valeur doit être définie sur 1 uniquement sous supervision, pour le dépannage et pour un temps minimum, par exemple pour récupérer d’un problème côté fournisseur.

#### Regex d&#39;extraction de l&#39;ID dans le SR {#regex-extraction}

Le format SR n&#39;est pas strictement appliqué par la spécification du protocole SMPP. Il ne s&#39;agit que d&#39;une recommandation décrite à l&#39;[appendice B](../../delivery/using/sms-protocol.md#sr-error-management) (page 167) de la spécification. Certains implémenteurs de SMPP formorisent ce champ différemment, de sorte que Adobe Campaign a besoin d&#39;un moyen d&#39;extraire le champ correct.

Par défaut, il capture jusqu’à 10 caractères alphanumériques après `id:`.

L’expression regex doit comporter exactement un groupe de capture avec une partie entre parenthèses. Les parenthèses doivent entourer la partie ID. Le format regex est PCRE.

Lors de la modification de ce paramètre, veillez à inclure le plus de contexte possible pour éviter les faux déclencheurs. S’il existe des préfixes spécifiques, tels que `id:` dans la norme, incluez-les dans l’expression regex. Utilisez également autant que possible des délimiteurs de mots (\b) pour éviter de capturer du texte au milieu d’un mot.

Ne pas inclure suffisamment de contexte dans le regex peut introduire un petit défaut de sécurité : le contenu réel du message peut être inclus dans la SR. Si vous ne faites correspondre qu’un format d’ID spécifique sans contexte, par exemple un UUID, il se peut qu’il analyse le contenu du texte réel, par exemple un UUID incorporé dans le champ de texte, au lieu de l’ID.

#### Regex appliqué pour déterminer l&#39;état de réussite/d&#39;erreur {#regex-applied}

Lorsque des messages avec une combinaison de champs stat/err inconnue sont détectés, ces regex sont appliqués sur le champ stat pour déterminer si la SR a été un succès ou une erreur. Les SR avec des valeurs stat qui ne correspondent à aucun de ces index sont ignorés.

Par défaut, définissez des valeurs commençant par `DELIV`, par ex. `DELIVRD` dans l&#39;[Annexe B](../../delivery/using/sms-protocol.md#sr-error-management), sera considéré comme livré avec succès et toutes les valeurs d&#39;état qui correspondent à des erreurs, p. ex. `REJECTED`, `UNDELIV`, sont considérées comme des erreurs.

#### Format d’ID dans l’accusé de réception MT {#id-format-mt}

Indique le format de l’ID renvoyé dans le champ `message_id` de l’`SUBMIT_SM_RESP PDU`.

* **Ne pas modifier** : L’ID est stocké tel quel dans la base de données, sous la forme de texte codé en ASCII. Aucun prétraitement ni filtrage n’est effectué.

* **Nombre** décimal : L’ID doit être un nombre décimal au format ASCII. Les espaces de début et de fin et les zéros de début sont supprimés lorsque ce paramètre est utilisé.

* **Nombre** hexadécimal : L’ID doit être un nombre hexadécimal au format ASCII, sans 0 x ni h à la fin. L’ID est ensuite converti en nombre décimal avant d’être stocké dans la base de données.

* **Chaîne** hexadécimale : L’ID doit être un texte codé en ASCII qui est lui-même une chaîne d’octets codés en hexadécimal. Par exemple, dans la PDU, vous trouverez `0x34 0x31 0x34 0x32 0x34 0x33`, qui se traduit par ASCII &quot;414243&quot;. Cette chaîne est alors décodée sous la forme d’une chaîne d’octets hexadécimale et vous obtenez &quot;ABC&quot; en conséquence : vous stockerez l’ID &quot;ABC&quot; dans la base de données.

#### Format d&#39;ID dans SR {#id-format-sr}

Indique le format de l’ID capturé par l’expression `Extraction` de l’ID dans la SR. Les valeurs ont la même signification et le même comportement que le format en MT ci-dessus.

**L&#39;identifiant du SR ou le code d&#39;erreur dans un champ optionnel**

>[!NOTE]
>
>Disponible uniquement dans le connecteur SMPP étendu Adobe Campaign Classic.

Si cette case est cochée, le contenu des champs facultatifs est ajouté au texte traité par les index ci-dessus. Le texte aura le format `0xTAG:VALUE`, `0xTAG` étant la valeur hexadécimale de 4 chiffres de la balise en majuscules, par exemple. `0x002E`.

Par exemple, vous pouvez capturer l’identifiant dans le champ `receipted_message_id`. Pour cela, activez cette case à cocher et le texte suivant sera ajouté à l’état :

```
0x001E:05e3299e-8d37-49d0-97c6-8e4fe60c7739
```

Dans cet exemple, 0x001E est la balise du champ facultatif et UUID est la valeur du champ.

Pour capturer cette valeur, vous pouvez désormais définir l’expression regex suivante dans l’expression regex d’Extraction de l’identifiant dans le champ SR :

```
\b0x001E:([0-9a-f]{8}-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{12})\b
```

>[!IMPORTANT]
>
>Vous pouvez uniquement capturer les champs facultatifs contenant des valeurs de texte (ASCII/UTF-8). En particulier, les champs binaires ne peuvent pas être capturés de manière fiable avec le système regex actuel.

**Stocker l&#39;identifiant du SR ou le code d&#39;erreur dans un champ de texte**

Si cette case est cochée, le champ **Texte** est conservé pendant le traitement du texte d&#39;état de la SR.

Cela s’avère utile si le fournisseur place des données importantes dans ce champ, telles que l’ID ou l’état. En règle générale, ce champ peut être ignoré en toute sécurité puisqu’il peut contenir du texte avec un codage non ASCII et perturber le traitement regex.

L’activation de cette option peut introduire un très petit défaut de sécurité si l’expression `Extraction` de l’ID dans le champ SR n’est pas suffisamment précise. Le contenu du champ **Texte** peut être analysé en tant qu’ID et un attaquant peut l’utiliser pour injecter des identifiants falsifiés, ce qui peut entraîner un déni de service partiel.

**Balise d’ID de service**

Permet d’ajouter un fichier TLV personnalisé. Ce champ définit la partie de balise. La valeur peut être personnalisée par diffusion dans la valeur **ID de service ou de programme** dans les paramètres avancés de la diffusion.

Ce paramètre permet uniquement d’ajouter une option TLV par message.

### Réponse automatique aux MO    {#automatic-reply}

>[!IMPORTANT]
>
>Dans Adobe Campaign Classic et dans une architecture hybride, l’application de réponse automatique pour le connecteur SMPP étendu nécessite l’ajout d’un accès en écriture pour l’opérateur mid sur le dossier **Compte externe**.

Cette fonctionnalité permet de répondre rapidement au texte à l&#39;opérateur et de gérer l&#39;envoi de code par abrégé à la liste bloquée.

Les colonnes **Mot-clé** et **Code court** définissent les conditions pour déclencher la réponse automatique. Si les deux champs correspondent, le MO est envoyé et l’action supplémentaire est déclenchée. Pour spécifier un caractère générique, vous devez laisser le champ vide. Le mot-clé correspond au premier mot alphanumérique du texte MO, en ignorant la ponctuation et les espaces de début. Cela signifie que le champ **Mot-clé** ne peut pas contenir d’espaces et doit être un seul mot.

Le paramètre **Mot-clé** est un préfixe. Par exemple, si vous spécifiez &quot;AD&quot;, il correspondra à &quot;AD&quot;, &quot;ADAPT&quot; et &quot;ADOBE&quot;. Si vous avez plusieurs mots-clés avec un préfixe commun, vous devez prêter attention à la commande car les mots-clés sont traités de haut en bas.

La colonne **Réponse** est le texte à répondre. Aucune personnalisation n’est disponible dans ce champ. Si vous laissez ce champ vide, aucun message ne sera répondu, mais l’action supplémentaire sera quand même déclenchée.

La colonne **Action supplémentaire** fournit une action supplémentaire lorsque **Mot-clé** et **Code court** correspondent tous les codes courts vides. Vous pouvez envoyer à la quarantaine ou supprimer de la quarantaine, la valeur aucune réponse au texte. Si vous spécifiez une **action supplémentaire** mais que le champ **Réponse** reste vide, l&#39;action est exécutée mais aucune réponse n&#39;est envoyée. La quarantaine est appliquée uniquement pour le code court spécifié ou pour tous les codes courts si le champ est vide.

>[!IMPORTANT]
>
>Le paramètre d&#39;envoi du numéro de téléphone complet a un impact sur le comportement du mécanisme de quarantaine de réponse automatique : si l&#39;envoi du numéro de téléphone complet n&#39;est pas vérifié, le numéro de téléphone mis en quarantaine sera précédé d&#39;un signe plus (&quot;+&quot;) afin de le rendre compatible avec le format de numéro de téléphone international.

Toutes les entrées de la table sont traitées dans l’ordre spécifié, jusqu’à ce qu’une règle corresponde. Si plusieurs règles correspondent à un MO, seule la règle la plus élevée est appliquée.

## Paramètres du modèle de diffusion SMS {#sms-delivery-template-parameters}

Certains paramètres peuvent être définis par modèle de diffusion.

### Du champ {#from-field}

Ce champ est facultatif. Il permet de remplacer l&#39;adresse de l&#39;expéditeur (oADC). Le contenu de ce champ est placé dans le champ `source_addr` de `SUBMIT_SM PDU`.

Le champ est limité à 21 caractères par la spécification SMPP, mais certains fournisseurs peuvent autoriser des valeurs plus longues. Notez également que des restrictions très strictes peuvent être appliquées dans certains pays, par exemple la longueur, le contenu, les caractères autorisés.

### Paramètres de la diffusion {#delivery-parameters}

#### Nombre maximal de SMS par message {#maximum-sms}

Ce paramètre ne fonctionne que si le paramètre **Charge utile du message** est désactivé. Si le message nécessite plus de SMS que cette valeur, une erreur est déclenchée.

Le protocole SMS limite les SMS à 255 parties, mais certains téléphones portables ont du mal à assembler de longs messages avec plus de 10 parties environ, la limite dépend du modèle exact. Nous vous conseillons de ne pas dépasser 5 parties par message.

En raison du fonctionnement des messages personnalisés en Adobe Campaign, la taille des messages peut varier. Avoir beaucoup de messages longs pourrait augmenter les coûts d&#39;envoi.

#### Mode de transmission {#transmission-mode}

Ce champ indique le type de SMS que vous souhaitez transférer : messages normaux ou flash, stockés sur le mobile ou la carte SIM.

Ce paramètre est transmis dans le champ facultatif `dest_addr_subunit` de `SUBMIT_SM PDU`.

* **L&#39;option** Non spécifié n&#39;envoie aucun champ facultatif dans la PDU.

* **** Flash définit la valeur sur 1. Il envoie un message Flash qui s&#39;affiche sur le mobile et n&#39;est pas stocké en mémoire.

* **** Normalise la valeur sur 0. Il envoie un message normal.

* **Enregistrer sur** mobileset définit la valeur sur 2. Il dit au téléphone de stocker le SMS dans la mémoire interne.

* **Enregistrer sur** terminalset la valeur à 3. Il indique au téléphone de stocker le SMS dans la carte SIM.

#### Période de validité {#validity-period}

La période de validité est transmise dans le champ `validity_period` du `SUBMIT_SM PDU`. La date est toujours formatée en tant que format d’heure UTC absolu, le champ de date se termine par &quot;00+&quot;.

## Connecteur SMPP générique étendu {#acc-extended-connector}

![](assets/sms_protocol_4.png)

Les flèches représentent des flux de données.

Lors de l’envoi de pièces de diffusion, la MTA génère des enfants MTA. Le nombre de processus enfants MTA est dynamique et dépend d’une configuration dans le fichier serverConf.xml. Chaque enfant MTA instancie le connecteur `CSmppConnectorWorker` qui se connecte au fournisseur SMPP. Les connexions sont maintenues en vie tant que l’enfant MTA est maintenu en vie, ce qui est également configurable dans serverConf.xml.

Le processus SMS ne traite que SR, se connecte au fournisseur et laisse la connexion ouverte. Le processus se reconnecte toutes les 10 minutes pour recharger de nouveaux paramètres, ce qui est normal.

### Correspondance des entrées MT, SR et à journal large {#matching-mt}

Une table intermédiaire `nmsProviderMsgId` est utilisée pour stocker temporairement les données MT et SR avant d&#39;être validée de manière asynchrone sur le journal large.

`nmsProviderMsgId` Le tableau comprend 3 groupes de colonnes :

* Colonnes mises à jour lorsqu’un MT est envoyé et accusé de réception : `iBroadLogId`, `iDeliveryId`

* Colonnes mises à jour lors de la réception d&#39;une SR : `iMsgId`, `iStatus`

* Colonnes qui sont toujours mises à jour : `tsCreated`, `sProviderId`

Une fois le traitement de MT et SR terminé, vous devriez avoir des lignes complètes, avec des informations à la fois sur le journal large et sur l&#39;état.

Ici, `iMsgId` est lié à la table `nmsBroadLogMsg`, ce qui indique le message d’état/d’erreur complet.

Le processus SMS recherche toutes les minutes des lignes complètes, puis les traite de façon asynchrone :

* La ligne complète est lue.
* Le processus SMS calcule le nom de la table du journal large en fonction du mappage des diffusions.
* Le processus SMS met à jour la table du journal de publication avec l&#39;ID du message et l&#39;état.

**Connexions de débit et parallèles**

Chaque enfant MTA crée un nombre configurable de connexions, de sorte que la limitation du nombre d’enfants MTA limite le nombre de connexions. Comme la corrélation entre les processus enfants MTA et le trafic est corrélée, cela peut être quelque peu contrôlé mais encore un peu imprévisible.

## Avant de commencer à être en direct {#checklist}

Cette liste de contrôle fournit une liste de choses que vous devriez vérifier avant de commencer à utiliser. Une configuration incomplète peut entraîner de nombreux problèmes.

### Rechercher les conflits de compte externe {#external-account-conflict}

Vérifiez que vous n&#39;avez pas de vieux comptes externes SMS. Si vous laissez le compte test désactivé, vous risquez qu’il soit réactivé sur le système de production et qu’il génère des conflits potentiels.

Si plusieurs comptes de la même instance Adobe Campaign se connectent au même fournisseur, contactez ce dernier pour vérifier qu’ils distinguent effectivement les connexions entre ces comptes. La présence de plusieurs comptes avec la même connexion nécessite une configuration supplémentaire.

### Activer les traces SMPP détaillées lors des vérifications {#enable-verbose}

Vous devez toujours activer les traces SMPP détaillées lors des vérifications.
Même si vous ne pouvez pas vérifier vous-même les journaux, il sera plus facile pour le Support de vous aider.

### Testez votre SMS {#test}

* **Envoyez des SMS avec toutes sortes de**
caractèresSi vous devez envoyer des SMS avec des caractères non GSM ou non ASCII, essayez d&#39;envoyer des messages avec autant de caractères différents que possible. Si vous définissez une table de mappage de caractères personnalisée, envoyez au moins un SMS pour tous les 
`data_coding` valeurs.

* **Vérifiez que les demandes de service sont correctement**
traitées. Le SMS doit être marqué comme reçu dans le journal de diffusion. Le journal des diffusions doit réussir et se présenter comme suit :

Vérifiez que vous avez modifié le nom du fournisseur de diffusions. Le journal des diffusions ne doit jamais contenir    `SR yourProvider stat=DELIVRD err=000|#MESSAGE`
Vérifiez que vous avez modifié le nom du fournisseur de diffusions. Le journal des diffusions ne doit jamais contenir **SR Generic** sur les environnements de production.

* **Vérifier que l&#39;ordinateur portable est**
traitéSi vous devez traiter l&#39;ordinateur portable (réponses automatiques, stockage de l&#39;ordinateur portable dans la base de données, etc.) essayez de faire des tests. Envoyez quelques SMS pour tous les mots-clés de réponse automatique et vérifiez si la réponse est assez rapide, pas plus de quelques secondes.
Archivez le journal auquel Adobe Campaign répond avec succès 
`DELIVER_SM_RESP` (command_status=0).

### Vérifier les PDU {#check-pdus}

Même si les messages ont l&#39;air réussis, il est important de vérifier que les PDU sont correctement formatées.

Cette étape est nécessaire lors de la connexion à un fournisseur qui n’était pas connecté à Adobe Campaign auparavant.

#### BIND {#bind}

Vérifiez que `BIND_* PDUs` est correctement envoyé. La chose la plus importante à vérifier est que le fournisseur renvoie toujours la réussite `BIND_*_RESP PDUs` (command_status = 0).

Vérifiez qu&#39;il n&#39;y a pas trop de `BIND_* PDU`s. S&#39;il y en a trop, cela peut indiquer que la connexion est instable. Pour plus d&#39;informations, consultez la section [Problèmes liés aux connexions instables](../../delivery/using/sms-protocol.md#issues-unstable-connection).

#### ENQUIRE_LINK {#enquire-link-pdus}

Vérifiez que `ENQUIRE_LINK PDU`s sont échangés régulièrement lorsque la connexion est inactive.

**SUBMIT_SM / DELIVER_SM**

Envoyez un message, puis recherchez dans les journaux les `SUBMIT_SM`, `SUBMIT_SM_RESP`, `DELIVER_SM` et `DELIVER_SM_RESP PDU`s correspondants.

Avec `SUBMIT_SM PDU` :

* Vérifiez que `data_coding` est correct, 0 par défaut.
* Vérifiez que `short_message` est correctement codé. Essayez de le décoder à l’aide d’un convertisseur hexadécimal qui prend en charge plusieurs codages.

Avec `SUBMIT_SM_RESP PDU` :

* Vérifiez qu&#39;il a réussi, command_status = 0.
* Vérifiez que son corps contient un ID correctement formaté suivi d’un octet &quot;0&quot;.

Avec `DELIVER_SM PDU` :

* Décodez le champ hexadécimal `short_message`.
* Vérifiez avec un outil de vérification regex que l&#39;expression regex définie dans `Extraction` regex de l&#39;identifiant dans la SR renvoie exactement un groupe de capture et qu&#39;elle capture l&#39;identifiant entier dans le message.
* Vérifiez que l&#39;ID extrait correspond à celui de `SUBMIT_SM_RESP`.
* Vérifiez que l&#39;expression regex définie dans `Extraction` regex de l&#39;état dans la SR renvoie le contenu du champ stat.
* Vérifiez que l&#39;expression regex définie dans `Extraction` regex de l&#39;erreur dans la SR renvoie le contenu du champ err.

Avec `DELIVER_SM_RESP PDU` :

* Vérifiez qu’il a été envoyé rapidement après avoir reçu le `DELIVER_SM PDU`, généralement moins d’une seconde.
* Vérifiez qu&#39;il a réussi, command_status = 0.

### Vérifiez auprès de votre fournisseur {#provider}

Même si votre SMS réussit, contactez le fournisseur pour voir si tout est en ordre.

### Désactiver les traces SMPP détaillées {#disable-verbose}

Une fois toutes les vérifications terminées, la dernière chose à faire est de **désactiver les traces SMPP détaillées** pour ne pas générer trop de journaux. Vous pouvez les réactiver à des fins de dépannage, même sur les systèmes de production.
