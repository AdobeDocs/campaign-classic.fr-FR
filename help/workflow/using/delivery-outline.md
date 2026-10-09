---
product: campaign
title: Composition de diffusion
description: En savoir plus sur l’activité de workflow de composition de diffusion
feature: Workflows, Targeting Activity
hide: true
exl-id: b4dee085-ccc4-43fd-850d-1501a99272aa
TQID: 'https://experienceleague.adobe.com/-KNip5bdMEMgGw7dz6Y4SQ4ueu-iPvYDF0D01hvGn94'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
    internal-label: HeatMap
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
    internal-label: Execution activities
  - id: d1110311-2ca4-442b-be37-088a6db845ee
    internal-label: Data Management activities
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
  - id: ff84ab2f-a7c2-4ced-a3c8-5113f4348d99
    internal-label: Targeting Activity
source-git-commit: 3e213ecc670d5a3cb8299c092ccbb5303858327d
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 100%
---
# Composition de diffusion{#delivery-outline}



L’activité de **composition de diffusion** vous permet d’utiliser une composition dans un workflow de campagne. La composition doit avoir été créée au préalable dans la campagne.

Pour plus d&#39;informations sur les compositions de diffusion dans Adobe Campaign, consultez cette [section](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

Pour configurer l’activité, il vous suffit de sélectionner la composition de votre choix ainsi que la date prévue de contact. Vous pouvez ajouter des règles de filtrage en ajoutant des typologies ou des règles de typologie.

## Exemple : Insérer une offre via une composition de diffusion {#example--inserting-an-offer-via-a-delivery-outline}

L’activité de **composition de diffusion**, disponible dans les workflows de campagne, vous permet de présenter des offres référencées dans une composition de diffusion de la campagne en cours.

>[!NOTE]
>
>Le package **Interaction** doit être installé.

1. Dans un workflow, placez une activité de composition de diffusion avant une activité de diffusion.
1. Dans l&#39;activité de composition, définissez la composition que vous souhaitez utiliser.

   Pour plus d&#39;informations sur la définition des compositions de diffusion, consultez [cette section](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

1. Complétez les champs disponibles en fonction de votre diffusion.
1. Deux cas se présentent :

   * Si vous souhaitez appeler le moteur d’offre, cochez la case **[!UICONTROL Limiter le nombre de propositions sélectionnées]**. Précisez l’emplacement et le nombre de propositions qui seront présentées dans la diffusion.

     Les poids et règles d&#39;éligibilité des offres seront pris en compte par le moteur d&#39;offres.

   * Si vous ne cochez pas la case, toutes les offres de la composition de diffusion seront présentées, sans appel au moteur d&#39;offres.

   La prévisualisation prend en compte le nombre d’offres défini dans la diffusion. Lors de l’exécution d’un workflow, c’est le nombre défini dans la composition de diffusion qui est pris en compte.

   ![](assets/int_compo_offre_wf1.png)
