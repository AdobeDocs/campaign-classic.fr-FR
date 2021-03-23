---
solution: Campaign Classic
product: campaign
title: À propos de la délivrabilité dans Campaign 
description: Découvrir les bonnes pratiques en matière de délivrabilité
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 0420de856d1506ab92d8f0e0824bf439e0ac7dc7
workflow-type: tm+mt
source-wordcount: '716'
ht-degree: 13%

---


# Qu&#39;est-ce que la délivrabilité{#about-deliverability}

La délivrabilité vous permet de mesurer le succès de vos campagnes en atteignant la boîte de réception de vos destinataires sans rebondir ni être marqué comme indésirable. [Découvrez pourquoi la délivrabilité est importante](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/deliverability-strategy-and-definition.html#why-deliverability-matters).

Plus précisément, la délivrabilité des e-mails se rapporte à l&#39;ensemble des caractéristiques qui déterminent la capacité d&#39;un message à atteindre sa destination, par l&#39;intermédiaire d&#39;une adresse e-mail personnelle, dans un laps de temps court, et avec la qualité attendue en termes de contenu et de format.

Pour en savoir plus sur ce qu&#39;est la délivrabilité et pour en savoir plus sur les termes, concepts et approches clés de la délivrabilité, consultez le [Guide des meilleures pratiques en matière de délivrabilité des Adobes](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html).

## Comment améliorer la délivrabilité {#deliverability-key-points}

Les problèmes de délivrabilité sont généralement liés aux mesures de protection contre le spam mises en oeuvre par les prestataires Internet et les administrateurs de serveurs de messagerie.

* Pour obtenir des recommandations générales sur la manière de concevoir des campagnes de marketing par courriel réussies, consultez la [Stratégie et définition de la délivrabilité](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/deliverability-strategy-and-definition.html).

* Pour des recommandations plus spécifiques sur la façon d&#39;optimiser la délivrabilité de vos courriels Adobe Campaign, l&#39;Adobe recommande d&#39;utiliser les meilleures pratiques répertoriées dans cette section.

>[!NOTE]
>
>Les FAI étant obligés de développer continuellement de nouvelles techniques de filtrage sophistiquées pour protéger leurs clients contre les spammeurs, la délivrabilité des courriels se caractérise par des critères et des règles en constante évolution. Consultez le [Guide des meilleures pratiques en matière de délivrabilité des Adobes](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html) régulièrement mis à jour.

### Taux de délivrabilité

Le taux de délivrabilité est le nombre de messages qui ont atteint les boîtes de réception des destinataires par rapport au nombre de messages qui ont été remis. Pour améliorer la délivrabilité, vous pouvez augmenter ce taux.

Avec Adobe Campaign, le taux de délivrabilité dépend de nombreux facteurs, notamment :

* Configuration correcte de vos instances : contactez votre représentant d&#39;Adobe pour obtenir de l&#39;aide.
* Configuration réseau légitime : voir [cette section](../../delivery/using/optimize-delivery.md#network-config) et [Configuration et stratégie du domaine](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#domain-setup-and-strategy).
* Votre réputation d&#39;adresse IP : voir [Stratégie IP](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#ip-strategy).
* Qualité des adresses ciblées : voir [Gestion des Quarantaines](../../delivery/using/optimize-delivery.md#quarantine-management).
* Faibles taux de [plaintes](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/complaints.html) et de [rebond](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/bounces.html#hard-bounces).
* Contenu de votre message : voir [Contrôle du contenu du courrier électronique](../../delivery/using/control-message-content.md).
* Authentification des messages (SPF, DKIM, DMARC) : voir [cette section](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication).
* Connaissance de l&#39;expéditeur : pour savoir comment les principaux FAI évaluent la réputation d&#39;un expéditeur, voir [cette section](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/internet-service-provider-specifics/overview.html).

## Outils de délivrabilité de Campaign {#deliverability-tools}

<!--Adobe Campaign provides a number of tools designed to ensure optimal deliverability.-->
Adobe Campaign fournit plusieurs outils pour suivre et améliorer les performances de délivrabilité de votre plate-forme. Cette page met également en évidence les principaux principes que vous devez garder à l&#39;esprit pour optimiser la délivrabilité lors de l&#39;utilisation de Campaign.

### Créez soigneusement votre message

Lors de la configuration, de la conception et du test de votre message, veillez à respecter les meilleures pratiques mentionnées dans les sections ci-dessous. L&#39;exploitation de toutes les fonctionnalités fournies par Adobe Campaign vous aide à améliorer la délivrabilité.

* [Bonnes pratiques de diffusion](../../delivery/using/delivery-best-practices.md)
* [Contrôle du contenu des emails](../../delivery/using/control-message-content.md)
* [Inbox rendering](../../delivery/using/inbox-rendering.md)
* [Envoyer un bon à tirer](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof)

### Vérifier le consentement au moyen de l&#39;inclusion de doublon {#double-opt-in}

Pour éviter d&#39;envoyer des messages à des adresses incorrectes, limiter les communications incorrectes et améliorer la réputation de l&#39;expéditeur, l&#39;Adobe recommande la mise en oeuvre d&#39;un mécanisme d&#39;inclusion doublon. Cette méthode vous permet de vous assurer que vos destinataires se sont abonnés intentionnellement.

Pour plus d&#39;informations à ce sujet, voir [Créer un formulaire d&#39;abonnement avec double opt-in](../../web/using/use-cases--web-forms.md#create-a-subscription--form-with-double-opt-in).

Pour plus d&#39;informations sur les meilleures pratiques lors de la collecte de données auprès de vos clients, consultez le [Guide des meilleures pratiques en matière de délivrabilité des Adobes](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/first-impressions/address-collection-and-list-growth.html#data-quality-and-hygiene).

### Exploitation de la gestion des quarantaines

Adobe Campaign gère une liste qui recueille les plaintes contre le spam, les rebonds durs et les rebonds doux qui se produisent de manière cohérente.

Pour protéger votre délivrabilité, les destinataires dont les adresses se trouvent sur cette liste sont exclus par défaut de toutes les diffusions futures, car envoyer à ces contacts pourrait nuire à votre réputation d&#39;envoi.

Certains fournisseurs d&#39;accès Internet considèrent automatiquement les emails comme du spam si le taux d&#39;adresses invalides est trop élevé. La quarantaine permet donc d&#39;éviter d&#39;être ajouté à une liste bloquée par ces fournisseurs.

Voir à ce propos les sections suivantes :

* [Comprendre les diffusions en échec](../../delivery/using/understanding-delivery-failures.md)
* [Comprendre la gestion des quarantaines](../../delivery/using/understanding-quarantine-management.md)
* [Quarantaine et liste bloquée](../../delivery/using/understanding-quarantine-management.md#quarantine-vs-denylist)

### Utilisation des outils de surveillance et de rapports

Utilisez les fonctionnalités offertes par Adobe Campaign pour surveiller votre délivrabilité.

Adobe Campaign vous permet de vérifier les performances de vos diffusions à l’aide d’un ensemble d’indicateurs et de rapports en temps réel intégrés afin de mieux comprendre vos diffusions.

Voir à ce propos les sections suivantes :

* [Contrôle de la délivrabilité](../../delivery/using/monitoring-deliverability.md)
* [A propos du suivi des diffusions](../../delivery/using/about-delivery-monitoring.md)
* [A propos des rapports natifs de Campaign](../../reporting/using/about-campaign-built-in-reports.md)

<!--TO REMOVE
## Background {#background}

Email deliverability presents a major challenge to marketers - whether they're sending a few thousand messages or several billion. One in five messages never reach the inbox, or their intended recipient.

Once relegated as a "technical issue" for the IT department, email deliverability continues to move higher on the marketing agenda. That's because savvy marketers recognize that although many of its elements are technical in nature, deliverability is ultimately a business issue with significant revenue implications.

Consider the email marketing funnel. Deliverability determines the number of messages received, which in turn impacts each subsequent stage of the funnel. Fewer emails received results in fewer opens, fewer clicks, and fewer conversions. **For companies with a large database, the difference between average and great deliverability could literally mean hundreds of thousands to millions of dollars in revenues.**

![](assets/deliverability_overview_1.png)

By settling for average (80%) deliverability, marketers are leaving significant conversions - and dollars - on the table.

What exactly is email deliverability? And how can marketers improve deliverability rates to widen the mouth of the funnel and squeeze more results from their email campaigns?

Email deliverability refers to the set of characteristics that determine a message's ability to reach its destination, via a personal e-mail address, within a short time, and with the expected quality in terms of content and format. These characteristics fall into four main categories: data quality, message and content, sending infrastructure, and reputation. Together, they form the foundation of a successful email deliverability program. This overview outlines the four fundamentals of email deliverability success and offers best practices for reaching the inbox and driving greater revenues from email marketing programs.

![](assets/deliverability_overview_2.png)-->
