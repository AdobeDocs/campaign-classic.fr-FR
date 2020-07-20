---
title: Accès à une base de données externe
seo-title: Accès à une base de données externe
description: Accès à une base de données externe
seo-description: null
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: c86af066045c1c35b51624de8565af21746354c1
workflow-type: ht
source-wordcount: '281'
ht-degree: 100%

---


# Options additionnelles {#additional-options}

<!--

## HTTP relay to a remote instance {#http-relay-to-a-remote-instance}

You can access external databases configured in remote instances using the HTTP protocol.

>[!NOTE]
>
>Not all SQL data types are supported by this feature. Blob data types are not supported at all. It is possible that other data types may not work depending on the targeted database (Timestamp on Microsoft SQL Server, for example). Please contact Adobe support for more information.

This simplifies transferring and synchronizing data between two instances. It also enables you to sidestep any tunneling between an instance and a remote database as well as the installation of the client layers to access this database. The destination instance can be a hosted instance.

>[!CAUTION]
>
>This option is only for facilitating data replication flows (ETL).   
>
>For example, it allows a cloud-hosted instance to have direct access to the data in an "on-premise" hosted database. However, it is not intended to allow targeting to be carried on an "on-premise" hosted database directly from the cloud.

To do this, you must configure the external accounts of the two instances so that the local instance can communicate with the remote instance using the HTTP protocol:

* Local instance: select the new **[!UICONTROL HTTP relay to a remote database]** connection type.

  In case of bulk load data transfer, also specify the buffer size. Select the compression option if you want to reduce the size of the transferred data.

  The **[!UICONTROL Data source]** must be defined with the following syntax: "nms:extAccount : `<internal_name_of_the_external_account>`"

  ![](assets/fda_over_http_1.png)

  >[!NOTE]
  >
  >We recommend that you use an HTTPS connection.

* Remote instance: in the FDA external account of the database accessed via the HTTP relay, check the Target of an **[!UICONTROL 'HTTP relay to a remote database' account option]**.

  ![](assets/fda_over_http_2.png)

The following example shows the new possible operating mode:

![](assets/schema_fda_over_http_2.png)

>[!CAUTION]
>
>The default database of the remote instance must be accessed via an external account as well.

This operating method avoids that the cleanup workflow of each instance deletes the work tables of the databases that use the instance as relay.

Thus, in the previous example, the cleanup workflow of the remote instance will not perform any action on the red FDA database as it is used by the local instance.

-->

## Création directe des schémas temporaires {#directly-creating-temporary-schemas}

Dans le cadre de la gestion de plusieurs accès à une base de données externe en FDA, une option vous permet de créer directement un schéma de travail depuis le paramétrage d&#39;un compte externe.

>[!NOTE]
>
>Cette option ne fonctionne qu&#39;avec PostgreSQL.

![](assets/fda_work_table.png)

## Optimiser la personnalisation d&#39;un email avec des données externes {#optimizing-email-personalization-with-external-data}

A partir du build 8740, l&#39;option **[!UICONTROL Préparer les données de personnalisation avec un workflow]** est disponible dans l&#39;onglet **[!UICONTROL Analyse]** des propriétés d&#39;une diffusion.

Cette option permet, lors de l&#39;analyse de la diffusion, de créer automatiquement et d&#39;exécuter un workflow qui stocke dans une table temporaire toutes les données liées à la cible, notamment les données issues des tables liées en FDA.

En cochant cette option, vous pouvez obtenir des performances nettement améliorées pour réaliser de la personnalisation.

## Utiliser les données d&#39;une base externe dans un workflow {#using-data-from-an-external-database-in-a-workflow}

Dans plusieurs activités des workflows Adobe Campaign, vous pouvez utiliser les données stockées dans une base externe.

### Filtrer sur les données externes {#filtering-on-external-data}

L&#39;activité de requête permet d&#39;ajouter des données externes et de les utiliser dans les paramètres de filtrage définis.

Voir à ce sujet la section [Requête](../../workflow/using/targeting-data.md#selecting-data).

### Construire des sous-ensembles {#creating-sub-sets}

L&#39;activité de partage permet de construire des sous-ensembles. Vous pouvez utiliser des données externes pour définir les critères de filtrage à utiliser.

Voir à ce sujet la section [Partage](../../workflow/using/split.md).

### Charger des données externes {#loading-external-database}

Vous pouvez utiliser les données externes dans l&#39;activité de chargement (SGBD). Cette activité est présentée dans la section [Chargement](../../workflow/using/data-loading--rdbms-.md).

### Ajouter des informations et des liens {#adding-information-and-links}

L&#39;activité d&#39;enrichissement permet d&#39;ajouter des données additionnelles à la table de travail du workflow ainsi que des liens vers une table externe. Elle peut pour cela exploiter les données d&#39;une base de données externe. Cette activité est présentée dans la section [Enrichissement](../../workflow/using/enrichment.md).
<!--

## Cloud Messaging - FDA synchronization {#cloud-messaging---fda-synchronization}

When the Cloud Messaging server and the Marketing server have not been synchronized for a long period, the volume of missing broadlogs on the Marketing server can be significant. To optimize broadlog synchronization via the FDA, the **NmsMidSourcing_LogsPeriodHour** option has been added. This allows a maximum period (expressed in hours) to be specified as to limit the number of broadlogs recovered every time the synchronization workflow is executed.

The option is to be added in the console, in the **[!UICONTROL Administration > Options]** node.

>[!CAUTION]
>
>This option must **only** be used for synchronizing a significant volume of broadlogs via the FDA.

>[!NOTE]
>
>The option is only taken into account if a last recovery date exists (**NmsMidSourcing_LastBroadLog_&#42;** option).

## Message Center - Read access on the XtkFolder table {#message-center---read-access-on-the-xtkfolder-table}

From build 8141 and above, manual action is necessary if Message Center uses the FDA as an archiving mode.

You need to grant read access on the XtKFolder table to the user linked with the external FDA account.

For a PostgreSQL database for example, the command is as follows:

```
GRANT SELECT ON XtkFolder TO DBUSER;
```

This user must have read access to the following tables:

* NmsBroadLogRtEvent
* NmsBroadLogBatchEvent
* NmsTrackingLogRtEvent
* NmsTrackingLogBatchEvent
* NmsRtEvent
* NmsBatchEvent
* NmsBroadLogMsg
* NmsTrackingUrl
* NmsDelivery
* NmsWebTrackingLog

>[!NOTE]
>
>This modification deletes the "Permission denied for relation xtkfolder" error message.

If the working schema selected in the external FDA account is not the out-of-the-box Neolane account, then this modification to the access rights is not necessary.

-->

