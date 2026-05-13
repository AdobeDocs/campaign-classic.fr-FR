---
product: campaign
title: Créer des catégories d'offres
description: Créer des catégories d'offres
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
exl-id: ed97a1b5-c870-4b67-98b6-16adc316fd46
TQID: https://experienceleague.adobe.com/NsHriPMpvkRFG2kEz4-wb5qFz1meeqkWcbA2EMdGbH4
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 292
ht-degree: 60%

---

# Créer des catégories d&#39;offres{#creating-offer-categories}



La création des catégories d&#39;offres ne peut avoir lieu que dans l&#39;environnement **[!UICONTROL En édition]**. Elles sont déployées automatiquement dans l&#39;environnement **[!UICONTROL En ligne]** (c&#39;est-à-dire mises à disposition) lorsque la ou les offres créées/modifiées qu&#39;elles contiennent sont validées. Par défaut, l&#39;environnement **[!UICONTROL En édition]** contient une catégorie pour recevoir toutes les offres. Il est possible de créer des sous-catégories pour ajouter une hiérarchie aux offres du catalogue.

Pour chaque catégorie, vous pouvez définir des dates d&#39;éligibilité, c&#39;est-à-dire une période au-delà de laquelle les offres contenues dans la catégorie peuvent ne plus être présentées à leur cible. Si vous souhaitez que les offres d&#39;une catégorie spécifique soient sélectionnées en priorité par le moteur d&#39;offres, afin de mieux exposer un produit par exemple, vous pouvez augmenter leur poids pour une période donnée en ajoutant un poids multiplicateur à la catégorie.

Pour créer une catégorie supplémentaire, procédez comme suit :

1. Positionnez-vous sur le dossier **[!UICONTROL Catalogue d&#39;offres]**.

   ![](assets/offer_cat_create_001.png)

1. Cliquez avec le bouton droit de la souris et sélectionnez **[!UICONTROL Créer un dossier « Catégorie d’offres »]** dans le menu contextuel.

   ![](assets/offer_cat_create_002.png)

1. Renommez la catégorie. Vous pourrez modifier le libellé ultérieurement via l&#39;onglet **[!UICONTROL Général]** de la catégorie.

   ![](assets/offer_cat_create_003.png)

   >[!NOTE]
   >
   >Répétez ces étapes pour créer autant de catégories que nécessaire.

   Par la suite, il vous est possible, selon vos besoins :

   * D&#39;attribuer des dates d&#39;éligibilité, depuis l&#39;onglet **[!UICONTROL Éligibilité]**.

     ![](assets/offer_cat_create_004.png)

   * D&#39;entrer des mots-clés qui pourront être utilisés pour sélectionner les offres de cette catégorie, depuis le champ **[!UICONTROL Thèmes]**.

     ![](assets/offer_cat_create_005.png)

     >[!NOTE]
     >
     >Lors de l&#39;appel au moteur d&#39;offres, seule la partie du catalogue dont les thèmes ou les catégories correspondent aux paramètres est sélectionnée.

   * &quot;Boostez&quot; temporairement le poids des offres de la catégorie pour une période donnée, depuis le champ **[!UICONTROL Poids multiplicateur]**.

     ![](assets/offer_cat_create_006.png)

Un récapitulatif des règles d&#39;éligibilité est disponible sur le tableau de bord des offres faisant partie de la catégorie. Pour les visualiser, cliquez sur le lien **[!UICONTROL Planning et règles d&#39;éligibilité de l&#39;offre]**.

![](assets/offer_create_006.png)
