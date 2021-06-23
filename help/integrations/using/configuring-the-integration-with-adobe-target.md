---
product: campaign
title: Configuration de l’intégration avec Adobe Target
description: Configuration de l’intégration avec Adobe Target
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: ae8c680f-52a6-4d00-91cd-44d1c3807546
source-git-commit: 94e609f3df94c553e2ec84ee427887a767b9af21
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 90%

---

# Configuration de l’intégration avec Adobe Target{#configuring-the-integration-with-adobe-target}

## Conditions préalables requises {#prerequisites}

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

>[!CAUTION]
>
>Pour les architectures hybrides et hébergées, ces options doivent être définies sur tous les serveurs, y compris le [serveur de mid-sourcing](../../installation/using/mid-sourcing-server.md) et l’[instance d’exécution](../../message-center/using/configuring-instances.md#execution-instance).