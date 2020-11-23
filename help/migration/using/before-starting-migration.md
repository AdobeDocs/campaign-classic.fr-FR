---
solution: Campaign Classic
product: campaign
title: Avant de commencer la migration
description: Avant de commencer la migration
audience: migration
content-type: reference
topic-tags: migration-procedure
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 88%

---


# Avant de commencer la migration{#before-starting-migration}

>[!NOTE]
>
>Dans ce document, les commandes liées à la base de données sont données à titre d&#39;exemple. Celles-ci peuvent varier en fonction de votre configuration. Contactez votre administrateur de base de données.

## Avertissements {#warnings}

* Le processus de migration ne doit être effectué que par des utilisateurs experts. Vous devez être assisté par au moins un expert en base de données, un administrateur système et un développeur d’applications d’Adobe Campaign.
* Avant de démarrer la migration, vérifiez que les systèmes et composants que vous utilisez sont bien compatibles avec la v7. Consultez la [matrice de compatibilité](../../rn/using/compatibility-matrix.md).
* Si vous utilisez Adobe Campaign Cloud Messaging (midsourcing), contactez l’Adobe avant de commencer la procédure de migration complète.
* Avant toute migration, vous devez **impérativement** effectuer une sauvegarde de vos données.
* La réalisation de l&#39;intégralité du processus de migration peut nécessiter plusieurs jours.
* Adobe Campaign v7 est plus strict en termes de paramétrage que les versions 5.11 et 6.02, cela afin, notamment, d&#39;éviter des problèmes de corruption de données et de préserver leur intégrité en base. Par conséquent, il est possible que certains paramétrages proposés en v5.11 ou en v6.02 ne soient plus fonctionnels tels quels en v7 et requièrent donc une adaptation lors de votre migration. Nous vous invitons à tester de façon systématique, avant la mise en production, tous les paramétrages et notamment les workflows, indispensables à votre utilisation d&#39;Adobe Campaign.

### Version installée {#installed-version}

Avant la migration, vous devez installer le dernier build correspondant à la version que vous utilisez.

Vérifiez la version de votre serveur via le menu **[!UICONTROL Aide > A propos]** de la console cliente ou à l&#39;aide de la commande **nlserver pdump**.

### Sauvegarde des données {#data-backup}

Avant toute migration, vous devez **impérativement** effectuer une sauvegarde de vos données.

### Environnement {#environment}

* Il n&#39;est pas possible de changer de type de moteur de base de données (SGBD). Par exemple, il n&#39;est pas possible de passer d&#39;un moteur PostgreSQL à un moteur Oracle. Il est cependant possible de passer d&#39;un moteur Oracle 8 à un moteur Oracle 10.
* Il n&#39;est pas possible de passer d&#39;une base non-Unicode à une base Unicode.

### Recommandations {#recommendation}

Comme la procédure de migration est délicate, nous recommandons vivement de lire ce document attentivement avant de commencer la procédure.

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

## Mots de passe des opérateurs {#user-passwords}

Dans v7, la connexion de l’opérateur **interne** et **administrateur** doit être sécurisée par un mot de passe. Nous vous recommandons vivement d’affecter des mots de passe à ces comptes et à tous les comptes d’opérateurs **avant la migration**. Si vous n&#39;avez pas spécifié de mot de passe pour la connexion **interne**, vous ne pourrez pas vous connecter. Pour attribuer un mot de passe à la connexion **interne**, saisissez la commande suivante :

```
nlserver config -internalpassword
```

>[!IMPORTANT]
>
>Le mot de passe **interne** doit être identique sur tous les serveurs de tracking. Pour plus d&#39;informations, consultez les sections [Identifiant interne](../../installation/using/campaign-server-configuration.md#internal-identifier) et [A propos des permissions](../../platform/using/access-management.md#about-permissions).

