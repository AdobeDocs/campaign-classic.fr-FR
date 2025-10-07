---
product: campaign
title: Commencer avec le canal des applications mobiles
description: Commencer avec le canal des applications mobiles dans Adobe Campaign
feature: Push
role: User
exl-id: c3b0406f-f652-42f4-ad0d-23fb719cd1b6
source-git-commit: a1e9fec0e9c85bf25b79e24a7432dfb45bd1a0cb
workflow-type: tm+mt
source-wordcount: '585'
ht-degree: 44%

---

# Commencer avec le canal des applications mobiles{#about-mobile-app-channel}

Avec Adobe Campaign, créez des diffusions de notification push pour envoyer des messages personnalisés aux utilisateurs de votre application mobile.

Les notifications push vous permettent d’interagir avec les utilisateurs et utilisatrices sur iOS et Android en temps réel. Que vous envoyiez des mises à jour, des annonces ou des promotions, vous pouvez contrôler le contenu, le timing et le ciblage. Découvrez comment configurer et utiliser le canal push, gérer les abonnements, intégrer aux APNs et à FCM, et personnaliser les messages dans la documentation [Adobe Campaign v8](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/send/emails/email){target=_blank}.

Dans le cadre de l’initiative de promotion de Campaign v8, la documentation de Campaign Classic a été réorganisée. Les fonctionnalités communes sont désormais uniquement disponibles dans l’ensemble documentaire de Campaign v8.

>[!BEGINTABS]

>[!TAB Documentation du canal push]

Pour en savoir plus sur le canal de notification push, consultez la documentation [Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html?lang=fr){target=_blank}.

[![Image](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html?lang=fr){target=_blank}


>[!TAB Création d&#39;une diffusion push]

Découvrez les étapes clés liées à la création d&#39;une diffusion push dans la documentation de Campaign v8 :

* [Créer une notification push](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html?lang=fr#push-create){target="_blank"} : découvrez les différentes étapes nécessaires pour créer une diffusion push.
* [Envoyer et surveiller la notification push](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html?lang=fr#push-test){target="_blank"} : découvrez comment valider, envoyer et suivre vos diffusions.
* [Concevoir une diffusion de notifications push enrichie Android](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/rich-push/rich-push-android.html?lang=fr){target="_blank"} : découvrez comment créer et configurer des notifications push enrichies pour les appareils Android.
* [Concevoir une diffusion de notifications push enrichie iOS](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/rich-push/rich-push-ios.html?lang=fr){target="_blank"} : découvrez comment concevoir et configurer des notifications push enrichies pour les appareils iOS dans Adobe Campaign v8.


>[!TAB Paramètres push]

Reportez-vous à ces pages pour en savoir plus sur les paramètres push dans la documentation de Campaign v8 :

* [Conditions préalables à la configuration](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html?lang=fr#before-starting){target="_blank"} : découvrez comment configurer les autorisations et votre application.
* [Configurer la propriété de lancement](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html?lang=fr#launch-property){target="_blank"} : découvrez comment configurer une propriété de balise mobile dans la collecte de données Adobe Experience Platform pour activer les notifications push.
* [Configuration des services push mobiles](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html?lang=fr#push-service){target="_blank"} : configurez les services push iOS et Android dans Adobe pour activer les notifications push ciblées pour les utilisateurs et utilisatrices de vos applications mobiles.
* [Configurer l’extension dans votre propriété mobile](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html?lang=fr#configure-extension){target="_blank"} : intégrez l’extension Campaign dans votre propriété mobile pour activer les notifications push et gérer efficacement les interactions utilisateur.

>[!ENDTABS]


Les informations suivantes sont spécifiques à Campaign Classic.

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

Une fois cette étape effectuée, vous pouvez configurer vos applications Android et iOS. Consultez la [documentation](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html?lang=fr){target="_blank"} de Campaign v8.

+++

+++ **Résolution des problèmes**

Si votre appareil mobile est connecté en Wi-Fi et que vous ne recevez pas les notifications, vérifiez que les ports FCM/APN ne sont pas bloqués par votre pare-feu.

**Android** : l&#39;appareil mobile se connecte aux serveurs FCM sur les ports 5228 à 5230. Vous devez donc configurer votre pare-feu pour qu&#39;il autorise la connexion avec FCM. Les ports à ouvrir sont les suivants : 5228 (le plus fréquemment utilisé), 5229 et 5230.

**iOS** :

Connecteur HTTP/2 : vous devez autoriser les communications à destination et en provenance des serveurs suivants :

* api.push.apple.com : port 443
* api.development.push.apple.com : port 443

>[!NOTE]
>
>Pour plus d’informations sur les deux connecteurs, consultez la [documentation](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html?lang=fr){target="_blank"} de Campaign v8.

+++
