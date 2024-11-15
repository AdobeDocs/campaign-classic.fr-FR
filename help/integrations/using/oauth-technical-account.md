---
product: campaign
title: Créer et configurer votre compte technique Adobe pour les API
description: En savoir plus sur la création de compte API Adobe
role: User, Admin
level: Beginner
exl-id: 5d830ea0-a0a3-4b35-8dc4-e955380431fb
source-git-commit: 5352426fc68cbcb6519127e5c89c1e9f8619ca6b
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 97%

---

# Créer votre compte technique Adobe {#create-service-account}

Les informations d’identification d’authentification serveur à serveur permettent au serveur de votre application de générer des jetons d’accès et d’effectuer des appels API pour le compte de votre application. [En savoir plus](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/)

## Migrer des intégrations existantes {#migrate-jwt}

Les informations d’identification du compte de service (JWT) sont en train d’être abandonnées par Adobe. Les intégrations de Campaign aux solutions et applications Adobe doivent désormais s’appuyer sur les informations d’identification OAuth de serveur à serveur.

Si vous avez implémenté des intégrations entrantes ou sortantes à Campaign avant juin 2024, vous devez mettre à niveau votre environnement Campaign vers la version 7.4.1 et migrer votre compte technique vers oAuth comme indiqué dans [dans cette documentation](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration){target="_blank"}. Les informations d’identification de compte de service (JWT) existantes continueront à fonctionner jusqu’qu’au **27 janvier 2025**.

Une fois la migration terminée, vous devez associer vos nouvelles informations d’identification à Campaign, comme expliqué dans [cette section](#add-credentials).

## Créer un nouveau compte technique OAuth pour les nouvelles intégrations {#oauth-service}

Pour créer votre compte technique OAuth pour les nouvelles intégrations, procédez comme suit :

1. Accédez à Adobe Developer Console et connectez-vous en tant qu’**administrateur ou administratrice système** de votre organisation.

   Pour plus d’informations sur les rôles d’administrateur, reportez-vous à cette [page](https://helpx.adobe.com/fr/enterprise/using/admin-roles.html).

1. Cliquez sur **[!UICONTROL Créer un projet]**.

   ![](assets/api-account-1.png)

1. Cliquez sur **[!UICONTROL Ajouter au projet]** et sélectionnez **[!UICONTROL API]**.

   ![](assets/api-account-2.png)

1. Sélectionnez le produit à intégrer à Campaign et cliquez sur **[!UICONTROL Suivant]**.

1. Choisissez **[!UICONTROL OAuth serveur à serveur]** comme type d’authentification et cliquez sur **[!UICONTROL Suivant]**.

   ![](assets/api-account-3.png)

1. Sélectionnez le lien **[!UICONTROL Profil de produit]** vers votre projet.

   Si nécessaire, vous pouvez en créer un nouveau. [En savoir plus](https://helpx.adobe.com/fr/enterprise/using/manage-product-profiles.html)

1. Cliquez ensuite sur **[!UICONTROL Enregistrer l’API configurée]**.

   ![](assets/api-account-4.png)

1. Dans votre projet, sous Informations d’identification, sélectionnez [!DNL OAuth Server-to-Server] et copiez les informations suivantes :

   * **[!UICONTROL Identifiant du client]**
   * **[!UICONTROL Secret client]**
   * **[!UICONTROL Identifiant du du compte technique]**
   * **[!UICONTROL Identifiant de l&#39;organisation]**

## Ajouter des informations d’identification de projet OAuth dans Campaign {#add-credentials}

Après la réalisation des étapes ci-dessus, ajoutez vos informations d’identification de projet OAuth dans Adobe Campaign.

>[!NOTE]
>
>En tant que client hébergé ou cliente hébergée ou Managed Cloud Service, ces étapes ne sont pas nécessaires : Adobe a déjà ajouté les informations d’identification de votre projet OAuth à votre environnement.
>

En tant que client ou cliente on-premise ou hybride, procédez comme suit :

1. Connectez-vous via SSH à chaque conteneur sur lequel l’instance Adobe Campaign est installée.

1. Ajoutez les informations d’identification de projet OAuth dans Adobe Campaign en exécutant la commande suivante en tant qu’utilisateur ou utilisatrice `neolane`. Les informations d’identification du **[!UICONTROL compte technique]** seront alors insérées dans le fichier de configuration de l’instance.

   ```
   nlserver config -instance:<instance_name> -setimsoauth:ims-org-id/client-id/technical-account-id/client-secret
   ```

   >[!NOTE]
   >
   > Pour les versions antérieures à la version 7.4.1, utilisez `setimsauth` ou `setimsjwtauth` au lieu de `setimsoauth`.


