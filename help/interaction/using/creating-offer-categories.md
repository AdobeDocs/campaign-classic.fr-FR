---
title: Créer des catégories d'offres
seo-title: Créer des catégories d'offres
description: Créer des catégories d'offres
seo-description: null
page-status-flag: never-activated
uuid: 5ac0ae5e-1731-4699-b4ef-f3867ad0ab58
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
discoiquuid: a9fad813-3256-4a00-ba74-7dbaba9e8e23
translation-type: tm+mt
source-git-commit: 8fc3e793ec544948049fc122b44b6bffdebecba0
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 85%

---


# Créer des catégories d&#39;offres{#creating-offer-categories}

La création des catégories d&#39;offres s&#39;effectue uniquement dans l&#39;environnement **[!UICONTROL En édition]**. Elles sont automatiquement déployées dans l&#39;environnement **[!UICONTROL En ligne]** (c.-à.-d. rendues disponibles pour être proposées) lorsque la ou les offres créées/modifiées qu&#39;elles contiennent sont validées. Par défaut, l&#39;environnement **[!UICONTROL En édition]** contient une catégorie destinée à recevoir l&#39;ensemble des offres. Il est possible de créer des sous-catégories afin de hiérarchiser les offres du catalogue.

Pour chaque catégorie il est possible de définir des dates d&#39;éligibilité, soit une période au-delà de laquelle les offres contenues dans la catégorie ne pourront plus être présentées à leur cible. Si vous souhaitez que les offres d&#39;une catégorie particulière soient sélectionnées en priorité par le moteur d&#39;offres, par exemple pour mieux exposer un produit, vous pouvez augmenter leur poids pendant une période donnée grâce à un poids multiplicateur au niveau de la catégorie.

Pour créer une catégorie supplémentaire, procédez comme suit :

1. Positionnez-vous sur le dossier **[!UICONTROL Catalogue d&#39;offres]**.

   ![](assets/offer_cat_create_001.png)

1. Cliquez avec le bouton droit de la souris et sélectionner **[!UICONTROL Ajouter un dossier &quot;Catégorie d&#39;offres&quot;]** dans le menu contextuel.

   ![](assets/offer_cat_create_002.png)

1. Renommez la catégorie. Vous pourrez modifier le libellé ultérieurement via l&#39;onglet **[!UICONTROL Général]** de la catégorie.

   ![](assets/offer_cat_create_003.png)

   >[!NOTE]
   >
   >Répétez ces étapes pour créer autant de catégories que nécessaire.

   Par la suite, il vous est possible, selon vos besoins :

   * Assign eligibility dates from the **[!UICONTROL Eligibility]** tab.

      ![](assets/offer_cat_create_004.png)

   * Enter key words that may be used to select offers from within this category, using the **[!UICONTROL Themes]** field.

      ![](assets/offer_cat_create_005.png)

      >[!NOTE]
      >
      >Lors de l&#39;appel au moteur d&#39;offres, seule la partie du catalogue dont les thèmes ou les catégories correspondent aux paramètres est sélectionnée.

   * Temporarily &quot;boost&quot; the offer weight of a category for a given period via the **[!UICONTROL Multiplier weight]** field.

      ![](assets/offer_cat_create_006.png)

Un récapitulatif des règles d&#39;éligibilité est disponible sur le tableau de bord des offres faisant partie de la catégorie. Pour les visualiser, cliquez sur le lien **[!UICONTROL Planning et règles d&#39;éligibilité de l&#39;offre]**.

![](assets/offer_create_006.png)

