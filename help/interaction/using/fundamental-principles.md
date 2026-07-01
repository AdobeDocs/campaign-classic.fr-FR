---
product: campaign
title: Principes fondamentaux
description: Principes fondamentaux
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: general-operation
exl-id: b13ecfc9-1723-42b2-ab30-d5637cc3d0dd
TQID: https://experienceleague.adobe.com/85eFjFxcGeeWAYkV8sHKgsrJc0rqATQlSEglE05LjAg
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
feature_v2:
  - id: b6fcaf36-3bc4-4604-94f3-81b5d3f41ecf
subfeature_v2: []
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 338
ht-degree: 100%

---

# Principes fondamentaux{#fundamental-principles}



## Déploiement des environnements {#deploying-environments}

Pour chaque dimension de ciblage utilisée dans le cadre de la gestion des offres existe un duo d&#39;environnements :

* Un environnement de conception, dans lequel la personne responsable des offres s’occupe de créer et catégoriser les offres, de les modifier, de lancer le processus de validation afin qu’elles puissent être utilisées.Dans cet environnement sont également définies les règles propres à chaque catégorie, les emplacements sur lesquels les offres peuvent être présentées et les filtres prédéfinis utilisables pour définir l’éligibilité d’une offre.

  Les catégories peuvent également être publiées manuellement dans l&#39;environnement en ligne.

  Le processus de validation des offres est détaillé dans la section [Valider et activer une offre](../../interaction/using/approving-and-activating-an-offer.md).

* Un environnement en ligne, dans lequel se trouvent les offres approuvées de l’environnement de conception, ainsi que les différents emplacements, filtres, catégories et règles paramétrés dans l’environnement de conception.Lors d’un appel au moteur d’offres, ce dernier utilisera toujours les offres de l’environnement en ligne.

Une offre n’est déployée que sur les emplacements sélectionnés lors de la validation.Ainsi, une offre peut être en ligne mais non utilisable sur un emplacement lui aussi en ligne.

![](assets/architecture_interaction1.png)

## Types d&#39;interactions et modes de contact {#interaction-types-and-contact-methods}

On distingue deux types d’interactions possibles : les interactions entrantes, provoquées par un contact, et les interactions sortantes, provoquées par le concepteur d’offres.

Ces deux types d’interactions peuvent être réalisés soit en mode unitaire (l’offre est calculée pour un seul contact), ou en mode par lots (l’offre est calculée pour un ensemble de contacts).Généralement, les interactions entrantes sont réalisées en mode unitaire et les interactions sortantes en mode par lots.Néanmoins, des exceptions peuvent exister, par exemple pour des messages transactionnels, où l&#39;interaction sortante est réalisée en mode unitaire (voir [cette section](../../message-center/using/about-transactional-messaging.md)).

Dès lors qu&#39;une offre peut ou doit être présentée (en fonction des paramétrages réalisés), le moteur d&#39;offre joue le rôle d&#39;intermédiaire : il calcule automatiquement la meilleure offre possible pour un contact parmi celles disponibles, en combinant les données recueillies sur le contact et les différentes règles applicables définies dans l&#39;application.

![](assets/architecture_interaction2.png)
