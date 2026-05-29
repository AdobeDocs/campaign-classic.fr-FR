---
product: campaign
title: Prise en main du canal SMS
description: Prise en main du canal SMS
feature: SMS
role: User
exl-id: 6fc2ab09-8ea7-4865-88ad-bd45eee68958
TQID: https://experienceleague.adobe.com/bk-HUOGv3u60NzOnXD0huo74lBJJuiBOaOJeGmPa2E4
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a075b2c1-7748-4328-b7f6-343aa314616aid: b631758a-142d-425f-b9aa-f756d85cb979id: c858a28b-ea19-49b0-8d48-828717fad89c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
subfeature_v2: id: e95a583b-fcfa-4524-8666-46a29c828119id: c8da4fdd-eb94-4751-a43c-f82733fb2d6eid: d5bbe3da-ba85-4242-817e-54f7c4b943e0id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 484
ht-degree: 100%

---

# Prise en main du canal SMS{#sms-channel}

Utilisez Adobe Campaign pour envoyer des messages texte aux clients et aux clientes sur leurs appareils mobiles. Vous pouvez créer, personnaliser et prévisualiser des messages au format texte à partir de l’éditeur de SMS.

Le canal SMS est un moyen direct et particulièrement efficace pour toucher les utilisateurs et utilisatrices, quel que soit l’endroit où ils se trouvent. Grâce à des taux d’ouverture élevés et à une diffusion quasi instantanée, le SMS est idéal pour les alertes urgentes, les mises à jour transactionnelles et les messages promotionnels concis. Il s’intègre parfaitement à une stratégie cross-canal pour assurer une communication percutante en temps réel. Découvrez comment configurer et utiliser efficacement le canal SMS dans la documentation d’[Adobe Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/sms.html?lang=fr){target=_blank}.

Dans le cadre de la transition de Campaign v7 vers v8, le jeu de documentation de Campaign Classic a été rationalisé et réorganisé. Les fonctionnalités communes sont désormais disponibles exclusivement dans le jeu de documentation de Campaign v8.

>[!BEGINTABS]

>[!TAB Documentation du canal SMS]

Pour en savoir plus sur le canal SMS, consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/sms.html?lang=fr){target=_blank}.


[![Image](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/sms.html?lang=fr){target=_blank}


>[!TAB Création de diffusion SMS]

Découvrez les étapes clés de la création d’une diffusion SMS dans la **documentation de Campaign v8** :

* [Vue d’ensemble du canal SMS](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/sms.html?lang=fr){target="_blank"} : découvrez comment envoyer des SMS à vos clientes et clients sur leurs appareils mobiles.
* [Créer une diffusion SMS](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/create-sms/create-sms.html?lang=fr){target="_blank"} : découvrez les différentes étapes nécessaires à la création d’une diffusion SMS.
* [Définir le contenu](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/create-sms/sms-content.html?lang=fr){target="_blank"} : apprenez à personnaliser le contenu de vos messages SMS.
* [Sélectionner l’audience](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/create-sms/sms-audience.html?lang=fr){target="_blank"} : la cible principale est extraite de la base de données d’Adobe Campaign ou peut aussi provenir d’un fichier externe.
* [Envoyer des BAT SMS](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/validate-sms/sms-proofs.html?lang=fr) : il est essentiel de configurer un cycle de validation de la diffusion. Assurez-vous que votre contenu est approuvé avant de l’envoyer à votre audience.
* [Envoyer à l’audience](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/validate-sms/sms-send.html?lang=fr) : une fois votre SMS validé, vous pouvez désormais l’envoyer à son audience.
* [Superviser et suivre une diffusion SMS](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/sms-monitor.html?lang=fr) : suivez votre diffusion SMS pour garantir l’efficacité de vos campagnes marketing.


>[!TAB Configuration des SMS]

Consultez les pages suivantes pour en savoir plus sur la configuration des SMS. Ces pages sont spécifiques à Campaign v7.

* [Configuration autonome](sms-set-up.md) : découvrez comment configurer le canal SMS sur une instance autonome.
* [Configuration de midsourcing](sms-set-up-mid.md) : découvrez comment envoyer du contenu à un téléphone mobile à l’aide de serveurs intermédiaires.
* [Connecteur SMS](sms-protocol.md) : découvrez le protocole et les paramètres du connecteur SMS.
* [Configuration supplémentaire](sms-send.md) : découvrez les paramètres avancés et autres options de configuration.
* [Dépannage](troubleshooting-sms.md) : nous avons répertorié une série de problèmes potentiels et leurs solutions.

>[!ENDTABS]



<!--
Use Adobe Campaign to send personalized SMS messages.

Before starting sending SMS:

* Make sure recipient profiles contain at least a mobile phone in their profile.
* Learn more about the Adobe Campaign [Delivery best practices](delivery-best-practices.md).

The key steps to send a SMS are as follows:

* [Configure the SMS channel](sms-set-up.md)
* [Create a SMS delivery](sms-create.md)
* [Define the audience](sms-create.md#selecting-the-target-population)
* [Define the SMS content](sms-create.md#defining-the-sms-content)
* [Send, monitor and track SMS](sms-send.md)
* [Troubleshoot](troubleshooting-sms.md)

In addition, you need to be familiar with SMS protocol and settings. Walk through the connection set up between Adobe Campaign and a SMPP provider in [this document](sms-protocol.md)

For global information on how to create a delivery, refer to [this section](steps-about-delivery-creation-steps.md).

>[!NOTE]
>
>Adobe Campaign also lets you submit notifications on mobile terminals, via its **Adobe Campaign Mobile App Channel (NMAC)** option. 
> 
>For more on this, refer to the [Get started with mobile app channel](about-mobile-app-channel.md) section.
-->