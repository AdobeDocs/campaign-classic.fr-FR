---
title: Prérequis pour la migration vers Adobe Campaign 7
seo-title: Prérequis pour la migration vers Adobe Campaign 7
description: Prérequis pour la migration vers Adobe Campaign 7
seo-description: null
page-status-flag: never-activated
uuid: 9f4e4cdf-5338-4597-9d9d-5a3bd13033c7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
discoiquuid: a3bbd8cc-97c6-4b08-adbf-76ab77b97262
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 100%

---


# Prérequis pour la migration vers Adobe Campaign 7{#prerequisites-for-migration-to-adobe-campaign}

Avant d&#39;effectuer une migration, consultez les sections [Avant de commencer la migration](../../migration/using/before-starting-migration.md) et [Configurer votre plateforme](../../migration/using/configuring-your-platform.md).

Lors de la migration de la v6.02 vers Adobe Campaign v7, certains fichiers auparavant diffusés ne le sont plus.

Si une erreur client apparaît, vous devez soit mettre à jour vos tableaux de bord avec le nouveau code Adobe Campaign v7, soit copier manuellement les fichiers suivants de l&#39;instance v6.02 vers l&#39;instance v7 :

```
v6.02 files and spaces:
/usr/local/neolane/nl6/datakit/xtk/eng/css/dropDownMenu.css
/usr/local/neolane/nl6/datakit/xtk/eng/js/client/dropDownMenu.js
v6.1 files and spaces:
/usr/local/neolane/nl6/deprecated/xtk/css/dropDownMenu.css
/usr/local/neolane/nl6/deprecated/xtk/js/client/dropDownMenu.js  
```
