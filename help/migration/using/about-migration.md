---
product: campaign
title: Migration vers Campaign Classic
description: Découvrez comment effectuer une migration vers Campaign Classic à partir d'une version précédente de Campaign
feature: Upgrade
audience: migration
content-type: reference
topic-tags: migration-overview
hide: true
exl-id: 3050238d-6f77-4ffa-9aef-677ab8009388
TQID: https://experienceleague.adobe.com/Cpa5--gsUgdw1FtmYuGJaKDEOVm2BOuG-Ok5bvfEPyA
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 460
ht-degree: 76%

---

# Prise en main de la migration{#about-migration}



Ce document présente les prérequis pour effectuer une migration, les étapes de migration vers Adobe Campaign Classic v7. Les étapes et les paramètres facultatifs dépendent de votre configuration.

Le processus de migration doit être mené avec précaution, ses impacts doivent être pleinement pris en compte au préalable et la procédure doit être menée avec rigueur. Elle ne doit être effectuée que par un utilisateur expert. Nous vous recommandons vivement de contacter le [service d&#39;assistance clientèle d&#39;Adobe](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) avant de commencer toute procédure de migration.

La migration doit être testée à l’avance sur l’environnement de test/d’évaluation afin de s’assurer qu’elle s’effectue correctement et sans erreurs. La migration de l’environnement de production doit être effectuée uniquement lorsque l’environnement de test migré est entièrement validé.

>[!NOTE]
>
>Les nouvelles fonctionnalités et améliorations apportées à Adobe Campaign v7 sont présentées en détail dans les [Notes de mise à jour](../../rn/using/latest-release.md).


## Conditions préalables requises

* Le processus de migration doit être uniquement effectué par des utilisateurs experts. Vous devez être assisté par au moins un expert en base de données, un administrateur système et un développeur d’applications d’Adobe Campaign.
* Avant de commencer la migration, vérifiez que les systèmes et composants système que vous utilisez sont compatibles avec la v7. [En savoir plus](../../rn/using/compatibility-matrix.md).
* Si vous utilisez Adobe Campaign Cloud Messaging (déploiement midsourcing), contactez l’assistance clientèle d’Adobe avant de commencer.
* Avant toute migration, vous devez **impérativement** effectuer une sauvegarde de vos données.
* La réalisation de l&#39;intégralité du processus de migration peut nécessiter plusieurs jours.
* Adobe Campaign v7 est une version plus sécurisée que les versions précédentes : cela a un impact sur les directives de configuration afin d’éviter des problèmes tels que la corruption des données et de préserver l’intégrité des données dans la base de données. En tant que client, vous êtes responsable du test de toutes les configurations, y compris les workflows.

D’autres prérequis sont disponibles dans [cette page](../../migration/using/before-starting-migration.md).


## Environnement modernisé {#modernizing-your-environment}

La migration peut être l’occasion de mettre à jour votre environnement (moteurs de base de données, systèmes d’exploitation). Adobe Campaign recommande vivement de mettre à niveau vos environnements de production vers les versions les plus récentes.

>[!CAUTION]
>
>Pour plus d’informations sur les versions prises en charge par Adobe Campaign v7, consultez la [matrice de compatibilité](../../rn/using/compatibility-matrix.md).

## Grandes étapes de migration {#key-migration-steps}

La procédure générale de migration vers Adobe Campaign v7 est présentée en détail dans [cette page](../../migration/using/before-starting-migration.md)


## Paramétrages spécifiques {#specific-configurations}

Les changements apportés par Adobe Campaign v7 peuvent également signifier que vous devez adapter certaines configurations spécifiques développées dans les versions antérieures. Par conséquent, il peut être nécessaire d’effectuer un audit de toutes vos configurations avant la migration : pour toute assistance, contactez Adobe Campaign.

Par exemple, les paramétrages spécifiques des applications web, des extensions de schémas avec SQLdata ou du clonage de schémas d’usine nécessitent une attention particulière. Pour plus d’informations, consultez [cette page](../../migration/using/configuring-your-platform.md).

De même, afin de répondre au renforcement de la sécurité dans Adobe Campaign, certains mécanismes internes ont été modifiés : les paramétrages doivent être adaptés en conséquence.

