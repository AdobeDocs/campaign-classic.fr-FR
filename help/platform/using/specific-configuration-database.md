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
source-git-commit: 959455ec92b40581f04cf0e357b6c0d3f3fba81c
workflow-type: ht
source-wordcount: '1898'
ht-degree: 100%

---


# Configuration des connecteurs FDA {#specific-configurations-by-database-type}

En fonction des bases de données externes auxquelles vous souhaitez pouvoir accéder depuis Adobe Campaign, certains paramétrages spécifiques sont nécessaires. Ces paramétrages concernent essentiellement l’installation de pilotes et la déclarations de variables d’environnement propres à chaque SGBDR sur le serveur Adobe Campaign.

Pour plus d’informations sur les connecteurs hérités tels que Teradata, Hadoop 2.1 ou Netezza, consultez cette [page](../../platform/using/legacy-connectors.md).

En règle générale, il est nécessaire d’installer la couche cliente correspondant à la base de données externe utilisée sur le serveur Adobe Campaign.

>[!NOTE]
>
>Les versions compatibles sont répertoriées dans la [Matrice de compatibilité Campaign](https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix.html#FederatedDataAccessFDA).

## Configurer l’accès à Azure Synapse {#configure-access-to-azure-synapse}

### Compte externe Azure Synapse {#azure-external}

Le compte externe [!DNL Azure] vous permet de connecter l’instance Campaign à la base de données externe Azure Synapse.
Pour créer votre compte externe [!DNL Azure Synapse] :

1. Dans Campaign Classic, configurez votre compte externe [!DNL Azure Synapse]. Dans l’**[!UICONTROL Explorateur]**, cliquez sur **[!UICONTROL Administration]** / **[!UICONTROL Plateforme]** / **[!UICONTROL Comptes externes]**.

1. Cliquez sur **[!UICONTROL Nouveau]**.

1. Sélectionnez **[!UICONTROL Base de données externe]** en tant que **[!UICONTROL Type]** de compte externe.

1. Configurez le compte externe [!DNL Azure Synapse]. Vous devez indiquer les informations suivantes :

   * **[!UICONTROL Type]** : Azure Synapse Analytics

   * **[!UICONTROL Serveur]** : URL du serveur Azure Synapse

   * **[!UICONTROL Compte]** : nom de l’utilisateur

   * **[!UICONTROL Mot de passe]** : mot de passe du compte utilisateur

   * **[!UICONTROL Base de données]** : nom de la base de données

   ![](assets/azure_1.png)

### Azure Synapse sous CentOS {#azure-centos}

**Prérequis:**

* Vous aurez besoin des privilèges racine pour installer un pilote ODBC.
* Les pilotes ODBC Red Hat Enterprise fournis par Microsoft peuvent également être utilisés avec CentOS pour se connecter à SQL Server.
* La version 13.0 fonctionnera avec Red Hat 6 et 7.

Pour configurer Azure Synapse sous CentOS :

1. Installez tout d’abord le pilote ODBC. Vous pouvez le trouver sur cette [page](https://www.microsoft.com/en-us/download/details.aspx?id=50420).

   >[!NOTE]
   >
   >Il s’agit uniquement de la version 13 du pilote ODBC.

   ```
   sudo su
   curl https://packages.microsoft.com/config/rhel/6/prod.repo > /etc/yum.repos.d/mssql-release.repo
   exit
   # Uninstall if already installed Unix ODBC driver
   sudo yum remove unixODBC-utf16 unixODBC-utf16-devel #to avoid conflicts
   
   sudo ACCEPT_EULA=Y yum install msodbcsql
   
   sudo ACCEPT_EULA=Y yum install mssql-tools
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   
   # the Microsoft driver expects unixODBC to be here /usr/lib64/libodbc.so.1, so add soft links to the '.so.2' files
   cd /usr/lib64
   sudo ln -s libodbccr.so.2   libodbccr.so.1
   sudo ln -s libodbcinst.so.2 libodbcinst.so.1
   sudo ln -s libodbc.so.2     libodbc.so.1
   
   # Set the path for unixODBC
   export ODBCINI=/usr/local/etc/odbc.ini
   export ODBCSYSINI=/usr/local/etc
   source ~/.bashrc
   
   #Add a DSN information to /etc/odbc.ini
   sudo vi /etc/odbc.ini
   
   #Add the following:
   [Azure Synapse Analytics]
   Driver      = ODBC Driver 13 for SQL Server
   Description = Azure Synapse Analytics DSN
   Trace       = No
   Server      = [insert your server here]
   ```

1. Si nécessaire, vous pouvez installer les en-têtes de développement unixODBC en exécutant la commande suivante :

   ```
   sudo yum install unixODBC-devel
   ```

1. Après avoir installé les pilotes, vous pouvez tester et vérifier votre pilote ODBC, et interroger votre base de données, si nécessaire. Exécutez la commande suivante :

   ```
   /opt/mssql-tools/bin/sqlcmd -S yourServer -U yourUserName -P yourPassword -q "your query" # for example -q "select 1"
   ```

1. Dans Campaign Classic, vous pouvez ensuite configurer votre compte externe [!DNL Azure Synapse]. Pour plus d’informations sur la configuration de votre compte externe, voir cette [section](../../platform/using/specific-configuration-database.md#azure-external).

1. Comme Azure Synapse Analytics communique par le biais du port TCP 1433, vous devez l’ouvrir sur votre pare-feu. Utilisez la commande suivante :

   ```
   firewall-cmd --permanent --add-rich-rule='rule family="ipv4" source address="[server_ip_here]/32" port port="1433" protocol="tcp" accept'
   # you can ping your hostname and the ping command will translate the hostname to IP address which you can use here
   ```

   >[!NOTE]
   >
   >Pour autoriser la communication du côté d’Azure Synapse Analytics, vous devrez peut-être ajouter votre adresse IP publique à la liste autorisée. Pour ce faire, voir la [documentation Azure](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-firewall-configure#use-the-azure-portal-to-manage-server-level-ip-firewall-rules).

1. Dans le cas des iptables, exécutez la commande suivante :

   ```
   iptables -A OUTPUT -p tcp -d [server_hostname_here] --dport 1433 -j ACCEPT
   ```

### Azure Synapse sous Windows {#azure-windows}

>[!NOTE]
>
>Il s’agit uniquement de la version 13 du pilote ODBC, mais Adobe Campaign Classic peut également utiliser les pilotes SQL Server Native Client 11.0 et 10.0.

Pour configurer Azure Synapse sous Windows :

1. Installez tout d’abord le pilote ODBC Microsoft. Vous pouvez le trouver sur cette [page](https://www.microsoft.com/en-us/download/details.aspx?id=50420).

1. Choisissez les fichiers suivants à installer :

   ```
   your_language\your_architecture\msodbcsql.msi (i.e: English\X64\msodbcsql.msi)
   ```

1. Une fois votre pilote ODBC installé, vous pouvez le tester, si nécessaire. Pour plus d’informations à ce propos, consultez cette [page](https://docs.microsoft.com/en-us/sql/connect/odbc/windows/system-requirements-installation-and-driver-files?view=sql-server-ver15#installing-microsoft-odbc-driver-for-sql-server).

1. Dans Campaign Classic, vous pouvez ensuite configurer votre compte externe [!DNL Azure Synapse]. Pour plus d’informations sur la configuration de votre compte externe, voir cette [section](../../platform/using/specific-configuration-database.md#azure-external).

1. Comme Azure Synapse Analytics communique par le biais du port TCP 1433, vous devez ouvrir ce port sur le pare-feu Windows Defender. Pour plus d’informations à ce propos, consultez la [documentation Windows](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-firewall/create-an-outbound-program-or-service-rule).

### Azure Synapse sous Debian {#azure-debian}

**Prérequis:**

* Vous aurez besoin des privilèges racine pour installer un pilote ODBC.
* Curl est nécessaire pour installer le package msodbcsql. Si vous ne l’avez pas installé, exécutez la commande suivante :

   ```
   sudo apt-get install curl
   ```

Pour configurer Azure Synapse sous Debian :

1. Installez tout d’abord le pilote ODBC Microsoft pour SQL Server. Utilisez les commandes suivantes pour installer le pilote ODBC 13.1 for SQL Server :

   ```
   sudo su
   curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
   curl https://packages.microsoft.com/config/debian/8/prod.list > /etc/apt/sources.list.d/mssql-release.list
   exit
   sudo apt-get update
   sudo ACCEPT_EULA=Y apt-get install msodbcsql
   ```

1. Si vous obtenez l’erreur suivante **« The method driver /usr/lib/apt/methods/https could not be found »** lors de l’appel de la commande **sudo apt-get update**, exécutez la commande :

   ```
   sudo apt-get install apt-transport-https ca-certificates
   ```

1. Vous devez maintenant installer mssql-tools à l’aide des commandes suivantes. Les outils Mssq sont nécessaires pour exploiter l’utilitaire BCP (programme de copie en masse) et pour exécuter des requêtes.

   ```
   sudo ACCEPT_EULA=Y apt-get install mssql-tools
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

1. Si nécessaire, vous pouvez installer les en-têtes de développement unixODBC en exécutant la commande suivante :

   ```
   sudo yum install unixODBC-devel
   ```

1. Après avoir installé les pilotes, vous pouvez tester et vérifier votre pilote ODBC, et interroger votre base de données, si nécessaire. Exécutez la commande suivante :

   ```
   /opt/mssql-tools/bin/sqlcmd -S yourServer -U yourUserName -P yourPassword -q "your query" # for example -q "select 1"
   ```

1. Dans Campaign Classic, vous pouvez maintenant configurer votre compte externe [!DNL Azure Synapse]. Pour plus d’informations sur la configuration de votre compte externe, voir cette [section](../../platform/using/specific-configuration-database.md#azure-external).

1. Pour configurer les iptables sous Debian afin d’assurer la connexion avec Azure Synapse Analytics, activez le port TCP 1433 sortant pour votre hostname à l’aide de la commande suivante :

   ```
   iptables -A OUTPUT -p tcp -d [server_hostname_here] --dport 1433 -j ACCEPT
   ```

   >[!NOTE]
   >
   >Pour autoriser la communication du côté d’Azure Synapse Analytics, vous devrez peut-être ajouter votre adresse IP publique à la liste autorisée. Pour ce faire, voir la [documentation Azure](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-firewall-configure#use-the-azure-portal-to-manage-server-level-ip-firewall-rules).

## Configurer l’accès à Snowflake {#configure-access-to-snowflake}

>[!NOTE]
>
>Le connecteur [!DNL Snowflake] est disponible pour les déploiements hébergés et on-premise. Voir à ce propos [cet article](https://helpx.adobe.com/fr/campaign/kb/acc-on-prem-vs-hosted.html).

![](assets/snowflake_3.png)

### Compte externe Snowflake {#snowflake-external}

Le compte externe [!DNL Snowflake] vous permet de connecter l’instance Campaign à la base de données externe Snowflake.

1. Dans Campaign Classic, configurez votre compte externe [!DNL Snowflake]. Dans l’**[!UICONTROL Explorateur]**, cliquez sur **[!UICONTROL Administration]** / **[!UICONTROL Plateforme]** / **[!UICONTROL Comptes externes]**.

1. Cliquez sur **[!UICONTROL Nouveau]**.

1. Sélectionnez **[!UICONTROL Base de données externe]** en tant que **[!UICONTROL Type]** de compte externe.

1. Pour configurer le compte externe **[!UICONTROL Snowflake]**, vous devez indiquer les informations suivantes :

   * **[!UICONTROL Type]**: [!DNL Snowflake]

   * **[!UICONTROL Serveur]** : URL du serveur [!DNL Snowflake]

   * **[!UICONTROL Compte]** : nom de l’utilisateur

   * **[!UICONTROL Mot de passe]** : mot de passe du compte utilisateur

   * **[!UICONTROL Base de données]** : nom de la base de données

   ![](assets/snowflake.png)

1. Cliquez sur l’onglet **[!UICONTROL Paramètres]**, puis sur le bouton **[!UICONTROL Déployer les fonctions]** pour créer des fonctions.

   ![](assets/snowflake_2.png)

Le connecteur prend en charge les options suivantes :

| Option | Description |
|---|---|
| workschema | Schéma de base de données à utiliser pour les tables de travail. |
| warehouse | Nom de l’entrepôt par défaut à utiliser. Il remplace la valeur par défaut de l’utilisateur. |
| TimeZoneName | Vide par défaut. C’est le fuseau horaire système du serveur applicatif Campaign Classic qui est utilisé. Il est possible d’utiliser cette option pour forcer le paramètre de session TIMEZONE. <br>Pour plus d’informations à ce sujet, consultez [cette page](https://docs.snowflake.net/manuals/sql-reference/parameters.html#timezone). |
| WeekStart | Paramètre de session WEEK_START. Par défaut, cette valeur est définie sur 0. <br>Pour plus d’informations à ce sujet, consultez [cette page](https://docs.snowflake.com/en/sql-reference/parameters.html#week-start). |
| UseCachedResult | Paramètre de session USE_CACHED_RESULTS. Par défaut, cette valeur est définie sur TRUE. Il est possible d’utiliser cette option pour désactiver les résultats de Snowflake mis en mémoire cache. <br>Pour plus d’informations à ce sujet, voir [cette page](https://docs.snowflake.net/manuals/user-guide/querying-persisted-results.html). |

### Snowflake sous CentOS {#snowflake-centos}

1. Téléchargez les pilotes ODBC pour [!DNL Snowflake]. [Cliquez ici](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/snowflake-odbc-2.20.2.x86_64.rpm) pour lancer le téléchargement.
1. Vous devez ensuite installer les pilotes ODBC sur CentOs à l’aide de la commande suivante :

   ```
   rpm -Uvh unixodbc
   rpm -Uvh snowflake-odbc-2.20.2.x86_64.rpm
   ```

1. Après avoir téléchargé et installé les pilotes ODBC, vous devez redémarrer Campaign Classic. Pour cela, exécutez la commande suivante :

   ```
   /etc/init.d/nlserver6 stop
   /etc/init.d/nlserver6 start
   ```

1. Dans Campaign Classic, vous pouvez ensuite configurer votre compte externe [!DNL Snowflake]. Pour plus d’informations sur la configuration de votre compte externe, voir cette [section](../../platform/using/specific-configuration-database.md#snowflake-external).

### Snowflake sous Debian {#snowflake-debian}

1. Téléchargez les pilotes ODBC pour [!DNL Snowflake]. [Cliquez ici](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/index.html) pour lancer le téléchargement.

1. Vous devez ensuite installer les pilotes ODBC sous Debian à l’aide de la commande suivante :

   ```
   apt-get install unixodbc
   apt-get install snowflake-odbc-x.xx.x.x86_64.deb
   ```

1. Après avoir téléchargé et installé les pilotes ODBC, vous devez redémarrer Campaign Classic. Pour cela, exécutez la commande suivante :

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. Dans Campaign Classic, vous pouvez ensuite configurer votre compte externe [!DNL Snowflake]. Pour plus d’informations sur la configuration de votre compte externe, voir cette [section](../../platform/using/specific-configuration-database.md#snowflake-external).

### Snowflake sous Windows {#snowflake-windows}

1. Téléchargez le pilote [ODBC pour Windows](https://docs.snowflake.net/manuals/user-guide/odbc-download.html). Notez la nécessité de disposer de privilèges de niveau administrateur pour installer le pilote. Voir à ce propos [cette page](https://docs.snowflake.net/manuals/user-guide/admin-user-management.html)

1. Configurez le pilote ODBC. Voir à ce propos [cette page](https://docs.snowflake.net/manuals/user-guide/odbc-windows.html#step-2-configure-the-odbc-driver)

1. Dans Campaign Classic, vous pouvez ensuite configurer votre compte externe [!DNL Snowflake]. Pour plus d’informations sur la configuration de votre compte externe, voir cette [section](../../platform/using/specific-configuration-database.md#snowflake-external).

## Configurer l’accès à Hadoop 3.0 {#configure-access-to-hadoop-3}

### Compte externe Hadoop {#hadoop-external}

Le compte externe [!DNL Hadoop] vous permet de connecter votre instance Campaign à votre base de données externe Hadoop.

1. Dans Campaign Classic, configurez votre compte externe [!DNL Hadoop]. Dans l’**[!UICONTROL Explorateur]**, cliquez sur **[!UICONTROL Administration]** / **[!UICONTROL Plateforme]** / **[!UICONTROL Comptes externes]**.

1. Cliquez sur **[!UICONTROL Nouveau]**.

1. Sélectionnez **[!UICONTROL Base de données externe]** en tant que **[!UICONTROL Type]** de compte externe.

1. Pour configuer le compte externe **[!UICONTROL Hadoop]**, vous devez indiquer les informations suivantes :

   * **[!UICONTROL Type]** : ODBC (Sybase ASE, Sybase IQ)

   * **[!UICONTROL Serveur]** : nom du DNS

   * **[!UICONTROL Compte]** : nom de l’utilisateur

   * **[!UICONTROL Mot de passe]** : mot de passe du compte utilisateur

   * **[!UICONTROL Base de données]** : nom de la base de données s’il n’est pas spécifié dans le DSN. Il peut rester vide s’il est spécifié dans le DSN

   * **[!UICONTROL Fuseau horaire]** : fuseau horaire du serveur

   ![](assets/hadoop3.png)

Le connecteur prend en charge les options ODBC suivantes :

| Nom | Valeur |
|---|---|
| ODBCMgr | iODBC |
| warehouse | 1/2/4 |

Le connecteur prend également en charge les options Hive suivantes :

| Nom | Valeur | Description |
|---|---|---|
| bulkKey | Clé d’accès Azure Blob ou DataLake. | Pour les chargeurs en masse wasb:// ou wasbs:// (c.-à-d. si l’outil de chargement en masse a pour préfixe wasb:// ou wasbs://). <br>Il s’agit de la clé d’accès pour le compartiment de blob ou de DataLake servant au chargement en masse. |
| hdfsPort | Numéro de port <br>défini par défaut sur 8020 | Pour le chargement HDFS en masse (c.-à-d. si l’outil de chargement en masse a pour préfixe webhdfs:// ou webhdfss://). |
| bucketsNumber | 20 | Nombre de compartiments lors de la création d’une table regroupée. |
| fileFormat | PARQUET | Format de fichier par défaut pour les tables de travail. |

### Configuration de Hadoop 3.0 {#configuring-hadoop}

La connexion à une base de données externe Hadoop dans FDA requiert les paramétrages suivants sur le serveur Adobe Campaign. Notez que cette configuration est possible pour Windows et Linux.

1. Téléchargez les pilotes ODBC pour Hadoop en fonction de votre version de système d’exploitation. Les pilotes se trouvent dans [cette page](https://www.cloudera.com/downloads.html).

1. Vous devez ensuite installer les pilotes ODBC et créer un DSN pour votre connexion Hive. Les instructions se trouvent dans [cette page](https://docs.cloudera.com/documentation/other/connectors/hive-odbc/2-6-5/Cloudera-ODBC-Driver-for-Apache-Hive-Install-Guide.pdf)

1. Après avoir téléchargé et installé les pilotes ODBC, vous devez redémarrer Campaign Classic. Pour cela, exécutez la commande suivante :

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. Dans Campaign Classic, vous pouvez ensuite configurer votre compte externe [!DNL Hadoop]. Pour plus d’informations sur la configuration de votre compte externe, voir cette [section](../../platform/using/specific-configuration-database.md#hadoop-external).

## Configurer l’accès à Oracle {#configure-access-to-oracle}

### Compte externe Oracle {#oracle-external}

Le compte externe [!DNL Oracle] vous permet de connecter votre instance Campaign à votre base de données externe Hadoop.

1. Dans Campaign Classic, configurez votre compte externe [!DNL oracle]. Dans l’**[!UICONTROL Explorateur]**, cliquez sur **[!UICONTROL Administration]** / **[!UICONTROL Plateforme]** / **[!UICONTROL Comptes externes]**.

1. Cliquez sur **[!UICONTROL Nouveau]**.

1. Sélectionnez **[!UICONTROL Base de données externe]** en tant que **[!UICONTROL Type]** de compte externe.

1. Pour configurer le compte externe **[!UICONTROL Oracle]**, vous devez indiquer les informations suivantes :

   * **[!UICONTROL Type]** : Oracle

   * **[!UICONTROL Serveur]** : nom du DNS

   * **[!UICONTROL Compte]** : nom de l’utilisateur

   * **[!UICONTROL Mot de passe]** : mot de passe du compte utilisateur

   * **[!UICONTROL Fuseau horaire]** : fuseau horaire du serveur

   ![](assets/oracle_config.png)

### Oracle sous Linux {#for-linux-1}

La connexion à une base de données externe Oracle en FDA requiert les paramétrages additionnels ci-dessous sur le serveur Adobe Campaign.

1. Installez le client complet Oracle correspondant à votre version d’Oracle.
1. Ajoutez vos définitions TNS à votre installation. Pour cela, indiquez-les dans un fichier **tnsnames.ora** dans le répertoire /etc/oracle. Si ce répertoire n’existe pas, créez-le.

   Créez alors une nouvelle variable d’environnement TNS_ADMIN : export TNS_ADMIN=/etc/oracle et redémarrez la machine.

1. Intégrez Oracle à votre serveur Adobe Campaign (nlserver). Pour cela, vérifiez que le fichier **customer.sh** est bien présent dans le dossier &quot;nl6&quot; de l’arborescence du serveur Adobe Campaign et que ce dernier comprend bien les liens vers les bibliothèques Oracle.

   Par exemple pour un client 11.2 :

   ```
   export ORACLE_HOME=/usr/lib/oracle/11.2
   export TNS_ADMIN=/etc/oracle
   export LD_LIBRARY_PATH=$ORACLE_HOME/client64/lib:$LD_LIBRARY_PATH
   ```

   >[!NOTE]
   >
   >Ces valeurs (notamment ORACLE_HOME), dépendent de vos répertoires d’installation. Vérifiez bien votre arborescence avant de référencer ces valeurs.

1. Installez les librairies nécessaires à Oracle :

   * **libclntsh.so**

      ```
      cd /usr/lib/oracle/<version>/client<architecture>/lib
      ln -s libclntsh.so.<version> libclntsh.so
      ```

   * **libaio1**

      ```
      aptitude install libaio1
      or
      yum install libaio1
      ```

1. Dans Campaign Classic, vous pouvez ensuite configurer votre compte externe [!DNL Oracle]. Pour plus d’informations sur la configuration de votre compte externe, voir cette [section](../../platform/using/specific-configuration-database.md#oracle-external).

### Oracle sous Windows {#for-windows-1}

La connexion à une base de données externe Oracle en FDA requiert les paramétrages additionnels ci-dessous sur le serveur Adobe Campaign.

1. Installez le client Oracle.

1. Dans le dossier C:Oracle, créez un fichier **tnsnames.ora** contenant vos définitions TNS.

1. Ajoutez une variable d’environnement TNS_ADMIN avec pour valeur C:Oracle et redémarrez la machine.

1. Dans Campaign Classic, vous pouvez ensuite configurer votre compte externe [!DNL Oracle]. Pour plus d’informations sur la configuration de votre compte externe, voir cette [section](../../platform/using/specific-configuration-database.md#oracle-external).