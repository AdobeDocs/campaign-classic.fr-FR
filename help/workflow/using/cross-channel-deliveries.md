---
product: campaign
title: Diffusions cross-canal
description: En savoir plus sur les diffusions cross-canal
feature: Workflows, Channels Activity
hide: true
exl-id: 3bb468e2-7bcf-456f-8d8f-1c4e608e2b25
TQID: 'https://experienceleague.adobe.com/BXn5nJkGD-NL8Rh5kYtltXfGJiWlYQqbyzcdZ1SleJA'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
    internal-label: HeatMap
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
    internal-label: Execution activities
  - id: d1110311-2ca4-442b-be37-088a6db845ee
    internal-label: Data Management activities
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
  - id: bce277d1-7efa-48d8-9a1b-b588bb45ba1c
    internal-label: Channels Activity
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 100%
---
# Diffusions cross-canal{#cross-channel-deliveries}



Les diffusions cross-canal sont disponibles dans l&#39;onglet **[!UICONTROL Diffusions]** des activités d&#39;un workflow de campagne.

Les différents canaux disponibles sont :

* [E-mail](../../delivery/using/about-email-channel.md)
* [Courrier](../../delivery/using/about-direct-mail-channel.md)
* [Mobile](../../delivery/using/sms-channel.md)
* [X (anciennement Twitter)](../../social/using/about-social-marketing.md)
* [iOS](../../delivery/using/create-notifications-ios.md)
* [Android](../../delivery/using/create-notifications-android.md)

Sélectionnez le modèle sur lequel vous souhaitez baser votre diffusion et définissez son contenu.

Vous pouvez définir la cible de votre diffusion en amont du workflow via les différentes activités de ciblages.

Dans l&#39;exemple ci-dessous, nous allons créer un workflow pour envoyer un e-mail ou un SMS aux abonnés aux notifications push, suivi d&#39;une notification push une semaine plus tard. Pour cela :

1. Créez une campagne.
1. Dans l&#39;onglet **[!UICONTROL Ciblages et workflows]** de votre campagne, ajoutez une **[!UICONTROL Requête]** à votre workflow.
1. Configurez votre requête. Par exemple, ici, nous sélectionnons les personnes destinataires abonnées aux notifications push comme dimension cible.

   >[!NOTE]
   >
   >Pour les notifications push, utilisez la dimension cible **applications abonnées**.

   ![](assets/cross_channel_delivery_1.png)

1. Ajoutez les conditions de filtre à votre requête. Ici, nous allons sélectionner les destinataires ayant un numéro de mobile ou une adresse e-mail.

   ![](assets/cross_channel_delivery_2.png)

1. Ajoutez une activité de **[!UICONTROL Partage]** à votre workflow pour diviser les destinataires ayant un numéro de mobile et ceux ayant une adresse email.
1. Dans l&#39;onglet **[!UICONTROL Diffusion]**, sélectionnez une diffusion pour chacune de vos cibles.

   Pour créer votre diffusion, procédez de la même manière qu’avec un assistant de diffusion classique en double-cliquant sur l’activité diffusion de votre workflow. Pour en savoir plus à ce sujet, consultez cette [page](../../delivery/using/about-email-channel.md).

   ![](assets/cross_channel_delivery_3.png)

1. Pour éviter que les destinataires ne reçoivent trop de diffusion à la fois, ajoutez et configurez une activité **[!UICONTROL Attente]**.
1. Ajoutez une activité **[!UICONTROL Partage]** pour diviser les abonnés aux applications mobiles iOS ou Android.

   Sélectionnez un service pour chacun des systèmes d&#39;exploitation. Pour en savoir plus sur la création de service, voir cette [page](../../delivery/using/configuring-the-mobile-application.md).

   ![](assets/cross_channel_delivery_4.png)

1. Sélectionnez et configurez une diffusion pour application mobile pour chacun des systèmes d’exploitation.

   ![](assets/cross_channel_delivery_5.png)
