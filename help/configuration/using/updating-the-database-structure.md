---
product: campaign
title: Mettre à jour la structure de la base de données
description: Mettre à jour la structure de la base de données
feature: Configuration
role: Developer
exl-id: 6c1e061b-8636-4285-8d83-97474544d252
TQID: 'https://experienceleague.adobe.com/y4P6bZcEyVIdfI4LHMivPIRVzb1Z4sV7ewISWqk29F0'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: a14877cc-63b1-41d9-bf0b-5f97cadd0417
    internal-label: Configuration guidelines
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 100%
---
# Mettre à jour la structure de la base de données{#updating-the-database-structure}



Pour appliquer les modifications apportées dans les schémas, lancez l’assistant de mise à jour de la base de données. Cet assistant est accessible via **[!UICONTROL Outils > Avancé > Mise à jour de la structure de la base de données]**. Il vérifie que la structure physique de la base de données correspond bien à sa description logique et exécute les scripts de mise à jour SQL.

![](assets/d_ncs_integration_schema_update.png)

Les modules présents dans la base de données sont automatiquement renseignés et activés.

![](assets/d_ncs_integration_schema_update_select.png)

Les options **[!UICONTROL Ajouter les procédures stockées]** et **[!UICONTROL Importer les données d&#39;initialisation]** permettent respectivement de lancer les scripts SQL initiaux et les packages de données (&quot;data package&quot;) exécutés lors de la création de la base de données.

Il est possible d&#39;importer un jeu de données provenant d&#39;un package de données externe : Pour ce faire, sélectionnez **[!UICONTROL Importer un package]** et saisissez le fichier XML du package.

Suivez les étapes et visualisez le script SQL de mise à jour de la base de données :

![](assets/d_ncs_integration_schema_update2.png)

>[!NOTE]
>
>Cette zone est en édition et peut être modifiée afin de supprimer ou ajouter du code SQL.

Lancez ensuite la mise à jour de la base de données :

![](assets/d_ncs_integration_schema_update3.png)
