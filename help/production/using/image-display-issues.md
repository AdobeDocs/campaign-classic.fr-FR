---
product: campaign
title: Problèmes liés à l'affichage des images
description: Problèmes liés à l'affichage des images
feature: Monitoring
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 62fa491e-3e83-422b-bcde-2bae2c1b676e
TQID: 'https://experienceleague.adobe.com/aBPQb0Yp8o7goe2CS4h6ydnZV5gjPYINHMxGcc-d140'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: c03a11ff-bdf9-4e5b-b279-f468b4293464
    internal-label: Performance Monitoring
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
    internal-label: Monitoring guidelines
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '134'
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
