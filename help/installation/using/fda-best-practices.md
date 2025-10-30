---
product: campaign
title: Bonnes pratiques et limites de FDA dans Campaign
description: Découvrez les bonnes pratiques et les limites de l’utilisation d’une base de données externe (FDA)
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: f3980859-2837-416b-a0ef-2b369d2d50bd
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: ht
source-wordcount: '471'
ht-degree: 100%

---

# Bonnes pratiques et limites



## Optimiser la personnalisation d’un e-mail avec des données externes {#optimizing-email-personalization-with-external-data}

Vous pouvez prétraiter la personnalisation des messages dans un workflow dédié. Pour ce faire, utilisez l&#39;option **[!UICONTROL Préparer les données de personnalisation avec un workflow]**, disponible dans l&#39;onglet **[!UICONTROL Analyse]** des propriétés de la diffusion.

Cette option permet, lors de l&#39;analyse de la diffusion, de créer et d&#39;exécuter automatiquement un workflow qui stocke toutes les données liées à la cible dans une table temporaire, notamment les données issues des tables liées dans une base de données externe.

Cette option améliore considérablement les performances lors de l&#39;exécution de l&#39;étape de personnalisation.

## Utiliser les données d’une base de données externe dans un workflow {#using-data-from-an-external-database-in-a-workflow}

Dans plusieurs activités des workflows Adobe Campaign, vous pouvez utiliser les données stockées dans une base de données externe.

* **Filtrer sur les données externes** : l’activité de requête permet d’ajouter des données externes et de les utiliser dans les configuration de filtre définies. Pour en savoir plus, consultez la [documentation de Campaign v8]&#x200B;(https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/wf-type/targeting-workflows.html?lang=fr){target="_blank"}.

* **Créer des sous-ensembles** : l’activité de partage permet de créer des sous-ensembles. Vous pouvez utiliser des données externes pour définir les critères de filtrage à utiliser. Consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/split.html?lang=fr){target="_blank"}.

* **Charger la base de données externe** : vous pouvez utiliser les données externes dans l’activité de chargement des données (SGBD). En savoir plus dans la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/data-loading-rdbms.html?lang=fr){target="_blank"}.

* **Ajout d’informations et de liens** : l’activité d’enrichissement permet d’ajouter des données supplémentaires à la table de travail du workflow et de créer des liens vers une table externe. Dans ce contexte, elle peut utiliser des données provenant d’une base de données externe. Consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/enrichment.html?lang=fr){target="_blank"}.

## Mécanismes de sécurisation et limitations {#fda-limitations}

L’option FDA est conçue pour manipuler les données de bases de données externes en mode lot dans des workflows. Pour éviter les problèmes de performance, il n’est pas recommandé d’utiliser le module FDA dans le cadre d’opérations unitaires, par exemple : personnalisation, interaction, messagerie en temps réel, etc.

Le ciblage des données d’une base de données et le filtrage des résultats à l’aide d’une dimension de filtrage appartenant à une autre base de données ne sont pas pris en charge. Vous ne pouvez pas joindre dans une même requête des tableaux qui se trouvent sur des sources de données différentes. Vous pouvez surmonter cette limite à l’aide d’autres activités de workflow, telles que Changement de dimension.

Évitez autant que possible les opérations nécessitant d’utiliser à la fois la base de données Adobe Campaign et la base de données externe. La bonne pratique consiste à :

* exporter les données de la base Adobe Campaign vers la base externe et effectuer les opérations uniquement depuis la base externe avant de réimporter les résultats dans Adobe Campaign.

* collecter les données de la base externe dans Adobe Campaign et effectuer les opérations localement.

Si vous souhaitez effectuer de la personnalisation dans vos diffusions à l&#39;aide des données de la base externe, collectez les données à utiliser dans un workflow afin de les rendre disponibles dans une table temporaire. Utilisez alors les données de la table temporaire pour personnaliser votre diffusion.

L&#39;option FDA est assujettie aux limitations du système de la base de données externe que vous utilisez.
