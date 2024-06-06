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
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: ht
source-wordcount: '176'
ht-degree: 100%

---

# Serveur de messagerie{#messaging-server}



Adobe Campaign gère nativement l&#39;envoi d&#39;emails. Toutefois, un serveur de messagerie traditionnel est nécessaire afin de recevoir les retours liés aux mails non livrables (mailer daemons). Les boîtes aux lettres configurées sur ce serveur sont automatiquement relevées et traitées par l&#39;application.

Tout serveur de messagerie peut être utilisé dès lors que les boîtes mails configurées pour recevoir les mails rebonds peuvent être relevées à l&#39;aide du protocole POP3 et que ce serveur préserve les en-têtes SMTP &quot;Message-ID&quot; lors du relevé des emails. Par exemple, des déploiements à base de Qmail, SendMail et Microsoft Exchange sont actuellement en production. Toutefois, certaines installations de Lotus Notes/Domino ont révélé un problème de préservation des en-têtes &quot;Message-ID&quot;.

>[!CAUTION]
>
>Ce serveur mail peut être exposé à une lourde charge : en phase initiale, des listes typiques génèrent un taux de 10% de rebonds (si vous faites une première diffusion de 100 000 mails, il est courant de recevoir 10 000 mails rebonds).
>
>Il est donc fortement déconseillé d&#39;utiliser votre serveur de messagerie d&#39;entreprise pour cette fonction, car il pourrait être fortement impacté.
>
>Il est recommandé de configurer un sous-domaine spécifique dans votre DNS et un serveur mail dédié à la gestion des mails rebonds.
