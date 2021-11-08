---
solution: Campaign Classic
product: campaign
title: Connecteur Adobe Analytics
description: En savoir plus sur le connecteur Adobe Analytics approvisionnement
feature: Overview
role: User, Admin
level: Beginner
exl-id: 24e002aa-4e86-406b-92c7-74f242ee4b86
source-git-commit: 0830e7b8a430fa18bc1326b972741e2e4dc76342
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 100%

---

# Approvisionnement du connecteur Adobe Analytics {#adobe-analytics-connector-provisioning}

![](../../assets/v7-only.svg)

>[!IMPORTANT]
>
> Ces étapes ne doivent être effectuées que par des implémentations hybrides et On-Premise.
>
>Pour les implémentations hébergées, contactez l’[Assistance clientèle d’Adobe](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

L’intégration entre l’authentification Adobe Campaign Classic et Adobe Analytics prend en charge Adobe Identity Management Service (IMS). Vous devez implémenter Adobe IMS et vous connecter à Campaign [via un Adobe ID](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/connect-to-campaign/connecting-via-an-adobe-id/about-adobe-id.html?lang=fr) avant de démarrer l’implémentation du connecteur Analytics.

Pour que cette intégration fonctionne, vous devez créer un profil produit Adobe Analytics qui sera utilisé exclusivement pour le connecteur Analytics. Vous devez ensuite créer un projet Adobe I/O.

## Création d’un profil produit Adobe Analytics {#analytics-product-profile}

Le profil produit détermine le niveau d’accès d’un utilisateur à vos différents composants Analytics.

Si vous disposez déjà d’un profil produit Analytics, vous devez tout de même créer un profil produit Adobe Analytics qui sera utilisé exclusivement pour le connecteur Analytics. Cela permet de s’assurer que votre profil produit est défini avec les autorisations appropriées pour cette intégration.

Pour en savoir plus sur les profils produit, consultez la [documentation relative à Admin Console](https://helpx.adobe.com/fr/enterprise/admin-guide.html).

1. Dans [Admin Console](https://adminconsole.adobe.com/), sélectionnez votre **[!UICONTROL Produit]** Adobe Analytics.

   ![](assets/do-not-localize/triggers_1.png)

1. Cliquez sur **[!UICONTROL Nouveau profil]**.

   ![](assets/do-not-localize/triggers_2.png)

1. Ajoutez un **[!UICONTROL Nom de profil produit]**. Nous vous suggérons d’utiliser la syntaxe suivante : `reserved_campaign_classic_<Company Name>`. Cliquez ensuite sur **[!UICONTROL Suivant]**.

   Ce **[!UICONTROL Profil produit]** doit être utilisé exclusivement pour le connecteur Analytics, ceci afin d’éviter les erreurs de configuration incorrecte.

1. Ouvrez le **[!UICONTROL Profil produit]** que vous venez de créer et sélectionnez l’onglet **[!UICONTROL Autorisations]**.

   ![](assets/do-not-localize/triggers_3.png)

1. Configurez les différentes fonctionnalités en cliquant sur **[!UICONTROL Modifier]**, puis sélectionnez les autorisations à attribuer à votre **[!UICONTROL Profil produit]** en cliquant sur l’icône représentant un plus (+).

   Pour en savoir plus sur la gestion des autorisations, consultez la [documentation relative à Admin Console](https://helpx.adobe.com/fr/enterprise/using/manage-permissions-and-roles.html).

1. Pour la fonctionnalité **[!UICONTROL Suites de rapports]**, ajoutez les **[!UICONTROL Suites de rapports]** dont vous aurez besoin ultérieurement.

   Si vous ne disposez d’aucune suite de rapports, vous pouvez en créer une en suivant [cette procédure](../../platform/using/adobe-analytics-connector.md#report-suite-analytics).

   ![](assets/do-not-localize/triggers_4.png)

1. Pour la fonctionnalité **[!UICONTROL Mesures]**, ajoutez les **[!UICONTROL Mesures]** que vous devrez configurer ultérieurement.

   Si nécessaire, vous pouvez activer l’option Inclusion automatique, qui ajoute chaque élément d’autorisation dans la liste incluse et ajoute automatiquement de nouveaux éléments d’autorisation.

   ![](assets/do-not-localize/triggers_13.png)

1. Pour la fonctionnalité **[!UICONTROL Dimensions]**, ajoutez les **[!UICONTROL Dimensions]** que vous devrez configurer ultérieurement.

1. Pour la fonctionnalité **[!UICONTROL Outils de suites de rapports]**, ajoutez les autorisations suivantes :

   * **[!UICONTROL Gestion des suites de rapports]**
   * **[!UICONTROL Variables de conversion]**
   * **[!UICONTROL Événements de succès]**
   * **[!UICONTROL Rapport Data Warehouse personnalisé]**
   * **[!UICONTROL Gestionnaire des sources de données]**
   * **[!UICONTROL Classifications]**

1. Pour la fonctionnalité **[!UICONTROL Outils Analytics]**, ajoutez les autorisations suivantes :

   * **[!UICONTROL Gestionnaire de code - Services web]**
   * **[!UICONTROL Logs - Services web]**
   * **[!UICONTROL Services web]**
   * **[!UICONTROL Accès aux services web]**
   * **[!UICONTROL Création de mesure calculée]**
   * **[!UICONTROL Création de segment]**

Votre profil produit est désormais configuré. Vous devez ensuite créer le projet Adobe I/O.

## Création de projet Adobe I/O {#create-adobe-io}

1. Accédez à Adobe I/O et connectez-vous en tant qu’**Administrateur système** pour I’organisation IMS.

   Pour plus d’informations sur les rôles d’administrateur, reportez-vous à cette [page](https://helpx.adobe.com/fr/enterprise/using/admin-roles.html).

1. Cliquez sur **[!UICONTROL Créer un projet]**.

   ![](assets/do-not-localize/triggers_5.png)

1. Cliquez sur **[!UICONTROL Ajouter au projet]** et sélectionnez **[!UICONTROL API]**.

   ![](assets/do-not-localize/triggers_6.png)

1. Sélectionnez [!DNL Adobe Analytics] et cliquez sur **[!UICONTROL Suivant]**.

   ![](assets/do-not-localize/triggers_7.png)

1. Choisissez **[!UICONTROL Compte Service (JWT)]** comme type d’authentification et cliquez sur **[!UICONTROL Suivant]**.

   ![](assets/do-not-localize/triggers_8.png)

1. Sélectionnez l’**[!UICONTROL Option 1 : générer une paire de clés]** et cliquez sur **[!UICONTROL Générer une paire de clés]**.

   Le fichier config.zip est alors automatiquement téléchargé.

   ![](assets/do-not-localize/triggers_9.png)

1. Cliquez sur **[!UICONTROL Suivant]**.

   ![](assets/do-not-localize/triggers_10.png)

1. Sélectionnez le **[!UICONTROL Profil produit]** créé lors des étapes précédentes détaillées dans cette [section](#analytics-product-profile).

1. Cliquez ensuite sur **[!UICONTROL Enregistrer l’API configurée]**.

   ![](assets/do-not-localize/triggers_11.png)

1. Dans votre projet, sélectionnez [!DNL Adobe Analytics] et copiez les informations suivantes sous **[!UICONTROL Compte Service (JWT)]** :

   * **[!UICONTROL Identifiant du client]**
   * **[!UICONTROL Secret du client]**
   * **[!UICONTROL Identifiant du du compte technique]**
   * **[!UICONTROL Identifiant de l&#39;organisation]**

   ![](assets/do-not-localize/triggers_12.png)

1. Collez ces identifiants du Compte de service dans nlserver à l’aide de la commande suivante :

   ```
   nlserver config -instance:<instanceName> -setimsjwtauth::<ImsOrgId>/<ClientId>/<TechnicalAccountId>/<ClientSecret>/<$(base64 -w0 /path/to/private.key)>
   ```

Vous pouvez maintenant commencer à utiliser le connecteur Analytics et suivre les comportements de vos clients.
