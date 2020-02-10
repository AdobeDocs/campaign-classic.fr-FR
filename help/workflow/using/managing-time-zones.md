---
title: Gestion des fuseaux horaires
seo-title: Gestion des fuseaux horaires
description: Gestion des fuseaux horaires
seo-description: null
page-status-flag: never-activated
uuid: a253861a-fc15-406d-969d-33cfb4169839
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: advanced-management
discoiquuid: 8bcbcd23-9251-412a-ae72-11f15db74112
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Gestion des fuseaux horaires{#managing-time-zones}

Adobe Campaign permet de gérer les décalages horaires entre plusieurs pays concernés par la même instance. La configuration appliquée est paramétrée lors de la création de l&#39;instance.

Pour plus d&#39;informations sur la configuration des fuseaux horaires dans Adobe Campaign, consultez cette [section](../../installation/using/time-zone-management.md).

Dans un workflow, vous pouvez adapter les plannings d&#39;exécution des activités, mais aussi associer un fuseau horaire spécifique à une activité ou à tout le workflow. Ce paramétrage peut être utile par exemple lors de l&#39;import de fichier ou dans le cadre de la planification des diffusions.

## Planifier l&#39;exécution {#execution-scheduling}

Vous pouvez planifier l’exécution des tâches à l’aide du planificateur (voir [Planificateur](../../workflow/using/scheduler.md)). Vous pouvez également utiliser les options de planification disponibles dans les activités qui offrent cette fonctionnalité. Ces activités offrent un **[!UICONTROL Schedule]** onglet : **[!UICONTROL File collector]**, **[!UICONTROL File transfer]**, **[!UICONTROL Web download]**, **[!UICONTROL Email reception]** &amp; **[!UICONTROL SMS]**, etc.

Pour toutes les tâches planifiées, c’est-à-dire toutes les activités avec des options de planification, vous pouvez sélectionner le fuseau horaire à appliquer. Le fuseau horaire est sélectionné via l’ **[!UICONTROL Advanced]** onglet de l’activité concernée :

![](assets/wf-timezone-in-a-box.png)

Les valeurs possibles sont les suivantes :

* Fuseau horaire du serveur

   Utilise le fuseau horaire du serveur applicatif d&#39;Adobe Campaign.

* Fuseau horaire de l&#39;utilisateur

   Utilise le fuseau horaire de l&#39;opérateur Adobe Campaign qui lance l&#39;exécution du workflow.

* Fuseau horaire de la base de données

   Utilise le fuseau horaire du serveur de base de données utilisé.

* Fuseaux horaire spécifiques

   Utilise le fuseau horaire sélectionné.

If the **[!UICONTROL By default]** value is selected, the time zone of the workflow is applied, or, otherwise, that of the application server.

## Associer un fuseau horaire à une activité {#linking-a-time-zone-to-an-activity}

L’ **[!UICONTROL Advanced]** onglet des activités du flux de travail vous permet de sélectionner son fuseau horaire. Bien que, la plupart du temps, le fuseau horaire des processus soit suffisant, il peut être nécessaire de le surcharger encore et encore pour une activité spécifique, telle que l’importation de données, afin de lier les dates à leur fuseau horaire correct.
