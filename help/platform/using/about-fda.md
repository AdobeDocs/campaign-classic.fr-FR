---
title: Accès à une base de données externe
description: Découvrez comment accéder aux données et les traiter dans une base de données externe
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
translation-type: tm+mt
source-git-commit: b447e316bed8e0e87d608679c147e6bd7b0815eb
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 98%

---


# A propos de Federated Data Access {#about-federated-data-access}

Adobe Campaign propose l’option **Federated Data Access** (FDA) afin d’exploiter des informations stockées dans une ou plusieurs bases de données externes : vous pouvez accéder à des données externes sans modifier la structure des données d’Adobe Campaign.

>[!CAUTION]
>
>L’accès à une base de données externe via FDA n’est possible que pour les installations on-premise ou hybrides, sauf avec les connecteurs Snowflake. Pour plus d&#39;informations à ce sujet, consultez cette [page](https://helpx.adobe.com/fr/campaign/kb/acc-on-prem-vs-hosted.html).

## Principe de fonctionnement {#operating-principle}

L’option FDA permet d’étendre votre modèle de données dans une base de données tierce. Le module détecte automatiquement la structure des tables ciblées et utilise les données provenant des sources SQL.

Afin de pouvoir utiliser cette fonctionnalité, vous devez :

1. posséder une base de données externe compatible avec le module FDA d’Adobe Campaign. La liste des systèmes de base de données et des versions compatibles est détaillée dans la [matrice de compatibilité](https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix.html). Les utilisateurs doivent également posséder les [permissions nécessaires](../../platform/using/remote-database-access-rights.md) dans Adobe Campaign et sur la base de données externe.
1. [installer les pilotes](../../platform/using/specific-configuration-database.md) qui correspondent à votre base de données sur le serveur marketing Adobe Campaign.
1. [créer et paramétrer un compte externe](../../platform/using/connecting-to-database.md) permettant d’établir la connexion entre Adobe Campaign et la base externe. Pour plus d’informations sur les comptes externes disponibles, consultez cette [page](../../platform/using/external-accounts.md).
1. [créer le schéma](../../platform/using/creating-data-schema.md) de la base de données externe dans Adobe Campaign. Il est ainsi possible de reconnaître la structure des données de la base de données externe.
1. éventuellement, [créer un mapping de ciblage](../../platform/using/defining-data-mapping.md) à partir du schéma créé précédemment, dans le cas où les destinataires de vos diffusions sont issus de la base externe. Ce cas présente certaines limitations, notamment au niveau de la personnalisation des diffusions.

Une fois le schéma de données créé, les données peuvent être traitées dans Adobe Campaign. Voir à ce propos [cette section](../../workflow/using/accessing-an-external-database--fda-.md).

## Bases de données externes disponibles {#external-database}

Vous trouverez ci-dessous la liste de toutes les bases de données externes compatibles avec le module Adobe Campaign FDA :

* Microsoft Azure Synapse Analytics. Pour plus d’informations à ce sujet, consultez cette [section](../../platform/using/specific-configuration-database.md#azure-external).
* Snowflake. Pour plus d’informations à ce sujet, consultez cette [section](../../platform/using/specific-configuration-database.md#configure-access-to-snowflake).
* Hadoop. Pour plus d’informations à ce sujet, consultez cette [section](../../platform/using/specific-configuration-database.md#configure-access-to-hadoop-3).
* Oracle. Pour plus d’informations à ce sujet, consultez cette [section](../../platform/using/specific-configuration-database.md#configure-access-to-oracle).
* Netezza. Pour plus d’informations à ce sujet, consultez cette [section](../../platform/using/specific-configuration-database.md#configure-access-to-netezza).
* Sybase IQ Pour plus d’informations à ce sujet, consultez cette [section](../../platform/using/specific-configuration-database.md#configure-access-to-sybase-iq).
* Teradata. Pour plus d’informations à ce sujet, consultez cette [section](../../platform/using/specific-configuration-database.md#configure-access-to-teradata).
* SAP HANA. Pour plus d’informations à ce sujet, consultez cette [section](../../platform/using/specific-configuration-database.md).

## Bonnes pratiques et recommandations {#best-practices-and-recommendations}

L’option FDA est conçue pour manipuler les données de bases externes en mode batch dans des workflows. L’utilisation du FDA dans un autre contexte, par exemple pour des opérations unitaires, doit être réalisée avec précaution (Personnalisation, Interaction, diffusions en temps réel, etc.).

Evitez autant que possible les opérations nécessitant d’utiliser à la fois la base Adobe Campaign et la base externe. Pour cela, vous pouvez :

* exporter les données de la base Adobe Campaign vers la base externe et effectuer les opérations uniquement depuis la base externe avant de réimporter les résultats dans Adobe Campaign.
* collecter les données de la base externe dans Adobe Campaign et effectuer les opérations localement.

Si vous souhaitez effectuer de la personnalisation dans vos diffusions à l’aide des données de la base externe, collectez les données à utiliser dans un workflow afin de les rendre disponibles dans une table temporaire. Utilisez alors les données de la table temporaire pour personnaliser votre diffusion.

## Limitations {#limitations}

L’option FDA est assujettie aux limitations du système de la base de données externe que vous utilisez.

Pour des raisons de performance, il est déconseillé d’utiliser cette fonctionnalité afin de réaliser des opérations unitaires (personnalisation de diffusions, module Interaction, temps réel).
