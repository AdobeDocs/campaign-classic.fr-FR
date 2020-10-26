---
title: Objets d'application
seo-title: Objets d'application
description: Objets d'application
seo-description: null
page-status-flag: never-activated
uuid: 84fbad0f-872d-4aca-8ea9-007577be076d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: database-maintenance
discoiquuid: 24d4875b-81fa-4bf3-8cf0-e6998bec4949
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '461'
ht-degree: 100%

---


# Objets d&#39;application{#application-objects}

Les objets natifs doivent être suivis. Il est important d&#39;éviter une croissance trop importante.

## Séquence d&#39;identifiants {#sequence-of-ids}

Adobe Campaign utilise une séquence d&#39;identifiants qui doit être consommée en conséquence : **xtkNewId**. Si la séquence est consommée très rapidement (c&#39;est-à-dire à partir de 100 000 par jour), vous devez vérifier que cela correspond aux besoins de votre entreprise (envoi de millions d&#39;emails par jour, par exemple). Il est possible de définir une séquence dédiée pour des tables spécifiques. Vous pouvez configurer un workflow pour suivre l&#39;utilisation des identifiants.

Lorsque la séquence dépasse les 2 milliards (2 147 483 648 pour être exact), elle revient à zéro, ce qui crée des problèmes et doit être évité. Cette séquence doit donc être suivie.

Pour empêcher ce problème avec les tables volumineuses, envisagez d&#39;utiliser une séquence spécifique. Cela peut être réalisé avec l&#39;attribut **pkSequence** dans le schéma.

Les workflows avec une fréquence élevée qui crée de nombreux logs consomment de nombreux identifiants. Il est donc vivement recommandé d&#39;éviter un trop grand nombre de logs et des workflows à haute fréquence.

Si le cycle de la séquence est déjà terminé, la meilleure solution consiste à passer à des identifiants négatifs à partir de -2 147 483 648.

## Dossiers {#folders}

Le nombre de dossiers sur chaque instance doit être inférieur à 1 000. Un nombre de dossiers supérieur peut entraîner des problèmes de performance du client Campaign. Vous pouvez configurer une opération de suivi pour comptabiliser le nombre de dossiers, de workflows, etc. Vous pouvez créer des rapports régulièrement.

Cette méthode permet également de mettre en lumière les utilisateurs qui créent trop d&#39;objets.

## Diffusions {#deliveries}

Le nombre de diffusions doit être à tout moment inférieur à 1 000 sur l&#39;instance. Un nombre trop élevé de diffusions occupe de l&#39;espace de base de données et entraîne des problèmes. Une instance qui crée plus de 10 diffusions par jour doit être contrôlée au regard des besoins de l&#39;entreprise. Envisagez d&#39;utiliser des diffusions au fil de l&#39;eau pour créer un nombre inférieur de diffusions. Pour plus d&#39;informations, consultez [cette section](../../workflow/using/continuous-delivery.md).

Les diffusions de plus de deux ans doivent être purgées de l&#39;instance.

## Fichiers {#files}

Le nombre de fichiers sur le disque du serveur applicatif ne doit pas augmenter indéfiniment.

Les workflows d&#39;import créent des fichiers et peuvent donc entraîner une extension de disque. Ce problème peut être évité grâce à l&#39;activité [Collecteur de fichiers](../../workflow/using/file-collector.md) standard. Le collecteur de fichiers déplace les fichiers vers un dossier temporaire et les purge automatiquement.

Si un workflow importe des fichiers et n&#39;utilise pas les fonctionnalités standards, il doit être purgé pour conserver un espace disque minimal.

## Données transactionnelles et logs {#transactional-data-and-logs}

Chaque [workflow](../../workflow/using/data-life-cycle.md#work-table) qui importe des données dans Adobe Campaign entraîne une augmentation de la taille de la base de données.

Vérifiez que les workflows de nettoyage ou de purge sont en cours d&#39;exécution et qu&#39;ils purgent effectivement les enregistrements. L&#39;ensemble des données transactionnelles et des logs doivent être purgés. La tâche de nettoyage purge les tables standards uniquement : logs de tracking et broadlogs. Les tables spécifiques doivent être purgées par des workflows en particulier. Voir à ce propos [cette section](../../workflow/using/monitoring-workflow-execution.md#purging-the-logs).

Surveillez les données transactionnelles âgées en vérifiant la date la plus ancienne de création des enregistrements.
