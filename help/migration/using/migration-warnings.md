---
product: campaign
title: Avertissements relatifs à la migration
description: Avertissements relatifs à la migration
audience: migration
content-type: reference
topic-tags: migration-overview
exl-id: 46b46fc9-c7c9-4c74-b5f3-7935d5368520
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 100%

---

# Avertissements relatifs à la migration{#migration-warnings}

![](../../assets/v7-only.svg)

* La procédure de migration est réservée à un utilisateur expert. Vous devez être assisté, au minimum, d&#39;un expert en base de données, d&#39;un administrateur système et d&#39;un développeur applicatif Adobe Campaign.
* Avant de démarrer la migration, vérifiez que les systèmes et composants que vous utilisez sont bien compatibles avec la v7. Consultez la [matrice de compatibilité](../../rn/using/compatibility-matrix.md).
* Si vous utilisez le Cloud Messaging (anciennement mid-sourcing), contactez-nous avant d’initier toute procédure de migration.
* Avant toute migration, vous devez **impérativement** effectuer une sauvegarde de vos données.
* La réalisation de l&#39;intégralité du processus de migration peut nécessiter plusieurs jours.
* Adobe Campaign v7 est plus strict en termes de paramétrage que les versions 5.11 et 6.02, cela afin, notamment, d&#39;éviter des problèmes de corruption de données et de préserver leur intégrité en base. Par conséquent, il est possible que certains paramétrages proposés en v5.11 ou en v6.02 ne soient plus fonctionnels tels quels en v7 et requièrent donc une adaptation lors de votre migration. Nous vous invitons à tester de façon systématique, avant la mise en production, tous les paramétrages et notamment les workflows, indispensables à votre utilisation d&#39;Adobe Campaign.

>[!NOTE]
>
>Vous devez également consulter la section [Avant de commencer la migration](../../migration/using/before-starting-migration.md).
