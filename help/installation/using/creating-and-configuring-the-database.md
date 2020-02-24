---
title: Création et paramétrage de la base de données
seo-title: Création et paramétrage de la base de données
description: Création et paramétrage de la base de données
seo-description: null
page-status-flag: never-activated
uuid: e5143d55-61fa-416a-80db-c29a0caf9a3e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: initial-configuration
discoiquuid: 7dd8a6a5-7cca-4e92-8226-1b9e450dfaf9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 4869eb41f942a89c48bc213913c44b70ae777bfc

---


# Création et paramétrage de la base de données{#creating-and-configuring-the-database}

Lors de la création de la base de données, Adobe Campaign propose deux options distinctes :

1. Création ou recyclage d’une base de données : choisissez cette option si vous souhaitez créer une nouvelle base de données ou réutiliser une base existante. Reportez-vous au [cas 1 : Création/recyclage d’une base de données](#case-1--creating-recycling-a-database).
1. Utilisation d’une base de données existante : choisissez cette option si une base de données vide a déjà été créée par votre administrateur et que vous souhaitez l&#39;utiliser ; ou pour étendre la structure d&#39;une base de données existante. Reportez-vous au [deuxième cas : Utilisation d’une base de données](#case-2--using-an-existing-database)existante.

Les étapes de paramétrage sont présentés ci-après.

>[!CAUTION]
>
>Les noms de la base de données, des utilisateurs ou des schémas ne doivent pas commencer par un chiffre, ni utiliser de caractères spéciaux.
>
>Seul l’identifiant **interne** peut effectuer ces opérations. For more on this, refer to [Internal identifier](../../installation/using/campaign-server-configuration.md#internal-identifier).

## 1er cas : créer/recycler une base {#case-1--creating-recycling-a-database}

Les étapes pour créer une base de données ou recycler une base existante sont présentées ci-après. Certains paramétrages dépendent du moteur de base de données utilisé.

Ces étapes sont les suivantes :

* [Etape 1 - Sélection du moteur de base de données](#step-1---selecting-the-database-engine),
* [Etape 2 - Connexion au serveur](#step-2---connecting-to-the-server),
* [Etape 3 - Connexion et caractéristiques de la base de données](#step-3---connection-and-characteristics-of-the-database),
* [Etape 4 - Packages à installer](#step-4---packages-to-install),
* [Etape 5 - Etapes de la création](#step-5---creation-steps),
* [Etape 6 - Lancement de la création de la base](#step-6---creating-the-database).

### Etape 1 - Sélection du moteur de base de données {#step-1---selecting-the-database-engine}

Sélectionnez le moteur de base de données parmi ceux proposés dans la liste déroulante.

![](assets/s_ncs_install_db_select_engine.png)

Les bases de données prises en charge sont présentées dans la section [Matrice de compatibilité](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html).

Identifiez le serveur et sélectionnez le type d&#39;opération à réaliser. Ici : **[!UICONTROL Créer ou recycler une base de données]**.

![](assets/s_ncs_install_db_oracle_creation01.png)

Selon le moteur de base sélectionné, les informations d&#39;identification du serveur diffèrent.

* Pour un moteur **Oracle**, renseignez le **nom TNS** qui a été défini sur le serveur applicatif.
* Pour un moteur **PostgreSQL** ou **DB2**, indiquez le nom DNS (ou l&#39;adresse IP) défini sur le serveur applicatif pour accéder au serveur de base de données.
* Pour un moteur **Microsoft SQL Server**, vous devez définir :

   1. the DNS name (or IP address) defined on the application server to access the database server: **DNS** or **DNS\`<instance>`**(instance mode),
   1. le mécanisme d’identification pour l’accès à Microsoft SQL Server : **[!UICONTROL Authentification SQL Server]** ou **[!UICONTROL Authentification Windows NT]**.

      ![](assets/s_ncs_install_db_mssql_creation01.png)

### Etape 2 - Connexion au serveur {#step-2---connecting-to-the-server}

Dans la fenêtre **[!UICONTROL Accès au serveur]**, définissez les paramètres de connexion au serveur de la base de données.

![](assets/s_ncs_install_db_oracle_creation02.png)

Pour cela, saisissez le nom et le mot de passe d&#39;un **compte système d&#39;administration** qui possède les permissions nécessaires pour créer des bases, soit :

* **system** pour une base Oracle,
* **sa** pour une base Microsoft SQL Server,
* **postgres** pour une base PostgreSQL,
* **db2inst1** pour une base DB2.

### Etape 3 - Connexion et caractéristiques de la base de données {#step-3---connection-and-characteristics-of-the-database}

L&#39;étape suivante permet de configurer les paramètres de connexion à la base de données.

![](assets/s_ncs_install_db_oracle_creation03.png)

Vous devez définir les paramètres suivants :

* Indiquez le nom de la base de données à créer.

   >[!NOTE]
   >
   >Pour une base DB2, nom de la base ne doit pas excéder 8 caractères.

* Saisissez le mot de passe du compte associé à cette base.
* Indiquez si la base doit être Unicode ou non.

   L&#39;option **[!UICONTROL Base Unicode]** permet de stocker tous les types de caractères en Unicode, quelle que soit la langue.

   >[!NOTE]
   >
   >Pour une base Oracle, l&#39;option **[!UICONTROL Stockage Unicode]** permet d&#39;utiliser des champs de type **NCLOB**, **NVARCHAR**, etc.
   > 
   >Si vous ne sélectionnez pas cette option, le jeu de caractères (charset) de la base Oracle doit permettre le stockage des données dans toutes les langues (AL32UTF8 est recommandé).

* Choisissez le fuseau horaire de la base de données et indiquez éventuellement si la base doit être en UTC, lorsque cette option est disponible.

   Pour plus d’informations, reportez-vous à la section Gestion des [fuseaux](../../installation/using/time-zone-management.md)horaires.

### Etape 4 - Packages à installer {#step-4---packages-to-install}

Sélectionnez les packages que vous souhaitez installer.

Consultez votre accord de licence afin de vérifier les options et solutions que vous avez acquises, par exemple &quot;Interaction&quot; ou &quot;Social Marketing&quot;.

![](assets/s_ncs_install_modules.png)

### Etape 5 - Etapes de la création {#step-5---creation-steps}

La fenêtre **[!UICONTROL Etapes de la création]** offre notamment la possibilité de vérifier et éditer le script SQL utilisé pour créer les tables.

![](assets/s_ncs_install_db_oracle_creation04.png)

* Pour une base Oracle, Microsoft SQL Server ou PostgreSQL, l&#39;administrateur de bases de données peut par ailleurs déterminer ici des **paramètres de stockage** à utiliser lors de la création des objets base de données.

   Ces paramètres recoivent les noms exacts (attention à la casse) des tablespaces. Ils sont stockés dans le noeud **[!UICONTROL Administration > Platform > Options]** respectivement dans les options suivantes :

   * **WdbcOptions_TableSpaceUser**: tables utilisateur basées sur un schéma
   * **WdbcOptions_TableSpaceIndex**: index des tables utilisateur basées sur un schéma
   * **WdbcOptions_TableSpaceWork**: tables de travail sans schéma
   * **WdbcOptions_TableSpaceWorkIndex**: index des tables de travail sans schéma

* Pour une base Oracle, l&#39;utilisateur Adobe Campaign doit avoir accès aux librairies Oracle, typiquement en étant membre du groupe **oinstall**.
* L&#39;option **[!UICONTROL Fixer ou changer le mot de passe administrateur]** permet de renseigner le mot de passe associé à l&#39;opérateur Adobe Campaign ayant les droits administrateur.

   Il est vivement recommandé de définir le mot de passe du compte administrateur Adobe Campaign afin de ne pas créer de faille de sécurité.

### Etape 6 - Lancement de la création de la base {#step-6---creating-the-database}

La dernière étape de l&#39;assistant permet de lancer la création de la base de données. Pour cela, cliquez sur le bouton **[!UICONTROL Démarrer]**.

![](assets/s_ncs_install_db_oracle_creation06.png)

Une fois la création de la base de données terminée, vous pourrez vous reconnecter afin de finaliser le paramétrage de l&#39;instance.

Vous devez maintenant démarrer l’assistant de déploiement pour terminer la configuration de l’instance. Reportez-vous à [l’assistant](../../installation/using/deploying-an-instance.md#deployment-wizard)de déploiement.

The connection settings for the database linked to the instance are stored in the file **`/conf/config-<instance>.xml`** found in the Adobe Campaign installation directory.

Exemple de configuration Microsoft SQL Server sur la base base61 associée au compte « campaign » avec son mot de passe crypté :

```
<dbcnx encrypted="1" login="campaign:myBase" password="myPassword" provider="DB" server="dbServer"/>
```

## 2e cas : utiliser une base existante {#case-2--using-an-existing-database}

La base de données, ainsi que l&#39;utilisateur doivent avoir été créés par l&#39;administrateur de base de données et les droits d&#39;accès correctement configurés.

Par exemple, pour une base Oracle, les droits minimum requis sont : GRANT CONNECT, RESOURCE et UNLIMITED TABLESPACE.

Pour utiliser une base existante, les étapes de configuration sont les suivantes :

* [Etape 1 - Choix du moteur de base de données](#step-1---choosing-the-database-engine),
* [Etape 2 - Paramètres de connexion à la base de données](#step-2---database-connection-settings),
* [Etape 3 - Packages à installer](#step-3---packages-to-install),
* [Etape 4 - Etapes de la création](#step-4---creation-steps),
* [Etape 5 - Lancement de la création de la base](#step-5---creating-the-database).

### Etape 1 - Choix du moteur de base de données {#step-1---choosing-the-database-engine}

Sélectionnez le moteur de base de données parmi ceux proposés dans la liste déroulante.

![](assets/s_ncs_install_db_select_engine.png)

Identifiez le serveur et sélectionnez le type d&#39;opération à réaliser. Ici : **[!UICONTROL Utiliser une base de données existante]**.

![](assets/s_ncs_install_db_oracle_exists_01.png)

Selon le moteur de base sélectionné, les informations d&#39;identification du serveur diffèrent.

* Pour un moteur **Oracle**, renseignez le **nom TNS** qui a été défini sur le serveur applicatif.
* Pour un moteur **PostgreSQL** ou **DB2**, indiquez le nom DNS (ou l&#39;adresse IP) défini sur le serveur applicatif pour accéder au serveur de base de données.
* Pour un moteur **Microsoft SQL Server**, vous devez définir :

   1. le nom DNS (ou l&#39;adresse IP) défini sur le serveur applicatif pour accéder au serveur de base de données,
   1. le mode de sécurité pour l’accès à Microsoft SQL Server : **[!UICONTROL Authentification SQL Server]** ou **[!UICONTROL Authentification Windows NT]**.

      ![](assets/s_ncs_install_db_mssql_exists_01.png)

### Etape 2 - Paramètres de connexion à la base de données {#step-2---database-connection-settings}

Dans la fenêtre **[!UICONTROL Base de données]**, définissez les paramètres de connexion à la base de données.

![](assets/s_ncs_install_db_oracle_exists_02.png)

Vous devez définir les paramètres suivants :

* Saisissez le nom de la base de données à utiliser,
* Saisissez le nom et le mot de passe du compte associé à cette base,

   >[!NOTE]
   >
   >Pour une base Oracle, il n&#39;est pas nécessaire de saisir le nom du compte.

* Indiquez si la base doit être Unicode ou non.

### Etape 3 - Packages à installer {#step-3---packages-to-install}

Sélectionnez les packages que vous souhaitez installer.

Consultez votre accord de licence afin de vérifier les options et solutions que vous avez acquises, par exemple l&#39;option &quot;Gestion de contenu&quot; ou la solution &quot;Gestion des ressources marketing&quot;.

![](assets/s_ncs_install_modules.png)

### Etape 4 - Etapes de la création {#step-4---creation-steps}

La fenêtre **[!UICONTROL Etapes de la création]** offre notamment la possibilité de vérifier et éditer le script SQL utilisé pour créer les tables.

![](assets/s_ncs_install_db_oracle_creation04.png)

* Pour une base Oracle, Microsoft SQL Server, PostgreSQL, l&#39;administrateur de bases de données peut par ailleurs déterminer ici des **paramètres de stockage** à utiliser lors de la création des objets base de données.
* Pour une base Oracle, l&#39;utilisateur Adobe Campaign doit avoir accès aux librairies Oracle, typiquement en étant membre du groupe **oinstall**.
* L&#39;option **[!UICONTROL Fixer ou changer le mot de passe administrateur]** permet de renseigner le mot de passe associé à l&#39;opérateur Adobe Campaign ayant les droits administrateur.

   Il est vivement recommandé de définir le mot de passe du compte administrateur Adobe Campaign afin de ne pas créer de faille de sécurité.

### Etape 5 - Lancement de la création de la base {#step-5---creating-the-database}

La dernière étape de l&#39;assistant permet de lancer la création de la base de données. Pour cela, cliquez sur le bouton **[!UICONTROL Démarrer]**.

![](assets/s_ncs_install_db_oracle_creation06.png)

Une fois la création de la base de données terminée, vous pourrez vous reconnecter afin de finaliser le paramétrage de l&#39;instance.

Vous devez maintenant démarrer l’assistant de déploiement pour terminer la configuration de l’instance. Reportez-vous à [l’assistant](../../installation/using/deploying-an-instance.md#deployment-wizard)de déploiement.

The connection settings for the database linked to the instance are stored in the file **`/conf/config-<instance>.xml`** found in the Adobe Campaign installation directory.

Exemple de configuration Microsoft SQL Server sur la base base61 associée au compte « campaign » avec son mot de passe crypté :

```
<dbcnx encrypted="1" login="campaign:myBase" password="myPassword" provider="DB" server="dbServer"/>
```

