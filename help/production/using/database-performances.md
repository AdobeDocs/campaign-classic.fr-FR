---
product: campaign
title: Performances de la base
description: Performances de la base
feature: Monitoring
badge-v7-prem: label="On-Premise/hybride uniquement" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 33dcfd4b-51fd-44f4-98e0-23eafb79d7da
TQID: https://experienceleague.adobe.com/wrssH80YsIhpcsjLajyPls3eslNzHRFLUAxkP7IOGu8
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
feature_v2: []
subfeature_v2:
  - id: c03a11ff-bdf9-4e5b-b279-f468b4293464
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 527
ht-degree: 53%

---

# Performances de la base de données{#database-performances}



La plupart des problèmes de performances sont liés à la maintenance de la base de données. Voici quatre pistes principales pour vous aider à trouver la cause de la lenteur des performances :

* Configuration
* Installation et la configuration de la plateforme Adobe Campaign
* Maintenance de la base de données
* Diagnostic en temps réel

## Configuration {#configuration}

Vérifiez que la configuration initiale de la plateforme Adobe Campaign est toujours valable et réévaluez, si nécessaire, les besoins de votre client en termes de délivrabilité ou de taille de la base de données. Nous vous recommandons également d’effectuer une vérification complète du matériel (CPU, RAM, système d’E/S).

>[!NOTE]
>
>Pour plus d’informations, consultez le [guide relatif au dimensionnement matériel d’Adobe Campaign](https://helpx.adobe.com/fr/campaign/kb/hardware-sizing-guide.html).

## Configuration de la plateforme {#platform-configuration}

Une configuration inappropriée peut avoir une incidence sur les performances de la plateforme. Nous vous recommandons de vérifier la configuration du réseau, les options de délivrabilité de la plateforme ainsi que la configuration du MTA dans le fichier **serverConf.xml**.

## Maintenance de la base de données {#database-maintenance}

**Tâche de nettoyage de la base**

Assurez-vous que la tâche de nettoyage de la base de données est opérationnelle. Pour ce faire, affichez les fichiers journaux pour voir s’ils contiennent des erreurs. Voir à ce propos [cette section](../../production/using/database-cleanup-workflow.md).

**Plans de maintenance**

Assurez-vous que la maintenance de la base de données est correctement planifiée et exécutée. Pour ce faire, contactez l’administrateur de votre base de données pour en savoir plus sur :

* Son planning de maintenance
* Les plans de maintenance déjà exécutés
* Comment consulter les logs de script

Pour plus d’informations, consultez [cette section](../../production/using/recommendations.md).

>[!IMPORTANT]
>
>Si vous utilisez une configuration de mid-sourcing, il est essentiel que les bases de données soient gérées régulièrement. Lors de l’analyse d’une diffusion sur la plateforme marketing, l’instance marketing envoie des informations à l’instance de mid-sourcing. Si le processus est ralenti, l’instance marketing sera affectée.

**Gestion des tables de travail**

Merci de vérifier le nombre et la taille des tables de travail. Lorsqu’elles dépassent une certaine taille, les performances de la base de données sont affectées. Ces tables sont créées par les workflows et les diffusions. Elles restent dans la base de données tant que les workflows et les diffusions sont actifs. Pour limiter la taille des tables de travail, vous pouvez effectuer les opérations suivantes :

* Arrêter ou supprimer les diffusions dont le statut est, au choix, **[!UICONTROL En échec]**, **[!UICONTROL En cours]**, **[!UICONTROL Prête à être diffusée]** ou **[!UICONTROL En pause]**.
* Arrêter ou supprimer les workflows qui sont en pause à cause d&#39;une erreur.
* Arrêter les workflows utilisés pour faire des tests, qui ne contiennent pas d&#39;activité **[!UICONTROL Fin]** et dont le statut est, de ce fait, **[!UICONTROL En pause]**.

>[!IMPORTANT]
>
>Si cette opération prend beaucoup de temps et qu&#39;une fois effectuée, beaucoup d&#39;espace disque est libéré, il est indispensable d&#39;effectuer une maintenance en profondeur (reconstruction des index, etc.). Pour plus d’informations, consultez [cette section](../../production/using/recommendations.md).

**Suivi des processus Adobe Campaign**

Selon les paramètres d&#39;installation d&#39;Adobe Campaign, vous avez deux outils à votre disposition pour effectuer le suivi de votre plateforme :

* La page de production de l&#39;instance. Pour plus d&#39;informations, consultez la section [Surveillance manuelle](../../production/using/monitoring-processes.md#manual-monitoring).
* Le script *netreport*. Pour plus d&#39;informations, consultez la section [Surveillance automatique via les scripts d&#39;Adobe Campaign](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts).

## Cas particuliers {#specifics}

Il peut s’avérer nécessaire d’effectuer un diagnostic en temps réel pour identifier la cause du problème. Vérifiez d&#39;abord les fichiers journaux des processus et de la plateforme, puis surveillez l&#39;activité de la base de données tout en recréant le problème. Accordez une attention particulière aux éléments suivants :

* Le plan d&#39;exécution de la maintenance
* les requêtes SQL en cours d&#39;exécution
* Si des processus externes s&#39;exécutent en même temps (nettoyage, import, calcul d&#39;agrégats, etc.).
