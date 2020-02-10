---
title: Lancement d'Adobe Campaign
seo-title: Lancement d'Adobe Campaign
description: Lancement d'Adobe Campaign
seo-description: null
page-status-flag: never-activated
uuid: c1c5bb0d-ae8e-4b0e-ab39-8b2291162557
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 6652b081-66b6-47a8-97e5-383e3251647e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 51e4d72abf3a1f48700ca38566dbf06dd24594b8

---


# Lancement d&#39;Adobe Campaign{#launching-adobe-campaign}

## Démarrage d&#39;Adobe Campaign {#starting-adobe-campaign}

Vous pouvez démarrer Adobe Campaign en sélectionnant **[!UICONTROL Start / All Programs / Adobe Campaign v.X / Adobe Campaign client console]**.

La page de connexion de la console cliente permet de configurer ou de sélectionner une base de données existante, et de s&#39;y connecter en utilisant un identifiant et un mot de passe :

![](assets/s_ncs_user_login.png)

## Connexion à Adobe Campaign {#connecting-to-adobe-campaign}

Il est possible de vous connecter à Adobe Campaign via votre Adobe ID. Voir à ce sujet [cette page](../../integrations/using/about-adobe-id.md).

Vous pouvez aussi vous connecter via un login/mot de passe dédié :

1. Saisissez l&#39;identifiant du compte opérateur dans le champ **[!UICONTROL login]**.

   L&#39;identifiant vous est fourni par l&#39;administrateur de la plate-forme Adobe Campaign.

1. Enter your password in the **[!UICONTROL Password]** field.

   La première fois que vous accédez à la base de données, votre mot de passe est celui que vous donne l’administrateur. Une fois connecté, vous pouvez modifier votre mot de passe par le **[!UICONTROL Tools > Change password...]** menu. Des détails sur les opérateurs et les connexions sont disponibles dans la gestion des [](../../platform/using/access-management.md)accès.

1. Cliquez sur **[!UICONTROL Log in]** pour confirmer.

Vous pouvez maintenant accéder à l&#39;[espace de travail Adobe Campaign](../../platform/using/adobe-campaign-workspace.md).

## Configuration de connexions {#setting-up-connections}

Vous pouvez accéder aux paramètres de connexion au serveur via le lien situé au-dessus de la zone de saisie.

![](assets/s_ncs_user_connections_management.png)

Dans la **[!UICONTROL Connections]** fenêtre, cliquez sur **[!UICONTROL Add > Connection]**.

![](assets/s_ncs_user_add_connexion.png)

Vous devez ensuite définir les paramètres de cette connexion. Pour cela :

* Enter a **[!UICONTROL Label]** to assign a name to your database connection.
* Ajoutez l’adresse du serveur d’applications dans le **[!UICONTROL URL]** champ. Si vous ne connaissez pas l’URL de connexion, contactez l’administrateur.
* Vérifiez **[!UICONTROL Connect with an Adobe ID]** que les opérateurs se connectent à la console à l’aide de leur Adobe ID. Voir à ce propos [cette page](../../integrations/using/about-adobe-id.md).
* Click **[!UICONTROL OK]** to validate.

>[!NOTE]
>
>Le **[!UICONTROL Add]** bouton vous permet de créer **[!UICONTROL folders]** pour organiser toutes vos connexions. Faites glisser et déposez simplement chaque connexion dans un dossier.

## Opérateurs et permissions {#operators-and-permissions}

The identifiers and passwords of operators with access to the software and their respective permissions are defined by your Adobe Campaign system administrator in the **[!UICONTROL Administration > Access management > Operators]** node of the Adobe Campaign tree.

This functionality is detailed in the [Access management](../../platform/using/access-management.md) section.

## Déconnexion d&#39;Adobe Campaign {#disconnecting-from-adobe-campaign}

Pour vous déconnecter d&#39;Adobe Campaign, utilisez la première icône de la barre d&#39;icônes.

![](assets/s_ncs_user_deconnexion.png)

>[!NOTE]
>
>Vous pouvez également quitter directement l&#39;application, sans vous déconnecter au préalable.

## Obtention de la version de Campaign {#getting-your-campaign-version}

The **[!UICONTROL Help > About...]** menu lets you access the following information:

* numéro de la **version** installée.
* numéro de **build**.
* lien pour contacter l&#39;assistance client Adobe Campaign.

   >[!CAUTION]
   >
   >Lorsque vous contactez l&#39;équipe de l&#39;assistance client Adobe, vous devez indiquer les numéros de version et de build du serveur applicatif et de la console cliente Campaign.

