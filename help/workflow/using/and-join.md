---
product: campaign
title: Rendez-vous
description: Rendez-vous
feature: Workflows
hide: true
exl-id: 8b6d5c03-e104-4cf0-82ab-a08467e3e478
source-git-commit: 720a5f4edf534788f7fd143a476c25e58a6f1586
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 72%

---

# Rendez-vous{#and-join}



Une jointure ne déclenche sa transition sortante que lorsque toutes les transitions entrantes sont activées, c&#39;est-à-dire lorsque toutes les activités précédentes sont terminées. Vous pouvez ainsi vous assurer que certaines activités sont terminées avant de continuer à exécuter le workflow.

Par exemple, vous pouvez utiliser une activité Rendez-vous dans le cadre de la création de contenu et de l’automatisation de l’envoi de diffusions, afin de vous assurer qu’une diffusion n’est lancée qu’une fois les étapes d’interrogation de cible et de mise à jour du contenu terminées. Un cas pratique dédié est disponible dans [cette section](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content)

![](assets/and-join-usage.png)

>[!NOTE]
>
>Notez que les transitions entrantes configurées avec des dimensions de ciblage différentes ne peuvent pas être jointes ensemble à l’aide d’une activité **[!UICONTROL Rendez-vous]**.

La population transmise en sortie de l&#39;activité est déterminée par le choix d&#39;un ensemble principal parmi les transitions entrantes dans l&#39;activité.

La transition sortante ne peut contenir que l’une des populations de la transition entrante. Si l’activité n’est pas configurée, la transition sortante sélectionne aléatoirement une des populations entrantes.

>[!CAUTION]
>
>Dans le cas des activités de type **Rendez-vous**, les variables sont fusionnées. Toutefois, si une même variable est définie deux fois, il y a conflit et la valeur reste indéterminée. Voir à ce propos [cette section](javascript-scripts-and-templates.md#event-variables).
