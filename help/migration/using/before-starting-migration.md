---
product: campaign
title: Avant de commencer la migration
description: Avant de commencer la migration
audience: migration
content-type: reference
topic-tags: migration-procedure
hide: true
hidefromtoc: true
exl-id: d666bc0b-596a-4908-9364-7df5bb8d68d0
source-git-commit: 80cf56e330731237d5e7b394381b737f30f8b350
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 100%

---

# Conditions préalables requises{#before-starting-migration}

![](../../assets/v7-only.svg)

Cette page répertorie les étapes spécifiques à effectuer avant de démarrer le processus de migration. Vous devez également vous référer à [cette page](about-migration.md) pour plus d’informations.

>[!NOTE]
>
>Dans ce document, les commandes sont données sous forme d’exemples. Ils peuvent varier en fonction de votre configuration.

1. Vérifiez votre version d’Adobe Campaign : avant de procéder à la migration, installez la dernière build de la version actuelle que vous utilisez.
1. Sauvegardez vos données.
1. Vérifiez votre environnement : vous ne pouvez pas modifier votre système de moteur de base de données (SGBD). Par exemple, vous ne pouvez pas passer d’un moteur PostgreSQL à un moteur Oracle. Vous pouvez toutefois passer à la dernière version de votre moteur de base de données. Notez qu’il n&#39;est pas possible de passer d’une base non-Unicode à une base Unicode.

## Etapes de migration {#migration-steps}

La procédure de migration doit être effectuée sur **tous** les serveurs, dans un ordre spécifique.

* Dans le cas d&#39;une **plateforme stand-alone** (monomachine), l&#39;application est migrée dans son ensemble.
* Dans le cas d&#39;une **plateforme standard** (entreprise), les étapes de migration sont les suivantes :

   1. Migrez le serveur marketing.
   1. Migrez le serveur d&#39;envoi (mta).
   1. Migrez les serveurs de redirection et de tracking (Apache / IIS).

* Dans le cas d&#39;une **plateforme Cloud Messaging**, les serveurs d&#39;exécution sont hébergés chez Adobe. Veuillez nous contacter pour coordonner la migration sur les différents serveurs.
* Dans le cas d&#39;une **plateforme Power Booster ou Power Cluster**, les étapes de migration sont les suivantes :

   1. Migrez les serveurs de redirection et de tracking (Apache / IIS).
   1. Migrez les serveurs de Power Booster/Cluster.
   1. Migrez le serveur marketing.

## Mots de passe des opérateurs {#user-passwords}

Dans v7, la connexion de l&#39;opérateur **interne** et **administrateur** doit être sécurisée par un mot de passe. Nous vous recommandons vivement d&#39;affecter des mots de passe à ces comptes et à tous les comptes d&#39;opérateurs **avant la migration**. Si vous n&#39;avez pas spécifié de mot de passe pour la connexion **interne**, vous ne pourrez pas vous connecter. Pour attribuer un mot de passe à la connexion **interne**, saisissez la commande suivante :

```
nlserver config -internalpassword
```

>[!CAUTION]
>
>Le mot de passe **interne** doit être identique pour tous les serveurs de tracking. Pour plus d’informations, consultez les sections [Identifiant interne](../../installation/using/configuring-campaign-server.md#internal-identifier) et [Autorisations](../../platform/using/access-management.md).
