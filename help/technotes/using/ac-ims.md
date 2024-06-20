---
title: Migration vers Adobe Identity Management System (IMS)
description: Découvrez comment migrer votre processus d’authentification vers Adobe Identity Management System (IMS)
source-git-commit: 106f0409f452595209f0e2aa2fa187a2e04338a9
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 27%

---

# Migration vers Adobe Identity Management System (IMS) {#migrate-to-ims}

Dans le cadre de l’effort visant à renforcer la sécurité et le processus d’authentification, Adobe Campaign recommande vivement de migrer le mode d’authentification de l’utilisateur final de l’authentification native login/password à [Adobe Identity Management System (IMS)](https://helpx.adobe.com/fr/enterprise/using/identity.html){target="_blank"}.

En outre, l’application cliente Adobe Campaign appelle désormais les API Campaign directement à l’aide du jeton de compte technique IMS. Vous devez migrer vos opérateurs techniques vers la console Adobe Developer.

>[!CAUTION]
>
>Cette modification est déjà applicable dans Campaign Classic v7 et sera **mandatory** pour passer à Campaign v8. L’authentification par utilisateur/mot de passe natif n’est pas autorisée dans Campaign v8. **Adobe recommande d&#39;effectuer cette migration à partir de Campaign v7.3.5 afin de pouvoir migrer en douceur vers Campaign v8.**
>

## Etapes de migration {#ims-steps}

La migration vers [Adobe Identity Management System (IMS)](https://helpx.adobe.com/fr/enterprise/using/identity.html){target="_blank"} est un impératif de sécurité visant à sécuriser et normaliser vos environnements, car la plupart des autres solutions et applications Adobe Experience Cloud sont déjà sur IMS.

Adobe vous aide dans cet effort de migration. Vous trouverez un contexte détaillé et des instructions détaillées étape par étape dans les articles ci-dessous :

* La migration pour l’authentification des utilisateurs finaux est présentée dans la section [cette page](migrate-users-to-ims.md).
* La migration pour l&#39;authentification des opérateurs techniques est présentée dans la section [cette page](ims-migration.md).
* À compter de Campaign v7.4.1, activez l’interface utilisateur et les restrictions de l’API pour supprimer les options et fonctionnalités spécifiques à l’authentification native, comme décrit dans la section [cette page](impact-ims-migration.md).


## Versions compatibles avec la migration IMS {#ims-versions}

La mise à niveau de votre environnement vers l’une des versions de produit suivantes est une condition préalable à cette migration :

* Campaign v7.4.1 (recommandé)
* Campaign v7.3.5
* Campaign v7.3.3.IMS
* Campaign v7.3.2.IMS

Ces versions de Campaign sont présentées dans la section [Notes de mise à jour](../../rn/using/latest-release.md).

## Forum aux questions {#ims-migration-faq}

### Quand puis-je démarrer la migration ? {#ims-migration-start}

Une recommandation pour la migration vers [Adobe Identity Management System (IMS)](https://helpx.adobe.com/fr/enterprise/using/identity.html){target="_blank"} est de mettre à niveau votre environnement vers Campaign Classic v7.4.1 (ou une [Version compatible avec la migration IMS](#ims-versions)).

Vous pouvez démarrer la migration IMS sur votre environnement d’évaluation une fois qu’il a été mis à niveau vers la dernière version, puis planifier en conséquence l’environnement de production.

### Que se passe-t-il après l&#39;upgrade de build vers Campaign Classic v7.4.1 ? {#ims-migration-after-upgrade}

Une fois les environnements mis à niveau vers Campaign Classic v7.4.1 (ou une [Version compatible avec la migration IMS](#ims-versions)), vous pouvez lancer votre transition vers [Adobe Identity Management System (IMS)](https://helpx.adobe.com/fr/enterprise/using/identity.html){target="_blank"}.

### Quand la migration est-elle terminée ? {#ims-migration-end}

Une fois la migration des utilisateurs finaux et la migration des opérateurs techniques vers Adobe Identity Management System (IMS) terminée, vous devez mettre à jour votre environnement pour supprimer les options spécifiques à l’authentification native et qui ne sont plus applicables avec l’authentification IMS. Cette mise à jour est uniquement disponible à partir de Campaign v7.4.1. [En savoir plus](impact-ims-migration.md)



## Liens utiles {#ims-useful-links}

* [Migration des utilisateurs finaux vers IMS](migrate-users-to-ims.md)
* [Migration des opérateurs techniques vers la console Adobe Developer](ims-migration.md)
* [Notes de mise à jour les plus récentes de Adobe Campaign Classic v7](../../rn/using/latest-release.md)
* [Présentation d’Adobe Identity Management System (IMS)](https://helpx.adobe.com/fr/enterprise/using/identity.html){target="_blank"}
