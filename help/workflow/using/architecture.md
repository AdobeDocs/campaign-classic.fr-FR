---
product: campaign
title: Architecture
description: Les workflows sont pris en charge par un module spécifique. Ce module peut être démarré sur plusieurs serveurs afin de répartir la charge d’exécution.
feature: Workflows
hide: true
exl-id: 46801f78-706c-4dfa-bce7-3d15f569f222
TQID: https://experienceleague.adobe.com/lQLXeSTFhKRCNhA9SdShd9Nyd1mbNt-KPa-XJw-6wAs
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 116
ht-degree: 19%

---

# Architecture {#architecture}



Les workflows sont gérés par un module spécifique. Ce module peut être démarré sur plusieurs serveurs afin de partager la charge de traitement.

![](assets/architecture.png)

* Le processus « Workflow Instance Runner » (runwf) exécute toutes les tâches d’une instance de workflow donnée. Lorsqu&#39;il n&#39;y a pas de tâche à exécuter pour l&#39;instant, il devient &#39;passif&#39;, c&#39;est-à-dire qu&#39;il conserve son état dans la base de données, puis s&#39;arrête.
* Le module « Workflow Server » (wfserver) surveille les instances de workflow actuelles. Lorsqu’il existe une tâche à effectuer, ce module crée un processus pour activer (ou réactiver) l’instance correspondante.
