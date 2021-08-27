---
product: campaign
title: Prérequis pour la migration vers Adobe Campaign 7
description: Prérequis pour la migration vers Adobe Campaign 7
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
exl-id: 747d8a2c-b13a-4852-a9b5-0d37b236a36f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '80'
ht-degree: 100%

---

# Prérequis pour la migration vers Adobe Campaign 7{#prerequisites-for-migration-to-adobe-campaign}

![](../../assets/v7-only.svg)

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
