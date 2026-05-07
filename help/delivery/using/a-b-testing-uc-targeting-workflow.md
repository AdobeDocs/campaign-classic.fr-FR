---
product: campaign
title: Créer un workflow de ciblage
description: Découvrez comment effectuer des tests A/B à lʼaide dʼun cas dʼutilisation spécifique
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
feature: A/B Testing
role: User
exl-id: aa21fa33-aef9-484a-b454-0cd5a6868a98
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 78%

---

# AB Testing : créer un workflow de ciblage {#step-1--creating-a-targeting-workflow}

Vous devez créer votre workflow dans l&#39;onglet **[!UICONTROL Ciblage et workflows]** d&#39;une campagne. Elle est composée d&#39;une activité **[!UICONTROL Requête]**, d&#39;une activité **[!UICONTROL Partage]** associée à deux activités **[!UICONTROL Diffusion e-mail]**, d&#39;une activité **[!UICONTROL Attente]**, d&#39;une activité **[!UICONTROL Code JavaScript]** et d&#39;une activité **[!UICONTROL Delivery]**.

1. Si ce n’est pas déjà fait, créez une campagne. Pour en savoir plus, consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/set-up-campaigns.html?lang=fr){target=_blank}.

   ![](assets/use_case_abtesting_targetwkfl_001.png)

1. Accédez à l’onglet **[!UICONTROL Ciblage et workflows]**.

   ![](assets/use_case_abtesting_targetwkfl_002.png)

1. Modifiez le libellé du workflow existant ou cliquez sur **[!UICONTROL Ajouter]** pour en créer un (voir à ce sujet la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-target.html?lang=fr){target="_blank"}).

   ![](assets/use_case_abtesting_targetwkfl_003.png)

1. A l&#39;aide de la souris, faites glisser les différentes activités dans la fenêtre du workflow, soit une activité **[!UICONTROL Requête]** (onglet **[!UICONTROL Ciblage]**), une activité **[!UICONTROL Partage]** (onglet **[!UICONTROL Ciblage]**), deux activités **[!UICONTROL Diffusion e-mail]** (onglet **[!UICONTROL Diffusions]**), une activité **[!UICONTROL Attente]** (onglet **[!UICONTROL Ordonnancement]**), une activité **[!UICONTROL Code JavaScript]** (onglet **[!UICONTROL Action]**) et une activité **[!UICONTROL Diffusion]** (onglet **[!UICONTROL Actions]**).

![](assets/use_case_abtesting_targetwkfl_004.png)

Vous pouvez maintenant configurer les échantillons de population. [En savoir plus](a-b-testing-uc-population-samples.md).
