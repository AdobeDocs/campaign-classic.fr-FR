---
title: Problèmes liés à l'affichage des images
seo-title: Problèmes liés à l'affichage des images
description: Problèmes liés à l'affichage des images
seo-description: null
page-status-flag: never-activated
uuid: 8fc51459-ee46-4c05-8011-f0651e6b451b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: dfccfe8c-b826-4648-9a0b-23d7e6a4808a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Problèmes liés à l&#39;affichage des images{#image-display-issues}

Si vous rencontrez des problèmes d&#39;affichage des images dans un message envoyé, les raisons peuvent être liées à un emplacement incorrect :

* Les emplacements peuvent ne pas correspondre ou les images ne pas avoir été correctement transmises au serveur de tracking : vérifiez votre configuration.
* Les images peuvent ne pas se trouver dans le dossier des ressources publiques sur l&#39;instance marketing : téléchargez les images dans votre dossier des ressources pour résoudre le problème.
* Si vous utilisez une architecture en mid-sourcing : vérifiez que les images sont téléchargées sans erreur lorsque les bons à tirer sont envoyés (les informations sont affichées dans les logs d&#39;analyse).

Comment résoudre le problème :

1. Envoyez un bon à tirer qui affichera les images.
1. Validez que la configuration des ressources dans la configuration de l&#39;instance est correcte.
1. Vérifiez le dossier des ressources publiques ou, si les images ne figurent pas dans ce dossier, le dossier référencé dans la diffusion.

