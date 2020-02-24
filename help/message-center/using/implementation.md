---
title: Mise en oeuvre
seo-title: Mise en oeuvre
description: Mise en oeuvre
seo-description: null
page-status-flag: never-activated
uuid: 12b5fbbf-fe0d-4598-8845-f7b8ee7672c3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: use-case
discoiquuid: ac1c0a00-41ef-4cc2-bb51-2808ef400bb1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Mise en oeuvre{#implementation}

Voici un diagramme avec les différentes étapes impliquées dans ce scénario.

![](assets/message-center-uc1.png)

Commencez par concevoir votre pièce jointe. Consultez cet [article](../../delivery/using/attaching-files.md#attach-a-personalized-file). Vous pouvez ainsi joindre les fichiers à un email, même s&#39;ils ne sont pas hébergés sur l&#39;instance d&#39;exécution.

Vous pouvez envoyer des courriers électroniques via un déclencheur de message SOAP. Pour plus d’informations sur les requêtes SOAP, voir Description [de l’](../../message-center/using/event-description.md)événement. Dans l’appel SOAP, il existe un paramètre d’URL (URL de la pièce jointe).

Lors de la conception de votre email, cliquez sur **[!UICONTROL Pièce jointe]**. Dans l&#39;écran **[!UICONTROL Définition d&#39;un fichier attaché]**, saisissez le paramètre de pièce jointe SOAP :

```
<%= rtEvent.ctx.attachementUrl %>
```

Lorsque le message est en cours de traitement/déploiement, le système extrait le fichier de l&#39;emplacement distant (serveur tiers) et le joint au message.

Comme ce paramètre peut être une variable, il doit accepter la variable d&#39;URL distante entièrement formée de votre fichier, envoyée via l&#39;appel SOAP.

![](assets/message-center-uc2.png)

