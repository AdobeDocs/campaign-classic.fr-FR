---
title: Résolution des problèmes
seo-title: Résolution des problèmes
description: Résolution des problèmes
seo-description: null
page-status-flag: never-activated
uuid: 02bd48cf-3928-4817-97b0-1e64cc8ad8ef
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
discoiquuid: b64c9729-cfe2-4d02-8c59-9e53efd34a96
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# Résolution des problèmes{#troubleshooting}

Si votre appareil mobile est connecté en Wi-Fi et que vous ne recevez pas les notifications, vérifiez que les ports FCM/APNS ne sont pas bloqués par votre pare-feu.

**Android** : l&#39;appareil mobile se connecte aux serveurs FCM sur les ports 5228 à 5230. Vous devez donc configurer votre pare-feu pour qu&#39;il autorise la connexion avec FCM. Les ports à ouvrir sont les suivants : 5228 (le plus fréquemment utilisé), 5229 et 5230.

**iOS** :

Connecteur binaire : pour envoyer des notifications, vous devez autoriser le trafic TCP entrant et sortant sur le port 2195. Les appareils connectés au service push doivent autoriser le trafic TCP entrant et sortant sur le port 5223.

Connecteur HTTP/2 : vous devez autoriser les communications à destination et en provenance des serveurs suivants :

* api.push.apple.com : port 443
* api.development.push.apple.com : port 443

>[!NOTE]
>
>For more information on the two connectors, refer to [Connectors](../../delivery/using/setting-up-mobile-app-channel.md#connectors).
