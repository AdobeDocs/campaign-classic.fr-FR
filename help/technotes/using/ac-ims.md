---
title: Migrer vers Adobe Identity Management System (IMS)
description: Découvrez comment migrer votre processus d’authentification vers Adobe Identity Management System (IMS).
exl-id: 84853dbe-8b6f-4875-b29a-c1b755423a3c
source-git-commit: 8eadea9f9cc0a44522726024bfbc825e3b4cad98
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 100%

---

# Migrer vers Adobe Identity Management System (IMS) {#migrate-to-ims}

Dans le cadre de ses efforts pour renforcer la sécurité et le processus d’authentification, Adobe Campaign recommande vivement de migrer le mode d’authentification de l’utilisateur ou de l’utilisatrice final, de l’authentification native par nom d’utilisateur ou d’utilisatrice/mot de passe vers [Adobe Identity Management System (IMS)](https://helpx.adobe.com/fr/enterprise/using/identity.html){target="_blank"}.

De plus, l’application cliente Adobe Campaign appelle désormais les API Campaign directement à l’aide du jeton de compte technique IMS. Vous devez migrer vos opérateurs et opératrices techniques vers Adobe Developer Console.

>[!CAUTION]
>
>Cette modification s’applique déjà à Campaign Classic v7 et sera **obligatoire** pour migrer vers Campaign v8. L’authentification native par nom d’utilisateur ou d’utilisatrice/mot de passe n’est pas autorisée dans Campaign v8. **Adobe recommande d’effectuer cette migration dans Campaign v7.3.5 afin de pouvoir migrer en douceur vers Campaign v8.**
>

## Étapes de migration {#ims-steps}

La migration vers [Adobe Identity Management System (IMS)](https://helpx.adobe.com/fr/enterprise/using/identity.html){target="_blank"} est un impératif de sécurité visant à sécuriser et normaliser vos environnements, car la plupart des autres solutions et applications Adobe Experience Cloud sont déjà sur IMS.

Adobe vous aide dans cet effort de migration. Vous trouverez le contexte détaillé et les instructions étape par étape dans les articles ci-dessous.

* La migration pour l’authentification des utilisateurs et des utilisatrices finaux est détaillée sur [cette page](migrate-users-to-ims.md).
* La migration pour l’authentification des opérateurs et des opératrices techniques est détaillée sur [cette page](ims-migration.md).
* À compter de Campaign v7.4.1, activez les restrictions de l’interface d’utilisation et de l’API pour supprimer les options et les fonctionnalités spécifiques à l’authentification native, comme décrit sur [cette page](impact-ims-migration.md).


## Versions compatibles avec la migration IMS {#ims-versions}

La mise à niveau de votre environnement vers l’une des versions de produit suivantes est une condition préalable à cette migration :

* Campaign v7.4.1 (recommandé)
* Campaign v7.3.5
* Campaign v7.3.3.IMS
* Campaign v7.3.2.IMS

Ces versions de Campaign sont présentées dans la section [Notes de mise à jour](../../rn/using/latest-release.md).

## Forum aux questions {#ims-migration-faq}

### Quand puis-je démarrer la migration ? {#ims-migration-start}

Il est recommandé de mettre à niveau votre environnement vers Campaign Classic v7.4.1 ou une [version compatible avec la migration IMS](#ims-versions) avant d’effectuer la migration vers [Adobe Identity Management System (IMS)](https://helpx.adobe.com/fr/enterprise/using/identity.html){target="_blank"}.

Vous pouvez démarrer la migration IMS sur votre environnement d’évaluation une fois qu’il a été mis à niveau vers la dernière version, puis planifier en conséquence l’environnement de production.

### Que se passe-t-il après la mise à niveau de version vers Campaign Classic v7.4.1 ? {#ims-migration-after-upgrade}

Une fois les environnements mis à niveau vers Campaign Classic v7.4.1 (ou une [version compatible avec la migration IMS](#ims-versions)), vous pouvez lancer la transition vers [Adobe Identity Management System (IMS)](https://helpx.adobe.com/fr/enterprise/using/identity.html){target="_blank"}.

### Quand la migration est-elle terminée ? {#ims-migration-end}

Une fois la migration des utilisateurs et des utilisatrices finaux et la migration des opérateurs et des opératrices techniques vers Adobe Identity Management System (IMS) terminée, vous devez mettre à jour votre environnement pour supprimer les options spécifiques à l’authentification native et qui ne sont plus applicables à l’authentification IMS. Cette mise à jour est uniquement disponible à partir de Campaign v7.4.1. [En savoir plus](impact-ims-migration.md)



## Liens utiles {#ims-useful-links}

* [Migration des utilisateurs et des utilisatrices finaux vers IMS](migrate-users-to-ims.md)
* [Migration des opérateurs et des opératrices techniques vers Adobe Developer Console](ims-migration.md)
* [Dernières notes de mise à jour d’Adobe Campaign Classic v7](../../rn/using/latest-release.md)
* [Présentation d’Adobe Identity Management System (IMS)](https://helpx.adobe.com/fr/enterprise/using/identity.html){target="_blank"}
