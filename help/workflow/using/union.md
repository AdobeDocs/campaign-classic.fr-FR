---
title: Union
seo-title: Union
description: Union
seo-description: null
page-status-flag: never-activated
uuid: 987e106e-c414-4db4-a93e-96e43dc04370
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 573021ad-1efb-4156-af6d-417737ce745a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Union{#union}

Une union permet de regrouper le résultat de plusieurs activités entrantes dans une même cible. La cible est construite avec tous les résultats reçus : toutes les activités antérieures doivent donc être terminées pour que l&#39;union soit exécutée.

![](assets/s_user_segmentation_union.png)

>[!NOTE]
>
>Pour plus d’informations sur la configuration et l’utilisation de l’activité syndicale, voir [Combinaison de plusieurs cibles (Union)](../../workflow/using/targeting-data.md#combining-several-targets--union-).

## Exemple d&#39;union {#union-example}

Dans l&#39;exemple suivant, les résultats de deux requêtes sont réunis afin de mettre à jour une liste. Les deux requêtes ciblent des destinataires. Les résultats sont donc basés sur la même table.

1. Insérez une activité de type **[!UICONTROL Union]** directement après les deux requêtes et avant une activité de mise à jour de liste puis ouvrez-la.
1. Indiquez éventuellement un libellé.
1. Select the **[!UICONTROL Keys only]** reconciliation method since, in this example, the population resulting from queries contains consistent data.
1. Si vous avez ajouté des données additionnelles au niveau des requêtes, vous pouvez éventuellement choisir de ne conserver que celles qui sont communes.
1. Si vous souhaitez limiter la taille de la population finale, cochez la **[!UICONTROL Limit size of generated population]** case.

   Définissez cette dernière en indiquant le nombre de destinataires maximal et en choisissant la requête dont la population sera prioritaire.

1. Approve the union activity then configure the list update activity (see [List update](../../workflow/using/list-update.md)).
1. Lancez le workflow. Le nombre de résultats s&#39;affiche et la liste définie au niveau de l&#39;activité de mise à jour de liste est créée ou mise à jour. Cette dernière contient l&#39;ensemble des destinataires des deux requêtes ou le nombre défini à l&#39;étape précédente, le cas échéant.

   ![](assets/union_example.png)

## Paramètres d&#39;entrée {#input-parameters}

* tableName
* schema

Chacun des événements entrants doit spécifier une cible définie par ces paramètres.

## Paramètres de sortie {#output-parameters}

* tableName
* schema
* recCount

Cet ensemble de trois valeurs identifie la cible résultant de l’union. **[!UICONTROL tableName]** est le nom de la table qui enregistre les identificateurs cible, **[!UICONTROL schema]** est le schéma de la population (généralement nms:destinataire) et **[!UICONTROL recCount]** est le nombre d’éléments de la table.
