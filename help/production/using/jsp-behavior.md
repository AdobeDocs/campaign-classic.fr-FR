---
product: campaign
title: Comportement des JSP
description: Comportement des JSP
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 858d00d0-7c65-43be-8bae-f0f945f71f1a
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: ht
source-wordcount: '36'
ht-degree: 100%

---

# Comportement des JSP{#jsp-behavior}



Si certaines **jsp** ne s&#39;exécutent pas correctement, vous devez forcer leur recompilation.

Pour cela, saisissez les commandes suivantes :

```
nlserver stop web
cd nl6/tomcat-8
rm -r work/
nlserver start web
```

Les **jsp** sont regénérées à la connexion suivante.
