---
title: Offres sur canal sortant
seo-title: Offres sur canal sortant
description: Offres sur canal sortant
seo-description: null
page-status-flag: never-activated
uuid: a8a7ce5f-0d18-47f2-b258-34b9471de769
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: case-study
discoiquuid: 3bd113c3-da67-4f4f-aa40-f4c7860a8569
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 215e4d1ca78938b38b53cae0357612deebf7727b

---


# Offres sur canal sortant{#offers-on-an-outbound-channel}

## Diffusion d&#39;une offre par email {#email-offer-delivery}

Dans votre base, vous disposez d&#39;une catégorie d&#39;offres de voyages à destination de l&#39;Afrique. L&#39;éligibilité, les contextes et les représentations de chaque offre ont été paramétrés. Vous allez à présent créer une campagne pour présenter vos offres par email.

1. Créez votre opération marketing et votre workflow de ciblage.

   ![](assets/offer_delivery_example_001.png)

1. Edit the email delivery and click the **[!UICONTROL Offers]** icon.

   ![](assets/offer_delivery_example_002.png)

1. Sélectionnez l&#39;emplacement Email de votre environnement d&#39;offres correspondant aux voyages.

   ![](assets/offer_delivery_example_003.png)

1. Choisissez la catégorie dans laquelle se trouvent les offres de voyages pour l&#39;Afrique.

   ![](assets/offer_delivery_example_004.png)

1. Choisissez de présenter deux offres dans votre diffusion.

   ![](assets/offer_delivery_example_005.png)

1. Fermez la fenêtre de gestion des offres et créez le contenu de votre diffusion.

   ![](assets/offer_delivery_example_006.png)

1. Cliquez sur le champ de fusion pour insérer une première proposition d&#39;offre et choisissez la Fonction de rendu HTML.

   ![](assets/offer_delivery_example_007.png)

1. Insérez la deuxième proposition d&#39;offre.

   ![](assets/offer_delivery_example_008.png)

1. Click **[!UICONTROL Preview]** to preview your offers in the delivery then select a recipient to preview the offers as they will receive them.

   ![](assets/offer_delivery_example_009.png)

1. Enregistrez votre diffusion et lancez le workflow de ciblage.
1. Open your delivery and click the **[!UICONTROL Audit]** tab of your delivery: you can see that the offer engine has selected the propositions to be made from the various offers in the catalog.

   ![](assets/offer_delivery_example_010.png)

## Effectuer une simulation d&#39;offres {#perform-an-offer-simulation}

1. Dans l’ **[!UICONTROL Profiles and Targets]** univers, cliquez sur le **[!UICONTROL Simulations]** lien, puis sur le **[!UICONTROL Create]** bouton.

   ![](assets/offer_simulation_001.png)

1. Choisissez un libellé et spécifiez des paramètres d&#39;exécution si besoin est.

   ![](assets/offer_simulation_example_002.png)

1. Enregistrez la simulation. Celle-ci s&#39;ouvre alors dans un nouvel onglet.

   ![](assets/offer_simulation_example_003.png)

1. Cliquez sur l’ **[!UICONTROL Edit]** onglet, puis **[!UICONTROL Scope]**.

   ![](assets/offer_simulation_example_004.png)

1. Sélectionnez la catégorie sur laquelle vous souhaitez simuler vos offres.

   ![](assets/offer_simulation_example_005.png)

1. Sélectionnez l&#39;emplacement sur lequel doit porter la simulation.

   ![](assets/offer_simulation_example_006.png)

1. Entrez des dates de validité. Vous devez obligatoirement spécifier au moins une date de début. Ceci permet au moteur d&#39;offres de filtrer les offres et de choisir celles qui sont valides à la date donnée.
1. Si nécessaire, spécifiez un ou plusieurs thèmes pour limiter le nombre d&#39;offres à celles ayant ce mot-clé dans leurs paramètres.

   Dans notre exemple, la catégorie **Produits financiers** contient deux sous-catégories ayant chacune un thème distinct. La simulation portera seulement sur les offres de la catégorie dont le thème d&#39;application est **Clients &lt; 1 an**.

   ![](assets/offer_simulation_example_007.png)

1. Sélectionnez les destinataires à cibler.

   ![](assets/offer_simulation_example_008.png)

1. Paramétrez le nombre d&#39;offres que vous souhaitez proposer à chaque destinataire.

   Dans notre exemple, le moteur d&#39;offres va sélectionner pour chaque destinataire les 3 offres dont le poids est le plus élevé.

   ![](assets/offer_simulation_example_009.png)

1. Save your settings, then click **[!UICONTROL Start]** in the **[!UICONTROL Dashboard]** tab to run the simulation.

   ![](assets/offer_simulation_example_010.png)

1. Once the simulation is finished, consult the **[!UICONTROL Results]** for a detailed breakdown of propositions per offer.

   Dans notre exemple, le moteur d&#39;offres a bien basé la répartition des offres sur une base de 3 propositions.

   ![](assets/offer_simulation_example_011.png)

1. Affichez la liste **[!UICONTROL Breakdown of offers by rank]** des offres sélectionnées par le moteur d’offre.

   ![](assets/offer_simulation_example_012.png)

1. If necessary, you can change the scope settings and run the simulation again by clicking **[!UICONTROL Start simulation]**.

   ![](assets/offer_simulation_example_010.png)

1. Pour conserver les données des simulations, utilisez les fonctions d&#39;historisation ou d&#39;export disponibles dans le rapport.

   ![](assets/offer_simulation_example_013.png)

