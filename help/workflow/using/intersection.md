---
product: campaign
title: Intersection
description: Intersection
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Targeting Activity
exl-id: f426bf02-9899-49eb-b699-728d51b57c64
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: ht
source-wordcount: '0'
ht-degree: 100%

---

# Intersection{#intersection}

>[!CONTEXTUALHELP]
>id="ac_workflow_intersection"
>title="Intersection activité"
>abstract="Une activité de type Intersection crée une cible à partir de l’intersection des cibles reçues. Une intersection permet d’extraire uniquement la population commune à tous les résultats de l’activité entrante."
>additional-url="https://video.tv.adobe.com/v/329373" text="Regarder une vidéo de démonstration"




Une activité de type **Intersection** crée une cible à partir de l&#39;intersection des cibles reçues.

Une intersection permet de n&#39;extraire que la population commune à tous les résultats des activités entrantes. La cible est construite avec tous les résultats reçus : toutes les activités antérieures doivent donc être terminées avant que l&#39;intersection ne puisse être exécutée. Pour paramétrer cette activité, vous devez renseigner son libellé et les options relatives au résultat.

![](assets/s_user_segmentation_inter.png)

Pour plus d&#39;informations sur la configuration et l&#39;utilisation de l&#39;activité Intersection, voir la section [Extraire les données communes (Intersection)](targeting-data.md#extracting-joint-data--intersection-).

Cochez l&#39;option **[!UICONTROL Générer le complémentaire]** si vous souhaitez exploiter la population restante. Le complémentaire contiendra l&#39;union des résultats de toutes les activités entrantes, moins l&#39;intersection. Une seconde transition sortante sera alors ajoutée à l&#39;activité, comme suit :

![](assets/s_user_segmentation_inter_compl.png)

## Exemple d&#39;intersection {#intersection-example}

Dans l&#39;exemple suivant, l&#39;intersection a pour but de calculer les destinataires communs à trois requêtes simples afin de les associer à une liste.

1. Insérez une activité de type **[!UICONTROL Intersection]** à la suite de trois requêtes simples.

   Dans cet exemple, les requêtes ciblent respectivement les destinataires masculins, les destinataires vivant à Paris et les destinataires âgés de 18 à 30 ans.

1. Paramétrez l&#39;intersection. Pour cela, sélectionnez la méthode de réconciliation **[!UICONTROL Uniquement les clés]** dans la mesure où les populations issues des requêtes contiennent des données homogènes.
1. Si vous avez ajouté des données additionnelles au niveau des requêtes, vous pouvez éventuellement choisir de ne conserver que celles qui sont communes en cochant la case correspondante.
1. Si vous souhaitez utiliser le reste des données (correspondant aux requêtes, mais pas à leur intersection), cochez la case **[!UICONTROL Générer le complémentaire]**.
1. Insérez une activité de mise à jour de liste après le résultat de l&#39;intersection. Insérez également une mise à jour de liste après le complémentaire dans le cas où vous souhaiteriez également l&#39;exploiter.
1. Exécutez le workflow. Ici, deux destinataires correspondent à la fois aux trois requêtes en entrée. Le complément est composé des cinq destinataires qui correspondent uniquement à une ou deux des trois requêtes.

   Le résultat de l&#39;intersection est envoyé vers la première mise à jour de liste. Si vous avez choisi d&#39;exploiter le complément, ce dernier est également envoyé vers la seconde mise à jour de liste.

   ![](assets/intersection_example.png)

## Paramètres d&#39;entrée {#input-parameters}

* tableName
* schema

Chacun des événements entrants doit spécifier une cible définie par ces paramètres.

## Paramètres de sortie {#output-parameters}

* tableName
* schema
* recCount

Ce triplet de valeurs identifie la cible résultant de l&#39;intersection. **[!UICONTROL tableName]** est le nom de la table qui mémorise les identifiants de la cible, **[!UICONTROL schema]** est le schéma de la population (habituellement **[!UICONTROL nms:recipient]**) et **[!UICONTROL recCount]** est le nombre d&#39;éléments dans la table.
