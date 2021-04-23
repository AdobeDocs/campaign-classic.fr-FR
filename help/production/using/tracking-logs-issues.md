---
solution: Campaign Classic
product: campaign
title: Problèmes relatifs aux logs de tracking
description: Problèmes relatifs aux logs de tracking
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 58656aa1-aa95-451f-80b8-9e2d28223056
translation-type: ht
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: ht
source-wordcount: '69'
ht-degree: 100%

---

# Problèmes relatifs aux logs de tracking{#tracking-logs-issues}

Lorsque les logs de tracking ne remontent pas, les causes peuvent être multiples. Nous vous recommandons de vérifier les informations suivantes :

* **Le workflow** Tracking **est-il en erreur ?**

   Consultez [Surveiller les workflows techniques](../../workflow/using/monitoring-technical-workflows.md).

   ![](assets/tracking_scheduled_task.png)

* **Le module** trackinglogd **est-il démarré sur le serveur ?**

   Consultez [Fichiers de log](../../production/using/log-files.md).

* **Des modifications ont-elles été apportées ?**

   Elles peuvent provoquer la perte de connexion aux serveurs en utilisant l&#39;alias de tracking.
