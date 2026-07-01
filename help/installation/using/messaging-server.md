---
product: campaign
title: Serveur de messagerie
description: Serveur de messagerie
feature: Installation, Instance Settings
badge-v7-prem: label="On-Premise/hybride uniquement" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: d9ffa58d-81e3-4291-8502-3cb7c326b666
feature_v2: []
subfeature_v2: []
source-git-commit: bb41e9407ab5853b0194bb325bbf3f17bc3ea232
workflow-type: ht
source-wordcount: 198
ht-degree: 100%

---

# Serveur de messagerie{#messaging-server}



Adobe Campaign gère nativement l’envoi d’e-mails. Toutefois, un serveur de messagerie traditionnel est nécessaire afin de recevoir les retours liés aux e-mails non livrables (depuis des démons de messagerie).Les boîtes de réception configurées sur ce serveur sont automatiquement traitées par l’application.

Tous les serveurs configurés pour un accès POP3 peuvent être utilisés pour recevoir des retours d’e-mail s’ils conservent les en-têtes « Message-ID » SMTP lors de la réception de l’e-mail.Par exemple, les implémentations utilisant Qmail, SendMail et Microsoft Exchange sont actuellement en production.Cependant, certaines installations de Lotus Notes/domino ont révélé un problème de conservation des en-têtes « Message-Id ».

>[!CAUTION]
>
>Ce serveur mail peut être exposé à une lourde charge : en phase initiale, des listes typiques génèrent un taux de 10 % de rebonds (si vous envoyez 100 000 messages, attendez-vous à recevoir 10 000 rebonds).
>
>Il est donc fortement déconseillé d&#39;utiliser votre serveur de messagerie d&#39;entreprise pour cette fonction, car il pourrait être fortement impacté.
>
>Il est recommandé de configurer un sous-domaine spécifique dans votre DNS et un serveur mail dédié à la gestion des mails rebonds.
