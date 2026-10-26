---
product: campaign
title: Serveur de messagerie
description: Serveur de messagerie
feature: Installation, Instance Settings
badge-v7-prem: label="On-premise/hybrid only" type="Caution" url="https://experienceleague.adobe.com/fr/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: d9ffa58d-81e3-4291-8502-3cb7c326b666
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 7f0a1ee5-eeb8-5478-a9cd-b1896f033118
    internal-label: Instance Settings
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: e656c701-3899-4db3-989c-de0980ddfffa
    internal-label: Installation
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: ht
source-wordcount: '186'
ht-degree: 100%
---
# Serveur de messagerie{#messaging-server}



Adobe Campaign gère nativement l’envoi d’e-mails. Toutefois, un serveur de messagerie traditionnel est nécessaire afin de recevoir les retours liés aux e-mails non livrables (depuis des démons de messagerie). Les boîtes de réception configurées sur ce serveur sont automatiquement traitées par l’application.

Tous les serveurs configurés pour un accès POP3 peuvent être utilisés pour recevoir des retours d’e-mail s’ils conservent les en-têtes « Message-ID » SMTP lors de la réception de l’e-mail. Par exemple, les implémentations utilisant Qmail, SendMail et Microsoft Exchange sont actuellement en production. Cependant, certaines installations de Lotus Notes/domino ont révélé un problème de conservation des en-têtes « Message-Id ».

>[!CAUTION]
>
>Ce serveur mail peut être exposé à une lourde charge : en phase initiale, des listes typiques génèrent un taux de 10 % de rebonds (si vous envoyez 100 000 messages, attendez-vous à recevoir 10 000 rebonds).
>
>Il est donc fortement déconseillé d&#39;utiliser votre serveur de messagerie d&#39;entreprise pour cette fonction, car il pourrait être fortement impacté.
>
>Il est recommandé de configurer un sous-domaine spécifique dans votre DNS et un serveur mail dédié à la gestion des mails rebonds.
