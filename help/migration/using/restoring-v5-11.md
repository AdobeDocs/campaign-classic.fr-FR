---
title: Restauration de la v5.11
seo-title: Restauration de la v5.11
description: Restauration de la v5.11
seo-description: null
page-status-flag: never-activated
uuid: 4480c97c-5845-483c-a17b-644f05783b4e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: rollback
discoiquuid: ef778333-8e50-402b-9a69-78ac94497c67
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9482a99c3be164651b3428179388cb0a8a75783f

---


# Restauration de la v5.11{#restoring-v}

Voici la procédure pour restaurer la version v5.11 à partir de la version v7.

1. Récupérez la sauvegarde de la base de données et restaurez-la.
1. Récupérez le dossier **Neolane v5.back** (**nl5.back** sous Linux), renommez-le **Neolane v5** (**nl5** sous Linux) et restaurez-le à son emplacement d&#39;origine.
1. Reparamétrez IIS en réaffectant les ports d&#39;écoute afin de rétablir l&#39;intégration de Neolane v5 au niveau du site Web IIS.
1. Arrêtez le service Adobe Campaign v7.
1. Redémarrez IIS.
1. Redémarrez le service Adobe Campaign v5.

