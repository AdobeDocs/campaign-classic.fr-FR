---
product: campaign
title: Configuration de l'intégration avec Adobe Target
description: Configuration de l’intégration avec Adobe Target
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: ae8c680f-52a6-4d00-91cd-44d1c3807546
source-git-commit: b6e24c63ece12f25b7dafe3fede9e38b3aab2427
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 62%

---

# Configuration de l&#39;intégration avec Adobe Target{#configuring-the-integration-with-adobe-target}

![](../../assets/common.svg)


>[!CAUTION]
>
> En tant que client hébergé ou hybride, contactez votre représentant d’Adobe pour configurer cette intégration. Les étapes ci-dessous s’appliquent uniquement aux clients on-premise.

## Conditions préalables requises {#prerequisites}

Afin de pouvoir utiliser l&#39;intégration entre Adobe Campaign et Adobe Target, les éléments suivants sont requis :

* des organisations Adobe Experience Cloud et Adobe Target
* un &quot;rawbox&quot; Adobe Target défini afin d&#39;établir la connexion avec Adobe Campaign

## Configurer Adobe Campaign {#configuring-adobe-campaign}

Les étapes de configuration d&#39;Adobe Campaign sont les suivants :

1. Installez le **[!UICONTROL Intégration à Adobe Experience Cloud]** module intégré. [En savoir plus](../../platform/using/working-with-data-packages.md#importing-packages)   

   Ce package vous donne accès aux ressources partagées via Digital Asset Manager.

1. Activez la connexion via IMS (service de connexion Adobe ID) pour utiliser les images partagées via Adobe Experience Cloud dans vos emails. [En savoir plus](../../integrations/using/about-adobe-id.md)   
1. Accédez à **[!UICONTROL Administration > Plateforme > Options]** pour configurer les options de serveur et d’organisation (Tenant) pour Adobe Target :

   ![](assets/tar_options.png)

   * **[!UICONTROL TNT_EdgeServer]** : serveur Adobe Target utilisé pour l&#39;intégration. Cette option est déjà renseignée par défaut. Cette valeur correspond au **[!UICONTROL Server Domain]** Adobe Target, suivie de la valeur **/m2**. Par exemple : **tt.omtrdc.net/m2**.
   * **[!UICONTROL TNT_TenantName]** : nom de l&#39;organisation Adobe Target. Cette valeur correspond au nom du **[!UICONTROL Client]** Adobe Target.


>[!CAUTION]
>
>Pour les architectures hybrides et hébergées, ces options doivent être définies sur tous les serveurs, y compris le [serveur de midsourcing](../../installation/using/mid-sourcing-server.md) et l&#39;[instance d&#39;exécution](../../message-center/using/configuring-instances.md#execution-instance).