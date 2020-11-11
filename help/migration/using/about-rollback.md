---
title: Restauration de la version précédente
description: Découvrez comment restaurer la version précédente
page-status-flag: never-activated
uuid: 9d404ca5-e38c-48ba-b5e0-8e70a40482c2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: rollback
discoiquuid: 0e17abea-5e86-43b5-8bca-ee39d9b24c90
translation-type: tm+mt
source-git-commit: 7a3cdf40da579fc3c4c7fc26b10c160543cc45d7
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 100%

---


# Restauration de la version précédente{#about-rollback}

Après une migration, en cas de problème, vous devrez peut-être revenir à la version précédente de Campaign.

La procédure de restauration dépend de votre version initiale de Campaign.

## Restauration de la v6.1

Voici la procédure pour restaurer la version v6.1 à partir de la version v7.

1. Récupérez la sauvegarde de la base de données et restaurez-la.
1. Récupérez le dossier Adobe Campaign **v6.back** (**nl6.back** sous Linux), renommez-le **Neolane v6** (**nl6** sous Linux) et restaurez-le à son emplacement d&#39;origine.
1. Reparamétrez IIS en réaffectant les ports d&#39;écoute afin de rétablir l&#39;intégration d&#39;Adobe Campaign v6.1 au niveau du site Web IIS.
1. Arrêtez le service Adobe Campaign v7.
1. Redémarrez IIS.
1. Redémarrez le service Adobe Campaign v6.1.

## Restauration de Campaign v6.02

Voici la procédure pour restaurer la version v6.02 à partir de la version v7.

1. Récupérez la sauvegarde de la base de données et restaurez-la.
1. Récupérez le dossier **Neolane v6.back** (**nl6.back** sous Linux), renommez-le **Neolane v6** (**nl6** sous Linux) et restaurez-le à son emplacement d&#39;origine.
1. Reparamétrez IIS en réaffectant les ports d&#39;écoute afin de rétablir l&#39;intégration d&#39;Adobe Campaign v6.02 au niveau du site Web IIS.
1. Arrêtez le service Adobe Campaign v6.1.
1. Redémarrez IIS.
1. Redémarrez le service Adobe Campaign v6.02.

## Restauration de Campaign v5.11

Voici la procédure pour restaurer la version v5.11 à partir de la version v7.

1. Récupérez la sauvegarde de la base de données et restaurez-la.
1. Récupérez le dossier **Neolane v5.back** (**nl5.back** sous Linux), renommez-le **Neolane v5** (**nl5** sous Linux) et restaurez-le à son emplacement d&#39;origine.
1. Reparamétrez IIS en réaffectant les ports d&#39;écoute afin de rétablir l&#39;intégration de Neolane v5 au niveau du site Web IIS.
1. Arrêtez le service Adobe Campaign v7.
1. Redémarrez IIS.
1. Redémarrez le service Adobe Campaign v5.
