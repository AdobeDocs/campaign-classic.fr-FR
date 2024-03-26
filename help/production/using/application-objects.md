---
product: campaign
title: Objets d'application
description: Objets d'application
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: fb4798d7-0a2c-455b-86b6-3dcb5fd25c82
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 69%

---

# Objets d&#39;application{#application-objects}



Les objets natifs doivent être suivis. Il est important d&#39;éviter une croissance trop importante.

## Séquence d&#39;identifiants {#sequence-of-ids}

Adobe Campaign utilise une séquence d&#39;identifiants qui doit être consommée en conséquence : **xtkNewId**. Si la séquence est consommée très rapidement (c&#39;est-à-dire à partir de 100 000 par jour), vous devez vérifier que cela correspond aux exigences de votre entreprise (envoi de millions d&#39;emails par jour, par exemple). Il est possible de définir une séquence dédiée pour des tables spécifiques. Vous pouvez configurer un workflow pour suivre l&#39;utilisation des identifiants.

Lorsque la séquence dépasse les 2 milliards (2 147 483 648 pour être exact), elle revient à zéro, ce qui crée des problèmes et doit être évité. Cette séquence doit donc être suivie.

Pour éviter cela avec les tableaux volumineux, pensez à utiliser une séquence spécifique. Vous pouvez le faire à l’aide de la méthode **pkSequence** dans le schéma.

Les workflows avec une fréquence élevée qui crée de nombreux logs consomment de nombreux identifiants. Il est donc vivement recommandé d&#39;éviter un trop grand nombre de logs et des workflows à haute fréquence.

Si le cycle de la séquence est déjà terminé, la meilleure solution consiste à passer à des identifiants négatifs à partir de -2 147 483 648.

## Dossiers {#folders}

Le nombre de dossiers sur chaque instance doit être inférieur à 1 000. Un nombre de dossiers supérieur peut entraîner des problèmes de performance du client Campaign. Vous pouvez configurer une opération de suivi pour comptabiliser le nombre de dossiers, de workflows, etc. Vous pouvez créer des rapports régulièrement.

Cette méthode permet également de mettre en lumière les utilisateurs qui créent trop d&#39;objets.

## Diffusions {#deliveries}

L&#39;instance doit contenir, à tout moment, moins de 1 000 diffusions. Le fait d’avoir beaucoup de diffusions consomme de l’espace de base de données et crée des problèmes. Une instance qui crée plus de 10 diffusions par jour doit être comparée aux besoins de l’entreprise. Envisagez d’utiliser des diffusions au fil de l’eau pour créer moins de diffusions. Pour plus d’informations, consultez [cette section](../../workflow/using/continuous-delivery.md).

Les diffusions de plus de deux ans doivent être purgées de l&#39;instance.

## Fichiers {#files}

Le nombre de fichiers sur le disque du serveur applicatif ne doit pas augmenter indéfiniment.

Les workflows d&#39;import créent des fichiers et entraînent donc une extension de disque. Cela peut être évité en utilisant la norme [Collecteur de fichiers](../../workflow/using/file-collector.md) activité. Le collecteur de fichiers déplace les fichiers vers un dossier temporaire et les purge automatiquement.

Si un workflow importe des fichiers et n&#39;utilise pas les fonctionnalités standards, il doit être purgé pour conserver un espace disque minimal.

## Données transactionnelles et logs {#transactional-data-and-logs}

Chaque [workflow](../../workflow/using/data-life-cycle.md#work-table) qui importe des données dans Adobe Campaign entraîne une augmentation de la taille de la base de données.

Vérifiez que les workflows de nettoyage ou de purge sont en cours d’exécution et qu’ils purgent effectivement les enregistrements. Toutes les données et tous les logs transactionnels doivent être purgés. La tâche de nettoyage purge les tables standards uniquement : logs de tracking et broadlogs. Les tables spécifiques doivent être purgées par des workflows spécifiques. Consultez [cette section](../../workflow/using/monitoring-workflow-execution.md#purging-the-logs).

Surveillez les données transactionnelles âgées en vérifiant la date la plus ancienne de création des enregistrements.
