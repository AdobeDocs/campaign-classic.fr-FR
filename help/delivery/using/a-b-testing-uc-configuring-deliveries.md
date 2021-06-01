---
product: campaign
title: Paramétrage des diffusions
description: Découvrez comment effectuer des tests A/B à l'aide d'un cas pratique spécifique.
audience: delivery
content-type: reference
topic-tags: a-b-testing
exl-id: 809de30b-7d08-40de-bf3e-dc80d62eae80
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 100%

---

# Paramétrer les diffusions dans le workflow {#step-4--configuring-the-deliveries-in-the-workflow}

L’étape suivante consiste à configurer les diffusions. Elles sont destinées aux trois populations créées au cours de l&#39;étape précédente : [Étape 2 : paramétrer les échantillons de population](#step-2--configuring-population-samples). Les deux premières diffusions vous permettent d&#39;envoyer des contenus différents à la population A et B. La troisième diffusion est destinée à la population qui n&#39;a reçu ni A ni B. Son contenu sera calculé par un script et sera identique à A ou B, selon celle qui a obtenu le taux d’ouverture le plus élevé. Il est nécessaire de configurer une période d&#39;attente pour la troisième diffusion, afin de connaître le résultat des diffusions A et B. C’est pourquoi la troisième diffusion comprend une activité **[!UICONTROL Attente]**.

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

Vous pouvez maintenant créer le script (voir [Étape 5 : créer le script ](../../delivery/using/a-b-testing-uc-script.md)).
