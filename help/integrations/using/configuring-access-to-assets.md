---
title: Configurer l'accès à Assets
seo-title: Configurer l'accès à Assets
description: Configurer l'accès à Assets
seo-description: null
page-status-flag: never-activated
uuid: dc8c0016-92c8-41ab-98c6-d0fe0bfd6c41
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: asset-sharing
discoiquuid: df1b6ead-3471-404a-b43f-a68fb86cb14c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# Configurer l&#39;accès à Assets{#configuring-access-to-assets}

Cette section décrit les étapes de configuration nécessaires dans Adobe Campaign permettant d&#39;utiliser les fonctionnalités de l&#39;intégration avec Assets core service ou la bibliothèque de ressources Adobe Experience Manager.

>[!CAUTION]
>
>Ces intégrations sont concurrentes. Lisez attentivement les informations suivantes avant de procéder à toute configuration.

* Intégration aux ressources **d’** Experience Cloud : cette intégration vous permet d’insérer des images à partir de votre bibliothèque Adobe Experience Cloud. Selon votre modèle de configuration et de licence, cette bibliothèque peut être le service principal Ressources ou Ressources à la demande. Cette intégration doit être configurée en installant le package **[!UICONTROL Integration with the Adobe Experience Cloud]** intégré dans Adobe Campaign.
* Intégration avec **AEM Assets**: cette intégration vous permet d’insérer des images à partir de votre bibliothèque de ressources Adobe Experience Manager. Cette intégration doit être configurée en installant le package **[!UICONTROL AEM Integration]** intégré dans Adobe Campaign.

>[!NOTE]
>
>Si les deux packages (**[!UICONTROL AEM Integration]** et **[!UICONTROL Integration with the Adobe Experience Cloud]** ) sont installés, seuls les actifs disponibles dans la bibliothèque Adobe Experience Cloud peuvent être utilisés. Pour accéder également aux ressources de votre bibliothèque AEM Assets, vous devez synchroniser AEM Assets et Adobe Experience Cloud. Les ressources dans AEM Assets seront ensuite également disponibles dans la bibliothèque Adobe Experience Cloud. Pour plus d’informations sur la synchronisation des ressources AEM et d’Adobe Experience Cloud, consultez la documentation [](https://docs.adobe.com/docs/en/aod/overview/collaborating/aem-assets-aod-sync.html)détaillée.

## Intégration avec Experience Cloud Assets {#integrating-with-experience-cloud-assets}

Afin de pouvoir utiliser l&#39;intégration entre Adobe Campaign et Experience Cloud Assets, les éléments suivants sont requis :

* une organisation Adobe Experience Cloud
* le mode d&#39;authentification IMS Adobe activé

Pour activer la connexion entre Adobe Campaign et Adobe Experience Cloud, configurez la connexion via IMS (service de connexion Adobe ID). Cette configuration est décrite dans le document [Connexion via un Adobe ID](../../integrations/using/about-adobe-id.md). Elle comprend notamment :

* Installing the **[!UICONTROL Integration with the Adobe Experience Cloud]** package.
* la configuration d&#39;un compte externe Adobe Experience Manager.

>[!NOTE]
>
>Les fonctionnalités liées à cette intégration sont uniquement disponibles pour les utilisateurs connectés avec leur Adobe ID via IMS.

## Intégration avec AEM Assets {#integrating-with-aem-assets}

Pour intégrer AEM Assets avec Adobe Campaign, vous devez tout d&#39;abord configurer l&#39;intégration entre Adobe Experience Manager et Adobe Campaign. Cette configuration comprend notamment :

* Installing the **[!UICONTROL AEM Integration]** built-in package
* la configuration d&#39;un compte externe spécifique à Adobe Experience Manager.

Découvrez comment intégrer Adobe Campaign et Adobe Experience Manager dans la [documentation détaillée](../../integrations/using/about-adobe-experience-manager.md).

Une fois cette intégration configurée, vous pouvez configurer un nouveau modèle de diffusion dans Adobe Campaign afin d&#39;utiliser la bibliothèque AEM Assets. Pour cela, procédez comme suit :

1. Créez un modèle de diffusion ou dupliquez un modèle existant. Pour plus d&#39;informations sur les modèles de diffusion, consultez [cette page](../../delivery/using/about-templates.md).
1. Editez les **Propriétés** de ce modèle.
1. Dans l’ **[!UICONTROL Advanced]** onglet, définissez **[!UICONTROL Content editing mode]** DCE **** sur.
1. Select the external **[!UICONTROL AEM account]** that you need to use to access your AEM Assets library.

   ![](assets/dam_aem_assets1.png)

Lorsque vous insérez des images dans le contenu d’une diffusion en fonction de ce modèle, l’ **[!UICONTROL Select a shared asset]** option vous permet ensuite de parcourir les images dans la bibliothèque AEM Assets. En savoir plus dans [cette section](../../integrations/using/inserting-a-shared-asset.md).

>[!NOTE]
>
>Si le **[!UICONTROL Integration with the Adobe Experience Cloud]** package est également installé sur votre instance Adobe Campaign, vous ne pourrez utiliser que les ressources disponibles dans la bibliothèque Adobe Experience Cloud. Pour accéder également aux ressources de votre bibliothèque AEM Assets, vous devez synchroniser AEM Assets et Adobe Experience Cloud. Les ressources dans AEM Assets seront ensuite également disponibles dans la bibliothèque Adobe Experience Cloud. Dans ce cas, vous n’avez pas besoin de créer un modèle de remise spécifique. Pour plus d’informations sur la synchronisation entre AEM Assets et Adobe Experience Cloud, consultez la documentation [](https://docs.adobe.com/docs/en/aod/overview/collaborating/aem-assets-aod-sync.html)détaillée.

