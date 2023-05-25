---
product: campaign
title: Paramétrer lʼapplication mobile iOS dans Adobe Campaign
description: Découvrez comment paramétrer votre application mobile pour iOS.
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Push
exl-id: 67eee1c5-a918-46b9-875d-7c3c71c00635
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: ht
source-wordcount: '738'
ht-degree: 100%

---

# Étapes de configuration pour iOS {#configuring-the-mobile-application-in-adobe-campaign-ios}



Une fois le package installé, vous pouvez définir les paramètres de votre application iOS dans Adobe Campaign Classic.

>[!NOTE]
>
>Pour savoir comment configurer votre application pour Android et comment créer une diffusion pour Android, reportez-vous à cette [section](configuring-the-mobile-application-android.md).

Les étapes clés sont les suivantes :

1. [Configuration du compte externe iOS](#configuring-external-account-ios)
1. [Configuration du service iOS](#configuring-ios-service)
1. [Intégration de l&#39;application mobile iOS dans Campaign](#creating-ios-app)

Vous pourrez ensuite [créer une notification push pour les appareils iOS](create-notifications-ios.md).


## Configuration du compte externe iOS {#configuring-external-account-ios}

Pour iOS, le connecteur HTTP/2 iOS envoie des notifications à l&#39;APNS HTTP/2.

Pour configurer ce connecteur, procédez comme suit :

1. Accédez à **[!UICONTROL Administration > Plateforme > Comptes externes]**.
1. Sélectionnez le compte externe **[!UICONTROL routage iOS]**.
1. Dans l&#39;onglet **[!UICONTROL Connecteur]**, renseignez le champ **[!UICONTROL URL d&#39;accès au connecteur]** avec l&#39;URL suivante :```http://localhost:8080/nms/jsp/iosHTTP2.jsp```

   ![](assets/nmac_connectors.png)

1. Cliquez sur **[!UICONTROL Enregistrer]**.

Votre connecteur iOS est maintenant paramétré. Vous pouvez créer votre service.

## Configuration du service iOS {#configuring-ios-service}

>[!CAUTION]
>
>L&#39;application doit avoir été configurée pour des actions de Push AVANT toute intégration au SDK Adobe.
>
>Si ce n&#39;est pas le cas, veuillez consulter [cette page](https://developer.apple.com/documentation/usernotifications).

1. Dans l&#39;arborescence, positionnez-vous sur le nœud **[!UICONTROL Profils et Cibles > Services et abonnements]** et cliquez sur le bouton **[!UICONTROL Nouveau]**.

   ![](assets/nmac_service_1.png)

1. Définissez un **[!UICONTROL Libellé]** et un **[!UICONTROL Nom interne]**.
1. Dans le champ **[!UICONTROL Type]**, choisissez **[!UICONTROL Application mobile]**.

   >[!NOTE]
   >
   >Le mapping de ciblage par défaut **[!UICONTROL Applications abonnées (nms:appSubscriptionRcp)]** est lié à la table des destinataires. Si vous souhaitez utiliser un autre mapping de ciblage, vous devez créer un nouveau mapping de ciblage et le renseigner dans le champ **[!UICONTROL Mapping de ciblage]** du service. La création d&#39;un mapping de ciblage est présentée dans le [Guide de configuration](../../configuration/using/about-custom-recipient-table.md).

   ![](assets/nmac_ios.png)

1. Cliquez ensuite sur le bouton **[!UICONTROL Ajouter]** pour sélectionner le type d&#39;application.

   ![](assets/nmac_service_2.png)

1. Créez vos applications de développement et de production iOS. Pour plus d’informations à ce sujet, consultez cette [section](configuring-the-mobile-application.md#creating-ios-app).

## Création d&#39;une application mobile iOS {#creating-ios-app}

Après avoir créé votre service, créez votre application iOS dans Campaign. Procédez comme suit :

1. Dans le service que vous venez de créer, cliquez sur le bouton **[!UICONTROL Ajouter]** pour choisir le type d&#39;application.

   ![](assets/nmac_service_2.png)

1. La fenêtre suivante s’affiche. Sélectionnez **[!UICONTROL Créer une application iOS]**, puis indiquez le **[!UICONTROL libellé]**.

   ![](assets/nmac_ios_2.png)

1. Vous pouvez, si nécessaire, enrichir un contenu de message push avec certaines **[!UICONTROL variables d’application]**. Elles sont entièrement personnalisables et font partie de la payload du message envoyé à l’appareil mobile.
Dans l’exemple suivant, nous ajoutons **mediaURl** et **mediaExt** pour créer une notification push enrichie, puis nous fournissons à l’application l’image à afficher dans la notification.

   ![](assets/nmac_ios_3.png)

1. L’onglet **[!UICONTROL Paramètres d’abonnement]** permet de définir la correspondance avec une extension du schéma **[!UICONTROL Applications abonnées (nms:appsubscriptionRcp)]**.

   >[!NOTE]
   >
   >Assurez-vous que vous n&#39;utilisez pas le même certificat pour la version de développement (sandbox) et la version de production de l&#39;application.

1. L’onglet **[!UICONTROL Sons]** permet de spécifier un son à lire. Cliquez sur **[!UICONTROL Ajouter]** et renseignez le champ **[!UICONTROL Nom interne]**. Il doit contenir le nom du fichier incorporé dans l’application ou le nom du son système.

1. Cliquez sur **[!UICONTROL Suivant]** pour passer à la configuration de l’application de développement.

1. Assurez-vous que la même **[!UICONTROL clé d’intégration]** est définie dans Adobe Campaign et dans le code de l’application via le SDK. Pour plus dʼinformations, consultez [cette page](integrating-campaign-sdk-into-the-mobile-application.md). Cette clé d’intégration, spécifique à chaque application, vous permet de lier l’application mobile à la plateforme Adobe Campaign.

   >[!NOTE]
   >
   > La **[!UICONTROL clé d’intégration]** est entièrement personnalisable avec une valeur de chaîne, mais doit être exactement identique à celle spécifiée dans le SDK.

1. Sélectionnez l&#39;une des icônes d’usine dans le champ **[!UICONTROL Icône de l&#39;application]** pour personnaliser l&#39;application mobile dans votre service.

1. Sélectionnez le **[!UICONTROL mode d&#39;authentification]**. Veuillez noter que vous pourrez toujours modifier votre mode d&#39;authentification ultérieurement dans l&#39;onglet **[!UICONTROL Certificat]** de votre application mobile.
   * **[!UICONTROL Authentification basée sur les certificats]** : cliquez sur **[!UICONTROL Renseigner le certificat...]**, sélectionnez votre clé p12 et saisissez le mot de passe fourni par le développeur d&#39;applications mobiles.
   * **[!UICONTROL Authentification basée sur les jetons]** : renseignez les paramètres de connexion **[!UICONTROL Identifiant de la clé]**, **[!UICONTROL Identifiant de l&#39;équipe]** et **[!UICONTROL Identifiant de paquet]**, puis sélectionnez votre certificat p8 en cliquant sur **[!UICONTROL Renseigner la clé privée.]** Pour plus d&#39;informations sur l&#39;**[!UICONTROL authentification basée sur les jetons]**, reportez-vous à la [documentation Apple](https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns).

   >[!NOTE]
   >
   > Adobe recommande l&#39;utilisation d&#39;une **[!UICONTROL authentification basée sur les jetons]** pour votre configuration iOS, car ce mode d&#39;authentification est plus sécurisé et n&#39;est pas lié à l’expiration du certificat.

   ![](assets/nmac_ios_4.png)

1. Vous pouvez cliquer sur **[!UICONTROL Tester la connexion]** pour vous assurer qu’elle fonctionne bien.

1. Cliquez sur **[!UICONTROL Suivant]** pour passer à la configuration de l’application de production et procédez comme décrit ci-dessus.

   ![](assets/nmac_ios_5.png)

1. Cliquez sur **[!UICONTROL Terminer]**.

Votre application iOS est maintenant prête à être utilisée dans Campaign Classic.
