---
title: Configuration de l'intégration
seo-title: Configuration de l'intégration
description: Configuration de l'intégration
seo-description: null
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 39d6da007d69f81da959660b24b56ba2558a97ba
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 2%

---


# Surveillance du pipeline {#pipeline-monitoring}

Le service Web d’état avec pipeline fournit des informations sur l’état du processus avec pipeline.

Il est accessible manuellement à l’aide d’un navigateur ou automatiquement à l’aide d’une application de surveillance.

Il est au format REST, qui est décrit ci-dessous.

![](assets/triggers_8.png)

## Indicators {#indicators}

Cette section liste les indicateurs du service Web d’état.

Les indicateurs recommandés pour le suivi sont mis en évidence.

* Consommateur : nom du client qui extrait les déclencheurs. Configuré dans l&#39;option de pipeline.
* http-request
   * last-alive-ms-ago : le temps passé en ms depuis qu&#39;une vérification de connexion a été effectuée.
   * last-failed-cnx-ms-ago : en ms depuis la dernière fois que la vérification de connexion a échoué.
   * pipeline-host : nom de l’hôte à partir duquel les données du pipeline sont extraites.
* pointeur
   * offset courant : valeur du pointeur dans le pipeline, par thread enfant.
   * last-flush-ms-ago : durée en ms depuis la récupération d&#39;un lot de déclencheurs.
   * next-offsets-flush : délai d’attente jusqu’au lot suivant, une fois terminé.
   * traité-depuis-le-dernier vidage : nombre de déclencheurs traités dans le dernier lot.
* routage
   * triggers : liste des déclencheurs récupérés. Configuré dans l’option d’oléoduc.
* stats
   * average-pointer-flush-time-ms : temps de traitement moyen pour un lot de déclencheurs.
   * average-trigger-processing-time-ms : durée moyenne passée à analyser les données des déclencheurs.
   * bytes-read : nombre d&#39;octets lus depuis la file d&#39;attente depuis le démarrage du processus.
   * current-messages : nombre actuel de messages en attente extraits de la file d&#39;attente et en attente de traitement. **Cet indicateur doit être proche de zéro**.
   * current-Reprises : nombre actuel de messages dont le traitement a échoué et qui attendent une nouvelle tentative.
   * messages de pointe : nombre maximal de messages en attente traités par le processus depuis son démarrage.
   * pointeur-pousses : nombre de lots de messages traités depuis le début.
   * routage-JS-custom : nombre de messages qui ont été traités par le JS personnalisé.
   * trigger-discarded : nombre de messages qui ont été ignorés après trop de Reprises en raison d’erreurs de traitement.
   * traité par déclencheur : nombre de messages qui ont été traités sans erreur.
   * trigger-receive : nombre de messages reçus de la file d&#39;attente.

Ces statistiques sont affichées par thread de traitement.

* average-trigger-processing-time-ms : durée moyenne passée à analyser les données des déclencheurs.
* is-JS-processor : valeur &quot;1&quot; si ce thread utilise la JS personnalisée.
* trigger-discarded : nombre de messages qui ont été ignorés après trop de Reprises en raison d’erreurs de traitement. **Cet indicateur doit être nul**.
* trigger-failure : nombre d’erreurs de traitement dans la JS. **Cet indicateur doit être nul**.
* trigger-receive : nombre de messages reçus de la file d&#39;attente.

* Paramètres : ils sont définis dans les fichiers de configuration.
   * flush-pointer-msg-count : nombre de messages dans un lot.
   * flush-pointer-period-ms : durée entre deux lots, en millisecondes.
   * processing-threads-JS : nombre de threads de traitement exécutant le fichier JS personnalisé.
   * retry-period-ms : intervalle entre deux Reprises lorsqu’une erreur de traitement se produit.
   * retry-valid-duration-ms : durée à partir du moment où le traitement est relancé jusqu’à ce que le message soit ignoré.
   * Rapport des messages du tuyau

## Rapport de messages sur les pipelines {#pipeline-report}

Ce rapport affiche le nombre de messages par heure au cours des cinq derniers jours.

![](assets/triggers_9.png)
