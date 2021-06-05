---
solution: Campaign Classic
product: campaign
title: Configurer l’accès à Google BigQuery
description: Découvrez comment configurer l’accès à Google BigQuery dans FDA
audience: platform
content-type: reference
topic-tags: connectors
source-git-commit: 911302475b5ece96d527575148ee611fdb839753
workflow-type: tm+mt
source-wordcount: '955'
ht-degree: 11%

---


# Configurer l’accès à Google BigQuery {#configure-fda-google-big-query}

Utilisez l’option Adobe Campaign Classic **Federated Data Access** (FDA) pour traiter les informations stockées dans une base de données externe. Suivez les étapes ci-dessous pour configurer l’accès à [!DNL Google BigQuery].

1. Configurer [!DNL Google BigQuery] sous [Windows](#google-windows) ou [Linux](#google-linux)
1. Configuration du [!DNL Google BigQuery] [compte externe](#google-external) dans Adobe Campaign Classic
1. Configurez le [!DNL Google BigQuery] chargement en masse du connecteur sur [Windows](#bulk-load-windows) ou [Linux](#bulk-load-linux)

>[!NOTE]
>
> [!DNL Google BigQuery] Le connecteur est disponible pour les déploiements hybrides et on-premise. Pour plus d’informations à ce sujet, consultez [cette page](../../installation/using/capability-matrix.md).

![](assets/snowflake_3.png)

## Google BigQuery sous Windows {#google-windows}

### Configuration du pilote sous Windows {#driver-window}

1. Téléchargez le pilote [ODBC pour Windows](https://cloud.google.com/bigquery/docs/reference/odbc-jdbc-drivers).

1. Configurez le pilote ODBC sous Windows. Pour plus d’informations à ce sujet, consultez [cette page](https://storage.googleapis.com/simba-bq-release/jdbc/Simba%20JDBC%20Driver%20for%20Google%20BigQuery%20Install%20and%20Configuration%20Guide.pdf).

1. Pour que le connecteur [!DNL Google BigQuery] fonctionne, Adobe Campaign Classic requiert les paramètres suivants pour se connecter :

   * **[!UICONTROL Projet]** : créer ou utiliser un projet existant ;

      Pour plus d’informations, consultez cette [page](https://cloud.google.com/resource-manager/docs/creating-managing-projects).

   * **[!UICONTROL Compte]** de service : créez un compte de service.

      Pour plus d’informations, consultez cette [page](https://cloud.google.com/iam/docs/creating-managing-service-accounts).

   * **[!UICONTROL Key File Path]** : Le compte  **[!UICONTROL de service]** nécessite un  **[!UICONTROL fichier]** clé pour une  [!DNL Google BigQuery] connexion via ODBC.

      Pour plus d’informations, consultez cette [page](https://cloud.google.com/iam/docs/creating-managing-service-account-keys).

   * **[!UICONTROL Jeu de données]** :  **** Les jeux de données sont facultatifs pour une connexion ODBC. Comme chaque requête doit fournir le jeu de données où se trouve le tableau, la spécification d’un **[!UICONTROL jeu de données]** est obligatoire pour le connecteur FDA [!DNL Google BigQuery] dans Adobe Campaign Classic.

      Pour plus d’informations, consultez cette [page](https://cloud.google.com/bigquery/docs/datasets).

1. Dans Adobe Campaign Classic, vous pouvez ensuite configurer votre compte externe [!DNL Google BigQuery]. Pour plus d’informations sur la configuration de votre compte externe, voir [cette section](#google-external).

### Chargement en masse configuré sous Windows {#bulk-load-window}

>[!NOTE]
>
>Pour que le SDK Google Cloud fonctionne, vous devez installer Python.
>
>Nous vous recommandons d’utiliser Python3, voir cette [page](https://www.python.org/downloads/).

L’utilitaire de chargement en masse permet un transfert plus rapide grâce au SDK Google Cloud.

1. Téléchargez l’archive Windows 64 bits (x86_64) à partir de cette [page](https://cloud.google.com/sdk/docs/downloads-versioned-archives) et extrayez-la dans le répertoire correspondant.

1. Exécutez le script `google-cloud-sdk\install.sh`. Vous devez accepter le paramètre de variable de chemin.

1. Après l’installation, vérifiez que la variable de chemin `...\google-cloud-sdk\bin` est définie. Si ce n’est pas le cas, ajoutez-le manuellement.

1. Dans le fichier `..\google-cloud-sdk\bin\bq.cmd` , ajoutez la variable locale `CLOUDSDK_PYTHON`, qui redirigera vers l’emplacement de l’installation Python.

   Par exemple :

   ![](assets/google-big-query_1.png)

1. Redémarrez Adobe Campaign Classic pour que les modifications soient prises en compte.

## Google BigQuery sous Linux {#google-linux}

### Pilote configuré sous Linux {#driver-linux}

1. Avant d’installer le pilote ODBC, vous devez mettre à jour votre système. Sous Linux ou CentOS, exécutez la commande suivante :

   ```
   yum update
   # install unixODBC driver manager
   yum install unixODBC
   ```

1. Vous devez ensuite installer le gestionnaire de pilotes unixODBC avec la commande suivante :

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

1. Téléchargez le [pilote ODBC Linux Magnitude Simba (.tar.gz)](https://cloud.google.com/bigquery/docs/reference/odbc-jdbc-drivers). Ensuite, transférez le fichier tarball dans un dossier temporaire sur votre ordinateur ou utilisez la commande wget :

   ```
   # in this example driver version is 2.3.1.1001
   wget https://storage.googleapis.com/simba-bq-release/odbc/SimbaODBCDriverforGoogleBigQuery_[Version]-Linux.tar.gz
   ```

1. Extrayez le fichier tarball principal comme suit, où **TarballName** est le nom du package tarball contenant le pilote :

   ```
   tar --directory=/tmp -zxvf [TarballName]
   ```

1. Accédez au dossier que vous avez extrait et extrayez le fichier tarball interne correspondant à la version du pilote. Installez-le dans un autre dossier temporaire, dans l’exemple suivant BigQueryDriver :

   ```
   mkdir /tmp/BigQueryDriver/
   cd /tmp/SimbaODBCDriverforGoogleBigQuery_[Version]-Linux/
   tar --directory=/tmp/BigQueryDriver/ -zxvf SimbaODBCDriverforGoogleBigQuery[Bitness]_[Version].tar.gz
   ```

1. Accédez à l’emplacement temporaire où le fichier tarball principal a été extrait, puis copiez les fichiers `GoogleBigQueryODBC.did` et `setup/simba.googlebigqueryodbc.ini` dans le nouveau dossier créé à l’étape précédente :

   ```
   cd /tmp/SimbaODBCDriverforGoogleBigQuery_[Version]-Linux/
   cp GoogleBigQueryODBC.did /tmp/BigQueryDriver/SimbaODBCDriverforGoogleBigQuery[Bitness]_[Version]/lib/
   cp setup/simba.googlebigqueryodbc.ini /tmp/BigQueryDriver/SimbaODBCDriverforGoogleBigQuery[Bitness]_[Version]/lib/
   ```

1. Créez le répertoire d&#39;installation, comme suit :

   ```
   mkdir -p /opt/simba/googlebigqueryodbc/
   ```

1. Copiez le contenu du répertoire dans le nouveau répertoire d’installation :

   ```
   cp -r /tmp/BigQueryDriver/SimbaODBCDriverforGoogleBigQuery[Bitness]_[Version]/* /opt/simba/googlebigqueryodbc/
   ```

1. Remplacez `<INSTALLDIR>` par `/opt/simba/googlebigqueryodbc` dans `simba.googlebigqueryodbc.ini` dans le répertoire d’installation :

   ```
   cd /opt/simba/googlebigqueryodbc/lib/
   sed -i 's/<INSTALLDIR>/\/opt\/simba\/googlebigqueryodbc/g' simba.googlebigqueryodbc.ini
   ```

1. Remplacez `DriverManagerEncoding` par UTF-16 et `SwapFilePath` dans `simba.googlebigqueryodbc.ini`. Si nécessaire, vous pouvez également modifier les paramètres de journalisation.

   Voici un exemple de fichier de configuration mis à jour à l’échelle du pilote :

   ```
   # /opt/simba/googlebigqueryodbc/lib/simba.googlebigqueryodbc.ini
   [Driver]
   DriverManagerEncoding=UTF-16
   ErrorMessagesPath=opt/simba/googlebigqueryodbc/ErrorMessages
   LogLevel=6
   LogPath=/tmp
   SwapFilePath=/tmp
   ```

1. Si vous utilisez un fichier de pilotes système ou un fichier `odbcinst.ini` actuel, configurez `/etc/odbcinst.ini` pour qu’il pointe vers l’emplacement du pilote Google BigQuery `/opt/simba/googlebigqueryodbc/lib/libgooglebigqueryodbc_sb[Bitness].so`.

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

1. Recherchez l’emplacement des bibliothèques du gestionnaire de pilotes unixODBC et ajoutez les chemins d’accès aux bibliothèques `unixODBC` et `googlebigqueryodbc` à la variable `LD_LIBRARY_PATH environment`.

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

1. Dans Adobe Campaign Classic, vous pouvez ensuite configurer votre compte externe [!DNL Google BigQuery]. Pour plus d’informations sur la configuration de votre compte externe, voir [cette section](#google-external).

### Chargement en masse configuré sous Linux {#bulk-load-linux}

>[!NOTE]
>
>Pour que le SDK Google Cloud fonctionne, vous devez installer Python.
>
>Nous vous recommandons d’utiliser Python3, voir cette [page](https://www.python.org/downloads/).

L’utilitaire de chargement en masse permet un transfert plus rapide grâce au SDK Google Cloud.

1. Téléchargez l’archive Linux 64 bits (x86_64) dans cette [page](https://cloud.google.com/sdk/docs/downloads-versioned-archives) et extrayez-la dans le répertoire correspondant.

1. Exécutez le script `google-cloud-sdk\install.sh`. Vous devez accepter le paramètre de variable de chemin.

1. Après l’installation, vérifiez que la variable de chemin `...\google-cloud-sdk\bin` est définie. Si ce n’est pas le cas, ajoutez-le manuellement.

1. Si vous souhaitez éviter d’utiliser la variable `PATH` ou de déplacer le répertoire `google-cloud-sdk` vers un autre emplacement, utilisez la valeur de l’option `bqpath` lors de la configuration du **[!UICONTROL Compte externe]** pour spécifier le chemin exact vers le répertoire bin de votre système.

1. Redémarrez Adobe Campaign Classic pour que les modifications soient prises en compte.

## Compte externe Google BigQuery {#google-external}

Vous devez créer un compte externe [!DNL Google BigQuery] pour connecter votre instance Adobe Campaign Classic à votre [!DNL Google BigQuery] base de données externe.

1. Dans Adobe Campaign Classic **[!UICONTROL Explorateur]**, cliquez sur **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Plateforme]** &#39;>&#39; **[!UICONTROL Comptes externes]**.

1. Cliquez sur **[!UICONTROL Nouveau]**.

1. Sélectionnez **[!UICONTROL Base de données externe]** en tant que **[!UICONTROL Type]** de compte externe.

1. Configurez le compte externe [!DNL Google BigQuery]. Vous devez indiquer les informations suivantes :

   * **[!UICONTROL Type]**: [!DNL Google BigQuery]

   * **[!UICONTROL Compte]** de service : Adresse électronique de votre compte  **[!UICONTROL de service]**. Voir à ce propos la [documentation Google Cloud](https://cloud.google.com/iam/docs/creating-managing-service-accounts).

   * **[!UICONTROL Projet]** : Nom de votre  **[!UICONTROL projet]**. Voir à ce propos la [documentation Google Cloud](https://cloud.google.com/resource-manager/docs/creating-managing-projects).

   * **[!UICONTROL Key file Path]** :
      * **[!UICONTROL Téléchargez le fichier de clé sur le serveur]** : sélectionnez  **[!UICONTROL Cliquez ici pour]** télécharger la clé si vous choisissez de la télécharger via Adobe Campaign Classic.

      * **[!UICONTROL Saisissez manuellement le chemin d’accès]** au fichier clé : copiez/collez votre chemin absolu dans ce champ si vous choisissez d’utiliser une clé préexistante.
   * **[!UICONTROL Jeu de données]** : Nom de votre  **[!UICONTROL jeu de données]**. Voir à ce propos la [documentation Google Cloud](https://cloud.google.com/bigquery/docs/datasets-intro).
   ![](assets/google-big-query.png)
