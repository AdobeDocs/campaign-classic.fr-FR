---
product: campaign
title: Adapter votre configuration
description: Découvrez comment adapter votre configuration avant et après une migration vers Campaign v7
feature: Upgrade
audience: migration
content-type: reference
topic-tags: migration-procedure
hide: true
hidefromtoc: true
exl-id: ad71dead-c0ca-42d5-baa8-0f340979231a
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: ht
source-wordcount: '470'
ht-degree: 100%

---

# Adapter votre configuration{#configuring-your-platform}



Certaines modifications majeures d’Adobe Campaign v7 nécessitent une configuration spécifique. Ces configurations peuvent être nécessaires avant ou après la migration.

Pendant la migration, le tableau **NmsRecipient** est reconstruit à partir de la définition des schémas. Toute modification apportée à la structure SQL de cette table en dehors d’Adobe Campaign sera perdue.

Exemples d&#39;éléments à vérifier :

* Si vous avez ajouté une colonne (ou un index) dans la table **NmsRecipient** mais que vous ne l&#39;avez pas décrite dans le schéma, celle-ci ne sera pas conservée.
* L&#39;attribut **tablespace** reprend ses valeurs par défaut, c&#39;est-à-dire celles définies dans l&#39;assistant de déploiement.
* Si vous avez ajouté une vue qui référence le tableau **NmsRecipient**, vous devez la supprimer avant la migration.


## Avant la migration {#before-the-migration}

Dans le cadre d&#39;une migration vers Adobe Campaign v7, les éléments suivants doivent être paramétrés. Ces paramétrages impliquent une prise en compte avant le lancement du **postupgrade**.

<!--

  * Timezones

  During a migration from a v5.11 platform, you must specify the timezone to use during the postupgrade.

  If you wish to use the "multi timezone" mode, refer to [this section](../../migration/using/general-configurations.md#time-zones).

  If you use Oracle as a database, check that the Oracle timezone files have properly been synched between the application server and the database server. [Learn more](../../migration/using/general-configurations.md#oracle)

* Security zones

  For security reasons, the Adobe Campaign platform is no longer accessible by default: you must configure the security zones, which requires collecting the user IP addresses before the migration. [Learn more](../../migration/using/general-configurations.md#security)

* Syntax

  Some Javascript code may no longer accepted in the v7 version, due to the use of a new interpreter. [Learn more](../../migration/using/general-configurations.md#javascript).

  Similarly, a new syntax is introduced in Adobe Campaign v7 to replace the SQLData based syntax. If you use code elements with this syntax, you must adapt them. [Learn more](../../migration/using/general-configurations.md#sqldata)

  -->

* Mots de passe

  Vous devez configurer les mots de passe **Admin** et **Interne**. [En savoir plus](../../migration/using/before-starting-migration.md#user-passwords)

<!--
* Tree structure

  If migrating from a v5.11 platform, you must reorganize the tree structure folders according to Adobe Campaign v6 norms. [Learn more](../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11).

-->

<!--

* Interaction

  If you are migrating from Campaign v6.02 and using the  **Interaction** module, you must delete all 6.02 schema references that no longer exist in v7. [Learn more](../../migration/using/general-configurations.md#interaction)

-->

## Après la migration {#after-the-migration}

Après avoir exécuté **postupgrade**, vérifiez et configurez les éléments suivants :

* Pages miroir

  Dans la version v6.x, le bloc de personnalisation des pages miroir a changé. Cette nouvelle version renforce la sécurité lors de l&#39;accès à ces pages.

  Si vous utilisez le bloc de personnalisation de la version v5 dans vos messages, les pages miroir ne s&#39;affichent pas. Adobe recommande vivement d&#39;utiliser le nouveau bloc de personnalisation lors de l&#39;insertion d&#39;une page miroir dans vos messages.

  Toutefois, à titre de solution temporaire (et comme les pages miroir sont toujours actives), vous pouvez revenir à l’ancien bloc de personnalisation pour éviter ce problème en modifiant l’option **[!UICONTROL XtkAcceptOldPasswords]** et en la définissant sur **[!UICONTROL 1]**. L’utilisation du nouveau bloc de personnalisation v6.x n’en sera pas affectée.

* Syntaxe

  Si vous rencontrez des erreurs, lors du postupgrade, liées à la syntaxe SQLData, vous devez temporairement activer l’option **allowSQLInjection** dans le fichier **serverConf.xml**, le temps de réécrire le code. Une fois le code adapté, n’oubliez pas de réactiver la sécurité.

* Conflits

  La migration étant effectuée au travers d&#39;un postupgrade, des conflits peuvent apparaître au niveau des rapports, formulaires ou applications web. Ces conflits peuvent être résolus manuellement depuis la console.

* Tomcat

  Si vous avez personnalisé le dossier d’installation, vérifiez qu’il est correctement mis à jour après la migration.

* Rapports

  Tous les rapports prêts à l’emploi utilisent actuellement le moteur de rendu v6.x. Si vous aviez ajouté du code JavaScript dans les rapports, certains éléments peuvent être affectés.

* Applications web

  Après le postupgrade, si vous rencontrez des problèmes de connexion à vos applications web identifiées, vous devez activer les options **allowUserPassword** et **sessionTokenOnly** dans le fichier **serverConf.xml**. Pour éviter tout problème de sécurité, ces deux options doivent être réactivées une fois le problème résolu.

  Selon le type d’applications Web et leur configuration, vous devez effectuer des manipulations complémentaires pour en assurer le bon fonctionnement.

<!--
  If migrating from a v5.11 platform, additional configurations must be carried out. [Learn more](../../migration/using/general-configurations.md#specific-configurations-in-v5-11.md)

* Security zones

  Before starting the server, you must configure the security zones. [Learn more](../../installation/using/security-zones.md) and [see here](../../migration/using/general-configurations.md#security)

-->

<!--

* Workflows

  If migrating from a v5.11 platform, you must check the workflows folder. [Learn more](../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11)

-->

<!--

* Tracking

  If migrating from a v5.11 platform, you must configure the tracking mode. [Learn more](../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11)

-->

* Interaction

  Si vous utilisez **Interaction**, vous devez ajuster les paramètres après la migration.

<!--

* Dashboards

  If a client error appears, you have to either update your dashboards with the new Adobe Campaign v7 code, or manually copy the following files from the v6.02 instance to the v7 instance:

  ```
  v6.02 files and spaces:
  /usr/local/neolane/nl6/datakit/xtk/eng/css/dropDownMenu.css
  /usr/local/neolane/nl6/datakit/xtk/eng/js/client/dropDownMenu.js
  v6.1 files and spaces:
  /usr/local/neolane/nl6/deprecated/xtk/css/dropDownMenu.css
  /usr/local/neolane/nl6/deprecated/xtk/js/client/dropDownMenu.js  
  ```

-->

<!--

## Specific configurations from a v5.11 to v7{#specific-configurations-in-v5-11}



This section details the additional configuration required when migrating from v5.11. You should also configure the settings detailed in the [General configurations](../../migration/using/general-configurations.md) section.

### Web applications {#web-applications-v5}

The following warning will be displayed automatically during migration:

```
The webApp ids have been modified during the migration process. Please make sure to check your scripts/css for broken compatibility (any client side JavaScript or css dealing directly with another element through its id is impacted). See file 'c:\svn\602\nl\build\ncs\var\upgrade/postupgrade/webAppsMigration_*************.txt' for details about the references that were automatically updated, if any.
```

Some components of web applications, for instance the various formula fields, have @id attributes. These are used in the XML code of web applications and are no longer generated in the same way. They are not visible in the interface and you must not normally use them. However, in some cases, @id attributes may have been used to personalize the rendering of web applications, for instance via a stylesheet or using JavaScript code.

During migration, you **must** check the log file path specified in the warning:

* **The file is not empty**: it contains warnings which concern inconsistencies recorded before migration and which still exist. This can be JavaScript code in a web application which references a non-existent ID. Each error must be checked and corrected.
* **The file is empty**: this means that Adobe Campaign has not detected any issues.

Whether the file is empty or not, you must check that these IDs are not used for configuration elsewhere (and adapt configuration if this is the case).

### Workflows {#workflows}

Since the name of the Adobe Campaign installation directory has changed, some workflows may not work after the migration. If a workflow references the nl5 directory in one of its activities, this will raise an error. Replace this reference with **build**. You can run an SQL query to identify these workflows (PostgreSQL example):

```
SELECT   iWorkflowId, sInternalName, sLabel 
FROM XtkWorkflow 
WHERE mData LIKE '%nl5%';
```

### MySQL {#mysql}

>[!CAUTION]
>
>MySQL is only supported in v7 as the main database engine when migrating from version 6.02 or 5.11 using this engine.

MySQL does not manage timezones by default. To enable timezone management, run the following command:

```
mysql_tzinfo_to_sql /usr/share/zoneinfo | mysql -u root mysql
```

>[!NOTE]
>
>For more information, refer to the [https://dev.mysql.com/doc/refman/8.0/en/time-zone-support.html](https://dev.mysql.com/doc/refman/8.0/en/time-zone-support.html) page.

If modifications have been made to the database structure, during configuration for example (creating specific indexes, creating SQL views, etc.), certain precautions should be taken when migrating. Indeed, certain modifications can be generated from incompatibilities with the migration procedure. For example, creating SQL views containing **Timestamp** fields are not compatible with the **usetimestamptz** option. We therefore advise you to follow the recommendations below:

1. Before starting the migration, back up the database.
1. Delete SQL changes.
1. Perform the postupgrade
    >[!NOTE]
    >
    >You must follow the migration steps presented in [this section](../../migration/using/migrating-in-windows-for-adobe-campaign-7.md).
1. Reintegrate SQL changes.

In this example, a **NmcTrackingLogMessages** view had been created and this has a **Timestamp** field named **tslog**. In this case, the migration procedure fails and the following error message appears:

```
2011-10-04 11:57:51.804Z B67B28C0 1 info log Updating table 'NmcTrackingLogMessages'
2011-10-04 11:57:51.804Z B67B28C0 1 error log PostgreSQL error: ERROR: cannot alter type of a column used by a view or rule\nDETAIL: rule _RETURN on view nmctrackinglogmessagesview depends on column "tslog"\n (iRc=-2006)
2011-10-04 11:57:51.804Z B67B28C0 1 error log SQL order 'ALTER TABLE NmcTrackingLogMessages ALTER COLUMN tsLog TYPE TIMESTAMPTZ' was not executed. (iRc=-2006)
```

To make sure the postupgrade works, you must delete the view before the migration and re-create it after the migration while adapting it to the TIMESTAMP WITH TIMEZONE mode.

### Tracking {#tracking}

The tracking formula has been modified. When migrating, the old formula (v5) is replaced by the new one (v7). If you use a personalized formula in Adobe Campaign v5, this configuration has to be adapted in Adobe Campaign v7 (**NmsTracking_ClickFormula** and **NmsTracking_OpenFormula** options).

Web tracking management has also been modified. Once migration to v7 has been carried out, you must start the deployment wizard to finish configuring the web tracking.

  ![](assets/migration_web_tracking.png)

Three modes are available:

* **Session web tracking**: If the **[!UICONTROL Leads]** package has not been installed, this option is selected by default. This option is the most ideal in terms of performance and it allows you to limit the size of the tracking logs.
* **Permanent Web tracking**
* **Anonymous Web Tracking**: If the **[!UICONTROL Leads]** package is installed, this option is selected by default. It is the most resource-consuming option. As above, the **sSourceId** column must be indexed (in the tracking table and the **CrmIncomingLead** table).

>[!NOTE]
>
>For more information on these three modes, refer to [this section](../../configuration/using/about-web-tracking.md).

### Adobe Campaign v7 tree structure {#campaign-vseven-tree-structure}

During migration, the tree structure is automatically reorganized based on the v7 standards. The new folders are added, the obsolete folders are deleted, and their content is placed in the "To move" folder. All items in this folder must be checked after the migration, and the consultant has to decide to either keep it or delete each one. Items to be kept then have to be moved to the right place.

An option has been added for disabling the automatic migration of the navigation tree. This operation is now manual. Obsolete folders are not deleted and new folders are not added. This option should only be used if the out-of-the-box v5 navigation tree has undergone too many changes. Add the option to the console, before migrating, in the **[!UICONTROL Administration > Options]** node:

* Internal name: NlMigration_KeepFolderStructure
* Data type: Integer
* Value (text): 1

If you use this option, after migration you will have to delete obsolete folders, add the new folders and run all necessary checks.

**List of new folders**:

The following folders need to be added after the migration:

| Internal name | Label | Condition |
|---|---|---|
| nmsAutoObjects | Objects created automatically | - |
| nmsCampaignAdmin | Campaign management | - |
| nmsCampaignMgt | Campaign management | - |
| nmsCampaignRes | Campaign management | - |
| nmsModels | Templates | - |
| nmsOnlineRes | Online | - |
| nmsProduction | Production | - |
| nmsProfilProcess | Processes | - |
| xtkDashboard | Dashboards | - |
| xtkPlatformAdmin | Platform | - |
| nmsLocalOrgUnit | Organizational units | - |
| nmsMRM | MRM | MRM installed |
| nmsOperations | Campaigns | Campaign installed |

**List of obsolete folders**:

The obsolete folders to be deleted after the migration are as follows:

>[!NOTE]
>
>The entire content of the obsolete folders must be checked, and for each item the consultant decides whether to keep or delete it. The items to be kept must be moved to the appropriate place.

| Internal name | Label | Condition |
|---|---|---|
| nmsAdministration | Administration | - |
| nmsDeliveryMgt | Campaign execution | - |
| ncmContent | Content management | Content Manager installed |
| ncmForm | Input form | Content Manager installed |
| ncmImage | Images | Content Manager installed |
| ncmJavascript | JavaScript codes | Content Manager installed |
| ncmJst | JavaScript templates | Content Manager installed |
| ncmParameters | Configuration | Content Manager installed |
| ncmSrcSchema | Data schemas | Content Manager installed |
| ncmStylesheet | XSL style files | Content Manager installed |
| nmsAdminPlan | Administration | Campaign installed |
| nmsResourcePlan | Resources | Campaign installed |
| nmsResourcesModels | Templates | Campaign installed |
| nmsRootPlan | Campaign management | Campaign installed |
| nmsOperator | Marketing operators | MRM installed |


## Specific configurations from v6.02 to v7{#specific-configurations-in-v6-02}



The following section details the additional configuration required when migrating from v6.02. You should also configure the settings detailed in [this page](../../migration/using/general-configurations.md).

### Web applications {#web-applications-v6}

If you are migrating from v6.02, error logs regarding overview-type web applications may appear. Error message examples:

```
[PU-0006] Entity of type : 'xtk:entityBackupNew' and Id 'nms:webApp|taskOverview', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'xtk:formDictionary' and Id 'nms:webApp|lastTasks', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'nms:webApp' and Id 'taskOverview', expression '[SQLDATA[' was found : '...@owner-id] IN ([SQLDATA[select iGroupid...'. (iRc=-1)
```

These web applications used SQLData and are not compatible with v7, due to heightened security. These errors will lead to a migration failure.

If you didn't use these web applications, run the following cleanup script and rerun the postupgrade:

```
Nlserver javascript -instance:[instance_name] -file [installation_path]/datakit/xtk/fra/js/removeOldWebApp.js
```

If you have modified these web applications and would like to continue using them in v7, you must activate the **allowSQLInjection** option in your different security zones and re-start the postupgrade. Refer to the [SQLData](../../migration/using/general-configurations.md#sqldata) section for more on this.

### Message Center {#message-center}

After a Message Center control instance migration, you must republish the transactional message templates for them to work.

In v7, the names of transactional message templates on execution instances have changed. They are currently prefixed by the operator name that corresponds to the control instance on which they are created, for example **control1_template1_rt** (where **control1** is the name of the operator). If you have a significant volume of templates, we recommend deleting old templates on control instances.

-->