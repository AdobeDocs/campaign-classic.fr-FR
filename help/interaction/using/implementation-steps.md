---
title: Etapes de mise en oeuvre
seo-title: Etapes de mise en oeuvre
description: Etapes de mise en oeuvre
seo-description: null
page-status-flag: never-activated
uuid: 11582071-00a2-4245-af3e-bc81174ce223
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: general-operation
discoiquuid: 7f79c0d8-77b0-4cc6-a888-7dbd32d2f3b6
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Etapes de mise en oeuvre{#implementation-steps}

## Paramétrage {#configuring-interaction}

>[!NOTE]
>
>Les étapes suivantes sont destinées à être réalisée par un profil de type **Administrateur** et uniquement dans les environnements en édition.

1. Création de profils utilisateur. For more on this, refer to [Operator profiles](../../interaction/using/operator-profiles.md).
1. Création d’un environnement d’offre en ciblant la dimension. Pour plus d’informations, reportez-vous à la section [Création d’un environnement](../../interaction/using/live-design-environments.md#creating-an-offer-environment)d’offre.
1. Création de règles de typologie pour chaque environnement. Pour plus d’informations, reportez-vous à la section [Création et référence d’une règle](../../interaction/using/managing-offer-presentation.md#creating-and-referencing-an-offer-presentation-rule)de présentation d’offre.
1. Création d’espaces d’offre pour chaque environnement et configuration des fonctions de rendu. For more on this, refer to [Creating offer spaces](../../interaction/using/creating-offer-spaces.md).

   >[!NOTE]
   >
   >Si l&#39;emplacement est défini sur un canal unitaire en mode identifié, il est nécessaire de spécifier les paramètres avancés de l&#39;emplacement.

1. Paramétrage du moteur d&#39;offres dans le cas d&#39;interactions entrantes, afin de proposer et mettre à jour une ou plusieurs offres.

   Les différents modes d’intégration sont détaillés dans [A propos des canaux](../../interaction/using/about-inbound-channels.md)entrants.

   >[!NOTE]
   >
   >Lors de la création d&#39;un emplacement sur le canal Web entrant, un paramétrage est également nécessaire au niveau de la page du site sur laquelle l&#39;offre doit être affichée.

## Gestion du catalogue d&#39;offres {#managing-the-offer-catalog-}

>[!NOTE]
>
>Les étapes suivantes sont destinées à être réalisées par un profil de type **Chargé d&#39;offres**.

1. Création de catégories d’offres dans des environnements de conception. For more on this, refer to [Creating offer categories](../../interaction/using/creating-offer-categories.md).
1. Création d’offres dans des environnements de conception. For more on this, refer to [Creating an offer](../../interaction/using/creating-an-offer.md).
1. Approbation et publication d’offres sur un ou plusieurs espaces afin de les rendre disponibles dans des environnements dynamiques pour le gestionnaire de diffusion. Pour plus d’informations, reportez-vous à la section [Approbation et activation d’une offre](../../interaction/using/approving-and-activating-an-offer.md).

## Utilisation du catalogue d&#39;offres {#using-the-offer-catalog-}

>[!NOTE]
>
>Les étapes suivantes sont destinées à être réalisées par un profil de type **Chargé de diffusions**. Ce dernier intervient uniquement sur les offres présentes dans les environnements en ligne.

1. Créer une campagne.
1. Référence à une offre dans une campagne ou une diffusion de campagne. For more on this, refer to [About outbound channels](../../interaction/using/about-outbound-channels.md).

