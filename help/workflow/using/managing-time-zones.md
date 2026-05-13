---
product: campaign
title: Gérer les fuseaux horaires
description: Gérer les fuseaux horaires
feature: Workflows
hide: true
exl-id: c2f6033c-30cd-4eb4-adf1-ab2de7510220
TQID: https://experienceleague.adobe.com/POlYZz1HCRqIp3TdBvIEsOu1grFmxVgqN1xQ1KnuQlQ
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 297
ht-degree: 61%

---

# Gérer les fuseaux horaires{#managing-time-zones}



Adobe Campaign permet de gérer les décalages horaires entre plusieurs pays concernés par la même instance. La configuration appliquée est configurée lors de la création de l’instance.

Pour plus d&#39;informations sur la configuration des fuseaux horaires dans Adobe Campaign, consultez le [Guide d&#39;installation de Campaign Classic v7](../../installation/using/time-zone-management.md).

Dans un workflow, vous pouvez adapter les plannings d’exécution des activités et associer un fuseau horaire spécifique à une activité ou à l’ensemble du workflow. Cette configuration peut s&#39;avérer utile lors de l&#39;import du fichier ou dans le cadre de la planification des diffusions.

## Planifier l&#39;exécution {#execution-scheduling}

Vous pouvez planifier l’exécution des tâches à l’aide du planificateur (voir [Planificateur](scheduler.md)). Vous pouvez également utiliser les options de planification disponibles dans les activités qui proposent cette fonctionnalité. Ces activités offrent un onglet **[!UICONTROL Planification]** : **[!UICONTROL Collecteur de fichiers]**, **[!UICONTROL Transfert de fichiers]**, **[!UICONTROL Téléchargement Web]**, **[!UICONTROL Réception d’emails]** et **[!UICONTROL SMS]**, etc.

Pour toute tâche planifiée, c&#39;est-à-dire dans toute activité qui propose des options de planification, vous pouvez choisir le fuseau horaire à appliquer. Le fuseau horaire est sélectionné à l&#39;aide de l’onglet **[!UICONTROL Avancé]** de l&#39;activité concernée :

![](assets/wf-timezone-in-a-box.png)

Les valeurs possibles sont les suivantes :

* Fuseau horaire du serveur

  Utilise le fuseau horaire du serveur applicatif d&#39;Adobe Campaign.

* Fuseau horaire de l&#39;utilisateur

  Utilise le fuseau horaire de l&#39;opérateur Adobe Campaign qui lance l&#39;exécution du workflow.

* Fuseau horaire de la base de données

  Utilise le fuseau horaire du serveur de base de données utilisé.

* Fuseaux horaire spécifiques

  Utilise le fuseau horaire sélectionné.

Si la valeur **[!UICONTROL Par défaut]** est sélectionnée, le fuseau horaire du workflow est appliqué, ou, à défaut, celui du serveur applicatif.

## Associer un fuseau horaire à une activité {#linking-a-time-zone-to-an-activity}

L&#39;onglet **[!UICONTROL Avancé]** des activités de workflow permet de sélectionner le fuseau horaire de l&#39;activité. Bien que la plupart du temps, le fuseau horaire du workflow soit suffisant, il peut être nécessaire de le surcharger de temps en temps pour une activité spécifique, telle que l’importation de données, afin de lier les dates au fuseau horaire approprié.
