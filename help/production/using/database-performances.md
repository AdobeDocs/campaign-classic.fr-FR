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
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 100%

---

# Performances de la base de données{#database-performances}



La plupart des problèmes de performance sont liés à l&#39;entretien de la base de données. Nous vous proposons quatre axes de recherche pour vous aider à en trouver les causes :

* Configuration 
* Installation et la configuration de la plateforme Adobe Campaign
* Maintenance de la base de données
* Diagnostic en temps réel

## Configuration  {#configuration}

Vous devez vérifier que la configuration initiale de la plateforme Adobe Campaign est toujours valable et revoir, le cas échéant, les besoins de votre client en termes de délivrabilité ou de taille de la base de données. Nous vous conseillons également d’effectuer une vérification complète de la configuration matérielle (CPU, RAM, système E/S).

>[!NOTE]
>
>Pour plus d’informations, consultez le [guide relatif au dimensionnement matériel d’Adobe Campaign](https://helpx.adobe.com/fr/campaign/kb/hardware-sizing-guide.html).

## Configuration de la plateforme {#platform-configuration}

Une configuration inappropriée peut avoir une incidence sur les performances de la plateforme. Nous vous recommandons de vérifier la configuration du réseau, les options de délivrabilité de la plateforme ainsi que la configuration du MTA dans le fichier **serverConf.xml**.

## Maintenance de la base de données {#database-maintenance}

**Tâche de nettoyage de la base**

Vous devez vérifier que la tâche de nettoyage de la base fonctionne correctement. Pour cela, consultez les fichiers journaux afin d&#39;être sûr qu&#39;ils ne contiennent pas d&#39;erreurs. Voir à ce propos [cette section](../../production/using/database-cleanup-workflow.md).

**Plans de maintenance**

Vous devez vous assurer que la maintenance de la base de données est correctement planifiée et effectuée. Pour cela, renseignez-vous auprès de votre administrateur de base de données pour connaître :

* Son planning de maintenance
* Les plans de maintenance déjà exécutés
* Comment consulter les logs de script

Voir à ce propos [cette section](../../production/using/recommendations.md).

>[!IMPORTANT]
>
>Si vous utilisez une configuration en mid-sourcing, il est important que les bases de données soient correctement maintenue. Lors de l&#39;analyse d&#39;une diffusion sur la plateforme marketing, l&#39;instance marketing envoie des informations vers l&#39;instance mid-sourcing. Si le processus ralentit, l&#39;activité de l&#39;instance marketing ralentira également afin que l&#39;instance de mid-sourcing puisse effectuer ses opérations correctement.

**Gestion des tables de travail**

Vous devez vérifier le nombre et la taille des tables de travail. Lorsqu&#39;elles deviennent trop volumineuses, les performances de la base sont affectées. Ces tables sont créées notamment par les workflows et les diffusions. Elles ne disparaissent pas de la base tant que le traitement des workflows et des diffusions n&#39;est pas terminé ou qu&#39;ils n&#39;ont pas été interrompus ou supprimés. Pour limiter les tables de travail vous pouvez effectuer les opérations suivantes :

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

Il peut être nécessaire d&#39;effectuer un diagnostic en temps-réel pour déterminer la cause du problème. Vous devez d&#39;abord vérifier les fichiers journaux des processus et de la plateforme. Puis, suivez l&#39;activité de la base lors de la reproduction du problème. Vous devez particulièrement porter votre attention sur les éléments suivants :

* Le plan d&#39;exécution de la maintenance
* les requêtes SQL en cours d&#39;exécution
* Si des processus externes s&#39;exécutent en même temps (nettoyage, import, calcul d&#39;agrégats, etc.).
