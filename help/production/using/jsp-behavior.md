---
product: campaign
title: Comportement des JSP
description: Comportement des JSP
feature: Monitoring
badge-v7-prem: label="On-Premise/hybride uniquement" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 858d00d0-7c65-43be-8bae-f0f945f71f1a
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: ht
source-wordcount: '47'
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
