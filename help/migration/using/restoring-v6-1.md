---
title: Restauration de la v6.1
seo-title: Restauration de la v6.1
description: Restauration de la v6.1
seo-description: null
page-status-flag: never-activated
uuid: 3fb71b6f-4d70-4814-a885-4d414a542eca
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: rollback
discoiquuid: e510482c-a56d-4254-90f8-19bd5c545e30
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9482a99c3be164651b3428179388cb0a8a75783f

---


# Restauration de la v6.1{#restoring-v}

Voici la procédure pour restaurer la version v6.1 à partir de la version v7.

1. Récupérez la sauvegarde de la base de données et restaurez-la.
1. Récupérez le dossier Adobe Campaign **v6.back** (**nl6.back** sous Linux), renommez-le **Neolane v6** (**nl6** sous Linux) et restaurez-le à son emplacement d&#39;origine.
1. Reparamétrez IIS en réaffectant les ports d&#39;écoute afin de rétablir l&#39;intégration d&#39;Adobe Campaign v6.1 au niveau du site Web IIS.
1. Arrêtez le service Adobe Campaign v7.
1. Redémarrez IIS.
1. Redémarrez le service Adobe Campaign v6.1.

