---
product: campaign
title: Diffusions cross-canal
description: En savoir plus sur les diffusions cross-canal
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Channels Activity
exl-id: 3bb468e2-7bcf-456f-8d8f-1c4e608e2b25
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: ht
source-wordcount: '292'
ht-degree: 100%

---

# Diffusions cross-canal{#cross-channel-deliveries}



Les diffusions cross-canal sont disponibles dans l&#39;onglet **[!UICONTROL Diffusions]** des activités d&#39;un workflow de campagne.

Les différents canaux disponibles sont :

* [E-mail](../../delivery/using/about-email-channel.md)
* [Courrier](../../delivery/using/about-direct-mail-channel.md)
* [Mobile](../../delivery/using/sms-channel.md)
* [Twitter](../../social/using/about-social-marketing.md)
* [iOS](../../delivery/using/create-notifications-ios.md)
* [Android](../../delivery/using/create-notifications-android.md)

Sélectionnez le modèle sur lequel vous souhaitez baser votre diffusion et définissez son contenu.

Vous pouvez définir la cible de votre diffusion en amont du workflow via les différentes activités de ciblages.

Dans l&#39;exemple ci-dessous, nous allons créer un workflow pour envoyer un e-mail ou un SMS aux abonnés aux notifications push, suivi d&#39;une notification push une semaine plus tard. Pour cela :

1. Créez une campagne.
1. Dans l&#39;onglet **[!UICONTROL Ciblages et workflows]** de votre campagne, ajoutez une **[!UICONTROL Requête]** à votre workflow.
1. Configurez votre requête. Par exemple, ici, nous sélectionnons les destinataires abonnés aux notification push comme dimension cible.

   >[!NOTE]
   >
   >Pour les notifications push, utilisez la dimension cible **applications abonnées**.

   ![](assets/cross_channel_delivery_1.png)

1. Ajoutez les conditions de filtrage à votre requête. Ici, nous allons sélectionner les destinataires ayant un numéro de mobile ou une adresse email.

   ![](assets/cross_channel_delivery_2.png)

1. Ajoutez une activité de **[!UICONTROL Partage]** à votre workflow pour diviser les destinataires ayant un numéro de mobile et ceux ayant une adresse email.
1. Dans l&#39;onglet **[!UICONTROL Diffusion]**, sélectionnez une diffusion pour chacune de vos cibles.

   Pour créer votre diffusion, procédez de la même manière qu&#39;avec un assistant de diffusion classique en double-cliquant sur l&#39;activité diffusion de votre workflow. Voir à ce propos cette [page](../../delivery/using/about-email-channel.md).

   ![](assets/cross_channel_delivery_3.png)

1. Pour éviter que les destinataires ne reçoivent trop de diffusion à la fois, ajoutez et configurez une activité **[!UICONTROL Attente]**.
1. Ajoutez une activité **[!UICONTROL Partage]** pour diviser les abonnés aux applications mobiles iOS ou Android.

   Sélectionnez un service pour chacun des systèmes d&#39;exploitation. Pour en savoir plus sur la création de service, voir cette [page](../../delivery/using/configuring-the-mobile-application.md).

   ![](assets/cross_channel_delivery_4.png)

1. Sélectionnez et configurez une diffusion application mobile pour chacun des systèmes d&#39;exploitation.

   ![](assets/cross_channel_delivery_5.png)
