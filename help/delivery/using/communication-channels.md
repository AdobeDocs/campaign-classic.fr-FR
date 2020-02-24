---
title: Canaux de communication
seo-title: Canaux de communication
description: Canaux de communication
seo-description: null
page-status-flag: never-activated
uuid: 42975431-64c9-4ecb-98ed-b1f9b13c157e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
discoiquuid: 2e2d1134-9b83-4ada-b74f-c3842a0cf044
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 4ac96bf0e54268832b84b17c3cc577af038cc712

---


# Canaux de communication{#communication-channels}

Avec Adobe Campaign, vous pouvez envoyer des campagnes cross-canal, notamment des emails, des SMS, des messages LINE, des notifications push et des courriers, et mesurer leur efficacité au travers de différents [rapports](../../reporting/using/reports-on-deliveries.md#accessing-existing-reports) dédiés. Ces messages sont conçus et envoyés par le biais des diffusions. Ils peuvent être personnalisés pour chaque destinataire.

Les principales fonctionnalités vont du ciblage, définition et personnalisation des messages, exécution des communications jusqu&#39;aux rapports opérationnels associés. Le point d&#39;entrée fonctionnel principal est l&#39;assistant de diffusion. Autour de ce point d&#39;entrée, plusieurs fonctionnalités sont couvertes par Adobe Campaign.

>[!NOTE]
>
>Adobe Campaign propose un ensemble d&#39;outils pour suivre la délivrabilité et optimiser l&#39;envoi des emails. Pour plus d&#39;informations, consultez [Prise en main de la délivrabilité](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html) et [Gestion de la délivrabilité](../../delivery/using/about-deliverability.md).

L&#39;envoi d&#39;une diffusion peut être automatisé en préparant la diffusion ou en l&#39;envoyant par le biais d&#39;un workflow. Pour plus d&#39;informations sur les activités de type diffusion dans les workflows, consultez [cette section](../../workflow/using/about-action-activities.md).

Les canaux de diffusion proposés par Adobe Campaign sont les suivants :

1. **Canal** de courriel : les remises de courrier électronique vous permettent d’envoyer des courriers électroniques personnalisés à la population cible. Reportez-vous à [A propos du canal](../../delivery/using/about-email-channel.md)de messagerie.
1. **Canal** de messagerie directe : les livraisons directes par courrier vous permettent de générer un fichier d&#39;extraction contenant des données sur la population cible. Reportez-vous à [A propos du canal](../../delivery/using/about-direct-mail-channel.md)de messagerie directe.
1. **Canal** mobile : les diffusions sur les canaux mobiles vous permettent d’envoyer des SMS personnalisés ou des messages LINE à la population cible. Reportez-vous au canal [](../../delivery/using/sms-channel.md)SMS.
1. **Canal** d&#39;application mobile : les remises d’applications mobiles vous permettent d’envoyer des notifications aux systèmes iOS et Android. Reportez-vous au chapitre sur le canal [des applications](../../delivery/using/about-mobile-app-channel.md) mobiles.

   Les autres canaux sont présentés dans [cette page](../../delivery/using/other-channels.md).

   >[!NOTE]
   >
   >L&#39;utilisation de plusieurs canaux dépend de votre package. Vérifiez votre contrat de licence.

Les diffusions peuvent être **on-line** (via email, un des canaux mobiles et les notifications push) et **off-line** (canal courrier).

Selon le canal, les modes de diffusion peuvent être les suivants :

* Envoi en masse directement via Adobe Campaign (mode par défaut pour le canal Email).
* Envoi en externe, via un opérateur spécialisé, auquel est fourni le fichier de sortie généré par l&#39;assistant de diffusion (mode par défaut pour le canal Courrier).

Les comptes externes sont paramétrés depuis le nœud **[!UICONTROL Administration > Plate-forme > Comptes externes]**. Ce paramétrage est réservé à des utilisateurs experts.

## Diffusions Email {#email-deliveries}

Le [canal Email](../../delivery/using/about-email-channel.md) est l&#39;un des principaux canaux dans Adobe Campaign. Il vous permet de planifier et d&#39;envoyer des emails personnalisés à des cibles spécifiques.

Vous pouvez envoyer différents types d&#39;emails :

* Emails uniques : emails que vous pouvez envoyer une fois à une cible définie. Ils sont généralement utilisés pour promouvoir un contenu spécifique qui ne sera préparé et envoyé qu&#39;une seule fois (newsletter, email promotionnel, etc.).
* Emails récurrents : dans une campagne, envoyez un même email régulièrement et agrégez chaque envoi et ses rapports de façon périodique. Un même email est envoyé, mais généralement à une cible différente, selon la cible éligible pour le jour de l&#39;envoi. Un exemple courant est un email d&#39;anniversaire. Voir à ce propos la section [Diffusions récurrentes](../../workflow/using/recurring-delivery.md).
* Emails transactionnels : emails unitaires qui sont déclenchés en fonction du comportement de vos clients. Voir à ce propos la section [Messages transactionnels](../../message-center/using/about-transactional-messaging.md).

Pour plus d&#39;informations sur l&#39;utilisation des diffusions et les recommandations relatives à celles-ci, consultez [Bonnes pratiques de diffusion](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliveryBestPractices.html) de Campaign.

Pour plus d&#39;informations sur les différents types de diffusion, consultez [cette section](../../delivery/using/types-of-deliveries.md).

## Diffusions sur des mobiles {#mobile-deliveries}

Adobe Campaign permet de diffuser des [SMS](../../delivery/using/sms-channel.md) et des messages [LINE](../../delivery/using/line-channel.md) sur des mobiles.

Pour les SMS, vous pouvez créer, modifier et personnaliser des messages au format texte uniquement. Vous pouvez également prévisualiser les SMS avant leur envoi.

Pour les messages LINE, vous pouvez envoyer du texte ou des images et des liens.

Pour diffuser des SMS ou des messages LINE vers un téléphone mobile, il vous faut :

* un compte externe paramétré sur le canal **[!UICONTROL Mobile (SMS)]** ou **[!UICONTROL LINE]**,
* un modèle de diffusion SMS ou LINE correctement lié à ce compte externe.

## Notifications push {#push-notifications}

Adobe Campaign vous permet d&#39;envoyer des [notifications push](../../delivery/using/about-mobile-app-channel.md) personnalisées et segmentées sur des appareils mobiles iOS et Android via des applications dédiées. Une fois les procédures de configuration et d&#39;intégration effectuées, les diffusions sur iOS et Android peuvent être créées et envoyées. Vous pouvez également concevoir des notifications enrichies avec des images et des vidéos.

## Canal Courrier {#direct-mail}

[Le canal Courrier est un canal off-line qui vous permet de personnaliser et de générer le fichier requis par les opérateurs de services postaux. Il vous offre la possibilité de mélanger des canaux off-line et on-line dans les parcours client.](../../delivery/using/about-direct-mail-channel.md)

Les canaux on-line vous permettent de créer vos messages (email, SMS, diffusion sur des applications mobiles, etc.) et de les envoyer à votre audience directement depuis Adobe Campaign. Les canaux off-line fonctionnent différemment. Lors de la préparation d&#39;une diffusion courrier, Adobe Campaign génère un fichier comprenant tous les profils ciblés et les informations de contact sélectionnées (adresse postale, par exemple). Vous pouvez ensuite envoyer ce fichier à votre opérateur de services postaux qui se chargera de l&#39;envoi.
