---
title: Collecte des événements
seo-title: Collecte des événements
description: Collecte des événements
seo-description: null
page-status-flag: never-activated
uuid: 8c373962-40d4-4982-9bd1-ce1cf8261dd5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: event-processing
discoiquuid: cfff302a-6ac0-461a-a1e4-8e4b617fe134
translation-type: tm+mt
source-git-commit: 95dff2f3704e316e9ec9e454a8f3fb9835508ccd
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 50%

---


# Collecte des événements{#event-collection}

Les événements générés par le système d&#39;information peuvent être collectés selon deux modes :

* Les appels aux méthodes SOAP vous permettent de pousser des événements dans Adobe Campaign : La méthode PushEvent vous permet d&#39;envoyer un événement à la fois, tandis que la méthode PushEvents vous permet d&#39;en envoyer plusieurs à la fois. Voir la section [Description des événements](../../message-center/using/event-description.md).
* Creating a workflow lets you recover events by importing files or via an SQL gateway (with the **Federated Data Access** option).

Une fois collectés, les événements sont ensuite répartis par les workflows techniques entre les files d&#39;attente temps réel ou batch des instances d&#39;exécution en attendant d&#39;être associés à un modèle de message.

![](assets/messagecenter_events_queues_001.png)
