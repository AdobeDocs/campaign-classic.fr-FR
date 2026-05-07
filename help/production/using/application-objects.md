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
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 50%

---

# Objets d&#39;application{#application-objects}



Les objets natifs doivent être suivis. Il est important d&#39;éviter une croissance trop importante.

## Séquence d&#39;identifiants {#sequence-of-ids}

Adobe Campaign utilise une séquence d’identifiants qui doit être consommée en conséquence : **xtkNewId**. Si la séquence est consommée très rapidement (c’est-à-dire à partir de 100 000 par jour), vous devez vérifier qu’elle est conforme aux exigences de votre entreprise, telles que l’envoi de millions d’e-mails par jour. Il est possible de définir une séquence dédiée pour des tables particulières. Vous pouvez configurer un workflow pour surveiller l’utilisation des identifiants.

Lorsque la séquence atteint plus de 2 milliards (2 147 483 648 est le nombre exact), elle revient à zéro. Elle doit être évitée et crée des problèmes, c’est pourquoi cette séquence doit être surveillée.

Pour empêcher ce problème avec les tables volumineuses, envisagez d&#39;utiliser une séquence spécifique. Cela peut être réalisé avec l&#39;attribut **pkSequence** dans le schéma.

Les workflows haute fréquence qui créent un grand nombre de journaux consomment un grand nombre d’identifiants. Il est donc vivement recommandé d’éviter un trop grand nombre de logs et une fréquence élevée dans les workflows.

Si le cycle de la séquence est déjà terminé, la meilleure solution consiste à passer à des identifiants négatifs à partir de -2 147 483 648.

## Dossiers {#folders}

Il doit y avoir moins de 1 000 dossiers sur une instance. Un nombre trop élevé de dossiers peut entraîner des problèmes de performances avec le client Campaign. Vous pouvez configurer une tâche de surveillance pour compter le nombre de dossiers, de workflows, etc., et générer des rapports périodiques.

Cette méthode permet également de mettre en lumière les utilisateurs qui créent trop d&#39;objets.

## Diffusions {#deliveries}

Le nombre de diffusions doit être à tout moment inférieur à 1 000 sur l’instance. Un nombre élevé de diffusions occupe de l’espace de base de données et crée des problèmes. Une instance qui crée plus de 10 diffusions par jour doit être contrôlée au regard des exigences de l’entreprise. Pensez à utiliser des diffusions au fil de l’eau pour créer moins de diffusions. Pour en savoir plus, consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/continuous-delivery.html?lang=fr){target="_blank"}.

Les diffusions de plus de deux ans doivent être purgées de l&#39;instance.

## Fichiers {#files}

Le nombre de fichiers sur le disque du serveur applicatif ne doit pas augmenter indéfiniment.

Les workflows d&#39;import créent des fichiers et peuvent donc entraîner une extension de disque. Ce problème peut être évité grâce à l&#39;activité [Collecteur de fichiers](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/event-activities/file-collector.html?lang=fr){target="_blank"} standard. Le collecteur de fichiers déplace les fichiers vers un dossier temporaire et les purge automatiquement.

Si un workflow importe des fichiers et n&#39;utilise pas les fonctionnalités standards, il doit être purgé pour conserver un espace disque minimal.

## Données transactionnelles et logs {#transactional-data-and-logs}

Chaque workflow qui importe des données dans Adobe Campaign entraîne une augmentation de la taille de la base de données. Consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/use-workflow-data.html?lang=fr){target="_blank"}.

Vérifiez que les workflows de nettoyage ou de purge s’exécutent et purgent efficacement les enregistrements. Toutes les données et tous les journaux transactionnels doivent être purgés. La tâche de nettoyage purge uniquement les tables standard : logs de tracking et broadLogs. Les tables spécifiques doivent être purgées par des workflows spécifiques. Consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-workflow-execution.html?lang=fr){target="_blank"}.

Surveillez les données transactionnelles vieillissantes en vérifiant la date la plus ancienne de création des enregistrements.
