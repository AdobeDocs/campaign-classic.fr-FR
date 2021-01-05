---
solution: Campaign Classic
product: campaign
title: Problèmes liés à l'affichage des images
description: Problèmes liés à l'affichage des images
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 50f95d7156e7104d90fa7a31eea30711b9c11bbf
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 35%

---


# Problèmes liés à l&#39;affichage des images{#image-display-issues}

Si vous rencontrez des problèmes d&#39;affichage des images dans un message envoyé, les raisons peuvent être liées à un emplacement incorrect :

* Les emplacements peuvent ne pas correspondre ou les images n&#39;ont pas été correctement transférées vers le serveur de suivi de duplicata : vérifiez votre configuration.
* Les images ne peuvent pas résider dans le dossier ressource publique de l’instance marketing : téléchargez les images dans votre dossier de ressources pour résoudre le problème.
* Si vous travaillez dans une architecture de midsourcing : les images de vérification sont téléchargées sans erreurs lorsque des BAT sont envoyés (les informations s’affichent dans les journaux des analyses).

Comment résoudre le problème :

1. Envoyez un bon à tirer qui affichera les images.
1. Validez que la configuration des ressources dans la configuration de l&#39;instance est correcte.
1. Vérifiez le dossier ressources publiques ou, si ce n’est dans le dossier ressources publiques, le dossier référencé dans la diffusion.
