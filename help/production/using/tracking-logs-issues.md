---
solution: Campaign Classic
product: campaign
title: Problèmes relatifs aux logs de tracking
description: Problèmes relatifs aux logs de tracking
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: ht
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: ht
source-wordcount: '69'
ht-degree: 100%

---


# Problèmes relatifs aux logs de tracking{#tracking-logs-issues}

Lorsque les logs de tracking ne remontent pas, les causes peuvent être multiples. Nous vous recommandons de vérifier les informations suivantes :

* Le workflow **Tracking** est-il en erreur ?

   Consultez [Surveiller les workflows techniques](../../workflow/using/monitoring-technical-workflows.md).

   ![](assets/tracking_scheduled_task.png)

* Le module **trackinglogd** est-il démarré sur le serveur ?

   Consultez [Fichiers de log](../../production/using/log-files.md).

* Des modifications réseau ont-elles eu lieu ? Elles peuvent provoquer la perte de connexion aux serveurs en utilisant l&#39;alias de tracking.

