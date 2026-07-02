---
product: campaign
title: Gestion des autorisations relatives aux workflows
description: Découvrez comment gérer les autorisations relatives aux workflows
feature: Workflows
hide: true
exl-id: 88995fb3-d336-4355-acd4-33118dd0e2b0
TQID: https://experienceleague.adobe.com/4H9-yPJl4lST0JYw5wPYYCPn8eZU2eV96dFa7ZUzcgk
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
  - id: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 339
ht-degree: 100%

---

# Gestion des autorisations relatives aux workflows{#managing-rights}



Pour créer, exécuter ou modifier les workflows, les opérateurs Adobe Campaign, lorsqu&#39;ils ne sont pas Administrateurs, doivent avoir les droits correspondants.

D&#39;une manière générale, les opérateurs qui agissent sur les workflows doivent pouvoir accéder aux dossiers contenant les données utilisées dans les différentes activités (destinataires, listes de destinataires, abonnements, diffusions, etc.), et éventuellement à leurs sous-dossiers.

Ils doivent également être associés aux droits nommés correspondants aux actions réalisées par les workflows sur lesquels ils sont amenés à intervenir (import de destinataires, accès aux fichiers, fusion, exécution de scripts SQL, etc.).

La gestion des opérateurs et des autorisations associées sont présentées dans cette [section](../../platform/using/access-management.md).

## Les groupes d&#39;opérateurs {#operator-groups-wf}

Les groupes d&#39;opérateurs associés aux workflows sont les suivants :

* Le groupe **[!UICONTROL Exécution des workflows]** permet de contrôler l’exécution et l’approbation des workflows de ciblage : le droit nommé WORKFLOW est associé aux opérateurs et opératrices de ce groupe.Il est nécessaire à toutes les actions sur les workflows, en plus des droits d’accès aux fichiers de données.Par défaut, le groupe **[!UICONTROL Exécution des workflows]** a un accès en lecture seule aux fichiers de workflow de ciblage standard et aux modèles de workflow. Les opérateurs et opératrices de ce groupe ont également accès en lecture et écriture au fichier d’approbations en attente.
* Le groupe **[!UICONTROL Superviseurs de workflows]** permet aux opérateurs de gérer les validations de workflows.
* Le groupe **[!UICONTROL Chargés d&#39;opération]** pour accéder aux workflows des opérations.

## Droits nommés {#named-rights}

Seul le droit nommé WORKFLOW est spécifique aux workflows : il vous permet de créer, de démarrer et d’arrêter des workflows.Les droits de lecture sur le fichier de workflow sont nécessaires pour que le droit nommé soit applicable. Pour les workflows de ciblage, le droit en lecture sur le dossier **[!UICONTROL Profils et Cibles]** est nécessaire.

## Compte d&#39;exécution d&#39;un workflow {#workflow-execution-account}

Vous pouvez configurer le compte d’exécution à utiliser au niveau du modèle de workflow.Le compte d’exécution permet d’associer les permissions directement au workflow, indépendamment de l’opérateur ou opératrice Adobe Campaign qui lance son exécution.Par défaut, chaque workflow est exécuté avec les droits de l’opérateur ou opératrice qui l’a démarré.

Pour associer un compte d&#39;exécution à un workflow, accédez à la liste des modèles de workflow et cliquez avec le bouton droit de la souris sur le modèle associé. Sélectionnez **[!UICONTROL Action > Changer le compte d&#39;exécution]**, puis sélectionnez le compte à utiliser.
