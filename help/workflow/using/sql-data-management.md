---
title: Gestion des données SQL
seo-title: Gestion des données SQL
description: Gestion des données SQL
seo-description: null
page-status-flag: never-activated
uuid: b6057496-2dd5-4289-96df-98378e4f0ae7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 18d6f5e1-308f-4080-b7c4-ebf836f74842
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7bcf222f41c0e40368644b76197b07f2ded699f0

---


# Gestion des données SQL{#sql-data-management}

L&#39;activité **Gestion des données SQL** permet d&#39;écrire vos requêtes SQL pour créer et remplir les tables de travail.

## Prérequis {#prerequisites}

Avant de configurer l&#39;activité, vérifiez que les prérequis suivants sont remplis :

* L&#39;activité est disponible pour les sources de données distantes uniquement. Le package **[!UICONTROL FDA]** (Federated Data Access) doit donc être installé sur votre instance (voir [cette section](../../platform/using/about-fda.md)).
* Le schéma sortant doit exister dans la base de données et être associé à une base de données FDA (pour plus d&#39;informations sur les schémas de données, reportez-vous à [cette section](../../configuration/using/about-schema-reference.md)).
* L&#39;opérateur exécutant le workflow doit disposer du droit nommé **[!UICONTROL USE SQL DATA MANAGEMENT ACTIVITY (useSqlDmActivity)]**. Pour plus d&#39;informations sur les droits nommés, reportez-vous à [cette section](../../platform/using/access-management.md#named-rights).

## Configuration de l&#39;activité Gestion des données SQL {#configuring-the-sql-data-management-activity}

1. Indiquez le **[!UICONTROL Libellé]** de l&#39;activité.
1. Sélectionnez le **[!UICONTROL Compte externe]** à utiliser, puis le **[!UICONTROL Schéma sortant]** associé à ce compte externe.

   >[!CAUTION]
   >
   >Le schéma sortant est fixe et ne peut pas être édité.

1. Ajoutez le script SQL.

   >[!CAUTION]
   >
   >Il incombe à la personne chargée de l&#39;écriture du script SQL de s&#39;assurer que celui-ci est fonctionnel et que ses références (noms de champs, etc.) sont conformes au schéma sortant.

   Si vous souhaitez charger un code SQL existant, sélectionnez l&#39;option **[!UICONTROL Le code SQL est contenu dans une entité stockée dans la base]**. Les scripts SQL doivent être créés et stockés dans le menu **[!UICONTROL Administration]** / **[!UICONTROL Paramétrage]** / **[!UICONTROL Scripts SQL]**.

   Sinon, saisissez ou effectuez un copier-coller du script SQL dans la zone dédiée.

   ![](assets/sql_datamanagement.png)

   L&#39;activité permet d&#39;utiliser les variables suivantes dans le script :

   * **activity.tableName** : nom SQL de la table de travail sortante.
   * **task.incomingTransitionByName(‘nom’).tableName** : nom SQL de la table de travail associée à la transition entrante à utiliser (la transition est identifiée par son nom).

      >[!NOTE]
      >
      >La valeur (&#39;nom&#39;) correspond au champ **[!UICONTROL Nom]** des propriétés de la transition.

1. Si le script SQL contient déjà des commandes pour créer une table de travail sortante, désélectionnez l&#39;option **[!UICONTROL Créer automatiquement une table de travail]**. Sinon, une table de travail est automatiquement créée lorsque le workflow est exécuté.
1. Cliquez sur **[!UICONTROL OK]** pour valider la configuration de l&#39;activité.

L&#39;activité est maintenant configurée. Elle est prête à être exécutée dans le workflow.

>[!CAUTION]
>
>Une fois l&#39;activité exécutée, le nombre d&#39;enregistrements de la transition sortante est fourni à titre indicatif uniquement. Il peut varier en fonction du niveau de complexité du script SQL.
>  
>Si l&#39;activité est redémarrée, l&#39;intégralité du script est exécutée depuis le début, quel que soit le statut d&#39;exécution.

## Exemples de script SQL {#sql-script-samples}

>[!NOTE]
>
>Les exemples de script présentés dans cette section sont destinés à être exécutés sous PostgreSQL.

Le script suivant permet de créer une table de travail et d&#39;y insérer des données :

```
CREATE UNLOGGED TABLE <%= activity.tableName %> (
  iRecipientId INTEGER DEFAULT 0,
  sFirstName VARCHAR(100),
  sMiddleName VARCHAR(100),
  sLastName VARCHAR(100),
  sEmail VARCHAR(100)
);

INSERT INTO <%= activity.tableName %>
SELECT iRecipientId, sFirstName, sMiddleName, sLastName, sEmail
FROM nmsRecipient
GROUP BY iRecipientId, sFirstName, sMiddleName, sLastName, sEmail;
```

Le script suivant permet d&#39;effectuer une opération CTAS (CREATE TABLE AS SELECT) et de créer un index de table de travail :

```
CREATE TABLE <%= activity.tableName %>
AS SELECT iRecipientId, sEmail, sFirstName, sLastName, sMiddleName
FROM nmsRecipient
WHERE sEmail IS NOT NULL
GROUP BY iRecipientId, sEmail, sFirstName, sLastName, sMiddleName;

CREATE INDEX ON <%= activity.tableName %> (sEmail);

ANALYZE <%= activity.tableName %> (sEmail);
```

Le script suivant permet de fusionner deux tables de travail :

```
CREATE TABLE <%= activity.tableName %>
AS SELECT i1.sFirstName, i1.sLastName, i2.sEmail
FROM <%= task.incomingTransitionByName('input1').tableName %> i1
JOIN <%= task.incomingTransitionByName('input2').tableName %> i2 ON (i1.id = i2.id)
```

