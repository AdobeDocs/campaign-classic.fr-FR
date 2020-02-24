---
title: Paramétrages spécifiques v6.02
seo-title: Paramétrages spécifiques v6.02
description: Paramétrages spécifiques v6.02
seo-description: null
page-status-flag: never-activated
uuid: ea072af3-fdc1-4828-ad13-d4327de1eaf8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: configuration
discoiquuid: 87a6cbda-54a6-4dae-8224-e06dc217f4fc
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9f7cf3d530f141a661df5fcc8cbcf0bb4c8d3e89

---


# Paramétrages spécifiques v6.02{#specific-configurations-in-v6-02}

The following section details the additional configuration required when migrating from v6.02. You should also configure the settings detailed in the [General configurations](../../migration/using/general-configurations.md) section.

## Des applications web {#web-applications}

Si vous migrez depuis une v6.02, des logs d&#39;erreur peuvent apparaître concernant des applications web de type vues d&#39;ensemble (overview). Exemples de messages d&#39;erreur :

```
[PU-0006] Entity of type : 'xtk:entityBackupNew' and Id 'nms:webApp|taskOverview', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'xtk:formDictionary' and Id 'nms:webApp|lastTasks', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'nms:webApp' and Id 'taskOverview', expression '[SQLDATA[' was found : '...@owner-id] IN ([SQLDATA[select iGroupid...'. (iRc=-1)
```

Ces applications web utilisaient du SQLData et ne sont plus compatibles avec la v7, en raison du renforcement de la sécurité. Ces erreurs entraineront un échec de migration.

Si vous n&#39;utilisiez pas ces applications web, exécutez le script de nettoyage suivant et relancez le postupgrade :

```
Nlserver javascript -instance:[instance_name] -file [installation_path]/datakit/xtk/fra/js/removeOldWebApp.js
```

If you have modified these web applications and would like to continue using them in v7, you must activate the **allowSQLInjection** option in your different security zones and re-start the postupgrade. Consultez la section [SQLData](../../migration/using/general-configurations.md#sqldata) pour en savoir plus.

## Convivialité : Page d’accueil et navigation {#user-friendliness--home-page-and-navigation}

>[!IMPORTANT]
>
>If you would like to continue using v6.02 overview-type web applications, you must activate the **allowSQLInjection** option in your different security zones before the postupgrade. Reportez-vous aux applications [](#web-applications)Web.

Après une migration depuis la version v6.02, la page d&#39;accueil d&#39;Adobe Campaign v6.02 n&#39;est plus affichée, mais reste accessible et compatible avec Adobe Campaign v7.

Pour continuer à utiliser la page d&#39;accueil v6.02, vous devez installer un package de &quot;compatibilité&quot; après la migration.

Pour cela, importez le package de compatibilité :

Click **[!UICONTROL Tools > Advanced > Import package]** and choose the **campaignMigration.xml** package in the **`\nl\datakit\nms\[Your language]\package\optional`**.

Pour permettre l&#39;accès aux interfaces de type Applications web v6.02, l&#39;option **sessionTokenOnly** des paramètres du serveur doit être activée, dans le fichier **serverConf.xml** :

```
sessionTokenOnly="true"
```

Cette option altère les niveaux de sécurité pour assurer la compatibilité des interfaces.

Une fois le package installé, la page d&#39;accueil d&#39;Adobe Campaign v7 est remplacée par votre ancienne page d&#39;accueil v6.02, complétée des paramètres généraux de la v7 (bandeau bleu de navigation).

![](assets/dashboards.png)

Tous les liens de cette page d’accueil pointent vers les écrans v7, à l’exception des listes (liste **[!UICONTROL des]** opérations, suivi des **[!UICONTROL remises dans les opérations]**, etc.). lien vers la présentation v6.02 (applications Web).

![](assets/dashboards2.png)

Si vous souhaitez ajouter une autre vue d&#39;ensemble paramétrée en v6.02, vous devez l&#39;ajouter sur la page d&#39;accueil à partir des tableaux de bord (**[!UICONTROL Administration > Gestion des accès > Tableaux de bord]**).

>[!NOTE]
>
>N&#39;oubliez pas de déconnecter puis reconnecter la console pour que les modifications soient prises en compte.

## Message Center {#message-center}

Après une migration d&#39;une instance de pilotage Message Center, vous devez republier les modèles de messages transactionnels pour que ceux-ci fonctionnent.

Dans v7, les noms des modèles de message transactionnel sur les instances d’exécution ont changé. Ils sont actuellement précédés du nom de l’opérateur qui correspond à l’instance de contrôle sur laquelle ils sont créés, par exemple **control1_template1_rt** (où **control1** est le nom de l’opérateur). Si vous disposez d’un volume important de modèles, nous vous recommandons de supprimer les anciens modèles sur les instances de contrôle.
