---
product: campaign
title: Configurer l’intégration à Adobe Target
description: Découvrez comment configurer l’intégration à Adobe Target.
feature: Target Integration
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: ae8c680f-52a6-4d00-91cd-44d1c3807546
TQID: https://experienceleague.adobe.com/k6TljRgymSefOITPaogJdR7HOrl1BnnZm9jbkemrcyg
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: c5474392-5419-4296-9e41-f6f4ce4f6e9bid: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2: id: b1fd1501-3105-4d6b-b4d4-9af53126df75
topic_v2: id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 212
ht-degree: 92%

---

# Configuration de l’intégration à Adobe Target{#configuring-the-integration-with-adobe-target}




>[!CAUTION]
>
> Si vous êtes client hébergé ou hybride, contactez votre représentant Adobe pour configurer cette intégration. Les étapes ci-dessous s’appliquent uniquement aux clients on-premise.

Cette intégration requiert les éléments suivants :

* des organisations Adobe Experience Cloud et Adobe Target
* un &quot;rawbox&quot; Adobe Target défini afin d&#39;établir la connexion avec Adobe Campaign

Pour configurer cette intégration dans Adobe Campaign, procédez comme suit :

1. Installez le package intégré **[!UICONTROL Intégration à Adobe Experience Cloud]**. [En savoir plus](../../platform/using/working-with-data-packages.md#importing-packages)

   Ce package vous donne accès aux ressources partagées via le gestionnaire de ressources numériques.

1. Activez la connexion via IMS (service de connexion Adobe ID) pour utiliser des images partagées via Adobe Experience Cloud dans vos e-mails. [En savoir plus](../../integrations/using/about-adobe-id.md)
1. Accédez à **[!UICONTROL Administration > Plateforme > Options]** pour configurer les options de serveur et d’organisation (client) pour Adobe Target :

   ![](assets/tar_options.png)

   * **[!UICONTROL TNT_EdgeServer]** : serveur Adobe Target utilisé pour l&#39;intégration. Cette option est déjà sélectionnée par défaut. Cette valeur correspond au **[!UICONTROL Server Domain]** Adobe Target, suivie de la valeur **/m2**. Par exemple : **tt.omtrdc.net/m2**.
   * **[!UICONTROL TNT_TenantName]** : nom de l&#39;organisation Adobe Target. Cette valeur correspond au nom du **[!UICONTROL Client Adobe Target]**.


>[!CAUTION]
>
>Pour les architectures hybrides et hébergées, ces options doivent être définies sur tous les serveurs, y compris le [serveur de midsourcing](../../installation/using/mid-sourcing-server.md) et l&#39;[instance d&#39;exécution](../../message-center/using/configuring-instances.md#execution-instance).