---
solution: Campaign Classic
product: campaign
title: Note technique
description: Note technique
hide: false
hidefromtoc: true
translation-type: tm+mt
source-git-commit: 08c6e84e07da2811c91aa58ddf40c5781de2b163
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 60%

---


# Mise à jour du certificat du serveur de service de notifications Push Apple {#apns-certificate-update}

Le 29 mars 2021, une mise à jour de l’infrastructure du service Apple Push Notification (APNs) aura un impact sur le canal iOS d’Adobe Campaign Classic. Une modification de la configuration du système d’exploitation est **obligatoire** pour éviter une coupure du canal push d’iOS.

Pour en savoir plus sur les modifications apportées à APNs, consultez [cette page](https://developer.apple.com/news/?id=7gx0a2lp).

En tant que client hébergé, aucune action n’est nécessaire : Adobe a déjà incorporé le nouveau certificat racine à votre environnement.

En tant que client On-premise/hybride, vous devez mettre à jour votre configuration afin de garantir une transition harmonieuse **avant le 29 mars 2021**.

Pour incorporer le nouveau certificat, procédez comme suit :

1. Téléchargez le **certificat AAACertificateServices 5/12/2020** certificat racine [à partir de cette page](https://support.sectigo.com/Com_KnowledgeDetailPage?Id=kA03l00000117cL).

1. Vérifiez que le certificat AAA est présent à la fois dans votre système d’exploitation et dans les Trust Store JAVA. Sinon, ajoutez-le.

1. Redémarrez le service Web Adobe Campaign :

   ```
   nlserver restart web
   ```

