---
title: Créer une offre
seo-title: Créer une offre
description: Créer une offre
seo-description: null
page-status-flag: never-activated
uuid: 9e8b0351-e2a5-4043-be86-e275d2f849ea
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
discoiquuid: 010c88f4-9444-448f-bb7b-7191517d2e23
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 215e4d1ca78938b38b53cae0357612deebf7727b

---


# Créer une offre{#creating-an-offer}

## Créer l&#39;offre {#creating-the-offer}

Pour créer une offre, procédez comme suit :

1. Go to the **[!UICONTROL Campaigns]** universe and click the **[!UICONTROL Offers]** link.

   ![](assets/offer_create_001.png)

1. Cliquez sur le **[!UICONTROL Create]** bouton.

   ![](assets/offer_create_005.png)

1. Modifiez le libellé et sélectionnez la catégorie à laquelle doit appartenir l&#39;offre.

   ![](assets/offer_create_002.png)

1. Click **[!UICONTROL Save]** to create the offer.

   ![](assets/offer_create_003.png)

   L&#39;offre est disponible dans la plateforme et son contenu peut être paramétré.

   ![](assets/offer_create_004.png)

## Paramétrer l&#39;éligibilité d&#39;une offre {#configuring-offer-eligibility}

In the **[!UICONTROL Eligibility]** tab, define the period the offer will be valid for and can be presented, the filters to apply to the target and the offer weight.

### Définir la période d&#39;éligibilité d&#39;une offre {#defining-the-eligibility-period-of-an-offer}

Pour définir la période d&#39;éligibilité de l&#39;offre, utilisez les listes déroulantes et sélectionnez une date de début et de fin dans le calendrier.

![](assets/offer_eligibility_create_002.png)

En dehors de ces dates, l&#39;offre ne sera pas sélectionnée par le moteur d&#39;Interaction. Si vous avez également paramétré des dates d&#39;éligibilité au niveau de la catégorie de l&#39;offre, la période la plus restrictive s&#39;appliquera.

### Filtres sur la cible {#filters-on-the-target}

Vous pouvez appliquer des filtres sur la cible de l&#39;offre.

Pour ce faire, cliquez sur le **[!UICONTROL Edit query]** lien et sélectionnez le filtre à appliquer. (Consultez [cette section](../../platform/using/steps-to-create-a-query.md#step-4---filter-data)).

![](assets/offer_eligibility_create_003.png)

Si des filtres prédéfinis ont déjà été créés, vous pouvez les sélectionner dans la liste des filtres utilisateur. For more on this, refer to [Creating predefined filters](../../interaction/using/creating-predefined-filters.md).

![](assets/offer_eligibility_create_004.png)

### Poids de l&#39;offre {#offer-weight}

Pour permettre au moteur d&#39;arbitrer entre plusieurs offres auxquelles la personne ciblée serait éligible, vous devez attribuer un ou plusieurs poids à l&#39;offre. Vous pouvez également appliquer des filtres sur la cible si nécessaire ou restreindre l&#39;emplacement auquel doit s&#39;appliquer le poids. Une offre dont le poids est plus important sera préférée à une offre avec un poids moindre.

Vous pouvez paramétrer plusieurs poids pour une même offre, notamment en fonction d&#39;une période, d&#39;une cible ou encore d&#39;un emplacement.

Par exemple, une offre peut avoir un poids A pour les contacts âgés de 18 à 25 ans et un poids B pour les contacts plus âgés. Ou, si une offre est éligible tout l&#39;été, elle peut avoir un poids A au mois de juillet, et un poids B au mois d&#39;août.

>[!NOTE]
>
>Le poids affecté peut être temporairement modifié en fonction des paramètres de la catégorie à laquelle appartient l’offre. For more on this, refer to [Creating offer categories](../../interaction/using/creating-offer-categories.md).

Pour créer un poids dans une offre, procédez comme suit :

1. Clics **[!UICONTROL Add]**.

   ![](assets/offer_weight_create_001.png)

1. Modifiez le libellé et attribuez un poids. Par défaut, celui-ci est de 1.

   ![](assets/offer_weight_create_006.png)

   >[!CAUTION]
   >
   >Si aucun poids n&#39;est renseigné (0), la cible est considérée comme inéligible à l&#39;offre.

1. Définissez des dates d&#39;éligibilité si vous souhaitez que le poids ne s&#39;applique que pendant une période donnée.

   ![](assets/offer_weight_create_002.png)

1. Si besoin est, choisissez un emplacement auquel se limitera le poids.

   ![](assets/offer_weight_create_003.png)

1. Appliquez un filtre sur la cible.

   ![](assets/offer_weight_create_004.png)

1. Cliquez sur **[!UICONTROL OK]** pour enregistrer le poids.

   ![](assets/offer_weight_create_005.png)

   >[!NOTE]
   >
   >Si un contact est éligible à plusieurs poids pour une offre sélectionnée, le moteur garde le meilleur poids (le plus grand). Lors d&#39;un appel au moteur, une offre ne sort qu&#39;une seule fois maximum par contact.

### Résumé des règles d&#39;éligibilité d&#39;une offre {#a-summary-of-offer-eligibility-rules}

Une fois le paramétrage terminé, un résumé des règles d&#39;éligibilité est disponible dans le tableau de bord de l&#39;offre.

Pour l’afficher, cliquez sur le **[!UICONTROL Schedule and eligibility rules]** lien.

![](assets/offer_eligibility_create_005.png)

## Créer le contenu de l&#39;offre {#creating-the-offer-content}

1. Click the **[!UICONTROL Edit]** tab, then click the **[!UICONTROL Content]** tab.

   ![](assets/offer_content_create_001.png)

1. Complétez les différents champs du contenu de l&#39;offre.

   * **[!UICONTROL Title]** : Indiquez le titre que vous souhaitez faire apparaître dans votre offre. Avertissement : il ne s’agit pas du libellé de l’offre, défini dans l’ **[!UICONTROL General]** onglet.
   * **[!UICONTROL Destination URL]** : spécifiez l’URL de votre offre. Pour être traité correctement, il doit commencer par &quot;http://&quot; ou &quot;https://&quot;.
   * **[!UICONTROL Image URL]** : spécifiez une URL ou un chemin d’accès à l’image de votre offre.
   * **[!UICONTROL HTML content]** / **[!UICONTROL Text content]** : entrez le corps de votre offre dans l’onglet de votre choix. Pour générer le suivi, il **[!UICONTROL HTML content]** doit être composé d’éléments HTML pouvant être inclus dans un élément `<div>` de type. Par exemple, le résultat d’un `<table>` élément dans la page HTML sera le suivant :

   ```
      <div> 
       <table>
        <tr>
         <th>Month</th>
         <th>Savings</th>   
        </tr>   
        <tr>    
         <td>January</td>
         <td>$100</td>   
        </tr> 
       </table> 
      </div>
   ```

   La définition de l’URL d’acceptation est présentée dans la section [Configuration de l’état lorsque la proposition est acceptée](../../interaction/using/creating-offer-spaces.md#configuring-the-status-when-the-proposition-is-accepted) .

   ![](assets/offer_content_create_002.png)

   Pour rechercher les champs obligatoires tels qu’ils ont été définis lors de la configuration de l’espace d’offre, cliquez sur le **[!UICONTROL Content definitions]** lien pour afficher la liste. For more on this, refer to [Creating offer spaces](../../interaction/using/creating-offer-spaces.md).

   ![](assets/offer_content_create_003.png)

   Dans notre exemple, l&#39;offre doit être constituée d&#39;un titre, d&#39;une image, d&#39;un contenu en HTML et d&#39;une URL de destination.

## Prévisualiser l&#39;offre {#previewing-the-offer}

Dès lors que le contenu de votre offre a été paramétré, vous pouvez prévisualiser l&#39;offre telle qu&#39;elle apparaîtra pour son destinataire. Pour cela :

1.  Cliquez sur l’ **[!UICONTROL Preview]** onglet.

   ![](assets/offer_preview_create_001.png)

1. Sélectionnez la représentation de l&#39;offre que vous souhaitez voir.

   ![](assets/offer_preview_create_002.png)

1. Si vous avez personnalisé le contenu de l&#39;offre, sélectionnez la cible de l&#39;offre afin de visualiser la personnalisation.

   ![](assets/offer_preview_create_003.png)

## Créer une hypothèse sur une offre {#creating-a-hypothesis-on-an-offer}

Vous avez la possibilité de créer des hypothèses sur vos propositions d&#39;offres. Cela vous permet de déterminer l&#39;impact de vos offres sur les ventes réalisées pour le produit concerné.

>[!NOTE]
>
>Ces hypothèses sont réalisées à l&#39;aide du module Response Manager. Vérifiez votre contrat de licence.

Hypotheses carried out on an offer proposition are referenced in their **[!UICONTROL Measure]** tab.

La création des hypothèses est expliquée dans le détail sur [cette page](../../campaign/using/about-response-manager.md).

![](assets/offer_hypothesis_001.png)

