---
product: campaign
title: Définir la diffusion finale
description: Découvrez comment effectuer des tests A/B à lʼaide dʼun cas dʼutilisation spécifique
feature: A/B Testing
exl-id: bc23a444-a872-48fb-8bba-64b301541089
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: ht
source-wordcount: '118'
ht-degree: 100%

---

# Définition de la diffusion finale {#step-6--defining-the-final-delivery}

![](../../assets/common.svg)

Une fois que le script pour sélectionner le gagnant du test A/B a été créé, vous pouvez définir les paramètres de la diffusion finale.

1. Reliez l&#39;activité **[!UICONTROL Code JavaScript]** à l&#39;activité **[!UICONTROL Diffusion]** restante.
1. Ouvrez l&#39;activité **[!UICONTROL Diffusion]**.
1. Décochez l&#39;option **[!UICONTROL Générer une transition sortante]** pour terminer le workflow avec cette activité.
1. Conservez les valeurs par défaut des autres options.

   ![](assets/ab_test_final_delivery.png)

En préparant la diffusion spécifiée dans la transition (définie via l&#39;activité **[!UICONTROL Code Javascript]**), vous pourrez alors la valider et démarrer l&#39;envoi, comme décrit à l&#39;étape suivante.

Vous pouvez maintenant démarrer le workflow. [En savoir plus](a-b-testing-uc-start-workflow.md).
