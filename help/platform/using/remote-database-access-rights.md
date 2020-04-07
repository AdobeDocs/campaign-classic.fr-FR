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
translation-type: tm+mt
source-git-commit: 6143f23e05f4528a9d76aece3a6e41165e2f95d4

---


# Droits d&#39;accès à la base externe {#remote-database-access-rights}

Tout d&#39;abord, afin qu&#39;un utilisateur puisse effectuer des opérations sur une base externe via FDA, ce dernier doit disposer d&#39;un droit nommé spécifique dans Adobe Campaign.

1. Sélectionnez le **[!UICONTROL Administration > Access Management > Named Rights]** noeud dans l’explorateur de Adobe Campaign .
1. Créez un nouveau droit en indiquant le libellé de votre choix.
1. The **[!UICONTROL Name]** field must take the following format **user:base@server**, where :

   * **user** correspond au nom de l&#39;utilisateur sur la base de données externe.
   * **base** correspond au nom de la base de données externe.
   * **server** correspond au nom du serveur de la base de données externe.

      >[!NOTE]
      >
      >La partie **:base** est optionnelle sur Oracle.

1. Save the named right then link it to your chosen user from the **[!UICONTROL Administration > Access Management > Operators]** node of the Adobe Campaign explorer.

Ensuite, pour exploiter les données contenues dans une base externe, l&#39;utilisateur Adobe Campaign doit au minimum avoir les droits en &#39;Ecriture&#39; sur cette base, afin de permettre la création des tables de travail. Ces tables sont automatiquement supprimées par Adobe Campaign.

En règle générale, les droits d&#39;accès suivants sont nécessaires :

* **CONNECT** : connexion à la base distante,
* **READ Data** : accès en lecture aux tables contenant les données du client,
* **READ &#39;MetaData&#39;** : accès aux catalogues de données du serveur afin d&#39;obtenir la structure des tables,
* **LOAD** : chargement en masse dans des tables de travail (opération nécessaire lorsque l&#39;on travaille sur des collections et des jointures),
* **CREATE/DROP** for **TABLE/INDEX/PROCEDURE/FONCTION** (uniquement pour les tables de travail générées par  Adobe Campaign),
* **EXPLAIN** (recommandé) : pour le suivi des performances en cas de problème,
* **WRITE Data** (selon le scénario d&#39;intégration).

L’administrateur de la base de données doit faire correspondre ces droits aux droits spécifiques à chaque moteur de base de données. Pour plus d&#39;informations, consultez la section ci-dessous.

## Droits {#fda-rights}

|   | Snowflake | Redshift | Oracle | SQLServer | PostgreSQL | MySQL |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **Connexion à une base de données distante** | UTILISATION SUR L’ENTREPÔT, UTILISATION SUR LA BASE DE DONNÉES ET UTILISATION SUR LES privilèges  | Création d’un utilisateur lié au compte AWS | Privilège CREATE SESSION | Autorisation CONNECT | Privilège CONNECT | Création d’un utilisateur lié à un hôte distant avec TOUS LES PRIVILÈGES |
| **Création de tableaux** | Privilège CREATE TABLE ON  | Privilège CREATE | Privilège CREATE TABLE | autorisation CREATE TABLE | Privilège CREATE | Privilège CREATE |
| **Création d&#39;index** | N/A | Privilège CREATE | privilège INDEX ou CREATE ANY INDEX | ALTER l’autorisation | Privilège CREATE | Privilège INDEX |
| **Création de fonctions** | Privilège CRÉER UNE FONCTION SUR  | UTILISATION SUR le jeu de langage privilège de pouvoir appeler des scripts python externes | CRÉER UNE PROCÉDURE ou CRÉER UN DROIT DE PROCÉDURE | autorisation CREATE FONCTION | Privilège USAGE | Privilège CREATE ROUTINE |
| **Création de procédures** | N/A | UTILISATION SUR le jeu de langage privilège de pouvoir appeler des scripts python externes | CRÉER UNE PROCÉDURE ou CRÉER UN DROIT DE PROCÉDURE | Autorisation CREATE PROCEDURE | Privilège USAGE (les procédures sont des fonctions) | Privilège CREATE ROUTINE |
| **Suppression d’objets (tables, index, fonctions, procédures)** | Propriété de l’objet | Posséder l’objet ou être un super-utilisateur | DROP ANY &lt; object > privilège | ALTER l’autorisation | Tableau : propriétaire du tableau Index : propriété de la fonction d’index : propriété de la fonction | Privilège DROP |
| **Surveillance des exécutions** | Privilège MONITOR sur l&#39;objet requis | Aucun privilège requis pour utiliser la commande EXPLAIN | INSÉRER et SÉLECTIONNER le privilège et le privilège nécessaire pour exécuter l&#39;instruction sur laquelle repose le PLAN EXPLICATIF | Autorisation SHOWPLAN | Aucun privilège requis pour l&#39;utilisation de l&#39;instruction EXPLAIN | Privilège SELECT |
| **Ecriture de données** | Privilèges INSERT et/ou UPDATE (selon l’opération d’écriture) | Privilèges INSERT et UPDATE | INSERTION, MISE À JOUR, INSERTION ET MISE À JOUR DES DROITS DE TOUT TABLEAU | Autorisations INSERT et UPDATE | Privilèges INSERT et UPDATE | Privilèges INSERT et UPDATE |
| **Chargement de données dans des tableaux** | CRÉER UNE ÉTAPE SUR , SÉLECTIONNER et INSÉRER sur les privilèges de la table  | Privilèges SELECT et INSERT | Privilèges SELECT et INSERT | INSÉRER, ADMINISTRER LES OPÉRATIONS EN BLOC ET MODIFIER LES AUTORISATIONS DE TABLEAU | Privilèges SELECT et INSERT | privilège FICHIER |
| **Accès aux données clientes** | SÉLECTIONNER sur (FUTURE) TABLE(S) ou (S) privilège(s) | Privilège SELECT | SÉLECTIONNEZ OU SÉLECTIONNEZ N’IMPORTE QUELLE TABLE, privilège | Autorisation SELECT | Privilège SELECT | Privilège SELECT |
| **Accès aux métadonnées** | SÉLECTIONNEZ sur le privilège de INFORMATION_ | Privilège SELECT | Aucun privilège requis pour l’utilisation de l’instruction DESCRIBE |  d&#39;autorisation de définition de la | Aucun privilège requis pour utiliser la commande &quot;\d table&quot; | Privilège SELECT |

|   | DB2 UDB | TeraData | InfiniDB | Sybase IQ / Sybase ASE | Netezza | Groenland | AsterData |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **Connexion à une base de données distante** | Autorité CONNECT | Privilège CONNECT | Création d’un utilisateur lié à un hôte distant avec TOUS LES PRIVILÈGES | Aucune autorisation requise pour utiliser l&#39;instruction CONNECT | Aucun privilège requis | Privilège CONNECT | Privilège CONNECT |
| **Création de tableaux** | Autorité CREATETAB | mot-clé CREATE TABLE ou TABLE | Privilège CREATE | autorisation RESOURCE et autorisation CREATE | Privilège TABLE | Privilège CREATE | Privilège CREATE |
| **Création d&#39;index** | Privilège INDEX | mot-clé CREATE INDEX ou INDEX | Privilège INDEX | autorisation RESOURCE et autorisation CREATE | Privilège INDEX | Privilège CREATE | Privilège CREATE |
| **Création de fonctions** | IMPLICIT_ autorité ou privilège CREATEIN | mot-clé CREATE FUNCTION ou FUNCTION | Privilège CREATE ROUTINE | Autorité RESOURCE ou autorité DBA pour les fonctions Java | Privilège FONCTION | Privilège USAGE | Privilège CREATE FUNCTION |
| **Création de procédures** | IMPLICIT_ autorité ou privilège CREATEIN | mot-clé CREATE PROCEDURE ou PROCEDURE | Privilège CREATE ROUTINE | Autorité de RESSOURCE | Privilège PROCEDURE | Privilège USAGE | Privilège CREATE FUNCTION |
| **Suppression d’objets (tables, index, fonctions, procédures)** | privilège DROPIN ou privilège CONTROL ou propriétaire de l’objet | DROP &lt; objet > ou mot-clé associé à l’objet | Privilège DROP | Propriété de l’objet ou de l’autorité DBA | Privilège DROP | Propriété de l’objet | Propriété de l’objet |
| **Surveillance des exécutions** | EXPLIQUER l&#39;autorité | Aucun privilège requis pour l&#39;utilisation de l&#39;instruction EXPLAIN | Privilège SELECT | Seul un administrateur système peut exécuter sp_showplan | Aucun privilège requis pour l&#39;utilisation de l&#39;instruction EXPLAIN | Aucun privilège requis pour l&#39;utilisation de l&#39;instruction EXPLAIN | Aucun privilège requis pour l&#39;utilisation de l&#39;instruction EXPLAIN |
| **Ecriture de données** | Privilèges INSERTION et MISE À JOUR ou autorité DATAACCESS | Privilèges INSERT et UPDATE | Privilèges INSERT et UPDATE | Autorisations INSERT et UPDATE | Privilèges INSERT et UPDATE | Privilèges INSERT et UPDATE | Privilèges INSERT et UPDATE |
| **Chargement de données dans des tableaux** | Autorité de chargement | Les privilèges SELECT et INSERT pour utiliser respectivement les instructions COPY TO et COPY FROM | privilège FICHIER | Soyez le propriétaire de la table ou de l’autorisation ALTER. Selon l’option -gl, LOAD TABLE ne peut être exécuté que si l’utilisateur dispose de l’autorité DBA | Privilèges SELECT et INSERT | Privilèges SELECT et INSERT | Privilèges SELECT et INSERT |
| **Accès aux données clientes** | Privilèges INSERT/UPDATE ou autorité DATAACCESS | Privilège SELECT | Privilège SELECT | Autorisation SELECT | Privilège SELECT | Privilège SELECT | Privilège SELECT |
| **Accès aux métadonnées** | Aucune autorisation requise pour utiliser l’instruction DESCRIBE | SHOW, privilège | Privilège SELECT | Aucune autorisation requise pour utiliser l’instruction DESCRIBE | Aucun privilège requis pour utiliser la commande &quot;\d table&quot; | Aucun privilège requis pour utiliser la commande &quot;\d table&quot; | Aucun privilège requis pour l’utilisation de la commande SHOW |