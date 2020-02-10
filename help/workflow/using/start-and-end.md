---
title: Début et Fin
seo-title: Début et Fin
description: Début et Fin
seo-description: null
page-status-flag: never-activated
uuid: ec0c818c-c307-4f50-908c-507bce0ea27b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: 8b239d5e-2317-42c8-9fee-7d40bea624da
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Début et Fin{#start-and-end}

Les activités **[!UICONTROL Start]** et **[!UICONTROL End]** vous permettent de marquer graphiquement le début et la fin d’un flux de travail. Ces activités n&#39;ont aucun impact fonctionnel et sont donc facultatives.

* **[!UICONTROL Start]**

   L&#39;exécution d&#39;un workflow démarre par les activités sans transition entrante et les activités de type Début.

   ![](assets/s_user_segmentation_start_stop.png)

* **[!UICONTROL End]**

   Vous pouvez configurer l’ **[!UICONTROL End]** activité pour interrompre toutes les tâches en cours. Pour ce faire, double-cliquez sur l’activité pour afficher ses propriétés, puis cochez l’option appropriée.

   ![](assets/s_user_segmentation_end.png)

   Les données de la table de travail sont automatiquement supprimées à l&#39;activation de l&#39;activité de fin. Si cela n&#39;est pas nécessaire, et afin d&#39;éviter toute charge inutile, vous pouvez choisir de désactiver la transition en sortie de la dernière activité. Par exemple, en sortie d&#39;une diffusion, si aucun traitement n&#39;est prévu, décochez l&#39;option correspondante comme ci-dessous :

   ![](assets/s_advuser_delivery_option_no_output.png)

