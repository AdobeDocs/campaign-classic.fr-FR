---
title: Advanced parameters
seo-title: Advanced parameters
description: Advanced parameters
seo-description: null
page-status-flag: never-activated
uuid: 9453d291-921b-4a03-80d1-2c8295f9a986
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: advanced-management
discoiquuid: f66f1ff5-3601-4eb8-b05d-6f99164890ae
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Paramètres avancés{#advanced-parameters}

The properties screen of an activity has an **[!UICONTROL Advanced]** tab that lets you define a behavior in case of errors, the execution period for the activity; and lets you enter an initialization script. Il existe deux versions de cet onglet :

* a simplified version (for **[!UICONTROL Start]** and **[!UICONTROL End]** activities for instance)

   ![](assets/wf-advanced-basic.png)

* a more detailed version (for the **[!UICONTROL Query]** activity, for instance)

   ![](assets/wf-advanced-full.png)

The fields to be entered in the **[!UICONTROL Advanced]** tab are detailed in the following sections.

## Nom {#name}

Ce champ contient le nom interne de l&#39;activité.

## Image {#image}

Ce champ vous permet de modifier l’image liée à une activité. Pour plus d’informations à ce sujet, voir : [Gestion des images](../../workflow/using/managing-activity-images.md)d’activité.

## Exécution {#execution}

Ce champ vous permet de définir l&#39;action à effectuer au moment du déclenchement de la tâche. Trois options sont disponibles :

Ces options sont généralement sélectionnées au niveau du diagramme en cliquant sur l&#39;activité avec le bouton droit.

* **[!UICONTROL Normal]**: l’activité est exécutée comme d’habitude.
* **[!UICONTROL Do not activate]**: cette tâche et toutes les tâches suivantes (dans la même branche) ne sont pas exécutées.
* **[!UICONTROL Activate but do not execute]**: cette tâche et toutes les tâches suivantes (dans la même branche) sont automatiquement arrêtées. Cela peut s’avérer utile si vous souhaitez y être au démarrage de la tâche. Pour exécuter la tâche manuellement, cliquez avec le bouton droit de la souris sur l’activité et sélectionnez **[!UICONTROL Normal execution]**.

## Affinité {#affinity}

Ce champ vous permet de forcer l’exécution d’une activité sur un ordinateur spécifique. For more on this, refer to: [Managing propensity](../../workflow/using/managing-propensity.md).

## Max. execution period {#max--execution-period}

Ce champ vous permet de définir un avertissement lorsque la tâche prend trop de temps. Cela n’aura aucun impact sur l’opération du flux de travail. Si la tâche n’est pas terminée au moment où elle **[!UICONTROL Max. execution period]** est terminée, la **[!UICONTROL Instance monitoring]** page affiche un avertissement pour ce flux de travail. Cette page est accessible via l’ **[!UICONTROL Monitoring]** onglet de la page d’accueil.

## Comportement {#behavior}

Ce champ vous permet de définir le comportement à effectuer dans le cas de l&#39;utilisation de tâches asynchrones. Deux options sont disponibles :

* **[!UICONTROL Several tasks authorized]**: plusieurs tâches peuvent être exécutées simultanément, même si la première n’est pas terminée.
* **[!UICONTROL The current task has priority]**: les tâches en cours sont prioritaires. Tant qu’une tâche est en cours, aucune autre tâche ne sera exécutée.

## Time zone {#time-zone}

Ce champ vous permet de sélectionner le fuseau horaire de l’activité. Pour en savoir plus : [Gestion des fuseaux](../../workflow/using/managing-time-zones.md)horaires.

## En cas d&#39;erreur {#in-case-of-errors}

Ce champ vous permet de définir l&#39;action à effectuer lorsque l&#39;activité est en erreur. Deux options sont disponibles :

* **[!UICONTROL Stop the process]**: le processus est arrêté automatiquement. Son statut devient **[!UICONTROL Failed]**. Une fois le problème résolu, redémarrez le flux de travaux.
* **[!UICONTROL Ignore]**: cette tâche et toutes les tâches suivantes (dans la même branche) ne sont pas exécutées. Cela peut s’avérer utile pour les tâches récurrentes. Si un planificateur est placé en amont de la branche, il démarrera comme d’habitude à la date d’exécution suivante.

## Script d&#39;initialisation {#initialization-script}

Ce champ vous permet d’initialiser des variables ou de modifier des propriétés d’activité. Pour plus d’informations à ce sujet, voir : Scripts [JavaScript et modèles](../../workflow/using/javascript-scripts-and-templates.md).

## Commentaire {#comment}

The **[!UICONTROL Comment]** field is a free field that lets you add a description.
