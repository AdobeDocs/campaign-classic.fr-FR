---
title: Carte thermique des workflows
description: Surveillez vos Workflows de campagne avec Workflow HeatMap
page-status-flag: never-activated
uuid: 4d215ff4-a61d-4294-8f15-17c612022577
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 6a71f5ee-c8e0-4ac4-acae-6dffbf799d0c
translation-type: tm+mt
source-git-commit: 6be6c353c3464839a74ba857d8d93d0f68bc8865
workflow-type: tm+mt
source-wordcount: '1399'
ht-degree: 98%

---


# Carte thermique des workflows {#workflow-heatmap}

Adobe Campaign Workflow HeatMap consiste en une représentation graphique codée par couleur de tous les workflows en cours d&#39;exécution. Elle est disponible uniquement pour les administrateurs de l’instance.

D’autres méthodes de surveillance des différents processus de Campaign sont présentées dans [cette page](../../production/using/monitoring-guidelines.md).

## A propos de la carte thermique des workflows {#about-the-workflow-heatmap}

En donnant un aperçu rapide du nombre de workflows simultanés, la carte thermique des workflows permet aux administrateurs de la plateforme Adobe Campaign de surveiller la charge de l&#39;instance et de planifier les workflows en conséquence.

Elle permet plus précisément aux administrateurs de la plate-forme d’effectuer les opérations suivantes :

* afficher et analyser les workflows simultanés ;
* filtrer les workflows par durée pour déterminer ceux risquant de rencontrer des problèmes ;
* filtrer les activités par durée pour déterminer celles risquant de rencontrer des problèmes ;
* trouver facilement des workflows distincts et toutes les activités associées (avec leur durée) ;
* effectuer une recherche par type de workflow ([workflows techniques](../../workflow/using/building-a-workflow.md#technical-workflows) ou [workflows de campagne](../../workflow/using/building-a-workflow.md#campaign-workflows)) ;
* rechercher un workflow spécifique à analyser.

>[!NOTE]
>
>Outre la **carte thermique des workflows**, vous pouvez créer un workflow qui vous permettra de surveiller le statut d’un ensemble de workflows et d’envoyer des messages récurrents aux superviseurs. Voir à ce sujet la [section dédiée](../../workflow/using/supervising-workflows.md).

L’utilisation de la carte thermique des workflows demande une bonne maîtrise des concepts suivants : [Workflows](../../workflow/using/about-workflows.md), [Activités](../../workflow/using/about-activities.md) et [Bonnes pratiques relatives aux workflows](../../workflow/using/workflow-best-practices.md).

La carte thermique des workflows est disponible par défaut dans Adobe Campaign à compter de la version 18.10. Si vous disposez d’un build entre 8700 et 8977 (18.10), vous pouvez également bénéficier de cette fonctionnalité. Pour demander le package correspondant, contactez l’[Assistance clientèle Adobe](https://support.neolane.net/) et suivez les instructions sur [cette page](https://helpx.adobe.com/fr/campaign/kb/install-workflow-heatmap-package.html) pour savoir comment l’installer.

Lors de votre premier accès à la carte thermique des workflows, la fenêtre contextuelle suivante apparaît. Cet accord autorise le transfert et le stockage aux États-Unis pour permettre à Adobe Campaign de :

* surveiller les instances pour enquêter sur tout problème de performance ;
* collecter des données afin de détecter des anomalies.

Notez que le transfert de vos données est uniquement disponible pour les utilisateurs qui se connectent à Adobe Campaign au moyen de leur Adobe ID.

![](assets/wf_monitoring_agreement.png)

Trois options sont disponibles :

* **[!UICONTROL Accepter]** : en acceptant cet accord, vous autorisez Adobe Campaign à collecter vos données et à les transférer aux États-Unis afin de vous aider si des anomalies sont détectées.
* **[!UICONTROL Refuser]** : si vous refusez l’accord, vos données ne seront pas transférées, mais vous pourrez continuer à utiliser la carte thermique des workflows.
* **[!UICONTROL Ne plus afficher ce message]** : si vous cliquez sur **[!UICONTROL Ne plus afficher ce message]**, la fenêtre contextuelle n’apparaîtra plus lorsque vous accéderez à la carte thermique des workflows, mais elle restera accessible au moyen du bouton **[!UICONTROL Conditions d’utilisation]**.

Ce choix n’est pas définitif, vous pouvez toujours le modifier en cliquant sur le bouton **[!UICONTROL Conditions d’utilisation]**.

## Utilisation de la carte thermique {#using-the-heatmap}

>[!NOTE]
>
>Seuls les utilisateurs disposant de droits d&#39;administration peuvent accéder à la Carte thermique des workflows Campaign.

1. Accédez à **[!UICONTROL Suivi]**, puis cliquez sur le lien **[!UICONTROL Carte thermique des workflows]** pour afficher la page **[!UICONTROL Carte thermique des workflows Campaign]**.

   ![](assets/wkf_monitoring_path.png)

1. Cliquez sur le calendrier pour sélectionner un jour.

   Par défaut, la page affiche l&#39;activité des workflows pour le jour en cours. Vous pouvez le changer et sélectionner n&#39;importe quel jour précédent.

   >[!NOTE]
   >
   >Seuls les workflows qui n&#39;ont pas été supprimés par le workflow **[!UICONTROL Nettoyage de la base]** sont visibles. Pour plus d&#39;informations sur le workflow Nettoyage de la base, consultez [cette section](../../production/using/database-cleanup-workflow.md).\
   >Par défaut, le fuseau horaire de la carte thermique des workflows est celui défini pour l&#39;utilisateur administrateur actuel. Vous pouvez vouloir le changer si, par exemple, vous ne vous trouvez pas dans la même zone géographique que les utilisateurs marketing avec lesquels vous travaillez.

1. Cliquez sur le bouton **[!UICONTROL Filtres]**.

   ![](assets/wkf_monitoring_filters.png)

1. Utilisez le curseur pour définir la durée minimale de 0 seconde à 1 heure. Vous pouvez ainsi rechercher uniquement des workflows exécutés pendant plus d&#39;un certain nombre de secondes ou de minutes.

   ![](assets/wkf_monitoring_filters_duration.png)

1. Vous pouvez également sélectionner un workflow spécifique dans la liste **[!UICONTROL Workflows]**.

   ![](assets/wkf_monitoring_filters_workflows.png)

   >[!NOTE]
   >
   >Le filtre **[!UICONTROL Durée min.]** est appliqué. Si vous ne parvenez pas à trouver un workflow spécifique, réinitialisez la durée minimale à 0 afin que tous les workflows soient affichés dans la liste.

1. Vous pouvez également appliquer un filtre selon le **[!UICONTROL Type de workflow]** :

   * **[!UICONTROL Technique]** : seuls les [workflows techniques d&#39;usine](../../workflow/using/building-a-workflow.md#technical-workflows) et les [workflows de Data Management](../../workflow/using/targeting-data.md#data-management) s&#39;affichent.
   * **[!UICONTROL Marketing]** : seuls les workflows associés à une campagne marketing, appelés [workflows de campagne](../../workflow/using/building-a-workflow.md#campaign-workflows), s&#39;affichent.

1. Pour rechercher un workflow spécifique par nom, vous pouvez également utiliser le champ **[!UICONTROL Filtre de nom de workflow]**.

   ![](assets/wkf_monitoring_filters_name.png)

1. Si vous avez édité certains workflows entre temps, cliquez sur le bouton **[!UICONTROL Recharger les données]** pour actualiser les données affichées dans la grille.

## Lecture de la carte thermique {#reading-the-heatmap}

La Carte thermique des workflows Campaign est une grille qui se lit naturellement en commençant en haut à gauche pour terminer en bas à droite. Il est possible de trouver les &quot;zones chaudes&quot; avec un code-couleur allant du vert au rouge.

* Les cellules d&#39;un rouge plus foncé correspondent aux périodes pendant lesquelles un grand nombre de workflows s&#39;exécutent simultanément.
* Les cellules grises correspondent aux périodes pendant lesquelles aucun workflow ne s&#39;exécute.

Pour découvrir comment le code-couleur est appliqué et comment parcourir la carte thermique, cliquez sur le bouton **[!UICONTROL Aide]**.

![](assets/wkf_monitoring_legend.png)

Chaque ligne représente une heure de la journée et chaque cellule, 5 minutes de cette heure.

La grille affiche tous les workflows exécutés à la même heure pour chacune de ces périodes de 5 minutes.

Dans l&#39;exemple suivant, trois workflows sont en cours d&#39;exécution (quelle que soit leur durée) entre 8h00 et 8h05 :

![](assets/wkf_monitoring_ex_8am.png)

1. Cliquez sur une cellule en couleur pour afficher les détails de tous les workflows simultanés exécutés pendant cette période.

   ![](assets/wkf_monitoring_details.png)

   Toutes les activités de chaque workflow sont répertoriées, avec leur durée.

1. Cliquez sur l&#39;identifiant ou le nom d&#39;un workflow pour l&#39;ouvrir directement.
1. Pour revenir à la vue **[!UICONTROL Carte thermique des workflows Campaign]**, cliquez sur le bouton **[!UICONTROL Accueil]**.

## Cas pratiques : utilisation de la carte thermique pour prendre des mesures {#use-cases--using-the-heatmap-to-take-actions}

La Carte thermique des workflows Campaign peut s&#39;avérer utile dans deux principaux scénarios.

### Réduction du nombre de workflows simultanés {#reducing-the-number-of-concurrent-workflows}

En tant qu&#39;administrateur de Campaign, la carte thermique des workflows peut vous aider à analyser la charge de l&#39;instance et à planifier les workflows existants ou nouveaux aux moments appropriés.

1. Dans la vue **[!UICONTROL Carte thermique des workflows Campaign]**, cliquez sur le bouton **[!UICONTROL Filtres]**.
1. Définissez la durée sur quelques secondes ou minutes.
1. Excluez les workflows les plus courts n&#39;étant pas significatifs en augmentant le filtre de durée.

   ![](assets/wkf_monitoring_short_duration.png)

1. Examinez les résultats pour analyser la charge de l&#39;instance, puis prenez les mesures adéquates :

   * Si vous rencontrez des problèmes de performances et si la grille contient une ou plusieurs cellules rouges, songez à modifier les heures de début de plusieurs workflows. Demandez aux utilisateurs marketing de déplacer manuellement les workflows des périodes surchargées (&quot;chaudes&quot;) vers des créneaux horaires moins chargés. Un niveau d&#39;activité stable devrait ainsi être maintenu tout au long de la journée.
   * Pour éviter les pics et la surcharge de l&#39;instance, examinez la carte thermique avant de planifier de nouveaux workflows et choisissez le meilleur horaire. Prenez en compte les créneaux horaires correspondant aux cellules grises ou vertes de la grille pour démarrer de nouveaux workflows.

### Recherche des workflows de longue durée ayant une incidence sur les performances {#finding-long-running-workflows-that-impact-performance}

En tant qu&#39;administrateur de Campaign, la carte thermique des workflows vous permet de trouver les workflows les plus longs pouvant ralentir l&#39;activité.

1. Dans la vue **[!UICONTROL Carte thermique des workflows Campaign]**, cliquez sur le bouton **[!UICONTROL Filtres]**.
1. Définissez la durée sur 1 heure.

   ![](assets/wkf_monitoring_long_duration.png)

1. Incluez d&#39;autres résultats en diminuant le filtre **[!UICONTROL Durée min.]**.
1. Examinez les résultats pour trouver les workflows les plus longs, susceptibles d&#39;avoir un impact plus important sur les ressources du serveur et de la base de données (CPU, RAM, réseau, IOPS, etc.).
1. Prenez les mesures adéquates :

   * Conseillez aux utilisateurs marketing de scinder les workflows les plus longs afin de réduire la durée de traitement.
   * Effectuez une analyse plus approfondie de workflows et d&#39;activités spécifiques (JavaScript, import, export, etc.) pour isoler les problèmes et les résoudre plus facilement.

## Exemple : utilisation de la carte thermique pour une meilleure planification des workflows {#example--using-the-heatmap-to-improve-workflow-planning}

L&#39;exemple ci-dessous montre comment rendre la planification plus efficace et améliorer les performances grâce à l&#39;utilisation de la Carte thermique des workflows d&#39;Adobe Campaign.

Dans ce cas pratique, de nombreux utilisateurs se plaignent des performances des workflows. Vous devez rechercher ce qui ralentit l&#39;activité et comment résoudre le problème.

1. Accédez à **[!UICONTROL Suivi]**, puis cliquez sur le lien **[!UICONTROL Workflows]** pour afficher la page **[!UICONTROL Carte thermique des workflows Campaign]**.
1. Définissez le filtre **[!UICONTROL Durée min.]** sur 5 minutes.
1. Définissez le filtre **[!UICONTROL Type de workflow]** sur **[!UICONTROL Marketing]** .
1. Dans la grille de la carte thermique, notez les points suivants :

   ![](assets/wkf_monitoring_without.png)

   * 50 workflows de campagne de longue durée (plus de 5 minutes) sont exécutés à 10h00.
   * La plupart d&#39;entre eux ont un statut en attente (par défaut, la limite de la simultanéité est définie sur 20).
   * Les workflows en attente doivent être redémarrés manuellement tous les jours.
   * Les performances sont faibles.

1. Au lieu d&#39;avoir 50 workflows commençant à 10h00, répartissez les heures de début de manière uniforme sur le reste de la journée.
1. Retournez dans la page **[!UICONTROL Carte thermique des workflows Campaign]**, puis cliquez sur le bouton **[!UICONTROL Recharger les données]**.
1. Notez maintenant les points suivants :

   ![](assets/wkf_monitoring_with.png)

   * Seuls 18 workflows de campagne de longue durée s&#39;exécutent toujours à 10h00.
   * Aucun workflow n&#39;est en attente (la limite de la simultanéité est toujours définie sur 20).
   * Les heures de début des workflows sont uniformément réparties tout au long de la journée.
   * Aucun utilisateur ne se plaint de problèmes de performances.
