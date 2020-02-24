---
title: Configurer l'intégration avec Adobe Target
seo-title: Configurer l'intégration avec Adobe Target
description: Configurer l'intégration avec Adobe Target
seo-description: null
page-status-flag: never-activated
uuid: b9337e92-e4e5-4cba-a559-75db7460d5c5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-target
discoiquuid: 378d5ff9-88c0-43f1-beb8-454701e9f1d1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# Configurer l&#39;intégration avec Adobe Target{#configuring-the-integration-with-adobe-target}

## Prérequis {#prerequisites}

Afin de pouvoir utiliser l&#39;intégration entre Adobe Campaign et Adobe Target, les éléments suivants sont requis :

* des organisations Adobe Experience Cloud et Adobe Target
* un &quot;rawbox&quot; Adobe Target défini afin d&#39;établir la connexion avec Adobe Campaign

## Configurer Adobe Campaign {#configuring-adobe-campaign}

Les étapes de configuration d&#39;Adobe Campaign sont les suivants :

1. Installez le package standard **[!UICONTROL Intégration avec Adobe Experience Cloud]**. L’installation d’un package d’intégration est identique à l’installation d’un package standard, détaillée dans la section [Import de packages](../../platform/using/working-with-data-packages.md#importing-packages). Cela permet d’accéder aux ressources partagées via Digital Asset Manager.
1. Activez la connexion via IMS (service de connexion Adobe ID) si vous souhaitez pouvoir utiliser des images partagées via Adobe Experience Cloud dans vos emails. Consultez la section concernant l’[IMS](../../integrations/using/about-adobe-id.md).
1. Dans **[!UICONTROL Administration > Plate-forme > Options]**, configurez les options de serveur et d&#39;organisation (Tenant) pour Adobe Target :

   * **[!UICONTROL TNT_EdgeServer]** : serveur Adobe Target utilisé pour l&#39;intégration. Cette option est déjà renseignée par défaut. Cette valeur correspond au **[!UICONTROL Server Domain]** Adobe Target, suivie de la valeur **/m2**. Par exemple : **tt.omtrdc.net/m2**.
   * **[!UICONTROL TNT_TenantName]** : nom de l&#39;organisation Adobe Target. Cette valeur correspond au nom du **[!UICONTROL Client]** Adobe Target.
   ![](assets/tar_options.png)

