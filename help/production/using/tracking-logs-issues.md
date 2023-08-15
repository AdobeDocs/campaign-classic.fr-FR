---
product: campaign
title: Problèmes relatifs aux logs de tracking
description: Problèmes relatifs aux logs de tracking
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 58656aa1-aa95-451f-80b8-9e2d28223056
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '76'
ht-degree: 100%

---

# Problèmes relatifs aux logs de tracking{#tracking-logs-issues}



Lorsque les logs de tracking ne remontent pas, les causes peuvent être multiples. Nous vous recommandons de vérifier les informations suivantes :

* **Le workflow** Tracking **est-il en erreur ?**

  Consultez [Surveiller les workflows techniques](../../workflow/using/monitoring-technical-workflows.md).

  ![](assets/tracking_scheduled_task.png)

* **Le module** trackinglogd **est-il démarré sur le serveur ?**

  Consultez [Fichiers de log](../../production/using/log-files.md).

* **Des modifications ont-elles été apportées ?**

  Elles peuvent provoquer la perte de connexion aux serveurs en utilisant l&#39;alias de tracking.
