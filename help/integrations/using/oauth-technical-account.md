---
product: campaign
title: Création et configuration de votre compte technique d’Adobe pour les API
description: Découvrez comment créer votre compte API Adobe
role: User, Admin
level: Beginner
source-git-commit: efd09fd71069878a5096bfa3592e6ebbaa9dd4e4
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 16%

---

# Créer votre compte technique d’Adobe {#create-service-account}

Les informations d’identification d’authentification serveur à serveur permettent au serveur de votre application de générer des jetons d’accès et d’effectuer des appels API pour le compte de votre application elle-même. [En savoir plus](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/)

## Migration des intégrations existantes {#migrate-jwt}

Les informations d’identification du compte de service (JWT) sont en train d’être abandonnées par Adobe. Les intégrations de Campaign avec les solutions et applications Adobe doivent désormais s’appuyer sur les informations d’identification OAuth Server-to-Server.

Si vous avez implémenté des intégrations entrantes ou sortantes avec Campaign avant juin 2024, vous devez mettre à niveau votre environnement Campaign vers la version 7.4.1 et migrer votre compte technique vers oAuth comme indiqué dans le détail. [dans cette documentation](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration){target="_blank"}. Les informations d’identification de compte de service (JWT) existantes continueront à fonctionner jusqu’à ce que **27 janvier 2025**.

Une fois la migration terminée, vous devez associer vos nouvelles informations d’identification à Campaign, comme expliqué dans la section [cette section](#add-credentials).

## Création d’un compte technique OAuth pour les nouvelles intégrations {#oauth-service}

Pour créer votre compte technique OAuth pour les nouvelles intégrations, procédez comme suit :

1. Accès à la console Adobe Developer et connexion en tant que **Administrateur système** de votre organisation.

   Pour plus d’informations sur les rôles d’administrateur, reportez-vous à cette [page](https://helpx.adobe.com/fr/enterprise/using/admin-roles.html).

1. Cliquez sur **[!UICONTROL Créer un projet]**.

   ![](assets/api-account-1.png)

1. Cliquez sur **[!UICONTROL Ajouter au projet]** et sélectionnez **[!UICONTROL API]**.

   ![](assets/api-account-2.png)

1. Sélectionnez le produit à intégrer à Campaign et cliquez sur **[!UICONTROL Suivant]**.

1. Choisir **[!UICONTROL OAuth serveur à serveur]** comme type d’authentification et cliquez sur **[!UICONTROL Suivant]**.

   ![](assets/api-account-3.png)

1. Sélectionnez la variable **[!UICONTROL Profil de produit]** lien vers votre projet.

   Si nécessaire, vous pouvez en créer un nouveau. [En savoir plus](https://helpx.adobe.com/enterprise/using/manage-product-profiles.html)

1. Cliquez ensuite sur **[!UICONTROL Enregistrer l’API configurée]**.

   ![](assets/api-account-4.png)

1. Dans votre projet, sous Informations d’identification, sélectionnez [!DNL OAuth Server-to-Server] et copiez les informations suivantes :

   * **[!UICONTROL Identifiant du client]**
   * **[!UICONTROL Client secret]**
   * **[!UICONTROL Identifiant du du compte technique]**
   * **[!UICONTROL Identifiant de l&#39;organisation]**

## Ajout des informations d’identification de projet OAuth dans Adobe Campaign {#add-credentials}

Suivez les étapes ci-dessous pour ajouter vos informations d’identification de projet OAuth dans Adobe Campaign :

1. Connectez-vous via SSH à chaque conteneur sur lequel l’instance Adobe Campaign est installée.

1. Ajoutez les informations d’identification de projet OAuth dans Adobe Campaign en exécutant la commande suivante en tant que `neolane` utilisateur. Les informations d&#39;identification du **[!UICONTROL compte technique]** seront alors insérées dans le fichier de configuration de l&#39;instance.

   ```
   nlserver config -instance:<instance_name> -setimsoauth:ims-org-id/client-id/technical-account-id/client-secret
   ```
