---
product: campaign
title: Configurer des diffusions
description: Découvrez comment effectuer des tests A/B à lʼaide dʼun cas dʼutilisation spécifique
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
feature: A/B Testing
exl-id: 809de30b-7d08-40de-bf3e-dc80d62eae80
TQID: https://experienceleague.adobe.com/7fr4R6dly8-CJh9XYRpAwus1-AUJaz496LOPrWebt0k
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2:
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: e739ee2b-6228-412e-878f-45de0791417d
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 259
ht-degree: 100%

---

# AB Testing : paramétrer les diffusions dans le workflow {#step-4--configuring-the-deliveries-in-the-workflow}

Une fois les [populations créées](a-b-testing-uc-population-samples.md), vous pouvez configurer les diffusions. Dans ce cas d&#39;utilisation, les deux premières diffusions permettent d&#39;envoyer des contenus différents à la population A et B. La troisième diffusion est la diffusion de secours : elle sera envoyée aux destinataires n&#39;appartenant pas à A ou B. Son contenu sera calculé par un script et sera identique à A ou B, selon celui qui a obtenu le taux d&#39;ouverture le plus élevé. Il est nécessaire de configurer une période d&#39;attente pour la troisième diffusion, afin de connaître le résultat des diffusions A et B. C’est pourquoi la troisième diffusion comprend une activité **[!UICONTROL Attente]**.

1. Depuis l&#39;activité **[!UICONTROL Partage]**, rattachez la transition destinée à la population A à l&#39;une des diffusions e-mail déjà présentes dans le workflow.

   ![](assets/use_case_abtesting_createdeliveries_001.png)

1. Double-cliquez sur la diffusion pour l&#39;ouvrir.
1. A l&#39;aide de la liste déroulante, sélectionnez le modèle de la diffusion A.

   ![](assets/use_case_abtesting_createdeliveries_003.png)

1. Cliquez sur **[!UICONTROL Continuer]** pour visualiser la diffusion puis enregistrez-la.

   ![](assets/use_case_abtesting_createdeliveries_002.png)

1. Rattachez la transition de l&#39;activité **[!UICONTROL Partage]** destiné à la population B à la seconde diffusion e-mail.

   ![](assets/use_case_abtesting_createdeliveries_004.png)

1. Ouvrez la diffusion et sélectionnez le modèle de la diffusion B et enregistrez la diffusion.

   ![](assets/use_case_abtesting_createdeliveries_005.png)

1. Reliez la transition destinée à la population restante à l&#39;activité **[!UICONTROL Attente]**.

   ![](assets/use_case_abtesting_createdeliveries_006.png)

1. Ouvrez l&#39;activité **[!UICONTROL Attente]** et configurez le délai à 5 jours.

   ![](assets/use_case_abtesting_createdeliveries_007.png)

1. Reliez l&#39;activité **[!UICONTROL Attente]** à l&#39;activité **[!UICONTROL Code JavaScript]**.

   ![](assets/use_case_abtesting_createdeliveries_008.png)

Vous pouvez maintenant créer le script. [En savoir plus](a-b-testing-uc-script.md).
