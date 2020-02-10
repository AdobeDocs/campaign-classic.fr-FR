---
title: Recyclage de l'événement
seo-title: Recyclage de l'événement
description: Recyclage de l'événement
seo-description: null
page-status-flag: never-activated
uuid: 55624a41-65a1-4759-8087-6e5d2c5c5b62
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: event-processing
discoiquuid: 568a9dec-5818-4666-b858-aa41fe827b92
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Recyclage de l&#39;événement{#event-recycling}

Si l&#39;envoi d&#39;un message sur un canal spécifique échoue, Adobe Campaign peut renvoyer le message en utilisant un autre canal. Par exemple, si l&#39;envoi d&#39;un message sur le canal SMS échoue, le message est renvoyé en utilisant le canal email.

To do this, you need to configure a workflow which recreates all events with the **Delivery error** status, and assigns a different channel to them.

>[!CAUTION]
>
>Cette étape n&#39;est réalisable qu&#39;à l&#39;aide d&#39;un workflow et s&#39;adresse donc aux utilisateurs avertis. Contactez le chargé de compte Adobe pour plus d&#39;informations.

