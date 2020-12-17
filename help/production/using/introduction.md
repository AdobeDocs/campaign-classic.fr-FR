---
solution: Campaign Classic
product: campaign
title: Introduction
description: Introduction
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
translation-type: tm+mt
source-git-commit: 5b35d2ffdd0f591e2fe31dc98a54be9ea0c0c18d
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 93%

---


# Introduction{#introduction}

Ce chapitre présente la procédure à suivre pour mettre à jour Adobe Campaign avec une nouvelle version, côté client et côté serveur, et décrit le mode de transformation en Unicode d&#39;une instance existante.

>[!NOTE]
>
>Pour les instances hébergées, vous devez collaborer avec votre administrateur Adobe.\
>Pour les instances on-premise, vous pouvez obtenir de l&#39;aide auprès des consultants Adobe.

L&#39;opération de mise à jour doit être effectuée sur l&#39;ensemble des serveurs où Adobe Campaign est installé.

1. Migrez les serveurs de redirection et de tracking (Apache / IIS).
1. Migrez les serveurs de Power Booster/Cluster.
1. Migrez le serveur marketing.

Adobe Campaign repose sur plusieurs processus exécutés côté serveur que vous serez amené à manipuler lors d&#39;une mise à jour, en particulier :

* Serveur applicatif (nlserver web)
* Serveur de diffusion (nlserver mta)
* Serveur de redirection (webmdl)

>[!CAUTION]
>
>La console client doit se trouver sur la même version que l’instance du serveur.

>[!NOTE]
>
>Reportez-vous à [cette section](../../installation/using/general-architecture.md#logical-application-layer) pour davantage d’informations sur les différents processus d’Adobe Campaign.\
>Dans le cas d&#39;une architecture de type Power Booster ou Power Cluster, vous devez appliquer cette procédure sur tous les serveurs Power Booster/Cluster.

Si la nouvelle version implique une modification de la structure de la base, il est recommandé de redémarrer les serveurs dans l&#39;ordre suivant :

1. Serveur applicatif (nlserver web),
1. Serveur de redirection (webmdl),
1. Serveur de diffusion (nlserver mta).

