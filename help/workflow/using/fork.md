---
solution: Campaign Classic
product: campaign
title: Branchement
description: En savoir plus sur l’activité de workflow de branchement
audience: workflow
content-type: reference
topic-tags: flow-control-activities
translation-type: tm+mt
source-git-commit: 3eecc16442a11849c12819cf83392f60c5b82a13
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 16%

---


# Branchement{#fork}

L&#39;activité **[!UICONTROL Fork]** vous permet de créer plusieurs transitions sortantes, afin d&#39;exécuter plusieurs activités indépendamment au sein du même flux de travail.

Par exemple, vous pouvez utiliser l’activité après une requête, afin d’effectuer deux actions en parallèle :

* Enregistrez le résultat de la requête dans une audience,
* Exécutez une segmentation sur le résultat afin d’envoyer plusieurs diffusions.

Vous pouvez également utiliser l’activité dans le contexte de la création de contenu et de l’automatisation de l’envoi de diffusions, afin de lancer le calcul de la cible et la création de contenu en parallèle. Un cas pratique dédié est disponible dans [cette section](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content).

>[!WARNING]
>
>Gardez à l’esprit que les transitions sortantes ajoutées après une activité Fork ne s’exécuteront pas simultanément.
>
>L&#39;activité ne doit donc pas être utilisée pour améliorer les performances du flux de travail, mais plutôt pour exécuter plusieurs activités de manière indépendante, et finalement les réunir avant d&#39;exécuter le reste du flux de travail.

Pour configurer l’activité, ouvrez-la, puis définissez le nombre et le libellé des transitions sortantes de votre choix.

![](assets/s_user_segmentation_fork.png)

Vous pouvez ensuite configurer chaque transition sortante, puis les associer à l’aide d’une activité [ET-join](../../workflow/using/and-join.md), si nécessaire. Ainsi, le reste du flux de travail ne s’exécutera qu’une fois les transitions sortantes de l’activité **[!UICONTROL Fork]** terminées.
