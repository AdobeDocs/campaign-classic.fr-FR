---
product: campaign
title: Envoi, surveillance et suivi de SMS
description: Découvrez comment envoyer, surveiller et suivre des SMS dans Campaign
feature: SMS
role: User
exl-id: 442672ee-5037-49b7-a06f-3a99920ce2b6
source-git-commit: 62ab16b206563aa25b8943e606d03a3184eb00db
workflow-type: ht
source-wordcount: '896'
ht-degree: 100%

---

# Configuration supplémentaire{#sms-properties}

<!--
## Send SMS messages {#sending-sms-messages}

To approve your message and send it to the recipients of the delivery being created, click **[!UICONTROL Send]**.

The detailed process when validating and sending a delivery is presented in the sections below:

* [Validate the delivery](steps-validating-the-delivery.md)
* [Send the delivery](steps-sending-the-delivery.md)
-->

## Paramètres avancés {#advanced-parameters}

Le bouton **[!UICONTROL Propriétés]** permet d&#39;accéder aux paramètres avancés de la diffusion. Les paramètres spécifiques à l&#39;envoi des SMS sont regroupés dans la section **[!UICONTROL Paramètres SMS]** de l&#39;onglet **[!UICONTROL Envoi]**.

Les options disponibles sont les suivantes :

* **Adresse expéditeur** : permet de personnaliser le nom de l’expéditeur de la diffusion en utilisant une chaîne de caractères alphanumériques limités à onze caractères. Le champ ne doit pas être exclusivement composé de chiffres. Vous pouvez définir une condition pour afficher, par exemple, différents noms selon l’indicatif régional du destinataire :

  ```
  <% if( String(recipient.mobilePhone).indexOf("+1") == 0){ %>NeoShopUS<%} else {%>NeoShopWorld<%}%>
  ```

  >[!IMPORTANT]
  >
  >Vérifiez la loi en vigueur dans votre pays concernant la modification du nom de l&#39;expéditeur. Vérifiez également auprès de votre opérateur s&#39;il propose cette fonctionnalité.

* **Mode de transmission** : moyen d&#39;acheminement des messages par SMS.
* **Priorité** : niveau d&#39;importance attribué à un message. La priorité **[!UICONTROL Normale]** est sélectionnée par défaut. Renseignez-vous auprès de votre fournisseur pour connaître les tarifs d&#39;un SMS envoyé en priorité **[!UICONTROL Haute]**.
* **Type d&#39;application** : choisissez l&#39;application que vous souhaitez attribuer à votre diffusion par SMS. L&#39;option **[!UICONTROL Marketing Direct]** est sélectionnée par défaut et constitue l&#39;utilisation la plus courante.

**Paramètres propres au connecteur NetSize**

![](assets/s_user_mobile_sms_adv_netsize.png)

* **Utiliser plusieurs SMS pour un seul message** : permet d&#39;envoyer un message de plus de 160 caractères via plusieurs SMS.

**Paramètres propres à un connecteur SMPP**

![](assets/s_user_mobile_sms_adv_smpp.png)

* **Nombre maximal de SMS par message** : cette option vous permet de régler le nombre de SMS à utiliser pour envoyer un message. Si le nombre est fixé à 0, vous pouvez utiliser un SMS pour diffuser votre message par SMS. Si le nombre de SMS est fixé à 1 ou 2 par exemple, et que le message dépasse ce nombre, le message ne sera pas envoyé.

<!--
## Monitor and track SMS {#monitoring-and-tracking-sms-deliveries}

After sending messages, you can monitor and track your deliveries. For more on this, refer to these sections:

* [Monitor a delivery](about-delivery-monitoring.md)
* [Understand delivery failures](delivery-failures-quarantine.md)
* [About message tracking](about-message-tracking.md)
-->

## Traitement des messages entrants {#processing-inbound-messages}

Le module **nlserver sms** interroge à intervalle régulier le routeur des messages SMS. Cela permet à Adobe Campaign de collecter les états d&#39;avancement des diffusions et de gérer les accusés de réception et les désinscriptions des destinataires.

* **Accusés de réception** : consultez les logs de diffusion pour connaître le statut de vos messages.

  >[!NOTE]
  >
  >Tout SMS envoyé est lié à un compte externe par la clé primaire de celui-ci. De cette manière :
  >
  > * Les accusés de réception d&#39;un compte externe de SMS effacé ne sont pas traités correctement.
  > * Un compte SMS ne peut être associé qu&#39;à un seul compte externe afin que les accusés de réception soient correctement attribués à ce dernier

* **Désinscription** : les destinataires qui ne souhaitent plus recevoir de diffusions par SMS peuvent renvoyer un message contenant le mot STOP. Si votre fournisseur vous le permet contractuellement, vous avez la possibilité de récupérer ses messages via l’activité de workflow **Réception de SMS** puis de créer une requête afin que l’option **Ne plus contacter cette personne** soit activée pour les personnes destinataires concernées.

## Schéma InSMS {#insms-schema}

Le schéma InSMS contient les informations relatives aux SMS entrants. Une description de ces champs est disponible via l&#39;attribut desc de ces derniers.

* **message** : contenu du SMS reçu.
* **origin** : numéro du mobile de l&#39;expéditeur du message.
* **providerId** : identifiant du message retourné par le SMSC (centre de messagerie).
* **created** : date d&#39;insertion du message entrant dans Adobe Campaign.
* **extAccount** : compte externe Adobe Campaign.

  >[!IMPORTANT]
  >
  >Les champs suivants sont spécifiques à Netsize.
  >
  >Si l&#39;opérateur utilisé n&#39;est pas Netsize, ces champs sont considérés comme vides.

* **alias** : alias du message entrant.
* **separator** : séparateur entre l&#39;alias et le corps du message.
* **messageDate** : date du message selon l&#39;opérateur.
* **receivalDate** : date de réception du message en provenance de l&#39;opérateur par le SMSC (centre de messagerie).
* **deliveryDate** : date d&#39;envoi du message par le SMSC (centre de messagerie).
* **largeAccount** : code du compte client associé au SMS entrant.
* **countryCode** : code pays de l&#39;opérateur.
* **operatorCode** : code du réseau de l&#39;opérateur.
* **linkedSmsId** : identifiant Adobe Campaign (broadlogId) associé au SMS sortant, dont ce SMS est la réponse.

## Gestion des réponses automatiques (réglementation américaine) {#managing-automatic-replies--american-regulation-}

Lorsqu&#39;un abonné répond à un SMS qui lui a été envoyé via Adobe Campaign par un message contenant un mot-clé tel que STOP, HELP ou YES, il est obligatoire sur le marché américain de configurer les messages qui lui sont automatiquement renvoyés.

Par exemple, si un destinataire envoie le mot-clé STOP, il reçoit automatiquement une confirmation de désinscription.

Le nom d&#39;expéditeur de ce type de messages est un numéro court (short code) habituellement utilisé pour envoyer les diffusions.

>[!IMPORTANT]
>
>La procédure détaillée suivante n&#39;est valide que pour les connecteurs SMPP, à l&#39;exception du connecteur SMPP générique étendu. Voir à ce sujet la section [Création d’un compte externe SMPP](sms-set-up.md#creating-an-smpp-external-account).
>
>Elle entre dans le cadre du processus de certification effectué par les opérateurs américains pour les campagnes marketing aux États-Unis. Ces SMS doivent notamment parvenir immédiatement à l’abonné qui a envoyé le mot-clé.

1. Créez un fichier XML de ce type :

   ```
   <autoreply>
     <shortcode name="12345">
       <reply keyword="STOP" text="You will not receive SMS anymore" />
       <reply keyword="HELP" text="Powered by Adobe Campaign" />
     </shortcode>
     <shortcode name="43115">
       <reply keyword="STOP" text="Vous ne recevrez plus de SMS" />
       <reply keyword="HELP" text="Service rendu par Adobe Campaign" />
     </shortcode>
     <shortcode name="*">
       <reply keyword="ADOBE" text="This text is replied when you send ADOBE to any short code" />
     </shortcode>
   </autoreply>
   ```

1. Pour l&#39;attribut **name** de la balise **`<shortcode>`**, indiquez le code court qui s&#39;affichera à la place du nom de l&#39;expéditeur du message.

   Dans chaque balise **`<reply>`**, renseignez l&#39;attribut **keyword** avec un mot-clé et l&#39;attribut **text** avec le message que vous souhaitez envoyer pour ce mot-clé.

   >[!NOTE]
   >
   >Chaque mot-clé doit être écrit en majuscules.

   Si vous voulez envoyer le même message pour plusieurs mots-clés, dupliquez la ligne correspondante.

   Par exemple :

   ```
   <reply keyword="STOP" text="You will not receive SMS anymore" />
   <reply keyword="QUIT" text="You will not receive SMS anymore" />
   ```

1. Une fois complété, enregistrez ce fichier sous le nom **smsAutoReply.xml**.

   Notez que le nom de ce fichier est sensible à la casse sous Linux.

1. Copiez ce fichier dans le répertoire **conf** d&#39;Adobe Campaign, à l&#39;endroit où se trouve le serveur Web.

>[!IMPORTANT]
>
>Il n’existe aucun historique pour ce type de messages automatiques. Ils ne figurent donc pas dans le tableau de bord des diffusions. [En savoir plus](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"}.
>
>Ces messages ne sont pas pris en compte dans les règles de pression commerciale. Consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/fr/docs/campaign/automation/campaign-optimization/pressure-rules.html?lang=fr){target="_blank"}.
