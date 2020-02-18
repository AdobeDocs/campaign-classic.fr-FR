---
title: Accès à une base de données externe
seo-title: Accès à une base de données externe
description: Accès à une base de données externe
seo-description: null
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d2758b5e81d1720a4f01a610e51c4a33995d88d1

---


# Utiliser les données d&#39;une base externe dans un workflow {#using-data-from-an-external-database-in-a-workflow}

Dans plusieurs activités des workflows Adobe Campaign, vous pouvez utiliser les données stockées dans une base externe.

## Filtrer sur les données externes {#filtering-on-external-data}

L&#39;activité de requête permet d&#39;ajouter des données externes et de les utiliser dans les paramètres de filtrage définis.

Voir à ce sujet la section [Requête](../../workflow/using/targeting-data.md#selecting-data).

## Construire des sous-ensembles {#creating-sub-sets}

L&#39;activité de partage permet de construire des sous-ensembles. Vous pouvez utiliser des données externes pour définir les critères de filtrage à utiliser.

Voir à ce sujet la section [Partage](../../workflow/using/split.md).

## Charger des données externes {#loading-external-database}

Vous pouvez utiliser les données externes dans l&#39;activité de chargement (SGBD). Cette activité est présentée dans la section [Chargement](../../workflow/using/data-loading--rdbms-.md).

## Ajouter des informations et des liens {#adding-information-and-links}

L&#39;activité d&#39;enrichissement permet d&#39;ajouter des données additionnelles à la table de travail du workflow ainsi que des liens vers une table externe. Elle peut pour cela exploiter les données d&#39;une base de données externe. Cette activité est présentée dans la section [Enrichissement](../../workflow/using/enrichment.md).
