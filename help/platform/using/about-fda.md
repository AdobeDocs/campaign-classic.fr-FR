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
source-git-commit: 47fd157e369ddf6c67f0b2b467799cecc6e5a822

---


# A propos de Federated Data Access {#about-federated-data-access}

Adobe Campaign propose l&#39;option **Federated Data Access** (FDA) afin d&#39;exploiter des informations stockées dans une ou plusieurs bases de données externes : vous pouvez accéder à des données externes sans modifier la structure des données d&#39;Adobe Campaign.

>[!CAUTION]
>
>L&#39;accès à une base de données externe par l&#39;intermédiaire de la FDA n&#39;est possible que pour les installations sur site ou hybrides, sauf avec les connecteurs Snowflake. Pour plus d’informations à ce propos, consultez [cette page](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html).

## Principe de fonctionnement {#operating-principle}

L&#39;option FDA vous permet d&#39;étendre votre modèle de données dans une base de données tierce. Il détecte automatiquement la structure des tables ciblées et utilise les données provenant des sources SQL.


Afin de pouvoir utiliser cette fonctionnalité, vous devez :

1. posséder une base de données externe compatible avec le module FDA d&#39;Adobe Campaign. La liste des systèmes de base de données et des versions compatibles est détaillée dans la [matrice de compatibilité](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html). Les utilisateurs doivent également posséder les [permissions nécessaires](../../platform/using/remote-database-access-rights.md) dans Adobe Campaign et sur la base de données externe.
1. [installer les pilotes](../../platform/using/specific-configuration-database.md) qui correspondent à votre base de données sur le serveur marketing Adobe Campaign.
1. [créer et paramétrer un compte externe](../../platform/using/connecting-to-database.md) permettant d&#39;établir la connexion entre Adobe Campaign et la base externe. Pour plus d&#39;informations sur les comptes externes disponibles, consultez cette [page](../../platform/using/external-accounts.md).
1. [Créez le schéma](../../platform/using/creating-data-schema.md) de la base de données externe dans Adobe Campaign. Vous pouvez ainsi reconnaître la structure des données de la base de données externe.
1. éventuellement, [créer un mapping de ciblage](../../platform/using/defining-data-mapping.md) à partir du schéma créé précédemment, dans le cas où les destinataires de vos diffusions sont issus de la base externe. Ce cas présente certaines limitations, notamment au niveau de la personnalisation des diffusions.

Une fois le schéma de données créé, les données peuvent être traitées dans les processus Adobe Campaign. Voir à ce propos [cette section](../../workflow/using/executing-a-workflow.md#architecture).

## Bonnes pratiques et recommendations {#best-practices-and-recommendations}

L&#39;option FDA est conçue pour manipuler les données de bases externes en mode batch dans des workflows. L&#39;utilisation du FDA dans un autre contexte, par exemple pour des opérations unitaires, doit être réalisée avec précaution (Personnalisation, Interaction, diffusions en temps réel, etc.).

Evitez autant que possible les opérations nécéssitant d&#39;utiliser à la fois la base Adobe Campaign et la base externe. Pour cela, vous pouvez :

* exporter les données de la base Adobe Campaign vers la base externe et effectuer les opérations uniquement depuis la base externe avant de réimporter les résultats dans Adobe Campaign.
* collecter les données de la base externe dans Adobe Campaign et effectuer les opérations localement.

Si vous souhaitez effectuer de la personnalisation dans vos diffusions à l&#39;aide des données de la base externe, collectez les données à utiliser dans un workflow afin de les rendre disponibles dans une table temporaire. Utilisez alors les données de la table temporaire pour personnaliser votre diffusion.

## Limitations {#limitations}

L&#39;option FDA est assujetie aux limitations du système de la base de données externe que vous utilisez.

Pour des raisons de performance, il est déconseillé d&#39;utiliser cette fonctionnalité afin de réaliser des opérations unitaires (personnalisation de diffusions, module Interaction, temps réel).
