---
product: campaign
title: Insérer une ressource partagée
description: Insérer une ressource partagée
feature: Asset Sharing
audience: integrations
content-type: reference
topic-tags: asset-sharing
exl-id: 30a94bce-6d96-4a6d-a62f-7451c822f0e3
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 100%

---

# Insérer une ressource partagée{#inserting-a-shared-asset}

Les ressources partagées depuis Adobe Experience Cloud peuvent être utilisées dans vos emails et landing pages de la manière suivante :

1. Créez un email ou une landing page.

   Si vous utilisez des ressources provenant de la bibliothèque de ressources Adobe Experience Manager, utilisez un modèle de diffusion créé lors de la [configuration de l&#39;intégration](../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets).

   Si vous ne disposez pas de modèle spécifique, assurez-vous que dans les **Propriétés** de la diffusion, le **[!UICONTROL Mode d&#39;édition du contenu]** (onglet **[!UICONTROL Avancé]**) est bien paramétré sur **DCE** et que le compte externe de type AEM que vous souhaitez utiliser pour accéder à votre bibliothèque de ressources AEM Assets est bien renseigné.

1. Dans la fenêtre d&#39;édition, sélectionnez l&#39;option d&#39;insertion d&#39;une image :

   * si vous utilisez le [mode d&#39;édition standard](../../delivery/using/defining-the-email-content.md#adding-images), sélectionnez **[!UICONTROL Image]** > **[!UICONTROL Sélectionner une ressource partagée]**.

     ![](assets/dam_insert_image_standard.png)

   * si vous utilisez le [mode d&#39;édition avancé](../../web/using/about-campaign-html-editor.md) (DCE), placez-vous sur un bloc de type image, puis via le menu contextuel, sélectionnez **[!UICONTROL Sélectionner une ressource partagée]**.

     ![](assets/dam_insert_image_dce.png)

     >[!NOTE]
     >
     >Vous ne pouvez pas insérer d&#39;images partagées depuis Adobe Campaign dans l&#39;[accès web](../../platform/using/adobe-campaign-workspace.md#console-and-web-access) si vous utilisez le DCE.

1. Dans la fenêtre de sélection qui s&#39;ouvre, sélectionnez une image, puis validez.

   Les images disponibles proviennent soit de votre bibliothèque Adobe Experience Cloud, soit de votre bibliothèque AEM Assets, en fonction de la configuration de votre instance Adobe Campaign. Pour plus d&#39;informations, consultez la section [Configurer l’accès à Assets](../../integrations/using/configuring-access-to-assets.md).

   ![](assets/dam_shared_image_selection.png)

>[!NOTE]
>
>Si vous utilisez l&#39;intégration avec Adobe Target, vous pouvez utiliser une image partagée comme image par défaut. Consultez [cette page](../../integrations/using/integrating-with-adobe-target.md).
