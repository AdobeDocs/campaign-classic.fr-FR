---
solution: Campaign Classic
product: campaign
title: Mise à jour d'agrégat
description: En savoir plus sur l’activité de workflow de mise à jour d’agrégat
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: d2b26af0-30a1-4852-acd5-996795f198a1
translation-type: ht
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: ht
source-wordcount: '100'
ht-degree: 100%

---

# Mise à jour d&#39;agrégat{#update-aggregate}

Les agrégats sont définis au niveau d&#39;un cube, à des fins de reporting. Un onglet **[!UICONTROL Workflow]** est disponible lors du paramétrage d&#39;un agrégat.

Pour plus d&#39;informations concernant les cubes et l&#39;utilisation des agrégats dans Adobe Campaign, consultez la [section](../../reporting/using/concepts-and-methodology.md#calculating-and-using-aggregates) dédiée.

L&#39;activité **[!UICONTROL Mise à jour d&#39;agrégat]** permet de choisir le mode de mise à jour à appliquer : complète ou partielle.

Par défaut, une mise à jour complète est réalisée à chaque calcul. Pour permettre une mise à jour partielle des données, sélectionnez l&#39;option correspondante puis définissez les conditions de mise à jour.

![](assets/s_advuser_cube_agregate_05.png)

**Bonne pratique** : une activité **[!UICONTROL Planificateur]** peut être utilisée pour définir la fréquence de mise à jour des calculs.

![](assets/s_advuser_cube_agregate_04.png)
