---
title: Comportement des JSP
seo-title: Comportement des JSP
description: Comportement des JSP
seo-description: null
page-status-flag: never-activated
uuid: b9e9f348-968c-46e0-8340-df1f1fcaf3a3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: 5dcc4090-effe-479e-8d5c-67e6a6542fbb
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '38'
ht-degree: 100%

---


# Comportement des JSP{#jsp-behavior}

Si certaines **jsp** ne s&#39;exécutent pas correctement, vous devez forcer leur recompilation.

Pour cela, saisissez les commandes suivantes :

```
nlserver stop web
cd nl6/tomcat-7
rm -r work/
nlserver start web
```

Les **jsp** sont regénérées à la connexion suivante.
