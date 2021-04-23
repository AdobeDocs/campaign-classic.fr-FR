---
solution: Campaign Classic
product: campaign
title: Etapes de mise en oeuvre
description: Etapes de mise en oeuvre
audience: interaction
content-type: reference
topic-tags: general-operation
exl-id: 82b88ab7-6a95-4bb3-b8b3-abea0fdd4ca0
translation-type: ht
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: ht
source-wordcount: '284'
ht-degree: 100%

---

# Etapes de mise en oeuvre{#implementation-steps}

## Paramétrage {#configuring-interaction}

>[!NOTE]
>
>Les étapes suivantes sont destinées à être réalisée par un profil de type **Administrateur** et uniquement dans les environnements en édition.

1. Création de profils utilisateur. Pour plus d’informations, consultez la section [Profils d’opérateurs](../../interaction/using/operator-profiles.md).
1. Créer un environnement d’offres en ciblant la dimension. Voir à ce sujet la section [Créer un environnement d’offre](../../interaction/using/live-design-environments.md#creating-an-offer-environment).
1. Créer des règles de typologie pour chaque environnement. Voir à ce sujet la section [Créer et référencer une règle de présentation d’offre](../../interaction/using/managing-offer-presentation.md#creating-and-referencing-an-offer-presentation-rule).
1. Créer des emplacements d’offre pour chaque environnement et configuration des fonctions de rendu. Voir à ce sujet la section [Créer des emplacements](../../interaction/using/creating-offer-spaces.md).

   >[!NOTE]
   >
   >Si l&#39;emplacement est défini sur un canal unitaire en mode identifié, il est nécessaire de spécifier les paramètres avancés de l&#39;emplacement.

1. Paramétrage du moteur d&#39;offres dans le cas d&#39;interactions entrantes, afin de proposer et mettre à jour une ou plusieurs offres.

   Les différents modes d’intégration sont détaillés dans [A propos des canaux entrants](../../interaction/using/about-inbound-channels.md).

   >[!NOTE]
   >
   >Lors de la création d&#39;un emplacement sur le canal Web entrant, un paramétrage est également nécessaire au niveau de la page du site sur laquelle l&#39;offre doit être affichée.

## Gestion du catalogue d&#39;offres {#managing-the-offer-catalog-}

>[!NOTE]
>
>Les étapes suivantes sont destinées à être réalisées par un profil de type **Chargé d&#39;offres**.

1. Créer des catégories d’offres dans des environnements d’édition. Voir à ce sujet la section [Créer des catégories d&#39;offres](../../interaction/using/creating-offer-categories.md).
1. Créer des d’offres dans des environnements d’édition. Voir à ce sujet la section [Créer une offre](../../interaction/using/creating-an-offer.md).
1. Validation et mise en ligne des offres sur un ou plusieurs emplacements afin de les rendre disponibles dans les environnements en ligne pour le chargé de diffusion. Voir à ce sujet la section [Valider et activer une offre](../../interaction/using/approving-and-activating-an-offer.md).

## Utilisation du catalogue d&#39;offres {#using-the-offer-catalog-}

>[!NOTE]
>
>Les étapes suivantes sont destinées à être réalisées par un profil de type **Chargé de diffusions**. Ce dernier intervient uniquement sur les offres présentes dans les environnements en ligne.

1. Créer une campagne.
1. Référencer une offre dans une campagne ou l’envoi d’une campagne. Voir à ce sujet la section [A propos des canaux sortants](../../interaction/using/about-outbound-channels.md).
