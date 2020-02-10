---
title: Recommandations
seo-title: Recommandations
description: Recommandations
seo-description: null
page-status-flag: never-activated
uuid: d898fe6d-7627-405f-b2bc-b17bf1dc9e96
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: database-maintenance
discoiquuid: a31c5c9f-503f-4b55-8409-34d4addbd581
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2a11a73b0679c0a65dc10f71869bf2a6c6efc008

---


# Recommandations{#recommendations}

Adobe Campaign est un système hautement transactionnel (base OLTP). De ce fait, la base de données sous-jacente est fréquemment mise à jour et, généralement, ses performances se dégradent au fil du temps. Pour y remédier, une maintenance régulière de la base de données est nécessaire.

>[!CAUTION]
>
>Une base de données ne peut rester performante que si elle bénéficie de procédures de maintenance régulières. La maintenance automatique proposée par certains SGBDR n&#39;est pas suffisante et ne remplace pas une maintenance en profondeur, comme pour tout système transactionnel de gestion de base de données relationnelle.
>  
>Les procédures décrites dans ce document sont des recommandations. Le responsable des plans de maintenance de la base de données est l&#39;administrateur de la base de données. C&#39;est à lui que vous devez d&#39;abord vous adresser en cas de problème.

