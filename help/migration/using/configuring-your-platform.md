---
product: campaign
title: Adapter votre configuration
description: Découvrez comment adapter votre configuration avant et après une migration vers Campaign v7
audience: migration
content-type: reference
topic-tags: migration-procedure
exl-id: ad71dead-c0ca-42d5-baa8-0f340979231a
source-git-commit: 327f220d6700242308ef3738a38cc95b970e3f46
workflow-type: tm+mt
source-wordcount: '1985'
ht-degree: 100%

---

# Adapter votre configuration{#configuring-your-platform}

![](../../assets/v7-only.svg)

Certaines modifications majeures d’Adobe Campaign v7 nécessitent une configuration spécifique. Ces configurations peuvent être nécessaires avant ou après la migration.

Le paramétrage détaillé à effectuer dans Adobe Campaign v7 lors de la migration depuis Campaign v5 ou v6 est disponible dans [cette page](general-configurations.md).


Pendant la migration, le tableau **NmsRecipient** est reconstruit à partir de la définition des schémas. Toute modification apportée à la structure SQL de cette table en dehors d’Adobe Campaign sera perdue.

Exemples d&#39;éléments à vérifier :

* Si vous avez ajouté une colonne (ou un index) dans la table **NmsRecipient** mais que vous ne l&#39;avez pas décrite dans le schéma, celle-ci ne sera pas conservée.
* L&#39;attribut **tablespace** reprend ses valeurs par défaut, c&#39;est-à-dire celles définies dans l&#39;assistant de déploiement.
* Si vous avez ajouté une vue qui référence le tableau **NmsRecipient**, vous devez la supprimer avant la migration.


## Avant la migration {#before-the-migration}

Dans le cadre d&#39;une migration vers Adobe Campaign v7, les éléments suivants doivent être paramétrés. Ces paramétrages impliquent une prise en compte avant le lancement du **postupgrade**.

* Fuseaux horaires

   Dans le cadre d&#39;une migration depuis une plateforme v5.11, vous devez indiquer le fuseau horaire à utiliser lors du postupgrade.

   Si vous souhaitez utiliser le mode « multi timezone », consultez [cette section](../../migration/using/general-configurations.md#time-zones).

   Si vous utilisez Oracle comme moteur de base de données, vérifiez que les fichiers de fuseaux horaires Oracle sont bien synchronisés entre le serveur applicatif et le serveur de base. [En savoir plus](../../migration/using/general-configurations.md#oracle)

* Zones de sécurité

   Pour des raisons de sécurité, la plateforme Adobe Campaign n’est plus accessible par défaut : vous devez configurer les zones de sécurité, et pour cela collecter, avant la migration, les adresses IP des utilisateurs. [En savoir plus](../../migration/using/general-configurations.md#security)

* Syntaxe

   Certains codes JavaScript peuvent ne plus être acceptés dans la version v7 en raison de l’utilisation d’un nouvel interpréteur. [En savoir plus](../../migration/using/general-configurations.md#javascript).

   Parallèlement, une nouvelle syntaxe est introduite dans Adobe Campaign v7 pour remplacer celle basée sur SQLData. Si vous utilisez des éléments de code avec cette syntaxe, vous devez les adapter. [En savoir plus](../../migration/using/general-configurations.md#sqldata)

* Mots de passe

   Vous devez configurer les mots de passe **Admin** et **Interne**. [En savoir plus](../../migration/using/before-starting-migration.md#user-passwords)

* Arborescence

   Si vous effectuez une migration à partir d&#39;une plateforme v5.11, vous devez réorganiser les dossiers de l&#39;arborescence conformément aux normes Adobe Campaign v6. [En savoir plus](../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11).

* Interaction

   Si vous migrez depuis Campaign v6.02 et que vous utilisez le module **Interaction**, vous devez supprimer toutes les références de schéma 6.02 qui n’existent plus dans la v7. [En savoir plus](../../migration/using/general-configurations.md#interaction)

## Après la migration {#after-the-migration}

Après avoir exécuté **postupgrade**, vérifiez et configurez les éléments suivants :

* Pages miroir

   Dans la version v6.x, le bloc de personnalisation des pages miroir a changé. Cette nouvelle version renforce la sécurité lors de l&#39;accès à ces pages.

   Si vous utilisez le bloc de personnalisation de la version v5 dans vos messages, les pages miroir ne s&#39;affichent pas. Adobe recommande vivement d&#39;utiliser le nouveau bloc de personnalisation lors de l&#39;insertion d&#39;une page miroir dans vos messages.

   Toutefois, à titre de solution temporaire (et comme les pages miroir sont toujours actives), vous pouvez revenir à l’ancien bloc de personnalisation pour éviter ce problème en modifiant l’option **[!UICONTROL XtkAcceptOldPasswords]** et en la définissant sur **[!UICONTROL 1]**. L’utilisation du nouveau bloc de personnalisation v6.x n’en sera pas affectée.

* Syntaxe

   Si vous rencontrez des erreurs, lors du postupgrade, liées à la syntaxe SQLData, vous devez temporairement activer l’option **allowSQLInjection** dans le fichier **serverConf.xml**, le temps de réécrire le code. Une fois le code adapté, n’oubliez pas de réactiver la sécurité. [En savoir plus](../../migration/using/general-configurations.md#sqldata)

* Conflits

   La migration étant effectuée au travers d’un postupgrade, des conflits peuvent apparaître au niveau des rapports, formulaires ou applications web. Ces conflits peuvent être résolus manuellement depuis la console. [En savoir plus](../../migration/using/general-configurations.md#conflicts)

* Tomcat

   Si vous avez personnalisé le dossier d&#39;installation, vérifiez qu&#39;il est correctement mis à jour après la migration. [En savoir plus](../../migration/using/general-configurations.md#tomcat)

* Rapports

   Tous les rapports prêts à l’emploi utilisent actuellement le moteur de rendu v6.x. Si vous aviez ajouté du code JavaScript dans les rapports, certains éléments peuvent être affectés. [En savoir plus](../../migration/using/general-configurations.md#reports)

* Applications web

   Après le postupgrade, si vous rencontrez des problèmes de connexion à vos applications web identifiées, vous devez activer les options **allowUserPassword** et **sessionTokenOnly** dans le fichier **serverConf.xml**. Pour éviter tout problème de sécurité, ces deux options doivent être réactivées une fois le problème résolu. [En savoir plus](../../migration/using/general-configurations.md#identified-web-applications)

   Selon le type d’applications web et leur configuration, vous devez effectuer des manipulations complémentaires pour en assurer le bon fonctionnement. [En savoir plus](../../migration/using/general-configurations.md#web-applications)

   Si vous effectuez une migration à partir d’une plateforme v5.11, des paramétrages supplémentaires doivent être réalisés. [En savoir plus](../../migration/using/general-configurations.md#specific-configurations-in-v5-11.md)

* Zones de sécurité

   Avant de démarrer le serveur, vous devez configurer les zones de sécurité. [En savoir plus](../../installation/using/security-zones.md) et [rendez-vous ici](../../migration/using/general-configurations.md#security)

* Workflows

   Si vous effectuez une migration à partir d’une plateforme v5.11, vous devez contrôler le dossier des workflows. [En savoir plus](../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11)

* Effectuer un tracking

   Si vous effectuez une migration à partir d&#39;une plateforme v5.11, vous devez configurer le mode de tracking. [En savoir plus](../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11)

* Interaction

   Si vous utilisez **Interaction**, vous devez ajuster les paramètres après la migration. [En savoir plus](../../migration/using/general-configurations.md#interaction)

* Tableaux de bord

   Si une erreur client apparaît, vous devez soit mettre à jour vos tableaux de bord avec le nouveau code Adobe Campaign v7, soit copier manuellement les fichiers suivants de l’instance v6.02 vers l’instance v7 :

   ```
   v6.02 files and spaces:
   /usr/local/neolane/nl6/datakit/xtk/eng/css/dropDownMenu.css
   /usr/local/neolane/nl6/datakit/xtk/eng/js/client/dropDownMenu.js
   v6.1 files and spaces:
   /usr/local/neolane/nl6/deprecated/xtk/css/dropDownMenu.css
   /usr/local/neolane/nl6/deprecated/xtk/js/client/dropDownMenu.js  
   ```


## Paramétrages spécifiques des versions v5.11 à v7{#specific-configurations-in-v5-11}

![](../../assets/v7-only.svg)

Cette section décrit le paramétrage supplémentaire à effectuer lorsque vous migrez depuis une v5.11. Vous devez également effectuer le paramétrage décrit dans la section [Paramétrages généraux](../../migration/using/general-configurations.md).

### Des applications web {#web-applications-v5}

L&#39;avertissement suivant apparaît systématiquement lors de la migration :

```
The webApp ids have been modified during the migration process. Please make sure to check your scripts/css for broken compatibility (any client side JavaScript or css dealing directly with another element through its id is impacted). See file 'c:\svn\602\nl\build\ncs\var\upgrade/postupgrade/webAppsMigration_*************.txt' for details about the references that were automatically updated, if any.
```

Certains composants des applications web, par exemple les différents champs d&#39;un formulaire, possèdent des identifiants. Ces identifiants (attributs @id), utilisés dans le code XML des applications web, ne sont plus générés de la même manière. Ils ne sont pas visibles dans l&#39;interface et vous ne devez normalement pas les utiliser. Cependant, dans certains cas, il se peut que ces identifiants aient été utilisés en paramétrage pour personnaliser l&#39;apparence des applications web, par exemple via une feuille de style ou du code JavaScript.

Lors de la migration, vous devez **impérativement** vérifier le fichier de logs dont le chemin est indiqué dans l&#39;avertissement :

* **Le fichier n&#39;est pas vide :** celui-ci contient des avertissements correspondant à des incohérences qui existaient avant la migration, et qui existent donc toujours. Il peut s&#39;agir par exemple de code JavaScript dans une application web référençant un identifiant qui n&#39;existe pas. Chaque erreur doit être vérifiée et corrigée.
* **Le fichier est vide :** cela signifie qu&#39;Adobe Campaign n&#39;a détecté aucun problème.

Que le fichier soit vide ou non, vous devez vérifier que ces identifiants ne sont pas utilisés en paramétrage à d&#39;autres endroits, et le cas échéant adapter ce paramétrage.

### Workflows {#workflows}

Le nom du répertoire d&#39;installation d&#39;Adobe Campaign ayant changé, il se peut que certains workflows ne fonctionnent pas après la migration. En effet, si un workflow fait référence au répertoire nl5 dans l&#39;une ses activités, celui-ci sera en erreur. Cette référence doit être remplacée par **build**. Une requête SQL peut être exécutée pour identifier ces workflows (par exemple, PostgreSQL) :

```
SELECT   iWorkflowId, sInternalName, sLabel 
FROM XtkWorkflow 
WHERE mData LIKE '%nl5%';
```

### MySQL {#mysql}

>[!CAUTION]
>
>MySQL est uniquement supporté en v7 comme moteur de la base principale dans le cas de migrations depuis une version 6.02 ou 5.11 utilisant ce moteur.

MySQL ne gère pas les fuseaux horaires par défaut. Pour activer la gestion des fuseaux horaires, exécutez la commande suivante :

```
mysql_tzinfo_to_sql /usr/share/zoneinfo | mysql -u root mysql
```

>[!NOTE]
>
>Pour plus d’informations, voir la page [ https://dev.mysql.com/doc/refman/8.0/en/time-zone-support.html](https://dev.mysql.com/doc/refman/8.0/en/time-zone-support.html).

Si des modifications de structure de base ont été effectuées, par exemple lors du paramétrage (création d&#39;index spécifiques, création de vues SQL, etc.), certaines précautions doivent être prises lors de la migration. En effet, certaines modifications peuvent générer des incompatibilités avec la procédure de migration. Par exemple, la création de vues SQL contenant des champs de type **Timestamp** n&#39;est pas compatible avec l&#39;option **usetimestamptz**. Nous vous conseillons donc de suivre les recommandations ci-dessous :

1. Avant la migration, effectuez une sauvegarde de la base.
1. Supprimez les modifications SQL.
1. Effectuer le postupgrade
   >[!NOTE]
   >
   >Vous devez suivre la procédure de migration décrite dans [cette section](../../migration/using/migrating-in-windows-for-adobe-campaign-7.md).
1. Réintégrez les modifications SQL.

Dans cet exemple, une vue **NmcTrackingLogMessages** a été créée et celle-ci contient un champ **Timestamp** nommé **tslog**. Dans ce cas, la procédure de migration échoue et le message d&#39;erreur suivant apparaît :

```
2011-10-04 11:57:51.804Z B67B28C0 1 info log Updating table 'NmcTrackingLogMessages'
2011-10-04 11:57:51.804Z B67B28C0 1 error log PostgreSQL error: ERROR: cannot alter type of a column used by a view or rule\nDETAIL: rule _RETURN on view nmctrackinglogmessagesview depends on column "tslog"\n (iRc=-2006)
2011-10-04 11:57:51.804Z B67B28C0 1 error log SQL order 'ALTER TABLE NmcTrackingLogMessages ALTER COLUMN tsLog TYPE TIMESTAMPTZ' was not executed. (iRc=-2006)
```

Pour garantir le bon fonctionnement du postupgrade, vous devez impérativement supprimer la vue avant la migration, puis la recréer après la migration, en l&#39;adaptant au mode TIMESTAMP WITH TIMEZONE.

### Tracking {#tracking}

La formule de tracking a été modifiée. Lors de la migration, l’ancienne formule (v5) est remplacée par la nouvelle (v7). Si vous utilisez une formule personnalisée dans Adobe Campaign v5, cette configuration doit être adaptée dans Adobe Campaign v7 (options **NmsTracking_ClickFormula** et **NmsTracking_OpenFormula**).

La gestion du tracking web a également été modifiée. Une fois la migration vers la version v7 effectuée, vous devez démarrer l’assistant de déploiement pour terminer la configuration du tracking web.

![](assets/migration_web_tracking.png)

Trois modes sont disponibles :

* **Tracking Web de session** : Si le package **[!UICONTROL Leads]** n&#39;est pas installé, cette option est sélectionnée par défaut. Cette option est la plus avantageuse en termes de performances et permet de limiter la taille des logs de tracking.
* **Tracking Web permanent**
* **Tracking Web anonyme** : Si le package **[!UICONTROL Leads]** est installé, cette option est sélectionnée par défaut. Cette option est la plus contraignante en termes de performances. Comme pour l&#39;option Tracking Web permanent, la colonne **sSourceId** doit être indexée (dans la table de tracking et la table **CrmIncomingLead**).

>[!NOTE]
>
>Pour plus d&#39;informations sur ces trois modes, consultez [cette section](../../configuration/using/about-web-tracking.md).

### L&#39;arborescence Adobe Campaign v7 {#campaign-vseven-tree-structure}

Lors de la migration, l&#39;arborescence est automatiquement réorganisée selon les nouvelles normes de la v7. Les nouveaux dossiers sont ajoutés, les dossiers obsolètes supprimés et le contenu de ces derniers placés dans le dossier &quot;To move&quot;. Tous les éléments de ce dossier doivent être vérifiés après la migration, et pour chacun, le consultant doit décider s&#39;il souhaite le conserver ou le supprimer. Il doit ensuite replacer au bon endroit les éléments à conserver.

Une option a été ajoutée permettant de désactiver la migration automatique de l&#39;arborescence. Celle-ci devient donc manuelle. Les dossiers obsolètes ne sont pas supprimés et les nouveaux dossiers ne sont pas ajoutés. Cette option n&#39;est à utiliser que dans le cas où l&#39;arborescence d&#39;usine v5 a subi un nombre de modifications trop important. L&#39;option est à ajouter dans la console, avant la migration, au niveau du noeud **[!UICONTROL Administration > Options]** :

* Nom interne : NlMigration_KeepFolderStructure
* Type de données : Entier
* Valeur (texte) : 1

Si vous utilisez cette option, vous devrez, après la migration, supprimer les dossiers obsolètes, ajouter les nouveaux dossiers et effectuer toutes les vérifications nécessaires.

**Liste des nouveaux dossiers** :

Les dossiers à ajouter après la migration sont les suivants :

| Nom interne | Libellé | Condition |
|---|---|---|
| nmsAutoObjects | Objets créés automatiquement | - |
| nmsCampaignAdmin | Gestion de campagne | - |
| nmsCampaignMgt | Gestion de campagne | - |
| nmsCampaignRes | Gestion de campagne | - |
| nmsModels | Modèles | - |
| nmsOnlineRes | On-line | - |
| nmsProduction | Production | - |
| nmsProfilProcess | Traitements | - |
| xtkDashboard | Tableaux de bord | - |
| xtkPlatformAdmin | Plateforme | - |
| nmsLocalOrgUnit | Entités organisationnelles | - |
| nmsMRM | MRM | MRM installé |
| nmsOperations | Opérations | Campaign installé |

**Liste des dossiers obsolètes** :

Les dossiers obsolètes, à supprimer après la migration, sont les suivants :

>[!NOTE]
>
>Tout le contenu des dossiers obsolètes doit être vérifié, et pour chaque élément, le consultant doit décider s&#39;il souhaite le conserver ou le supprimer. Il doit ensuite replacer au bon endroit les éléments à conserver.

| Nom interne | Libellé | Condition |
|---|---|---|
| nmsAdministration | Administration  | - |
| nmsDeliveryMgt | Exécution de campagne | - |
| ncmContent | Gestion de contenu | Content Manager installé |
| ncmForm | Formulaires de saisie | Content Manager installé |
| ncmImage | Images | Content Manager installé |
| ncmJavascript | Codes JavaScript | Content Manager installé |
| ncmJst | Templates JavaScript | Content Manager installé |
| ncmParameters | Configuration  | Content Manager installé |
| ncmSrcSchema | Schémas de données | Content Manager installé |
| ncmStylesheet | Feuilles de style XSL | Content Manager installé |
| nmsAdminPlan | Administration  | Campaign installé |
| nmsResourcePlan | Ressources | Campaign installé |
| nmsResourcesModels | Modèles | Campaign installé |
| nmsRootPlan | Gestion de campagne | Campaign installé |
| nmsOperator | Opérateurs marketing | MRM installé |


## Paramétrages spécifiques des versions v6.02 à v7{#specific-configurations-in-v6-02}

![](../../assets/v7-only.svg)

La section suivante décrit le paramétrage supplémentaire à effectuer lorsque vous migrez depuis une v6.02. Vous devez également effectuer le paramétrage décrit sur [cette page](../../migration/using/general-configurations.md).

### Des applications web {#web-applications-v6}

Si vous migrez depuis une v6.02, des logs d&#39;erreur peuvent apparaître concernant des applications web de type vues d&#39;ensemble (overview). Exemples de messages d&#39;erreur :

```
[PU-0006] Entity of type : 'xtk:entityBackupNew' and Id 'nms:webApp|taskOverview', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'xtk:formDictionary' and Id 'nms:webApp|lastTasks', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'nms:webApp' and Id 'taskOverview', expression '[SQLDATA[' was found : '...@owner-id] IN ([SQLDATA[select iGroupid...'. (iRc=-1)
```

Ces applications web utilisaient du SQLData et ne sont plus compatibles avec la v7, en raison du renforcement de la sécurité. Ces erreurs entraineront un échec de migration.

Si vous n&#39;utilisiez pas ces applications web, exécutez le script de nettoyage suivant et relancez le postupgrade :

```
Nlserver javascript -instance:[instance_name] -file [installation_path]/datakit/xtk/fra/js/removeOldWebApp.js
```

Si vous aviez modifié ces applications web et souhaitez continuer à les utiliser en v7, vous devez activer l&#39;option **allowSQLInjection** dans vos différentes zones de sécurité et relancer le postupgrade. Consultez la section [SQLData](../../migration/using/general-configurations.md#sqldata) pour en savoir plus.

### Message Center {#message-center}

Après une migration d&#39;une instance de pilotage Message Center, vous devez republier les modèles de messages transactionnels pour que ceux-ci fonctionnent.

Dans la v7, les noms des modèles de messages transactionnels sur les instances d&#39;exécution ont changé. Ils sont précédés du nom de l&#39;opérateur qui correspond à l&#39;instance de pilotage sur laquelle ils sont créés, par exemple **control1_template1_rt** (où **control1** est le nom de l&#39;opérateur). Si vous disposez d&#39;un volume important de modèles, nous vous recommandons de supprimer les anciens sur les instances de pilotage.