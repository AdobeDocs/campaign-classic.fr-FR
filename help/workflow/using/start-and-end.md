---
product: campaign
title: Début et Fin
description: En savoir plus sur les activités de workflow de début et de fin
feature: Workflows
hide: true
exl-id: 56dfbaf3-93de-4ade-b4ad-9b54d239c7a5
TQID: https://experienceleague.adobe.com/Vw3JK6VyMf4HrEkvYk4-34dGTp0e3e1xPZ8jG0bAxz8
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 140
ht-degree: 21%

---

# Début et Fin{#start-and-end}



Les activités **[!UICONTROL Début]** et **[!UICONTROL Fin]** vous permettent de marquer graphiquement le début et la fin d’un workflow. Ces activités n’ont aucun impact fonctionnel et sont donc facultatives.

* **[!UICONTROL Début]**

  L&#39;exécution d&#39;un workflow démarre par les activités sans transition entrante et les activités de type Début.

  ![](assets/s_user_segmentation_start_stop.png)

* **[!UICONTROL Fin]**

  Vous pouvez paramétrer l&#39;activité **[!UICONTROL Fin]** pour interrompre toutes les tâches en cours. Pour ce faire, double-cliquez sur l’activité pour afficher ses propriétés, puis cochez l’option appropriée.

  ![](assets/s_user_segmentation_end.png)

  Les données de la table de travail sont automatiquement supprimées lorsque l&#39;activité de fin est activée. Si cela n’est pas nécessaire, et pour éviter des charges inutiles, vous pouvez choisir de désactiver la transition à la sortie de la dernière activité. Par exemple, au niveau d&#39;une sortie de diffusion, si aucun traitement n&#39;est planifié, désélectionnez l&#39;option correspondante comme dans l&#39;exemple ci-dessous :

  ![](assets/s_advuser_delivery_option_no_output.png)
