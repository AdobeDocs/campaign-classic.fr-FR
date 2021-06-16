---
product: campaign
title: Création d’un workflow de ciblage
description: Découvrez comment effectuer des tests A/B à l’aide d’un cas d’utilisation spécifique.
audience: delivery
content-type: reference
topic-tags: a-b-testing
exl-id: aa21fa33-aef9-484a-b454-0cd5a6868a98
source-git-commit: 895aa2fd4fa9c7c71c0073e9be33c12d4e92c9fa
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 71%

---

# Création d&#39;un workflow de ciblage {#step-1--creating-a-targeting-workflow}

Vous devez créer votre workflow dans l&#39;onglet **[!UICONTROL Ciblages et Workflows]** d&#39;une opération. Il est composé d&#39;une activité **[!UICONTROL Requête]**, d&#39;une activité **[!UICONTROL Partage]** à laquelle sont reliées deux activités **[!UICONTROL Diffusions e-mail]**, une activité **[!UICONTROL Attente]**, d&#39;une activité **[!UICONTROL Code JavaScript]** et une activité **[!UICONTROL Diffusion]**.

1. Si vous ne l’avez pas déjà fait, créez une campagne (voir à ce sujet [cette section](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)).

   ![](assets/use_case_abtesting_targetwkfl_001.png)

1. Positionnez-vous dans l&#39;onglet **[!UICONTROL Ciblages et Workflows]**.

   ![](assets/use_case_abtesting_targetwkfl_002.png)

1. Modifiez le libellé du workflow existant ou cliquez sur **[!UICONTROL Ajouter]** pour en créer un nouveau (voir à ce sujet [cette section](../../campaign/using/marketing-campaign-deliveries.md#selecting-the-target-population)).

   ![](assets/use_case_abtesting_targetwkfl_003.png)

1. A l&#39;aide de la souris, faites glisser les différentes activités dans la fenêtre du workflow, soit une activité **[!UICONTROL Requête]** (onglet **[!UICONTROL Ciblage]**), une activité **[!UICONTROL Partage]** (onglet **[!UICONTROL Ciblage]**), deux activités **[!UICONTROL Diffusion e-mail]** (onglet **[!UICONTROL Diffusions]**), une activité **[!UICONTROL Attente]** (onglet **[!UICONTROL Ordonnancement]**), une activité **[!UICONTROL Code JavaScript]** (onglet **[!UICONTROL Action]**) et une activité **[!UICONTROL Diffusion]** (onglet **[!UICONTROL Actions]**).

![](assets/use_case_abtesting_targetwkfl_004.png)

Vous pouvez maintenant paramétrer les échantillons de population. [En savoir plus](a-b-testing-uc-population-samples.md).
