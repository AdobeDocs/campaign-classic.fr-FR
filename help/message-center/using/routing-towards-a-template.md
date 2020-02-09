---
title: Acheminement vers un modèle
seo-title: Acheminement vers un modèle
description: Acheminement vers un modèle
seo-description: null
page-status-flag: never-activated
uuid: 1f8252c4-7f96-4759-9544-39b8f854961f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: event-processing
discoiquuid: 8fa464e6-3c88-441c-8179-0c54960469a7
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Acheminement vers un modèle{#routing-towards-a-template}

Lorsque le modèle de message est publié sur la ou les instances d&#39;exécution, deux modèles destinés à être associés respectivement à un événement temps réel ou à un événement batch sont automatiquement générés. L&#39;étape d&#39;acheminement consiste à associer un événement avec le modèle de message qui lui correspond. L&#39;association entre l&#39;événement et le modèle de message est basée sur le type d&#39;événement spécifié dans les propriétés de l&#39;événement lui-même et dans celles du modèle.

Définition du type d&#39;événement dans les propriétés de l&#39;événement :

![](assets/messagecenter_event_type_001.png)

Définition du type d&#39;événement dans les propriétés du modèle de message :

![](assets/messagecenter_event_type_002.png)

Par défaut, l&#39;acheminement est basé sur les informations suivantes :

* le type d&#39;événement,
* le canal à utiliser (email par défaut),
* le modèle de diffusion le plus récent, selon la date de publication.

