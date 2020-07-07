---
title: Directives de supervision
description: Cette section présente des directives générales pour la surveillance des Campaign Classic.
page-status-flag: never-activated
uuid: cf0d782d-47bf-40ae-ab6f-d1d47fa15792
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: introduction
discoiquuid: 8b33e6af-15c3-4b30-8ad6-d76a1f33be21
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7d944973e10c4df166325049b947e359853a2353
workflow-type: tm+mt
source-wordcount: '700'
ht-degree: 14%

---


# Directives de supervision {#monitoring-guidelines}

## Tableau de bord de supervision de l&#39;instance {#instance-monitoring-dashboard}

L&#39;onglet **[!UICONTROL Surveillance]** , accessible à partir de la page d&#39;accueil du Campaign Classic, est le principal point d&#39;entrée pour vous aider à surveiller votre instance.

Il fournit un tableau de bord de ce qui se produit sur votre instance :  son état (version de build, packages installés, etc.), les indicateurs système, les journaux, les workflows en cours d&#39;exécution, l&#39;état des dernières diffusions envoyées, etc.

Des informations détaillées sont disponibles [ici](../../production/using/monitoring-processes.md).

![](assets/monitoring_tab.png)

## Monitoring Campaign Classic processes {#monitoring-campaign-classic-processes}

D’autres moyens de surveillance des différents processus Campaign sont disponibles. Pour plus d&#39;informations, reportez-vous aux sections ci-dessous.

<table>
<tr><td><img src="assets/do-not-localize/instance_icon.svg" width="60px"><p><a href="#monitoring-instance">Surveillez votre instance</a></p></td>
<td><img src="assets/do-not-localize/workflow_icon.svg" width="60px"><p><a href="#moniroting-workflows">workflows d’analyse</a></p></td>
<td><img src="assets/do-not-localize/database_icon.svg" width="60px"><p><a href="#monitoring-database">Surveillance de la base de données</a></p></td>
<td><img src="assets/do-not-localize/delivery_icon.svg" width="60px"><p><a href="#monitoring-deliveries">Surveillance des diffusions</a></p></td></tr>
</table>

### Surveillance de votre instance {#monitoring-instance}

**Outils de surveillance automatique**

Plusieurs méthodes automatiques sont disponibles. pour vous aider à surveiller votre instance. Vous pouvez, par exemple, configurer des rapports par courriel avec des anomalies détectées, récupérer une liste d’indicateurs au format XML, etc. [Cliquez ici](../../production/using/monitoring-processes.md#automatic-monitoring) pour en savoir plus.

**Suivi**

La piste d’audit vous permet de visualiser l’historique complet des modifications liées aux options, workflows et schémas de votre instance. [Cliquez ici](../../production/using/audit-trail.md) pour en savoir plus.

**Panneau de contrôle**

Le Panneau de configuration vous permet de gérer plusieurs paramètres de votre instance : gérez les autorisations d’URL, vérifiez les détails de votre instance tels que les versions de création de vos serveurs, etc. Il vous permet également de surveiller l’espace disponible sur les serveurs SFTP connectés à votre instance. [Cliquez ici](https://docs.adobe.com/content/help/fr-FR/control-panel/using/control-panel-home.html) pour en savoir plus.

>[!NOTE]
>
>Veuillez noter que le Panneau de configuration est accessible uniquement aux administrateurs et disponible pour tous les clients utilisant des Adobes Managed Services.

### Surveillance des workflows {#monitoring-workflows}

**Carte thermique des workflows**

La carte de chaleur de flux de travaux fournit une représentation visuelle de tous les workflows qui s’exécutent sur votre instance. Il vous permet de surveiller facilement la charge sur l&#39;instance et de planifier les workflows en conséquence. [Cliquez ici](../../workflow/using/heatmap.md) pour en savoir plus.

**Suivi**

La piste d’audit vous permet de visualiser toutes les modifications apportées aux workflows, ainsi que leur état actuel. [Cliquez ici](../../production/using/audit-trail.md).

**Dépannage des Workflows**

Des actions spécifiques peuvent être exécutées en cas de problème lié à l’exécution d’un processus. [Cliquez ici](../../production/using/workflow-execution.md) pour en savoir plus

**Surveillance de l&#39;état du workflow**

De plus, vous pouvez créer un processus qui vous permettra de surveiller l&#39;état d&#39;un ensemble de workflows et d&#39;envoyer des messages récurrents aux superviseurs. [Cliquez ici](../../workflow/using/supervising-workflows.md) pour en savoir plus.

**Directives générales**

Suivez les directives et les bonnes pratiques en cas d’utilisation de workflows pour améliorer les performances. Pour plus d’informations, consultez les sections suivantes :
* [Bonnes pratiques relatives à l’utilisation des workflows](../../workflow/using/workflow-best-practices.md)
* [Surveiller l&#39;exécution des workflows](../../workflow/using/monitoring-workflow-execution.md)

### Suivre les diffusions {#monitoring-deliveries}

**Rapports SMTP**

Les rapports SMTP affichent les statistiques de diffusion et les erreurs SMTP par domaine. [Cliquez ici](../../production/using/monitoring-processes.md) pour en savoir plus.

**Bonnes pratiques**

[Les meilleures pratiques d’envoi et de conception](http://docs.campaign.adobe.com/doc/AC/getting_started/FR/deliveryBestPractices.html) de diffusions peuvent vous aider à améliorer leurs performances.

**Dépannage** des Diffusions Des actions spécifiques peuvent être effectuées en cas de problème avec des diffusions :
* [Problèmes de délivrabilité](../../production/using/performance-and-throughput-issues.md#deliverability_issues)
* [Problèmes liés à l&#39;affichage des images](../../production/using/image-display-issues.md)
* [Problèmes de performances des Diffusions](../../delivery/using/monitoring-a-delivery.md#performance_issues)
* [Problèmes](../../production/using/temporary-files.md) de fichiers temporaires - *sur les modèles d’hébergement locaux uniquement*

### Surveillance de la base de données {#monitoring-database}

**Workflow de Nettoyage de la base**

Le processus de nettoyage de la base de données vous permet de supprimer des données obsolètes de votre base de données. Il est recommandé d’éviter une croissance exponentielle de la base de données. [Cliquez ici](../../production/using/database-cleanup-workflow.md) pour en savoir plus.

**Dépannage des performances de la base de données**

Des actions spécifiques peuvent être effectuées en cas de problème lié aux performances des bases de données. [Cliquez ici](../../production/using/database-performances.md) pour en savoir plus.

**Maintenance de la base de données**

*modèles d’hébergement sur site et hybrides uniquement*

Nous vous recommandons d&#39;effectuer régulièrement la maintenance des bases de données afin d&#39;éviter une surconsommation d&#39;espace disque, affectant ainsi l&#39;accès aux bases de données. [Cliquez ici](../../production/using/recommendations.md) pour en savoir plus.

**Sauvegarde et restauration**

*modèles d’hébergement sur site et hybrides uniquement*

La sauvegarde est une opération primordiale afin de ne pas perdre de données en cas de problème (physique ou système) sur une machine. [Cliquez ici](../../production/using/backup.md) pour en savoir plus. La procédure de restauration est décrite dans [cette section](../../production/using/restoration.md).

## Principes techniques Campaign Classic {#campaign-classic-technical-principles}

Des ressources techniques sont disponibles dans la documentation Campaign Classic. Nous vous recommandons de vous familiariser avec ces sujets avant d’effectuer toute opération technique sur votre instance.

**Hébergement de modèles et de fonctionnalités**

* [Modèles d’hébergement Campaign Classic](../../installation/using/hosting-models.md)
* [Hébergement des capacités du modèle](https://helpx.adobe.com/fr/campaign/kb/acc-on-prem-vs-hosted.html)

**Paramétrage du serveur**

*Modèles d’hébergement sur site et hybrides uniquement*

* [Configurations de serveur obligatoires](../../installation/using/campaign-server-configuration.md)
* [Configuration du fichier Serverconf.xml](../../installation/using/the-server-configuration-file.md)
* [Configuration du serveur pour la délivrabilité](../../installation/using/email-deliverability.md)
* [Lignes de commande pour créer une instance et déclarer une base de données](../../installation/using/command-lines.md)

**Principes généraux**

* [Architecture Campaign Classic](../../production/using/general-architecture.md)
* [Modules Campaign Classic](../../production/using/operating-principle.md)
* [Options des Campaign Classic](../../installation/using/configuring-campaign-options.md)
* [Configuration du démarrage automatique des modules](../../production/using/administration.md)
* [Principe de configuration de Campaign](../../production/using/configuration-principle.md)
* [Procédures de dépannage](../../production/using/performance-and-throughput-issues.md)
