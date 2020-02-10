---
title: A propos du canal d’application mobile dans Adobe Campaign Classic
description: Cette section fournit des informations générales spécifiques au canal d’application mobile dans Adobe Campaign Classic.
page-status-flag: never-activated
uuid: e8d26b33-dc7c-4abd-956a-92f419a117e1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
discoiquuid: 6b3fe8b9-dae6-4f8e-83e1-3376c0fe72a5
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c581f22261af7e083f6bd47e603d17d2d71e7ce6

---


# A propos de Mobile App Channel{#about-mobile-app-channel}

>[!CAUTION]
>
>Cette documentation décrit le processus d&#39;intégration de votre application mobile avec la plateforme Adobe Campaign. Elle ne fournit pas d&#39;informations sur la création de l&#39;application mobile et sa configuration pour la gestion des notifications. Si vous souhaitez obtenir des informations à ce sujet, référez-vous aux documentations officielles Apple ([https://developer.apple.com/](https://developer.apple.com/)) et Android ([https://developer.android.com/index.html](https://developer.android.com/index.html)).

Les sections ci-dessous fournissent des informations spécifiques au canal de l’application mobile. Pour plus d’informations sur la création d’une diffusion, voir[cette section](../../delivery/using/steps-about-delivery-creation-steps.md).

Le canal des applications mobiles (**Mobile App Channel**) permet d&#39;envoyer des notifications personnalisées depuis la plateforme Adobe Campaign sur des terminaux iOS et Android, via des applications (apps). Deux canaux de diffusion sont disponibles :

* Un canal iOS permettant d’envoyer des notifications sur les appareils mobiles Apple.

   ![](assets/nmac_intro_2.png)

* Un canal Android permettant d’envoyer des messages de données sur les appareils mobiles Android.

   ![](assets/nmac_intro_1.png)

A ces deux canaux correspondent deux activités de diffusion dans les workflows des opérations :

![](assets/nmac_intro_3.png)

>[!NOTE]
>
>Deux modèles sont également disponibles pour les messages transactionnels.

Vous pouvez définir le comportement de l’application lorsque l’utilisateur active la notification afin d’afficher l’écran correspondant au contexte de l’application. Par exemple :

* Une notification est envoyée au client pour l&#39;informer que son colis est sorti de l&#39;entrepôt. L&#39;activation de la notification affiche une page contenant les informations relatives à la livraison.
* L&#39;utilisateur a ajouté des éléments à son panier, mais il a quitté l&#39;application sans concrétiser l&#39;achat. Une notification est envoyée, l&#39;informant que son panier a été abandonné. Lorsque l&#39;utilisateur active la notification, l&#39;écran du produit abandonné est affiché.

>[!CAUTION]
>
>* Vous devez vous assurer que les notifications envoyées vers une application mobile sont conformes aux pré-requis et conditions définis par Apple (Apple Push Notification Service) et Google (Google Cloud Messaging).
>* Attention : dans certains pays, la loi exige que vous informiez les utilisateurs de vos applications mobiles du type de données collectées et de la finalité de leur traitement. Vous devez vérifier la législation.


Le processus **[!UICONTROL NMAC opt-out management]** (mobileAppOptOutMgt) met à jour les désabonnements de notification sur les périphériques mobiles. For more information on this workflow, refer to the [Workflows guide](../../workflow/using/mobile-app-channel.md).

Adobe Campaign est compatible avec les API binaires et HTTP/2. Pour plus d’informations sur les étapes de configuration, reportez-vous à la section [Connectors](../../delivery/using/setting-up-mobile-app-channel.md#connectors) .
