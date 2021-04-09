---
solution: Campaign Classic
product: campaign
title: Note technique
description: Note technique
hide: false
hidefromtoc: true
exl-id: 263fb4b5-ca62-4b92-a82d-8820ee998296
translation-type: tm+mt
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 87%

---

# Mise à jour du certificat du serveur du service Apple Push Notification {#apns-certificate-update}

Le 29 mars 2021, une mise à jour de l’infrastructure du service Apple Push Notification (APNs) aura un impact sur le canal iOS d’Adobe Campaign Classic. Une modification de la configuration du système d’exploitation est **obligatoire** pour éviter une panne du canal push d’iOS.

Pour en savoir plus sur les modifications d’APNs, consultez [cette page](https://developer.apple.com/news/?id=7gx0a2lp).

En tant que client hébergé, aucune action n’est nécessaire : Adobe a déjà intégré le nouveau certificat racine à votre environnement.

En tant que client On-premise/hybride, vous devez mettre à jour votre configuration pour garantir une transition harmonieuse **avant le 29 mars 2021**.

Pour intégrer le nouveau certificat, procédez comme suit :

1. Téléchargez le certificat racine **AAACertificateServices 5/12/2020** [à partir de cette page](https://support.sectigo.com/Com_KnowledgeDetailPage?Id=kA03l00000117cL).

1. Vérifiez que le certificat AAA est présent à la fois dans votre système d’exploitation et dans les Trust Store JAVA. Sinon, ajoutez-le.

1. Redémarrez le service web d’Adobe Campaign :

   ```
   nlserver restart web
   ```
