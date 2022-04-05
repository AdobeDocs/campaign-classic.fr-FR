---
product: campaign
title: FAQ destinée aux développeurs
description: FAQ destinée aux développeurs
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 20552812-5c58-4d48-9636-d5135197685d
source-git-commit: f4513834cf721f6d962c7c02c6c64b2171059352
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 100%

---

# FAQ destinée aux développeurs {#dev-faq}

![](../../assets/v7-only.svg)

En tant que solution ouverte, Adobe Campaign est prêt pour la personnalisation et le développement d&#39;applications avancées.

## Quel est le modèle de données de Campaign ?  {#what-is-the-campaign-data-model}

Le modèle de données conceptuel de la base de données Adobe Campaign se compose d’un ensemble de tables intégrées et de leur interaction. La structure physique et logique des données véhiculées dans l&#39;application est décrite en XML et respecte une grammaire propre à Adobe Campaign appelée schéma. Pour plus d’informations sur les schémas Adobe Campaign, [consultez cette section](../../configuration/using/about-schema-edition.md).

[Cliquez ici pour en savoir plus sur le modèle de données de Campaign](https://helpx.adobe.com/fr/campaign/kb/acc-datamodel.html).

Les bonnes pratiques sont répertoriées [dans cet article](../../configuration/using/data-model-best-practices.md).

## Comment utiliser des schémas de Campaign ? {#how-to-work-with-campaign-schemas-}

Dans Adobe Campaign, les schémas de données permettent de :

* définir la façon dont les objets de l&#39;application sont liés à des tables de la base de données ;
* définir des liens entre les différents objets de l&#39;application ;
* définir et décrire les champs individuels inclus dans chaque objet.

Consultez la section sur [la prise en main des tables et schémas](../../configuration/using/about-schema-edition.md) pour comprendre comment utiliser les schémas de données, étendre et personnaliser Campaign afin de répondre à vos besoins.

## Comment utiliser une table de destinataires personnalisée ? {#how-to-use-a-custom-recipient-table-}

Vous pouvez créer et implémenter une table des destinataires non intégrée dans Campaign pour envoyer vos messages.

[Pour en savoir plus, cliquez ici.](../../configuration/using/about-custom-recipient-table.md)

## Quelles sont les bonnes pratiques pour définir des requêtes dans Campaign ?  {#what-are-the-best-practices-to-define-queries-in-campaign-}

Le requêteur Adobe Campaign est un outil puissant permettant d&#39;explorer les données et de créer des segments.

L&#39;outil de requêtage est présent à de nombreux niveaux de la plateforme Adobe Campaign : pour créer une population cible, segmenter les clients, extraire et filtrer des logs de tracking, construire des filtres, etc.

Vous pouvez interroger la base de données Campaign grâce au requêteur générique. Il est accessible depuis le menu **Outils > Requêteur générique...**. Il permet d&#39;extraire des informations stockées dans une base de données, les organiser, les regrouper, les trier, etc. Par exemple, l&#39;utilisateur peut récupérer les destinataires ayant cliqué plus de &#39;n&#39; fois dans le lien d&#39;une newsletter et sur une période donnée. Il pourra organiser la collecte, le tri et l&#39;affichage des résultats selon ses besoins. Cet outil regroupe toutes les possibilités de requêtage d&#39;Adobe Campaign. Par exemple, il permet la création et la sauvegarde des filtres de restriction. Ainsi, un filtre utilisateur créé dans le requêteur générique est réutilisable dans la boîte de requête d&#39;un workflow de ciblage, etc.

Les requêtes sont créées soit avec les champs disponibles de la table sélectionnée, soit à l&#39;aide d&#39;une formule. Les principes de base pour créer une requête sur la base de données Campaign sont présentés [dans cette page](../../platform/using/about-queries-in-campaign.md).

[Cliquez ici](../../workflow/using/query.md) pour découvrir le requêteur de Campaign.

## Comment importer un package de données ?  {#how-can-i-import-a-data-package-}

Adobe Campaign vous permet d&#39;exporter ou d&#39;importer la configuration et les données de la plateforme grâce à un système de packages. Les packages de données permettent l&#39;affichage des entités de la base de données Adobe Campaign à l&#39;aide de fichiers au format XML. Chaque entité contenue dans un package est représentée avec l&#39;ensemble de ses données.

Le principe des packages de données consiste à exporter un paramétrage de données puis l&#39;intégrer dans un autre système Adobe Campaign.

[Cliquez ici](../../platform/using/working-with-data-packages.md) pour découvrir comment utiliser les packages de données pour importer et exporter des configurations Campaign.

## Où puis-je trouver la liste des API Campaign Classic ?  {#where-can-i-find-the-list-of-campaign-classic-apis}

Toutes les API de Campaign, y compris leur description complète, sont disponibles dans cette [documentation dédiée](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=fr).
