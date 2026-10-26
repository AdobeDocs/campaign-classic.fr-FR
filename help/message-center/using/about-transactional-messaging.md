---
product: campaign
title: Commencer avec les messages transactionnels
description: En savoir plus sur le principe de fonctionnement et les étapes clés des messages transactionnels Adobe Campaign Classic
feature: Transactional Messaging, Message Center
exl-id: dc52e789-d0bf-4e8f-b448-9d69a2762cc1
TQID: 'https://experienceleague.adobe.com/n4w2hZkuzHlD3Axc1tUCGfBQ13D28j3Xpmdh07tVr4g'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
  - id: 6d358f27-4f3c-5ddf-9159-05192e672ba7
    internal-label: Message Center
subfeature_v2:
  - id: d3b34fea-a110-482f-adb2-aae8d686bac8
    internal-label: Transactional messaging
source-git-commit: 617db6f51887118c965b8938b2b9f14335293875
workflow-type: ht
source-wordcount: '610'
ht-degree: 100%
---
# Commencer avec les messages transactionnels {#about-transactional-messaging}



## Vue d&#39;ensemble {#overview}

**Messages transactionnels** (Message Center) est un module de Campaign conçu pour gérer les notifications de déclenchement personnalisées générées à partir d’événements envoyés par un système d’informations externe.

Dans le cadre de la transition de Campaign v7 vers v8, la documentation de Campaign Classic a été rationalisé et réorganisé. Les fonctionnalités communes sont désormais disponibles exclusivement dans le jeu de documentation de Campaign v8. Pour en savoir plus sur les messages transactionnels, consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/send/real-time/transactional){target=_blank}.

[![image](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/send/real-time/transactional){target=_blank}

Cette section couvre l’architecture et la configuration des messages transactionnels des instances de contrôle et d’exécution, spécifiques aux déploiements On-Premise et hybrides.

>[!IMPORTANT]
>
>Les messages transactionnels nécessitent une licence spécifique. Veuillez vérifier votre contrat de licence.

<!--Before starting with transactional messaging, make sure you read the corresponding [best practices and limitations]().-->

## Principe de fonctionnement des messages transactionnels {#transactional-messaging-operating-principle}

Le module de messages transactionnels Adobe Campaign s&#39;intègre dans un système d&#39;informations qui renvoie les événements à transformer en messages transactionnels personnalisés. Ces messages peuvent être envoyés individuellement ou par lots via e-mail, SMS ou notifications push.

Cette fonctionnalité repose sur une architecture spécifique, où l&#39;**instance d&#39;exécution** est séparée de l&#39;**instance de pilotage**. Cette distribution garantit une disponibilité accrue et une meilleure gestion de la charge. Voir à ce propos [Architecture des messages transactionnels](../../message-center/using/transactional-messaging-architecture.md).

>[!NOTE]
>
>Pour créer des utilisateurs pour les instances d&#39;exécution Message Center hébergées sur Adobe Cloud, vous devez contacter l&#39;[Assistance clientèle d&#39;Adobe](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). Les utilisateurs de Message Center sont des opérateurs spécifiques qui ont besoin d&#39;autorisations dédiées pour accéder aux dossiers **[!UICONTROL Evénements temps réel (nmsRtEvent)]**.

>[!NOTE]
>
>Adobe Campaign donne la priorité au traitement des messages transactionnels par rapport à toute autre diffusion.

## Principales étapes {#key-steps}

Les principales étapes de création et de gestion des messages transactionnels personnalisés dans Adobe Campaign sont résumées ci-dessous.

### Étapes à effectuer sur l&#39;instance de pilotage

Sur l’**instance de pilotage**, vous devez effectuer les actions suivantes :

1. [Créer un type d’événement](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/send/real-time/transactional){target="_blank"} (documentation de Campaign v8).
1. [Créer et concevoir le modèle de message](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/send/real-time/transactional-template){target="_blank"} (documentation de Campaign v8). Vous devez associer un événement à votre message au cours de cette étape.
1. [Tester le message](../../message-center/using/testing-message-templates.md).
1. [Publier le modèle de message](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/send/real-time/transactional-template){target="_blank"} (documentation de Campaign v8).

>[!NOTE]
>
>Toutes les étapes ci-dessus sont effectuées sur l&#39;**instance de pilotage**. La publication du modèle sur l&#39;instance de pilotage le publiera également sur toutes les **instances d&#39;exécution**. Pour plus d&#39;informations sur les instances de message transactionnel, voir [Architecture des messages transactionnels](../../message-center/using/transactional-messaging-architecture.md).

### Traitement des événements sur l&#39;instance d&#39;exécution

Une fois que vous avez conçu et publié le modèle de message transactionnel, si un événement correspondant est déclenché, les principales étapes ci-dessous sont effectuées sur l&#39;**instance d&#39;exécution** :

1. Lorsque l&#39;événement est généré par le système d&#39;informations externe, les données pertinentes sont envoyées à Campaign via les méthodes **PushEvent** et **PushEvents**. Consultez [Collection d’événements](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/send/real-time/event/event-processing#event-collection){target="_blank"} (documentation de Campaign v8).
1. L’événement est associé au modèle de message approprié. Consultez [Routage vers un modèle](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/send/real-time/event/event-processing#event-to-template){target="_blank"} (documentation de Campaign v8).
1. Une fois l’étape d’enrichissement terminée, la diffusion est envoyée. Consultez [Exécution de la diffusion](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/send/real-time/event/delivery-execution){target="_blank"} (documentation de Campaign v8). Chaque destinataire ciblé reçoit un message personnalisé.

## Rubriques connexes : {#related-topics}

* [Commencer avec les canaux de communication](../../delivery/using/communication-channels.md)
* [Étapes clés de création de diffusion](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html?lang=fr){target="_blank"}
* [Architecture des messages transactionnels](../../message-center/using/transactional-messaging-architecture.md)
* [Accéder aux rapports des messages transactionnels](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/send/real-time/event/delivery-execution){target="_blank"} (documentation de Campaign v8)
