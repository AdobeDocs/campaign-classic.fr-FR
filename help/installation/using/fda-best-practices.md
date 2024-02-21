---
product: campaign
title: Bonnes pratiques et limites de FDA dans Campaign
description: Découvrez les bonnes pratiques et les limites de l’utilisation d’une base de données externe (FDA)
feature: Installation, Federated Data Access
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: f3980859-2837-416b-a0ef-2b369d2d50bd
source-git-commit: 668cee663890fafe27f86f2afd3752f7e2ab347a
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 100%

---

# Bonnes pratiques et limites



## Optimiser la personnalisation d’un e-mail avec des données externes {#optimizing-email-personalization-with-external-data}

Vous pouvez prétraiter la personnalisation des messages dans un workflow dédié. Pour ce faire, utilisez l&#39;option **[!UICONTROL Préparer les données de personnalisation avec un workflow]**, disponible dans l&#39;onglet **[!UICONTROL Analyse]** des propriétés de la diffusion.

Cette option permet, lors de l&#39;analyse de la diffusion, de créer et d&#39;exécuter automatiquement un workflow qui stocke toutes les données liées à la cible dans une table temporaire, notamment les données issues des tables liées dans une base de données externe.

Cette option améliore considérablement les performances lors de l&#39;exécution de l&#39;étape de personnalisation.

## Utiliser les données d’une base de données externe dans un workflow {#using-data-from-an-external-database-in-a-workflow}

Dans plusieurs activités des workflows Adobe Campaign, vous pouvez utiliser les données stockées dans une base de données externe.

* **Filtrer sur les données externes** - L&#39;activité de [requête](../../workflow/using/targeting-data.md#selecting-data) permet d&#39;ajouter des données externes et de les utiliser dans les paramètres de filtrage définis. Voir à ce propos [cette page](../../workflow/using/targeting-data.md#selecting-data).

* **Créer des sous-ensembles** : l&#39;activité de [partage](../../workflow/using/split.md) vous permet de créer des sous-ensembles. Vous pouvez utiliser des données externes pour définir les critères de filtrage à utiliser. Pour plus d’informations, consultez [cette page](../../workflow/using/split.md).

* **Charger la base de données externe** : vous pouvez utiliser les données externes dans l&#39;activité de [chargement](../../workflow/using/data-loading-rdbms.md) (SGBD). En savoir plus sur [cette page](../../workflow/using/data-loading-rdbms.md).

* **Ajouter des informations et des liens** - L’activité d’[Enrichissement](../../workflow/using/enrichment.md) permet d’ajouter des données supplémentaires à la table de travail du workflow et de créer des liens vers une table externe. Dans ce contexte, elle peut utiliser des données provenant d’une base de données externe. En savoir plus sur [cette page](../../workflow/using/enrichment.md).

## Limites de FDA {#limitations}

L&#39;option FDA est utilisée pour manipuler les données des bases de données externes en mode batch dans les workflows. Pour éviter les problèmes de performance, il n&#39;est pas recommandé d&#39;utiliser le module FDA dans le cadre d&#39;opérations unitaires, par exemple : personnalisation, interaction, messagerie en temps réel, etc.

Evitez autant que possible les opérations nécessitant d&#39;utiliser à la fois la base Adobe Campaign et la base externe. Pour cela, vous pouvez :

* exporter les données de la base Adobe Campaign vers la base externe et effectuer les opérations uniquement depuis la base externe avant de réimporter les résultats dans Adobe Campaign.

* collecter les données de la base externe dans Adobe Campaign et effectuer les opérations localement.

Si vous souhaitez effectuer de la personnalisation dans vos diffusions à l&#39;aide des données de la base externe, collectez les données à utiliser dans un workflow afin de les rendre disponibles dans une table temporaire. Utilisez alors les données de la table temporaire pour personnaliser votre diffusion.

L&#39;option FDA est assujettie aux limitations du système de la base de données externe que vous utilisez.
