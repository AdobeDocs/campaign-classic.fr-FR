---
title: Mettre à jour la structure de la base de données
seo-title: Mettre à jour la structure de la base de données
description: Mettre à jour la structure de la base de données
seo-description: null
page-status-flag: never-activated
uuid: 084dcc7b-f890-4dff-a322-c9a8f1d614b8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: b82ae459-30b5-4a1c-91cc-5c7b8f128333
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Mettre à jour la structure de la base de données{#updating-the-database-structure}

To apply the modifications made to the schemas, launch the database update wizard. This wizard is accessible via **[!UICONTROL Tools > Advanced > Update database structure]** . It checks whether the physical structure of the database matches its logical description and executes the SQL update scripts.

![](assets/d_ncs_integration_schema_update.png)

Les modules présents dans la base de données sont automatiquement renseignés et activés.

![](assets/d_ncs_integration_schema_update_select.png)

The **[!UICONTROL Add stored procedures]** and **[!UICONTROL Import initialization data]** options are used to launch the initial SQL scripts and the data packages executed when the database is created.

Vous pouvez importer un ensemble de données à partir d’un package de données externe. Pour ce faire, sélectionnez **[!UICONTROL Import a package]** et saisissez le fichier XML du package.

Suivez les étapes et visualisez le script SQL de mise à jour de la base de données :

![](assets/d_ncs_integration_schema_update2.png)

>[!NOTE]
>
>Cette zone est en édition et peut être modifiée afin de supprimer ou ajouter du code SQL.

Lancez ensuite la mise à jour de la base de données :

![](assets/d_ncs_integration_schema_update3.png)

