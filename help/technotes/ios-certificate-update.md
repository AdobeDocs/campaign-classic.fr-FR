---
solution: Campaign Classic
product: campaign
title: Technote
description: Technote
hide: false
hidefromtoc: true
translation-type: tm+mt
source-git-commit: a21f970b6b81105517a11bcbd7f334173acc76e4
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 0%

---


# Mise à jour du certificat du serveur de service de notifications Push Apple {#apns-certificate-update}

Le 29 mars 2021, une mise à jour de l’infrastructure du service de notifications Push Apple (APN) aura un impact sur le canal Adobe Campaign Classic iOS. Une modification de la configuration du système d’exploitation est **obligatoire** pour éviter une panne de canal Push iOS.

Pour en savoir plus sur les modifications des APN [dans cette page](https://developer.apple.com/news/?id=7gx0a2lp).

En tant que client hébergé, aucune action n’est nécessaire : Adobe a déjà incorporé le nouveau certificat racine à votre environnement.

En tant que client sur site/hybride, vous devez mettre à jour votre configuration pour garantir une transition **transparente avant le 29 mars 2021**.

Pour incorporer le nouveau certificat, procédez comme suit :

1. Téléchargez le **certificat AAACertificateServices 5/12/2020** certificat racine [à partir de cette page](https://support.sectigo.com/Com_KnowledgeDetailPage?Id=kA03l00000117cL).

1. Ajoutez-le au Trust Store du système d’exploitation.

1. Redémarrez le service Web Adobe Campaign :

   ```
   nlserver restart web
   ```
