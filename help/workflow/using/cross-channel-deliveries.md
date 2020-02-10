---
title: Diffusions cross-canal
seo-title: Diffusions cross-canal
description: Diffusions cross-canal
seo-description: null
page-status-flag: never-activated
uuid: 191ff39e-f739-48b3-8865-ad1b641b7499
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 8dda45b4-4b5d-4b4e-a8b4-45d9bc49aaf3
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Diffusions cross-canal{#cross-channel-deliveries}

Cross-channel deliveries are available in the **[!UICONTROL Deliveries]** tab of campaign workflow activities.

Elles permettent de créer une diffusion propre à un canal en particulier. Vous pouvez y définir le modèle sur lequel vous souhaitez baser votre diffusion ainsi que son contenu, de la même manière qu&#39;avec un assistant de diffusion classique.

Les différents canaux disponibles sont :

* [Email](../../delivery/using/about-email-channel.md)
* [Courrier](../../delivery/using/about-direct-mail-channel.md)
* [Mobile](../../delivery/using/sms-channel.md)
* [Twitter](../../social/using/publishing-on-twitter.md)
* [Facebook](../../social/using/publishing-on-facebook.md)
* [iOS](../../delivery/using/creating-notifications.md#sending-notifications-on-ios)
* [Android](../../delivery/using/creating-notifications.md#sending-notifications-on-android)

Vous pouvez définir la cible de votre diffusion en amont du workflow via les différentes activités de ciblages.

Par exemple, ici, nous allons créer un workflow pour envoyer un email ou un SMS aux abonnés aux notifications push, suivi d&#39;une notification push une semaine plus tard. Pour cela :

1. Créez une campagne.
1. Dans l’ **[!UICONTROL Targeting and workflows]** onglet de votre campagne, ajoutez une **[!UICONTROL Query]** balise à votre processus.
1. Configurez votre requête. Par exemple, ici, nous sélectionnons les destinataires abonnés aux notification push comme dimension cible.

   >[!NOTE]
   >
   >Pour les notifications push, pensez à utiliser la dimension cible **applications abonnées**.

   ![](assets/cross_channel_delivery_1.png)

1. Ajoutez les conditions de filtrage à votre requête. Ici, nous allons sélectionner les destinataires ayant un numéro de mobile ou une adresse email.

   ![](assets/cross_channel_delivery_2.png)

1. Add a **[!UICONTROL Split]** activity to your workflow to divide recipients who have a mobile number and those who have an email address.
1. In the **[!UICONTROL Delivery]** tab, select a delivery for each of your targets.

   Pour créer votre diffusion, procédez de la même manière qu&#39;avec un assistant de diffusion classique en double-cliquant sur l&#39;activité diffusion de votre workflow. Voir à ce propos cette [page](../../delivery/using/about-email-channel.md).

   ![](assets/cross_channel_delivery_3.png)

1. Add and configure a **[!UICONTROL Wait]** activity in order for the recipients not to receive too many deliveries at once.
1. Add a **[!UICONTROL Split]** activity to divide subscribers of an iOS or Android mobile applications.

   Sélectionnez un service pour chacun des systèmes d&#39;exploitation. Pour en savoir plus sur la création de service, voir cette [page](../../delivery/using/setting-up-mobile-app-channel.md#creating-the-service-and-collecting-subscriptions).

   ![](assets/cross_channel_delivery_4.png)

1. Sélectionnez et configurez une diffusion application mobile pour chacun des systèmes d&#39;exploitation.

   ![](assets/cross_channel_delivery_5.png)

