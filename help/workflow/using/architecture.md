---
product: campaign
title: Architecture
description: Les workflows sont pris en charge par un module spécifique. Ce module peut être démarré sur plusieurs serveurs afin de répartir la charge d’exécution.
feature: Workflows
hide: true
exl-id: 46801f78-706c-4dfa-bce7-3d15f569f222
source-git-commit: 720a5f4edf534788f7fd143a476c25e58a6f1586
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 19%

---

# Architecture {#architecture}



Les workflows sont gérés par un module spécifique. Ce module peut être démarré sur plusieurs serveurs afin de partager la charge de traitement.

![](assets/architecture.png)

* Le processus « Workflow Instance Runner » (runwf) exécute toutes les tâches d’une instance de workflow donnée. Lorsqu&#39;il n&#39;y a pas de tâche à exécuter pour l&#39;instant, il devient &#39;passif&#39;, c&#39;est-à-dire qu&#39;il conserve son état dans la base de données, puis s&#39;arrête.
* Le module « Workflow Server » (wfserver) surveille les instances de workflow actuelles. Lorsqu’il existe une tâche à effectuer, ce module crée un processus pour activer (ou réactiver) l’instance correspondante.
