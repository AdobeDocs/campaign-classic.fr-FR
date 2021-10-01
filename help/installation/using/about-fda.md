---
product: campaign
title: Accès à une base de données externe
description: Découvrez comment accéder aux données et les traiter dans une base de données externe
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 9d8d1e9c-63e4-40c4-8338-b921d08ea405
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: ht
source-wordcount: '166'
ht-degree: 100%

---

# Prise en main de Federated Data Access {#about-federated-data-access}

![](../../assets/v7-only.svg)

Adobe Campaign propose l’option **Federated Data Access** (FDA) afin d’exploiter des informations stockées dans une ou plusieurs bases de données externes : vous pouvez accéder à des données externes sans modifier la structure des données d’Adobe Campaign.

## Conditions préalables requises {#operating-principle}

L’option FDA permet d’étendre votre modèle de données dans une base de données tierce. Le module détecte automatiquement la structure des tables ciblées et utilise les données provenant des sources SQL.

Pour utiliser cette fonctionnalité, les prérequis sont énumérés ci-dessous :

* **Configuration** : à l’exception de Snowflake, vous avez besoin d’un modèle d’hébergement **On-Premise** ou **hybride** pour configurer Federated Data Access. [En savoir plus](../../installation/using/hosting-models.md)
* **Version de base de données externe** : vous devez disposer d’une base de données externe compatible avec le module Adobe Campaign FDA. La liste des systèmes de base de données et des versions compatibles est détaillée dans la [matrice de compatibilité](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA) de Campaign.
* **Autorisations** : les utilisateurs doivent également disposer des autorisations [](../../installation/using/remote-database-access-rights.md) nécessaires dans Adobe Campaign et dans la base de données externe.

