---
product: campaign
title: Note technique
description: Note technique
hide: false
hidefromtoc: true
exl-id: 263fb4b5-ca62-4b92-a82d-8820ee998296
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 100%

---

# Mise à jour du certificat du serveur du service Apple Push Notification {#apns-certificate-update}

![](../../assets/v7-only.svg)

Le 29 mars 2021, une mise à jour de l’infrastructure du service Apple Push Notification (APNs) aura un impact sur le canal iOS d’Adobe Campaign Classic. Une modification de la configuration du système d’exploitation est **obligatoire** pour éviter une panne du canal push d’iOS.

Pour en savoir plus sur les modifications d’APNs, consultez [cette page](https://developer.apple.com/news/?id=7gx0a2lp).

En tant que client hébergé, aucune action n’est nécessaire : Adobe a déjà intégré le nouveau certificat racine à votre environnement.

En tant que client On-premise/hybride, vous devez mettre à jour votre configuration pour garantir une transition harmonieuse **avant le 29 mars 2021**.

Pour intégrer le nouveau certificat, procédez comme suit :

1. Téléchargez le certificat racine **AAACertificateServices 5/12/2020** [à partir de cette page](https://support.sectigo.com/Com_KnowledgeDetailPage?Id=kA03l00000117cL).

1. Vérifiez que le certificat AAA est présent à la fois dans votre système d’exploitation et dans les truststores JAVA. Sinon, ajoutez-le.

1. Redémarrez le service web d’Adobe Campaign :

   ```
   nlserver restart web
   ```