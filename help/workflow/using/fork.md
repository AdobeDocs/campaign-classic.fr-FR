---
product: campaign
title: Branchement
description: En savoir plus sur l'activité de workflow Branchement
audience: workflow
content-type: reference
topic-tags: flow-control-activities
exl-id: 7a38653b-c15d-4ed8-85dc-f7214409f42b
source-git-commit: 1113afb573bad958ec7cc2cf008f71c8e751e8f9
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 11%

---

# Branchement{#fork}

![](../../assets/common.svg)

Vous pouvez utiliser l&#39;activité **[!UICONTROL Branchement]** pour créer plusieurs transitions sortantes et exécuter plusieurs activités indépendamment au sein d&#39;un même workflow.

>[!IMPORTANT]
>
>Les transitions sortantes que vous ajoutez après une activité **[!UICONTROL Branchement]** ne s&#39;exécutent pas simultanément. Ce comportement peut avoir un impact sur les performances du workflow. Utilisez l&#39;activité **[!UICONTROL Branchement]** si vous devez exécuter plusieurs activités indépendamment. Vous pouvez éventuellement rejoindre les activités sortantes avant la partie suivante du workflow.

Pour configurer une activité **[!UICONTROL Branchement]** et ses activités associées, procédez comme suit :

1. Ouvrez l&#39;activité **[!UICONTROL Branchement]** et définissez le nom et le libellé des transitions sortantes.

   ![](assets/s_user_segmentation_fork.png)

1. Ouvrez chaque transition sortante et configurez-la.
1. Si vous le souhaitez, ajoutez une activité Rendez-vous pour rejoindre les transitions sortantes. [En savoir plus](and-join.md).

   La partie suivante du workflow s’exécute uniquement à la fin des transitions sortantes jointes.

## Exemple : segmentation

Dans cet exemple, différents emails sont envoyés à différents groupes de population. Une activité **[!UICONTROL Branchement]** est utilisée après une requête, pour effectuer deux actions en parallèle :

* Enregistrer le résultat de la requête
* Segmenter le résultat pour envoyer plusieurs diffusions

   ![L&#39;activité branchement suit l&#39;intersection de deux requêtes et précède une activité de mise à jour de liste et de partage.](assets/wkf_fork_example.png)

Le workflow comprend les activités suivantes :

1. **** Queryactivity

   Deux groupes de population sont sélectionnés : femmes et Parisiennes.

1. **** Intersection-activity

   L&#39;intersection des résultats de la requête, c&#39;est-à-dire les femmes parisiennes, est sélectionnée.

1. **** Forkactivity

   La population calculée est enregistrée et, en parallèle, segmentée en deux groupes :

   1. Parisiennes de 18 à 40 ans
   1. Parisiennes de plus de 40 ans

1. **[!UICONTROL Activité Diffusion]**

   Un email différent est envoyé à chaque groupe de population.

## Cas pratique : envoyer un email d&#39;anniversaire

Un email récurrent est envoyé à une liste de destinataires le jour de leur anniversaire. Une activité **[!UICONTROL Branchement]** est utilisée pour inclure les destinataires nés un 29 février sur une année bissextile. [En savoir ](sending-a-birthday-email.md) plus sur ce cas pratique.

![L&#39;activité branchement suit une activité de test et précède deux activités de requête.](assets/birthday-workflow_usecase_1.png)

## Cas pratique : automatiser le contenu avec un workflow

La création et la diffusion d&#39;un bloc de contenu sont automatisées. Une activité **[!UICONTROL Branchement]** est utilisée pour calculer la cible et, parallèlement, pour créer le contenu. [En savoir ](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content) plus sur ce cas pratique.

![L&#39;activité Branchement suit une activité de diffusion et précède une activité de requête et une activité de gestion de contenu, toutes deux reliées par une activité Rendez-vous .](../../delivery/using/assets/d_ncs_content_workflow10.png)

Vous pouvez ensuite configurer chaque transition sortante, puis les associer à l&#39;aide d&#39;une activité [Rendez-vous](and-join.md), si nécessaire. Ainsi, le reste du workflow ne s&#39;exécutera qu&#39;une fois les transitions sortantes de l&#39;activité **[!UICONTROL Branchement]** terminées.

## Rubriques connexes :

* [Activité Rendez-vous](and-join.md)
* [Cas pratique : email d&#39;anniversaire](sending-a-birthday-email.md)
* [Cas pratique : création et diffusion de contenu](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content)