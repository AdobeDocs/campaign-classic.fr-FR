---
product: campaign
title: Installation de packages avec Linux
description: Installation de packages avec Linux
feature: Installation, Application Settings
badge-v7-prem: label="On-premise/hybride uniquement" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: f41c7510-5ad7-44f3-9485-01f54994b6cb
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '1205'
ht-degree: 92%

---

# Installation de packages avec Linux{#installing-packages-with-linux}



Pour une plateforme Linux 32 bits, procédez à une installation d&#39;Adobe Campaign 32 bits. Pour une plateforme Linux 64 bits, procédez à une installation d&#39;Adobe Campaign 64 bits.

Pour chacune de ces versions, Adobe Campaign est livré avec un package **nlserver**, qui contient les binaires et les fichiers de configuration pour une version donnée.

Les commandes d&#39;installation permettent de :

* Copier les fichiers sous **/usr/local/neolane**
* Créer un compte Linux Adobe Campaign (et le groupe associé), avec pour répertoire racine (home directory) : **/usr/local/neolane**,
* Création d’un script automatique **/etc/init.d/nlserver6** à utiliser au démarrage ou à créer une unité systemd (à partir de la version 20.1).

>[!NOTE]
>
>La variable **neolane** l’utilisateur système ne doit pas avoir été créé avant l’exécution de la commande. La variable **neolane** l’utilisateur est automatiquement créé lors de l’installation.
>
>La variable **home** du répertoire **neolane** l’utilisateur est également créé automatiquement dans **[!UICONTROL /usr/local/neolane]**. Assurez-vous qu’il y a suffisamment d’espace sur le **[!UICONTROL /usr/local]** disque (plusieurs Go).

Vous pouvez tester si le serveur peut s&#39;atteindre lui-même en lançant un **ping`hostname`**.

## Distribution basée sur les packages RPM {#distribution-based-on-rpm--packages}

Pour installer Adobe Campaign sur un système d&#39;exploitation RPM (RHEL, CentOS et SUSE), les étapes sont les suivantes :

1. Vous devez au préalable accéder aux deux packages d&#39;Adobe Campaign.

   Le fichier est nommé comme ci-dessous, où **XXXX** est le numéro de build d’Adobe Campaign : **nlserver6-v7-XXXX-0.x86_64.rpm**.

   >[!CAUTION]
   >
   >Vérifiez que vous utilisez bien le nom de fichier correct pour votre version d&#39;Adobe Campaign dans les exemples de commande de cette section.

1. Pour les installer, connectez-vous en tant que **root** et exécutez la commande suivante (où **XXXX** est le numéro de build d&#39;Adobe Campaign) :

   ```
   yum install nlserver6-v7-XXXX-0.x86_64.rpm
   ```

   Le fichier rpm possède des dépendances dans les packages des distributions CentOS/Red Hat. Si vous ne souhaitez pas employer certaines de ces dépendances (par exemple, si vous souhaitez utiliser Oracle JDK au lieu d&#39;OpenJDK), vous devrez peut-être utiliser l&#39;option &quot;nodeps&quot; du fichier rpm :

   ```
   rpm --nodeps -Uvh nlserver6-v7-XXXX-0.x86_64.rpm
   ```

La commande &#39;bc&#39;, nécessaire à l&#39;exécution du netreport (voir [cette section](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts), pour plus d&#39;informations) n&#39;est pas présente par défaut sur toutes les distributions Linux. Pour vérifier si la commande est disponible, exécutez la commande &#39;which bc&#39;. Si elle n&#39;est pas présente, vous devez l&#39;installer.

Sur CentOS, il faut installer le package bc.x86_64 : connectez-vous en tant que **root** et exécutez la commande suivante :

```
yum install bc.x86_64
```

## Distribution basée sur ATP (Debian) {#distribution-based-on-apt--debian-}

### Sous Debian 64 bits {#in-debian-64-bits}

Pour installer Adobe Campaign 64 bits sur un système d’exploitation Debian 64 bits, les étapes sont les suivantes :

1. Vous devez d’abord obtenir le package Adobe Campaign : **nlserver6-v7-XXXX-linux-2.6-amd64.deb**, où **XXXX** est le numéro de la build.

   >[!CAUTION]
   >
   >Vérifiez que vous utilisez bien le nom de fichier correct pour votre version d&#39;Adobe Campaign dans les exemples de commande de cette section.

1. Pour les installer, connectez-vous en tant que **root** et exécutez la commande suivante (où **XXXX** est le numéro de build d&#39;Adobe Campaign) :

   ```
   dpkg -i nlserver6-v7-XXXX-linux-2.6-amd64.deb
   ```

   S’il manque des dépendances, exécutez la commande suivante :

   ```
   apt-get install -f
   ```

**Particularités de Debian 8/9**

Pour installer Adobe Campaign sur un système d’exploitation Debian 8/9, tenez compte des points suivants :

* OpenSSL doit être installé préalablement.
* Installer les librairies libicu52 (Debian 8) ou libicu57 (Debian 9), libprotobuf9 (Debian8) et libc-ares2 avec les commandes suivantes :

  ```
  aptitude install libicu52 (Debian 8) libicu57 (Debian 9)
  ```

  ```
  aptitude install libc-ares2
  ```

  ```
  aptitude install libprotobuf9 (only Debian 8)
  ```

* Installer le JDK7 avec la commande suivante :

  ```
  aptitude install openjdk-7-jdk (Debian 8)
  ```

  ```
  aptitude install openjdk-7-jdk (Debian 9)
  ```

## Personnaliser les paramètres {#personalizing-parameters}

Certains paramètres peuvent être personnalisés via le fichier **customer.sh**.

Si vous effectuez l&#39;installation pour la première fois, le fichier **customer.sh** n&#39;existe peut-être pas encore sur le serveur. Créez-le et assurez-vous qu&#39;il dispose des droits d&#39;exécution. Dans le cas contraire, saisissez la commande suivante :

```
chmod +x /usr/local/neolane/nl6/customer.sh
```

### Encodage du serveur {#server-encoding}

Par défaut, le serveur est démarré dans un environnement iso8859-15. Néanmoins, le serveur peut être démarré dans un environnement UTF-8.

>[!CAUTION]
>
>Cette modification a une incidence sur les interactions avec le système de fichiers (fichiers chargés via un workflow ou un script JavaScript) et sur le codage des fichiers. Nous vous recommandons donc d&#39;utiliser l&#39;environnement par défaut.

Toutefois, pour la création d&#39;une **instance japonaise**, l&#39;utilisation d&#39;un environnement UTF-8 est obligatoire.

Pour activer l&#39;environnement UTF-8, utilisez la commande suivante :

```
mkdir -p /usr/local/neolane/nl6 
touch /usr/local/neolane/nl6/unicodeenv
```

### Langue par défaut pour le serveur {#default-language-for-the-server}

L&#39;installation supporte à la fois le français et l&#39;anglais. Par défaut, le serveur utilise l&#39;anglais.

Pour basculer en français, saisissez les commandes suivantes :

```
su - neolane
vi nl6/customer.sh
```

et ajoutez la ligne suivante :

```
export neolane_LANG=fra
```

Pour garantir une bonne lecture des messages système, les consoles doivent être dans une page de codes correspondant à la langue (ISO-8859-1 ou -15 pour le français).

### Variables d&#39;environnement {#environment-variables}

Les variables d&#39;environnement suivantes doivent être définies correctement.

Certaines combinaisons nécessitent des modifications de l&#39;environnement utilisé pour exécuter Adobe Campaign. Un fichier spécifique (`/usr/local/neolane/nl6/customer.sh`) peut être créé et modifié pour ajouter des modifications spécifiques à l&#39;environnement Adobe Campaign.

Au besoin, éditez le fichier **customer.sh** à l&#39;aide de la commande **vi customer.sh** et adaptez la configuration ou ajoutez les lignes manquantes :

* Pour le client Oracle :

  ```
  export ORACLE_HOME=/usr/local/instantclient_10_2
  export TNS_ADMIN=/etc/oracle
  export LD_LIBRARY_PATH=$ORACLE_HOME/lib:$LD_LIBRARY_PATH 
  ```

  Le contenu de la variable d&#39;environnement ORACLE_HOME correspond au répertoire d&#39;installation d&#39;Oracle.

  Le contenu de la variable TNS_ADMIN doit correspondre au répertoire d&#39;enregistrement du fichier **tnsnames.ora**.

* Pour LibreOffice :

  Si vous souhaitez faire fonctionner Adobe Campaign sur une version de LibreOffice existante, une configuration complémentaire est nécessaire : vous devez indiquer les chemins d&#39;accès aux répertoires d&#39;installation. Par exemple :

   * Debian

     Les valeurs par défaut de OOO_INSTALL_DIR et OOO_BASIS_INSTALL_DIR sont fournies. Vous pouvez les remplacer dans **customer.sh** si la disposition de l&#39;installation LibreOffice est différente :

     ```
     export OOO_BASIS_INSTALL_DIR=/usr/lib/libreoffice/ 
     export OOO_INSTALL_DIR=/usr/lib/libreoffice/
     ```

   * CentOs

     Utiliser les valeurs par défaut suivantes :

     ```
     export OOO_BASIS_INSTALL_DIR=/usr/lib64/libreoffice/
     export OOO_INSTALL_DIR=/usr/lib64/libreoffice/
     ```

* Pour Java Development Kit (JDK) :

  Par défaut, le script de configuration de l&#39;environnement Adobe Campaign (`~/nl6/env.sh`) recherche le répertoire d&#39;installation du JDK. Ce comportement n&#39;étant pas fiable à 100 %, vous devez indiquer le JDK à utiliser. Pour ce faire, vous pouvez forcer la variable d&#39;environnement **JDK_HOME** à l&#39;aide de la commande suivante :

  ```
  export JDK_HOME=/usr/java/jdk1.6.0_07
  ```

  >[!NOTE]
  >
  >Il s&#39;agit ici d&#39;un exemple. Assurez-vous que la version du JDK utilisée correspond au nom du répertoire.

  Pour tester la configuration du JDK, connectez-vous en tant qu&#39;utilisateur Adobe Campaign système avec la commande suivante :

  ```
  su - neolane
  ```

Vous devez relancer le service Adobe Campaign afin que les changements d&#39;environnement soient pris en compte.

Les commandes sont les suivantes :

```
/etc/init.d/nlserver6 stop
/etc/init.d/nlserver6 start
```

À compter de la version 20.1, nous vous recommandons d’utiliser plutôt la commande suivante :

```
systemctl stop nlserver
systemctl start nlserver
```

### Client Oracle sous Linux {#oracle-client-in-linux}

Lorsque vous utilisez Oracle avec Adobe Campaign, vous devez configurer les couches clientes Oracle sous Linux.

* Utilisez la version cliente complète
* Définition TNS

  Vous devez ajouter vos définitions TNS lors de la phase d&#39;installation. Pour cela, les commandes sont les suivantes :

  ```
  cd /etc
  mkdir oracle
  cd oracle
  vi tnsnames.ora
  ```

* Variables d&#39;environnement

  Pour plus d&#39;informations, consultez la section [Variables d&#39;environnement](../../installation/using/installing-packages-with-linux.md#environment-variables).

* Paramétrage pour Adobe Campaign

  Pour finaliser l&#39;installation du client Oracle pour Adobe Campaign, vous devez créer un lien symbolique pour le fichier **.so** utilisé par Adobe Campaign.

  Pour cela, les commandes sont les suivantes :

  ```
  cd /usr/lib/oracle/10.2.0.4/client/lib
  ln -s libclntsh.so.10.1 libclntsh.so
  ```

En cas de problème, vérifiez que les packages listés dans la [documentation d&#39;installation Oracle](https://docs.oracle.com/) sont bien installés.

## Vérification de l&#39;installation {#installation-checks}

Vous pouvez procéder à un test initial de l&#39;installation à l&#39;aide des commandes suivantes :

```
su - neolane
nlserver pdump
```

Lorsque Adobe Campaign n&#39;est pas démarré, la réponse est :

```
no task
```

## Premier démarrage du serveur {#first-start-up-of-the-server}

Une fois le test d&#39;installation réalisé, saisissez la commande suivante :

```
nlserver web
```

Les informations affichées sont alors les suivantes :

```
17:11:03 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
17:11:03 >   Web server start (pid=17546, tid=-151316352)...
17:11:03 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/serverConf.xml' via '/usr/local/[INSTALL]/nl6/conf/fra/serverConf.xml.sample'
17:11:03 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/config-default.xml' via '/usr/local/[INSTALL]/nl6/conf/models/config-default.xml'
17:11:03 >   Server started
17:11:08 >   Stop requested (pid=17546)
17:11:08 >   Web server stop(pid=17546, tid=-151316352)...
```

Ces commandes permettent de créer les fichiers de configuration **config-default.xml** et **serverConf.xml**. Tous les paramètres disponibles dans le fichier **serverConf.xml** sont répertoriés dans cette [section](../../installation/using/the-server-configuration-file.md).

Saisissez la combinaison **Ctr+C** pour arrêter le processus, puis la commande suivante :

```
nlserver start web
```

Les informations affichées sont alors les suivantes :

```
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Running task 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair') in a new process
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Web server start (pid=29188, tid=-1224824320)...
12:17:21 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/serverConf.xml' via '/usr/local/[INSTALL]/nl6/conf/fra/serverConf.xml.sample'
12:17:22 >   Tomcat started
12:17:22 >   Server started
```

Pour l&#39;arrêter, saisissez :

```
nlserver stop web
```

Les informations affichées sont alors les suivantes :

```
12:18:31 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:18:31 >   Stop requested for 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair', pid=29188, tid=-1224824320)...
12:18:31 >   Stop requested (pid=29188)
12:18:31 >   Web server stopped (pid=29188, tid=-1224824320)...
```

## Mot de passe de l&#39;identifiant internal {#password-for-the-internal-identifier}

Le serveur Adobe Campaign définit un identifiant (ou &#39;login&#39;) technique nommé **internal** qui possède tous les droits, sur toutes les instances. Après une installation récente, cet identifiant n&#39;a pas de mot de passe. Il est obligatoire d&#39;en définir un.

En savoir plus dans [cette section](../../installation/using/configuring-campaign-server.md#internal-identifier).
