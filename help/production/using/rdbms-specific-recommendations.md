---
product: campaign
title: Spécificités par SGBDR
description: Spécificités par SGBDR
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: a586d70b-1b7f-47c2-a821-635098a70e45
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1125'
ht-degree: 100%

---

# Spécificités par SGBDR{#rdbms-specific-recommendations}

Cette section contient une série de recommandations et de bonnes pratiques destinées à vous aider à mettre en place les plans de maintenance de vos bases de données pour chacun des moteurs SGBDR supportés par Adobe Campaign. Gardez à l&#39;esprit que ce ne sont que des recommandations. C&#39;est à vous qu&#39;il revient de les adapter en fonction de vos contraintes et de vos procédures internes. L&#39;administrateur de base de données est la personne qui doit être responsable de ces procédures.

## PostgreSQL {#postgresql}

### Détecter les grandes tables {#detecting-large-tables}

1. Ajoutez la vue suivante à votre base de données :

   ```
   create or replace view uvSpace
    as
    SELECT c1.relname AS tablename, c2.relname AS indexname, c2.relpages * 8 / 1024 AS size_mbytes, c2.relfilenode AS filename, 0 AS row_count
    FROM pg_class c1, pg_class c2, pg_index i
    WHERE c1.oid = i.indrelid AND i.indexrelid = c2.oid
    UNION 
    SELECT pg_class.relname AS tablename, NULL::"unknown" AS indexname, pg_class.relpages * 8 / 1024 AS size_mbytes, pg_class.relfilenode AS filename, cast(pg_class.reltuples as integer) AS row_count
    FROM pg_class
    WHERE pg_class.relkind = 'r'::"char"
    ORDER BY 3 DESC, 1, 2 DESC;
   ```

1. Lancez la commande suivante pour répertorier les tables volumineuses et les index :

   ```
   select * from uvSpace;
   ```

### Maintenance simple {#simple-maintenance}

Sous PostgreSQL, les commandes habituellement utilisées sont **vacuum full** et **reindex**.

Voici un exemple classique de plan de maintenance SQL qui doit être exécuté régulièrement à l&#39;aide de ces deux commandes :

```
vacuum full nmsdelivery;
 reindex table nmsdelivery;
 
 vacuum full nmsdeliverystat;
 reindex table nmsdeliverystat;
 
 vacuum full xtkworkflow;
 reindex table xtkworkflow;
 
 vacuum full xtkworkflowevent;
 reindex table xtkworkflowevent;
 
 vacuum full xtkworkflowjob;
 reindex table xtkworkflowjob;
 
 vacuum full xtkworkflowlog;
 reindex table xtkworkflowlog;
 
 vacuum full xtkworkflowtask;
 reindex table xtkworkflowtask;
 
 vacuum full xtkjoblog;
 reindex table xtkjoblog;
 
 vacuum full xtkjob;
 reindex table xtkjob;
 
 vacuum full nmsaddress;
 reindex table nmsaddress;

 vacuum full nmsdeliverypart;
 reindex table nmsdeliverypart;
 
 vacuum full nmsmirrorpageinfo;
 reindex table nmsmirrorpageinfo;
```

>[!NOTE]
>
>* Adobe conseille de commencer par les tables de petite taille. Si l&#39;opération de maintenance devait échouer sur les tables volumineuses (ce qui est davantage le cas que sur les petites tables), une partie de la maintenance serait déjà assurée.
>* Adobe recommande d&#39;ajouter tables spécifiques à votre modèle de données, notamment celles qui subissent des mises à jour massives. Par exemple, cela peut être le cas pour **NmsRecipient** si vous procédez chaque jour à d&#39;importantes réplications de données.
>* Les commandes **vacuum** et **re-index** verrouillent la table ce qui met certains processus en attente pendant toute la durée de la maintenance.
>* Pour les très grandes tables (généralement au-dessus de 5 Go), la commande **vacuum full** peut devenir assez inefficace et nécessiter beaucoup de temps. Adobe déconseille de l&#39;utiliser pour la table **YyyNmsBroadLogXxx**.
>* Cette opération de maintenance peut être effectuée par un workflow d’Adobe Campaign via une activité de type **[!UICONTROL SQL]** (voir à ce sujet [cette section](../../workflow/using/architecture.md)). Assurez-vous de lancer la maintenance pendant une période de faible activité et en dehors des périodes de sauvegarde.

>



### Reconstruire une base {#rebuilding-a-database}

PostgreSQL ne propose pas de moyen efficace pour effectuer une reconstruction de table en ligne, car la commande **vacuum full** verrouille la table, empêchant ainsi une production régulière. La maintenance doit donc être effectuée lorsque la table n&#39;est pas utilisée. Vous pouvez, au choix :

* effectuer la maintenance lorsque la plateforme Adobe Campaign est arrêtée,
* arrêter les processus Adobe Campaign susceptibles d&#39;écrire dans la table qui est en cours de reconstruction (par exemple **nlserver stop wfserver@nom_de_l&#39;instance** pour arrêter le processus de workflow).

Voici un exemple de défragmentation de table à l&#39;aide de fonctions qui permettent de générer le langage de définition de données (LDD) voulu. La requête SQL suivante permet de créer deux nouvelles fonctions : **GenRebuildTablePart1** et **GenRebuildTablePart2** qui peuvent être utilisées pour générer le LDD destiné à recréer une table.

* La première fonction permet de créer une table de travail (** _tmp** dans notre exemple) qui est une copie de la table d&#39;origine.
* La deuxième fonction supprime la table d&#39;origine et renomme la table de travail et ses index comme celle d&#39;origine.
* L&#39;utilisation de deux fonctions au lieu d&#39;une permet d&#39;éviter de supprimer définitivement la table d&#39;origine au cas où la première fonction échouerait.

```
 -- --------------------------------------------------------------------------
 -- Generate the CREATE TABLE DDL for a table
 -- --------------------------------------------------------------------------
 create or replace function GenTableDDL(text) returns text as $$
 declare
 vstrTable text;
 vrecFld RECORD;
 vstrDDL text;
 vstrFields text;
 vstrNsTable text;
 vstrTableSpace text;
 begin
 vstrTable = lower($1);
 
 vstrDDL = ;
 
 SELECT
 pg_catalog.quote_ident(n.nspname) || '.' || pg_catalog.quote_ident(c.relname),
 pg_catalog.quote_ident(t.spcname)
 INTO
 vstrNsTable, vstrTableSpace
 FROM
 pg_namespace n, pg_class c left outer join pg_tablespace t on c.reltablespace = t.oid
 WHERE
 n.oid = c.relnamespace AND
 c.relname = vstrTable;
 
 vstrDDL = 'CREATE TABLE ' || vstrNsTable || '_tmp(';
 
 vstrFields = ;
 FOR vrecFld IN
 SELECT
 pg_catalog.quote_ident(a.attname) ||
 ' ' || t.typname ||
 case when t.typname='varchar' then '(' || cast(a.atttypmod-4 as text) || ')'
 when t.typname='numeric' then '(' || cast((a.atttypmod-4)/65536 as text) || ',' || cast((a.atttypmod-4)%65536 as text) || ')'
 else end ||
 case when a.attnotnull then ' not null' else end ||
 case when a.atthasdef then ' default '|| d.adsrc else end as DDL
 FROM
 pg_type t, pg_class c, pg_attribute a LEFT OUTER JOIN pg_attrdef d ON d.adrelid=a.attrelid and d.adnum=a.attnum
 WHERE 
 a.attnum > 0 AND
 a.attrelid = c.oid AND
 t.oid = a.atttypid AND
 c.relname = vstrTable
 ORDER BY
 a.attnum
 LOOP
 IF vstrFields <> THEN
 vstrFields = vstrFields || ',' || chr(10) || ' ';
 ELSE
 vstrFields = vstrFields || chr(10) || ' ';
 END IF;
 vstrFields = vstrFields || vrecFld.DDL;
 END LOOP;
 
 vstrDDL = vstrDDL || vstrFields || chr(10) || ')';
 if vstrTableSpace <> then
 vstrDDL = vstrDDL || ' TABLESPACE ' || vstrTableSpace;
 end if;
 vstrDDL = vstrDDL || ';' || chr(10);
 
 return vstrDDL;
 END;
 $$ LANGUAGE plpgsql;

 -- --------------------------------------------------------------------------
 -- Generate the CREATE INDEX DDL for a table
 -- --------------------------------------------------------------------------
 create or replace function GenIndexDDL(text) returns text as $$
 declare
 vstrTable text;
 vrecIndex RECORD;
 vstrDDL text;
 viFld integer;
 vstrFld text;
 begin
 vstrTable = lower($1);
 
 vstrDDL = ;
 
 FOR vrecIndex IN
 SELECT
 i.indkey, i.indisunique,
 pg_catalog.quote_ident(c.relname) as tablename,
 pg_catalog.quote_ident(ic.relname) as indexname,
 pg_catalog.quote_ident(t.spcname) as tablespace
 FROM
 pg_class c, pg_index i, pg_class ic left outer join pg_tablespace t on ic.reltablespace = t.oid
 WHERE
 i.indexrelid = ic.oid AND
 i.indrelid = c.oid AND
 c.relname = vstrTable
 LOOP
 
  vstrDDL = vstrDDL || 'CREATE ';
  if vrecIndex.indisunique then
  vstrDDL = vstrDDL || 'UNIQUE ';
  end if;
  vstrDDL = vstrDDL ||
   'INDEX ' ||vrecIndex.indexname || '_tmp ON ' ||
   vrecIndex.tablename || '_tmp(';
 
  FOR viFld IN array_lower(vrecIndex.indkey, 1) .. array_upper(vrecIndex.indkey, 1) LOOP
  SELECT pg_catalog.quote_ident(a.attname) INTO vstrFld 
  FROM 
   pg_attribute a, pg_class c
  WHERE 
   a.attnum = vrecIndex.indkey[viFld] AND
   a.attrelid = c.oid AND c.relname=vstrTable;
  
  vstrDDL = vstrDDL || vstrFld;
  if viFld <> array_upper(vrecIndex.indkey, 1) then
   vstrDDL = vstrDDL || ', ';
  end if;
  END LOOP;
  vstrDDL = vstrDDL || ')';
 
  if vrecIndex.tablespace <> then
  vstrDDL = vstrDDL || 'TABLESPACE ' || vrecIndex.tablespace;
  end if;
  vstrDDL = vstrDDL || ';' || chr(10);
 
 END LOOP;
 
 return vstrDDL;
 END;
 $$ LANGUAGE plpgsql;

 -- --------------------------------------------------------------------------
 -- Generate the ALTER INDEX RENAME for a table
 -- --------------------------------------------------------------------------
 create or replace function GenRenameIndexDDL(text) returns text as $$
 declare
 vstrTable text;
 vrecIndex RECORD;
 vstrDDL text;
 begin
 vstrTable = lower($1);
 
 vstrDDL = ;
 
 FOR vrecIndex IN
  SELECT
  pg_catalog.quote_ident(n.nspname) as namespace,
  pg_catalog.quote_ident(ic.relname) as indexname
  FROM
  pg_namespace n, pg_class c, pg_index i, pg_class ic
  WHERE
  i.indexrelid = ic.oid AND
  n.oid = ic.relnamespace AND
  i.indrelid = c.oid AND
  c.relname = vstrTable
 LOOP
 
  vstrDDL = vstrDDL || 'ALTER INDEX ' || vrecIndex.namespace || '.' || vrecIndex.indexname ||
    '_tmp RENAME TO ' || vrecIndex.indexname ||
    ';' || chr(10);
 END LOOP;
 
 return vstrDDL;
 END;
 $$ LANGUAGE plpgsql;

 -- --------------------------------------------------------------------------
 -- Build a copy of a table, with index
 -- --------------------------------------------------------------------------
 create or replace function GenRebuildTablePart1(text) returns text as $$
 declare
 vstrTable text;
 vstrTmp text;
 vstrDDL text;
 begin
 vstrTable = lower($1);
  
 vstrDDL = ;
 
 SELECT GenTableDDL(vstrTable) INTO vstrTmp;
 vstrDDL = vstrDDL|| vstrTmp || chr(10);
 
 vstrDDL = vstrDDL|| 'INSERT INTO ' || vstrTable || '_tmp SELECT * FROM ' || vstrTable || ';'||chr(10);
 SELECT GenIndexDDL(vstrTable) INTO vstrTmp;
 
 vstrDDL = vstrDDL|| vstrTmp || chr(10);
 vstrDDL = vstrDDL|| 'VACUUM ANALYSE '|| vstrTable || '_tmp;' ||chr(10);
 
 return vstrDDL;
 end;
 $$ LANGUAGE plpgsql;
 
 -- --------------------------------------------------------------------------
 -- Drop the original table and rename the copy
 -- --------------------------------------------------------------------------
 create or replace function GenRebuildTablePart2(text) returns text as $$
 declare
 vstrTable text;
 vstrTmp text;
 vstrDDL text;
 begin
 vstrTable = lower($1);
  
 vstrDDL = 'DROP TABLE ' || vstrTable||';'|| chr(10);
 vstrDDL = vstrDDL|| 'ALTER TABLE ' || vstrTable || '_tmp RENAME TO ' || vstrTable ||';'|| chr(10);
 
 SELECT GenRenameIndexDDL(vstrTable) INTO vstrTmp;
 vstrDDL = vstrDDL|| vstrTmp || chr(10);
 
 return vstrDDL;
 end;
 $$ LANGUAGE plpgsql;
```

L&#39;exemple qui suit peut être utilisé dans un workflow pour reconstruire les tables requises plutôt que d&#39;utiliser la commande **vacuum/rebuild** :

```
function sqlGetMemo(strSql)
 {
 var res = sqlSelect("s, m:memo", strSql);
 return res.s.m.toString();
 }

 function RebuildTable(strTable)
 {
 // Rebuild a table_tmp
 var strSql = sqlGetMemo("select GenRebuildTablePart1('"+strTable+"')");
 logInfo("Rebuilding table '"+strTable+"'...");
 // logInfo(strSql);
 sqlExec(strSql);
 
 // If fails, there is an exception thrown and so we do not delete the original table
 strSql = sqlGetMemo("select GenRebuildTablePart2('"+strTable+"')");
 logInfo("Swapping table '"+strTable+"'...");
 //logInfo(strSql);
 sqlExec(strSql);
 }
 
 RebuildTable('nmsrecipient');
 RebuildTable('nmsrcpgrlrel');
 // ... other tables here
```

## Oracle {#oracle}

Veuillez consulter votre administrateur de base de données pour connaître les procédures les mieux adaptées à votre version d&#39;Oracle.

## Microsoft SQL Server {#microsoft-sql-server}

>[!NOTE]
>
>Pour Microsoft SQL Server, vous pouvez utiliser le plan de maintenance décrit sur [cette page](https://ola.hallengren.com/sql-server-index-and-statistics-maintenance.html).

L’exemple ci-dessous concerne Microsoft SQL Server 2005. Si vous utilisez une autre version, contactez l’administrateur de base de données pour connaître les procédures de maintenance de cette version.

1. Connectez-vous à Microsoft SQL Server Management Studio avec un identifiant auquel ont été attribués des droits administrateur.
1. Cliquez avec le bouton droit de la souris sur le dossier **[!UICONTROL Gestion > Plans de maintenance]** et sélectionnez **[!UICONTROL Assistant Plan de maintenance]** dans le menu contextuel.
1. Cliquez sur **[!UICONTROL Suivant]** lorsque la page d&#39;accueil s&#39;affiche.
1. Choisissez le type de plan de maintenance que vous souhaitez créer (exécution de la maintenance en une fois ou création d&#39;un plan pour chaque tâche de maintenance), puis cliquez sur **[!UICONTROL Modifier]**.
1. Dans la fenêtre **[!UICONTROL Propriétés de la planification du travail]**, choisissez les paramètres d&#39;exécution voulus et cliquez sur **[!UICONTROL OK]** puis sur **[!UICONTROL Suivant]** .
1. Sélectionnez les tâches de maintenance à effectuer comme illustré ci-dessous puis cliquez sur **[!UICONTROL Suivant]** .

   >[!NOTE]
   >
   >Nous vous conseillons d&#39;effectuer au moins les tâches de maintenance comme illustré ci-dessus. Vous pouvez également sélectionner la tâche de mise à jour des statistiques si vous le souhaitez, sachant que cette tâche est déjà effectuée par le workflow de nettoyage de la base.

1. Dans la liste déroulante, sélectionnez la base sur laquelle vous souhaitez effectuer la tâche **[!UICONTROL Vérifier l&#39;intégrité de la base de données]**.
1. Sélectionnez la base concernée et cliquez sur **[!UICONTROL OK]** puis **[!UICONTROL Suivant]** .
1. Configurez la taille maximale allouée à votre base de données puis cliquez sur **[!UICONTROL Suivant]** .

   >[!NOTE]
   >
   >Si la taille de la base devait dépasser la limite fixée, le système de maintenance essaiera de détruire les données non-utilisées pour libérer de l&#39;espace-disque.

1. Effectuez une réorganisation ou une reconstruction de l&#39;index :

   * Si le taux de fragmentation de l&#39;index est compris entre 10% et 40%, il est recommandé d&#39;effectuer une réorganisation :

      Choisissez la base de données et les objets (tables ou vues) dont vous voulez réorganiser l&#39;index puis cliquez sur **[!UICONTROL Suivant]** .

      >[!NOTE]
      >
      >Selon votre configuration vous ne pourrez sélectionner que les tables sélectionnées précédemment ou la totalité des tables de votre base de données.

   * Si le taux de fragmentation de l&#39;index est supérieur à 40%, il est recommandé d&#39;effectuer une reconstruction :

      Choisissez les options de la tâche de reconstruction de l&#39;index puis cliquez sur **[!UICONTROL Suivant]** .

      >[!NOTE]
      >
      >Le processus de reconstruction de l&#39;index est plus contraignant en termes d&#39;utilisation du processeur et verrouille les ressources de la base de données. Cochez l&#39;option **[!UICONTROL Keep index online while reindexing]** (Conserver l&#39;index en ligne lors de la réindexation) si vous souhaitez que l&#39;index soit disponible pendant la reconstruction.

1. Choisissez les options du rapport d&#39;activité des tâches de maintenance puis cliquez sur **[!UICONTROL Suivant]** .
1. Vérifiez la liste des tâches du plan de maintenance puis cliquez sur **[!UICONTROL Terminer]** .

   L&#39;état d&#39;avancement du plan de maintenance et le statut des différentes étapes s&#39;affiche à l&#39;écran.

1. Lorsque le plan de maintenance est arrivé à son terme, cliquez sur **[!UICONTROL Fermer]** .
1. Dans l’explorateur de Microsoft SQL Server, double-cliquez sur le dossier **[!UICONTROL Gestion > Plans de maintenance]**.
1. Sélectionnez le plan de maintenance d&#39;Adobe Campaign : les différentes étapes sont présentées sous la forme d&#39;un workflow.

   Vous remarquerez qu&#39;un objet a été créé dans le dossier **[!UICONTROL SQL Server Agent > Travaux]**. Cet objet permet de lancer le plan de maintenance. Dans notre exemple il n&#39;y a qu&#39;un seul objet car toutes les tâches de maintenance font partie du même plan de maintenance.

   >[!IMPORTANT]
   >
   >Pour que cet objet puisse s’exécuter, l’agent Microsoft SQL Server doit être activé.

**Configuration d&#39;une base de données distincte pour les tables de travail**

>[!NOTE]
>
>Ce paramétrage est facultatif.

L&#39;option **WdbcOptions_TempDbName** permet de configurer une base de données distincte pour les tables de travail de Microsoft SQL Server. Cette configuration permet d&#39;optimiser les sauvegardes et la réplication.

Cette option peut être utilisée si vous souhaitez que les tables de travail (par exemple, les tables créées pendant l&#39;exécution d&#39;un workflow) soient créées dans une autre base de données.

Lorsque vous définissez l&#39;option sur &quot;tempdb.dbo.&quot;, les tables de travail sont créées dans la base de données temporaire par défaut de Microsoft SQL Server. L&#39;administrateur de la base de données doit autoriser l&#39;accès en écriture à la base de données tempdb.

Si cette option est définie, elle sera utilisée sur toutes les bases de données Microsoft SQL Server configurées dans Adobe Campaign (base de données principale et comptes externes). Notez que si deux comptes externes partagent le même serveur, des conflits peuvent survenir (car tempdb est unique). De même, si deux instances Campaign utilisent le même serveur MSSQL, il peut y avoir des conflits si elles utilisent la même tempdb.
