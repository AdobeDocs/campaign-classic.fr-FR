---
product: campaign
title: Résolution des problèmes liés aux notifications push
description: Résolution des problèmes liés aux notifications push
feature: Push, Troubleshooting
role: User
hide: true
exl-id: 313eae5f-40db-4b1a-b013-f4adf8781763
TQID: https://experienceleague.adobe.com/3T6eC52Edyai-8Bn-ioDxvB5C04iDqBNmlZzuxVturE
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 109
ht-degree: 63%

---

# Résolution des problèmes{#troubleshooting}

Si votre appareil mobile est connecté en Wi-Fi et que vous ne recevez pas les notifications, vérifiez que les ports FCM/APN ne sont pas bloqués par votre pare-feu.

**&#x200B;**&#x200B;: l&#39;appareil mobile se connecte aux serveurs FCM sur les ports 5228 à 5230. Vous devez donc configurer votre pare-feu afin qu’il autorise la connexion à FCM. Les ports à ouvrir sont : 5228 (les plus utilisés), 5229 et 5230.

**iOS** :

Connecteur HTTP/2 : vous devez autoriser les communications à destination et en provenance des serveurs suivants :

* api.push.apple.com : port 443
* api.development.push.apple.com : port 443

>[!NOTE]
>
>Pour plus d’informations sur les deux connecteurs, voir la section [Paramétrage de l’application mobile dans Adobe Campaign](configuring-the-mobile-application.md).
