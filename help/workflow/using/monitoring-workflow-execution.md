---
product: campaign
title: Surveiller l’exécution des workflows
description: Surveiller l’exécution des workflows
feature: Workflows
hide: true
exl-id: d589180b-8e1d-4149-9b16-3f541018a41f
TQID: https://experienceleague.adobe.com/PdqoAAfpNfS1GIdnbtMkkm-2sd0GcidR99za2Nxgbfo
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a658c786-869b-4194-a780-2594d663addaid: c5474392-5419-4296-9e41-f6f4ce4f6e9b
subfeature_v2: id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cfid: ee25c34b-ea50-427b-9369-ba0a160f7d70id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22fid: d1110311-2ca4-442b-be37-088a6db845ee
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 2122
ht-degree: 100%

---

# Surveiller l’exécution des workflows {#monitoring-workflow-execution}



Cette section présente des informations sur la manière de surveiller l’exécution de vos workflows.

Vous trouverez également dans [cette section](supervising-workflows.md#supervising-workflows) un exemple de création d’un workflow qui permet de surveiller l’état d’un ensemble de workflows en pause, arrêtés ou en erreur.

En outre, les administrateurs de l’instance peuvent utiliser le **journal d’audit** pour vérifier les activités et les dernières modifications apportées aux workflows, c’est-à-dire l’état de vos workflows. Pour en savoir plus à ce sujet consultez le [Guide de production de Campaign Classic v7](../../production/using/audit-trail.md).

D’autres moyens de surveiller les différents processus de Campaign sont présentés dans le [Guide de production de Campaign Classic v7](../../production/using/monitoring-guidelines.md).

## Afficher la progression {#displaying-progress}

Vous pouvez suivre l&#39;exécution en affichant la progression à partir de l&#39;icône correspondante de la barre d&#39;outils.

L&#39;icône **[!UICONTROL Afficher la progression]** permet de matérialiser à l&#39;écran l&#39;exécution, l&#39;état et le résultat des activités.

![](assets/s_user_segmentation_toolbar_progr.png)

Lorsque cette option est sélectionnée, les activités exécutées apparaissent en bleu, les activités en attente clignotent, les avertissements sont affichés en orange et les erreurs en rouge.Cette option affiche également le résultat des activités sur leur transition sortante, suivi du libellé du résultat tel qu’il a été défini dans les propriétés de l’activité et de la durée du traitement, lorsqu’elle est supérieure à une seconde.

![](assets/s_user_segmentation_results.png)

## Afficher le log {#displaying-logs}

Le log contient l’historique ou le journal d’audit du workflow.Il enregistre toutes les actions des utilisateurs et utilisatrices, toutes les opérations effectuées et les erreurs rencontrées.Vous pouvez ainsi :

* Sélectionnez l’onglet **[!UICONTROL Tracking]** du détail.Cette liste contient tous les messages de workflow.

  ![](assets/new-workflow-display-log-tab.png)

* Filtrer les messages du log par activité. Pour ce faire, cliquez sur **[!UICONTROL Afficher les tâches et le log]** dans la barre d’outils située au-dessus du diagramme afin d’afficher les onglets **[!UICONTROL Log]** et **[!UICONTROL Tâches]** sous le diagramme. Sélectionnez une activité pour visualiser tous les messages associés. Cette liste contient tous les messages lorsqu’aucune activité n’est sélectionnée.

  ![](assets/new-workflow-display-log-activity.png)

  >[!NOTE]
  >
  >Cliquez sur l’arrière-plan du diagramme pour tout désélectionner.

* Affichez uniquement les messages liés à une tâche donnée. Pour ce faire, sélectionnez l’option **[!UICONTROL Tâche]**, puis sélectionnez une activité dans le diagramme afin de restreindre la liste. Double-cliquez sur une tâche pour afficher les informations ; le dernier onglet de la fenêtre contient le log.

  ![](assets/new-workflow-display-tasks-activity.png)

  Le bouton **[!UICONTROL Détails…]** vous permet d’afficher toutes les informations complémentaires relatives à l’exécution de l’activité.Vous pouvez par exemple visualiser l’opérateur ou l’opératrice validant et éventuellement le commentaire saisi lors de la validation, comme dans l’exemple ci-dessous :

  ![](assets/new-workflow-display-tasks-activity-details.png)

>[!NOTE]
>
>Le log n’est pas purgé lors du redémarrage d’un workflow.Tous les messages sont conservés.Si ne vous pas conserver les messages d’une exécution précédente, vous devez purger l’historique.

Le log affiche la liste chronologique des messages d&#39;exécution des activités du workflow de ciblage.

* Log d&#39;une campagne de ciblage

  Lorsqu&#39;une opération de ciblage a été exécutée, cliquez sur l&#39;onglet **[!UICONTROL Suivi]** pour consulter la trace de l&#39;exécution.

  ![](assets/s_user_segmentation_journal.png)

  Tous les messages de l&#39;opération sont affichés: les opérations réalisées et les avertissements ou les erreurs d&#39;exécution.

* Log d&#39;une activité

  Vous pouvez également visualiser le log et les détails d’exécution de chaque activité.Vous avez le choix entre les deux méthodes suivantes :

   1. Sélectionnez l&#39;activité visée et cliquez sur l&#39;icône **[!UICONTROL Afficher les tâches et le log]**.

      ![](assets/s_user_segmentation_show_logs.png)

      La section inférieure du diagramme affiche alors deux onglets : Log et Tâches.

      La sélection d&#39;une activité sur le diagramme agit comme un filtre sur le log et la liste des tâches.

      ![](assets/s_user_segmentation_logs.png)

   1. Cliquez sur l&#39;activité visée avec le bouton droit de la souris et choisissez **[!UICONTROL Afficher le log]**.

      ![](assets/s_user_segmentation_logs_menu.png)

      Le log est alors affiché dans une fenêtre distincte.

## Purger l&#39;historique {#purging-the-logs}

L’historique d’un workflow n’est pas purgé automatiquement : tous les messages sont conservés par défaut. L’historique peut être purgé via le menu **[!UICONTROL Fichier > Actions]** ou en cliquant sur le bouton **[!UICONTROL Actions]** situé dans la barre d’outils au-dessus de la liste. Sélectionnez **[!UICONTROL Purger l’historique]**. Les options disponibles dans le menu **[!UICONTROL Actions]** sont détaillées dans la section [Barre d’outils des actions](starting-a-workflow.md).

![](assets/purge_historique.png)

## Tables de travail et schémas des workflows {#worktables-and-workflow-schema}

Le workflow véhicule des tables de travail qui peuvent être manipulées via certaines activités.Adobe Campaign permet, via les activités de Data Management, de modifier, renommer et enrichir les colonnes des tables de travail du workflow, par exemple pour les aligner sur la nomenclature en fonction des besoins du client ou de la cliente, collecter des informations complémentaires sur la personne co-titulaire d’un contrat, etc.

Il est également possible de créer des liens entre des dimensions de travail différentes et de définir des changements de dimension.Par exemple, pour chaque contrat enregistré dans la base de données, s’adresser à la personne titulaire principale et utiliser les données relatives à la ou aux personnes co-titulaires dans les informations complémentaires.

Les tables de travail du workflow sont automatiquement supprimées lorsque le workflow est passif. Si vous souhaitez conserver une table de travail, enregistrez-la dans une liste via l’activité **[!UICONTROL Mise à jour de liste]** (voir [Mise à jour de liste](list-update.md)).

## Gérer les erreurs {#managing-errors}

Lorsqu’une erreur se produit, le workflow se met en pause et l’activité qui était en cours d’exécution lorsque l’erreur s’est produite clignote alors en rouge. Dans la vue d’ensemble du workflow, sous l’onglet **[!UICONTROL Supervision]** et le lien **[!UICONTROL Workflows]**, vous pouvez afficher les workflows avec des erreurs uniquement, comme illustré ci-dessous.

![](assets/wf-global-view_filter_only_errors.png)

Dans l’explorateur Adobe Campaign, la liste des workflows affiche par défaut une colonne **[!UICONTROL En échec]**.

![](assets/wf-explorer_errors_col.png)

Lorsqu’un workflow est en erreur, les opérateurs et opératrices appartenant au groupe de supervision du workflow reçoivent une notification par e-mail, pour autant que leur adresse e-mail soit indiquée dans leur profil. Ce groupe est sélectionné dans le champ **[!UICONTROL Personnes chargées de la supervision]** des propriétés de workflow.

![](assets/wf-properties_select-supervisors.png)

Le contenu de la notification est configuré dans le modèle par défaut **[!UICONTROL Notification de la personne responsable d’un workflow]** : ce modèle est sélectionné dans l’onglet **[!UICONTROL Exécution]** des propriétés du workflow.La notification indique le nom du workflow en erreur et la tâche concernée.

Exemple de notification :

![](assets/wf-notification_error-msg.png)

Le lien permet d&#39;accéder en Web à la console Adobe Campaign et, après connexion, d&#39;agir sur le workflow en erreur.

![](assets/wf-notification_error-console.png)

Vous pouvez paramétrer le workflow pour qu’il ne se mette pas en pause et continue son exécution en cas d’erreur. Pour ce faire, modifiez les **[!UICONTROL Propriétés]** du workflow et dans la section **[!UICONTROL Gestion des erreurs]**, sélectionnez **[!UICONTROL Ignorer]** dans le champ **[!UICONTROL En cas d’erreur]**. Vous pouvez indiquer le nombre d’erreurs qui peuvent être ignorées avant la suspension du processus.

Dans ce cas, la tâche en erreur est abandonnée.Ce mode est particulièrement adapté aux workflows conçus pour retenter la campagne ultérieurement (actions périodiques).

![](assets/wf_edit_properties_for_error_mgt.png)

>[!NOTE]
>
>Vous pouvez appliquer ce paramétrage au niveau de chaque activité. Pour ce faire, modifiez les propriétés de l’activité et sélectionnez le mode de gestion des erreurs dans l’onglet **[!UICONTROL Avancé]**.

Pour plus d’informations sur la résolution des problèmes d’exécution des workflows, consultez le [Guide de production de Campaign Classic v7](../../production/using/workflow-execution.md).

## Traiter les erreurs {#processing-errors}

Au niveau des activités, l’option **[!UICONTROL Traiter les erreurs]** fait apparaître une transition particulière qui sera activée si une erreur est générée.Dans ce cas, le workflow ne passe pas en état d’erreur et l’exécution se poursuit.

Les erreurs prises en compte sont les erreurs du système de fichiers (impossible de déplacer un fichier, impossible d&#39;accéder au répertoire, etc.).

Cette option ne traite pas les erreurs liées au paramétrage de l&#39;activité, c&#39;est-à-dire des valeurs invalides. Les erreurs liées à une mauvaise configuration n’activeront pas cette transition (répertoire inexistant, etc.).

Si un workflow est en mis en pause (manuellement ou automatiquement suite à une erreur), le bouton **[!UICONTROL Démarrer]** permet de redémarrer l’exécution du workflow là où elle s’est arrêtée.L’activité en erreur (ou en pause) sera exécutée à nouveau.Les activités précédentes ne sont pas exécutées à nouveau.

Pour exécuter à nouveau toutes les activités du workflow, utilisez le bouton **[!UICONTROL Redémarrer]**.

Si vous effectuez des modifications sur les activités déjà exécutées, elles ne sont pas prises en compte lorsque lexécution du workflow redémarre.

Si vous effectuez des modifications sur les activités non exécutées, elles sont prises en compte lorsque lexécution du workflow redémarre.

Si vous effectuez des modifications sur lactivité en pause, elles peuvent ne pas être correctement prises en compte lors du redémarrage du workflow.

Si possible, il est recommandé de le redémarrer complètement après avoir effectué des modifications.

## Supervision de l&#39;instance {#instance-supervision}

La page **[!UICONTROL Supervision de l’instance]** permet de visualiser l’activité du serveur Adobe Campaign et de consulter la liste des workflows et des diffusions contenant des erreurs.

Pour accéder à cette page, allez dans l’onglet **[!UICONTROL Supervision]** et cliquez sur le lien **[!UICONTROL Vue générale]**.

![](assets/wf-monitoring_from-homepage.png)

Pour afficher tous les workflows, cliquez sur le lien **[!UICONTROL Workflows]**.Utilisez la liste déroulante pour afficher les workflows de la plateforme selon leur état.

![](assets/wf-monitoring_edit-wf.png)

Lorsqu&#39;un workflow est en erreur, cliquez sur le lien pour l&#39;ouvrir et visualiser le log.

![](assets/wf-monitoring_edit-task-wf.png)

## Empêcher les exécutions multiples simultanées {#preventing-simultaneous-multiple-executions}

Il peut arriver que plusieurs exécutions opèrent en même temps sur un même workflow.Dans certains cas, ce processus doit être empêché.

Par exemple, il se peut qu’un planificateur déclenche l’exécution du workflow une fois par heure, mais parfois, l’exécution du workflow dans son ensemble dure plus d’une heure. Vous pouvez ignorer l’exécution si le workflow est déjà en cours d’exécution.

En cas de présence d&#39;une activité signal au début du workflow,il peut être préférable de passer le signal si le workflow est déjà en cours d&#39;exécution.

Le principe général est le suivant :

![](assets/workflow-reentrancy-protection-principle.png)

La solution consiste à utiliser une variable d’instance.Les variables d’instance sont partagées par toutes les exécutions parallèles des workflows.

Voici un workflow de test simple :

![](assets/wkf_simultaneous_execution1.png)

Le **[!UICONTROL Planificateur]** déclenche un événement toutes les minutes. L’activité **[!UICONTROL Test]** suivante va tester la variable d’instance **isRunning** pour décider si l’exécution doit se poursuivre ou non :

![](assets/wkf_simultaneous_execution2.png)

>[!NOTE]
>
>**isRunning** est un nom de variable choisi pour cet exemple.Il ne s’agit pas d’une variable intégrée.

L&#39;activité qui suit le **[!UICONTROL Test]** dans la branche **oui** doit configurer la variable d&#39;instance dans son **Script d&#39;initialisation** :

```
instance.vars.isRunning = true
```

La dernière activité de la branche **oui** doit rétablir le statut faux de la variable dans son **Script d&#39;initialisation** :

```
instance.vars.isRunning = false
```

Notez que :

* La valeur actuelle de la variable d&#39;instance est visible dans l&#39;onglet **Variables** des **Propriétés** du workflow.
* Les variables dinstance sont remise à zéro lorsquun workflow est redémarré.
* Dans JavaScript, une valeur non définie est considérée comme fausse dans un test, ce qui permet de tester la variable d&#39;instance avant même de l&#39;avoir initiée.
* Il est possible de surveiller les activités non traitées par ce mécanisme en ajoutant une consigne d&#39;enregistrement au script d&#39;initialisation de la fin « non ».

  ```
  logInfo("Workflow already running, parallel execution not allowed.");
  ```

Cette section présente un cas d’utilisation : [Coordonner les mises à jour des données](coordinating-data-updates.md).

## Maintenance de la base de données {#database-maintenance}

Les workflows utilisent beaucoup de tables de travail qui occupent de l&#39;espace et finissent par ralentir l&#39;ensemble de la plateforme s&#39;ils ne sont pas maintenus. Pour plus d&#39;informations sur la maintenance des bases de données, voir cette [section](../../production/using/tables-to-maintain.md).

Le workflow **Nettoyage de la base de données**, accessible à partir du nœud **Administration > Exploitation > Workflows techniques**, vous permet de supprimer les données obsolètes afin d’éviter une croissance exponentielle de la base de données.Le workflow se déclenche automatiquement sans intervention de l’utilisateur ou de l’utilisatrice.Voir [Guide de production de Campaign Classic v7](../../production/using/database-cleanup-workflow.md).

Vous pouvez également créer des workflows techniques spécifiques pour purger les données inutiles qui occupent de l’espace. Reportez-vous au [Guide de production de Campaign Classic v7](../../production/using/application-objects.md) et à cette [section](#purging-the-logs).

## Gérer les workflows en pause {#handling-of-paused-workflows}

Par défaut, si un workflow est en pause, ses tables de travail ne sont jamais purgées.Depuis le build 8880, les workflows ayant été dans un état « en pause » pendant trop longtemps sont automatiquement arrêtés et leurs tables de travail sont purgées.Ce comportement est déclenché comme suit :

* Les workflows qui sont en pause depuis plus de 7 jours apparaissent sous la forme d’un avertissement dans le tableau de bord de surveillance (et l’API de surveillance) et une notification est envoyée au groupe des personnes chargées de la supervision.
* Cette situation se produit chaque semaine, lorsque le workflow technique **[!UICONTROL cleanupPausedWorkflows]** est déclenché. Pour plus d’informations sur le workflow, reportez-vous à [cette section](delivery.md).
* Après 4 notifications (un mois en pause par défaut), le workflow est arrêté de manière inconditionnelle. Un log s’affiche dans le workflow après son arrêt. Les tables sont purgées lors de la prochaine exécution du workflow **[!UICONTROL de nettoyage]**

Ces périodes peuvent être configurées à l&#39;aide de l&#39;option NmsServer_PausedWorkflowPeriod.

Les personnes responsables des workflows sont averties.Le créateur ou la créatrice et la dernière personne ayant modifié le workflow sont également informés.Les administrateurs et administratrices ne reçoivent pas les notifications.

## Filtrer des workflows en fonction de leur état {#filtering-workflows-status}

L’interface de Campaign Classic vous permet de surveiller l’état d’exécution de tous les workflows de votre instance à l’aide de **vues** prédéfinies. Pour accéder à ces vues, ouvrez le nœud **[!UICONTROL Administration]** / **[!UICONTROL Audit]** / **[!UICONTROL Statut des workflows]**.

Les vues disponibles sont les suivantes :

* **[!UICONTROL En cours d’exécution]** : répertorie tous les workflows en cours d’exécution.
* **[!UICONTROL En pause]** : répertorie tous les workflows en pause.
* **[!UICONTROL Échec]** : répertorie tous les workflows en échec.
* **[!UICONTROL Démarrage en attente]** : répertorie tous les workflows en attente de démarrage par le processus operationMgt. Cette vue est disponible avec le package **Campagnes marketing** uniquement. Pour en savoir plus, consultez le [Guide d’installation de Campaign Classic v7](../../installation/using/installing-campaign-standard-packages.md)).

![](assets/workflow-monitoring-views.png)

Par défaut, ces vues sont accessibles dans le dossier **[!UICONTROL Audit]**. Vous pouvez toutefois les recréer à l’emplacement de votre choix dans l’arborescence des dossiers. De cette manière, ils seront accessibles aux utilisateurs standard sans droit d’administration.

Pour cela :

1. Cliquez avec le bouton droit sur le dossier dans lequel vous souhaitez ajouter la vue.
1. Dans **[!UICONTROL Ajouter un dossier]** / **[!UICONTROL Administration]**, sélectionnez la vue à ajouter.
1. Une fois le dossier ajouté à l’arborescence, assurez-vous de le configurer en tant que vue afin qu’il affiche tous les workflows, quel que soit leur dossier d’origine. Pour plus d’informations sur la configuration des vues, consultez [cette section](../../platform/using/about-adobe-campaign-classic.md).

En outre, vous pouvez configurer des dossiers de filtres qui vous permettront de filtrer la liste des workflows en fonction de leur état d’exécution. Pour ce faire :

1. Accédez à un dossier de type workflow, puis sélectionnez le menu **[!UICONTROL Filtres]**/**[!UICONTROL Filtres avancés]**.
1. Configurez le filtre de sorte que le champ **[!UICONTROL @status]** du workflow soit égal à l’état de votre choix.
1. Enregistrez le filtre et attribuez-lui un nom. Il sera alors directement disponible dans la liste des filtres.

![](assets/workflow-monitoring-filter.png)

Pour plus d’informations sur les filtres, consultez la [documentation de Campaign v8 (console)](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/audience/create-filters){target=_blank}.
