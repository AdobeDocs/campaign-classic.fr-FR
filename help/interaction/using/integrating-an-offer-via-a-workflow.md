---
product: campaign
title: Intégration d'une offre via un workflow
description: Intégration d'une offre via un workflow
feature: Interaction, Offers, Workflows
audience: interaction
content-type: reference
topic-tags: delivering-an-offer
exl-id: 33d318f3-1eb4-4c74-8c20-8b9f0442c7c3
TQID: https://experienceleague.adobe.com/mAyeOK618LvVCdtRqLykUECmgWZce8bKoMiT-WIOe1Q
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: b6fcaf36-3bc4-4604-94f3-81b5d3f41ecf
subfeature_v2: []
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 1128
ht-degree: 80%

---

# Intégrer une offre via un workflow{#integrating-an-offer-via-a-workflow}



En dehors de l&#39;activité de diffusion elle-même, plusieurs activités des workflows vous permettent de définir la présentation d&#39;offres :

* Composition de diffusion
* Enrichissement
* Moteur d’offres
* Offres par cellule

## Composition de diffusion {#delivery-outline}

L&#39;activité de composition de diffusion, disponible dans les workflows de campagne, vous permet de présenter des offres référencées dans une composition de diffusion de la campagne en cours.

1. Dans un workflow, placez une activité de composition de diffusion avant une activité de diffusion.
1. Dans l&#39;activité de composition, définissez la composition que vous souhaitez utiliser.

   Pour plus d’informations sur la définition des compositions de diffusion, consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-assets#delivery-outlines.html?lang=fr){target="_blank"}.

1. Complétez les champs disponibles en fonction de votre diffusion.
1. Deux cas se présentent :

   * Si vous souhaitez appeler le moteur d&#39;offres, cochez la case **[!UICONTROL Limiter le nombre de propositions sélectionnées]**. Indiquez l&#39;emplacement et le nombre de propositions qui seront présentées dans la diffusion.

     Les poids et règles d&#39;éligibilité des offres seront pris en compte par le moteur d&#39;offres.

   * Si vous ne cochez pas la case, toutes les offres de la composition de diffusion seront présentées, sans appel au moteur d&#39;offres.

   >[!NOTE]
   >
   >La prévisualisation prend en compte le nombre d’offres spécifié dans la diffusion. Lors de l&#39;exécution d&#39;un workflow, c&#39;est le nombre spécifié dans la composition de diffusion qui est pris en compte.

   ![](assets/int_compo_offre_wf1.png)

## Enrichissement {#enrichment}

L’activité d’enrichissement vous permet d’ajouter des offres ou des liens vers des offres pour les personnes destinataires d’une diffusion.

>[!NOTE]
>
>Pour plus d’informations sur l’activité d’enrichissement, consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/enrichment.html?lang=fr){target="_blank"}.

Vous pouvez par exemple enrichir les données d&#39;une requête sur les destinataires, avant une diffusion.

![](assets/int_enrichment_offer1.png)

Deux méthodes permettent de définir des propositions d&#39;offre.

* En définissant une offre ou un appel au moteur d&#39;offres.
* En référençant un lien vers une offre.

### Définir une offre ou un appel au moteur {#specifying-an-offer-or-a-call-to-the-offer-engine}

Après avoir configuré votre requête (voir la [documentation de Campaign v8](https://experienceleague.adobe.com/fr/docs/campaign/automation/workflows/wf-activities/targeting-activities/query.html?lang=fr){target="_blank"}) :

1. Placez et ouvrez une activité d’enrichissement.
1. Dans l&#39;onglet **[!UICONTROL Enrichissement]**, sélectionnez **[!UICONTROL Ajouter des données]**.
1. Sélectionnez **[!UICONTROL Une proposition d&#39;offre]** dans les types de données à ajouter.

   ![](assets/int_enrichment_offer2.png)

1. Indiquez un identifiant ainsi qu&#39;un libellé pour la proposition qui sera ajoutée.
1. Définissez la sélection d’offres. Deux options sont possibles :

   * **[!UICONTROL Rechercher la meilleure offre dans une catégorie]** : cochez cette option et définissez les paramètres de l&#39;appel au moteur d&#39;offres (emplacement, catégorie ou thème(s), date de contact, nombre d&#39;offres à conserver). Le moteur calculera automatiquement la ou les offres à ajouter en fonction de ces paramètres. Nous vous recommandons de renseigner soit le champ **[!UICONTROL Catégorie]**, soit le champ le **[!UICONTROL Thème]**, plutôt que les deux à la fois.

     ![](assets/int_enrichment_offer3.png)

   * **[!UICONTROL Une offre prédéfinie]** : cochez cette option et définissez un emplacement, une offre précise, ainsi qu&#39;une date de contact afin de directement paramétrer l&#39;offre que vous souhaitez ajouter, sans appeler le moteur d&#39;offres.

     ![](assets/int_enrichment_offer4.png)

1. Paramétrez ensuite une activité de diffusion correspondant au canal de votre choix. Pour plus d’informations, voir la section [Insérer une proposition d’offres dans une diffusion](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery).

   >[!NOTE]
   >
   >Le nombre de propositions disponibles pour la prévisualisation dépend du paramétrage réalisé dans l’activité d’enrichissement et non d’un éventuel paramétrage directement dans la diffusion.

### En référençant un lien vers une offre {#referencing-a-link-to-an-offer}

Vous avez également la possibilité de référencer un lien vers une offre dans une activité d’enrichissement.

Pour cela :

1. Dans l&#39;onglet **[!UICONTROL Enrichissement]** de l&#39;activité, sélectionnez **[!UICONTROL Ajouter des données]**.
1. Dans la fenêtre de sélection du type de données à ajouter, choisissez **[!UICONTROL Un lien]**.
1. Sélectionnez le type de lien que vous souhaitez établir ainsi que sa cible. Dans ce cas, la cible est le schéma d&#39;offre.

   ![](assets/int_enrichment_link1.png)

1. Indiquez la jointure entre les données de la table entrante dans l&#39;activité d&#39;enrichissement (ici la table des destinataires) et la table des offres. Vous pouvez, par exemple, lier un code d’offre à un destinataire.

   ![](assets/int_enrichment_link2.png)

1. Paramétrez ensuite une activité de diffusion correspondant au canal de votre choix. Pour plus d’informations, voir la section [Insérer une proposition d’offres dans une diffusion](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery).

   >[!NOTE]
   >
   >Le nombre de propositions disponibles pour la prévisualisation dépend du paramétrage réalisé dans la diffusion.

### Stocker le rang et le poids des offres {#storing-offer-rankings-and-weights}

Par défaut, lorsque l&#39;activité d&#39;**enrichissement** est utilisée pour diffuser des offres, leur rang ainsi que leur poids ne sont pas stockés dans la table des propositions.

>[!NOTE]
>
>Rappel : L&#39;activité **[!UICONTROL Moteur d&#39;offres]** stocke bien ces informations par défaut.

Cependant, il est possible de stocker ces informations de la manière suivante :

1. Créez un appel au moteur d’offre dans une activité d’enrichissement placée après une requête et avant une activité de diffusion. Pour plus d&#39;informations, consultez la section [Définir une offre ou un appel au moteur](../../interaction/using/integrating-an-offer-via-a-workflow.md#specifying-an-offer-or-a-call-to-the-offer-engine).
1. Dans la fenêtre principale de l&#39;activité, sélectionnez **[!UICONTROL Editer les données additionnelles]**.

   ![](assets/ita_enrichment_rankweight_1.png)

1. Ajoutez les colonnes **[!UICONTROL @rank]** pour le rang et **[!UICONTROL @weight]** pour le poids des offres.

   ![](assets/ita_enrichment_rankweight_2.png)

1. Validez votre ajout et enregistrez votre workflow.

La diffusion stocke automatiquement le rang et le poids des offres. Ces informations sont visibles dans l’onglet **[!UICONTROL Offres]** de la diffusion.

## Moteur d’offres {#offer-engine}

L&#39;activité **[!UICONTROL Moteur d&#39;offres]** vous permet également de définir un appel au moteur d&#39;offres en amont d&#39;une diffusion.

Cette activité fonctionne sur le même principe que l’activité d’enrichissement avec un appel au moteur, en enrichissant les données de la population entrante avec une offre calculée par le moteur, avant une diffusion.

![](assets/int_offerengine_activity2.png)

Après avoir paramétré votre requête (voir le [Guide des Workflows](../../workflow/using/query.md)) :

1. Placez et ouvrez une activité **[!UICONTROL Moteur d&#39;offres]**.
1. Renseignez les différents champs disponibles afin de définir les paramètres de l&#39;appel au moteur d&#39;offres (emplacement, catégorie ou thème(s), date de contact, nombre d&#39;offres à conserver). Le moteur calculera automatiquement la ou les offres à ajouter en fonction de ces paramètres.

   >[!NOTE]
   >
   >Attention, si vous utilisez cette activité, seules les propositions utilisées dans la diffusion sont stockées.

   ![](assets/int_offerengine_activity1.png)

1. Paramétrez ensuite une activité de diffusion correspondant au canal de votre choix. Pour plus d’informations, voir la section [Insérer une proposition d’offres dans une diffusion](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery).

## Offres par cellule {#offers-by-cell}

L&#39;activité **[!UICONTROL Offres par cellules]** vous permet de répartir la population entrante (par exemple issue d&#39;une requête) en plusieurs segments, et de définir une offre à proposer pour chacun de ces segments.

Pour cela :

1. Placez l&#39;activité **[!UICONTROL Offres par cellules]** après avoir défini la population cible, puis ouvrez-là.
1. Dans l&#39;onglet **[!UICONTROL Général]**, sélectionnez l&#39;emplacement sur lequel vous souhaitez proposer les offres.
1. Dans l&#39;onglet **[!UICONTROL Cellules]**, définissez les différents sous-ensembles via le bouton **[!UICONTROL Ajouter]** :

   * Définissez la population du sous-ensemble grâce aux règles de filtrage et de limitation disponibles.
   * Sélectionnez ensuite l&#39;offre que vous souhaitez présenter au sous-ensemble. Les offres disponibles sont celles qui sont éligibles dans l’environnement d’offres qui a été sélectionné à l’étape précédente.

     ![](assets/int_offer_per_cell1.png)

1. Paramétrez ensuite une activité de diffusion correspondant au canal de votre choix. Pour plus d’informations, voir la section [Insérer une proposition d’offres dans une diffusion](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery).
