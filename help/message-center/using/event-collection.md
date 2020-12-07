---
solution: Campaign Classic
product: campaign
title: Collecte des événements
description: Collecte des événements
audience: message-center
content-type: reference
topic-tags: event-processing
translation-type: ht
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: ht
source-wordcount: '104'
ht-degree: 100%

---


# Collecte des événements{#event-collection}

Les événements générés par le système d&#39;information peuvent être collectés selon deux modes :

* L&#39;appel à des méthodes SOAP permet de pousser les événements dans Adobe Campaign (la méthode PushEvent permet d&#39;envoyer un événement à la fois, la méthode PushEvents d&#39;en envoyer plusieurs). Voir la section [Description des événements](../../message-center/using/event-description.md).
* La réalisation d&#39;un workflow permet de récupérer les événements par import de fichier ou via une passerelle SQL (avec l&#39;option **Federated Data Access**).

Une fois collectés, les événements sont ensuite répartis par les workflows techniques entre les files d&#39;attente temps réel ou par lots des instances d&#39;exécution en attendant d&#39;être associés à un modèle de message.

![](assets/messagecenter_events_queues_001.png)
