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
source-wordcount: '116'
ht-degree: 100%

---

# Recommandations{#recommendations}



Adobe Campaign est un système hautement transactionnel (base OLTP). De ce fait, la base de données sous-jacente est fréquemment mise à jour et, généralement, ses performances se dégradent au fil du temps. Pour y remédier, une maintenance régulière de la base de données est nécessaire.

>[!IMPORTANT]
>
>Une base de données ne peut rester performante que si elle bénéficie de procédures de maintenance régulières. La maintenance automatique proposée par certains SGBDR n&#39;est pas suffisante et ne remplace pas une maintenance en profondeur, comme pour tout système transactionnel de gestion de base de données relationnelle.
>  
>Les procédures décrites dans ce document sont des recommandations. Les plans de maintenance sont la responsabilité de l’administrateur de la base de données, qui doit être votre premier contact en cas de problème.
