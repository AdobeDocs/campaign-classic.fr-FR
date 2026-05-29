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
TQID: https://experienceleague.adobe.com/IQSjBaSbnZcsqs0glv8z1aIwOBbtVO2roeXlJiYgEfo
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
feature_v2: []
subfeature_v2:
  - id: c03a11ff-bdf9-4e5b-b279-f468b4293464
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 66
ht-degree: 100%

---

# Comportement des JSP{#jsp-behavior}



Si certains traitements **jsp** ne s’exécutent pas correctement, vous devez forcer leur recompilation.

Pour cela, saisissez les commandes suivantes :

```
nlserver stop web
cd nl6/tomcat-X
rm -r work/
nlserver start web
```

Les traitements **jsp** sont regénérés àla connexion suivante.
