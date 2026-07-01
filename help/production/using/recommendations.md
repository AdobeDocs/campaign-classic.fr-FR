---
product: campaign
title: Recommandations
description: Recommandations
feature: Monitoring
badge-v7-prem: label="On-Premise/hybride uniquement" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: e458f6cb-f6d1-4688-9f6d-2a27a2f90829
TQID: https://experienceleague.adobe.com/hz0wmjq8MEpmen-C30F0tHt5-sRXjQAJ6vaie3hjfAo
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: id: c03a11ff-bdf9-4e5b-b279-f468b4293464id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 136
ht-degree: 100%

---

# Recommandations{#recommendations}



Adobe Campaign est un système hautement transactionnel (base de données OLTP).Cela signifie que la base de données sous-jacente sera fréquemment mise à jour, ce qui entraînera une dégradation des performances au fil du temps.Pour éviter ce type de problème, une maintenance régulière de la base de données est nécessaire.

>[!IMPORTANT]
>
>Une base de données ne fonctionne de manière optimale que si elle est fait l’objet d’une maintenance régulière.La maintenance automatique proposée par certains SGBDR n’est pas suffisante et ne remplace pas une maintenance en profondeur, comme pour tout système transactionnel de gestion de base de données relationnelle.
>  
>Les procédures décrites dans ce document sont des recommandations. Les plans de maintenance sont la responsabilité de l’administrateur de la base de données, qui doit être votre premier contact en cas de problème.
