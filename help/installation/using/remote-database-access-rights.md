---
product: campaign
title: Autorisations d’accès à une base de données externe
description: Autorisations d’accès aux bases de données externes
feature: Installation, Instance Settings, Federated Data Access
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 3d43010e-53f8-4aa2-a651-c422a02191fe
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '993'
ht-degree: 100%

---

# Droits d&#39;accès à la base externe {#remote-database-access-rights}



Tout d&#39;abord, afin qu&#39;un utilisateur puisse effectuer des opérations sur une base externe via FDA, ce dernier doit disposer d&#39;un droit nommé spécifique dans Adobe Campaign.

1. Sélectionnez le noeud **[!UICONTROL Administration > Gestion des accès > Droits nommés]** de l&#39;explorateur Adobe Campaign.
1. Créez un nouveau droit en indiquant le libellé de votre choix.
1. Le champ **[!UICONTROL Nom]** doit être de la forme suivante : **user:base@server**, où :

   * **user** correspond au nom de l&#39;utilisateur sur la base de données externe.
   * **base** correspond au nom de la base de données externe.
   * **server** correspond au nom du serveur de la base de données externe.

     >[!NOTE]
     >
     >La partie **:base** est optionnelle sur Oracle.

1. Enregistrez le droit nommé puis associez-le à l&#39;utilisateur de votre choix à partir du noeud **[!UICONTROL Administration > Gestion des accès > Opérateurs]** de l&#39;explorateur Adobe Campaign.

Ensuite, pour exploiter les données contenues dans une base externe, l&#39;utilisateur Adobe Campaign doit au minimum avoir les droits en &#39;Ecriture&#39; sur cette base, afin de permettre la création des tables de travail. Ces tables sont automatiquement supprimées par Adobe Campaign.

En règle générale, les droits d&#39;accès suivants sont nécessaires :

* **CONNECT** : connexion à la base distante,
* **READ Data** : accès en lecture aux tables contenant les données du client,
* **READ &#39;MetaData&#39;** : accès aux catalogues de données du serveur afin d&#39;obtenir la structure des tables,
* **LOAD** : chargement en masse dans des tables de travail (opération nécessaire lorsque l&#39;on travaille sur des collections et des jointures),
* **CREATE/DROP** pour **TABLE/INDEX/PROCEDURE/FUNCTION** (uniquement pour les tables de travail générées par Adobe Campaign),
* **EXPLAIN** (recommandé) : pour la surveillance des performances en cas de problème,
* **WRITE Data** (selon le scénario d&#39;intégration).

L’administrateur de la base de données doit mettre en correspondance ces droits avec les droits spécifiques à chaque moteur de base de données. Pour en savoir plus, voir la section ci-dessous.

## Droits FDA {#fda-rights}

|   | Snowflake | Redshift | Oracle | SQLServer | PostgreSQL | MySQL |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **Connexion à une base de données distante** | Privilèges USAGE ON WAREHOUSE, USAGE ON DATABASE et USAGE ON SCHEMA | Création d’un utilisateur lié au compte AWS | Privilège CREATE SESSION | Autorisation CONNECT | Privilège CONNECT | Création d’un utilisateur lié à un hôte distant possédant tous les privilèges (ALL PRIVILEGES) |
| **Création de tables** | Privilège CREATE TABLE ON SCHEMA  | Privilège CREATE | Privilège CREATE TABLE | Autorisation CREATE TABLE | Privilège CREATE | Privilège CREATE |
| **Création d&#39;index** | N/A | Privilège CREATE | Privilège INDEX ou CREATE ANY INDEX | Autorisation ALTER  | Privilège CREATE | Privilège INDEX |
| **Création de fonctions** | Privilège CREATE FUNCTION ON SCHEMA | Privilège USAGE ON LANGUAGE plpythonu pour pouvoir appeler des scripts Python externes | Privilège CREATE PROCEDURE ou CREATE ANY PROCEDURE | Autorisation CREATE FUNCTION | Privilège USAGE | Privilège CREATE ROUTINE |
| **Création de procédures** | N/A | Privilège USAGE ON LANGUAGE plpythonu pour pouvoir appeler des scripts Python externes | Privilège CREATE PROCEDURE ou CREATE ANY PROCEDURE | Autorisation CREATE PROCEDURE | Privilège USAGE (les procédures sont des fonctions) | Privilège CREATE ROUTINE |
| **Suppression d’objets (tables, index, fonctions, procédures)** | Propriété de l&#39;objet | Être propriétaire de l’objet ou être un super-utilisateur | Privilège DROP ANY &lt; objet >  | Autorisation ALTER | Table : propriété de la table Index : propriété de l’index Fonction : propriété de la fonction | Privilège DROP |
| **Surveillance des exécutions** | Privilège MONITOR sur l&#39;objet requis | Aucun privilège requis pour utiliser la commande EXPLAIN | Privilèges INSERT et SELECT et privilège nécessaire pour exécuter l’instruction sur laquelle repose la séquence des opérations EXPLAIN PLAN | Autorisation SHOWPLAN | Aucun privilège requis pour utiliser l’instruction EXPLAIN | Privilège SELECT |
| **Écriture de données** | Privilèges INSERT et/ou UPDATE (selon l&#39;opération d&#39;écriture) | Privilèges INSERT et UPDATE | Privilèges INSERT et UPDATE ou INSERT et UPDATE ANY TABLE | Autorisations INSERT et UPDATE | Privilèges INSERT et UPDATE | Privilèges INSERT et UPDATE |
| **Chargement de données dans des tables** | Privilèges CREATE STAGE ON SCHEMA, SELECT et INSERT sur la table ciblée | Privilèges SELECT et INSERT | Privilèges SELECT et INSERT | Autorisations INSERT, ADMINISTER BULK OPERATIONS et ALTER TABLE | Privilèges SELECT et INSERT | Privilège FILE |
| **Accès aux données clientes** | Privilège(s) SELECT sur (FUTURE) TABLE(S) ou VIEW(S) | Privilège SELECT | Privilège SELECT ou SELECT ANY TABLE | Autorisation SELECT | Privilège SELECT | Privilège SELECT |
| **Accès aux métadonnées** | Privilège SELECT sur INFORMATION_SCHEMA SCHEMA | Privilège SELECT | Aucun privilège requis pour utiliser l’instruction DESCRIBE | Autorisation VIEW DEFINITION | Aucun privilège requis pour utiliser la commande &quot;\d table&quot; | Privilège SELECT |

|   | DB2 UDB | TeraData | InfiniDB | Sybase IQ / Sybase ASE | Netezza | AsterData |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **Connexion à une base de données distante** | Autorité CONNECT | Privilège CONNECT | Création d’un utilisateur lié à un hôte distant possédant tous les privilèges (ALL PRIVILEGES) | Aucune autorisation requise pour utiliser l’instruction CONNECT | Aucun privilège requis | Privilège CONNECT |
| **Création de tables** | Autorité CREATETAB | Mot-clé CREATE TABLE ou TABLE | Privilège CREATE | Autorité RESOURCE et autorisation CREATE | Privilège TABLE | Privilège CREATE |
| **Création d’index** | Privilège INDEX | Mot-clé CREATE INDEX ou INDEX | Privilège INDEX | Autorité RESOURCE et autorisation CREATE | Privilège INDEX | Privilège CREATE |
| **Création de fonctions** | Autorité IMPLICIT_SCHEMA ou privilège CREATEIN | Mot-clé CREATE FUNCTION ou FUNCTION | Privilège CREATE ROUTINE | Autorité RESOURCE ou autorité DBA pour les fonctions Java | Privilège FUNCTION | Privilège CREATE FUNCTION |
| **Création de procédures** | Autorité IMPLICIT_SCHEMA ou privilège CREATEIN | Mot-clé CREATE PROCEDURE ou PROCEDURE | Privilège CREATE ROUTINE | Autorité RESOURCE | Privilège PROCEDURE | Privilège CREATE FUNCTION |
| **Suppression d’objets (tables, index, fonctions, procédures)** | Privilège DROPIN ou privilège CONTROL ou propriété de l’objet | DROP &lt; objet > ou mot-clé associé à l’objet | Privilège DROP | Propriété de l’objet ou autorité DBA | Privilège DROP | Propriété de l’objet |
| **Surveillance des exécutions** | Autorité EXPLAIN | Aucun privilège requis pour utiliser l’instruction EXPLAIN | Privilège SELECT | Seul un administrateur système peut exécuter sp_showplan | Aucun privilège requis pour utiliser l’instruction EXPLAIN | Aucun privilège requis pour utiliser l’instruction EXPLAIN |
| **Écriture de données** | Privilèges INSERT et UPDATE ou autorité DATAACCESS | Privilèges INSERT et UPDATE | Privilèges INSERT et UPDATE | Autorisations INSERT et UPDATE | Privilèges INSERT et UPDATE | Privilèges INSERT et UPDATE |
| **Chargement de données dans des tables** | Autorité LOAD | Privilèges SELECT et INSERT pour utiliser respectivement les instructions COPY TO et COPY FROM | Privilège FILE | Être propriétaire de la table ou autorisation ALTER. Selon l’option -gl, LOAD TABLE ne peut être exécutée que si l’utilisateur dispose de l’autorité DBA | Privilèges SELECT et INSERT | Privilèges SELECT et INSERT |
| **Accès aux données clientes** | Privilèges INSERT/UPDATE ou autorité DATAACCESS | Privilège SELECT | Privilège SELECT | Autorisation SELECT | Privilège SELECT | Privilège SELECT |
| **Accès aux métadonnées** | Aucune autorisation requise pour utiliser l’instruction DESCRIBE | Privilège SHOW | Privilège SELECT | Aucune autorisation requise pour utiliser l’instruction DESCRIBE | Aucun privilège requis pour utiliser la commande &quot;\d table&quot; | Aucun privilège requis pour utiliser la commande SHOW |
