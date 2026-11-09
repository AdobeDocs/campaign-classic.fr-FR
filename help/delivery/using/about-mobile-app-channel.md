---
product: campaign
title: Commencer avec le canal d’application mobile
description: Commencer avec le canal des applications mobiles dans Adobe Campaign
feature: Push
role: User
exl-id: c3b0406f-f652-42f4-ad0d-23fb719cd1b6
TQID: 'https://experienceleague.adobe.com/hNwtWC-TnFXsSv7CqqzKqr29sk67h2rwMBOTcBTToDs'
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
  - id: a4657621-810c-498b-8a27-7ced9c176dda
    internal-label: Push notifications
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
source-git-commit: 758d5159759b19f7ef32e8cc8f6237547599e727
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 91%
---
# Commencer avec le canal d’application mobile{#about-mobile-app-channel}

Avec Adobe Campaign, créez des diffusions de notifications push pour envoyer des messages personnalisés aux utilisateurs et utilisatrices de votre application mobile.

>[!NOTE]
>
>Dans le cadre de la transition de Campaign v7 vers v8, la documentation de Campaign Classic a été rationalisé et réorganisé. Les fonctionnalités communes sont désormais disponibles exclusivement dans le jeu de documentation de Campaign v8. Pour en savoir plus sur le canal de notification push, consultez la documentation [Campaign v8](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/send/push/push){target=_blank}.
>
>[![image](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/send/push/push){target=_blank}

Les informations suivantes concernent uniquement Campaign Classic.

+++ **Installation du package**

![](assets/do-not-localize/how-to-video.png) [Découvrez comment installer le package d’application mobile en vidéo](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/sending-messages/push-channel/installing-the-mobile-app-channel.html?lang=fr#sending-messages)

En tant que client hybride/hébergé, contactez l&#39;équipe d&#39;[Assistance clientèle d&#39;Adobe](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) pour accéder au canal de notifications push dans Campaign.

En tant que client on-premise, vous devez installer un package natif.

>[!CAUTION]
>
>Pour en savoir plus sur les packages natifs de Campaign, les bonnes pratiques et les recommandations, consultez [cette page](../../installation/using/installing-campaign-standard-packages.md).

Les étapes d&#39;installation sont les suivantes :

1. Accédez à l’assistant d’import de package depuis le menu **[!UICONTROL Outils > Avancé > Import de package]** de la console cliente Adobe Campaign.

   ![](assets/package_ios.png)

1. Sélectionnez **[!UICONTROL Installer un package standard]**.

1. Dans la liste qui s&#39;affiche, cochez **[!UICONTROL Canal des applications mobiles]**.

   ![](assets/package_ios_2.png)

1. Cliquez sur **[!UICONTROL Suivant]** puis **[!UICONTROL Démarrer]** pour commencer l&#39;installation du package.

   Une fois les packages installés, la barre de progression indique **100 %**. De plus, les logs de l&#39;installation contiennent le message suivant : **[!UICONTROL L&#39;installation des packages s&#39;est terminée avec succès]**.

   ![](assets/package_ios_3.png)

1. **[!UICONTROL Fermez]** la fenêtre d&#39;installation.

Une fois cette étape effectuée, vous pouvez configurer vos applications Android et iOS. Consultez la [documentation](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html?lang=fr){target="_blank"} de Campaign v8.

+++

+++ **Résolution des problèmes**

Si votre appareil mobile est connecté en Wi-Fi et que vous ne recevez pas les notifications, vérifiez que les ports FCM/APN ne sont pas bloqués par votre pare-feu.

**Android** : l’appareil mobile se connecte aux serveurs FCM sur les ports 5228 à 5230. Vous devez donc configurer votre pare-feu afin qu’il autorise la connexion à FCM. Les ports à ouvrir sont : 5228 (le plus fréquemment utilisé), 5229 et 5230.

**iOS** :

Connecteur HTTP/2 : vous devez autoriser les communications à destination et en provenance des serveurs suivants :

* api.push.apple.com : port 443
* api.development.push.apple.com : port 443

>[!NOTE]
>
>Pour plus d’informations sur les deux connecteurs, consultez la [documentation](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html?lang=fr){target="_blank"} de Campaign v8.

+++
