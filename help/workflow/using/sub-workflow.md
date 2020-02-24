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
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Sous-workflow{#sub-workflow}

L’activité **[!UICONTROL Sous-workflow]** permet de déclencher l’exécution d’un autre workflow et de récupérer le résultat du calcul. Cette activité permet d’utiliser des workflows complexes tout en gardant une interface simplifiée.

Vous pouvez appeler plusieurs sous-workflows au sein d’un même workflow. Les sous-workflows sont exécutés de manière synchrone.

>[!NOTE]
>
>Pour que le sous-workflow s’exécute correctement, vous devez disposer d’un seul saut de type « arrivée » avec le numéro le plus petit, et d’un seul saut de type « départ » avec le numéro le plus élevé. Par exemple, si vous avez des sauts de type « départ » avec une priorité de 1, 2 et 3, vous ne devriez avoir qu’un seul saut de type « départ » avec une priorité de 3.

1. Créez un workflow que vous allez utiliser en tant que sous-workflow dans un autre workflow.
1. Insérez une activité **[!UICONTROL Saut (arrivée)]** avec une priorité de 1 au début du workflow. Si vous avez plusieurs sauts de type « arrivée », Adobe Campaign utilisera le saut « arrivée » dont le numéro est le plus petit.

   Insérez une activité **[!UICONTROL Saut (départ)]** avec une priorité de 2 à la fin du workflow. Si vous avez plusieurs sauts de type « départ », Adobe Campaign utilisera le saut « départ » dont le numéro est le plus élevé.

   ![](assets/subworkflow_jumps.png)

   >[!NOTE]
   >
   >Si l&#39;activité de sous-workflow référence un workflow comportant plusieurs activités **[!UICONTROL Saut]**, l&#39;exécution du sous-workflow s&#39;effectue entre le saut de type &quot;arrivée&quot; dont le numéro est le plus petit et le saut de type &quot;départ&quot; dont le numéro est le plus élevé.

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

* targetSchema

Cette valeur est le schéma de la table de travail. Ce paramètre est valable pour toutes les transitions avec **[!UICONTROL tableName]** et **[!UICONTROL schema]**.
