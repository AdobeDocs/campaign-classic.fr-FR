---
product: campaign
title: Mettre à jour l’agrégat
description: En savoir plus sur l’activité de workflow de mise à jour d’agrégat
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
feature: Workflows
exl-id: d2b26af0-30a1-4852-acd5-996795f198a1
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 100%

---

# Mise à jour d&#39;agrégat{#update-aggregate}



Les agrégats sont définis au niveau d&#39;un cube, à des fins de reporting. Un onglet **[!UICONTROL Workflow]** est disponible lors du paramétrage d&#39;un agrégat.

Les agrégats sont pertinents lorsque vous manipulez un gros volume de données. Ils sont mis à jour automatiquement selon les paramètres définis dans la boîte de workflow dédiée, afin d&#39;intégrer les dernières données collectées dans les indicateurs.

Les agrégats sont définis au niveau du cube, dans l&#39;onglet correspondant.

![](assets/s_advuser_cube_agregate_01.png)


L&#39;activité **[!UICONTROL Mise à jour d&#39;agrégat]** permet de choisir le mode de mise à jour à appliquer : complète ou partielle.

Par défaut, une mise à jour complète est réalisée à chaque calcul. Pour permettre une mise à jour partielle des données, sélectionnez l&#39;option correspondante puis définissez les conditions de mise à jour.

![](assets/s_advuser_cube_agregate_05.png)

**Bonne pratique** : une activité **[!UICONTROL Planificateur]** peut être utilisée pour définir la fréquence de mise à jour des calculs.

![](assets/s_advuser_cube_agregate_04.png)
