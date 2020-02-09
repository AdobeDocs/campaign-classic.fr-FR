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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Créer des catégories d&#39;offres{#creating-offer-categories}

La création de catégories d’offres ne peut avoir lieu que dans l’ **[!UICONTROL Design]** environnement. Ils sont déployés automatiquement dans l’ **[!UICONTROL Live]** environnement (c.-à-d. rendus disponibles) lorsque les offres créées/modifiées qu’ils contiennent sont approuvées. Par défaut, l’ **[!UICONTROL Design]** environnement contient une catégorie pour recevoir toutes les offres. Vous pouvez créer des sous-catégories pour ajouter une hiérarchie aux offres de catalogue.

Pour chaque catégorie il est possible de définir des dates d&#39;éligibilité, soit une période au-delà de laquelle les offres contenues dans la catégorie ne pourront plus être présentées à leur cible. Si vous souhaitez que les offres d&#39;une catégorie particulière soient sélectionnées en priorité par le moteur d&#39;offres, par exemple pour mieux exposer un produit, vous pouvez augmenter leur poids pendant une période donnée grâce à un poids multiplicateur au niveau de la catégorie.

Pour créer une catégorie supplémentaire, procédez comme suit :

1. Accédez au **[!UICONTROL Offer catalog]** dossier.

   ![](assets/offer_cat_create_001.png)

1. Cliquez avec le bouton droit de la souris et sélectionnez-la **[!UICONTROL Create a new "Offer category" folder]** dans la liste déroulante.

   ![](assets/offer_cat_create_002.png)

1. Attribuez un nouveau nom à la catégorie. Vous pouvez modifier le libellé ultérieurement à l’aide de l’ **[!UICONTROL General]** onglet.

   ![](assets/offer_cat_create_003.png)

   >[!NOTE]
   >
   >Répétez ces étapes pour créer autant de catégories que nécessaire.

   Par la suite, il vous est possible, selon vos besoins :

   * assign eligibility dates from the **[!UICONTROL Eligibility]** tab.

      ![](assets/offer_cat_create_004.png)

   * enter key words that may be used to select offers from within this category, using the **[!UICONTROL Themes]** field.

      ![](assets/offer_cat_create_005.png)

      >[!NOTE]
      >
      >Lors de l&#39;appel au moteur d&#39;offres, seule la partie du catalogue dont les thèmes ou les catégories correspondent aux paramètres est sélectionnée.

   * You can temporarily &quot;boost&quot; the offer weight of a category for a given period via the **[!UICONTROL Multiplier weight]** field.

      ![](assets/offer_cat_create_006.png)

Un résumé des règles d’éligibilité est disponible sur le tableau de bord des offres incluses dans la catégorie. Pour les afficher, cliquez sur le **[!UICONTROL Schedule and eligibility rules of the offer]** lien.

![](assets/offer_create_006.png)

