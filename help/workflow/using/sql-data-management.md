---
product: campaign
title: Gestion des données SQL
description: En savoir plus sur l’activité de workflow de gestion des données SQL
feature: Workflows
hide: true
exl-id: cada78cb-658f-4b9e-8136-31c17cb1d82f
TQID: https://experienceleague.adobe.com/69utVGZghklulU5x5HcHF-hA-UKbSgGLQZ-CtlVanL0
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a658c786-869b-4194-a780-2594d663adda
topic_v2: id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 454
ht-degree: 79%

---

# Gestion des données SQL{#sql-data-management}



L&#39;activité **Gestion des données SQL** permet d&#39;écrire vos requêtes SQL pour créer et remplir les tables de travail.

## Conditions préalables requises {#prerequisites}

Avant de configurer l&#39;activité, vérifiez que les prérequis suivants sont remplis :

* L&#39;activité est disponible uniquement pour les sources de données distantes. Le package **[!UICONTROL FDA]** (Federated Data Access) doit donc être installé sur votre instance. [En savoir plus](../../installation/using/about-fda.md).

  Pour plus d&#39;informations à ce sujet, en fonction de la version de Campaign, reportez-vous aux sections suivantes :

  ![](assets/do-not-localize/v7.jpeg)[Documentation de Campaign v7](../../installation/using/about-fda.md)

  ![](assets/do-not-localize/v8.png)[Documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/connect/fda.html?lang=fr)

* Le schéma sortant doit exister dans la base de données et être lié à une base de données FDA.
* L&#39;opérateur qui exécute le workflow doit disposer du droit nommé **[!UICONTROL USE SQL DATA MANAGEMENT ACTIVITY (useSqlDmActivity)]** [En savoir plus](../../platform/using/access-management-named-rights.md).

## Configuration de l&#39;activité Gestion des données SQL {#configuring-the-sql-data-management-activity}

1. Indiquez le **[!UICONTROL Libellé]** de l&#39;activité.
1. Sélectionnez le **[!UICONTROL Compte externe]** à utiliser, puis le **[!UICONTROL Schéma sortant]** associé à ce compte externe.

   >[!CAUTION]
   >
   >Le schéma sortant est fixe et ne peut pas être édité.

1. Ajoutez le script SQL.

   >[!CAUTION]
   >
   >Il incombe au rédacteur de script SQL de s’assurer que le script SQL est fonctionnel et que ses références (noms de champs, etc.) sont conformes au schéma sortant.

   Si vous souhaitez charger un code SQL existant, sélectionnez l&#39;option **[!UICONTROL Le code SQL est contenu dans une entité stockée dans la base]**. Les scripts SQL doivent être créés et stockés dans le menu **[!UICONTROL Administration]** / **[!UICONTROL Paramétrage]** / **[!UICONTROL Scripts SQL]**.

   Sinon, saisissez ou effectuez un copier-coller du script SQL dans la zone dédiée.

   ![](assets/sql_datamanagement.png)

   L&#39;activité permet d&#39;utiliser les variables suivantes dans le script :

   * **activity.tableName** : nom SQL de la table de travail sortante.
   * **task.incomingTransitionByName(‘nom’).tableName** : nom SQL de la table de travail associée à la transition entrante à utiliser (la transition est identifiée par son nom).

     >[!NOTE]
     >
     >La valeur (&#39;nom&#39;) correspond au champ **[!UICONTROL Nom]** des propriétés de la transition.

1. Si le script SQL contient déjà des commandes pour créer une table de travail sortante, désélectionnez l&#39;option **[!UICONTROL Créer automatiquement la table de travail]**. Dans le cas contraire, une table de travail est automatiquement créée une fois le workflow exécuté.
1. Cliquez sur **[!UICONTROL OK]** pour valider la configuration de l&#39;activité.

L’activité est désormais configurée. Il est prêt à être exécuté dans le workflow.

>[!CAUTION]
>
>Une fois l’activité exécutée, le nombre d’enregistrements de transition sortante n’est qu’indicatif. Elle peut varier en fonction du niveau de complexité du script SQL.
>  
>Si lactivité est redémarrée, lintégralité du script est exécutée depuis le début, quel que soit le statut dexécution.

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
