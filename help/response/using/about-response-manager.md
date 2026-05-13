---
product: campaign
title: À propos de la gestion de la réaction
description: À propos de la gestion de la réaction
feature: Campaigns
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
exl-id: b5c0e960-2afe-4a98-b82c-d47a74659703
TQID: https://experienceleague.adobe.com/ScwRjZlHoAjXQBxig5Mt3HuNkpPiZ9J-FQTm9FuCY4g
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
subfeature_v2:
  - id: ede6e1ec-9279-415e-b828-a09735018d48
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 418
ht-degree: 65%

---

# Prise en main de la gestion de la réaction de Campaign{#about-response-manager}



Adobe Campaign propose un module complémentaire de gestion de la réaction qui permet de mesurer le succès et la rentabilité d&#39;une campagne marketing ou d&#39;une proposition d&#39;offre, quel que soit le canal de communication utilisé : email, mobile, courrier, etc.

## Hypothèse {#hypothesis-concept}

Les hypothèses peuvent être paramétrées sur une période donnée à partir de la date de contact afin de déduire le comportement des personnes ciblées après réception d&#39;une diffusion. Ces hypothèses sont basées sur un tableau **transaction** qui enregistre les achats et les détails de ces achats.

Les hypothèses sont délimitées dans le temps et peuvent être réalisées sur une population témoin que l&#39;on comparera à la population ciblée. Les résultats de l&#39;hypothèse sont donnés par des **indicateurs** qui sont automatiquement mis à jour lorsque le calcul est terminé. Le ROI associé aux hypothèses sera pris en compte dans les rapports de campagne.

D&#39;autre part, les **rapports** standards fournis avec le Response Manager permettent de synthétiser les informations relatives à l&#39;augmentation du chiffre d&#39;affaire, au calcul de la marge, ainsi qu&#39;au retour sur investissement de la diffusion ou de l&#39;offre.

De plus, grâce au lignes de détail des achats, vous pouvez préciser vos hypothèses afin de ne les concentrer par exemple que sur un produit en particulier.

Par exemple, à la suite d&#39;une diffusion faisant la promotion d&#39;un article, nous souhaitons évaluer le chiffre d&#39;affaires généré. Nous appliquons l&#39;hypothèse que tout destinataire ayant acheté au moins un article dans le mois suivant le déclenchement de la diffusion a réagi à cette action. La gestion de la réaction déterminera, en fonction de cette hypothèse, les lignes de demande d&#39;achat qui lui seront affectées. Ensuite, sur la base de ces données, il sera possible de déterminer les recettes obtenues comme étant la somme de ces lignes.

>[!CAUTION]
>
>Response Manager est une option **[!UICONTROL Campaign]**. Veuillez vérifier votre accord de licence.

Vous pouvez également comptabiliser l&#39;ensemble des réactions du foyer du destinataire ayant reçu la diffusion ou l&#39;offre.

Chaque hypothèse est liée à une table de transactions unique. Une diffusion ou une offre peut être associée à plusieurs hypothèses.

## Étapes dʼimplémentation {#method}

Avant d&#39;utiliser le Response Manager, consultez la section [Configuration](configuration.md) et procédez aux paramétrages qui vous sont nécessaires.

Pour pouvoir lancer une hypothèse sur une diffusion ou une offre, vous devez préalablement définir son contexte dans un modèle auquel vous ferez référence pour chaque hypothèse créée.

Pour définir et créer des hypothèses de mesure, procédez comme suit :

1. Définissez un modèle d’hypothèse. [Apprenez-en davantage](hypothesis-templates.md#creating-a-hypothesis-model)
1. Créez une ou plusieurs hypothèses sur une diffusion existante. [Apprenez-en davantage](creating-hypotheses.md#referencing-a-hypothesis-in-a-campaign-delivery)

   ou

   Créez une ou plusieurs hypothèses sur des offres. [Apprenez-en davantage](creating-hypotheses.md#creating-a-hypothesis-on-an-offer)

1. Vérifiez les résultats des hypothèses. [Apprenez-en davantage](hypothesis-tracking.md)
1. Relancez les hypothèses si nécessaire. [En savoir plus](creating-hypotheses.md#creating-a-hypothesis-on-the-fly-on-a-delivery)
