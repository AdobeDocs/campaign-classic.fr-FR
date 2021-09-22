---
solution: Campaign Classic
product: campaign
title: Connecteur Adobe Analytics
description: En savoir plus sur le connecteur Adobe Analytics approvisionnement
feature: Overview
role: User, Admin
level: Beginner
source-git-commit: 5f596c14639e085edab9c08c2e3abba36e76acd3
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 7%

---

# Approvisionnement d’Adobe Analytics Connector {#adobe-analytics-connector-provisioning}

![](../../assets/v7-only.svg)

>[!IMPORTANT]
>
> Ces étapes ne doivent être effectuées que par des implémentations hybrides et On-Premise.
>
>Pour les implémentations hébergées, contactez l’ [Assistance clientèle Adobe](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) équipe.

L’intégration entre l’authentification Adobe Campaign Classic et Adobe Analytics prend en charge Adobe Identity Management Service (IMS). Vous devez mettre en oeuvre Adobe IMS et vous connecter à Campaign [via une Adobe ID](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/connect-to-campaign/connecting-via-an-adobe-id/about-adobe-id.html?lang=en), avant de démarrer l’implémentation d’Analytics Connector.

Pour que cette intégration fonctionne, vous devez créer un profil de produit Adobe Analytics qui sera utilisé exclusivement pour le connecteur Analytics. Vous devez ensuite créer un projet Adobe I/O.

## Création d’un profil de produit Adobe Analytics {#analytics-product-profile}

Le profil de produit détermine le niveau d’accès d’un utilisateur à vos différents composants Analytics.

Si vous disposez déjà d’un profil de produit Analytics, vous devez tout de même créer un nouveau profil de produit Adobe Analytics utilisé exclusivement pour le connecteur Analytics. Cela permet de s’assurer que votre profil de produit est défini avec les autorisations appropriées pour cette intégration.

Pour plus d’informations sur les profils de produit, consultez la [documentation de la console d’administration](https://helpx.adobe.com/mt/enterprise/admin-guide.html).

1. Dans la [console d’administration](https://adminconsole.adobe.com/), sélectionnez votre **[!UICONTROL produit Adobe Analytics]**.

   ![](assets/do-not-localize/triggers_1.png)

1. Cliquez sur **[!UICONTROL Nouveau profil]**.

   ![](assets/do-not-localize/triggers_2.png)

1. Ajoutez un **[!UICONTROL nom de profil de produit]**, nous vous suggérons d’utiliser la syntaxe suivante : `reserved_campaign_classic_<Company Name>`. Cliquez ensuite sur **[!UICONTROL Suivant]**.

   Ce **[!UICONTROL profil de produit]** doit être utilisé exclusivement pour Analytics Connector afin d’éviter les erreurs de configuration incorrectes.

1. Ouvrez le **[!UICONTROL profil de produit]** que vous venez de créer et sélectionnez l’onglet **[!UICONTROL Autorisations]** .

   ![](assets/do-not-localize/triggers_3.png)

1. Configurez les différentes fonctionnalités en cliquant sur **[!UICONTROL Modifier]** et sélectionnez les autorisations à attribuer à votre **[!UICONTROL profil de produit]** en cliquant sur l’icône plus (+).

   Pour plus d’informations sur la gestion des autorisations, consultez la [documentation de la console d’administration](https://helpx.adobe.com/mt/enterprise/using/manage-permissions-and-roles.html).

1. Pour la fonctionnalité **[!UICONTROL Report Suites]**, ajoutez les **[!UICONTROL Report Suites]** que vous devez utiliser ultérieurement.

   Si vous ne disposez d’aucune suite de rapports, vous pouvez la créer en suivant [ces étapes](../../platform/using/adobe-analytics-connector.md#report-suite-analytics).

   ![](assets/do-not-localize/triggers_4.png)

1. Pour la fonctionnalité **[!UICONTROL Mesures]**, ajoutez les **[!UICONTROL Mesures]** que vous devrez configurer ultérieurement.

   Si nécessaire, vous pouvez activer l’option Auto-include (Inclusion automatique) qui ajoute chaque élément d’autorisation à la liste incluse et ajoute automatiquement de nouveaux éléments d’autorisation.

   ![](assets/do-not-localize/triggers_13.png)

1. Pour la fonctionnalité **[!UICONTROL Dimensions]**, ajoutez les **[!UICONTROL Dimensions]** que vous devrez configurer ultérieurement.

1. Pour la fonctionnalité **[!UICONTROL Outils de suites de rapports]**, ajoutez les autorisations suivantes :

   * **[!UICONTROL Gestion des suites de rapports]**
   * **[!UICONTROL Variables de conversion]**
   * **[!UICONTROL Événements de succès]**
   * **[!UICONTROL Rapport personnalisé de Data Warehouse]**
   * **[!UICONTROL Gestionnaire des sources de données]**
   * **[!UICONTROL Classifications]**

1. Pour la fonctionnalité **[!UICONTROL Outils Analytics]**, ajoutez les autorisations suivantes :

   * **[!UICONTROL Gestionnaire de code - Services web]**
   * **[!UICONTROL Logs - Web services]**
   * **[!UICONTROL Services web]**
   * **[!UICONTROL Accès aux services web]**
   * **[!UICONTROL Création de mesures calculées]**
   * **[!UICONTROL Création de segment]**

Votre profil de produit est maintenant configuré. Vous devez ensuite créer le projet Adobe I/O.

## Créer un projet d’Adobe I/O {#create-adobe-io}

1. Accédez à l’Adobe I/O et connectez-vous en tant qu’**administrateur système** de l’organisation IMS.

   Pour plus d’informations sur les rôles d’administrateur, consultez cette [page](https://helpx.adobe.com/enterprise/using/admin-roles.html).

1. Cliquez sur **[!UICONTROL Créer un projet]**.

   ![](assets/do-not-localize/triggers_5.png)

1. Cliquez sur **[!UICONTROL Ajouter au projet]** et sélectionnez **[!UICONTROL API]**.

   ![](assets/do-not-localize/triggers_6.png)

1. Sélectionnez [!DNL Adobe Analytics] et cliquez sur **[!UICONTROL Suivant]**.

   ![](assets/do-not-localize/triggers_7.png)

1. Choisissez **[!UICONTROL Compte de service (JWT)]** comme type d’authentification et cliquez sur **[!UICONTROL Suivant]**.

   ![](assets/do-not-localize/triggers_8.png)

1. Sélectionnez l&#39;**[!UICONTROL Option 1 : Générez une option Key-Pair]** et cliquez sur **[!UICONTROL Générer une paire de clés]**.

   Le fichier config.zip est alors automatiquement téléchargé.

   ![](assets/do-not-localize/triggers_9.png)

1. Cliquez sur **[!UICONTROL Suivant]**.

   ![](assets/do-not-localize/triggers_10.png)

1. Sélectionnez le **[!UICONTROL Profil produit]** créé lors des étapes précédentes, détaillées dans cette [section](#analytics-product-profile).

1. Cliquez ensuite sur **[!UICONTROL Enregistrer l’API configurée]**.

   ![](assets/do-not-localize/triggers_11.png)

1. Dans votre projet, sélectionnez [!DNL Adobe Analytics] et copiez les informations suivantes sous **[!UICONTROL Compte Service (JWT)]** :

   * **[!UICONTROL Identifiant du client]**
   * **[!UICONTROL Secret du client]**
   * **[!UICONTROL Identifiant du du compte technique]**
   * **[!UICONTROL Identifiant de l&#39;organisation]**

   ![](assets/do-not-localize/triggers_12.png)

1. Collez ces informations d’identification du compte de service dans le nlserver à l’aide de la commande suivante :

   ```
   nlserver config -instance:<instanceName> -setimsjwtauth::<ImsOrgId>/<ClientId>/<TechnicalAccountId>/<ClientSecret>/<$(base64 -w0 /path/to/private.key)>
   ```

Vous pouvez maintenant commencer à utiliser le connecteur Analytics et suivre les comportements de vos clients.
