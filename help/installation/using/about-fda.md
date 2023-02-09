---
product: campaign
title: Prise en main de Federated Data Access
description: Découvrez comment accéder aux données et les traiter dans une base de données externe.
feature: Federated Data Access
exl-id: 9d8d1e9c-63e4-40c4-8338-b921d08ea405
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 100%

---

# Prise en main de Federated Data Access {#about-federated-data-access}

![](../../assets/v7-only.svg)

Adobe Campaign propose l’option **Federated Data Access** (FDA) afin d’exploiter des informations stockées dans une ou plusieurs bases de données externes : vous pouvez accéder à des données externes sans modifier la structure des données d’Adobe Campaign.

## Conditions préalables requises {#operating-principle}

L’option FDA permet d’étendre votre modèle de données dans une base de données tierce. Le module détecte automatiquement la structure des tables ciblées et utilise les données provenant des sources SQL.

Pour utiliser cette fonctionnalité, les prérequis sont énumérés ci-dessous :

* **Configuration** : la liste des bases de données externes compatibles dépend de votre [modèle d’hébergement](../../installation/using/hosting-models.md).
* **Version de base de données externe** : vous devez disposer d’une base de données externe compatible avec le module Adobe Campaign FDA.

   La liste des systèmes de base de données et des versions compatibles par modèle d’hébergement est détaillée dans la [matrice de compatibilité](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA) de Campaign.

* **Autorisations** : les utilisateurs doivent également disposer des [autorisations nécessaires](../../installation/using/remote-database-access-rights.md) dans Adobe Campaign et dans la base de données externe.

