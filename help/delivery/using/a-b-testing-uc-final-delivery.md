---
solution: Campaign Classic
product: campaign
title: Définir la diffusion finale
description: Découvrez comment effectuer des tests A/B à l'aide d'un cas pratique spécifique.
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: ht
source-git-commit: 50a10e16f320a67cb4ad0e31c1cbe8a9365b7887
workflow-type: ht
source-wordcount: '121'
ht-degree: 100%

---


# Définir la diffusion finale {#step-6--defining-the-final-delivery}

Une fois que le script pour sélectionner le gagnant du test A/B a été créé, vous pouvez définir les paramètres de la diffusion finale.

1. Reliez l&#39;activité **[!UICONTROL Code JavaScript]** à l&#39;activité **[!UICONTROL Diffusion]** restante.
1. Ouvrez l&#39;activité **[!UICONTROL Diffusion]**.
1. Décochez l&#39;option **[!UICONTROL Générer une transition sortante]** pour terminer le workflow avec cette activité.
1. Conservez les valeurs par défaut des autres options.

   ![](assets/ab_test_final_delivery.png)

En préparant la diffusion spécifiée dans la transition (définie via l&#39;activité **[!UICONTROL Code Javascript]**), vous pourrez alors la valider et démarrer l&#39;envoi, comme décrit à l&#39;étape suivante.

Vous pouvez maintenant démarrer le workflow (voir [Étape 7 : lancer le workflow](../../delivery/using/a-b-testing-uc-start-workflow.md)).
