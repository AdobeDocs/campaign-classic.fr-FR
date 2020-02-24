---
title: Objectif
seo-title: Objectif
description: Objectif
seo-description: null
page-status-flag: never-activated
uuid: 4452d839-318a-49d8-8abb-4ba04c803e9f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: use-case
discoiquuid: 7b8ab9d6-e47e-46d8-99df-da793486654c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Objectif{#purpose}

L&#39;objectif de ce cas pratique est d&#39;ajouter des pièces jointes d&#39;emails à la volée aux envois sortants.

Dans ce scénario, nous allons voir comment envoyer des emails transactionnels avec des pièces jointes individuelles/personnalisées. Les pièces jointes ne seront pas préchargées sur le serveur de messagerie transactionnelle, mais générées à la volée.

Lorsque vous capturez des interactions ou des détails sur un client, vous devrez peut-être lui renvoyer ces informations à la fin du processus, par exemple dans un fichier PDF joint à un email. Voici les étapes générales de ce scénario.

1. Le client accède au site web et trouve le produit qu&#39;il souhaite acheter.
1. Il sélectionne le produit et personnalise certaines options.
1. Il termine la transaction.
1. Un email est envoyé au client pour confirmer la transaction. Nous ne souhaitons pas envoyer de PII (informations personnellement identifiables) dans l&#39;email. Nous générons donc un fichier PDF sécurisé et le joignons à l&#39;email.
1. Le client reçoit l&#39;email et la pièce jointe contenant toutes les données nécessaires.

Dans ce scénario, les pièces jointes ne sont pas précréées, mais ajoutées à la volée aux emails sortants. Vous pouvez ainsi personnaliser le contenu de la pièce jointe. De même, si la pièce jointe est associée à une transaction (comme dans l&#39;exemple ci-dessus), vous aurez peut-être besoin qu&#39;elle contienne des données dynamiques générées lors du processus client. Joindre des fichiers PDF de cette manière renforce également la sécurité, car vous pouvez les chiffrer et les envoyer via HTTPS.
