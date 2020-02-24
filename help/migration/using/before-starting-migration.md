---
title: Avant de commencer la migration
seo-title: Avant de commencer la migration
description: Avant de commencer la migration
seo-description: null
page-status-flag: never-activated
uuid: b9325510-2fa5-4be4-9cf0-f37232bbbd8c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migration-procedure
discoiquuid: d8877378-fb43-4f32-91c6-60f2f788f916
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9f7cf3d530f141a661df5fcc8cbcf0bb4c8d3e89

---


# Avant de commencer la migration{#before-starting-migration}

>[!NOTE]
>
>Dans ce document, les commandes liées à la base de données sont données à titre d&#39;exemple. Celles-ci peuvent varier en fonction de votre configuration. Contactez votre administrateur de base de données.

## Avertissements {#warnings}

### Version installée {#installed-version}

Avant la migration, vous devez installer le dernier build correspondant à la version que vous utilisez.

Vérifiez la version de votre serveur via le menu **[!UICONTROL Aide > A propos]** de la console cliente ou à l&#39;aide de la commande **nlserver pdump**.

### Sauvegarde des données {#data-backup}

Avant toute migration, vous devez **impérativement** effectuer une sauvegarde de vos données.

### Environnement {#environment}

* Il n&#39;est pas possible de changer de type de moteur de base de données (SGBD). Par exemple, il n&#39;est pas possible de passer d&#39;un moteur PostgreSQL à un moteur Oracle. Il est cependant possible de passer d&#39;un moteur Oracle 8 à un moteur Oracle 10.
* Il n&#39;est pas possible de passer d&#39;une base non-Unicode à une base Unicode.

### Recommandations {#recommendation}

La procédure de migration étant hautement sensible, nous vous recommandons vivement de lire l&#39;intégralité de ce document avant d&#39;entreprendre son exécution.

## Etapes de migration {#migration-steps}

La procédure de migration doit être effectuée sur **tous** les serveurs, dans un ordre spécifique.

* Dans le cas d&#39;une **plateforme stand-alone** (monomachine), l&#39;application est migrée dans son ensemble.
* Dans le cas d&#39;une **plateforme standard** (entreprise), les étapes de migration sont les suivantes :

   1. Migrez le serveur marketing.
   1. Migrez le serveur d&#39;envoi (mta).
   1. Migrez les serveurs de redirection et de tracking (Apache / IIS).

* Dans le cas d&#39;une **plateforme Cloud Messaging**, les serveurs d&#39;exécution sont hébergés chez Adobe. Veuillez nous contacter pour coordonner la migration sur les différents serveurs.
* Dans le cas d&#39;une **plateforme Power Booster ou Power Cluster**, les étapes de migration sont les suivantes :

   1. Migrez les serveurs de redirection et de tracking (Apache / IIS).
   1. Migrez les serveurs de Power Booster/Cluster.
   1. Migrez le serveur marketing.

>[!NOTE]
>
>La communication entre un serveur de marketing v6.02 et un serveur de Cloud Messaging ou Power Booster/Cluster v7 est possible. Toutefois, si vous décidez de conserver votre serveur marketing en v6.02, celui-ci doit être mis à jour avec le build v6.02 le plus récent avant la migration du serveur de Cloud Messaging ou Power Booster/Cluster.

## Mots de passe des opérateurs {#user-passwords}

Dans v7, la connexion de l’opérateur **interne** et **administrateur** doit être sécurisée par un mot de passe. Nous vous recommandons vivement d’affecter des mots de passe à ces comptes et à tous les comptes d’opérateurs **avant la migration**. Si vous n&#39;avez pas spécifié de mot de passe pour **interne**, vous ne pourrez pas vous connecter. Pour attribuer un mot de passe à **interne**, saisissez la commande suivante :

```
nlserver config -internalpassword
```

>[!IMPORTANT]
>
>Le mot de passe **interne** doit être identique sur tous les serveurs de tracking. Pour plus d&#39;informations, consultez les sections [Identifiant interne](../../installation/using/campaign-server-configuration.md#internal-identifier) et [A propos des permissions](../../platform/using/access-management.md#about-permissions).

