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
source-git-commit: fecfff477b0750782c87c017a15e306acac4c61d
workflow-type: tm+mt
source-wordcount: '2967'
ht-degree: 98%

---


# Configurations spécifiques par type de base de données {#specific-configurations-by-database-type}

En fonction des bases de données externes auxquelles vous souhaitez pouvoir accéder depuis Adobe Campaign, certains paramétrages spécifiques sont nécessaires. Ces paramétrages concernent essentiellement l&#39;installation de pilotes et la déclarations de variables d&#39;environnement propres à chaque SGBDR sur le serveur Adobe Campaign.

En règle générale, il est nécessaire d&#39;installer la couche cliente correspondant à la base externe utilisée sur le serveur Adobe Campaign.

>[!NOTE]
>
>Les versions compatibles sont répertoriées dans la [Matrice de compatibilité Campaign](https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix.html#FederatedDataAccessFDA).

## Configurer l’accès à Azure Synapse {#configure-access-to-azure-synapse}

### Compte externe Azure Synapse {#azure-external}

Le compte externe [!DNL Azure] vous permet de connecter l’instance Campaign à la base de données externe Azure Synapse.
Pour créer votre compte externe [!DNL Azure Synapse] :

1. Dans Campaign Classic, configurez votre compte externe [!DNL Azure Synapse]. Dans l’**[!UICONTROL Explorateur]**, cliquez sur **[!UICONTROL Administration]** / **[!UICONTROL Plateforme]** / **[!UICONTROL Comptes externes]**.

1. Cliquez sur **[!UICONTROL Créer]**.

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
   >Pour autoriser la communication du côté d&#39;Azure Synapse Analytics, vous devrez peut-être ajouter votre adresse IP publique à la liste autorisée. Pour ce faire, voir la [documentation Azure](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-firewall-configure#use-the-azure-portal-to-manage-server-level-ip-firewall-rules).

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
   >Pour autoriser la communication du côté d&#39;Azure Synapse Analytics, vous devrez peut-être ajouter votre adresse IP publique à la liste autorisée. Pour ce faire, voir la [documentation Azure](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-firewall-configure#use-the-azure-portal-to-manage-server-level-ip-firewall-rules).

## Configurer l’accès à Snowflake {#configure-access-to-snowflake}

>[!NOTE]
>
>Le connecteur [!DNL Snowflake] est disponible pour les déploiements hébergés et on-premise. Voir à ce propos [cet article](https://helpx.adobe.com/fr/campaign/kb/acc-on-prem-vs-hosted.html).

![](assets/snowflake_3.png)

### Compte externe Snowflake {#snowflake-external}

Le compte externe [!DNL Snowflake] vous permet de connecter l’instance Campaign à la base de données externe Snowflake.

1. Dans Campaign Classic, configurez votre compte externe [!DNL Snowflake]. Dans l’**[!UICONTROL Explorateur]**, cliquez sur **[!UICONTROL Administration]** / **[!UICONTROL Plateforme]** / **[!UICONTROL Comptes externes]**.

1. Sélectionnez le compte externe **[!UICONTROL Snowflake]** intégré.

1. Configurez le compte externe **[!UICONTROL Snowflake]**. Vous devez indiquer les informations suivantes :

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
| TimeZoneName | Vide par défaut. C’est le fuseau horaire système du serveur applicatif Campaign Classic qui est utilisé. Il est possible d’utiliser cette option pour forcer le paramètre de session TIMEZONE. <br>[Voir à ce propos cette page](https://docs.snowflake.net/manuals/sql-reference/parameters.html#timezone). |
| WeekStart | Paramètre de session WEEK_START. Par défaut, cette valeur est définie sur 0. <br>[Voir à ce propos cette page](https://docs.snowflake.com/en/sql-reference/parameters.html#week-start). |
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

La connexion à une base de données externe Hadoop dans FDA requiert les paramétrages suivants sur le serveur Adobe Campaign. Notez que cette configuration est possible pour Windows et Linux.

1. Téléchargez les pilotes ODBC pour Hadoop en fonction de votre version de système d’exploitation. Les pilotes se trouvent dans [cette page](https://www.cloudera.com/downloads.html).

1. Vous devez ensuite installer les pilotes ODBC et créer un DSN pour votre connexion Hive. Les instructions se trouvent dans [cette page](https://docs.cloudera.com/documentation/other/connectors/hive-odbc/2-6-5/Cloudera-ODBC-Driver-for-Apache-Hive-Install-Guide.pdf)

1. Après avoir téléchargé et installé les pilotes ODBC, vous devez redémarrer Campaign Classic. Pour cela, exécutez la commande suivante :

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. Dans Campaign Classic, vous pouvez ensuite configurer votre compte externe Snowflake. Dans l’**[!UICONTROL Explorateur]**, cliquez sur **[!UICONTROL Administration]** / **[!UICONTROL Plateforme]** / **[!UICONTROL Comptes externes]**.

1. Cliquez sur **[!UICONTROL Créer]**, puis sélectionnez le type de compte **[!UICONTROL Base de données externe]**.

1. Pour configurer le compte externe **[!UICONTROL Hadoop]**, vous devez indiquer les informations suivantes :

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

## Configurer l’accès à Hadoop 2.1 {#configure-access-to-hadoop}

### Pour Windows {#for-windows}

1. Installez les pilotes ODBC et [Azure HD Insight](https://www.microsoft.com/en-us/download/details.aspx?id=40886) pour Windows.
1. Créez le nom de la source de données en exécutant l&#39;outil ODBC DataSource Administrator. Il vous est fourni un exemple de nom de source de données système pour Hive que vous pouvez modifier.

   ```
   Description: vorac (or any name you like)
   Host: vorac.azurehdinsight.net
   Port: 443
   Database: sm_tst611 (or your database name)
   Mechanism: Azure HDInsight Service
   User/Password: admin/<your password here>
   ```

1. Créez le compte externe Hadoop, comme décrit dans [cette page](../../platform/using/external-accounts.md#hadoop-external-account).

### Pour Linux {#for-linux}

1. Installez unixodbc pour Linux.

   ```
   apt-get install unixodbc
   ```

1. Téléchargez et installez les pilotes ODBC pour Apache Hive depuis HortonWorks : [https://www.hortonworks.com/downloads/](https://www.hortonworks.com/downloads/).

   ```
   dpkg -i hive-odbc-native_2.1.10.1014-2_amd64.deb
   ```

1. Vérifiez l’emplacement des fichiers ODBC.

   ```
   root@campadpac71:/tmp# odbcinst -j
   unixODBC 2.3.1
   DRIVERS............: /etc/odbcinst.ini
   SYSTEM DATA SOURCES: /etc/odbc.ini
   FILE DATA SOURCES..: /etc/ODBCDataSources
   USER DATA SOURCES..: /root/.odbc.ini
   SQLULEN Size.......: 8
   SQLLEN Size........: 8
   SQLSETPOSIROW Size.: 8
   ```

1. Créez le nom de la source de données et éditez le fichier odbc.ini. Puis, créez un nom de source de données pour votre connexion Hive.

   Voici un exemple pour HDInsight destiné à configurer une connexion appelée &quot;viral&quot; :

   ```
   [ODBC Data Sources]
   vorac 
   
   [vorac]
   Driver=/usr/lib/hive/lib/native/Linux-amd64-64/libhortonworkshiveodbc64.so
   HOST=vorac.azurehdinsight.net
   PORT=443
   Schema=sm_tst611
   HiveServerType=2
   AuthMech=6
   UID=admin
   PWD=<your password here>
   HTTPPath=
   UseNativeQuery=1
   ```

   >[!NOTE]
   >
   >Le paramètre **UseNativeQuery** est ici très important. Campaign est basé sur Hive et ne fonctionnera pas correctement si le paramètre UseNativeQuery n&#39;est pas défini. En règle générale, le pilote ou Hive SQL Connector réécrit les requêtes et modifie l&#39;ordre des colonnes.

   La configuration de l&#39;authentification dépend de la configuration de Hive/Hadoop. Par exemple, pour HDInsight, utilisez AuthMech=6 pour l&#39;authentification par utilisateur/mot de passe, comme décrit [ici](https://www.simba.com/products/Spark/doc/ODBC_InstallGuide/unix/content/odbc/hi/configuring/authenticating/azuresvc.htm).

1. Exportez les variables.

   ```
   export ODBCINI=/etc/myodbc.ini
   export ODBCSYSINI=/etc/myodbcinst.ini
   ```

1. Configurez les pilotes Hortonworks via /usr/lib/hive/lib/native/Linux-amd64-64/hortonworks.hiveodbc.ini.

   Vous devez utiliser UTF-16 pour vous connecter à Campaign et unix-odbc (libodbcinst).

   ```
   [Driver]
   
   DriverManagerEncoding=UTF-16
   ErrorMessagesPath=/usr/lib/hive/lib/native/hiveodbc/ErrorMessages/
   LogLevel=0
   LogPath=/tmp/hive
   SwapFilePath=/tmp
   
   ODBCInstLib=libodbcinst.so
   ```

1. Vous pouvez maintenant tester votre connexion en utilisant isql.

   ```
   isql vorac
   isql vorac -v
   ```

1. Créez le compte externe Hadoop, comme décrit dans [cette page](../../platform/using/external-accounts.md#hadoop-external-account).

## Configurer l’accès à Netezza {#configure-access-to-netezza}

La connexion à une base de données externe Netezza en FDA requiert les paramétrages additionnels ci-dessous sur le serveur Adobe Campaign :

1. Installez les pilotes ODBC pour Netezza, en fonction du système d&#39;exploitation que vous utilisez :

   * **nz-linuxclient-v7.2.0.0.tar.gz pour Linux. Sélectionnez le dossier correspondant à votre système d&#39;exploitation (linux ou linux64) et lancez la commande unpack. Vous pouvez laisser l&#39;installation s&#39;effectuer dans le répertoire par défaut proposé : &quot;/usr/local/nz&quot;.**
   * **nz-winclient-v7.2.0.0.zip pour Windows. Décompressez le fichier et lancez le script exécutable correspondant à votre système d&#39;exploitation : nzodbcsetup.exe ou nzodbcsetup64.exe. Suivez les indications de l&#39;assistant pour finaliser l&#39;installation des pilotes.**

1. Configurez le pilote ODBC. La configuration peut être réalisée dans les fichiers standard : **/etc/odbc.ini** pour les paramètres généraux et **/etc/odbcinst.ini** pour la déclaration des pilotes.

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      ```

      « InstallDir » correspond à l’emplacement du fichier odbcinst.ini.

   * **/etc/odbcinst.ini**

      ```
      [ODBC Drivers]
      NetezzaSQL = Installed
      
      [NetezzaSQL]
      Driver           = /usr/local/nz/lib/libnzsqlodbc3.so
      Setup            = /usr/local/nz/lib/libnzsqlodbc3.so
      APILevel         = 1
      ConnectFunctions = YYN
      Description      = Netezza ODBC driver
      DriverODBCVer    = 03.51
      DebugLogging     = false
      LogPath          = /tmp
      UnicodeTranslationOption = utf8
      CharacterTranslationOption = all
      PreFetch         = 256
      Socket           = 16384
      ```

1. Définissez les variables d’environnement du serveur Adobe Campaign :

   * **LD_LIBRARY_PATH** : /usr/local/nz/lib et /usr/local/nz/lib64. &quot;/usr/local/nz&quot; correspond au répertoire d&#39;installation proposé par défaut lors de l&#39;installation des pilotes. Indiquez ici le répertoire que vous avez sélectionné pour l&#39;installation.
   * **ODBCINI** : emplacement du fichier odbc.ini (par exemple /etc/odbc.ini).
   * **NZ_ODBC_INI_PATH** : emplacement du fichier odbc.ini. Netezza requiert également cette seconde variable pour l&#39;utilisation du fichier odbc.ini.

1. Dans Campaign Classic, vous pouvez ensuite configurer votre compte externe Netezza. Dans l’**[!UICONTROL Explorateur]**, cliquez sur **[!UICONTROL Administration]** / **[!UICONTROL Plateforme]** / **[!UICONTROL Comptes externes]**.

1. Cliquez sur **[!UICONTROL Nouveau]**, puis sélectionnez **[!UICONTROL Base de données externe]** comme **[!UICONTROL Type]**.

1. Pour configurer le compte externe **[!UICONTROL Netezza]**, vous devez indiquer les informations suivantes :

   * **[!UICONTROL Type]** : Netezza

   * **[!UICONTROL Serveur]** : URL du serveur Netezza

   * **[!UICONTROL Compte]** : nom de l&#39;utilisateur

   * **[!UICONTROL Mot de passe]** : mot de passe du compte utilisateur

   * **[!UICONTROL Base de données]** : nom de la base de données

>[!NOTE]
>
>Les opérations sur les schémas comportant des clés primaires générées automatiquement ne sont pas prises en charge.
>
>La table utilise la clause **Organize on** sur le premier index défini dans le schéma. Comme cette clause est limitée de 1 à 4 colonnes avec Netezza, cet index ne peut pas contenir plus de 4 colonnes.

## Configurer l’accès à Oracle {#configure-access-to-oracle}

La connexion à une base de données externe Oracle en FDA requiert les paramétrages additionnels ci-dessous sur le serveur Adobe Campaign.

### Pour Linux {#for-linux-1}

1. Installez le client complet Oracle correspondant à votre version d&#39;Oracle.
1. Ajoutez vos définitions TNS à votre installation. Pour cela, indiquez-les dans un fichier **tnsnames.ora** dans le répertoire /etc/oracle. Si ce répertoire n’existe pas, créez-le.

   Créez alors une nouvelle variable d&#39;environnement TNS_ADMIN : export TNS_ADMIN=/etc/oracle et redémarrez la machine.

1. Intégrez Oracle à votre serveur Adobe Campaign (nlserver). Pour cela, vérifiez que le fichier **customer.sh** est bien présent dans le dossier &quot;nl6&quot; de l’arborescence du serveur Adobe Campaign et que ce dernier comprend bien les liens vers les bibliothèques Oracle.

   Par exemple pour un client 11.2 :

   ```
   export ORACLE_HOME=/usr/lib/oracle/11.2
   export TNS_ADMIN=/etc/oracle
   export LD_LIBRARY_PATH=$ORACLE_HOME/client64/lib:$LD_LIBRARY_PATH
   ```

   >[!NOTE]
   >
   >Ces valeurs (notamment ORACLE_HOME), dépendent de vos répertoires d&#39;installation. Vérifiez bien votre arborescence avant de référencer ces valeurs.

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

### Pour Windows {#for-windows-1}

1. Installez le client Oracle.
1. Dans le dossier C:Oracle, créez un fichier **tnsnames.ora** contenant vos définitions TNS.

   Ajoutez une variable d&#39;environnement TNS_ADMIN avec pour valeur C:Oracle et redémarrez la machine.

## Configurer l’accès à Sybase IQ {#configure-access-to-sybase-iq}

La connexion à une base de données externe Sybase IQ en FDA requiert les paramétrages additionnels ci-dessous sur le serveur Adobe Campaign :

1. Vérifiez que le package unixodbc se trouve sur le serveur.
1. Installez **iq_odbc**. Une erreur peut se produire à la fin de l&#39;installation. Celle-ci peut être ignorée.
1. Installez **iq_client_common**. Une erreur Java peut se produire à la fin de l&#39;installation. Celle-ci peut être ignorée.
1. Configurez le pilote ODBC. La configuration peut être réalisée dans les fichiers standard : /etc/odbc.ini pour les paramètres généraux et /etc/odbcinst.ini pour la déclaration des pilotes :

   * **/etc/odbc.ini**(remplacez les valeurs telles que `<server_alias>` par les vôtres) :

      ```
      [ODBC Data Sources]
      <server_alias>=libdbodbc.so
      
      [<server_alias>]
      Driver=/opt/sybase/IQ-16_0/lib64/libdbodbc16.so
      Description=<description>
      Username=<username>
      Password=<password>
      ServerName=<server_name>
      CommLinks=tcpip(host=<host>)
      ```

   * **/etc/odbcinst.ini**

      ```
      [ODBC DRIVERS]
      SAP SybaseIQ=Installed
      
      [SAP SybaseIQ]
      Driver=/opt/sybase/IQ-16_0/lib64/libdbodbc16.so
      ```

1. Ajoutez le chemin d&#39;accès de la nouvelle bibliothèque libodbc16.so dans la variable LD_LIBRARY_PATH. Pour ce faire :

   * Si vous utilisez un fichier customer.sh pour déclarer le chemin d&#39;accès : ajoutez le chemin d&#39;accès /opt/sybase/IQ-16_0/lib64 pour la variable LD_LIBRARY_PATH.
   * Sinon, utilisez une commande Unix.

1. Dans Campaign Classic, vous pouvez ensuite configurer votre compte externe Sybase IQ. Dans l’**[!UICONTROL Explorateur]**, cliquez sur **[!UICONTROL Administration]** / **[!UICONTROL Plateforme]** / **[!UICONTROL Comptes externes]**.

1. Cliquez sur **[!UICONTROL Nouveau]**, puis sélectionnez **[!UICONTROL Base de données externe]** comme **[!UICONTROL Type]**.

1. Pour configurer le compte externe **[!UICONTROL Sybase IQ]**, vous devez indiquer les informations suivantes :

   * **[!UICONTROL Type]** : ODBC (Sybase ASE, Sybase IQ)

   * **[!UICONTROL Serveur]** : correspond à la connexion ODBC (`<server_alias>`) définie à l’étape 5. Il ne s’agit pas nécessairement du nom du serveur lui-même.

   * **[!UICONTROL Compte]** : nom de l&#39;utilisateur

   * **[!UICONTROL Mot de passe]** : mot de passe du compte utilisateur

   * **[!UICONTROL Base de données]** : nom de la base de données

>[!NOTE]
>
>Pour Windows, vous devez installer le client Sybase IQ sur le serveur Adobe Campaign et créer une connexion ODBC. Veillez à créer une source de données système lorsque le serveur Adobe Campaign (nlserver) s’exécute en tant que service sous Windows.

## Configurer l’accès à Teradata {#configure-access-to-teradata}

La connexion à une base de données externe Teradata en FDA requiert certains paramétrages additionnels sur le serveur Adobe Campaign. Pour plus d’informations sur le paramétrage de votre base de données Teradata, consultez cet [article](https://helpx.adobe.com/fr/campaign/kb/campaign_fda_teradata.html).

1. Installez le [pilote ODBC pour Teradata](https://downloads.teradata.com/download/connectivity/odbc-driver/linux).

   Il est constitué de trois packages pouvant être installés sur Red Hat (ou CentOS)/Suse dans l&#39;ordre suivant :

   * TeraGSS
   * tdicu1510 (installez-le via setup_wrapper.sh)
   * tdodbc1510 (installez-le via setup_wrapper.sh)

1. Configurez le pilote ODBC. La configuration peut être réalisée dans les fichiers standard : **/etc/odbc.ini** pour les paramètres généraux et /etc/odbcinst.ini pour la déclaration des pilotes :

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      ```

      « InstallDir » correspond à l’emplacement du fichier **odbcinst.ini**.

   * **/etc/odbcinst.ini**

      ```
      [ODBC DRIVERS]
      teradata=Installed
      
      [teradata]
      Driver=/opt/teradata/client/15.10/lib64/tdata.so
      APILevel=CORE
      ConnectFunctions=YYY
      DriverODBCVer=3.51
      SQLLevel=1
      ```

1. Définissez les variables d’environnement du serveur Adobe Campaign :

   * **LD_LIBRARY_PATH** : /opt/teradata/client/15.10/lib64 et /opt/teradata/client/15.10/odbc_64/lib.
   * **ODBCINI** : emplacement du fichier odbc.ini (par exemple /etc/odbc.ini).
   * **NLSPATH** : emplacement du fichier opermsgs.cat (/opt/teradata/client/15.10/msg/opermsgs.cat)

1. Dans Campaign Classic, vous pouvez ensuite configurer votre compte Teradata. Dans l’**[!UICONTROL Explorateur]**, cliquez sur **[!UICONTROL Administration]** / **[!UICONTROL Plateforme]** / **[!UICONTROL Comptes externes]**.

1. Cliquez sur **[!UICONTROL Nouveau]**, puis sélectionnez **[!UICONTROL Base de données externe]** comme **[!UICONTROL Type]**.

1. Pour configurer le compte externe **[!UICONTROL Teradata]**, vous devez indiquer les informations suivantes :

   * **[!UICONTROL Type]** : Teradata

   * **[!UICONTROL Serveur]** : URL du serveur Teradata

   * **[!UICONTROL Compte]** : nom de l’utilisateur

   * **[!UICONTROL Mot de passe]** : mot de passe du compte utilisateur

   * **[!UICONTROL Base de données]** : nom de la base de données

## Configurer l’accès à SAP HANA {#configure-access-to-sap-hana}

La connexion à une base de données externe SAP HANA en FDA requiert certains paramétrages additionnels sur le serveur Adobe Campaign :

1. Installez les pilotes ODBC pour SAP HANA, en fonction du système d&#39;exploitation que vous utilisez :

   * **hdb_client_linux.tgz pour Linux. Une fois le fichier décompressé, lancez la commande hdbinst et suivez les instructions pour terminer l&#39;installation des pilotes.**
   * **Hdb_client_windows.zip** pour Windows. Décompressez le fichier et lancez l&#39;exécutable : **hdbinst.exe**. Suivez les instructions de l&#39;assistant pour terminer l&#39;installation des pilotes.

1. Configurez le pilote ODBC. La configuration peut être réalisée dans les fichiers standard : /etc/odbc.ini pour les paramètres généraux et /etc/odbcinst.ini pour la déclaration des pilotes.

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      
      [HDB]
      Driver=HDBODBC
      servernode=localhost:39013 (this value depend of your server)
      User:SYSTEM
      ```

      « InstallDir » correspond à l’emplacement du fichier **odbcinst.ini**.

   * **/etc/odbcinst.ini**

      ```
      [HDBODBC]
      Description = "SmartCloudPT HANA"
      Driver = /usr/sap/hdbclient/libodbcHDB.so
      ```

1. Définissez les variables d’environnement du serveur Adobe Campaign :

   * **LD_LIBRARY_PATH** : doit inclure le lien vers votre client SAP HANA (/usr/sap/hdbclient/libodbcHDB.so par défaut).
   * **ODBCINI** : emplacement du fichier odbc.ini (par exemple /etc/odbc.ini).

1. Dans Campaign Classic, vous pouvez ensuite configurer votre compte externe SAP Hana. Dans l’**[!UICONTROL Explorateur]**, cliquez sur **[!UICONTROL Administration]** / **[!UICONTROL Plateforme]** / **[!UICONTROL Comptes externes]**.

1. Cliquez sur **[!UICONTROL Nouveau]**, puis sélectionnez **[!UICONTROL Base de données externe]** comme **[!UICONTROL Type]**.

1. Pour configurer le compte externe **[!UICONTROL SAP Hana]**, vous devez indiquer les informations suivantes :

   * **[!UICONTROL Type]** : SAP Hana

   * **[!UICONTROL Serveur]** : URL du serveur SAP Hana

   * **[!UICONTROL Compte]** : nom de l’utilisateur

   * **[!UICONTROL Mot de passe]** : mot de passe du compte utilisateur
