---
title: Planificateur
seo-title: Planificateur
description: Planificateur
seo-description: null
page-status-flag: never-activated
uuid: e814b978-2edd-442e-9334-9633bc9ec63a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: 093dbe8a-494f-4fe7-8614-3bf58486e34c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 23629289ac5da3f9bef01f50c452f7c761a6fa44
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 58%

---


# Planificateur {#scheduler}

Le **Planificateur** est une tâche persistante qui active sa transition aux moments spécifiés par son planning.

L&#39;activité **[!UICONTROL Planificateur]** est à considérer comme un départ planifié. Les règles de positionnement de l&#39;activité dans le diagramme sont les mêmes que pour l&#39;activité **[!UICONTROL Début]**. L&#39;activité ne doit jamais comporter de transition entrante.

## Bonnes pratiques {#best-practices}

* Ne planifiez pas l&#39;exécution d&#39;un flux de travail plus de toutes les 15 minutes, car cela peut nuire aux performances globales du système et créer des blocs dans la base de données.

* N’utilisez jamais plus d’une activité de **[!UICONTROL Planificateur]** par branche dans un processus. Voir [Utilisation d’activités](../../workflow/using/workflow-best-practices.md#using-activities).

* L’utilisation d’une activité de planificateur peut entraîner plusieurs exécutions simultanées d’un workflow. Par exemple, un Planificateur peut déclencher l’exécution du processus toutes les heures, mais parfois l’exécution de l’ensemble du processus prend plus d’une heure.

   Vous pouvez ignorer l’exécution si le processus est déjà en cours d’exécution. Pour plus d’informations sur la manière d’empêcher les exécutions simultanées d’un workflow, consultez [cette page](../../workflow/using/monitoring-workflow-execution.md#preventing-simultaneous-multiple-executions).

* Notez que la transition peut être activée plusieurs heures plus tard si le flux de travail exécutait une tâche à long terme, telle qu’une importation, ou si le module wfserver a été arrêté pendant un certain temps. Dans ce cas, il peut être nécessaire de limiter l&#39;exécution de la tâche activée par le Planificateur à une certaine période.

## Configuring the Scheduler activity {#configuring-scheduler-activity}

Le planificateur définit le planning d&#39;activation de sa transition. Pour le paramétrer, double-cliquez sur l&#39;objet graphique et cliquez sur le bouton **[!UICONTROL Changer...]**.

![](assets/s_user_segmentation_scheduler.png)

Un assistant permet de définir la fréquence et la période de validité de l&#39;activité. Les étapes de paramétrage sont les suivantes :

1. Sélectionnez la fréquence d&#39;activation et cliquez sur **[!UICONTROL Suivant]**.

   ![](assets/s_user_segmentation_scheduler2.png)

1. Indiquez les heures et jours d&#39;activation. Les paramètres de cette étape dépendent de la périodicité sélectionnée à l&#39;étape précédente. Si vous choisissez de lancer l&#39;activité plusieurs fois par jour, les options de paramétrage seront les suivantes :

   ![](assets/s_user_segmentation_scheduler3.png)

1. Définissez la période de validité du planning ou indiquez le nombre de fois où il sera exécuté.

   ![](assets/s_user_segmentation_scheduler4.png)

1. Vérifiez le paramétrage et cliquez sur le bouton **[!UICONTROL Terminer]** pour l&#39;enregistrer.

   ![](assets/s_user_segmentation_scheduler5.png)
