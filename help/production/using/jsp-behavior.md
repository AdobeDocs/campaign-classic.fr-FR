---
product: campaign
title: Comportement des JSP
description: Comportement des JSP
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 858d00d0-7c65-43be-8bae-f0f945f71f1a
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '36'
ht-degree: 100%

---

# Comportement des JSP{#jsp-behavior}

![](../../assets/v7-only.svg)

Si certaines **jsp** ne s&#39;exécutent pas correctement, vous devez forcer leur recompilation.

Pour cela, saisissez les commandes suivantes :

```
nlserver stop web
cd nl6/tomcat-8
rm -r work/
nlserver start web
```

Les **jsp** sont regénérées à la connexion suivante.
