---
title: Serveur de messagerie
seo-title: Serveur de messagerie
description: Serveur de messagerie
seo-description: null
page-status-flag: never-activated
uuid: d7de0405-23eb-4a0d-80a5-c75d661771bb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
discoiquuid: 1556e87f-9d92-4548-a75a-4f44030ab8d5
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 46f5bfb41bfe9c938ac0ffa767ead3e47a32047d

---


# Serveur de messagerie{#messaging-server}

Adobe Campaign gère nativement l&#39;envoi d&#39;emails. Toutefois, un serveur de messagerie traditionnel est nécessaire afin de recevoir les retours liés aux mails non livrables (mailer daemons). Les boîtes aux lettres configurées sur ce serveur sont automatiquement relevées et traitées par l&#39;application.

Tout serveur de messagerie peut être utilisé dès lors que les boîtes mails configurées pour recevoir les mails rebonds peuvent être relevées à l&#39;aide du protocole POP3 et que ce serveur préserve les en-têtes SMTP &quot;Message-ID&quot; lors du relevé des emails. Par exemple, des déploiements à base de Qmail, SendMail et Microsoft Exchange sont actuellement en production. Toutefois, certaines installations de Lotus Notes/Domino ont révélé un problème de préservation des en-têtes &quot;Message-ID&quot;.

>[!CAUTION]
>
>Ce serveur mail peut être exposé à une lourde charge : en phase initiale, des listes typiques génèrent un taux de 10% de rebonds (si vous faites une première diffusion de 100 000 mails, il est courant de recevoir 10 000 mails rebonds).
>
>Il est donc fortement déconseillé d&#39;utiliser votre serveur de messagerie d&#39;entreprise pour cette fonction, car il pourrait être fortement impacté.
>
>Il est recommandé de configurer un sous-domaine spécifique dans votre DNS et un serveur mail dédié à la gestion des mails rebonds.
