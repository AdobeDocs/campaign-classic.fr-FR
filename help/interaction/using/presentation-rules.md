---
title: Règles de présentation
seo-title: Règles de présentation
description: Règles de présentation
seo-description: null
page-status-flag: never-activated
uuid: 460f06f8-cdb9-401d-a45e-e54e56d66781
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: case-study
discoiquuid: 8ef303b4-d9ce-40ee-a6c6-ed5012ab8eb8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 28614a6b0c45deef17d9b3275a16e65bdff4538b

---


# Règles de présentation{#presentation-rules}

## Création d&#39;une règle de présentation {#creating-a-presentation-rule}

Dans votre base, vous disposez de plusieurs offres de voyages pour l&#39;Europe, l&#39;Afrique, les Etats-Unis et le Canada. Vous souhaitez proposer des offres de voyage pour le Canada mais si un destinataire devait refuser ce type d&#39;offre, vous ne voulez pas lui reproposer.

Vous allez donc paramétrer votre règle de façon à ne proposer de voyages au Canada qu&#39;une seule fois à un destinataire et à ne pas lui reproposer s&#39;il l&#39;a déjà refusé.

1. Dans l’arborescence d’Adobe Campaign, accédez au noeud **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Typology management]** > **[!UICONTROL Typology rules]** .
1. Create a new **[!UICONTROL Offer presentation]** type rule.

   ![](assets/offer_typology_example_001.png)

1. Modifiez son libellé et sa description si nécessaire.

   ![](assets/offer_typology_example_002.png)

1. Choose the **[!UICONTROL All channels]** option to extend the rule to all channels.

   ![](assets/offer_typology_example_003.png)

1. Click the **[!UICONTROL Edit expression]** link and choose the **[!UICONTROL Category]** node as an expression.

   ![](assets/offer_typology_example_004.png)

1. Sélectionnez la catégorie correspondant à vos offres de voyage pour le Canada puis cliquez sur **[!UICONTROL OK]** pour fermer la fenêtre de requête.

   ![](assets/offer_typology_example_005.png)

1. In the **[!UICONTROL Offer presentation]** tab, choose the same dimensions as those configured in the environment.

   ![](assets/offer_typology_example_006.png)

1. Indiquez la période pendant laquelle la règle doit s&#39;appliquer.

   ![](assets/offer_typology_example_007.png)

1. Limitez la proposition à une occurrence afin que les destinataires qui ont déjà refusé un voyage au Canada ne reçoivent pas à nouveau une proposition similaire.

   ![](assets/offer_typology_example_008.png)

1. Sélectionnez le **[!UICONTROL Offers for the same category]** filtre pour exclure toutes les offres de la catégorie **Canada** .

   ![](assets/offer_typology_example_020.png)

1. Select the **[!UICONTROL Rejected propositions]** filter to take into account only propositions rejected by the recipient.

   ![](assets/offer_typology_example_021.png)

1. Choisissez les destinataires pour lesquels la règle doit s&#39;appliquer.

   Dans notre exemple, nous choisissons les destinataires **Grands voyageurs**.

   ![](assets/offer_typology_example_009.png)

1. Référencez votre règle dans une typologie propre aux offres.

   ![](assets/offer_typology_example_013.png)

1. Go to the offer environment, (**Environment - Recipient** in this case) and reference the new typology just created using the drop-down list in the **[!UICONTROL Eligibility]** tab.

   ![](assets/offer_typology_example_014.png)

## Application de la règle de présentation {#applying-the-presentation-rule}

Voici un exemple d&#39;application de la règle de typologie créée précédemment.

Vous allez faire une première proposition d&#39;offre appartenant, entre autre, à la catégorie de voyages pour le Canada. Si l&#39;offre est refusée par un des destinataires une première fois, elle n&#39;est pas reproposée au destinataire qui l&#39;a refusée.

1. In the **Frequent travelers** recipient folder, choose one of the profiles to check the offers for which they are eligible: click the **[!UICONTROL Propositions]** tab, then the **[!UICONTROL Preview]** tab.

   Dans notre exemple, le destinataire **Nicolas Lumos** est éligible à une offre qui fait partie de la catégorie **Canada**.

   ![](assets/offer_typology_example_015.png)

1. Créez une première diffusion email destinée à cibler vos destinataires **Grands voyageurs** avec des offres.
1. Choisissez les paramètres d&#39;appels au moteur d&#39;offres.

   Dans notre exemple la catégorie **Amériques** est choisie, sachant qu&#39;elle contient les sous-catégories **Canada** et **Etats-Unis**.

   ![](assets/offer_typology_example_016.png)

1. Insérez vos offres dans le corps du message et envoyez-les. For more on this, refer to [About outbound channels](../../interaction/using/about-outbound-channels.md).

   Votre destinataire a bien reçu l&#39;offre pour laquelle il est éligible.

1. Le destinataire a refusé l&#39;offre pour le Canada, comme indiqué dans l&#39;historique de ses propositions.

   ![](assets/offer_typology_example_018.png)

1. Vérifiez les offres auxquelles il est désormais éligible.

   Vous constatez qu&#39;aucune offre sur le Canada n&#39;est retenue.

   ![](assets/offer_typology_example_019.png)

**Rubrique connexe**

* [Gérer les offres et contrôler la redondance sur les canaux](https://helpx.adobe.com/campaign/kb/simplifying-campaign-management-acc.html#Manageoffersandcontrolredundancyacrosschannels)