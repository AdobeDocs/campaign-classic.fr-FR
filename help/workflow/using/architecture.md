---
product: campaign
title: Architecture
description: Les workflows sont pris en charge par un module spécifique. Ce module peut être démarré sur plusieurs serveurs afin de répartir la charge d’exécution.
feature: Workflows
hide: true
exl-id: 46801f78-706c-4dfa-bce7-3d15f569f222
TQID: https://experienceleague.adobe.com/lQLXeSTFhKRCNhA9SdShd9Nyd1mbNt-KPa-XJw-6wAs
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: id: ee25c34b-ea50-427b-9369-ba0a160f7d70id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22fid: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 116
ht-degree: 100%

---

# Architecture {#architecture}



Les workflows sont gérés par un module spécifique.Ce module peut être démarré sur plusieurs serveurs afin de répartir la charge de traitement.

![](assets/architecture.png)

* Le processus « Workflow Instance Runner » (runwf) exécute toutes les tâches d’une instance de workflow donnée.Lorsqu’il n’y a plus de tâche à exécuter dans l’immédiat, ce processus devient « passif », c’est-à-dire qu’il sauvegarde son statut dans la base de données puis s’arrête.
* Le module « Workflow Server » (wfserver) surveille les instances de workflow en cours.Lorsqu’il y a une tâche à effectuer, ce module crée un processus pour activer (ou réactiver) l’instance correspondante.
