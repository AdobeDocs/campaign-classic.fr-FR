---
product: campaign
title: Mettre à jour l’agrégat
description: En savoir plus sur l’activité de workflow de mise à jour d’agrégat
feature: Workflows
hide: true
exl-id: d2b26af0-30a1-4852-acd5-996795f198a1
TQID: https://experienceleague.adobe.com/YnOd1mT0WQqXHVeFUXFoumzDHxSSlKE2tgGSQFrjBzQ
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 127
ht-degree: 40%

---

# Mettre à jour l’agrégat{#update-aggregate}



Les agrégats sont définis au niveau d&#39;un cube, à des fins de reporting. Un onglet **[!UICONTROL Workflow]** est disponible lors de la configuration d’un agrégat.

Les agrégats sont utiles pour manipuler de grands volumes de données. Elles sont mises à jour automatiquement en fonction des paramètres définis dans la zone de workflow dédiée, afin d’intégrer les données collectées le plus récemment dans les indicateurs

Les agrégats sont définis au niveau du cube, dans l&#39;onglet correspondant.

![](assets/s_advuser_cube_agregate_01.png)


L&#39;activité **[!UICONTROL Mise à jour d&#39;agrégat]** permet de choisir le mode de mise à jour à appliquer : complète ou partielle.

Par défaut, une mise à jour complète est effectuée lors de chaque calcul. Pour activer une mise à jour partielle, sélectionnez l&#39;option correspondante et définissez les conditions de mise à jour.

![](assets/s_advuser_cube_agregate_05.png)

**Bonne pratique** : une activité **[!UICONTROL Planificateur]** peut être utilisée pour définir la fréquence de mise à jour des calculs.

![](assets/s_advuser_cube_agregate_04.png)
