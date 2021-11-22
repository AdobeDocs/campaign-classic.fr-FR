---
product: campaign
title: Mettre à jour la structure de la base de données
description: Mettre à jour la structure de la base de données
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: 6c1e061b-8636-4285-8d83-97474544d252
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 100%

---

# Mettre à jour la structure de la base de données{#updating-the-database-structure}

![](../../assets/v7-only.svg)

Pour appliquer les modifications apportées dans les schémas, vous devez lancer l&#39;assistant de mise à jour de la base de données. Cet assistant est accessible à partir du menu **[!UICONTROL Outils > Avancé > Mise à jour de la structure de la base]**. Il vérifie si la structure physique de la base est bien conforme à sa description logique et exécute les scripts SQL de mise à jour.

![](assets/d_ncs_integration_schema_update.png)

Les modules présents dans la base de données sont automatiquement renseignés et activés.

![](assets/d_ncs_integration_schema_update_select.png)

Les options **[!UICONTROL Ajouter les procédures stockées]** et **[!UICONTROL Importer les données d&#39;initialisation]** permettent respectivement de lancer les scripts SQL initiaux et les packages de données (&quot;data package&quot;) exécutés lors de la création de la base de données.

Il est possible d&#39;importer un jeu de données provenant d&#39;un package de données externe : pour cela, il faut cocher l&#39;option **[!UICONTROL Importer un package]** et renseigner le fichier XML du package.

Suivez les étapes et visualisez le script SQL de mise à jour de la base de données :

![](assets/d_ncs_integration_schema_update2.png)

>[!NOTE]
>
>Cette zone est en édition et peut être modifiée afin de supprimer ou ajouter du code SQL.

Lancez ensuite la mise à jour de la base de données :

![](assets/d_ncs_integration_schema_update3.png)
