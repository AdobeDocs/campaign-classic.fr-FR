---
title: Restauration de la v6.02
seo-title: Restauration de la v6.02
description: Restauration de la v6.02
seo-description: null
page-status-flag: never-activated
uuid: df21209b-4825-42fa-a303-f383f872abb5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: rollback
discoiquuid: 4f65ba19-e9f0-4425-b640-f27c61394859
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9482a99c3be164651b3428179388cb0a8a75783f

---


# Restauration de la v6.02{#restoring-v}

Voici la procédure pour restaurer la version v6.02 à partir de la version v7.

1. Récupérez la sauvegarde de la base de données et restaurez-la.
1. Récupérez le dossier **Neolane v6.back** (**nl6.back** sous Linux), renommez-le **Neolane v6** (**nl6** sous Linux) et restaurez-le à son emplacement d&#39;origine.
1. Reparamétrez IIS en réaffectant les ports d&#39;écoute afin de rétablir l&#39;intégration d&#39;Adobe Campaign v6.02 au niveau du site Web IIS.
1. Arrêtez le service Adobe Campaign v6.1.
1. Redémarrez IIS.
1. Redémarrez le service Adobe Campaign v6.02.

