---
product: campaign
title: Surveillance du pipeline
description: Surveillance du pipeline
feature: Triggers
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
audience: integrations
content-type: reference
level: Intermediate, Experienced
exl-id: 84399496-33fd-4936-85e7-32de8503740f
TQID: https://experienceleague.adobe.com/JfrzR2a-nKDQBMQJlZ8snVIEavWU1FdJ-oPR-K3RaSg
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2:
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
  - id: df0d6518-6f49-46e2-b46e-3bcc513f553f
  - id: eb007b6d-6e57-46ab-9485-3f24d6102304
  - id: b1fd1501-3105-4d6b-b4d4-9af53126df75
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 501
ht-degree: 100%

---

# Surveillance du pipeline {#pipeline-monitoring}



Le service web de statut [!DNL pipelined] fournit des informations sur le statut du processus [!DNL pipelined].

Il est accessible manuellement à l’aide d’un navigateur ou automatiquement à l’aide d’une application de surveillance.

Il est au format REST, qui est décrit ci-dessous.

![](assets/triggers_8.png)

## Indicators {#indicators}

Cette section répertorie les indicateurs dans le service web de statut.

Les indicateurs recommandés pour la surveillance sont mis en surbrillance.

* Consumer : nom du client qui active les déclencheurs. Configuré dans l’option de pipeline.
* http-request
   * last-alive-ms-ago : laps de temps en ms depuis qu’une vérification de connexion a été effectuée.
   * last-failed-cnx-ms-ago : laps de temps en ms depuis le dernier échec de la vérification de connexion.
   * pipeline-host : nom de l’hôte à partir duquel les données du pipeline sont extraites.
* pointeur
   * current-offsets : valeur du pointeur dans le pipeline, par thread enfant.
   * last-flush-ms-ago : laps de temps en ms depuis la récupération d’un lot de déclencheurs.
   * next-offsets-flush : délai d’attente jusqu’au lot suivant, une fois le lot actuel terminé.
   * processed-since-last-flush : nombre de déclencheurs traités dans le dernier lot.
* routage
   * triggers : liste des déclencheurs récupérés. Configuré dans l’option [!DNL pipelined].
* stats
   * average-pointer-flush-time-ms : temps de traitement moyen pour un lot de déclencheurs.
   * average-trigger-processing-time-ms : temps moyen passé à analyser les données des déclencheurs.
   * bytes-read : nombre d’octets lus à partir de la file d’attente depuis le démarrage du processus.
   * current-messages : nombre actuel de messages en attente extraits de la file d’attente et en attente de traitement. **Cet indicateur doit être proche de zéro**.
   * current-retries : nombre actuel de messages dont le traitement a échoué et qui attendent une reprise.
   * peak-messages : nombre maximal de messages en attente traités par le processus depuis le démarrage de celui-ci.
   * pointer-flushes : nombre de lots de messages traités depuis le début.
   * routing-JS-custom : nombre de messages qui ont été traités par le JS personnalisé.
   * trigger-discarded : nombre de messages qui ont été ignorés après un trop grand nombre de reprises en raison d’erreurs de traitement.
   * trigger-processed : nombre de messages qui ont été traités sans erreur.
   * trigger-received : nombre de messages reçus de la file d’attente.

Ces statistiques sont affichées par thread de traitement.

* average-trigger-processing-time-ms : temps moyen passé à analyser les données des déclencheurs.
* is-JS-processor : valeur « 1 » si ce thread utilise le JS personnalisé.
* trigger-discarded : nombre de messages qui ont été ignorés après un trop grand nombre de reprises en raison d’erreurs de traitement. **Cet indicateur doit être nul**.
* trigger-failure : nombre d’erreurs de traitement dans le JS. **Cet indicateur doit être nul**.
* trigger-received : nombre de messages reçus de la file d&#39;attente.

* Paramètres : ils sont définis dans les fichiers de configuration.
   * flush-pointer-msg-count : nombre de messages dans un lot.
   * flush-pointer-period-ms : laps de temps entre deux lots, en millisecondes.
   * processing-threads-JS : nombre de threads de traitement exécutant le JS personnalisé.
   * retry-period-ms : laps de temps entre deux reprises lorsqu’une erreur de traitement se produit.
   * retry-valid-duration-ms : durée à partir du moment où le traitement est relancé et jusqu’à ce que le message soit ignoré.
   * Rapport des messages de pipeline

## Rapport des messages de pipeline {#pipeline-report}

Ce rapport affiche le nombre de messages par heure au cours des cinq derniers jours.

![](assets/triggers_9.png)
