---
product: campaign
title: Objets d'application
description: Objets d'application
feature: Monitoring
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: fb4798d7-0a2c-455b-86b6-3dcb5fd25c82
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: ht
source-wordcount: '480'
ht-degree: 100%

---

# Objets d&#39;application{#application-objects}



Les objets natifs doivent être suivis. Il est important d&#39;éviter une croissance trop importante.

## Séquence d&#39;identifiants {#sequence-of-ids}

Adobe Campaign utilise une séquence d&#39;identifiants qui doit être consommée en conséquence : **xtkNewId**. Si la séquence est consommée très rapidement (c&#39;est-à-dire à partir de 100 000 par jour), vous devez vérifier que cela correspond aux exigences de votre entreprise (envoi de millions d&#39;emails par jour, par exemple). Il est possible de définir une séquence dédiée pour des tables spécifiques. Vous pouvez configurer un workflow pour suivre l&#39;utilisation des identifiants.

Lorsque la séquence dépasse les 2 milliards (2 147 483 648 pour être exact), elle revient à zéro, ce qui crée des problèmes et doit être évité. Cette séquence doit donc être suivie.

Pour empêcher ce problème avec les tables volumineuses, envisagez d&#39;utiliser une séquence spécifique. Cela peut être réalisé avec l&#39;attribut **pkSequence** dans le schéma.

Les workflows avec une fréquence élevée qui crée de nombreux logs consomment de nombreux identifiants. Il est donc vivement recommandé d&#39;éviter un trop grand nombre de logs et des workflows à haute fréquence.

Si le cycle de la séquence est déjà terminé, la meilleure solution consiste à passer à des identifiants négatifs à partir de -2 147 483 648.

## Dossiers {#folders}

Le nombre de dossiers sur chaque instance doit être inférieur à 1 000. Un nombre de dossiers supérieur peut entraîner des problèmes de performance du client Campaign. Vous pouvez configurer un traitement de surveillance pour comptabiliser le nombre de dossiers, de workflows, etc. Vous pouvez créer des rapports régulièrement.

Cette méthode permet également de mettre en lumière les utilisateurs qui créent trop d&#39;objets.

## Diffusions {#deliveries}

Le nombre de diffusions doit être à tout moment inférieur à 1 000 sur l&#39;instance. Un nombre trop élevé de diffusions occupe de l&#39;espace de base de données et entraîne des problèmes. Une instance qui crée plus de 10 diffusions par jour doit être contrôlée au regard des besoins de l&#39;entreprise. Pensez à utiliser des diffusions continues pour créer un nombre inférieur de diffusions. Pour en savoir plus, consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/continuous-delivery.html?lang=fr){target="_blank"}.

Les diffusions de plus de deux ans doivent être purgées de l&#39;instance.

## Fichiers {#files}

Le nombre de fichiers sur le disque du serveur applicatif ne doit pas augmenter indéfiniment.

Les workflows d&#39;import créent des fichiers et peuvent donc entraîner une extension de disque. Ce problème peut être évité grâce à l&#39;activité [Collecteur de fichiers](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/event-activities/file-collector.html?lang=fr){target="_blank"} standard. Le collecteur de fichiers déplace les fichiers vers un dossier temporaire et les purge automatiquement.

Si un workflow importe des fichiers et n&#39;utilise pas les fonctionnalités standards, il doit être purgé pour conserver un espace disque minimal.

## Données transactionnelles et logs {#transactional-data-and-logs}

Chaque workflow qui importe des données dans Adobe Campaign entraîne une augmentation de la taille de la base de données. Consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/use-workflow-data.html?lang=fr){target="_blank"}.

Vérifiez que les workflows de nettoyage ou de purge sont en cours d’exécution et qu’ils purgent effectivement les enregistrements. L’ensemble des données transactionnelles et des logs doivent être purgés. La tâche de nettoyage purge uniquement les tables standard : logs de tracking et broadlogs. Les tables spécifiques doivent être purgées par des workflows spécifiques. Consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-workflow-execution.html?lang=fr){target="_blank"}.

Surveillez les données transactionnelles vieillissantes en vérifiant la date la plus ancienne de création des enregistrements.
