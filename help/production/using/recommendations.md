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
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 43%

---

# Recommandations{#recommendations}



Adobe Campaign est un système hautement transactionnel (base de données OLTP). Cela signifie que la base de données sous-jacente sera fréquemment mise à jour, ce qui entraînera une dégradation des performances au fil du temps. Pour éviter ce type de problème, une maintenance régulière de la base de données est nécessaire.

>[!IMPORTANT]
>
>Une base de données ne fonctionne de manière optimale que si elle est gérée régulièrement. La maintenance automatique proposée par certains SGBDR n&#39;est pas suffisante et ne remplace pas la maintenance en profondeur, comme pour tout système de gestion transactionnelle de base de données relationnelle.
>  
>Les procédures décrites dans ce document sont des recommandations. Les plans de maintenance sont la responsabilité de l’administrateur de la base de données, qui doit être votre premier contact en cas de problème.
