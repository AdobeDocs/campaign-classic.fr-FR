---
solution: Campaign Classic
product: campaign
title: Recommandations
description: Recommandations
audience: production
content-type: reference
topic-tags: database-maintenance
translation-type: ht
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: ht
source-wordcount: '105'
ht-degree: 100%

---


# Recommandations{#recommendations}

Adobe Campaign est un système hautement transactionnel (base OLTP). De ce fait, la base de données sous-jacente est fréquemment mise à jour et, généralement, ses performances se dégradent au fil du temps. Pour y remédier, une maintenance régulière de la base de données est nécessaire.

>[!IMPORTANT]
>
>Une base de données ne peut rester performante que si elle bénéficie de procédures de maintenance régulières. La maintenance automatique proposée par certains SGBDR n&#39;est pas suffisante et ne remplace pas une maintenance en profondeur, comme pour tout système transactionnel de gestion de base de données relationnelle.
>  
>Les procédures décrites dans ce document sont des recommandations. Le responsable des plans de maintenance de la base de données est l&#39;administrateur de la base de données. C&#39;est à lui que vous devez d&#39;abord vous adresser en cas de problème.
