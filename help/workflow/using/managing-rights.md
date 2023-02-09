---
product: campaign
title: Gestion des autorisations relatives aux workflows
description: Découvrez comment gérer les autorisations relatives aux workflows
feature: Workflows
exl-id: 88995fb3-d336-4355-acd4-33118dd0e2b0
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 100%

---

# Gestion des autorisations relatives aux workflows{#managing-rights}

![](../../assets/v7-only.svg)

Pour créer, exécuter ou modifier les workflows, les opérateurs Adobe Campaign, lorsqu&#39;ils ne sont pas Administrateurs, doivent avoir les droits correspondants.

D&#39;une manière générale, les opérateurs qui agissent sur les workflows doivent pouvoir accéder aux dossiers contenant les données utilisées dans les différentes activités (destinataires, listes de destinataires, abonnements, diffusions, etc.), et éventuellement à leurs sous-dossiers.

Ils doivent également être associés aux droits nommés correspondants aux actions réalisées par les workflows sur lesquels ils sont amenés à intervenir (import de destinataires, accès aux fichiers, fusion, exécution de scripts SQL, etc.).

La gestion des opérateurs et des autorisations associées sont présentées dans cette [section](../../platform/using/access-management.md).

## Les groupes d&#39;opérateurs {#operator-groups-wf}

Les groupes d&#39;opérateurs associés aux workflows sont les suivants :

* Le groupe **[!UICONTROL Exécution des workflows]** permet de contrôler l&#39;exécution et la validation des workflows de ciblage : le droit nommé WORKFLOW est associé aux opérateurs de ce groupe. Il est nécessaire à toute action sur les workflows, en plus des permissions d&#39;accès aux dossiers de données. Le groupe **[!UICONTROL Exécution des workflows]** a par défaut accès en lecture aux dossiers standard des workflows de ciblage et des modèles de workflow. Les opérateurs de ce groupe ont également accès en lecture et en écriture au dossier des validations en attente.
* Le groupe **[!UICONTROL Superviseurs de workflows]** permet aux opérateurs de gérer les validations de workflows.
* Le groupe **[!UICONTROL Chargés d&#39;opération]** pour accéder aux workflows des opérations.

## Droits nommés {#named-rights}

Seul le droit nommé WORKFLOW est spécifique aux workflows : il permet de créer, démarrer et arrêter les workflows. Le droit en lecture sur le dossier des workflows est au minimum requis pour que ce droit nommé puisse s&#39;appliquer. Pour les workflows de ciblage, le droit en lecture sur le dossier **[!UICONTROL Profils et Cibles]** est nécessaire.

## Compte d&#39;exécution d&#39;un workflow {#workflow-execution-account}

Vous pouvez paramétrer, au niveau du modèle de workflow, le compte d&#39;exécution à utiliser. Le compte d&#39;exécution permet d&#39;associer les permissions directement au workflow, indépendamment de l&#39;opérateur Adobe Campaign qui lancera son exécution. Par défaut, chaque workflow s&#39;exécute avec les droits de l&#39;opérateur qui l&#39;a démarré.

Pour associer un compte d&#39;exécution à un workflow, accédez à la liste des modèles de workflow et cliquez avec le bouton droit de la souris sur le modèle associé au workflow. Choisissez **[!UICONTROL Action > Changer le compte d&#39;exécution...]** puis sélectionnez le compte à utiliser.
