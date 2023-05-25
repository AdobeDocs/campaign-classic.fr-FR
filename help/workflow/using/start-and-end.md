---
product: campaign
title: Début et Fin
description: En savoir plus sur les activités de workflow de début et de fin
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: 56dfbaf3-93de-4ade-b4ad-9b54d239c7a5
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: ht
source-wordcount: '138'
ht-degree: 100%

---

# Début et Fin{#start-and-end}



Les activités **[!UICONTROL Début]** et **[!UICONTROL Fin]** permettent de marquer graphiquement le début et la fin d&#39;un workflow. Elles n&#39;ont pas d&#39;impact fonctionnel et sont donc facultatives.

* **[!UICONTROL Début]**

   L&#39;exécution d&#39;un workflow démarre par les activités sans transition entrante et les activités de type Début.

   ![](assets/s_user_segmentation_start_stop.png)

* **[!UICONTROL Fin]**

   Vous pouvez paramétrer l&#39;activité **[!UICONTROL Fin]** pour qu&#39;elle interrompe toutes les tâches en cours. Pour cela, double-cliquez sur l&#39;activité pour afficher ses propriétés et cochez l&#39;option correspondante.

   ![](assets/s_user_segmentation_end.png)

   Les données de la table de travail sont automatiquement supprimées à l&#39;activation de l&#39;activité de fin. Si cela n&#39;est pas nécessaire, et afin d&#39;éviter toute charge inutile, vous pouvez choisir de désactiver la transition en sortie de la dernière activité. Par exemple, en sortie d&#39;une diffusion, si aucun traitement n&#39;est prévu, décochez l&#39;option correspondante comme ci-dessous :

   ![](assets/s_advuser_delivery_option_no_output.png)
