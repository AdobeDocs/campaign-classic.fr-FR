---
title: Workflow de Nettoyage de la base
seo-title: Workflow de Nettoyage de la base
description: Workflow de Nettoyage de la base
seo-description: null
page-status-flag: never-activated
uuid: a7478641-cdf6-4bd4-9dd7-0c84416c9de6
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: data-processing
discoiquuid: 6b188d78-abb4-4f03-80b9-051ce960f43c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d5813af76e3cad16d9094a19509dcb855e36c01f

---


# Workflow de Nettoyage de la base{#database-cleanup-workflow}

## Introduction {#introduction}

Le **[!UICONTROL Database cleanup]** flux de travail accessible via le **[!UICONTROL Administration > Production > Technical workflows]** noeud permet de supprimer des données obsolètes afin d’éviter une croissance exponentielle de la base de données. Le processus est déclenché automatiquement sans intervention de l’utilisateur.

![](assets/ncs_cleanup_workflow.png)

## Configuration {#configuration}

Le paramétrage du nettoyage de la base s&#39;effectue à deux niveaux : dans le planificateur du workflow et dans l&#39;assistant de déploiement.

### Le planificateur {#the-scheduler}

>[!NOTE]
>
>Pour plus d’informations sur le planificateur, reportez-vous à [cette section](../../workflow/using/scheduler.md).

Par défaut, le **[!UICONTROL Database cleanup]** processus est configuré pour démarrer tous les jours à 4 heures du matin. Le planificateur vous permet de modifier la fréquence de déclenchement du processus. Les fréquences suivantes sont disponibles :

* **[!UICONTROL Several times a day]**
* **[!UICONTROL Daily]**
* **[!UICONTROL Weekly]**
* **[!UICONTROL Once]**

![](assets/ncs_cleanup_scheduler.png)

>[!CAUTION]
>
>Pour que le **[!UICONTROL Database cleanup]** flux de travaux commence à la date et à l’heure définies dans le planificateur, le moteur de flux de travaux (wfserver) doit être démarré. Si ce n&#39;est pas le cas, le nettoyage de la base de données n&#39;aura lieu qu&#39;au prochain démarrage du moteur de flux de travail.

### L&#39;assistant de déploiement {#deployment-wizard}

Le **[!UICONTROL Deployment wizard]** , accessible par le **[!UICONTROL Tools > Advanced]** menu, vous permet de configurer la durée d’enregistrement des données. Les valeurs sont exprimées en jours. Si ces valeurs ne sont pas modifiées, le processus utilise les valeurs par défaut.

![](assets/ncs_cleanup_deployment-wizard.png)

Les champs de la **[!UICONTROL Purge of data]** fenêtre coïncident avec les options suivantes. Elles sont utilisées par certaines des tâches exécutées par le **[!UICONTROL Database cleanup]** processus :

* Suivi consolidé : **NmsCleanup_TrackingStatPurgeDelay** (voir [Nettoyage des journaux](#cleanup-of-tracking-logs)de suivi)
* Journaux de remise : **NmsCleanup_BroadLogPurgeDelay** (voir [Nettoyage des journaux](#cleanup-of-delivery-logs)de remise)
* Journaux de suivi : **NmsCleanup_TrackingLogPurgeDelay** (voir [Nettoyage des journaux](#cleanup-of-tracking-logs)de suivi)
* Livraisons supprimées : **NmsCleanup_RecycledDeliveryPurgeDelay** (voir [Nettoyage des livraisons à supprimer ou à recycler](#cleanup-of-deliveries-to-be-deleted-or-recycled))
* Rejetons d’importation : **NmsCleanup_RejectsPurgeDelay** (voir [Nettoyage des rejets générés par les importations](#cleanup-of-rejects-generated-by-imports-))
* Profils des visiteurs : **NmsCleanup_VisitorPurgeDelay** (voir [Nettoyage des visiteurs](#cleanup-of-visitors))
* Propositions d’offre : **NmsCleanup_PropositionPurgeDelay** (voir [Nettoyage des propositions](#cleanup-of-propositions))

   >[!NOTE]
   >
   >The **[!UICONTROL Offer propositions]** field is only available when the **Interaction** module is installed.

* Evénements : **NmsCleanup_EventPurgeDelay** (voir [Nettoyage des événements](#cleansing-expired-events)expirés)
* Evénements archivés : **NmsCleanup_EventHistoPurgeDelay** (voir [Nettoyage des événements](#cleansing-expired-events)expirés)

   >[!NOTE]
   >
   >The **[!UICONTROL Events]** and **[!UICONTROL Archived events]** fields are only available if the **Message Center** module is installed.

* Piste d’audit : **XtkCleanup_AuditTrailPurgeDelay** (voir [Nettoyage de la piste](#cleanup-of-audit-trail)d’audit)

All tasks executed by the **[!UICONTROL Database cleanup]** workflow are described in the following section.

## Tâches effectuées par le workflow Nettoyage de la base {#tasks-carried-out-by-the-database-cleanup-workflow}

À la date et à l’heure définies dans le planificateur de flux de travail (voir [Le planificateur](#the-scheduler)), le moteur de flux de travail lance le processus de nettoyage de la base de données. Le nettoyage de la base de données se connecte à la base de données et exécute les tâches dans l’ordre indiqué ci-dessous.

>[!CAUTION]
>
>Si l&#39;une de ces tâches échoue, les tâches suivantes ne seront pas exécutées.\
>SQL queries with a **LIMIT** attribute will be executed repeatedly until all information is processed.

>[!NOTE]
>
>Les sections ci-dessous décrivant les tâches effectuées par le workflow Nettoyage de la base sont réservées aux administrateurs de bases de données ou aux utilisateurs familiarisés avec le langage SQL.

### Nettoyage des listes à supprimer {#lists-to-delete-cleanup}

La première tâche exécutée par le **[!UICONTROL Database cleanup]** processus supprime tous les groupes avec **deleteStatus != attribut 0** du **NmsGroup**. Les enregistrements liés à ces groupes et qui existent dans d&#39;autres tableaux sont également supprimés.

1. Les listes à supprimer sont récupérées à l&#39;aide de la requête SQL suivante :

   ```
   SELECT iGroupId, sLabel, iType FROM NmsGroup WHERE iDeleteStatus <> 0 OR tsExpirationDate <= GetDate() 
   ```

1. Chaque liste possède plusieurs liens vers d&#39;autres tables. Tous ces liens sont supprimés en masse à l&#39;aide de la requête suivante :

   ```
   DELETE FROM $(relatedTable) WHERE iGroupId=$(l) IN (SELECT iGroupId FROM $(relatedTable) WHERE iGroupId=$(l) LIMIT 5000) 
   ```

   where **$(relatedTable)** is a table related to **NmsGroup** and **$(l)** is the list identifier.

1. Lorsque la liste est de type &#39;Liste&#39;, la table associée est supprimée à l&#39;aide de la requête suivante :

   ```
   DROP TABLE grp$(l)
   ```

1. Chaque liste récupérée par l&#39;opération de type **Select** est supprimée à l&#39;aide de la requête suivante :

   ```
   DELETE FROM NmsGroup WHERE iGroupId=$(l) 
   ```

   where **$(l)** is the list identifier

### Nettoyage des diffusions à supprimer ou à recycler {#cleanup-of-deliveries-to-be-deleted-or-recycled}

Cette tâche purge toutes les diffusions à supprimer ou à recycler.

1. Le **[!UICONTROL Database cleanup]** processus sélectionne toutes les livraisons pour lesquelles le champ **deleteStatus** a la valeur **[!UICONTROL Yes]** ou **[!UICONTROL Recycled]** et dont la date de suppression est antérieure à la période définie dans le champ **[!UICONTROL Deleted deliveries]** (**NmsCleanup_RecycledDeliveryPurgeDelay) de l’assistant de déploiement.** For more on this, refer to [Deployment wizard](#deployment-wizard). Cette période est calculée par rapport à la date actuelle du serveur.
1. La tâche sélectionne ensuite, pour chaque serveur de mid-sourcing, la liste des diffusions à supprimer.
1. The **[!UICONTROL Database cleanup]** workflow deletes delivery logs, attachments, mirror page information and all other related data.
1. Avant la suppression définitive de la diffusion, le workflow purge les informations associées dans les tables suivantes :

   * Dans la table des exclusions de diffusion (**NmsDlvExclusion**), la requête suivante est utilisée :

      ```
      DELETE FROM NmsDlvExclusion WHERE iDeliveryId=$(l)
      ```

      where **$(l)** is the identifier of the delivery.

   * Dans la table des coupons (**NmsCouponValue**), la requête suivante est utilisée (avec des suppressions en masse) :

      ```
      DELETE FROM NmsCouponValue WHERE iMessageId IN (SELECT iMessageId FROM NmsCouponValue WHERE EXISTS (SELECT B.iBroadLogId FROM $(BroadLogTableName) B WHERE B.iDeliveryId = $(l) AND B.iBroadLogId = iMessageId ) LIMIT 5000)
      ```

      where **$(l)** is the identifier of the delivery.

   * Dans les tables de logs de diffusion (**NmsBroadlogXxx**), des suppressions en masse sont exécutées, par groupes de 10000 enregistrements.
   * Dans les tables de propositions d&#39;offres (**NmsPropositionXxx**), des suppressions en masse sont exécutées, par groupes de 10000 enregistrements.
   * Dans les tables de logs de tracking (**NmsTrackinglogXxx**), des suppressions en masse sont exécutées, par groupes de 5000 enregistrements.
   * Dans la table des fragments de diffusion (**NmsDeliveryPart**), des suppressions en masse sont exécutées, par groupes de 5000 enregistrements. Cette table contient les informations de personnalisation des messages restant à envoyer.
   * Dans la table des fragments de données de page miroir (**NmsMirrorPageInfo**), des suppressions en masse sont exécutées, par groupes de 5000 enregistrements. Cette table contient les informations de personnalisation de tous les messages qui sont utilisées pour la génération des pages miroir.
   * Dans la table de recherche des pages miroir (**NmsMirrorPageSearch**), des suppressions en masse sont exécutées, par groupes de 5000 enregistrements. Cette table est un index de recherche permettant d&#39;accélérer l&#39;accès aux informations de personnalisation stockées dans la table **NmsMirrorPageInfo**.
   * Dans la table des logs de traitements batch (**XtkJobLog**), des suppressions en masse sont exécutées, par groupes de 5000 enregistrements. Cette table contient le journal des diffusions à supprimer.
   * Dans la table de tracking des URL d&#39;une diffusion (**NmsTrackingUrl**), la requête suivante est utilisée :

      ```
      DELETE FROM NmsTrackingUrl WHERE iDeliveryId=$(l)
      ```

      where **$(l)** is the identifier of the delivery.

      Cette table contient les URL présentes dans les diffusions à supprimer afin de permettre leur tracking.

1. La diffusion est ensuite supprimée de la table des diffusions (**NmsDelivery**) :

   ```
   DELETE FROM NmsDelivery WHERE iDeliveryId = $(l)
   ```

   where **$(l)** is the identifier of the delivery.

#### Diffusions utilisant le mid-sourcing {#deliveries-using-mid-sourcing}

The **[!UICONTROL Database cleanup]** workflow also deletes deliveries on the mid-sourcing server(s).

1. Pour cela, le workflow vérifie que chaque diffusion est inactive (en se basant sur son état). Si une diffusion est active, elle sera interrompue avant d&#39;être supprimée. La vérification est effectuée en exécutant la requête suivante :

   ```
   SELECT iState FROM NmsDelivery WHERE iDeliveryId = $(l) AND iState <> 100;
   ```

   where **$(l)** is the identifier of the delivery.

1. Si la valeur de l’état est **[!UICONTROL Start pending]** , **[!UICONTROL In progress]** , **[!UICONTROL Recovery pending]** , **[!UICONTROL Recovery in progress]** , **[!UICONTROL Pause requested]** **[!UICONTROL Pause in progress]** **[!UICONTROL Paused]** , ou (valeurs 51, 55, 61, 62, 71, 72, 75), la remise est arrêtée et la tâche purge les informations liées.

### Nettoyage des diffusions ayant expiré {#cleanup-of-expired-deliveries}

Cette tâche interrompt les diffusions dont la période de validité a expiré.

1. Le **[!UICONTROL Database cleanup]** processus crée la liste des livraisons qui ont expiré. Cette liste comprend toutes les livraisons arrivées à expiration avec un statut autre que **[!UICONTROL Finished]** , ainsi que les livraisons récemment interrompues avec plus de 10 000 messages non traités. La requête suivante est utilisée :

   ```
   SELECT iDeliveryId, iState FROM NmsDelivery WHERE iDeleteStatus=0 AND iIsModel=0 AND iDeliveryMode=1 AND ( (iState >= 51 AND iState < 85 AND tsValidity IS NOT NULL AND tsValidity < $(currentDate) ) OR (iState = 85 AND DateMinusDays(15) < tsLastModified AND iToDeliver - iProcessed >= 10000 ))
   ```

   where **delivery mode 1** matches the **[!UICONTROL Mass delivery]** mode, **state 51** matches the **[!UICONTROL Start pending]** state, **state 85** matches the **[!UICONTROL Stopped]** state, and the highest number of delivery logs mass-updated on the delivery server equals 10,000.

1. Le workflow inclut ensuite la liste des diffusions qui ont récemment expiré et qui utilisent le mid-sourcing. Les diffusions pour lesquelles les logs de diffusion n&#39;ont pas encore été récupérés depuis serveur de mid-sourcing ne sont pas incluses.

   La requête suivante est utilisée :

   ```
   SELECT iDeliveryId, tsValidity, iMidRemoteId, mData FROM NmsDelivery WHERE (iDeliveryMode = 4 AND (iState = 85 OR iState = 95) AND tsValidity IS NOT NULL AND (tsValidity < SubDays(GetDate() , 15) OR tsValidity < $(DateOfLastLogPullUp)) AND tsLastModified > SubDays(GetDate() , 15))
   ```

1. La requête suivante est utilisée pour détecter si le compte externe est toujours actif, afin de pouvoir filtrer les diffusions selon la date :

   ```
   SELECT iExtAccountId FROM NmsExtAccount WHERE iActive<>0 AND sName=$(providerName)
   ```

1. In the list of expired deliveries, delivery logs whose status is **[!UICONTROL Pending]** , switch to **[!UICONTROL Delivery cancelled]** , and all deliveries in this list switch to **[!UICONTROL Finished]** .

   Les requêtes utilisées sont les suivantes :

   ```
   UPDATE $(BroadLogTableName) SET tsLastModified=$(curdate), iStatus=7, iMsgId=$(bl) WHERE iDeliveryId=$(dl) AND iStatus=6
   ```

   where **$(curdate)** is the current date of the database server, **$(bl)** is the identifier of the delivery logs message, **$(dl)** is the delivery identifier, **delivery status 6** matches the **[!UICONTROL Pending]** status and **delivery status 7** matches the **[!UICONTROL Delivery cancelled]** status.

   ```
   UPDATE NmsDelivery SET iState = 95, tsLastModified = $(curdate), tsBroadEnd = tsValidity WHERE iDeliveryId = $(dl)
   ```

   where **delivery state 95** matches the **[!UICONTROL Finished]** status, and **$(dl)** is the identifier of the delivery.

1. Tous les fragments (**deliveryParts**) des diffusions obsolètes sont supprimés et tous les fragments obsolètes des diffusions de notification toujours en cours sont supprimés. Une suppression en masse est utilisée pour ces deux tâches.

   Les requêtes utilisées sont les suivantes :

   ```
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE iDeliveryId IN (SELECT iDeliveryId FROM NmsDelivery WHERE iState=95 OR iState=85) LIMIT 5000)
   ```

   ```
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE tsValidity < $(curDate) LIMIT 500000)
   ```

   where **delivery state 95** matches the **[!UICONTROL Finished]** status, **delivery state 85** matches the **[!UICONTROL Stopped]** status, and **$(curDate)** is the current server date.

### Nettoyage des pages miroir {#cleanup-of-mirror-pages}

Cette tâche supprime les ressources web (pages miroir) utilisées par les diffusions.

1. Tout d&#39;abord, la liste des diffusions à purger est récupérée à l&#39;aide de la requête suivante :

   ```
   SELECT iDeliveryId, iNeedMirrorPage FROM NmsDelivery WHERE iWebResPurged = 0 AND tsWebValidity IS NOT NULL AND tsWebValidity < $(curdate)"
   ```

   where **$(curDate)** is the current server date.

1. La table **NmsMirrorPageInfo** est ensuite purgée, si nécessaire, à l&#39;aide de l&#39;identifiant de la diffusion récupéré précédemment. Une suppression en masse est utilisée pour générer les requêtes suivantes :

   ```
   DELETE FROM NmsMirrorPageInfo WHERE iMirrorPageInfoId IN (SELECT iMirrorPageInfoId FROM NmsMirrorPageInfo WHERE iDeliveryId = $(dl)) LIMIT 5000)
   ```

   ```
   DELETE FROM NmsMirrorPageSearch WHERE iMessageId IN (SELECT iMessageId FROM NmsMirrorPageSearch WHERE iDeliveryId = $(dl)) LIMIT 5000)
   ```

   où **$(dl)** est l’identifiant de la remise.

1. Un log est ensuite ajouté au journal de la diffusion.
1. Les diffusions purgées sont ensuite identifiées afin de ne pas avoir à les retraiter par la suite. La requête suivante est exécutée :

   ```
   UPDATE NmsDelivery SET iWebResPurged = 1 WHERE iDeliveryId IN ($(strIn))
   ```

   where **$(strIn)** is the list of delivery identifiers.

### Nettoyage des tables de travail {#cleanup-of-work-tables}

This task deletes from the database, all work tables which match deliveries whose status is **[!UICONTROL Being edited]** , **[!UICONTROL Stopped]** or **[!UICONTROL Deleted]** .

1. La liste des tables dont le nom commence par **wkDlv_** est récupérée en premier lieu avec la requête suivante (postgresql) :

   ```
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkDlv_') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. Les tables utilisées par des workflows en cours sont ensuite exclues. Pour cela, la liste des diffusions en cours est récupérée à l&#39;aide de la requête suivante :

   ```
   SELECT iDeliveryId FROM NmsDelivery WHERE iDeliveryId<>0 AND iDeleteStatus=0 AND iState NOT IN (0,85,100);
   ```

   where 0 is the value which matches the **[!UICONTROL Being edited]** delivery status, 85 matches the **[!UICONTROL Stopped]** status and 100 matches the **[!UICONTROL Deleted]** status.

1. Les tables qui ne sont plus utilisées sont supprimées à l&#39;aide de la requête suivante :

   ```
   DROP TABLE wkDlv_15487_1;
   ```

### Nettoyage des rejets générés par les imports {#cleanup-of-rejects-generated-by-imports-}

Cette étape permet de supprimer les enregistrements dont les données n&#39;ont pas été toutes traitées par l&#39;import.

1. Une suppression en masse est exécutée sur la table **XtkReject** avec la requête suivante :

   ```
   DELETE FROM XtkReject WHERE iRejectId IN (SELECT iRejectId FROM XtkReject WHERE tsLog < $(curDate)) LIMIT $(l))
   ```

   where **$(curDate)** is the current server date from which we subtract the period defined for the **NmsCleanup_RejectsPurgeDelay** option (refer to [Deployment wizard](#deployment-wizard)) and **$(l)** is the maximum number of records to be mass deleted.

1. Tous les rejets orphelins sont alors supprimés à l&#39;aide de la requête suivante :

   ```
   DELETE FROM XtkReject WHERE iJobId NOT IN (SELECT iJobId FROM XtkJob)
   ```

### Nettoyage des instances de workflow {#cleanup-of-workflow-instances}

Cette tâche purge chaque instance de processus à l’aide de son identifiant (**lWorkflowId**) et de son historique (**lHistory**). Il supprime les tableaux inactifs en exécutant à nouveau la tâche de nettoyage de la table de travail.

>[!NOTE]
>
>La périodicité de la purge de l’historique est définie pour chaque workflow dans le champ **Jours d’historique** (valeur par défaut de 30 jours). Ce champ se situe sur l’onglet **Exécution** des propriétés du workflow. Voir à ce sujet [cette section](../../workflow/using/workflow-properties.md#execution).

1. Pour récupérer la liste des workflows à supprimer, la requête suivante est utilisée :

   ```
   SELECT iWorkflowId, iHistory FROM XtkWorkflow WHERE iWorkflowId<>0
   ```

1. Cette requête génère la liste des workflows qui seront utilisés pour supprimer tous les logs associés, les tâches terminées et les évènements terminés, à l&#39;aide des requêtes suivantes :

   ```
   DELETE FROM XtkWorkflowLog WHERE iWorkflowId=$(lworkflow) AND tsLog < DateMinusDays($(lhistory))
   ```

   ```
   DELETE FROM XtkWorkflowTask WHERE iWorkflowId=$(lworkflow) AND iStatus<>0 AND tsCompletion < DateMinusDays($(lhistory)) 
   ```

   ```
   DELETE FROM XtkWorkflowEvent WHERE iWorkflowId=$(l) AND iStatus>2 AND tsProcessing < DateMinusDays($(lHistory))
   ```

   where **$(lworkflow)** is the identifier of the workflow and **$(lhistory)** is the identifier of the history.

1. Toutes les tables inutilisées sont alors supprimées. Pour cela, toutes les tables sont collectées à l&#39;aide d&#39;un masque de type **wkf%** utilisant la requête suivante (postgresql) :

   ```
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkf%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. Puis, toutes les tables utilisées par une instance de workflow en cours sont exclues. La liste des workflows actifs est récupérée à l&#39;aide de la requête suivante :

   ```
   SELECT iWorkflowId FROM XtkWorkflow WHERE iWorkflowId<>0 AND iState<>20
   ```

1. Chaque identifiant de workflow est ensuite récupéré afin de trouver le nom des tables utilisées par des workflows en cours. Ces noms sont exclus de la liste de tables récupérée précédemment.
1. Les tables d&#39;historique des activités de type &quot;requête incrémentale&quot; sont exclues, à l&#39;aide des requêtes suivantes :

   ```
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkfhisto%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

   ```
   SELECT iWorkflowId FROM XtkWorkflow WHERE iWorkflowId IN ($(strCondition))
   ```

   where **$(strcondition)** is the list of tables which match the **wkfhisto%** mask.

1. Les tables restantes sont supprimées à l&#39;aide de la requête suivante :

   ```
   DROP TABLE wkf15487_12;
   ```

### Nettoyage des logins de workflows {#cleanup-of-workflow-logins}

Cette tâche supprime les logins de workflows à l&#39;aide de la requête suivante :

```
DELETE FROM XtkWorkflowLogin WHERE iWorkflowId NOT IN (SELECT iWorkflowId FROM XtkWorkflow)
```

### Nettoyage des tables de travail orphelines {#cleanup-of-orphan-work-tables}

Cette tâche supprime les tables de travail orphelines liées à des groupes. La table **NmsGroup** stocke les groupes à nettoyer (ceux dont le type est différent de 0). Le nom des tables de travail a pour préfixe **grp**. Pour identifier les groupes à nettoyer, la requête suivante est utilisée :

```
SELECT iGroupId FROM NmsGroup WHERE iType>0"
```

### Nettoyage des visiteurs {#cleanup-of-visitors}

Cette tâche supprime les enregistrements obsolètes de la table des visiteurs à l’aide de la suppression en masse. Les enregistrements obsolètes sont ceux pour lesquels la dernière modification est antérieure à la période de conservation définie dans l’assistant de déploiement (voir Assistant [de](#deployment-wizard)déploiement). La requête suivante est utilisée :

```
DELETE FROM NmsVisitor WHERE iVisitorId IN (SELECT iVisitorId FROM NmsVisitor WHERE iRecipientId = 0 AND tsLastModified < $(tsDate) LIMIT 5000)
```

where **$(tsDate)** is the current server date, from which we subtract the period defined for the **NmsCleanup_VisitorPurgeDelay** option.

### Nettoyage des NPAI {#cleanup-of-npai}

Cette tâche permet la suppression, dans la table **NmsAddress**, des enregistrements correspondant à des adresses valides. La requête suivante est utilisée pour effectuer une suppression en masse :

```
DELETE FROM NmsAddress WHERE iAddressId IN (SELECT iAddressId FROM NmsAddress WHERE iStatus=2 AND tsLastModified < $(tsDate1) AND tsLastModified >= $(tsDate2) LIMIT 5000)
```

where **status 2** matches the **[!UICONTROL Valid]** status, **$(tsDate1)** is the current server date, and **$(tsDate2)** matches the **NmsCleanup_LastCleanup** option.

### Nettoyage des abonnements {#cleanup-of-subscriptions-}

Cette tâche purge, dans la table **NmsSubscription**, les abonnements qui ont été supprimés par l&#39;utilisateur, à l&#39;aide d&#39;une suppression en masse. La requête suivante est utilisée :

```
DELETE FROM NmsSubscription WHERE iDeleteStatus <>0
```

### Nettoyage des logs de tracking {#cleanup-of-tracking-logs}

Cette tâche supprime les enregistrements obsolètes des tables du journal de suivi et de suivi Web. Les enregistrements obsolètes sont ceux qui sont antérieurs à la période de conservation définie dans l’assistant de déploiement (voir Assistant [de](#deployment-wizard)déploiement).

1. Tout d&#39;abord, la liste des tables de logs de tracking est récupérée à l&#39;aide de la requête suivante :

   ```
   SELECT distinct(sTrackingLogSchema) FROM NmsDeliveryMapping WHERE sTrackingLogSchema IS NOT NULL;
   ```

1. Une suppression en masse est utilisée pour purger toutes les tables dans la liste des tables récupérées précédemment. La requête utilisée est la suivante :

   ```
   DELETE FROM XtkTrackingLogRcp WHERE iTrackingLogId IN (SELECT iTrackingLogId FROM XtkTrackingLogRcp WHERE tsLog < $(tsDate) LIMIT 5000) 
   ```

   where **$(tsDate)** is the current server date from which we subtract the period defined for the **NmsCleanup_TrackingLogPurgeDelay** option.

1. La table des statistiques de tracking est purgée à l&#39;aide d&#39;une suppression en masse. La requête suivante est utilisée :

   ```
   DELETE FROM NmsTrackingStats WHERE iTrackingStatsId IN (SELECT iTrackingStatsId FROM NmsTrackingStats WHERE tsStart < $(tsDate) LIMIT 5000) 
   ```

   where **$(tsDate)** is the current server date from which we subtract the period defined for the **NmsCleanup_TrackingStatPurgeDelay** option.

### Nettoyage des logs de diffusion {#cleanup-of-delivery-logs}

Cette tâche permet de purger les logs de diffusion stockés dans différentes tables.

1. Pour cela, la liste des schémas de logs de diffusion est récupérée à l&#39;aide de la requête suivante :

   ```
   SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL UNION SELECT distinct(sBroadLogExclSchema) FROM NmsDeliveryMapping WHERE sBroadLogExclSchema IS NOT NULL
   ```

1. Dans le cas de l&#39;utilisation du mid-sourcing, la table **NmsBroadLogMid** n&#39;est pas référencée dans les mappings de diffusion. Le schéma **nms:broadLogMid** est alors ajouté à la liste récupérée par la requête précédente.
1. Le workflow **Nettoyage de la base** procède ensuite à la purge des enregistrements obsolètes dans les tables récupérées précédemment. La requête suivante est utilisée :

   ```
   DELETE FROM $(tableName) WHERE iBroadLogId IN (SELECT iBroadLogId FROM $(tableName) WHERE tsLastModified < $(option) LIMIT 5000) 
   ```

   where **$(tableName)** is the name of each table in the list of schemas, and **$(option)** is the date defined for the **NmsCleanup_BroadLogPurgeDelay** option (refer to [Deployment wizard](#deployment-wizard)).

1. Le workflow vérifie enfin si la table **NmsProviderMsgId** existe. Si c&#39;est le cas, tous ses enregistrements obsolètes sont supprimés à l&#39;aide de la requête suivante :

   ```
   DELETE FROM NmsProviderMsgId WHERE iBroadLogId IN (SELECT iBroadLogId FROM NmsProviderMsgId WHERE tsCreated < $(option) LIMIT 5000)
   ```

   where **$(option)** matches the date defined for the **NmsCleanup_BroadLogPurgeDelay** option (refer to [Deployment wizard](#deployment-wizard)).

### Nettoyage de la table NmsEmailErrorStat {#cleanup-of-the-nmsemailerrorstat-table-}

Cette tâche nettoie la table **NmsEmailErrorStat**. Le programme principal (**coalesceErrors**) définit deux dates :

* **Date de début :** date du prochain traitement correspondant à l&#39;option **NmsLastErrorStatCoalesce** ou correspondant à la date la plus récente dans la table.
* **Date de fin :** date courante du serveur.

Si la date de début est supérieure ou égale à la date de fin, aucun traitement n&#39;a lieu. Le message **coalesceUpToDate** apparaît alors.

Si la date de début est inférieure à la date de fin, la table **NmsEmailErrorStat** est nettoyée.

Le nombre total d&#39;erreurs dans la table **NmsEmailErrorStat**, entre les dates de début et de fin, est récupéré à l&#39;aide de la requête suivante :

```
"SELECT COUNT(*) FROM NmsEmailErrorStat WHERE tsDate>= $(start) AND tsDate< $(end)"
```

where **$end** and **$start** are the start and end dates defined previously.

Si le total est supérieur à 0 :

1. La requête suivante est exécutée afin de ne conserver que les erreurs situées au-delà d&#39;un certain seuil (égal à 20) :

   ```
   "SELECT iMXIP, iPublicId, SUM(iTotalConnections), SUM(iTotalErrors), SUM(iMessageErrors), SUM(iAbortedConnections), SUM(iFailedConnections), SUM(iRefusedConnections), SUM(iTimeoutConnections) FROM NmsEmailErrorStat WHERE tsDate>=$(start ) AND tsDate<$(end ) GROUP BY iMXIP, iPublicId HAVING SUM(iTotalErrors) >= 20"
   ```

1. Le message **coalescingErrors** apparaît.
1. Une nouvelle connexion est créée pour supprimer toutes les erreurs survenues entre les dates de début et de fin. La requête suivante est utilisée :

   ```
   "DELETE FROM NmsEmailErrorStat WHERE tsDate>=$(start) AND tsDate<$(end)"
   ```

1. Chaque erreur est enregistrée dans la table **NmsEmailErrorStat** à l&#39;aide de la requête suivante :

   ```
   "INSERT INTO NmsEmailErrorStat(iMXIP, iPublicId, tsDate, iTotalConnections, iTotalErrors, iTimeoutConnections, iRefusedConnections, iAbortedConnections, iFailedConnections, iMessageErrors) VALUES($(lmxip ), $(lpublicId ), $(tsstart ), $(lconnections ), $(lconnectionErrors ),$(ltimeoutConnections ), $(lrefusedConnections ), $(labortedConnections ), $(lfailedConnections ), $(lmessageErrors))"
   ```

   où chaque variable correspond à une valeur récupérée par la requête précédente.

1. The **start** variable is updated with the values of the previous process to finish the loop.

La boucle et la tâche s&#39;arrêtent.

Deux tâches sont ensuite exécutées : le nettoyage des tables **NmsEmailError** et **cleanupNmsMxDomain**.

### Nettoyage de la table NmsEmailError {#cleanup-of-the-nmsemailerror-table-}

La requête suivante est utilisée :

```
DELETE FROM NmsEmailError WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

Cette requête supprime, dans la table **NmsEmailError**, toutes les lignes n&#39;ayant aucun enregistrement associé dans la table **NmsEmailErrorStat**.

### Nettoyage de la table NmsMxDomain {#cleanup-of-the-nmsmxdomain-table-}

La requête suivante est utilisée :

```
DELETE FROM NmsMxDomain WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

Cette requête supprime, dans la table **NmsMxDomain**, toutes les lignes n&#39;ayant aucun enregistrement associé dans la table **NmsEmailErrorStat**.

### Nettoyage des propositions {#cleanup-of-propositions}

Si le module **Interaction** est installé, cette tâche est exécutée afin de purger les tables **NmsPropositionXxx**.

La liste des tables de propositions est récupérée et une suppression en masse est exécutée sur chacune d&#39;entre elles, à l&#39;aide de la requête suivante :

```
DELETE FROM NmsPropositionXxx WHERE iPropositionId IN (SELECT iPropositionId FROM NmsPropositionXxx WHERE tsLastModified < $(option) LIMIT 5000) 
```

where **$(option)** is the date defined for the **NmsCleanup_PropositionPurgeDelay** option (refer to [Deployment wizard](#deployment-wizard)).

### Nettoyage des tables de simulation {#cleanup-of-simulation-tables}

Cette tâche nettoie les tables de simulation orphelines (qui ne sont plus associées à une simulation d&#39;offre ou une simulation de diffusion).

1. Pour récupérer la liste des simulations à nettoyer, la requête suivante est utilisée :

   ```
   SELECT iSimulationId FROM NmsSimulation WHERE iSimulationId<>0
   ```

1. Le nom des tables à supprimer est composé du préfixe **wkSimu_** suivi de l&#39;identifiant de la simulation (par exemple : **wkSimu_456831_aggr**). La requête suivante est utilisée :

   ```
   DROP TABLE wkSimu_456831_aggr
   ```

### Mise à jour des statistiques et optimisation du stockage {#statistics-update}

L&#39;option **XtkCleanup_NoStats** permet de contrôler le comportement de l&#39;étape d&#39;optimisation du stockage du processus de nettoyage.

Si l&#39;option **XtkCleanup_NoStats** n&#39;existe pas ou si sa valeur est 0, l&#39;optimisation du stockage est exécutée en mode verbose (VACUUM VERBOSE ANALYZE) sur PostgreSQL et les statistiques sont mises à jour sur toutes les autres bases de données. Pour vous assurer que cette commande est exécutée, vérifiez les journaux PostgreSQL. VACUUM génère des lignes au format suivant : Les lignes `INFO: vacuuming "public.nmsactivecontact"` et ANALYZE sont générées au format suivant : `INFO: analyzing "public.nmsactivecontact"`.

Si la valeur de l’option est 1, la mise à jour des statistiques n’est exécutée sur aucune base de données. La ligne de journal suivante apparaît dans les journaux de flux de travaux : `Option 'XtkCleanup_NoStats' is set to '1'`.

Si la valeur de l&#39;option est 2, l&#39;analyse du stockage en mode verbose (ANALYZE VERBOSE) sera exécutée sur PostgreSQL et les statistiques seront mises à jour sur toutes les autres bases de données. Pour vous assurer que cette commande est exécutée, vérifiez les journaux PostgreSQL. ANALYZE génère des lignes au format suivant : `INFO: analyzing "public.nmsactivecontact"`.

### Nettoyage des abonnements (NMAC) {#subscription-cleanup--nmac-}

Cette tâche supprime les abonnements liés à des services ou à des applications mobiles supprimés.

1. Pour récupérer la liste des schémas des broadlogs, la requête suivante est utilisée :

   ```
   SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL
   ```

1. La tâche récupère ensuite les noms des tables associées au lien **appSubscription** et supprime ces tables.

### Nettoyage des informations de session {#cleansing-session-information}

Cette tâche nettoie les informations de la table **sessionInfo**, la requête suivante est utilisée :

```
 DELETE FROM XtkSessionInfo WHERE tsexpiration < $(curdate) 
```

### Nettoyage des événements ayant expiré {#cleansing-expired-events}

Cette tâche nettoie les événements reçus et stockés sur les instances d&#39;exécution et les événements historisés sur une instance de pilotage.

### Nettoyage des réactions {#cleansing-reactions}

Cette tâche nettoie les réactions (table **NmsRemaMatchRcp**) dont les hypothèses ont été supprimées sont elles-mêmes supprimées.

### Nettoyer le Suivi {#cleanup-of-audit-trail}

La requête suivante est utilisée :

```
DELETE FROM XtkAudit WHERE tsChanged < $(tsDate)
```

where **$(tsDate)** is the current server date from which the period defined for the **XtkCleanup_AuditTrailPurgeDelay** option is substracted.
