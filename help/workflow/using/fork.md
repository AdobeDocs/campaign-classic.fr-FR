---
product: campaign
title: Branchement
description: En savoir plus sur l'activité de workflow Branchement
audience: workflow
content-type: reference
topic-tags: flow-control-activities
exl-id: 7a38653b-c15d-4ed8-85dc-f7214409f42b
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 100%

---

# Branchement{#fork}

![](../../assets/common.svg)

L&#39;activité **[!UICONTROL Branchement]** vous permet de créer plusieurs transitions sortantes, afin d&#39;exécuter plusieurs activités indépendamment au sein du même workflow.

Par exemple, vous pouvez utiliser l&#39;activité après une requête, afin d&#39;effectuer deux actions en parallèle :

* Enregistrer le résultat de la requête dans une audience,
* Exécuter une segmentation sur le résultat afin d&#39;envoyer plusieurs diffusions.

Vous pouvez également utiliser l&#39;activité dans le cadre de la création de contenu et de l&#39;automatisation de l&#39;envoi des diffusions, afin de lancer simultanément le calcul de la cible et la création de contenu. Un cas pratique dédié est disponible dans [cette section](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content).

>[!IMPORTANT]
>
>Les transitions sortantes ajoutées après une activité **[!UICONTROL Branchement]** **ne s&#39;exécuteront pas** simultanément. Ce comportement peut avoir un impact sur les performances du workflow. Utilisez cette activité si vous devez exécuter plusieurs activités indépendamment, puis associez-les avant d&#39;exécuter le reste du workflow.

Pour configurer l&#39;activité **[!UICONTROL Branchement]**, ouvrez-la, puis définissez le nombre et le libellé des transitions sortantes.

![](assets/s_user_segmentation_fork.png)

Vous pouvez ensuite configurer chaque transition sortante, puis les associer à l&#39;aide d&#39;une activité [Rendez-vous](and-join.md), si nécessaire. Ainsi, le reste du workflow ne s&#39;exécutera qu&#39;une fois les transitions sortantes de l&#39;activité **[!UICONTROL Branchement]** terminées.
