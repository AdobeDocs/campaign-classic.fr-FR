---
solution: Campaign Classic
product: campaign
title: Purge des événements
description: Purge des événements
audience: message-center
content-type: reference
topic-tags: instance-configuration
translation-type: tm+mt
source-git-commit: 5bc6c8a824929c6a61cf562fc961e5bdd1867837
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 100%

---


# Purge des événements{#purging-events}

Vous pouvez utiliser l&#39;[assistant de déploiement](../../production/using/database-cleanup-workflow.md#deployment-wizard) pour configurer la durée pendant laquelle vous souhaitez conserver les événements en base dans la base de données.

La purge des événements est effectuée automatiquement par le workflow [](../../production/using/database-cleanup-workflow.md)Nettoyage de la base. Ce workflow purge les événements reçus et stockés sur les instances d&#39;exécution et des événements archivés sur une instance de pilotage.

Pour modifier les paramètres de purge, utilisez la flèche ascendante et descendante.

Paramètres de purge des événements sur une instance de pilotage :

![](assets/messagecenter_delete_events_001.png)

Paramètres de purge des événements sur une instance d&#39;exécution :

![](assets/messagecenter_delete_events_002.png)

Pour plus d&#39;informations sur le workflow de nettoyage de la base, consultez [cette section](../../production/using/database-cleanup-workflow.md).
