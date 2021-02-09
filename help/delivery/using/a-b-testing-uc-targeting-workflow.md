---
solution: Campaign Classic
product: campaign
title: Création d’un workflow de ciblage
description: Découvrez comment effectuer des tests A/B à l’aide d’un cas d’utilisation spécifique.
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: 177b4e74c75e4fcca70dc90b5ff2c0406181e0f7
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 92%

---


# Créer un workflow de ciblage {#step-1--creating-a-targeting-workflow}

Vous devez créer votre workflow dans l&#39;onglet **[!UICONTROL Ciblages et Workflows]** d&#39;une opération. Il est composé d&#39;une activité **[!UICONTROL Requête]**, d&#39;une activité **[!UICONTROL Partage]** à laquelle sont reliées deux activités **[!UICONTROL Diffusions e-mail]**, une activité **[!UICONTROL Attente]**, d&#39;une activité **[!UICONTROL Code JavaScript]** et une activité **[!UICONTROL Diffusion]**.

1. Créez une opération si elle n&#39;existe pas déjà, (voir à ce sujet cette [section](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)).

   ![](assets/use_case_abtesting_targetwkfl_001.png)

1. Positionnez-vous dans l&#39;onglet **[!UICONTROL Ciblages et Workflows]**.

   ![](assets/use_case_abtesting_targetwkfl_002.png)

1. Modifiez le libellé du workflow déjà existant ou cliquez sur **[!UICONTROL Ajouter]** pour en créer un (voir à ce sujet cette [section](../../campaign/using/marketing-campaign-deliveries.md#selecting-the-target-population)).

   ![](assets/use_case_abtesting_targetwkfl_003.png)

1. A l&#39;aide de la souris, faites glisser les différentes activités dans la fenêtre du workflow, soit une activité **[!UICONTROL Requête]** (onglet **[!UICONTROL Ciblage]**), une activité **[!UICONTROL Partage]** (onglet **[!UICONTROL Ciblage]**), deux activités **[!UICONTROL Diffusion e-mail]** (onglet **[!UICONTROL Diffusions]**), une activité **[!UICONTROL Attente]** (onglet **[!UICONTROL Ordonnancement]**), une activité **[!UICONTROL Code JavaScript]** (onglet **[!UICONTROL Action]**) et une activité **[!UICONTROL Diffusion]** (onglet **[!UICONTROL Actions]**).

![](assets/use_case_abtesting_targetwkfl_004.png)
