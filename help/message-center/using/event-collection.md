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
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90
workflow-type: ht
source-wordcount: '106'
ht-degree: 100%

---


# Collecte des événements{#event-collection}

Les événements générés par le système d&#39;information peuvent être collectés selon deux modes :

* l’appel à des méthodes SOAP permet de pousser les événements dans Adobe Campaign (la méthode PushEvent permet d’envoyer un événement à la fois, la méthode PushEvents d’en envoyer plusieurs). Voir la section [Description des événements](../../message-center/using/event-description.md).
* la réalisation d&#39;un workflow permet de récupérer les événements par import de fichier ou via une passerelle SQL (avec l&#39;option **Federated Data Access**).

Une fois collectés, les événements sont ensuite répartis par les workflows techniques entre les files d&#39;attente temps réel ou batch des instances d&#39;exécution en attendant d&#39;être associés à un modèle de message.

![](assets/messagecenter_events_queues_001.png)

