---
product: campaign
title: Méthode de migration
description: Méthode de migration
audience: migration
content-type: reference
topic-tags: migration-overview
exl-id: dd4d068b-f414-448f-8d9a-eedf44e7b6e6
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 100%

---

# Méthode de migration{#migration-method}

![](../../assets/v7-only.svg)

## Modernisation de votre environnement {#modernizing-your-environment}

La mise en oeuvre d&#39;une migration peut être l&#39;occasion de moderniser votre environnement (moteurs de base de données, systèmes d&#39;exploitation). Nous vous recommandons vivement d&#39;étudier la possibilité de mettre à niveau vos environnements de production avec des versions plus récentes.

Les versions 32 bits des moteurs de base de données et des systèmes d&#39;exploitation sont encore prises en charge en v7, mais ne le seront plus dans les versions ultérieures d&#39;Adobe Campaign. Nous vous recommandons vivement de mettre à niveau votre plateforme vers une version 64 bits dès que possible.

Le mode &quot;multi timezone&quot; n&#39;était disponible, en v6.02, que pour les moteurs de base de données PostgreSQL. Il est à présent proposé quelle que soit la version de votre moteur de base. Nous vous recommandons fortement de transformer votre base en base &quot;multi timezone&quot;. Voir à ce sujet la section [Fuseaux horaires](../../migration/using/general-configurations.md#time-zones).

>[!IMPORTANT]
>
>Certaines versions de logiciels prises en charge dans les versions 5.11 et 6.02 ne sont plus prises en charge par Adobe Campaign v7.
>
>Pour plus d&#39;informations sur les versions prises en charge par Adobe Campaign, consultez la [matrice de compatibilité](../../rn/using/compatibility-matrix.md).

## Grandes étapes de migration {#key-migration-steps}

La procédure générale de migration vers Adobe Campaign v7 est présentée dans la section [Avant de commencer la migration](../../migration/using/before-starting-migration.md).

Les étapes de mise en œuvre de la migration vers Adobe Campaign v7 sont présentées dans la section [Prérequis pour la migration vers Adobe Campaign 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md).

Les paramétrages requis dépendent de ceux qui existent et de la version initiale de la plateforme. Ces informations sont fournies dans la section [Paramétrages généraux](../../migration/using/general-configurations.md).

## Paramétrages spécifiques {#specific-configurations}

Les évolutions apportées à Adobe Campaign v7 peuvent vous amener à devoir adapter certains paramétrages spécifiques développés dans les versions antérieures. Ainsi, il peut être nécessaire de réaliser un audit complet de vos paramétrages avant la migration : contactez-nous pour toute demande d&#39;assistance.

Par exemple, les paramétrages spécifiques des applications web, des extensions de schémas avec SQLdata ou du clonage de schémas d’usine nécessitent une attention particulière. Voir à ce sujet la section [Configurer votre plateforme](../../migration/using/configuring-your-platform.md).

De même, afin de répondre au renforcement de la sécurité dans Adobe Campaign, certains mécanismes internes ont été modifiés : les paramétrages correspondants devront être adaptés.
