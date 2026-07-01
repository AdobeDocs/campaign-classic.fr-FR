---
product: campaign
title: Rendez-vous
description: Rendez-vous
feature: Workflows
hide: true
exl-id: 8b6d5c03-e104-4cf0-82ab-a08467e3e478
TQID: https://experienceleague.adobe.com/L6SmrK6xHkRqZI69OepbB4drLPfrX-cmvi6h6su3LYk
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: id: ee25c34b-ea50-427b-9369-ba0a160f7d70id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22fid: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 197
ht-degree: 100%

---

# Rendez-vous{#and-join}



Une jointure ne déclenche sa transition sortante qu’une fois toutes les transitions entrantes activées, lorsque toutes les activités précédentes sont donc terminées.Cela vous permet de vous assurer que certaines activités sont bien terminées avant de continuer l’exécution du workflow.

Par exemple, vous pouvez utiliser une activité Rendez-vous dans le cadre de la création de contenu et de l’automatisation de l’envoi de diffusions, afin de vous assurer qu’une diffusion n’est lancée qu’une fois les étapes d’interrogation de cible et de mise à jour du contenu terminées. Un cas pratique dédié est disponible dans [cette section](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content)

![](assets/and-join-usage.png)

>[!NOTE]
>
>Notez que les transitions entrantes configurées avec des dimensions de ciblage différentes ne peuvent pas être jointes ensemble à l’aide d’une activité **[!UICONTROL Rendez-vous]**.

La population transmise en sortie de l&#39;activité est déterminée par le choix d&#39;un ensemble principal parmi les transitions entrantes dans l&#39;activité.

La transition sortante ne peut contenir que l’une des populations de la transition entrante. Si l’activité n’est pas configurée, la transition sortante sélectionnera l’une des populations entrantes de manière aléatoire.

>[!CAUTION]
>
>Dans le cas des activités de type **Rendez-vous**, les variables sont fusionnées. Toutefois, si une même variable est définie deux fois, il y a conflit et la valeur reste indéterminée. Voir à ce propos [cette section](javascript-scripts-and-templates.md#event-variables).
