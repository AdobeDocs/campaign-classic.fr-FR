---
product: campaign
title: Configuration de l'accès à BigQuery Google
description: Découvrez comment Configuration de l'accès à BigQuery Google dans FDA
audience: platform
content-type: reference
topic-tags: connectors
exl-id: ebaad59f-0607-4090-92d0-e457fbf9a348
source-git-commit: 6d53ba957fb567a9a921544418a73a9bde37c97b
workflow-type: tm+mt
source-wordcount: '955'
ht-degree: 100%

---

# Configuration de l&#39;accès à BigQuery Google {#configure-fda-google-big-query}

![](../../assets/v7-only.svg)

Utilisez l&#39;option Adobe Campaign Classic **Federated Data Access** (FDA) pour traiter les informations stockées dans une base de données externe. Suivez les étapes ci-dessous pour Configuration de l&#39;accès à [!DNL Google BigQuery].

1. Configuration de [!DNL Google BigQuery] sous [Windows](#google-windows) ou [Linux](#google-linux)
1. Configuration du [compte externe](#google-external) [!DNL Google BigQuery] dans Adobe Campaign Classic
1. Configuration du chargement en masse du connecteur [!DNL Google BigQuery] sous [Windows](#bulk-load-windows) ou [Linux](#bulk-load-linux)

>[!NOTE]
>
> Le connecteur [!DNL Google BigQuery] est disponible pour les déploiements hybrides et on-premise. Pour plus d&#39;informations à ce sujet, consultez [cette page](../../installation/using/capability-matrix.md).

![](assets/snowflake_3.png)

## BigQuery Google sous Windows {#google-windows}

### Configuration du pilote sous Windows {#driver-window}

1. Téléchargez le pilote [ODBC pour Windows](https://cloud.google.com/bigquery/docs/reference/odbc-jdbc-drivers).

1. Configurez le pilote ODBC sous Windows. Pour plus d&#39;informations à ce sujet, consultez [cette page](https://storage.googleapis.com/simba-bq-release/jdbc/Simba%20JDBC%20Driver%20for%20Google%20BigQuery%20Install%20and%20Configuration%20Guide.pdf).

1. Pour que le connecteur [!DNL Google BigQuery] fonctionne, Adobe Campaign Classic requiert les paramètres de connexion suivants :

   * **[!UICONTROL Projet]** : permet de créer ou utiliser un projet existant.

      Pour plus d&#39;informations, consultez cette [page](https://cloud.google.com/resource-manager/docs/creating-managing-projects).

   * **[!UICONTROL Compte Service]** : permet de créer un compte de service.

      Pour plus d&#39;informations, consultez cette [page](https://cloud.google.com/iam/docs/creating-managing-service-accounts).

   * **[!UICONTROL Chemin d&#39;accès au fichier de clé]** : le **[!UICONTROL compte Service]** nécessite un **[!UICONTROL fichier de clé]** pour une connexion [!DNL Google BigQuery] via ODBC.

      Pour plus d&#39;informations, consultez cette [page](https://cloud.google.com/iam/docs/creating-managing-service-account-keys).

   * **[!UICONTROL Jeu de données]** : le **[!UICONTROL jeu de données]** est facultatif pour une connexion ODBC. Comme chaque requête doit fournir le jeu de données dans lequel se trouve la table, la spécification d&#39;un **[!UICONTROL jeu de données]** est obligatoire pour le connecteur FDA [!DNL Google BigQuery] dans Adobe Campaign Classic.

      Pour plus d&#39;informations, consultez cette [page](https://cloud.google.com/bigquery/docs/datasets).

1. Dans Adobe Campaign Classic, vous pouvez ensuite configurer votre compte externe [!DNL Google BigQuery]. Pour plus d&#39;informations sur la configuration de votre compte externe, voir [cette section](#google-external).

### Configuration du chargement en masse sous Windows {#bulk-load-window}

>[!NOTE]
>
>Pour que le SDK Google Cloud fonctionne, vous devez installer Python.
>
>Nous vous recommandons d&#39;utiliser Python3 ; voir cette [page](https://www.python.org/downloads/).

L&#39;utilitaire de chargement en masse permet un transfert plus rapide grâce au SDK Google Cloud.

1. Téléchargez l&#39;archive Windows 64 bits (x86_64) à partir de cette [page](https://cloud.google.com/sdk/docs/downloads-versioned-archives) et extrayez-la dans le répertoire correspondant.

1. Exécutez le script `google-cloud-sdk\install.sh`. Vous devez accepter le paramètre de variable de chemin.

1. Après l&#39;installation, vérifiez que la variable de chemin `...\google-cloud-sdk\bin` est définie. Sinon, ajoutez-la manuellement.

1. Dans le fichier `..\google-cloud-sdk\bin\bq.cmd`, ajoutez la variable locale `CLOUDSDK_PYTHON`, qui redirigera vers l&#39;emplacement de l&#39;installation Python.

   Par exemple :

   ![](assets/google-big-query_1.png)

1. Redémarrez Adobe Campaign Classic pour que les modifications soient prises en compte.

## BigQuery Google sous Linux {#google-linux}

### Configuration du pilote sous Linux {#driver-linux}

1. Avant d&#39;installer le pilote ODBC, vous devez mettre à jour votre système. Sous Linux ou CentOS, exécutez la commande suivante :

   ```
   yum update
   # install unixODBC driver manager
   yum install unixODBC
   ```

1. Vous devez ensuite installer le gestionnaire de pilotes unixODBC avec la commande suivante :

   ```
   # switch to root user
   sudo su
   ```

   Sous Debian :

   ```
   apt-get update
   apt-get upgrade
   # install unixODBC driver manager
   apt-get install unixODBC
   ```

1. Téléchargez le [pilote ODBC Linux Magnitude Simba (.tar.gz)](https://cloud.google.com/bigquery/docs/reference/odbc-jdbc-drivers). Ensuite, transférez le fichier tarball vers un dossier temporaire sur votre ordinateur ou utilisez la commande wget :

   ```
   # in this example driver version is 2.3.1.1001
   wget https://storage.googleapis.com/simba-bq-release/odbc/SimbaODBCDriverforGoogleBigQuery_[Version]-Linux.tar.gz
   ```

1. Extrayez le fichier tarball principal comme suit, où **TarballName** correspond au nom du package tarball contenant le pilote :

   ```
   tar --directory=/tmp -zxvf [TarballName]
   ```

1. Accédez au dossier que vous avez extrait et extrayez le fichier tarball interne correspondant à la version du pilote. Installez-le dans un autre dossier temporaire, BigQueryDriver dans l&#39;exemple suivant :

   ```
   mkdir /tmp/BigQueryDriver/
   cd /tmp/SimbaODBCDriverforGoogleBigQuery_[Version]-Linux/
   tar --directory=/tmp/BigQueryDriver/ -zxvf SimbaODBCDriverforGoogleBigQuery[Bitness]_[Version].tar.gz
   ```

1. Accédez à l&#39;emplacement temporaire où le fichier tarball principal a été extrait, puis copiez les fichiers `GoogleBigQueryODBC.did` et `setup/simba.googlebigqueryodbc.ini` dans le nouveau dossier créé à l&#39;étape précédente :

   ```
   cd /tmp/SimbaODBCDriverforGoogleBigQuery_[Version]-Linux/
   cp GoogleBigQueryODBC.did /tmp/BigQueryDriver/SimbaODBCDriverforGoogleBigQuery[Bitness]_[Version]/lib/
   cp setup/simba.googlebigqueryodbc.ini /tmp/BigQueryDriver/SimbaODBCDriverforGoogleBigQuery[Bitness]_[Version]/lib/
   ```

1. Créez le répertoire d&#39;installation, comme suit :

   ```
   mkdir -p /opt/simba/googlebigqueryodbc/
   ```

1. Copiez le contenu du répertoire dans le nouveau répertoire d&#39;installation :

   ```
   cp -r /tmp/BigQueryDriver/SimbaODBCDriverforGoogleBigQuery[Bitness]_[Version]/* /opt/simba/googlebigqueryodbc/
   ```

1. Remplacez `<INSTALLDIR>` par `/opt/simba/googlebigqueryodbc` dans `simba.googlebigqueryodbc.ini` dans le répertoire d&#39;installation :

   ```
   cd /opt/simba/googlebigqueryodbc/lib/
   sed -i 's/<INSTALLDIR>/\/opt\/simba\/googlebigqueryodbc/g' simba.googlebigqueryodbc.ini
   ```

1. Remplacez `DriverManagerEncoding` par UTF-16 et `SwapFilePath` dans `simba.googlebigqueryodbc.ini`. Si nécessaire, vous pouvez également modifier les paramètres de connexion.

   Voici un exemple de fichier de configuration mis à jour à l&#39;échelle du pilote :

   ```
   # /opt/simba/googlebigqueryodbc/lib/simba.googlebigqueryodbc.ini
   [Driver]
   DriverManagerEncoding=UTF-16
   ErrorMessagesPath=opt/simba/googlebigqueryodbc/ErrorMessages
   LogLevel=6
   LogPath=/tmp
   SwapFilePath=/tmp
   ```

1. Si vous utilisez un fichier de pilotes système ou un fichier `odbcinst.ini` actuel, configurez `/etc/odbcinst.ini` pour qu&#39;il pointe vers l&#39;emplacement du pilote BigQuery Google `/opt/simba/googlebigqueryodbc/lib/libgooglebigqueryodbc_sb[Bitness].so`.

   Par exemple :

   ```
   # /etc/odbcinst.ini
   # Make sure to use Simba ODBC Driver for Google BigQuery as a driver name.
   
   [ODBC Drivers]
   Simba ODBC Driver for Google BigQuery=Installed
   
   [Simba ODBC Driver for Google BigQuery]
   Description=Simba ODBC Driver for Google BigQuery(64-bit)
   Driver=/opt/simba/googlebigqueryodbc/lib/libgooglebigqueryodbc_sb64.so
   ```

1. Recherchez l&#39;emplacement des bibliothèques du gestionnaire de pilotes unixODBC et ajoutez les chemins d&#39;accès aux bibliothèques `unixODBC` et `googlebigqueryodbc` à la variable `LD_LIBRARY_PATH environment`.

   ```
   find / -name 'lib*odbc*.so*' -print
   #output:
   /usr/lib/x86_64-linux-gnu/libodbccr.so.2
   /usr/lib/x86_64-linux-gnu/libodbcinst.so.2.0.0
   /usr/lib/x86_64-linux-gnu/libodbccr.so.1
   .
   .
   /opt/simba/googlebigqueryodbc/lib/libgooglebigqueryodbc_sb64.so
   
   #the command would look like this
   export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/opt/simba/googlebigqueryodbc:/usr/lib
   ```

1. Dans Adobe Campaign Classic, vous pouvez ensuite configurer votre compte externe [!DNL Google BigQuery]. Pour plus d&#39;informations sur la configuration de votre compte externe, voir [cette section](#google-external).

### Configuration du chargement en masse sous Linux {#bulk-load-linux}

>[!NOTE]
>
>Pour que le SDK Google Cloud fonctionne, vous devez installer Python.
>
>Nous vous recommandons d&#39;utiliser Python3 ; voir cette [page](https://www.python.org/downloads/).

L&#39;utilitaire de chargement en masse permet un transfert plus rapide grâce au SDK Google Cloud.

1. Téléchargez l&#39;archive Linux 64 bits (x86_64) à partir de cette [page](https://cloud.google.com/sdk/docs/downloads-versioned-archives) et extrayez-la dans le répertoire correspondant.

1. Exécutez le script `google-cloud-sdk\install.sh`. Vous devez accepter le paramètre de variable de chemin.

1. Après l&#39;installation, vérifiez que la variable de chemin `...\google-cloud-sdk\bin` est définie. Sinon, ajoutez-la manuellement.

1. Si vous souhaitez éviter d&#39;utiliser la variable `PATH` ou de déplacer le répertoire `google-cloud-sdk` vers un autre emplacement, utilisez la valeur de l&#39;option `bqpath` lors de la configuration du **[!UICONTROL Compte externe]** pour spécifier le chemin exact vers le répertoire bin de votre système.

1. Redémarrez Adobe Campaign Classic pour que les modifications soient prises en compte.

## Compte externe BigQuery Google {#google-external}

Vous devez créer un compte externe [!DNL Google BigQuery] pour connecter votre instance Adobe Campaign Classic à votre base de données [!DNL Google BigQuery] externe.

1. Dans l&#39;**[!UICONTROL Explorateur]** Adobe Campaign Classic, cliquez sur **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Plateforme]** &#39;>&#39; **[!UICONTROL Comptes externes]**.

1. Cliquez sur **[!UICONTROL Nouveau]**.

1. Sélectionnez **[!UICONTROL Base de données externe]** en tant que **[!UICONTROL Type]** de compte externe.

1. Configurez le compte externe [!DNL Google BigQuery]. Vous devez indiquer les informations suivantes :

   * **[!UICONTROL Type]**: [!DNL Google BigQuery]

   * **[!UICONTROL Compte Service]** : adresse e-mail de votre **[!UICONTROL compte Service]**. Pour plus d&#39;informations à ce propos, consultez la [documentation Google Cloud](https://cloud.google.com/iam/docs/creating-managing-service-accounts).

   * **[!UICONTROL Projet]** : nom de votre **[!UICONTROL projet]**. Pour plus d&#39;informations à ce propos, consultez la [documentation Google Cloud](https://cloud.google.com/resource-manager/docs/creating-managing-projects).

   * **[!UICONTROL Chemin d&#39;accès au fichier de clé]** :
      * **[!UICONTROL Télécharger le fichier de clé sur le serveur]** : sélectionnez **[!UICONTROL Cliquer ici pour effectuer le téléchargement]** si vous choisissez de télécharger la clé via Adobe Campaign Classic.

      * **[!UICONTROL Saisir manuellement le chemin d&#39;accès au fichier de clé]** : copiez/collez votre chemin absolu dans ce champ si vous choisissez d&#39;utiliser une clé préexistante.
   * **[!UICONTROL Jeu de données]** : nom de votre **[!UICONTROL jeu de données]**. Pour plus d&#39;informations à ce propos, consultez la [documentation Google Cloud](https://cloud.google.com/bigquery/docs/datasets-intro).
   ![](assets/google-big-query.png)
