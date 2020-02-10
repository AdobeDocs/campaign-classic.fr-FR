---
title: Problèmes relatifs aux logs de tracking
seo-title: Problèmes relatifs aux logs de tracking
description: Problèmes relatifs aux logs de tracking
seo-description: null
page-status-flag: never-activated
uuid: 996869c4-7ffe-4fcc-9555-1d8b65e93e87
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: 1b9ff479-4847-408d-a5c2-9a164805081f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e1937c1ddcbde092a22f4fe8c50d3d72b02cfeed

---


# Problèmes relatifs aux logs de tracking{#tracking-logs-issues}

Lorsque les logs de tracking ne remontent pas, les causes peuvent être multiples. Nous vous recommandons de vérifier les informations suivantes :

* Le workflow **Tracking** est-il en erreur ?

   Consultez [Surveiller les workflows techniques](../../workflow/using/monitoring-technical-workflows.md).

   ![](assets/tracking_scheduled_task.png)

* Le module **trackinglogd** est-il démarré sur le serveur ?

   Consultez [Fichiers de log](../../production/using/log-files.md).

* Des modifications réseau ont-elles eu lieu ? Elles peuvent provoquer la perte de connexion aux serveurs en utilisant l&#39;alias de tracking.

