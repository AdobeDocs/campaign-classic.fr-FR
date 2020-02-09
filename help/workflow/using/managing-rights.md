---
title: Gestion des droits
seo-title: Gestion des droits
description: Gestion des droits
seo-description: null
page-status-flag: never-activated
uuid: 07039fec-c957-4548-acc7-22dc7827a54b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: advanced-management
discoiquuid: f78603e9-f6ff-4ebe-941b-b3fbd1924b71
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Gestion des droits{#managing-rights}

Pour créer, exécuter ou modifier les workflows, les opérateurs Adobe Campaign, lorsqu&#39;ils ne sont pas Administrateurs, doivent avoir les droits correspondants.

D&#39;une manière générale, les opérateurs qui agissent sur les workflows doivent pouvoir accéder aux dossiers contenant les données utilisées dans les différentes activités (destinataires, listes de destinataires, abonnements, diffusions, etc.), et éventuellement à leurs sous-dossiers.

Ils doivent également être associés aux droits nommés correspondants aux actions réalisées par les workflows sur lesquels ils sont amenés à intervenir (import de destinataires, accès aux fichiers, fusion, exécution de scripts SQL, etc.).

La gestion des opérateurs et des permissions associées sont présentées dans cette [section](../../platform/using/access-management.md).

## Les groupes d&#39;opérateurs {#operator-groups}

Les groupes d&#39;opérateurs associés aux workflows sont les suivants :

* Le **[!UICONTROL Workflow execution]** groupe vous permet de contrôler l’exécution et l’approbation des processus de ciblage : le WORKFLOW nommé right est mappé aux opérateurs de ce groupe. Elle est requise pour toutes les actions sur les processus, en plus des droits d’accès aux fichiers de données. Par défaut, le **[!UICONTROL Workflow execution]** groupe dispose d’un accès en lecture seule aux fichiers de flux de travail de ciblage standard et aux modèles de flux de travail. Les opérateurs de ce groupe ont également accès en lecture et en écriture au fichier d&#39;approbations en attente.
* The **[!UICONTROL Workflow supervisors]** group lets operators manage workflow approvals.
* Le **[!UICONTROL Operation Managers]** groupe pour accéder aux processus de campagne.

## Droits nommés {#named-rights}

Seul le flux de travail nommé right est spécifique aux processus : il vous permet de créer, démarrer et arrêter des processus. Les droits de lecture sur le fichier de flux de travail sont requis pour que le droit nommé soit applicable. Pour les processus de ciblage, la lecture à droite du **[!UICONTROL Profiles and Targets]** fichier est nécessaire.

## Compte d&#39;exécution d&#39;un workflow {#workflow-execution-account}

Vous pouvez paramétrer, au niveau du modèle de workflow, le compte d&#39;exécution à utiliser. Le compte d&#39;exécution permet d&#39;associer les permissions directement au workflow, indépendamment de l&#39;opérateur Adobe Campaign qui lancera son exécution. Par défaut, chaque workflow s&#39;exécute avec les droits de l&#39;opérateur qui l&#39;a démarré.

Pour mapper un compte d’exécution à un processus, accédez à la liste des modèles de processus et cliquez avec le bouton droit sur le modèle lié au processus. Sélectionnez **[!UICONTROL Action > Change execution account...]** ensuite le compte à utiliser.
