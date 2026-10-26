---
product: campaign
title: Protocole et paramètres du connecteur SMS
description: En savoir plus sur le connecteur SMS et comment le configurer
feature: SMS
role: Developer
exl-id: fded088a-11a2-4b87-a368-7b197334aca4
TQID: 'https://experienceleague.adobe.com/-e39I2kK3veYtZTufN0ZZrnZPAAco47dU8HFlCtlIxY'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
    internal-label: Campaign Email Designer
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
    internal-label: Prepare and test messages
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
    internal-label: Email messaging
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
    internal-label: Email design
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
    internal-label: A/B testing
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
    internal-label: Manage deliverability
  - id: b1bd1421-1927-4c59-9bc6-ce292360e43b
    internal-label: SMS Messaging
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
source-git-commit: d7e5f68c0d2e0b94fd5cfdf2981bed29f33d9f62
workflow-type: ht
source-wordcount: '4785'
ht-degree: 100%
---
# Protocole et paramètres du connecteur SMS {#sms-connector-protocol}

>[!NOTE]
>
>Dans ce document, toutes les références au protocole, aux noms de champ et aux valeurs se rapportent à la [spécification SMPP 3.4](https://smpp.org/SMPP_v3_4_Issue1_2.pdf).
>

Dans le cadre de la transition de Campaign v7 vers v8, la documentation de Campaign Classic a été rationalisé et réorganisé. Les fonctionnalités communes sont désormais disponibles exclusivement dans le jeu de documentation de Campaign v8. Pour en savoir plus sur les paramètres du connecteur SMS, consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/send/sms/config-sms/smpp-external-account){target=_blank}.

[![image](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/send/sms/config-sms/smpp-external-account){target=_blank}

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

## Protocole SMPP {#smpp-protocol}

Adobe Campaign Classic prend en charge le protocole SMPP version 3.4. Il s’agit d’un protocole répandu qui permet d’envoyer des SMS à un fournisseur (SMSC) et de recevoir des SMS ainsi que des accusés de réception. Consultez à ce sujet la [documentation SMPP](https://smpp.org/SMPP_v3_4_Issue1_2.pdf).

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

Un `SUBMIT_SM_RESP PDU` réussi déclenche le statut du message &quot;envoyé&quot; dans le log d&#39;envoi tandis qu&#39;un `DELIVER_SM (SR) PDU` réussi déclenche le statut du message &quot;reçu&quot;.

### Aspects liés à la sécurité {#security-aspects}

Le protocole proprement dit n’est pas chiffré. La plupart des fournisseurs mettent en œuvre une variante d&#39;IP sur la liste autorisée, de sorte que les adresses IP du serveur Adobe Campaign doivent être déclarées au fournisseur.

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

* **data_coding** : indique le codage utilisé dans le champ de texte. Pour plus d’informations, consultez la section [Encodage des SMS](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/send/sms/sms-channel#sms-text-encoding){target="_blank"} (documentation de Campaign v8).

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

### Limitation du débit et fenêtrage {#throughput-capping}

La plupart des fournisseurs exigent une limite de débit pour chaque connexion SMPP. Pour ce faire, il est possible d&#39;établir un certain nombre de SMS dans le compte externe. Notez que le ralentissement du débit se produit par connexion, le débit effectif total est la limite par connexion multipliée par le nombre total de connexions. Ceci est détaillé dans la section [Connexions simultanées](sms-protocol.md#connection-settings).

Pour atteindre le débit maximal possible, vous devez affiner la fenêtre d&#39;émission maximale. La fenêtre d&#39;émission est le nombre de `SUBMIT_SM PDU` qui peuvent être envoyés sans attendre un `SUBMIT_SM_RESP`. Pour plus d’informations, consultez la section [Paramètres de la fenêtre d’envoi](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/send/sms/config-sms/smpp-external-account#smpp-delays){target="_blank"} (documentation de Campaign v8).

### Gestion des SR et des erreurs (&quot;Annexe B&quot;) {#sr-error-management}

Le protocole SMPP définit des erreurs synchrones standard dans `RESP PDU`, mais il ne définit pas de codes d&#39;erreur pour SR. Chaque fournisseur utilise ses propres codes d&#39;erreur avec leur signification.

Une recommandation est faite dans la section de l&#39;Annexe B de la [spécification du protocole SMPP](https://smpp.org/SMPP_v3_4_Issue1_2.pdf) (page 167), mais sans indiquer les codes d&#39;erreur réels ni leur signification.

Pour s&#39;adapter à la gestion des erreurs, le système de messagerie broadlog d&#39;Adobe Campaign a été exploité pour indiquer correctement les erreurs et leur sévérité (hard, soft, etc.).

Comme mentionné ci-dessus, il existe deux types d&#39;erreurs :

* réponses synchrones dans le `SUBMIT_SM_RESP` qui surviennent immédiatement après l&#39;envoi du message au SMSC
* accusés de réception qui peuvent s&#39;afficher beaucoup plus tard lorsque le mobile a reçu le message ou lorsque le message a expiré. Dans ce cas, l&#39;erreur se trouve dans un SR.

Lorsqu&#39;un SR est reçu, le statut et l&#39;erreur se trouvent dans son champ `short_message` (exemple pour les mises en œuvre conformes à l&#39;Annexe B). Le champ `short_message` du PDU est souvent appelé le **champ de texte**, car il contient du texte en MT. En cas de SR, il contient des informations techniques ainsi qu’un sous-champ nommé **Texte**. Ces deux champs sont différents et `short_message` contiennent en fait le champ **Texte** et d&#39;autres informations.

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

### Exemple de traitement SR dans un SMPP générique étendu Adobe Campaign Classic {#sr-processing}

Cet exemple montre comment afficher le cas d&#39;une mise en œuvre suivant la recommandation de l&#39;Annexe B, les valeurs par défaut dans le compte externe et un SMS MT réussi.

```
id:1234567890 sub:001 dlvrd:001 submit date:1608011415 done date:1608011417 stat:DELIVRD err:000 Text:Hello Adobe world
```

Tout d’abord, l’expression régulière `id extraction` est appliquée pour extraire l’identifiant et le réconcilier avec le MT correspondant.

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

>[!NOTE]
>
>L’engagement de l’équipe chargée de la délivrabilité repose sur un contrat. La clientèle doit contacter son représentant ou sa représentante Adobe pour obtenir des informations relatives à l’engagement en matière de délivrabilité.

#### Nombre de connexions enfant MTA {#number-mta-child}

Dans Adobe Campaign Classic, il définit le nombre de connexions par enfant MTA.

Le connecteur SMPP étendu Adobe Campaign Classic peut contrôler le nombre de connexions par enfant MTA. Pour contrôler la limite globale des connexions, vous devrez limiter le nombre de processus enfant MTA, ce qui signifie souvent disposer d&#39;une plateforme de mid-sourcing dédiée pour les SMS.

Pour Adobe Campaign Classic, le nombre de connexions de récepteurs et d&#39;émetteurs peut être différent :

* **Connexions de l&#39;émetteur = Nombre de connexions enfant MTA * Nombre de processus enfant MTA * Nombre de MTA (si la réponse automatique est définie) * Nombre de connexions enfant MTA**

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

#### Stocker les MO entrants dans la base de données {#incoming-mo-storing}

Lorsque l&#39;option est activée, le MO entrant est stocké dans le tableau inSMS de la base de données. Ce tableau peut être interrogé à l&#39;aide de l&#39;activité requête de tout workflow.

Adobe Campaign Classic stocke toujours tous les MO dans la base de données inSMS. Cette option n&#39;est donc pas disponible.

#### Activer les mises à jour des KPI en temps réel pendant le traitement du SR (rapport d&#39;état) {#real-time-kpi}

Lorsqu&#39;ils sont activés, les KPI (indicateurs de performance clés) sont mis à jour en temps réel sur la page de diffusion principale lors de la réception d&#39;un SR d&#39;erreur.

L&#39;inconvénient peut être de faibles performances en raison de la contention de base de données qu&#39;elle génère. Si cette option est désactivée, les statistiques sont mises à jour par le workflow **syncfromexec**, qui s&#39;exécute toutes les 20 minutes.

Adobe Campaign Classic dispose d&#39;un mécanisme entièrement différent pour les KPI (indicateurs de performance clés). Cette option n&#39;est donc pas disponible.

#### Numéro court {#short-code}

Indique le numéro court principal du compte. Si plusieurs numéros courts sont utilisés pour ce compte ou si le numéro court est inconnu, laissez ce champ vide.

La spécification d&#39;un numéro court s&#39;avère utile pour deux fonctionnalités :

* La prévisualisation affiche le numéro court si aucun numéro source n&#39;est fourni. Il reflétera le comportement réel sur le téléphone portable.

* Le paramètre de liste bloquée de la fonction de réponse automatique envoie uniquement à la quarantaine l&#39;utilisateur pour un numéro court spécifique.

### Spécificités des SMSC {#SMSC-specifics}

Ces paramètres sont des paramètres avancés qui adaptent le connecteur Adobe Campaign à la plupart des particularités d&#39;implémentation SMPP.

#### Ignorer la vérification du certificat TLS {#skip-tls}

Lorsque le TLS est activé, ignorez toutes les vérifications de certificat.

Lorsque l&#39;option est cochée, la connexion n&#39;est plus sécurisée, elle ne doit pas être activée en production.

Ceci peut être utile à des fins de débogage ou de test.

Vous pouvez choisir entre trois valeurs différentes pour la validation du certificat :

* Procéder à une vérification complète de la certification (y compris le nom d&#39;hôte), par défaut.
* Ignorer la vérification du nom d&#39;hôte.
* Ignorer la vérification du certificat.

#### Expression régulière appliquée pour déterminer le statut de réussite / erreur {#regex-applied}

Lorsque des messages avec une combinaison de champs &quot;stat&quot; / &quot;err&quot; inconnue sont détectés, ces expressions régulières sont appliqués sur le champ &quot;stat&quot; pour déterminer si le SR a été un succès ou une erreur. Les SR avec des valeurs &quot;stat&quot; qui ne correspondent à aucune de ces expressions régulières sont ignorés.

Par défaut, les valeurs &quot;stat&quot; commençant par `DELIV`, par ex.`DELIVRD` dans l&#39;[Annexe B](sms-protocol.md#sr-error-management), seront considérées comme délivrées avec succès et toutes les valeurs &quot;stat&quot; qui correspondent à des erreurs, p.ex.`REJECTED`, `UNDELIV`, sont considérées comme des erreurs.

#### Format de l&#39;ID dans l&#39;acquittement MT {#id-format-mt}

Indique le format de l&#39;ID renvoyé dans le champ `message_id` du `SUBMIT_SM_RESP PDU`.

* **Ne pas modifier** : l&#39;ID est stocké tel quel dans la base de données, sous la forme de texte encodé en ASCII. Aucun prétraitement ni filtrage n&#39;est effectué.

* **Nombre décimal** : l&#39;ID doit être un nombre décimal au format ASCII. Les espaces de début et de fin et les zéros de début sont supprimés lorsque ce paramètre est utilisé.

* **Nombre hexadécimal** : l’ID doit être un nombre hexadécimal au format ASCII, sans 0x au début ni h à la fin. L’ID est ensuite converti en nombre décimal avant d’être stocké dans la base de données.

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

**Balise d&#39;ID de service**

Permet d&#39;ajouter un fichier TLV personnalisé. Ce champ définit la partie balise. La valeur peut être personnalisée par diffusion dans la valeur **Identifiant service ou programme** dans les paramètres avancés de la diffusion.

Ce paramètre permet uniquement d&#39;ajouter une option TLV par message.

### Réponse automatique aux MO {#automatic-reply}

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
>Le paramètre d’envoi du numéro de téléphone complet a un impact sur le comportement du mécanisme de quarantaine de réponse automatique : si l’envoi du numéro de téléphone complet n’est pas vérifié, le numéro de téléphone mis en quarantaine sera précédé d’un signe plus (« + ») afin de le rendre compatible avec le format de numéro de téléphone international.

Toutes les entrées du tableau sont traitées dans l&#39;ordre spécifié, jusqu&#39;à ce qu&#39;une règle corresponde. Si plusieurs règles correspondent à un MO, seule la règle la plus élevée est appliquée.

## Paramètres du modèle de diffusion SMS {#sms-delivery-template-parameters}

Certains paramètres peuvent être définis par modèle de diffusion.

### Paramètres de diffusion {#delivery-parameters}

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
