---
product: campaign
title: Note technique - Mise à jour du certificat du serveur du service Apple Push Notification
description: Mise à jour du certificat du serveur du service Apple Push Notification
feature: Technote, Push
exl-id: 263fb4b5-ca62-4b92-a82d-8820ee998296
source-git-commit: 0143e0d6ebcdbd96d183ddd0c7f07beb149a9670
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 64%

---

# Mise à jour du certificat du serveur du service Apple Push Notification {#apns-certificate-update}



Le 17 octobre 2024, une mise à jour de l’infrastructure du service Apple Push Notification (APNs) a eu un impact sur le canal Adobe Campaign Classic iOS. Une modification de la configuration du système d’exploitation est **obligatoire** pour éviter une panne du canal push d’iOS.

Pour en savoir plus sur les modifications d’APNs, consultez [cette page](https://developer.apple.com/news/?id=09za8wzy).

En tant que client hébergé, aucune action n’est nécessaire : Adobe a déjà intégré le nouveau certificat racine à votre environnement.

En tant que client on-premise/hybride, vous devez mettre à jour votre configuration pour assurer une transition transparente **avant le 24 février 2025**.

Pour intégrer le nouveau certificat, procédez comme suit :

1. Téléchargez le **certificat racine SHA-2 : USERTrust RSA Certification Authority** certificat racine [à partir de cette page](https://www.sectigo.com/knowledge-base/detail/Sectigo-Intermediate-Certificates/kA01N000000rfBO).

1. Vérifiez que le certificat AAA est présent à la fois dans votre système d’exploitation et dans les truststores JAVA. Sinon, ajoutez-le.

1. Redémarrez le service web d’Adobe Campaign :

   ```
   nlserver restart web
   ```
