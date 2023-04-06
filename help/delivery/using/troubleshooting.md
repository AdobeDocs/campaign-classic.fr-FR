---
product: campaign
title: Résolution des problèmes liés aux notifications push
description: Résolution des problèmes liés aux notifications push
feature: Push
exl-id: 313eae5f-40db-4b1a-b013-f4adf8781763
source-git-commit: 8d635722b8961b3edac9cc98f00f17b86f4ee523
workflow-type: ht
source-wordcount: '0'
ht-degree: 100%

---

# Résolution des problèmes{#troubleshooting}

![](../../assets/v7-only.svg)

Si votre appareil mobile est connecté en Wi-Fi et que vous ne recevez pas les notifications, vérifiez que les ports FCM/APN ne sont pas bloqués par votre pare-feu.

**Android** : l&#39;appareil mobile se connecte aux serveurs FCM sur les ports 5228 à 5230. Vous devez donc configurer votre pare-feu pour qu&#39;il autorise la connexion avec FCM. Les ports à ouvrir sont les suivants : 5228 (le plus fréquemment utilisé), 5229 et 5230.

**iOS** :

Connecteur HTTP/2 : vous devez autoriser les communications à destination et en provenance des serveurs suivants :

* api.push.apple.com : port 443
* api.development.push.apple.com : port 443

>[!NOTE]
>
>Pour plus d’informations sur les deux connecteurs, voir la section [Paramétrage de l’application mobile dans Adobe Campaign](configuring-the-mobile-application.md).
