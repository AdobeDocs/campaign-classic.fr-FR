---
solution: Campaign Classic
product: campaign
title: Recyclage de l'événement
description: Recyclage de l'événement
audience: message-center
content-type: reference
topic-tags: event-processing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 100%

---


# Recyclage de l&#39;événement{#event-recycling}

Si l&#39;envoi d&#39;un message sur un canal spécifique échoue, Adobe Campaign peut renvoyer le message en utilisant un autre canal. Par exemple, si l&#39;envoi d&#39;un message sur le canal SMS échoue, le message est renvoyé en utilisant le canal email.

Pour cela, vous devez paramétrer un workflow qui recrée tous les événements dont le statut est **Erreur de diffusion**, et leur assigner un canal différent de celui utilisé précédemment.

>[!CAUTION]
>
>Cette étape n&#39;est réalisable qu&#39;à l&#39;aide d&#39;un workflow et s&#39;adresse donc aux utilisateurs avertis. Contactez le chargé de compte Adobe pour plus d&#39;informations.

