---
product: campaign
title: Introduction
description: Introduction
feature: Monitoring, Upgrade
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 3e39a0d2-ff7e-4233-82bb-2b360f696a33
TQID: 'https://experienceleague.adobe.com/L6Ais2NSt-Z29b7Jgz25a6uYInel9V-Hb5kv0u6oSLo'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: c03a11ff-bdf9-4e5b-b279-f468b4293464
    internal-label: Performance Monitoring
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
    internal-label: Monitoring guidelines
  - id: eff19c99-440a-4318-b319-444edc4d8d8f
    internal-label: Upgrade
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 100%
---
# Introduction{#introduction}



Ce chapitre présente la procédure à suivre pour mettre à niveau Adobe Campaign avec une nouvelle version, côté client et côté serveur, et décrit le mode de transformation en Unicode d&#39;une instance existante.

>[!NOTE]
>
>Pour les instances de services hébergés/gérés, vous devez collaborer avec votre administrateur Adobe.\
>Pour les instances on-premise, vous pouvez obtenir de l&#39;aide auprès des consultants Adobe.

L’opération de mise à niveau doit être effectuée sur l’ensemble des serveurs où Adobe Campaign est installé.

1. Migrez les serveurs de redirection et de tracking (Apache / IIS).
1. Migrez les serveurs de Power Booster/Cluster.
1. Migrez le serveur marketing.

Adobe Campaign repose sur plusieurs processus exécutés côté serveur que vous serez amené à manipuler lors d&#39;une mise à jour, en particulier :

* Serveur applicatif (nlserver web)
* Serveur de diffusion (nlserver mta)
* Serveur de redirection (webmdl)

>[!CAUTION]
>
>La console cliente doit présenter le même build que l&#39;instance de serveur.

>[!NOTE]
>
>Reportez-vous à [cette section](../../installation/using/general-architecture.md#logical-application-layer) pour davantage d’informations sur les différents processus d’Adobe Campaign.\
>Dans le cas d&#39;une architecture de type Power Booster ou Power Cluster, vous devez appliquer cette procédure sur tous les serveurs Power Booster/Cluster.

Si la nouvelle version implique une modification de la structure de la base, il est recommandé de redémarrer les serveurs dans l&#39;ordre suivant :

1. Serveur applicatif (nlserver web),
1. Serveur de redirection (webmdl),
1. Serveur de diffusion (nlserver mta).
