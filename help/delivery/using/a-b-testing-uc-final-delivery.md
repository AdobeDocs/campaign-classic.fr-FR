---
product: campaign
title: Définir la diffusion finale
description: Découvrez comment effectuer des tests A/B à lʼaide dʼun cas dʼutilisation spécifique.
badge-v7: label="v7" type="Informative" tooltip="S’applique à Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="S’applique également à Campaign v8"
feature: A/B Testing
role: User
exl-id: bc23a444-a872-48fb-8bba-64b301541089
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 95%

---

# Tests AB : définissez la diffusion finale {#step-6--defining-the-final-delivery}

Une fois que le script pour sélectionner le gagnant du test A/B a été créé, vous pouvez définir les paramètres de la diffusion finale.

1. Reliez l&#39;activité **[!UICONTROL Code JavaScript]** à l&#39;activité **[!UICONTROL Diffusion]** restante.
1. Ouvrez l&#39;activité **[!UICONTROL Diffusion]**.
1. Décochez l&#39;option **[!UICONTROL Générer une transition sortante]** pour terminer le workflow avec cette activité.
1. Conservez les valeurs par défaut des autres options.

   ![](assets/ab_test_final_delivery.png)

En préparant la diffusion spécifiée dans la transition (définie via l&#39;activité **[!UICONTROL Code Javascript]**), vous pourrez alors la valider et démarrer l&#39;envoi, comme décrit à l&#39;étape suivante.

Vous pouvez maintenant démarrer le workflow. [En savoir plus](a-b-testing-uc-start-workflow.md).
