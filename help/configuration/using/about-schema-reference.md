---
product: campaign
title: Prise en main des schémas dans Adobe Campaign
description: Découvrez comment utiliser les schémas et étendre le modèle de données conceptuel de la base de données Adobe Campaign
feature: Schema Extension
role: Developer
level: Intermediate, Experienced
exl-id: f36a1b01-a002-4a21-9255-ea78b5f173fe
TQID: 'https://experienceleague.adobe.com/ikQVjdkvhTM-361S7mcpRYsuhpqjHxX-Y-9wdRCYldg'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
    internal-label: Schemas
subfeature_v2:
  - id: a72a22e0-8c8d-4019-ba42-3f2644aa91a3
    internal-label: Schema extension
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
    internal-label: PI
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: a97306b73a2b577841e6f24536c62b2526e9fda9
workflow-type: ht
source-wordcount: '264'
ht-degree: 100%
---
# Prise en main des schémas {#about-schema-reference}

## Qu’est-ce qu’un schéma ? {#what-is-a-schema}

Ce chapitre explique comment configurer des schémas d’extension afin d’étendre le modèle conceptuel de données de la base de données Adobe Campaign.

Pour une meilleure compréhension des tables intégrées de Campaign et de leur interaction, consultez la section [Modèle de données Campaign Classic](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/developer/datamodel){target="_blank"} (documentation de Campaign v8).

Dans Adobe Campaign, la structure physique et logique des données véhiculées dans l’application est décrite en XML. Un **schéma** est un document XML lié à une table de base de données. Il définit la structure des données et décrit la définition SQL de la table :

* le nom de la table,
* des champs ;
* des index ;
* les liens avec les autres tables,

mais aussi la structure XML utilisée pour stocker les données :

* Eléments et attributs
* la hiérarchie entre les éléments,
* les types des éléments et des attributs,
* Les valeurs par défaut
* les libellés, les descriptions et autres propriétés.

Les schémas vous permettent de définir une entité dans la base de données. À chaque entité correspond un schéma.

L&#39;illustration suivante montre la place des schémas dans le système de données d&#39;Adobe Campaign :

![](assets/reference_schema_intro.png)

Dans le cadre de la transition de Campaign v7 vers v8, la documentation de Campaign Classic a été rationalisé et réorganisé. Les fonctionnalités communes sont désormais disponibles exclusivement dans le jeu de documentation de Campaign v8. Pour en savoir plus sur la syntaxe et l’identification des schémas, consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/developer/schemas-forms/schemas){target=_blank}.

[![Image](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/developer/schemas-forms/schemas){target=_blank}
