---
title: Créer un environnement de test
seo-title: Créer un environnement de test
description: Créer un environnement de test
seo-description: null
page-status-flag: never-activated
uuid: 60ce42d5-6c0c-4a0d-bfd6-c778b42563a7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: advanced-parameters
discoiquuid: 7a92bc51-24cf-4ce6-bd50-a315f8f6e34e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Créer un environnement de test{#creating-a-test-environment}

Pour créer un environnement de test (bac à sable), procédez comme suit :

>[!CAUTION]
>
>Utilisez uniquement cette méthode de création d’environnement pour les environnements de test. Dans tous les autres cas, utilisez l’assistant de mappage de cible. Pour plus d’informations, reportez-vous à la section [Création d’un environnement](../../interaction/using/live-design-environments.md#creating-an-offer-environment)d’offre.

1. Lancez l&#39;explorateur Adobe Campaign et positionnez-vous au niveau du noeud racine de l&#39;instance.
1. Right-click and add a **[!UICONTROL Generic folder]** using the drop-down menus.

   ![](assets/offer_env_creation_001.png)

1. Next, go to the folder you just created and add an **[!UICONTROL Offer environment]** using the right-click menus.

   ![](assets/offer_env_creation_001bis.png)

1. Procédez de la même manière pour créer les sous-dossiers et éléments de l&#39;environnement.
1. Once your tests have finished and you wish to use the environment in production, duplicate the offers and spaces in your design environment. (Right-click > **[!UICONTROL Actions]** > **[!UICONTROL Deploy]** ).

   ![](assets/migration_interaction_5.png)

