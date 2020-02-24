---
title: Intersection
seo-title: Intersection
description: Intersection
seo-description: null
page-status-flag: never-activated
uuid: a8ff7a66-6c12-4e3c-ad45-d11b34ca64ff
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: d0dd9c74-aad5-452e-a11d-c231dacd2aec
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Intersection{#intersection}

Une activité de type **Intersection** crée une cible à partir de l&#39;intersection des cibles reçues.

Une intersection permet de n&#39;extraire que la population commune à tous les résultats des activités entrantes. La cible est construite avec tous les résultats reçus : toutes les activités antérieures doivent donc être terminées avant que l&#39;intersection ne puisse être exécutée. Pour paramétrer cette activité, vous devez renseigner son libellé et les options relatives au résultat.

![](assets/s_user_segmentation_inter.png)

Pour plus d’informations sur la configuration et l’utilisation de l’activité d’intersection, voir [Extraction des données d’articulation (intersection)](../../workflow/using/targeting-data.md#extracting-joint-data--intersection-).

Cochez l&#39;option **[!UICONTROL Générer le complémentaire]** si vous souhaitez exploiter la population restante. Le complémentaire contiendra l&#39;union des résultats de toutes les activités entrantes, moins l&#39;intersection. Une seconde transition sortante sera alors ajoutée à l&#39;activité, comme suit :

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
