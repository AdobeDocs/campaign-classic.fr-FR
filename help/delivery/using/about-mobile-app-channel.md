---
solution: Campaign Classic
product: campaign
title: À propos de Mobile App Channel dans Adobe Campaign Classic
description: Cette section contient des informations générales spécifiques à Mobile App Channel dans Adobe Campaign Classic.
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '756'
ht-degree: 100%

---


# A propos de Mobile App Channel{#about-mobile-app-channel}

>[!CAUTION]
>
>Ce document décrit le processus d’intégration de votre application mobile avec la plateforme Adobe Campaign. Il ne donne aucune information ni sur la création de l’application mobile ni sur son paramétrage pour la gestion des notifications. Si vous souhaitez obtenir des informations à ce sujet, reportez-vous aux documentations officielles [Apple](https://developer.apple.com/) et [Android](https://developer.android.com/index.html).

Les sections ci-dessous apportent des informations spécifiques à Mobile App Channel.

Pour plus d&#39;informations sur la création d&#39;une diffusion, voir [cette section](../../delivery/using/steps-about-delivery-creation-steps.md).

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

* Une notification est envoyée au client pour l&#39;informer que son colis est sorti de l&#39;entrepôt. L&#39;activation de la notification affiche une page contenant les informations relatives à la diffusion.
* L&#39;utilisateur a ajouté des éléments à son panier, mais il a quitté l&#39;application sans concrétiser l&#39;achat. Une notification est envoyée, l&#39;informant que son panier a été abandonné. Lorsque l&#39;utilisateur active la notification, l&#39;écran du produit abandonné est affiché.

>[!CAUTION]
>
>* Vous devez vous assurer que les notifications envoyées vers une application mobile sont conformes aux prérequis et conditions définis par Apple (Apple Push Notification Service) et Google (Firebase Cloud Messaging).
>* Attention : dans certains pays, la loi exige que vous informiez les utilisateurs de vos applications mobiles du type de données collectées et de la finalité de leur traitement. Vous devez vérifier la législation.


Le workflow **[!UICONTROL Gestion des opt-out NMAC]** (mobileAppOptOutMgt) met à jour les désabonnements aux notifications sur les appareils mobiles. Pour plus d&#39;informations sur ce workflow, consultez le [Guide Workflows](../../workflow/using/mobile-app-channel.md).

Adobe Campaign est compatible avec l&#39;APNS binaire et HTTP/2. Pour plus d’informations sur la procédure de configuration, voir la section [Paramétrage de l’application mobile dans Adobe Campaign](../../delivery/using/configuring-the-mobile-application.md).

## Parcours des données {#data-path}

Les schémas suivants présentent les étapes permettant à une application mobile d&#39;échanger des données avec Adobe Campaign. Ce processus comporte trois acteurs :

* l&#39;application mobile
* le service de notification : APNS (Apple Push Notification Service) pour Apple et FCM (Firebase Cloud Messaging) pour Android
* Adobe Campaign

Les trois grandes étapes du processus de notification sont : l&#39;enregistrement de l&#39;application dans Adobe Campaign (collecte des abonnements), les diffusions et le tracking.

### Etape 1 : collecte des abonnements {#step-1--subscription-collection}

L&#39;application mobile est téléchargée par l&#39;utilisateur sur l&#39;App Store ou Google Play. Cette application contient, entre autres, les paramètres de connexion (certificat pour iOS et clé de projet pour Android) et la clé d&#39;intégration. Lors du premier lancement de l&#39;application, l&#39;utilisateur peut être amené (selon la configuration de l&#39;application) à renseigner une information d&#39;enregistrement (@userKey : par exemple l&#39;email ou le numéro de compte). Au même moment, l&#39;application interroge le service de notification pour récupérer un identifiant de notification (push id). Toutes ces informations (paramètres de connexion, clé d&#39;intégration, identifiant de notification, userKey) sont envoyées à Adobe Campaign.

![](assets/nmac_register_view.png)

### Etape 2 : diffusion {#step-2--delivery}

Le marketeur cible les abonnés d&#39;une application. Le processus de diffusion envoie au service de notifications les paramètres de connexion (certificat pour iOS et clé de projet pour Android), l&#39;identifiant de notification (push id), et le contenu de la notification. Le service de notification envoie les notifications sur les terminaux ciblés.

Les informations suivantes sont remontées dans Adobe Campaign :

* Android uniquement : nombre d&#39;appareils ayant affiché la notification (impressions)
* Android et iOS : nombre d&#39;appuis sur la notification (clics sur notification)

![](assets/nmac_delivery_view.png)

Le serveur Adobe Campaign doit pouvoir contacter le serveur APNS sur les ports suivants :

* 2195 (envoi) et 2186 (feedback service) pour le connecteur binaire iOS
* 443 pour le connecteur HTTP/2 iOS

   >[!NOTE]
   >
   > À compter de la version Campaign 20.3, le connecteur binaire hérité d&#39;iOS est obsolète. Si vous utilisez ce connecteur, vous devez adapter votre implémentation en conséquence. [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/migrate-to-apns-http2.html)

Pour en tester le bon fonctionnement, utilisez les commandes suivantes :

* Pour les tests :

   ```
   telnet gateway.sandbox.push.apple.com
   ```

* En production :

   ```
   telnet gateway.push.apple.com
   ```

Si un connecteur binaire iOS est utilisé, le MTA et le serveur web doivent pouvoir contacter l&#39;APNS sur le port 2195 (envoi), le serveur de workflow doit pouvoir contacter l&#39;APNS sur le port 2196 (feedback service).

Si un connecteur HTTP/2 iOS est utilisé, le MTA, le serveur web et le serveur de workflow doivent pouvoir contacter l&#39;APNS sur le port 443.

