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
translation-type: tm+mt
source-git-commit: 0112d5bd052ad66169225073276d1da4f3c245d8
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 3%

---


# A propos des Triggers Adobe Experience Cloud{#about-adobe-experience-triggers}

[!DNL Triggers] est une intégration entre Adobe Campaign et Adobe Analytics utilisant le pipeline. Le pipeline récupère les actions ou déclencheurs des utilisateurs de votre site Web. Un abandon de panier est un exemple de déclenchement. Les déclencheurs sont traités dans l’Adobe Campaign pour envoyer des courriers électroniques en temps quasi réel.

[!DNL Triggers] exécuter des actions marketing dans un délai court après l’action d’un utilisateur. Le temps de réponse habituel est inférieur à une heure.

Il permet des intégrations plus agiles puisque la configuration est minimale et qu’un tiers n’est pas impliqué.
Il prend également en charge des volumes élevés de trafic sans affecter les performances des activités marketing. Par exemple, l’intégration peut traiter un million de déclencheurs par heure.

## [!DNL Triggers] architecture {#triggers-architecture}

### Qu&#39;est-ce que Pipeline ? {#pipeline-explanation}

>[!CAUTION]
>
>Seules les solutions Adobe Cloud peuvent produire et consommer des événements provenant des services de pipeline de Adobe. Les systèmes externes à Adobe ne le peuvent pas.

Pipeline est un système de messagerie hébergé dans l&#39;Experience Cloud qui utilise [Apache Kafka](http://kafka.apache.org/). C&#39;est un moyen de transmettre facilement des données entre les solutions. De plus, Pipeline est une file d&#39;attente de messages plutôt qu&#39;une base de données. Les producteurs poussent les événements dans le pipeline et les consommateurs écoutent le flux et font ce qu&#39;ils veulent avec le événement. Les Événements sont gardés quelques jours mais pas plus. L&#39;objectif est d&#39;écouter 24 heures sur 24 et 7 jours sur 7 et de traiter les événements immédiatement.

![](assets/triggers_1.png)

### Comment fonctionne Pipeline ? {#how-pipeline-work}

Le [!DNL pipelined] processus est toujours en cours d’exécution sur le serveur de marketing d’Adobe Campaign. Il se connecte au pipeline, récupère les événements et les traite immédiatement.

![](assets/triggers_2.png)

Le [!DNL pipelined] processus se connecte à l’Experience Cloud à l’aide d’un service d’authentification et envoie une clé privée. Le service d’authentification renvoie un jeton. Le jeton est utilisé pour l’authentification lors de la récupération des événements. [!DNL Triggers] sont récupérées à partir d’un service Web REST à l’aide d’une requête GET simple. La réponse est au format JSON. Les paramètres de la requête incluent le nom du déclencheur et un pointeur qui indique le dernier message récupéré. Le [!DNL pipelined] processus le gère automatiquement.

## Utilisation de l’intégration d’Adobe Experience Cloud Triggers avec Adobe Campaign Classic

Voici quelques [!DNL Triggers] bonnes pratiques :

* Les [!DNL Trigger] données doivent être stockées au moment où elles arrivent à Campaign. Il ne doit pas être traité directement, car il créerait une latence.
* L’horodatage doit être vérifié à partir du message et non de la base de données.
* Utilisez TriggerTimestamp et ID de déclenchement pour supprimer des duplicata.

>[!CAUTION]
>
>L’exemple ci-dessous n’est pas fourni prêt à l’emploi. Il s’agit d’un exemple spécifique de différentes implémentations possibles.

Les événements de pipeline sont téléchargés automatiquement. Ces événements peuvent être surveillés à l’aide d’un formulaire.

![](assets/triggers_3.png)

Le noeud de Événement Pipeline n’est pas intégré et doit être ajouté, de même que le formulaire associé doit être créé dans Campaign. Ces opérations sont limitées aux utilisateurs experts uniquement. Pour plus d’informations à ce sujet, reportez-vous aux sections suivantes : [Hiérarchie](../../configuration/using/about-navigation-hierarchy.md) de navigation et [Modification de formulaires](../../configuration/using/editing-forms.md).

Un processus de campagne récurrent requête sur les déclencheurs et s’ils correspondent aux critères marketing, il début une diffusion.

![](assets/triggers_4.png)
