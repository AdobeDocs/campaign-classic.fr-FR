---
product: campaign
title: Restauration de la version précédente
description: Découvrez comment restaurer la version précédente
audience: migration
content-type: reference
topic-tags: rollback
exl-id: 5120a7c4-3760-48d9-94da-d587d333e8d8
source-git-commit: 8610d29a3df1080f1622a2cb3685c0961fb40092
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 100%

---

# Restauration de la version précédente{#about-rollback}

![](../../assets/v7-only.svg)

Après une migration, en cas de problème, vous devrez peut-être revenir à la version précédente de Campaign.

La procédure de restauration dépend de votre version initiale de Campaign.

## Restauration de Campaign v6.1

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
