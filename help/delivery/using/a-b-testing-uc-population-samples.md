---
product: campaign
title: Configurer des échantillons de population
description: Découvrez comment effectuer des tests A/B à lʼaide dʼun cas dʼutilisation spécifique
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: A/B Testing
exl-id: 1ca01cab-734a-4299-b112-04eec51222fb
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: ht
source-wordcount: '0'
ht-degree: 100%

---

# Configuration des échantillons de population {#step-2--configuring-population-samples}



## Configurer l&#39;activité de Requête {#configuring-the-query-activity}

* Double-cliquez sur l&#39;activité **[!UICONTROL Requête]**.

   ![](assets/use_case_abtesting_createrecipients_001.png)

* Cliquez sur le lien **[!UICONTROL Editer la requête]** et sélectionnez les destinataires que vous souhaitez cibler.

   ![](assets/use_case_abtesting_createrecipients_002.png)

* Reliez l&#39;activité **[!UICONTROL Requête]** à l&#39;activité **[!UICONTROL Partage]**.

   ![](assets/use_case_abtesting_createrecipients_003.png)

## Configurer l&#39;activité Partage {#configuring-the-split-activity}

Cette activité permet de créer plusieurs populations : celle qui reçoit la diffusion A, celle qui reçoit la diffusion B et la population restante. D&#39;autre part, l&#39;utilisation du tirage aléatoire permet de ne cibler qu&#39;une partie de la population de chacune des diffusions.

1. Création de la population A :

   * Double-cliquez sur l&#39;activité **[!UICONTROL Partage]**.

      ![](assets/use_case_abtesting_createrecipients_004.png)

   * Dans l&#39;onglet existant, modifiez le libellé pour désigner la population A.

      ![](assets/use_case_abtesting_createrecipients_005.png)

   * Sélectionnez l&#39;option **[!UICONTROL Limiter les enregistrements sélectionnés]**.

      ![](assets/use_case_abtesting_createrecipients_006.png)

   * Cliquez sur le lien **[!UICONTROL Editer]**, sélectionnez **[!UICONTROL Activer le tirage aléatoire]**, puis cliquez sur **[!UICONTROL Suivant]**.

      ![](assets/use_case_abtesting_createrecipients_007.png)

   * Configurez la limite à 10%, puis cliquez sur **[!UICONTROL Terminer]**.

      ![](assets/use_case_abtesting_createrecipients_008.png)

1. Création de la population B :

   * Cliquez sur **[!UICONTROL Ajouter]** pour créer un nouvel onglet destiné à la population B.

      ![](assets/use_case_abtesting_createrecipients_009.png)

   * Limitez la population à 10% comme fait précédemment.

      ![](assets/use_case_abtesting_createrecipients_010.png)

1. Création de la population restante :

   * Positionnez-vous dans l&#39;onglet **[!UICONTROL Général]**.

      ![](assets/use_case_abtesting_createrecipients_011.png)

   * Sélectionnez **[!UICONTROL Générer le complémentaire]**.

      ![](assets/use_case_abtesting_createrecipients_012.png)

   * Modifiez le libellé pour désigner la population qui ne comprend ni la population A, ni la B et cliquez sur **[!UICONTROL OK]** pour fermer l&#39;activité.

      ![](assets/use_case_abtesting_createrecipients_013.png)

Vous pouvez maintenant créer les deux modèles de diffusion. [En savoir plus](a-b-testing-uc-delivery-templates.md)).
