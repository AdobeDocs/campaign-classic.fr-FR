---
title: A propos de la gestion de la réaction
seo-title: A propos de la gestion de la réaction
description: A propos de la gestion de la réaction
seo-description: null
page-status-flag: never-activated
uuid: 3087a96d-50fb-488a-9b76-70eb5c67deed
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: response-manager
discoiquuid: a4669fee-4512-455f-b495-ebd5a0746b76
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# A propos de la gestion de la réaction{#about-response-manager}

## Objectifs {#objectives}

Adobe Campaign propose une application de gestion de la réaction (Response Manager), qui permet de mesurer le succès et la rentabilité d&#39;une campagne marketing ou d&#39;une proposition d&#39;offre, quel que soit le canal de communication utilisé (email, mobile, téléphone, courrier, fax, agence, etc.).

## Concept d&#39;hypothèse {#hypothesis-concept}

Afin de déduire le comportement des personnes ciblées suite à la réception d&#39;une offre ou d&#39;une diffusion, des hypothèses peuvent être paramétrées sur une période donnée à partir de la date de contact. Ces hypothèses sont basées sur une table des **transactions** qui enregistre les achats et qui contient également le détail de ces achats.

Les hypothèses sont délimitées dans le temps et peuvent être réalisées sur une population témoin que l&#39;on comparera à la population ciblée. Les résultats de l&#39;hypothèse sont donnés par des **indicateurs** qui sont automatiquement mis à jour lorsque le calcul est terminé. Le ROI associé aux hypothèses sera pris en compte dans les rapports de campagne.

D&#39;autre part, les **rapports** standards fournis avec le Response Manager permettent de synthétiser les informations relatives à l&#39;augmentation du chiffre d&#39;affaire, au calcul de la marge, ainsi qu&#39;au retour sur investissement de la diffusion ou de l&#39;offre.

De plus, grâce au lignes de détail des achats, vous pouvez préciser vos hypothèses afin de ne les concentrer par exemple que sur un produit en particulier.

Par exemple, suite à une diffusion faisant la promotion d&#39;un article, vous pouvez évaluer le chiffre d&#39;affaire généré par cette action. Pour cela, on fait l&#39;hypothèse que tout destinataire ayant acheté au moins un exemplaire de l&#39;article dans le mois suivant le déclenchement de la diffusion a réagi à cette action. La gestion de la réaction va déterminer, suivant cette hypothèse, quels actes d&#39;achats doivent lui être rattachés. Puis, en se basant sur ces rattachements, vous pourrez déterminer le chiffre d&#39;affaire résultant de l&#39;action comme étant la somme des montants des actes rattachés.

>[!CAUTION]
>
>Le Response Manager est une option de **[!UICONTROL Campaign]**. Vérifiez votre contrat de licence.

Vous pouvez également comptabiliser l&#39;ensemble des réactions du foyer du destinataire ayant reçu la diffusion ou l&#39;offre.

Chaque hypothèse est associée à une seule table des transactions. Une diffusion ou une offre peut être associée à plusieurs hypothèses.

## Méthodologie {#method}

Before you start using Response Manager, refer to [Configuration](../../campaign/using/configuration.md) and carry out the necessary configurations.

Pour pouvoir lancer une hypothèse sur une diffusion ou une offre, vous devez préalablement définir son contexte dans un modèle auquel vous ferez référence pour chaque hypothèse créée.

Pour définir et créer des hypothèses de mesure, procédez comme suit :

1. Définissez un modèle d’hypothèse. Reportez-vous à [Création d&#39;un modèle](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model)d&#39;hypothèse.
1. Créez une ou plusieurs hypothèses sur une diffusion existante. Refer to [Referencing a hypothesis in a campaign delivery](../../campaign/using/creating-hypotheses.md#referencing-a-hypothesis-in-a-campaign-delivery).

   or

   Créez une ou plusieurs hypothèses sur les offres. Reportez-vous à [Création d’une hypothèse sur une offre](../../campaign/using/creating-hypotheses.md#creating-a-hypothesis-on-an-offer).

1. Vérifier les résultats de l&#39;hypothèse. Reportez-vous à la section Suivi des [hypothèses](../../campaign/using/hypothesis-tracking.md).
1. Relancez les hypothèses si nécessaire. Refer to [Creating a hypothesis on the fly on a delivery](../../campaign/using/creating-hypotheses.md#creating-a-hypothesis-on-the-fly-on-a-delivery).

