---
product: campaign
title: À propos de la gestion de la réaction
description: À propos de la gestion de la réaction
feature: Campaigns
badge-v7: label="v7" type="Informative" tooltip="S’applique à Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="S’applique également à Campaign v8"
exl-id: b5c0e960-2afe-4a98-b82c-d47a74659703
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 97%

---

# Prise en main de la gestion de la réaction de Campaign{#about-response-manager}



Adobe Campaign propose un module complémentaire de gestion de la réaction qui permet de mesurer le succès et la rentabilité d&#39;une campagne marketing ou d&#39;une proposition d&#39;offre, quel que soit le canal de communication utilisé : email, mobile, courrier, etc.

## Hypothèse {#hypothesis-concept}

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

## Étapes dʼimplémentation {#method}

Avant d&#39;utiliser le Response Manager, consultez la section [Configuration](configuration.md) et procédez aux paramétrages qui vous sont nécessaires.

Pour pouvoir lancer une hypothèse sur une diffusion ou une offre, vous devez préalablement définir son contexte dans un modèle auquel vous ferez référence pour chaque hypothèse créée.

Pour définir et créer des hypothèses de mesure, procédez comme suit :

1. Définissez un modèle d’hypothèse. [Apprenez-en davantage](hypothesis-templates.md#creating-a-hypothesis-model)
1. Créez une ou plusieurs hypothèses sur une diffusion existante. [Apprenez-en davantage](creating-hypotheses.md#referencing-a-hypothesis-in-a-campaign-delivery)

   ou

   Créez une ou plusieurs hypothèses sur des offres. [Apprenez-en davantage](creating-hypotheses.md#creating-a-hypothesis-on-an-offer)

1. Vérifiez les résultats des hypothèses. [Apprenez-en davantage](hypothesis-tracking.md)
1. Relancez les hypothèses si nécessaire. [Apprenez-en davantage](creating-hypotheses.md#creating-a-hypothesis-on-the-fly-on-a-delivery)
