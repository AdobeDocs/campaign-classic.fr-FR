---
title: Méthode de migration
seo-title: Méthode de migration
description: Méthode de migration
seo-description: null
page-status-flag: never-activated
uuid: 6b954d5b-cfa3-43c6-ac3d-da9185e9e9d1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migration-overview
discoiquuid: 3ac779a7-1f91-4c1c-a439-10d01697326a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 4437d2ea4e4044245a2b9a5a870267cd1f1c0bc9

---


# Méthode de migration{#migration-method}

## Modernisation de votre environnement {#modernizing-your-environment}

La mise en oeuvre d&#39;une migration peut être l&#39;occasion de moderniser votre environnement (moteurs de base de données, systèmes d&#39;exploitation). Nous vous recommandons vivement d&#39;étudier la possibilité de mettre à niveau vos environnements de production avec des versions plus récentes.

Les versions 32 bits des moteurs de base de données et des systèmes d&#39;exploitation sont encore prises en charge en v7, mais ne le seront plus dans les versions ultérieures d&#39;Adobe Campaign. Nous vous recommandons vivement de mettre à niveau votre plateforme vers une version 64 bits dès que possible.

Le mode &quot;multi timezone&quot; n&#39;était disponible, en v6.02, que pour les moteurs de base de données PostgreSQL. Il est à présent proposé quelle que soit la version de votre moteur de base. Nous vous recommandons fortement de transformer votre base en base &quot;multi timezone&quot;. Pour plus d’informations sur ce sujet, voir la section Fuseaux [](../../migration/using/general-configurations.md#time-zones) horaires.

>[!CAUTION]
>
>Certaines versions de logiciels prises en charge dans les versions 5.11 et 6.02 ne sont plus prises en charge par Adobe Campaign v7.
>
>Pour plus d&#39;informations sur les versions prises en charge par Adobe Campaign, consultez la [matrice de compatibilité](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html).

## Grandes étapes de migration {#key-migration-steps}

The general procedure for migrating to Adobe Campaign v7 is detailed in the [Before starting migration](../../migration/using/before-starting-migration.md) section.

Les étapes de mise en oeuvre de la migration vers Adobe Campaign v7 sont détaillées dans la section [Conditions préalables à la migration vers Adobe Campaign 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md) .

Les configurations requises dépendent de vos configurations existantes et de la version initiale de la plateforme. Ces informations sont décrites dans la section Configurations [](../../migration/using/general-configurations.md) générales.

## Paramétrages spécifiques {#specific-configurations}

Les évolutions apportées à Adobe Campaign v7 peuvent vous amener à devoir adapter certains paramétrages spécifiques développés dans les versions antérieures. Ainsi, il peut être nécessaire de réaliser un audit complet de vos paramétrages avant la migration : contactez-nous pour toute demande d&#39;assistance.

Par exemple, une attention particulière doit être portée aux paramètres spécifiques des applications Web, aux extensions de schéma avec SQLdata ou au clonage de schéma prêt à l&#39;emploi. Pour plus d’informations, reportez-vous à la section [Configuration de votre plateforme](../../migration/using/configuring-your-platform.md) .

De même, afin de répondre au renforcement de la sécurité dans Adobe Campaign, certains mécanismes internes ont été modifiés : les paramétrages correspondants devront être adaptés.
