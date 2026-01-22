---
product: campaign
title: Problèmes liés à l'affichage des images
description: Problèmes liés à l'affichage des images
feature: Monitoring
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 62fa491e-3e83-422b-bcde-2bae2c1b676e
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: ht
source-wordcount: '133'
ht-degree: 100%

---

# Problèmes liés à l&#39;affichage des images{#image-display-issues}



Si vous rencontrez des problèmes d&#39;affichage des images dans un message envoyé, les raisons peuvent être liées à un emplacement incorrect :

* Il se peut que les emplacements ne correspondent pas ou que les images n’aient pas été correctement transmises à un serveur de tracking en double : vérifiez votre configuration.
* Les images peuvent ne pas se trouver dans le dossier des ressources publiques sur l&#39;instance marketing : téléchargez les images dans votre dossier des ressources pour résoudre le problème.
* Si vous utilisez une architecture en midsourcing : vérifiez que les images sont téléchargées sans erreur lorsque les bons à tirer sont envoyés (les informations sont affichées dans les logs d&#39;analyse).

Comment résoudre le problème :

1. Envoyez un bon à tirer qui affichera les images.
1. Validez que la configuration des ressources dans la configuration de l&#39;instance est correcte.
1. Vérifiez le dossier des ressources publiques ou, si les images ne figurent pas dans le dossier des ressources publiques, le dossier référencé dans la diffusion.
