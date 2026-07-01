---
product: campaign
title: Créer un workflow de ciblage
description: Découvrez comment effectuer des tests A/B à lʼaide dʼun cas dʼutilisation spécifique
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
feature: A/B Testing
role: User
exl-id: aa21fa33-aef9-484a-b454-0cd5a6868a98
TQID: https://experienceleague.adobe.com/D4O223FYCiIwT-P4WCXa1gYjxB56lCGVIuGL3x-fDRo
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
subfeature_v2:
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: e739ee2b-6228-412e-878f-45de0791417d
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 198
ht-degree: 100%

---

# AB Testing : créer un workflow de ciblage {#step-1--creating-a-targeting-workflow}

Vous devez créer votre workflow dans l’onglet **[!UICONTROL Ciblage et workflows]** d’une campagne.Il est composé d’une activité **[!UICONTROL Requête]**, d’une activité **[!UICONTROL Partage]** à laquelle sont reliées deux activités **[!UICONTROL Diffusion par e-mail]**, d’une activité **[!UICONTROL Attente]**, d’une activité **[!UICONTROL Code JavaScript]** et d’une activité **[!UICONTROL Diffusion]**.

1. Si ce n’est pas déjà fait, créez une campagne. Pour en savoir plus, consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/set-up-campaigns.html?lang=fr){target=_blank}.

   ![](assets/use_case_abtesting_targetwkfl_001.png)

1. Accédez à l’onglet **[!UICONTROL Ciblage et workflows]**.

   ![](assets/use_case_abtesting_targetwkfl_002.png)

1. Modifiez le libellé du workflow existant ou cliquez sur **[!UICONTROL Ajouter]** pour en créer un (voir à ce sujet la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-target.html?lang=fr){target="_blank"}).

   ![](assets/use_case_abtesting_targetwkfl_003.png)

1. A l&#39;aide de la souris, faites glisser les différentes activités dans la fenêtre du workflow, soit une activité **[!UICONTROL Requête]** (onglet **[!UICONTROL Ciblage]**), une activité **[!UICONTROL Partage]** (onglet **[!UICONTROL Ciblage]**), deux activités **[!UICONTROL Diffusion e-mail]** (onglet **[!UICONTROL Diffusions]**), une activité **[!UICONTROL Attente]** (onglet **[!UICONTROL Ordonnancement]**), une activité **[!UICONTROL Code JavaScript]** (onglet **[!UICONTROL Action]**) et une activité **[!UICONTROL Diffusion]** (onglet **[!UICONTROL Actions]**).

![](assets/use_case_abtesting_targetwkfl_004.png)

Vous pouvez maintenant configurer les échantillons de population. [En savoir plus](a-b-testing-uc-population-samples.md).
