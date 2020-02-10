---
title: Intégrer une offre via un workflow
seo-title: Intégrer une offre via un workflow
description: Intégrer une offre via un workflow
seo-description: null
page-status-flag: never-activated
uuid: 57c4d4e0-6594-46f0-b9ce-2c689fb2eaa2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: delivering-an-offer
discoiquuid: 6e27caea-1f1a-457d-bdec-1f93a12b01cf
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 67dce820b7a90163032ee72263a9dd23b521ea69

---


# Intégrer une offre via un workflow{#integrating-an-offer-via-a-workflow}

En dehors de l&#39;activité de diffusion elle-même, plusieurs activités des workflows vous permettent de définir la présentation d&#39;offres :

* Composition de diffusion
* Enrichissement
* Moteur d&#39;offres
* Offres par cellule

## Composition de diffusion {#delivery-outline}

L&#39;activité de composition de diffusion, disponible dans les workflows de campagne, vous permet de présenter des offres référencées dans une composition de diffusion de la campagne en cours.

1. Dans un workflow, placez une activité de composition de diffusion avant une activité de diffusion.
1. Dans l&#39;activité de composition, définissez la composition que vous souhaitez utiliser.

   Pour plus d&#39;informations sur la définition des compositions de diffusion, consultez le guide [Campaign - MRM](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

1. Complétez les champs disponibles en fonction de votre diffusion.
1. Deux cas se présentent :

   * Si vous souhaitez appeler le moteur d’offre, cochez la **[!UICONTROL Restrict the number of propositions selected]** case. Spécifiez l’espace d’offre et le nombre de propositions qui seront présentées dans la diffusion.

      Les poids et règles d&#39;éligibilité des offres seront pris en compte par le moteur d&#39;offres.

   * Si vous ne cochez pas la case, toutes les offres de la composition de diffusion seront présentées, sans appel au moteur d&#39;offres.
   >[!NOTE]
   >
   >La prévisualisation prend en compte le nombre d&#39;offres défini dans la diffusion. Lors de l&#39;exécution du workflow, c&#39;est le nombre défini dans la composition de diffusion qui est pris en compte.

   ![](assets/int_compo_offre_wf1.png)

## Enrichissement {#enrichment}

L&#39;activité d&#39;enrichissement vous permet d&#39;ajouter des offres ou des liens vers des offres pour les destinataires d&#39;une diffusion.

>[!NOTE]
>
>Pour plus d&#39;informations sur l&#39;activité d&#39;enrichissement, consultez la documentation dédiée dans le [Guide des Workflows](../../workflow/using/enrichment.md).

Vous pouvez par exemple enrichir les données d&#39;une requête sur les destinataires, avant une diffusion.

![](assets/int_enrichment_offer1.png)

Deux méthodes permettent de définir des propositions d&#39;offre.

* En définissant une offre ou un appel au moteur d&#39;offres.
* En référençant un lien vers une offre.

### Définir une offre ou un appel au moteur {#specifying-an-offer-or-a-call-to-the-offer-engine}

After configuring your query (refer to the [Workflows guide](../../workflow/using/query.md)):

1. Placez et ouvrez une activité d&#39;enrichissement.
1. Dans l’ **[!UICONTROL Enrichment]** onglet, sélectionnez **[!UICONTROL Add data]**.
1. Sélectionnez **[!UICONTROL An offer proposition]** les types de données à ajouter.

   ![](assets/int_enrichment_offer2.png)

1. Indiquez un identifiant ainsi qu&#39;un libellé pour la proposition qui sera ajoutée.
1. Définissez la sélection de l&#39;offre. Deux options sont possibles :

   * **[!UICONTROL Search for the best offer in a category]** : cochez cette option et spécifiez les paramètres d’appel du moteur d’offre (espace d’offre, catégorie ou thème(s), date de contact, nombre d’offres à conserver). Le moteur calculera automatiquement les offres à ajouter en fonction de ces paramètres. Nous vous recommandons de remplir le champ **[!UICONTROL Category]** ou le **[!UICONTROL Theme]** champ, plutôt que les deux en même temps.

      ![](assets/int_enrichment_offer3.png)

   * **[!UICONTROL A predefined offer]** : cochez cette option et spécifiez un espace d’offre, une offre spécifique et une date de contact pour configurer directement l’offre que vous souhaitez ajouter, sans appeler le moteur d’offre.

      ![](assets/int_enrichment_offer4.png)

1. Configurez ensuite une activité de diffusion correspondant au canal choisi. Pour plus d’informations, reportez-vous à la section [Insertion d’une proposition d’offre dans une section de remise](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery) .

   >[!NOTE]
   >
   >Le nombre de propositions disponibles pour la prévisualisation dépend du paramétrage réalisé dans l&#39;activité d&#39;enrichissement et non d&#39;un éventuel paramétrage directement dans la diffusion.

### Référencer un lien vers une offre {#referencing-a-link-to-an-offer}

Vous avez également la possibilité de référencer un lien vers une offre dans une activité d&#39;enrichissement.

Pour cela :

1. Sélectionnez **[!UICONTROL Add data]** dans l’ **[!UICONTROL Enrichment]** onglet de l’activité.
1. In the window where you choose the type of data to add, select **[!UICONTROL A link]**.
1. Sélectionnez le type du lien que vous souhaitez établir ainsi que sa cible. Dans le cas présent, la cible est le schéma des offres.

   ![](assets/int_enrichment_link1.png)

1. Définissez la jointure entre les données de la table entrante dans l&#39;activité d&#39;enrichissement (ici la table des destinataires) et la table des offres. Vous pouvez par exemple associer un code offre à un destinataire.

   ![](assets/int_enrichment_link2.png)

1. Configurez ensuite une activité de diffusion correspondant au canal choisi. Pour plus d’informations, reportez-vous à la section [Insertion d’une proposition d’offre dans une section de remise](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery) .

   >[!NOTE]
   >
   >Le nombre de propositions disponibles pour la prévisualisation dépend du paramétrage réalisé dans la diffusion.

### Stocker le rang et le poids des offres {#storing-offer-rankings-and-weights}

Par défaut, lorsque l&#39;activité d&#39;**enrichissement** est utilisée pour diffuser des offres, leur rang ainsi que leur poids ne sont pas stockés dans la table des propositions.

>[!NOTE]
>
>Remember: The **[!UICONTROL Offer engine]** activity does store this information by default.

Cependant, il est possible de stocker ces informations de la manière suivante :

1. Créez un appel au moteur d’offre dans une activité d’enrichissement placée après une requête et avant une activité de remise. Reportez-vous à la section [Spécification d’une offre ou d’un appel au moteur](../../interaction/using/integrating-an-offer-via-a-workflow.md#specifying-an-offer-or-a-call-to-the-offer-engine) d’offre.
1. Dans la fenêtre principale de l’activité, sélectionnez **[!UICONTROL Edit additional data...]**.

   ![](assets/ita_enrichment_rankweight_1.png)

1. Add the **[!UICONTROL @rank]** columns for the ranking and **[!UICONTROL @weight]** for the offer weight.

   ![](assets/ita_enrichment_rankweight_2.png)

1. Validez votre ajout et enregistrez votre workflow.

La diffusion stocke automatiquement le classement et le poids des offres. Ces informations sont visibles dans l’ **[!UICONTROL Offers]** onglet de la remise.

## Moteur d&#39;offres {#offer-engine}

The **[!UICONTROL Offer engine]** activity also lets you specify a call to the offer engine prior to the delivery.

Cette activité fonctionne sur le même principe que l&#39;activité d&#39;enrichissement avec un appel au moteur, en enrichissant les données de la population entrante avec une offre calculée par le moteur, avant une diffusion.

![](assets/int_offerengine_activity2.png)

After configuring your query (refer to the [Workflows guide](../../workflow/using/query.md)):

1. Add and open an **[!UICONTROL Offer engine]** activity.
1. Renseignez les différents champs disponibles afin de définir les paramètres d&#39;appel au moteur (emplacement, catégorie ou thème(s), date de contact, nombre d&#39;offres à conserver). Le moteur calculera automatiquement la ou les offres à ajouter en fonction de ces paramètres.

   >[!NOTE]
   >
   >Attention, si vous utilisez cette activité, seules les propositions utilisées dans la diffusion sont stockées.

   ![](assets/int_offerengine_activity1.png)

1. Configurez ensuite une activité de diffusion correspondant au canal choisi. Pour plus d’informations, reportez-vous à la section [Insertion d’une proposition d’offre dans une section de remise](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery) .

## Offres par cellule {#offers-by-cell}

The **[!UICONTROL Offers by cell]** activity lets you distribute the inbound population (from a query for example) into several segments and to specify an offer to present for each of these segments.

Pour cela :

1. Add the **[!UICONTROL Offers by cell]** activity once you have specified the target population, then open it.
1. In the **[!UICONTROL General]** tab, select the offer space on which you want to present the offers.
1. In the **[!UICONTROL Cells]** tab, specify the different sub-sets using the **[!UICONTROL Add]** button:

   * Définissez la population du sous-ensemble grâce aux règles de filtrage et de limitation disponibles.
   * Sélectionnez ensuite l&#39;offre que vous souhaitez proposer au sous-ensemble. Les offres disponibles sont celles éligibles sur l&#39;emplacement sélectionné à l&#39;étape précédente.

      ![](assets/int_offer_per_cell1.png)

1. Configurez ensuite une activité de diffusion correspondant au canal choisi. Pour plus d’informations, reportez-vous à la section [Insertion d’une proposition d’offre dans une section de remise](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery) .

