---
title: A propos d'Adobe Experience Manager
seo-title: A propos d'Adobe Experience Manager
description: A propos d'Adobe Experience Manager
seo-description: null
page-status-flag: never-activated
uuid: c523822f-8178-4989-bd88-ab402470e540
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 0d617f1c-0d0b-489f-9027-a92b1f1eee37
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 0112d5bd052ad66169225073276d1da4f3c245d8
workflow-type: ht
source-wordcount: '479'
ht-degree: 100%

---


# A propos des Triggers Adobe Experience Cloud{#about-adobe-experience-triggers}

[!DNL Triggers] est une intégration entre Adobe Campaign et Adobe Analytics, qui utilise le pipeline. Le pipeline récupère les actions ou déclencheurs des utilisateurs de votre site web. Un abandon de panier est un exemple de déclencheur. Les déclencheurs sont traités dans Adobe Campaign pour envoyer des emails en temps quasi réel.

[!DNL Triggers] exécute des actions marketing dans un délai court après l’action d’un utilisateur. Le temps de réponse habituel est inférieur à une heure.

Il permet des intégrations plus agiles puisque la configuration est minimale et qu’un tiers n’est pas impliqué.
Il prend également en charge des volumes élevés de trafic sans affecter les performances des activités marketing. Par exemple, l’intégration peut traiter un million de déclencheurs par heure.

## Architecture de [!DNL Triggers] {#triggers-architecture}

### Qu’est-ce que Pipeline ? {#pipeline-explanation}

>[!CAUTION]
>
>Seules les solutions Adobe Cloud peuvent produire et consommer des événements provenant des services de Pipeline d’Adobe. Les systèmes externes à Adobe ne le peuvent pas.

Pipeline est un système de messagerie hébergé dans Experience Cloud qui utilise [Apache Kafka](http://kafka.apache.org/). C’est un moyen de transmettre facilement des données entre les solutions. De plus, Pipeline est une file d’attente de messages plutôt qu’une base de données. Les producteurs envoient les événements dans le pipeline et les consommateurs écoutent le flux et font ce qu’ils veulent avec les événements. Les événements sont conservés quelques jours mais pas plus. L’objectif est de procéder à l’écoute 24 heures sur 24, 7 jours sur 7, et de traiter les événements immédiatement.

![](assets/triggers_1.png)

### Comment fonctionne Pipeline ? {#how-pipeline-work}

Le processus [!DNL pipelined] est toujours en cours d’exécution sur le serveur marketing d’Adobe Campaign. Il se connecte au pipeline, récupère les événements et les traite immédiatement.

![](assets/triggers_2.png)

Le processus [!DNL pipelined] se connecte à Experience Cloud à l’aide d’un service d’authentification et envoie une clé privée. Le service d’authentification renvoie un jeton. Le jeton est utilisé pour l’authentification lors de la récupération des événements. Les [!DNL Triggers] sont récupérés à partir d’un service web REST à l’aide d’une requête GET simple. La réponse est au format JSON. Les paramètres de la requête incluent le nom du déclencheur et un pointeur qui indique le dernier message récupéré. Le processus [!DNL pipelined] le gère automatiquement.

## Utilisation de l’intégration des Triggers Adobe Experience Cloud avec Adobe Campaign Classic

Voici quelques bonnes pratiques [!DNL Triggers] :

* Les données [!DNL Trigger] doivent être stockées au moment où elles arrivent dans Campaign. Elles ne doivent pas être traitées directement, car cela créerait une latence.
* La date et l’heure doivent être vérifiées à partir du message et non de la base de données.
* Utilisez TriggerTimestamp et l’identifiant du déclencheur pour supprimer des duplicatas.

>[!CAUTION]
>
>L’exemple ci-dessous n’est pas fourni d’usine. Il s’agit d’un exemple spécifique de différentes implémentations possibles.

Les événements de pipeline sont téléchargés automatiquement. Ils peuvent être surveillés à l’aide d’un formulaire.

![](assets/triggers_3.png)

Le nœud d’événement de pipeline n’est pas natif et doit être ajouté, de même que le formulaire associé doit être créé dans Campaign. Ces opérations sont limitées aux utilisateurs experts uniquement. Pour plus d’informations à ce sujet, reportez-vous aux sections suivantes : [Arborescence de navigation](../../configuration/using/about-navigation-hierarchy.md) et [Éditer les formulaires](../../configuration/using/editing-forms.md).

Un workflow de campagne récurrent effectue des requêtes sur les déclencheurs et s’ils correspondent aux critères marketing, il débute une diffusion.

![](assets/triggers_4.png)
