---
title: Sous-workflow
seo-title: Sous-workflow
description: Sous-workflow
seo-description: null
page-status-flag: never-activated
uuid: c952633f-1aca-44cf-bb50-a67e9b086030
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: a4441820-1b3d-4bac-a6e3-1c9c14466d19
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b1a961822224ab0a9551f51942a5f94cf201c8ee
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 59%

---


# Sous-workflow{#sub-workflow}

L’activité **[!UICONTROL Sous-workflow]** permet de déclencher l’exécution d’un autre workflow et de récupérer le résultat du calcul. Cette activité permet d’utiliser des workflows complexes tout en gardant une interface simplifiée.

Vous pouvez appeler plusieurs sous-workflows au sein d’un même workflow. Les sous-workflows sont exécutés de manière synchrone.

Dans l’exemple ci-dessous, un processus &quot;maître&quot; appelle un sous-processus à l’aide de sauts. Pour plus d’informations sur les objets graphiques de type saut, voir [cette section](../../workflow/using/jump--start-point-and-end-point-.md).

1. Créez un workflow que vous allez utiliser en tant que sous-workflow dans un autre workflow.
1. Insérez une activité **[!UICONTROL de saut (point de terminaison)]** avec une priorité de 1 au début du flux de travaux. Si vous avez plusieurs sauts de type &quot;point de terminaison&quot;, Adobe Campaign utilisera le saut &quot;point de terminaison&quot; avec le nombre le plus faible.
1. Insérez une activité **[!UICONTROL de saut (point de début)]** avec une priorité de 2 à la fin du processus. Si vous avez plusieurs sauts de type &quot;point de début&quot;, Adobe Campaign utilisera le saut &quot;point de début&quot; avec le plus grand nombre.

   ![](assets/subworkflow_jumps.png)

   >[!NOTE]
   >
   >If the sub-workflow activity references a workflow with several **[!UICONTROL Jump]** activities, the sub-workflow is executed between the &quot;end point&quot; type jump with the lowest number and the &quot;start point&quot; type jump with the highest number.
   >
   >Pour que le sous-processus soit exécuté correctement, vous devez avoir un seul saut de type &quot;point de terminaison&quot; avec le nombre le plus faible et un seul saut de type &quot;point de début&quot; avec le nombre le plus élevé.

1. Finalisez et enregistrez ce « sous-workflow ».
1. Créez un workflow « maître ».
1. Insérez une activité **[!UICONTROL Sous-workflow]** et ouvrez-la.
1. Sélectionnez le workflow que vous souhaitez utiliser dans la liste déroulante **[!UICONTROL Modèle de workflow]**.

   ![](assets/subworkflow_selection.png)

1. Vous pouvez également ajouter un script de paramétrage pour modifier le fonctionnement du workflow référencé.
1. Cliquez sur **[!UICONTROL Ok]**. Cela créera automatiquement une transition sortante avec le libellé de l’activité **[!UICONTROL Saut (départ)]** du workflow sélectionné.

   ![](assets/subworkflow_outbound.png)

1. Exécutez le workflow.

Une fois exécuté, le workflow qui a été appelé en tant que sous-workflow reste à l’état **[!UICONTROL En édition]**, ce qui a les implications suivantes :

* Vous ne pouvez pas cliquer avec le bouton droit sur les transitions pour afficher la cible.
* Le nombre de populations intermédiaires ne peut pas être affiché.
* Les logs sont agrégés dans le workflow « maître » et sont libellés uniquement comme « sous-workflow ».

En effet, ce workflow n’est qu’un modèle. Un sous-workflow est créé sur la base de ce modèle lorsqu’il est appelé à partir du workflow « maître ».

## Paramètres d&#39;entrée (optionnel) {#input-parameters--optional-}

* tableName
* schema

Chacun des événements entrants doit spécifier une cible définie par ces paramètres.

## Paramètres de sortie {#output-parameters}

* tableName
* schema
* recCount

Ce triplet de valeurs identifie la population ciblée par la requête. **[!UICONTROL tableName]** est le nom de la table qui mémorise les identifiants de la cible, **[!UICONTROL schema]** est le schéma de la population (habituellement nms:recipient) et **[!UICONTROL recCount]** est le nombre d&#39;éléments dans la table.

* targetSchema : Cette valeur correspond au schéma de la table de travail. Ce paramètre est valide pour toutes les transitions avec **[!UICONTROL tableName]** et **[!UICONTROL schéma]**.
