---
solution: Campaign Classic
product: campaign
title: Branchement
description: En savoir plus sur l’activité de workflow de branchement
audience: workflow
content-type: reference
topic-tags: flow-control-activities
translation-type: tm+mt
source-git-commit: e5f718908d0bb6893e54c51700865ecda09c80db
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 54%

---


# Branchement{#fork}

L&#39;activité **[!UICONTROL Branchement]** vous permet de créer plusieurs transitions sortantes, afin d&#39;exécuter plusieurs activités indépendamment au sein du même workflow.

Par exemple, vous pouvez utiliser l’activité après une requête, afin d’effectuer deux actions en parallèle :

* Enregistrer le résultat de la requête dans une audience,
* Exécuter une segmentation sur le résultat afin d’envoyer plusieurs diffusions.

Vous pouvez également utiliser l’activité dans le cadre de la création de contenu et de l’automatisation de l’envoi des diffusions, afin de lancer simultanément le calcul de la cible et la création de contenu. Un cas pratique dédié est disponible dans [cette section](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content).

>[!IMPORTANT]
>
>Les transitions sortantes ajoutées après une activité **[!UICONTROL Fork]** **ne s&#39;exécuteront pas simultanément.** Ce comportement peut avoir un impact sur les performances du workflow. Utilisez cette activité si vous devez exécuter plusieurs activités indépendamment, puis les rassembler avant d’exécuter le reste du processus.

Pour configurer l&#39;activité **[!UICONTROL Fork]**, ouvrez-la pour définir le numéro et l&#39;étiquette des transitions sortantes.

![](assets/s_user_segmentation_fork.png)

Vous pouvez ensuite configurer chaque transition sortante, puis les joindre ensemble à l’aide d’une activité [ET-join](../../workflow/using/and-join.md), si nécessaire. Ainsi, le reste du flux de travail ne s’exécutera qu’une fois les transitions sortantes de l’activité **[!UICONTROL Fork]** terminées.
