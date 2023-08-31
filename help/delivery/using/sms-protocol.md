---
product: campaign
title: Protocole et paramètres du connecteur SMS
description: En savoir plus sur le connecteur SMS et comment le configurer
badge-v7: label="v7" type="Informative" tooltip="S’applique à Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="S’applique également à Campaign v8"
feature: SMS
role: Developer, Data Engineer
exl-id: fded088a-11a2-4b87-a368-7b197334aca4
source-git-commit: d2f5f2a662c022e258fb3cc56c8502c4f4cb2849
workflow-type: tm+mt
source-wordcount: '8458'
ht-degree: 99%

---

# Protocole et paramètres du connecteur SMS {#sms-connector-protocol}

>[!NOTE]
>
>Dans ce document, toutes les références au protocole, aux noms de champs et aux valeurs se rapportent à la [spécification SMPP 3.4](https://smpp.org/SMPP_v3_4_Issue1_2.pdf).
>

## Vue d&#39;ensemble {#overview}

Les SMS peuvent se limiter à envoyer des SMS courts sans formatage, mais leur simplicité en fait un canal de communication précieux.

Il existe deux façons principales d&#39;envoyer un SMS :

* L&#39;envoyer manuellement à partir d&#39;un téléphone, façon habituelle de communiquer directement entre personnes.
* L&#39;envoyer depuis Internet, façon dont Adobe Campaign envoie des messages. Pour cela, vous avez besoin d&#39;un fournisseur de services de SMS destiné à connecter Internet au réseau mobile.
Adobe Campaign utilise le protocole SMPP pour envoyer des SMS à un fournisseur de services.

Ce document vous guide tout au long de la configuration de la connexion entre Adobe Campaign et un fournisseur SMPP.

Les fournisseurs SMPP peuvent parfois s&#39;écarter des spécifications officielles, mais le connecteur SMS d&#39;Adobe Campaign offre de nombreuses options pour adapter son comportement pour qu&#39;il soit compatible avec la plupart des fournisseurs.

>[!IMPORTANT]
>
>La configuration d&#39;une connexion à un nouveau fournisseur peut nécessiter des compétences techniques, des connaissances relatives au protocole TCP, au binaire, à la représentation hexadécimale et aux encodages de texte. Il faudra également une coopération active avec le fournisseur.

### Types de SMS {#sms-types}

Lorsque vous envoyez des SMS en masse par l&#39;intermédiaire d&#39;un fournisseur de services SMS, vous rencontrerez trois types de SMS différents :

* **SMS MT (Mobile Terminated)** : un SMS émis par Adobe Campaign vers les téléphones portables par l&#39;intermédiaire du fournisseur SMPP.

* **SMS MO (Mobile Originated)** : un SMS envoyé par un téléphone mobile à Adobe Campaign par l&#39;intermédiaire du fournisseur SMPP.

* **SMS SR (Status Report) ou DR ou DLR (Delivery Receipt)** : un accusé de réception envoyé par le téléphone mobile à Adobe Campaign par l&#39;intermédiaire du fournisseur SMPP indiquant que le SMS a été reçu avec succès. Adobe Campaign peut également recevoir des SR indiquant que le message n&#39;a pas pu être remis, souvent avec une description de l&#39;erreur.

Vous devez faire la distinction entre les accusés de réception (PDU RESP, partie du protocole SMPP) et SR : le SR est un type de SMS qui est envoyé par le réseau de bout en bout, alors qu&#39;un acquittement n&#39;est qu&#39;une confirmation de la réussite d&#39;un transfert.

Les acquittements et les SR peuvent déclencher des erreurs, la distinction entre les deux facilitera le résolution des problèmes.

### Informations transportées par un SMS {#information-sms}

Un SMS contient plus d&#39;informations que de texte. Voici une liste de ce que vous pouvez vous attendre à trouver dans un SMS :

* Le texte, qui est limité à 140 octets, ce qui signifie entre 70 et 160 caractères selon l&#39;encodage. Voir [Encodage du texte SMS](sms-protocol.md#sms-text-encoding) ci-dessous pour plus de détails et pour connaître les limitations.

* Adresse du destinataire, parfois appelée `ADC` ou `MSISDN`. C&#39;est le numéro du mobile qui recevra le SMS.

* Adresse de l&#39;expéditeur, qui peut être appelée `oADC` ou parfois `sender id`. Il peut s&#39;agir d&#39;un numéro de téléphone utilisé au quotidien, d&#39;un numéro court envoyé par l&#39;intermédiaire d&#39;un fournisseur ou d&#39;un nom. Le nom est une fonctionnalité facultative. Dans ce cas, vous ne pouvez pas répondre au SMS.

* Indicateur indiquant si le message est un message Flash. Un message Flash est un pop-up qui n’est pas stocké en mémoire.

* Indicateur indiquant si un SR est attendu ou non.

* Date de validité, après laquelle aucun équipement réseau n&#39;est autorisé à réessayer.

* Champ `data_coding` qui indique l&#39;encodage du texte.

## Protocole SMPP {#smpp-protocol}

Adobe Campaign Classic prend en charge le protocole SMPP version 3.4. Il s&#39;agit d&#39;un protocole répandu qui permet d&#39;envoyer des SMS à un fournisseur (SMSC) et de recevoir des SMS ainsi que des accusés de réception. Consultez à ce sujet la [documentation SMPP](https://smpp.org/SMPP_v3_4_Issue1_2.pdf).

L&#39;équipement réseau côté fournisseur SMS est souvent appelé SMSC.

### Connexions SMPP {#smpp-connections}

Adobe Campaign se connecte à l&#39;équipement réseau du fournisseur SMS via TCP. Le protocole SMPP définit des connexions TCP permanentes d&#39;Adobe Campaign au fournisseur. Les connexions TCP sont toujours initiées par Adobe Campaign, même pour recevoir des messages.
SMPP ouvre 1 ou 2 connexions TCP, selon son mode. Toutes les connexions sont toujours initiées par Adobe Campaign.

Le protocole SMPP peut fonctionner en deux modes :

* **Transmitter + receiver (ou TX+RX)** : deux connexions TCP distinctes sont utilisées pour la transmission et la réception de messages.
* **Transceiver (ou TRX)** : une connexion TCP unique est utilisée pour transmettre et recevoir des messages.

>[!NOTE]
>
> Adobe Campaign Classic ne prend en charge que le mode TX+RX. Cette limite est liée à son architecture technique.

### PDU SMPP {#smpp-pdu}

Les unités de transmission SMPP (&quot;paquets&quot;) sont appelées PDU. Un **PDU** contient une commande, un statut, un numéro de séquence et des données.

Chaque PDU doit être acquitté par une `SMPP RESP PDU` (réponse synchrone). Les requêtes peuvent être acheminées : l&#39;expéditeur peut envoyer de nombreuses commandes sans attendre `RESP`, le nombre de requêtes pouvant être acheminé par pipeline à tout moment est appelé la fenêtre. `RESP PDU` peut arriver dans n&#39;importe quel ordre, sans rapport avec l&#39;ordre de leur PDU initiateur correspondant.

Dans le mode séparé **Transmitter + receiver**, la connexion utilisée dépend du type de message transmis. La connexion de l&#39;émetteur est utilisée pour les MT, et la connexion du récepteur est utilisée pour les MO et SR. Les requêtes et réponses pour chaque type de message sont envoyées via la même connexion TCP.

Par exemple, lors de l&#39;envoi d&#39;un MT, la connexion de l&#39;émetteur est utilisée et le `RESP` qui acquitte le MT est également envoyé par l&#39;intermédiaire du canal de l&#39;émetteur. Lorsque vous recevez un MO (ou un SR), la connexion du récepteur est utilisée pour recevoir le MO et pour envoyer le `RESP` qui acquitte le MO.

![](assets/do-not-localize/sms_protocol_1.png)

Dans Adobe Campaign Classic, pour lier un SR à son MT correspondant, un identifiant est renvoyé par le SMSC avec les étapes `SUBMIT_SM_RESP` et `DELIVER_SM`. L&#39;identifiant est stocké dans le champ `providerId` de la table `nms::providerMsgId` et est lié à `broadLogId` et `deliveryId`. Cette opération de correspondance est effectuée par le processus SMS lors de l&#39;écriture dans la base de données.

Un `SUBMIT_SM_RESP PDU` réussi déclenche le statut du message &quot;envoyé&quot; dans le journal d&#39;envoi tandis qu&#39;un `DELIVER_SM (SR) PDU` réussi déclenche le statut du message &quot;reçu&quot;.

### Aspects liés à la sécurité {#security-aspects}

Le protocole lui-même n&#39;est pas chiffré. La plupart des fournisseurs mettent en œuvre une variante d&#39;IP sur la liste autorisée, de sorte que les adresses IP du serveur Adobe Campaign doivent être déclarées au fournisseur.

Adobe Campaign prend en charge la transmission d&#39;un nom d&#39;utilisateur et d&#39;un mot de passe lors de la phase de liaison. Il prend également en charge le SMPP plutôt que le TLS. Il convient de noter que des certificats sont requis pour assurer une sécurité adéquate. Bien que le connecteur SMPP permette de contourner les vérifications de certificats, il ne doit être utilisé que pour les tests, car un TLS sans certificat offre un niveau de sécurité nettement inférieur.

Le connecteur utilise les certificats par défaut fournis par la bibliothèque système `openssl`. En général, il est fourni par le répertoire `/etc/ssl/certs` sur Debian. Ce répertoire est fourni par le package &quot;ca-certificates&quot; par défaut, mais il peut être personnalisé.

### Informations sur chaque type de PDU {#information-pdu}

Chaque type de PDU possède des champs distincts qui portent des éléments d&#39;information différents. Ces PDU sont détaillés dans la [spécification SMPP 3.4](https://smpp.org/SMPP_v3_4_Issue1_2.pdf).

Chaque section ci-dessous décrit le PDU et sa réponse synchrone (`*_RESP PDU`). Tous les PDU doivent être acquittés par un `RESP` correspondant, c&#39;est une partie obligatoire de la spécification.

Les PDU peuvent comporter des champs facultatifs. Seuls les champs les plus courants sont décrits ici. Pour plus d&#39;informations, consultez la [spécification SMPP 3.4](https://smpp.org/SMPP_v3_4_Issue1_2.pdf).

**BIND_TRANSMITTER / BIND_RECEIVER / BIND_TRANSCEIVER**

Ce PDU est utilisé pour initier une connexion avec le SMSC. Les modes **Transmitter**, **Receiver** et **Transceiver** ne modifient que le type de SMS autorisé à être transféré sur ce lien, en particulier :

| Mode | Types de SMS autorisés |
|:-:|:-:|
| Transmitter | MT |
| Receiver | MO + SR |
| Transceiver | MT + MO + SR |

Champs visibles dans un `BIND_* PDU` :

* **system_id** : nom d&#39;utilisateur utilisé pour l&#39;authentification. Défini dans le compte externe.

* **Password** : mot de passe utilisé pour l&#39;authentification. Défini dans le compte externe.

* **System_type** : obligatoire pour définir une valeur spécifique pour certains fournisseurs. Défini dans le compte externe, disponible dans toutes les versions. Il est souvent fait la distinction entre différents types de contrats, canaux, pays, etc.

* **addr_ton** et **addr_npi** : requis par certains fournisseurs. Défini par les paramètres `Bind TON` et `Bind NPI` dans le compte externe.

* **address_range** : requis par certains fournisseurs. La plupart du temps, il s&#39;agit d&#39;une liste de numéros courts autorisés sur cette connexion. Défini dans le compte externe.

`BIND_*_RESP` n&#39;a pas de champ spécifique, il confirme si la connexion a réussi ou non.

#### UNBIND {#unbind}

Ce PDU doit être envoyé par le système avant de se déconnecter. Il doit attendre le PDU `UNBIND_RESP` correspondant avant de fermer la connexion.

La conformité SMSC ne doit pas fermer la connexion, la connexion TCP est contrôlée par le connecteur Adobe Campaign.

#### SUBMIT_SM {#submit-sm}

Ce PDU envoie un MT au SMSC. Sa réponse PDU donne l&#39;ID du MT.

Champs visibles dans un PDU`SUBMIT_SM` :

* **service_type** : requis par certains fournisseurs. Défini dans les propriétés de la diffusion.

* **source_addr_ton** et **source_addr_npi** : indique le type d&#39;adresse source transmise. La signification de ces champs est normalisée, mais comme certains fournisseurs les utilisent différemment, vous devriez demander au fournisseur sa valeur correcte. Défini dans le compte externe.

* **source_addr** : l&#39;adresse source / oADC du MT. Elle sera affichée sur le téléphone mobile. Définie dans le compte externe et la diffusion, la valeur de la diffusion prévaut sur la valeur du compte externe.

* **dest_addr_ton** et **dest_addr_npi** : indique le type d&#39;adresse de destination transmise (format local ou international, par exemple). La signification de ces champs est normalisée, mais comme certains fournisseurs les utilisent différemment, vous devriez demander au fournisseur sa valeur correcte. Défini dans le compte externe.

* **destination_addr** : adresse du destinataire, numéro de téléphone ou MSISDN.

* **esm_class** : permet de déterminer si UDH est utilisé ou non dans le champ de texte. Activé automatiquement par le connecteur pour scinder les SMS si le mode `message_payload` n&#39;est pas utilisé.

* **priority_flag** : priorité de ce message sur les autres. Cela est lié à la priorité de la diffusion elle-même.

* **validity_period** : date et heure après lesquelles aucune nouvelle tentative ne doit être effectuée. Défini dans la diffusion elle-même.

* **registered_delivery** : indique si un SR est demandé ou non. Adobe Campaign définit toujours cet indicateur, à l&#39;exception des réponses automatiques. Pour les messages en plusieurs parties, l&#39;indicateur n&#39;est défini que pour la première partie. Toutes les versions ont le même comportement.

* **data_coding** : indique le codage utilisé dans le champ de texte. Pour plus d&#39;informations, consultez la section [Encodage du texte SMS](sms-protocol.md#sms-text-encoding) pour plus d&#39;informations.

* **short_message** : texte du message. Si UDH est utilisé, il contient également l&#39;en-tête UHD.

Adobe Campaign prend en charge les champs facultatifs suivants :

* **Dest_addr_subunit** : utilisé pour spécifier la cible du SMS : flash, mobile ou carte SIM. Défini dans les propriétés de la diffusion.

* **message_payload** : lorsqu&#39;il est activé dans le compte externe, de longs messages sont envoyés dans un seul PDU et le texte est transmis dans ce champ plutôt que dans le champ `short_message`.

#### SUBMIT_SM_RESP {#submit-sm-resp}

Ce PDU contient l&#39;ID du MT. Ceci est utile pour établir une correspondance avec le SR entrant.

>[!IMPORTANT]
>
>De nombreux fournisseurs transmettent l&#39;ID MT au format hexadécimal. Assurez-vous de définir correctement le **format de l&#39;ID dans l&#39;acquittement MT** dans le compte externe.

Certains fournisseurs envoient `SUBMIT_SM_RESP` après l&#39;envoi du SR. Pour tenir compte de ce comportement, Adobe Campaign attend 30 secondes avant de répondre **Identifiant du message non valide** à un SR avec un ID inconnu.

#### DELIVER_SM {#delivery-sm}

Ce PDU est envoyé par le SMSC à Adobe Campaign. Il contient un MO ou un SR.

La plupart des champs ont la même signification que leur contrepartie `SUBMIT_SM`. Voici la liste des champs utiles :

* **source_addr** : adresse source du MO/SR. Il s&#39;agit généralement d&#39;un numéro de téléphone.

* **destination_addr** : numéro court qui a reçu le MO ou le SR.

* **esm_class** : utilisé pour déterminer si le PDU est un MO ou un SR.

* **short_message** : texte du message. Pour le SR, il contient les données décrites à l&#39;annexe B de la spécification du protocole SMPP. Voir [Gestion des erreurs SR](sms-protocol.md#sr-error-management) pour plus de détails.

Adobe Campaign peut lire l&#39;identifiant du message dans le champ facultatif `receipted_message_id` avec un ajustement de la configuration.

#### DELIVER_SM_RESP {#deliver-sm-resp}

Ce PDU est envoyé par Adobe Campaign pour acquitter SR et MO.

Adobe Campaign Classic reconnaît SR et MO une fois qu&#39;ils ont été insérés dans la base de données. Certaines erreurs de traitement peuvent se produire même si un PDU `DELIVER_SM_RESP` réussi a été envoyé. Cette limite est due à l&#39;architecture logicielle d&#39;Adobe Campaign Classic.

#### ENQUIRE_LINK {#enquire-links}

Ce PDU n&#39;est utilisé que pour vérifier que la connexion est active. Sa fréquence doit être définie en fonction des besoins du fournisseur.

Les 60 secondes par défaut doivent correspondre à la plupart des configurations définies dans le compte externe.

#### ENQUIRE_LINK_RESP {#enquire-links-resp}

Ce PDU acquitte le fait que la connexion est active.

### SMS en plusieurs parties (SMS long) {#multipart}

>[!IMPORTANT]
>
> Adobe Campaign prend uniquement en charge l’envoi de SMS en plusieurs parties ou de SMS longs. UDH et `message_payload` ne sont pas pris en charge pour les SMS entrants (MO), ce qui signifie que les MO sont limités à 160 caractères.

Les SMS en plusieurs parties, ou les SMS longs, sont des SMS envoyés en plusieurs parties. En raison des limitations techniques du protocole de réseau mobile, un SMS ne peut pas dépasser 140 octets ou doit être fractionné. Consultez la section [Encodage du texte SMS](sms-protocol.md#sms-text-encoding) pour en savoir plus sur le nombre de caractères pouvant tenir dans un SMS.

Chaque partie d&#39;un long message est un SMS individuel. Ces pièces se déplacent indépendamment sur le réseau et sont assemblées par le téléphone mobile récepteur. Pour gérer les reprises et les problèmes de connectivité, Adobe Campaign envoie ces pièces dans l&#39;ordre inverse et ne demande un SR que sur la première partie du message, la dernière envoyée. Puisque le téléphone portable n&#39;affiche un message que lors de la réception de sa première partie, les reprises sur d&#39;autres parties ne produisent pas de doublons sur le téléphone portable.

Le nombre maximal de SMS par message peut être défini par diffusion à l&#39;aide du paramètre **Nombre maximal de SMS par message** défini dans le **Modèle de diffusion**. Les messages qui dépassent cette limite échouent lors de l&#39;envoi d&#39;un SMS avec une raison d&#39;échec trop longue.

Il y a deux façons d&#39;envoyer des SMS longs :

* **UDH** : la méthode par défaut et recommandée pour envoyer des messages longs. Dans ce mode, le connecteur divise le message en plusieurs `SUBMIT_SM PDU` avec les informations UDH. Ce protocole est celui utilisé par les téléphones portables eux-mêmes. Cela signifie qu&#39;Adobe Campaign a le plus grand contrôle sur la génération de messages, ce qui lui permet de calculer exactement combien de parties ont été envoyées et comment elles ont été fractionnées.

* **message_payload** : la façon d&#39;envoyer tout le long message en un seul `SUBMIT_SM PDU`. Le fournisseur devra le fractionner, ce qui signifie qu&#39;il est impossible pour Adobe Campaign de savoir exactement combien de parties ont été envoyées. Certains fournisseurs exigent ce mode, mais nous vous conseillons de ne l&#39;utiliser que s&#39;ils ne prennent pas en charge l&#39;UDH.

Consultez la description des champs `esm_class`, `short_message` et `message_payload` du PDU [SUBMIT_SM](sms-protocol.md#information-pdu) pour plus d&#39;informations sur le protocole et les formats.

### Limitation du débit et fenêtrage {#throughput-capping}

La plupart des fournisseurs exigent une limite de débit pour chaque connexion SMPP. Pour ce faire, il est possible d&#39;établir un certain nombre de SMS dans le compte externe. Notez que le ralentissement du débit se produit par connexion, le débit effectif total est la limite par connexion multipliée par le nombre total de connexions. Ceci est détaillé dans la section [Connexions simultanées](sms-protocol.md#connection-settings).

Pour atteindre le débit maximal possible, vous devez affiner la fenêtre d&#39;émission maximale. La fenêtre d&#39;émission est le nombre de `SUBMIT_SM PDU` qui peuvent être envoyés sans attendre un `SUBMIT_SM_RESP`. Pour plus d&#39;informations, consultez la section [Paramètres de la fenêtre d&#39;émission](sms-protocol.md#throughput-timeouts).

### Gestion des SR et des erreurs (&quot;Annexe B&quot;) {#sr-error-management}

Le protocole SMPP définit des erreurs synchrones standard dans `RESP PDU`, mais il ne définit pas de codes d&#39;erreur pour SR. Chaque fournisseur utilise ses propres codes d&#39;erreur avec leur signification.

Une recommandation est faite dans la section de l&#39;Annexe B de la [spécification du protocole SMPP](https://smpp.org/SMPP_v3_4_Issue1_2.pdf) (page 167), mais sans indiquer les codes d&#39;erreur réels ni leur signification.

Pour s&#39;adapter à la gestion des erreurs, le système de messagerie broadlog d&#39;Adobe Campaign a été exploité pour indiquer correctement les erreurs et leur sévérité (hard, soft, etc.).

Comme mentionné ci-dessus, il existe deux types d&#39;erreurs :

* réponses synchrones dans le `SUBMIT_SM_RESP` qui surviennent immédiatement après l&#39;envoi du message au SMSC
* accusés de réception qui peuvent s&#39;afficher beaucoup plus tard lorsque le mobile a reçu le message ou lorsque le message a expiré. Dans ce cas, l&#39;erreur se trouve dans un SR.

Lorsqu&#39;un SR est reçu, le statut et l&#39;erreur se trouvent dans son champ `short_message` (exemple pour les mises en œuvre conformes à l&#39;Annexe B). Le champ `short_message` du PDU est souvent appelé le **champ de texte**, car il contient du texte en MT. En cas de SR, il contient des informations techniques ainsi qu&#39;un sous-champ nommé **Texte**. Ces deux champs sont différents et `short_message` contiennent en fait le champ **Texte** et d&#39;autres informations.

Les connecteurs Adobe Campaign Classic (à l&#39;exception de l&#39;option SMPP étendu) utilisent un comportement codé en dur qui dépend du fournisseur sélectionné. Le SMPP générique ne fait que distinguer la réussite de l&#39;erreur, sans aucun détail. Le log de diffusion peut contenir certaines informations qui ne sont pas garanties.

#### Format de champ de texte SR {#sr-text-field-format}

La spécification recommande d&#39;utiliser ce format pour le champ de texte SR. Il s&#39;agit d&#39;une liste de sous-champs séparés dans l&#39;espace par deux points pour séparer le nom du champ et sa valeur. Les noms de champ ne respectent jamais la casse.

Exemple d&#39;un champ de texte SR correspondant à la recommandation de l&#39;Annexe B :

```
id:1234567890 sub:001 dlvrd:001 submit date:1608011415 done date:1608011417 stat:DELIVRD err:000 Text:Hello Adobe world
```

Le champ id correspond à l&#39;ID reçu dans `SUBMIT_SM_RESP PDU`, c&#39;est-à-dire l&#39;acquittement de la valeur MT.

`sub` et `dlvrd` sont censés compter la quantité de parties délivrées et de messages délivrés, mais ceci n&#39;est pas utilisé par Adobe Campaign puisque le système broadlog donne une information meilleure et plus intégrée.

Les champs `submit date` et `done date` sont des dates et heures indicatives du moment où le MT a été envoyé et du moment où le SR a été envoyé par le mobile. Vous pouvez vous attendre à des problèmes de fuseaux horaires ou même à des dates et heures incorrectes données par les mobiles avec un jeu de dates incorrect.

Le champ &quot;stat&quot; est important car il indique le statut du message. Les seuls statuts importants sont `DELIVRD`, `UNDELIV` et `REJECTD`. Le statut `DELIVRD` indique une réussite, les deux autres indiquent une erreur. D&#39;autres valeurs sont possibles, mais il s&#39;agit généralement de notifications intermédiaires, par exemple le MT a atteint l&#39;opérateur de téléphonie mobile, mais pas le téléphone mobile. Ces notifications intermédiaires sont ignorées par Adobe Campaign.

Le champ &quot;err&quot; contient le code d&#39;erreur propre au fournisseur. Le fournisseur doit fournir un tableau des codes d&#39;erreur possibles ainsi que leur signification pour pouvoir interpréter cette valeur.

Enfin, le champ &quot;text&quot; contient généralement le début du texte du MT. Adobe Campaign n&#39;en tient pas compte et certains fournisseurs ne le transmettent pas pour éviter les fuites d&#39;informations d&#39;identification personnelle et la consommation de bande passante du réseau. Il peut être utilisé lors de résolution des problèmes pour repérer plus facilement le SR correspondant à un test MT en lisant ce champ.

### Exemple de traitement SR dans un SMPP générique étendu Adobe Campaign Standard {#sr-processing}

Cet exemple montre comment afficher le cas d&#39;une mise en œuvre suivant la recommandation de l&#39;Annexe B, les valeurs par défaut dans le compte externe et un SMS MT réussi.

```
id:1234567890 sub:001 dlvrd:001 submit date:1608011415 done date:1608011417 stat:DELIVRD err:000 Text:Hello Adobe world
```

Tout d&#39;abord, l&#39;expression régulière `id extraction` est appliquée pour extraire l&#39;identifiant et le rapprocher avec le MT correspondant.

Ensuite, les champs expression régulière `status extraction` et expression régulière `error code extraction` sont appliqués pour extraire ces champs et sont ajoutés à la chaîne.

Le message broadlog est construit à l&#39;aide de ces informations et la chaîne d&#39;origine non modifiée est ajoutée à titre de référence :

```
SR ExampleProvider DELIVRD 000|MESSAGE=id:1234567890 sub:001 dlvrd:001 submit date:1608011415 done date:1608011417 stat:DELIVRD err:000 Text:Hello Adobe world
```

Le message est alors normalisé, supprimant la partie MESSAGE pour pouvoir faire correspondre plusieurs messages avec le même statut et le même code d&#39;erreur.

```
SR ExampleProvider DELIVRD 000|#MESSAGE#
```

Si le message n&#39;est pas déjà configuré dans le tableau des messages broadlog, une nouvelle entrée est créée, en utilisant le message entier comme **firstText** et le message normalisé. Ensuite, le connecteur utilise le succès et l&#39;expression régulière `error` pour déterminer s&#39;il s&#39;agissait d&#39;une réussite ou d&#39;un échec :

* S&#39;il correspond à l&#39;expression régulière `success`, il est considéré comme une réussite.

* S&#39;il correspond à l&#39;expression régulière `error`, le message est qualifié d&#39;erreur.

* Si aucune de ces deux expressions régulières ne correspond, le SR est ignoré. Il peut s&#39;agir d&#39;une notification intermédiaire, qui n&#39;est pas gérée par Adobe Campaign.

Par défaut, toutes les erreurs sont configurées en tant qu&#39;erreurs logicielles. Cela signifie que les erreurs hard doivent être corrigées à la main.

### Encodage du texte SMS {#sms-text-encoding}

Vous devez **toujours contacter le fournisseur SMSC en cas de problèmes d&#39;encodage**. Seuls les fournisseurs SMSC ont une connaissance de l&#39;encodage qu&#39;ils prennent en charge et des règles spéciales qui peuvent s&#39;appliquer en raison des limites de leur plateforme technique.

Les messages SMS utilisent un encodage spécial de 7 bits, souvent appelé encodage GSM7.

Dans le protocole SMPP, le texte GSM7 sera étendu à 8 bits par caractère pour faciliter le résolution des problèmes. La SMSC le compresse en 7 bits par caractère avant de l&#39;envoyer au mobile. Cela signifie que le champ `short_message` du SMS peut comporter jusqu&#39;à 160 octets dans le cadre SMPP, alors qu&#39;il est limité à 140 octets lorsqu&#39;il est envoyé sur le réseau mobile.

En cas de problème d&#39;encodage, voici quelques éléments importants à vérifier :

* Assurez-vous de connaître les caractères qui font partie de l&#39;encodage. GSM7 ne prend pas entièrement en charge les signes diacritiques ou les accents. Surtout en français, où &quot;é&quot; et &quot;è&quot; font partie de GSM7, mais &quot;ê&quot;, &quot;â&quot; ou &quot;ï&quot; non. Il en va de même pour l&#39;espagnol.

* Le C avec cédille (ç) n&#39;est présent que dans les majuscules de l&#39;alphabet GSM7, mais certains téléphones le rendent en minuscules ou &quot;smart&quot;. La recommandation générale est d&#39;éviter complètement la cédille ou de basculer en UCS-2.

* **N&#39;utilisez pas l&#39;ASCII dans les SMS**, sauf si le fournisseur SMSC le demande explicitement. Cet encodage réduit l&#39;espace car il comporte des caractères 8 bits et une couverture inférieure à celle de GSM7. Cet encodage peut être requis pour les réseaux CDMA, utilisés en Amérique du Nord.

* Latin-1 n&#39;est pas toujours pris en charge. Vérifiez la compatibilité avec votre fournisseur SMSC avant de tenter d&#39;utiliser Latin-1.

* Les tableaux de conversion de langue nationale ne sont pas pris en charge par le connecteur Adobe Campaign. Vous devez utiliser UCS-2 ou autre `data_coding` à la place.

* UCS-2 et UTF-16 sont souvent mélangés par les téléphones. Ceci est un problème lors de l&#39;utilisation d&#39;émoticônes et d&#39;autres caractères non présents dans UCS-2.

* La plupart des téléphones ne contiennent pas de glyphes de police pour tous les caractères UCS-2. Les smartphones ont tendance à être en mesure d&#39;afficher des caractères rares assez facilement, mais les téléphones numériques ont généralement un support limité à ce qui est utile dans la langue maternelle du pays dans lequel ils ont été achetés. Si vous voulez utiliser un émoticône ou de l&#39;art ASCII, testez-le sur un large éventail de téléphones avant de l&#39;envoyer. La prévisualisation Adobe Campaign ne simule pas les glyphes manquants et affiche les symboles disponibles dans le navigateur Web.

Le champ `data_coding` indique l&#39;encodage utilisé. Un problème majeur est que la valeur 0 signifie un encodage SMSC par défaut dans la spécification, qui fait généralement référence à GSM7. Vérifiez auprès du partenaire SMSC quel encodage est associé à `data_coding` = 0 qu&#39;Adobe Campaign ne fait que prendre en charge. D&#39;autres valeurs `data_coding` tendent à suivre la spécification, mais la seule façon de s&#39;en assurer est de vérifier auprès du fournisseur SMSC.

La taille maximale d&#39;un message dépend de son encodage. Ce tableau récapitule toutes les informations pertinentes :

| Encodage | data_coding habituel | Taille du message (caractères) | Taille de partie pour SMS à plusieurs parties | Caractères disponibles |
|:-:|:-:|:-:|:-:|:-:|
| GSM 7 | 0 | 160 | 152 | Jeu de caractères de base GSM7 + extension (les caractères étendus prennent 2 caractères) |
| Latin -1 | 3 | 140 | 134 | ISO-8859-1 |
| UCS-2 <br>UTF-16 | 8 | 70 | 67 | Unicode (varie d&#39;un téléphone à l&#39;autre) |

## Paramètres de compte externe SMPP {#SMPP-parameters-external}

Chaque mise en œuvre du protocole SMPP comporte de nombreuses variations. Pour améliorer la compatibilité et l&#39;adaptabilité, de nombreux paramètres sont disponibles pour modifier le comportement du connecteur SMPP. Cette section décrit chaque paramètre et ses effets sur le connecteur.

### Paramètres généraux et routage {#general-parameters-routing}

**Limiter les instances MTA pour ce compte**

Il est possible de définir une limite au nombre d&#39;instances MTA autorisées à se connecter au fournisseur SMPP. Si cette option est cochée, vous pouvez spécifier le nombre maximum de MTA à utiliser.

Cette option permet un contrôle plus précis du nombre de connexions, voir [Connexions simultanées](sms-protocol.md#connection-settings).

Si vous définissez une valeur supérieure au nombre de MTA en cours d&#39;exécution, tous les MTA s&#39;exécuteront normalement : cette option n&#39;est qu&#39;une limite et ne peut pas générer d&#39;autres MTA.

Si vous devez contrôler précisément le nombre de connexions, par exemple les besoins du fournisseur, il est recommandé de toujours définir cette option même si le déploiement actuel comporte le nombre approprié de MTA en cours d&#39;exécution. Si d&#39;autres MTA sont ajoutés par la suite, la limite de connexion reste respectée.

### Paramètres de connexion {#connection-settings}

#### Nom de l&#39;implémentation du SMSC {#smsc-implementation-name}

Définit le nom de l&#39;implémentation SMSC. Il doit être défini sur le nom de votre fournisseur. Contactez l&#39;administrateur ou l&#39;équipe chargée de la délivrabilité pour savoir ce qui doit être ajouté à ce champ. Le rôle de ce champ est décrit dans la section [Gestion des erreurs SR](sms-protocol.md#sr-error-management).

#### Serveur {#server}

Nom DNS ou adresse IP du serveur auquel se connecter.

#### Port {#port}

Port TCP auquel se connecter.

#### Compte {#account}

Nom d&#39;utilisateur de la connexion. Transmis dans le champ `system_id` du PDU BIND.

#### Mot de passe {#password}

Mot de passe de la connexion SMPP. Transmis dans le champ du mot de passe du PDU BIND.

#### Type de système {#system-type}

Valeur transmise dans le champ `system_id` du PDU BIND. Certains fournisseurs ont besoin d&#39;une valeur spécifique ici.

#### Nombre de connexions enfant MTA {#number-mta-child}

Dans Adobe Campaign Classic, il définit le nombre de connexions par enfant MTA.

Le connecteur SMPP étendu Adobe Campaign Classic peut contrôler le nombre de connexions par enfant MTA. Pour contrôler la limite globale des connexions, vous devrez limiter le nombre de processus enfant MTA, ce qui signifie souvent disposer d&#39;une plateforme de mid-sourcing dédiée pour les SMS.

Pour Adobe Campaign Classic, le nombre de connexions de récepteurs et d&#39;émetteurs peut être différent :

* **Connexions de l&#39;émetteur = Nombre de connexions enfant MTA * Nombre de processus enfant MTA * Nombre de MTA </br>(si la réponse automatique est définie) + Nombre de connexions enfant MTA**

Comme nous l&#39;avons suggéré plus haut, le processus SMS d&#39;Adobe Campaign Classic ouvre davantage de connexions d&#39;émetteur si la réponse automatique est activée. Ces connexions supplémentaires sont utilisées pour envoyer les réponses automatiques.

* **Connexions de récepteur = Nombre de connexions enfant MTA**

Si vous configurez des réponses automatiques, le processus SMS ouvrira des paires émetteur/récepteur, augmentant ainsi le nombre de connexions d&#39;émetteur. Si vous n&#39;avez pas configuré de réponse automatique, elle n&#39;ouvrira que les connexions de récepteur.

#### Activer TLS via SMPP {#enable-TLS}

Utilisez TLS pour vous connecter au fournisseur. La connexion sera chiffrée. La connexion TLS est gérée par la bibliothèque OpenSSL.Tout ce qui est applicable à OpenSSL sera vrai pour cette connexion.

#### Activer les traces SMPP en mode verbeux dans le fichier de log {#enable-verbose-log-file}

Ce paramètre permet de vider tout le trafic SMPP dans les fichiers logs. Il est souvent nécessaire d&#39;ajuster les paramètres lors de la configuration initiale. Ceci doit être activé lors de la résolution des problèmes du connecteur et comparé au trafic vu par le fournisseur.

Dans Adobe Campaign Classic, la sortie du log se trouve dans le log MTA pour le trafic lié aux MT et dans le log SMS pour le trafic lié aux MO et SR.

### Paramètre de connexion du récepteur {#receiver-connection}

Cette section est uniquement visible en mode **Transmitter + receiver** séparé.

#### Utiliser des paramètres différents pour le récepteur {#receiver-parameters}

Lorsque la case n&#39;est pas cochée, les mêmes paramètres sont utilisés pour l&#39;émetteur et le récepteur.

Lorsque la case est cochée, les paramètres de la section **Paramètres de connexion** s&#39;appliquent à l&#39;émetteur et les paramètres de la **connexion du récepteur** s&#39;appliquent au récepteur.

**Serveur du récepteur, port, compte, mot de passe, type de système**

Ces paramètres s&#39;appliquent au récepteur en mode Transmitter + receiver. Ils fonctionnent comme la partie émetteur, voir ci-dessus pour plus de détails.

### Paramètres du canal SMPP {#smpp-channel-settings}

#### Autoriser la translitération des caractères {#allow-character-transliteration}

La translitération est le processus de recherche de caractères équivalents à ceux qui sont manquants. Par exemple, le caractère français &quot;ê&quot; (avec un accent circonflexe) est absent de l&#39;encodage GSM, mais il peut être remplacé par &quot;e&quot; sans nuire à la lisibilité.

Si cette case n&#39;est pas cochée, l&#39;encodage du texte échoue s&#39;il ne peut pas coder la chaîne telle quelle.

Si cette case est cochée, l&#39;encodage de texte tentera de convertir la chaîne en une version approximative plutôt que d&#39;échouer. Si certains caractères n&#39;ont pas d&#39;équivalent en encodage de cible, l&#39;encodage de texte échoue.

Pour obtenir une explication plus générale du processus d&#39;encodage, consultez la section [Définir un mapping spécifique du paramètre d&#39;encodage](sms-protocol.md#SMSC-specifics).

#### Stocker les MO entrants dans la base de données {#incoming-mo-storing}

Lorsque l&#39;option est activée, le MO entrant est stocké dans le tableau inSMS de la base de données. Ce tableau peut être interrogé à l&#39;aide de l&#39;activité requête de tout workflow.

Adobe Campaign Classic stocke toujours tous les MO dans la base de données inSMS. Cette option n&#39;est donc pas disponible.

#### Activer les mises à jour des KPI en temps réel pendant le traitement du SR (rapport d&#39;état) {#real-time-kpi}

Lorsqu&#39;ils sont activés, les KPI (indicateurs de performance clés) sont mis à jour en temps réel sur la page de diffusion principale lors de la réception d&#39;un SR d&#39;erreur.

L&#39;inconvénient peut être de faibles performances en raison de la contention de base de données qu&#39;elle génère. Si cette option est désactivée, les statistiques sont mises à jour par le workflow **syncfromexec**, qui s&#39;exécute toutes les 20 minutes.

Adobe Campaign Classic dispose d&#39;un mécanisme entièrement différent pour les KPI (indicateurs de performance clés). Cette option n&#39;est donc pas disponible.

#### Numéro source {#source-number}

Définit l&#39;adresse source par défaut des messages. Ce paramètre ne s&#39;applique que si le numéro source a été laissé vide dans la diffusion.

Par défaut, le champ du numéro source n&#39;est pas transmis.Le fournisseur le remplace donc par le numéro court.

Ceci active la fonction d&#39;écrasement de l&#39;adresse de l&#39;expéditeur / oADC.

#### Numéro court {#short-code}

Indique le numéro court principal du compte. Si plusieurs numéros courts sont utilisés pour ce compte ou si le numéro court est inconnu, laissez ce champ vide.

La spécification d&#39;un numéro court s&#39;avère utile pour deux fonctionnalités :

* La prévisualisation affiche le numéro court si aucun numéro source n&#39;est fourni. Il reflétera le comportement réel sur le téléphone portable.

* Le paramètre de liste bloquée de la fonction de réponse automatique envoie uniquement à la quarantaine l&#39;utilisateur pour un numéro court spécifique.

#### NPI/TON source, NPI/TON destination {#ton-npi}

Le TON (Type de numéro) et le NPI (Indicateur de plan de numérotation) sont décrits à la section 5.2.5 de la [spécification SMPP 3.4](https://smpp.org/SMPP_v3_4_Issue1_2.pdf) (page 117). Ces valeurs doivent être définies en fonction des besoins du fournisseur.

Ils sont transmis tels quels dans les champs `source_addr_ton`, `source_addr_npi`, `dest_addr_ton` et `dest_addr_npi` du `SUBMIT_SM PDU`.

#### Service type {#service-type}

Ce champ est transmis tel quel dans le champ `service_type` du `SUBMIT_SM PDU`. Définissez cette variable en fonction des besoins du fournisseur.

### Débit et délais {#throughput-timeouts}

Ces paramètres contrôlent tous les aspects du timing du canal SMPP. Certains fournisseurs ont besoin d&#39;un contrôle très précis du taux de message, des délais de fenêtre et des délais de reprise. Ces paramètres doivent être définis sur des valeurs correspondant à la capacité du fournisseur et aux conditions indiquées dans son contrat.

#### Fenêtre d&#39;émission {#sending-window}

La fenêtre est le nombre de `SUBMIT_SM PDU` qui peuvent être envoyés sans attendre une correspondance `SUBMIT_SM_RESP`.

Exemple de transmission avec une fenêtre maximale de 4 :

![](assets/do-not-localize/sms_protocol_2.png)

La fenêtre permet d&#39;augmenter le débit lorsque la liaison réseau présente une latence élevée.  La valeur de la fenêtre doit être au moins égale au nombre de SMS/s multiplié par la latence du lien en secondes, de sorte que le connecteur n&#39;attend jamais un `SUBMIT_SM_RESP` avant d&#39;envoyer le message suivant.
Si la fenêtre est trop grande, vous pouvez envoyer plus de messages en doublons en cas de problème de connexion. En outre, la plupart des fournisseurs ont une limite très stricte pour la fenêtre et refusent les messages qui dépassent la limite.

Comment calculer la formule optimale de la fenêtre d&#39;émission :

* Mesurez la latence maximale entre `SUBMIT_SM` et `SUBMIT_SM_RESP`.

* Multipliez cette valeur en secondes jusqu&#39;au débit max de MT. Cela donnera la valeur optimale de la fenêtre d&#39;émission.

Exemple : si 300 SMS/s sont définis dans le débit maximal MT et qu&#39;il y a une latence de 100 ms entre `SUBMIT_SM` et `SUBMIT_SM_RESP` en moyenne, la valeur optimale sera `300×0.1 = 30`.

#### Débit max de MT {#max-mt-throughput}

Nombre maximal de MT par seconde et par connexion. Ce paramètre est strictement appliqué, le MTA n&#39;enverra jamais de messages plus rapidement que cette limite. Il est utile pour les fournisseurs qui nécessitent un ralentissement précis.

Pour connaître la limite de débit totale, multipliez ce nombre par le nombre total de connexions, comme indiqué dans la formule ci-dessus.

0 signifie pas de limite, le MTA enverra le MT aussi vite que possible.

Il est généralement recommandé de maintenir ce paramètre en dessous de 1000, puisqu&#39;il est impossible de garantir un débit précis au-dessus de ce nombre, à moins que l&#39;architecture finale ne soit correctement évaluée et que le fournisseur SMPP ait été spécifiquement demandé. Il peut être préférable d&#39;augmenter le nombre de connexions au-dessus de 1000 MT/s.

#### Temps avant reconnexion {#time-reconnection}

Lorsque la connexion TCP est perdue, le connecteur attend ce nombre de secondes avant d&#39;essayer d&#39;établir une connexion.

#### Délai d&#39;expiration des MT {#expiration-period}

Délai entre `SUBMIT_SM` et son `SUBMIT_SM_RESP` correspondant. Si `RESP` n&#39;est pas reçu à temps, le message sera considéré comme ayant échoué et la politique de nouvelle tentative globale du MTA s&#39;appliquera.

#### Délai d&#39;attente maximal d&#39;un bind {#bind-timeout}

Délai entre la tentative de connexion TCP et la réponse `BIND_*_RESP`. Lorsqu&#39;elle expire, la connexion est fermée par le connecteur Adobe Campaign et il faut attendre le temps avant reconnexion avant de réessayer.

#### Période d&#39;enquire_link {#enquire-link-period}

`enquire_link` est un type spécial de PDU envoyé pour maintenir la connexion en vie. Cette période est en secondes. Le connecteur de campagne n&#39;envoie `enquire_link` que lorsque la connexion est inactive pour économiser la bande passante. Si aucun RESP n&#39;est reçu après deux fois cette période, la connexion est considérée comme étant inactive et un processus de reconnexion est déclenché.

### Spécificités des SMSC {#SMSC-specifics}

Ces paramètres sont des paramètres avancés qui adaptent le connecteur Adobe Campaign à la plupart des particularités d&#39;implémentation SMPP.

**Définir un mapping des encodages spécifique**

Pour plus d&#39;informations, consultez la section [Encodage de texte SMS](sms-protocol.md#sms-text-encoding) pour plus d&#39;informations sur l&#39;encodage de texte.

Ce paramètre permet de définir un mapping de codage personnalisé différent de la spécification. Vous pourrez déclarer une liste d&#39;encodages, ainsi que leur valeur `data_coding`.

Le MTA tentera d&#39;effectuer un encodage en utilisant le premier de la liste. S&#39;il échoue, il essaiera d&#39;utiliser l&#39;encodage suivant sur la liste, etc. Si aucun encodage ne peut être utilisé pour encoder le message, une erreur se produit. Une fois l&#39;encodage trouvé, le MTA crée le `SUBMIT_SM PDU` avec le texte encodé et le champ `data_coding` défini avec la valeur spécifiée dans le tableau.

L&#39;ordre des éléments du tableau est important : les encodages sont des tentatives de haut en bas. Placez l&#39;encodage le moins cher ou le plus recommandé en haut de la liste, puis choisissez des encodages de plus en plus chers.

Veuillez noter que UCS-2 n&#39;échouera jamais car il peut coder tous les caractères pris en charge dans Adobe Campaign et que la longueur maximale d&#39;un SMS UCS-2 est beaucoup plus petite : 70 caractères uniquement.

Vous pouvez également utiliser ce paramètre pour forcer l&#39;utilisation d&#39;un encodage spécifique en ne déclarant que 1 ligne dans le tableau de mapping.

Le mapping par défaut utilisé lorsque la case à cocher n&#39;est pas cochée est équivalent au tableau suivant :

| data_coding | Encodage |
|---|---|
| 0 | GSM |
| 9 | UCS -2 |

Cela signifie que le MTA tente d&#39;encoder le message en GSM. S&#39;il réussit, il l&#39;envoie avec `data_coding` défini sur 0.

Si le message ne peut pas être encodé en GSM, il est encodé en UCS-2 et définit `data_coding` sur 8.

#### Activer message_payload {#enable-message-payload}

Lorsque l&#39;option n&#39;est pas cochée, les SMS longs sont fractionnés par le MTA et envoyés dans plusieurs `SUBMIT_SM PDU` avec l&#39;UDH. Le message est recomposé par le téléphone portable suivant les données UDH.

Si cette option est cochée, un SMS long est envoyé dans un PDU SUBMIT_SM, plaçant le texte dans le champ message_payload facultatif. Consultez la [spécification SMPP](sms-protocol.md#ACS-SMPP-connector) pour plus d&#39;informations à ce sujet.

Si cette fonction est activée, Adobe Campaign ne peut pas comptabiliser les parties SMS individuellement : tous les messages sont comptés comme envoyés en une seule partie.

#### Envoyer le numéro de téléphone complet {#send-full-phone-number}

Si cette case n&#39;est pas cochée, seuls les chiffres du numéro de téléphone sont envoyés au fournisseur (champ `destination_addr` du champ `SUBMIT_SM`). Il s&#39;agit du comportement par défaut puisque l&#39;indicateur de numéro international, généralement un préfixe +, est remplacé par les champs TON et NPI en SMPP.

Si cette case est cochée, le numéro de téléphone est envoyé tel quel, sans prétraitement ni espaces potentiels, préfixe + ou signes dièse/hachage/étoile.

Cette fonctionnalité a également un effet sur le comportement de la fonctionnalité de liste bloquée de réponse automatique : lorsque la case n&#39;est pas cochée, un préfixe + est ajouté aux numéros de téléphone insérés dans le tableau de quarantaine afin de compenser la suppression du préfixe + du numéro de téléphone par le protocole SMPP lui-même.

#### Ignorer la vérification du certificat TLS {#skip-tls}

Lorsque le TLS est activé, ignorez toutes les vérifications de certificat.

Lorsque l&#39;option est cochée, la connexion n&#39;est plus sécurisée, elle ne doit pas être activée en production.

Ceci peut être utile à des fins de débogage ou de test.

Vous pouvez choisir entre trois valeurs différentes pour la validation du certificat :

* Procéder à une vérification complète de la certification (y compris le nom d&#39;hôte), par défaut.
* Ignorer la vérification du nom d&#39;hôte.
* Ignorer la vérification du certificat.

#### Liaison TON/NPI {#bind-ton-npi}

TON (Type de numéro) et NPI (Indicateur de plan de numérotation) décrits à la section 5.2.5 de la [spécification SMPP 3.4](https://smpp.org/SMPP_v3_4_Issue1_2.pdf) (page 117). Ces valeurs doivent être définies selon les besoins du fournisseur.

Ils sont transmis tels quels dans les champs `addr_ton` et `addr_npi` du PDU BIND.

#### Plage d&#39;adresses {#address-range}

Envoyé tel quel dans le champ address_range du PDU BIND. Cette valeur doit être définie selon les besoins du fournisseur.

#### Nombre d&#39;acquittements d&#39;identifiant invalides {#invalid-id}

Limite le nombre d&#39;**identifiants de message non valides** `DELIVER_SM_RESP` pouvant être envoyés pour un seule SR.

**Cette valeur ne doit être utilisée qu&#39;à des fins de résolution des problèmes en tant que solution de contournement** et définie sur 0 dans des conditions normales.

Par exemple, lorsque vous définissez sur 2 :

* Le fournisseur envoie un SR (`DELIVER_SM`) avec l&#39;ID &quot;1234&quot;.

* L&#39;ID &quot;1234&quot; est introuvable dans la base de données.

* Le connecteur comptabilise 1 erreur **ID non valide** pour cet ID, de sorte qu&#39;il envoie `DELIVER_SM_RESP` avec le code d&#39;erreur &quot;Identifiant du message non valide&quot; (comportement normal).

* Le fournisseur réessaye le même SR avec l&#39;ID &quot;1234&quot;.

* L&#39;ID &quot;1234&quot; est toujours introuvable dans la base de données.

* Le connecteur comptabilise 2 erreurs **ID non valide** pour cet ID, de sorte qu&#39;il envoie `DELIVER_SM_RESP` &quot;OK&quot;, même s&#39;il n&#39;a pas été traité correctement.

* Cette fonctionnalité est destinée à vider les tampons SR côté fournisseur lorsque des blocs SR non valides sont légitimes pour que les messages ne puissent pas être traités.

La définition de ce champ sur 0 désactive le mécanisme où **ID de message non valide** est toujours renvoyé, c&#39;est un comportement normal.

Si ce champ est défini sur 1, le connecteur répond toujours &quot;OK&quot;, même si l&#39;ID n&#39;est pas valide. Cette valeur doit être définie sur 1 uniquement sous supervision, à des fins de résolution des problèmes et pour une durée minimale, par exemple pour récupérer d&#39;un problème côté fournisseur.

#### Expression régulière d&#39;extraction de l&#39;ID dans le SR {#regex-extraction}

Le format SR n&#39;est pas strictement appliqué par la spécification du protocole SMPP. Il ne s&#39;agit que d&#39;une recommandation décrite à l&#39;[Annexe B](sms-protocol.md#sr-error-management) (page 167) de la spécification. Certains implémenteurs de SMPP formattent ce champ différemment, de sorte qu&#39;Adobe Campaign a besoin d&#39;un moyen d&#39;extraire le champ correct.

Par défaut, il capture jusqu&#39;à 10 caractères alphanumériques après `id:`.

L&#39;expression régulière doit comporter exactement un groupe de capture avec une partie entre parenthèses. Les parenthèses doivent entourer la partie ID. Le format d&#39;expression régulière est PCRE.

Lors de la modification de ce paramètre, veillez à inclure le plus de contexte possible pour éviter les faux triggers. S&#39;il existe des préfixes spécifiques, tels que `id:` dans la norme, incluez-les dans l&#39;expression régulière. Utilisez également autant que possible des délimiteurs de mots (\b) pour éviter de capturer du texte au milieu d&#39;un mot.

Ne pas inclure suffisamment de contexte dans l&#39;expression régulière peut introduire un petit défaut de sécurité : le contenu réel du message peut être inclus dans le SR. Si vous ne faites correspondre qu&#39;un format d&#39;ID spécifique sans contexte, par exemple un UUID, il se peut qu&#39;il analyse le contenu du texte réel, par exemple un UUID incorporé dans le champ de texte, au lieu de l&#39;ID.

#### Expression régulière appliquée pour déterminer le statut de réussite / erreur {#regex-applied}

Lorsque des messages avec une combinaison de champs &quot;stat&quot; / &quot;err&quot; inconnue sont détectés, ces expressions régulières sont appliqués sur le champ &quot;stat&quot; pour déterminer si le SR a été un succès ou une erreur. Les SR avec des valeurs &quot;stat&quot; qui ne correspondent à aucune de ces expressions régulières sont ignorés.

Par défaut, les valeurs &quot;stat&quot; commençant par `DELIV`, par ex.`DELIVRD` dans l&#39;[Annexe B](sms-protocol.md#sr-error-management), seront considérées comme délivrées avec succès et toutes les valeurs &quot;stat&quot; qui correspondent à des erreurs, p.ex.`REJECTED`, `UNDELIV`, sont considérées comme des erreurs.

#### Format de l&#39;ID dans l&#39;acquittement MT {#id-format-mt}

Indique le format de l&#39;ID renvoyé dans le champ `message_id` du `SUBMIT_SM_RESP PDU`.

* **Ne pas modifier** : l&#39;ID est stocké tel quel dans la base de données, sous la forme de texte encodé en ASCII. Aucun prétraitement ni filtrage n&#39;est effectué.

* **Nombre décimal** : l&#39;ID doit être un nombre décimal au format ASCII. Les espaces de début et de fin et les zéros de début sont supprimés lorsque ce paramètre est utilisé.

* **Nombre hexadécimal** : l&#39;ID doit être un nombre hexadécimal au format ASCII, sans 0x ni h à la fin.L&#39;ID est ensuite converti en nombre décimal avant d&#39;être stocké dans la base de données.

* **Chaîne hexadécimale** : l&#39;ID doit être un texte encodé en ASCII qui est lui-même une chaîne d&#39;octets encodés en hexadécimal. Par exemple, dans le PDU, vous trouverez `0x34 0x31 0x34 0x32 0x34 0x33`, qui se traduit par &quot;414243&quot; en ASCII. Cette chaîne est alors décodée sous la forme d&#39;une chaîne hexadécimale d&#39;octets et vous obtenez &quot;ABC&quot; en conséquence : vous stockerez l&#39;ID &quot;ABC&quot; dans la base de données.

#### Format de l&#39;ID dans le SR {#id-format-sr}

Ceci indique le format de l&#39;ID capturé par l&#39;expression régulière `Extraction` de l&#39;ID dans le SR. Les valeurs ont la même signification et le même comportement que le format en MT ci-dessus.

**L&#39;identifiant du SR ou le code d&#39;erreur dans un champ optionnel**

>[!NOTE]
>
>Disponible uniquement dans le connecteur SMPP étendu Adobe Campaign Classic.

Si cette case est cochée, le contenu des champs facultatifs est ajouté au texte traité par les expressions régulières ci-dessus. Le texte aura le format `0xTAG:VALUE`, `0xTAG` étant la valeur hexadécimale de 4 chiffres de la balise en majuscules, par exemple `0x002E`.

Par exemple, vous pouvez capturer l&#39;identifiant dans le champ `receipted_message_id`. Pour cela, activez cette case à cocher et le texte suivant est ajouté au statut :

```
0x001E:05e3299e-8d37-49d0-97c6-8e4fe60c7739
```

Dans cet exemple, 0x001E est la balise du champ facultatif et UUID est la valeur du champ.

Pour capturer cette valeur, vous pouvez désormais définir l&#39;expression régulière suivante dans l&#39;expression régulière d&#39;extraction de l&#39;ID dans le champ de SR :

```
\b0x001E:([0-9a-f]{8}-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{12})\b
```

>[!IMPORTANT]
>
>Vous pouvez uniquement capturer les champs facultatifs contenant des valeurs de texte (ASCII/UTF-8). En particulier, les champs binaires ne peuvent pas être capturés de manière fiable avec le système d&#39;expressions régulières actuel.

**Stocker l&#39;identifiant du SR ou le code d&#39;erreur dans un champ de texte**

Si cette case est cochée, le champ **Texte** est conservé pendant le traitement du texte de statut du SR.

Cela s&#39;avère utile si le fournisseur place des données importantes dans ce champ, telles que l&#39;ID ou le statut. En règle générale, ce champ peut être ignoré en toute sécurité puisqu&#39;il peut contenir du texte avec un codage non ASCII et perturber le traitement d&#39;expression régulière.

L&#39;activation de cette option peut introduire un très petit défaut de sécurité si l&#39;expression régulière `Extraction` de l&#39;ID dans le champ SR n&#39;est pas suffisamment précise. Le contenu du champ **Texte** peut être analysé en tant qu&#39;ID et un agresseur peut l&#39;utiliser pour injecter des identifiants falsifiés, ce qui peut entraîner un déni de service partiel.

**Balise d&#39;ID de service**

Permet d&#39;ajouter un fichier TLV personnalisé. Ce champ définit la partie balise. La valeur peut être personnalisée par diffusion dans la valeur **Identifiant service ou programme** dans les paramètres avancés de la diffusion.

Ce paramètre permet uniquement d&#39;ajouter une option TLV par message.

### Réponse automatique aux MO   {#automatic-reply}

>[!IMPORTANT]
>
>Dans Adobe Campaign Classic et avec une architecture hybride, l’application d’une réponse automatique pour le connecteur SMPP étendu nécessite l’ajout d’un accès en écriture pour l’opérateur mid sur le dossier **Compte externe**.

Cette fonctionnalité permet de répondre rapidement du texte au MO et de gérer l&#39;envoi de numéro court à la liste bloquée.

Les colonnes **Mot-clé** et **Numéro court** définissent les conditions pour déclencher la réponse automatique. Si les deux champs correspondent, le MO est envoyé et l&#39;action supplémentaire est déclenchée. Pour spécifier un caractère de remplacement, vous devez laisser le champ vide. Le mot-clé correspond au premier mot alphanumérique du texte MO, en ignorant la ponctuation et les espaces de début. Cela signifie que le champ **Mot-clé** ne peut pas contenir d&#39;espaces et doit être un seul mot.

Le paramètre **Mot-clé** est un préfixe. Par exemple, si vous spécifiez &quot;AD&quot;, il correspondra à &quot;AD&quot;, &quot;ADAPT&quot; et &quot;ADOBE&quot;. Si vous avez plusieurs mots-clés avec un préfixe commun, vous devez prêter attention à l&#39;ordre car les mots-clés sont traités de haut en bas.

La colonne **Répondre** correspond au texte à répondre. Aucune personnalisation n&#39;est disponible dans ce champ. Si vous laissez ce champ vide, aucun message ne sera répondu, mais l&#39;action supplémentaire sera quand même déclenchée.

La colonne **Action supplémentaire** fournit une action supplémentaire lorsque **Mot-clé** et **Numéro court** correspondent tous les numéros courts vides. Vous pouvez envoyer en quarantaine ou supprimer de la quarantaine, la valeur &quot;aucune réponse au texte&quot;. Si vous spécifiez une **action supplémentaire** mais que le champ **Répondre** reste vide, l&#39;action est exécutée mais aucune réponse n&#39;est envoyée. La quarantaine est appliquée uniquement pour le numéro court spécifié ou pour tous les numéros courts si le champ est vide.

>[!IMPORTANT]
>
>Le paramètre d&#39;envoi du numéro de téléphone complet a un impact sur le comportement du mécanisme de quarantaine de réponse automatique : si l&#39;envoi du numéro de téléphone complet n&#39;est pas vérifié, le numéro de téléphone mis en quarantaine sera précédé d&#39;un signe plus (&quot;+&quot;) afin de le rendre compatible avec le format de numéro de téléphone international.

Toutes les entrées du tableau sont traitées dans l&#39;ordre spécifié, jusqu&#39;à ce qu&#39;une règle corresponde. Si plusieurs règles correspondent à un MO, seule la règle la plus élevée est appliquée.

## Paramètres du modèle de diffusion SMS {#sms-delivery-template-parameters}

Certains paramètres peuvent être définis par modèle de diffusion.

### À partir du champ {#from-field}

Ce champ est facultatif. Il permet d&#39;écraser l&#39;adresse de l&#39;expéditeur (oADC). Le contenu de ce champ est placé dans le champ `source_addr` du `SUBMIT_SM PDU`.

Le champ est limité à 21 caractères par la spécification SMPP, mais certains fournisseurs peuvent autoriser des valeurs plus longues. Notez également que des restrictions très strictes peuvent être appliquées dans certains pays, par exemple la longueur, le contenu, les caractères autorisés.

### Paramètres de diffusion {#delivery-parameters}

#### Nombre maximal de SMS par message {#maximum-sms}

Ce paramètre ne fonctionne que si le paramètre **Payload du message** est désactivé. Si le message nécessite plus de SMS que cette valeur, une erreur est déclenchée.

Le protocole SMS limite les SMS à 255 parties, mais certains téléphones portables ont du mal à assembler de longs messages avec plus de 10 parties environ, la limite dépend du modèle exact. Nous vous conseillons de ne pas dépasser 5 parties par message.

En raison du fonctionnement des messages personnalisés dans Adobe Campaign, la taille des messages peut varier. Le fait d&#39;avoir beaucoup de messages longs pourrait augmenter les coûts d&#39;envoi.

#### Mode de transmission {#transmission-mode}

Ce champ indique le type de SMS que vous souhaitez transférer : messages normaux ou flash, stockés sur le mobile ou la carte SIM.

Ce paramètre est transmis dans le champ facultatif `dest_addr_subunit` du `SUBMIT_SM PDU`.

* L&#39;option **Non spécifié** n&#39;envoie aucun champ facultatif dans le PDU.

* **Flash** définit la valeur sur 1. Cela envoie un message Flash qui s&#39;affiche sur le mobile et n&#39;est pas stocké en mémoire.

* **Normal** définit la valeur sur 0. Cela envoie un message normal.

* **Enregistrer sur mobile** définit la valeur sur 2. Cela dit au téléphone de stocker le SMS dans la mémoire interne.

* **Enregistrer sur le terminal** définit la valeur sur 3. Cela indique au téléphone de stocker le SMS dans la carte SIM.

#### Période de validité {#validity-period}

La période de validité est transmise dans le champ `validity_period` du `SUBMIT_SM PDU`. La date est toujours formatée au format des heures UTC absolu, le champ de date se termine par &quot;00+&quot;.

## Connecteur SMPP générique étendu {#acc-extended-connector}

![](assets/do-not-localize/sms_protocol_4.png)

Les flèches représentent les flux de données.

Lors de l&#39;envoi de fragments de diffusion, le MTA génère des enfants MTA. Le nombre de processus enfant MTA est dynamique et dépend d&#39;une configuration dans le fichier serverConf.xml. Chaque enfant MTA instancie le connecteur `CSmppConnectorWorker` qui se connecte au fournisseur SMPP. Les connexions sont maintenues actives tant que l&#39;enfant MTA est en vie, ce qui est également configurable dans serverConf.xml.

Le processus SMS ne traite que le SR, se connecte au fournisseur et laisse la connexion ouverte. Le processus se reconnecte toutes les 10 minutes pour recharger de nouveaux paramètres, ce qui est normal.

### Correspondance des entrées MT, SR et broadlog {#matching-mt}

Une table `nmsProviderMsgId` intermédiaire est utilisée pour stocker temporairement les données MT et SR avant la validation asynchrone sur le broadlog.

La table `nmsProviderMsgId` comprend 3 groupes de colonnes :

* Colonnes mises à jour lorsqu&#39;un MT est envoyé et fait l&#39;objet d&#39;un accusé de réception : `iBroadLogId`, `iDeliveryId`

* Colonnes mises à jour lors de la réception d&#39;un SR : `iMsgId`, `iStatus`

* Colonnes toujours mises à jour : `tsCreated`, `sProviderId`

Une fois le traitement des MT et SR terminé, vous devriez avoir des lignes complètes, avec des informations concernant à la fois le broadlog et l&#39;état.

Ici, `iMsgId` est lié à la table `nmsBroadLogMsg`, ce qui indique le message d&#39;état/d&#39;erreur complet.

Le processus SMS recherche toutes les minutes des lignes complètes, puis les traite de façon asynchrone :

* La ligne complète est lue.
* Le processus SMS calcule le nom de la table de broadlog en fonction du mapping de diffusion.
* Le processus SMS met à jour la table du broadlog avec l&#39;identifiant du message et l&#39;état.

**Débit et connexions parallèles**

Chaque enfant MTA crée un nombre configurable de connexions, de sorte que la limite du nombre d&#39;enfants MTA restreint le nombre de connexions. Comme les processus enfant MTA et le trafic sont corrélés, il existe un certain contrôle bien qu&#39;encore un peu imprévisible.

## Avant la mise en ligne {#checklist}

Cette liste de contrôle fournit une liste de choses que vous devriez vérifier avant la mise en ligne. Une configuration incomplète peut entraîner de nombreux problèmes.

### Rechercher les conflits de compte externe {#external-account-conflict}

Vérifiez que vous n&#39;avez pas de vieux comptes externes SMS. Si vous laissez le compte test désactivé, il existe un risque qu&#39;il soit réactivé sur le système de production et qu&#39;il génère des conflits potentiels.

Si plusieurs comptes de la même instance Adobe Campaign se connectent au même fournisseur, contactez ce dernier pour vérifier qu&#39;il distingue effectivement les connexions entre ces comptes. La présence de plusieurs comptes avec le même nom d&#39;utilisateur nécessite une configuration supplémentaire.

### Activer les traces SMPP de verbose lors des vérifications {#enable-verbose}

Vous devez toujours activer les traces SMPP de verbose lors des vérifications.
Même si vous ne pouvez pas vérifier vous-même les logs, il sera plus facile pour l&#39;[Assistance clientèle d&#39;Adobe](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) de vous aider.

### Tester votre SMS {#test}

* **Envoyer des SMS avec toutes sortes de caractères**
Si vous devez envoyer des SMS avec des caractères non GSM ou non ASCII, essayez d&#39;envoyer des messages avec autant de caractères différents que possible. Si vous définissez un tableau de mapping de caractères personnalisé, envoyez au moins un SMS pour toutes les valeurs `data_coding` possibles.

* **Vérifier que les SR sont correctement traités**
Le SMS doit être marqué comme reçu dans le log de diffusion. Le log de diffusion doit réussir et se présenter comme suit :
  `SR yourProvider stat=DELIVRD err=000|#MESSAGE`
Vérifiez que vous avez modifié le nom du fournisseur de diffusions. Le log de diffusion ne doit jamais contenir **SR Generic** sur les environnements de production.

* **Vérifier que les MO sont traités**
Si vous devez traiter les MO (réponses automatiques, stockage de MO dans la base de données, etc.) essayez de faire des tests. Envoyez quelques SMS pour tous les mots-clés de réponse automatique et vérifiez si la réponse est assez rapide, pas plus de quelques secondes.
Archivez le journal auquel Adobe Campaign répond avec un `DELIVER_SM_RESP` (command_status=0) réussi.

### Vérifier les PDU {#check-pdus}

Même si les messages semblent avoir réussi, il est important de vérifier que les PDU sont correctement formatés.

Cette étape est nécessaire lors de la connexion avec un fournisseur qui n&#39;était pas connecté à Adobe Campaign auparavant.

#### BIND {#bind}

Vérifiez que les `BIND_* PDUs` sont correctement envoyés. La chose la plus importante à vérifier est que le fournisseur renvoie toujours un `BIND_*_RESP PDUs` (command_status = 0) réussi.

Vérifiez qu&#39;il n&#39;y a pas trop de `BIND_* PDU`.S&#39;il y en a trop, cela peut indiquer que la connexion est instable. Pour plus d&#39;informations, consultez la section [Problèmes liés aux connexions instables](sms-protocol.md#issues-unstable-connection).

#### ENQUIRE_LINK {#enquire-link-pdus}

Vérifiez que les `ENQUIRE_LINK PDU` sont échangés régulièrement lorsque la connexion est inactive.

**SUBMIT_SM / DELIVER_SM**

Envoyez un message, puis recherchez dans les journaux les `SUBMIT_SM`, `SUBMIT_SM_RESP`, `DELIVER_SM` et `DELIVER_SM_RESP PDU` correspondants.

Avec le `SUBMIT_SM PDU` :

* Vérifiez que `data_coding` est correct, 0 par défaut.
* Vérifiez que `short_message` est correctement encodé. Essayez de le décoder à l&#39;aide d&#39;un convertisseur hexadécimal qui prend en charge plusieurs encodages.

Avec le `SUBMIT_SM_RESP PDU` :

* Vérifiez qu&#39;il a réussi, command_status = 0.
* Vérifiez que son corps contient un ID correctement formaté suivi d&#39;un octet &quot;0&quot;.

Avec le `DELIVER_SM PDU` :

* Décodez le champ hexadécimal `short_message`.
* Vérifiez avec un outil de vérification d&#39;expression régulière que l&#39;expression régulière définie dans l&#39;expression régulière `Extraction` de l&#39;identifiant dans le SR renvoie exactement un groupe de capture et qu&#39;il capture l&#39;identifiant entier dans le message.
* Vérifiez que l&#39;ID extrait correspond à celui dans `SUBMIT_SM_RESP`.
* Vérifiez que l&#39;expression régulière définie dans l&#39;expression régulière `Extraction` du statut dans le SR renvoie le contenu du champ &quot;stat&quot;.
* Vérifiez que l&#39;expression régulière définie dans l&#39;expression régulière `Extraction` de l&#39;erreur dans le SR renvoie le contenu du champ &quot;err&quot;.

Avec le `DELIVER_SM_RESP PDU` :

* Vérifiez qu&#39;il a été envoyé rapidement après avoir reçu le `DELIVER_SM PDU`, généralement moins d&#39;une seconde.
* Vérifiez qu&#39;il a réussi, command_status = 0.

### Vérifiez auprès de votre fournisseur {#provider}

Même si votre SMS réussit, contactez le fournisseur pour voir si tout est en ordre.

### Désactiver les traces SMPP de verbose {#disable-verbose}

Une fois toutes les vérifications terminées, la dernière chose à faire est de **désactiver les traces SMPP de verbose** pour ne pas générer trop de journaux. Vous pouvez les réactiver à des fins de résolution des problèmes, même sur les systèmes de production.
