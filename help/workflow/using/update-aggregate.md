---
product: campaign
title: Mettre à jour l’agrégat
description: En savoir plus sur l’activité de workflow de mise à jour d’agrégat
feature: Workflows
hide: true
exl-id: d2b26af0-30a1-4852-acd5-996795f198a1
TQID: 'https://experienceleague.adobe.com/YnOd1mT0WQqXHVeFUXFoumzDHxSSlKE2tgGSQFrjBzQ'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
    internal-label: HeatMap
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
    internal-label: Execution activities
  - id: d1110311-2ca4-442b-be37-088a6db845ee
    internal-label: Data Management activities
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
    internal-label: Reporting
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 100%
---
# Mettre à jour l’agrégat{#update-aggregate}



Les agrégats sont définis au niveau d’un cube, à des fins de création de rapports. Un onglet **[!UICONTROL Workflow]** est disponible lors de la configuration de l’agrégat.

Les agrégats sont utiles lorsque vous manipulez de grands volumes de données. Ils sont mis à jour automatiquement selon les paramètres définis dans la zone de workflow dédiée, afin d’intégrer les dernières données collectées dans les indicateurs.

Les agrégats sont définis au niveau du cube, dans l&#39;onglet correspondant.

![](assets/s_advuser_cube_agregate_01.png)


L&#39;activité **[!UICONTROL Mise à jour d&#39;agrégat]** permet de choisir le mode de mise à jour à appliquer : complète ou partielle.

Par défaut, une mise à jour complète est exécutée lors de chaque calcul. Pour activer une mise à jour partielle, sélectionnez l’option correspondante et définissez les conditions de mise à jour.

![](assets/s_advuser_cube_agregate_05.png)

**Bonne pratique** : une activité **[!UICONTROL Planificateur]** peut être utilisée pour définir la fréquence de mise à jour des calculs.

![](assets/s_advuser_cube_agregate_04.png)

