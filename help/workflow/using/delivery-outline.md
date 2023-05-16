---
product: campaign
title: Composition de diffusion
description: En savoir plus sur l’activité de workflow de composition de diffusion
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Targeting Activity
exl-id: b4dee085-ccc4-43fd-850d-1501a99272aa
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 100%

---

# Composition de diffusion{#delivery-outline}



L&#39;activité de **composition de diffusion** permet d&#39;utiliser une composition dans un workflow de campagne. La composition doit avoir été préalablement créée dans la campagne.

Pour plus d&#39;informations sur les compositions de diffusion dans Adobe Campaign, consultez cette [section](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

Pour paramétrer l&#39;activité, vous devez simplement sélectionner la composition de votre choix ainsi que la date prévue de contact. Vous pouvez ajouter des règles de filtrages en ajoutant des typologies ou des règles de typologie.

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

   * Si vous souhaitez appeler le moteur d&#39;offres, cochez la case **[!UICONTROL Limiter le nombre de propositions sélectionnées]**. Définissez l&#39;emplacement et le nombre d&#39;offres qui seront présentées dans la diffusion.

      Les poids et règles d&#39;éligibilité des offres seront pris en compte par le moteur d&#39;offres.

   * Si vous ne cochez pas la case, toutes les offres de la composition de diffusion seront présentées, sans appel au moteur d&#39;offres.

   La prévisualisation prend en compte le nombre d&#39;offres défini dans la diffusion. Lors de l&#39;exécution du workflow, c&#39;est le nombre défini dans la composition de diffusion qui est pris en compte.

   ![](assets/int_compo_offre_wf1.png)
