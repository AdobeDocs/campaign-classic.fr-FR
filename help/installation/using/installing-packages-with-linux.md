---
product: campaign
title: Installation de packages avec Linux
description: Installation de packages avec Linux
feature: Installation, Application Settings
badge-v7-prem: label="On-Premise/hybride uniquement" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: f41c7510-5ad7-44f3-9485-01f54994b6cb
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: ht
source-wordcount: '0'
ht-degree: 100%

---

# Installation de packages avec Linux {#installing-packages-with-linux}

Adobe Campaign est fourni avec le package **nlserver** qui contient les fichiers binaires et de configuration pour une version donnée.

Les commandes d&#39;installation permettent de :

* Copier les fichiers sous **/usr/local/neolane**
* Créer un compte Linux Adobe Campaign (et le groupe associé), avec pour répertoire racine (home directory) : **/usr/local/neolane**,
* Créez un script automatique **/etc/init.d/nlserver6** à utiliser au démarrage ou créez une unité systemd.

>[!NOTE]
>
>L&#39;utilisateur système **neolane** ne doit pas avoir été créé avant de lancer ces commandes. L&#39;utilisateur **neolane** est automatiquement créé lors de l&#39;installation.
>
>Le répertoire **home** associé à l&#39;utilisateur **neolane** est lui aussi automatiquement créé sous **[!UICONTROL /usr/local/neolane]**. Assurez-vous que **[!UICONTROL /usr/local]** dispose de suffisamment d’espace disque.

Vous pouvez tester si le serveur peut s&#39;atteindre lui-même en lançant un **ping`hostname`**.

## Distribution basée sur les packages RPM {#distribution-based-on-rpm--packages}

>[!AVAILABILITY]
>
>À compter de la version 7.4.1, les bibliothèques XML pour les packages RPM Linux ne sont plus incluses dans Campaign. Vous devez installer ces bibliothèques.
> 

Pour installer Adobe Campaign sur un système d’exploitation RPM (RHEL, CentOS), suivez les étapes ci-après :

1. Récupérez le package Adobe Campaign. Le nom du fichier est **nlserver6-v7-XXXX-0.x86_64.rpm**, où **XXXX** est le numéro de build d’Adobe Campaign.

   >[!CAUTION]
   >
   >Vérifiez que vous utilisez bien le nom de fichier correct pour votre version d’Adobe Campaign dans les exemples de commandes de cette section.

1. Pour l’installer, connectez-vous en tant que **root** et exécutez la commande suivante (où **XXXX** est le numéro de build d’Adobe Campaign) :

   ```
   yum install nlserver6-v7-XXXX-0.x86_64.rpm
   ```

   Le fichier rpm possède des dépendances dans les packages des distributions CentOS/Red Hat. Si vous ne souhaitez pas employer certaines de ces dépendances (par exemple, si vous souhaitez utiliser Oracle JDK au lieu d’OpenJDK), vous devrez peut-être utiliser l&#39;option « nodeps » du fichier rpm :

   ```
   rpm --nodeps -Uvh nlserver6-v7-XXXX-0.x86_64.rpm
   ```

Notez que la plupart des dépendances répertoriées sont obligatoires et que `nlserver` ne peut pas démarrer si elles ne sont pas installées (opendk fait exception à la règle ; un autre JDK peut être installé).

La commande `bc`, obligatoire pour exécuter le script [netreport](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts), n’est pas disponible par défaut sur toutes les distributions Linux. Pour vérifier si la commande est disponible, exécutez la commande `which bc`. Si elle n&#39;est pas présente, vous devez l&#39;installer.

Sur CentOS, il faut installer le package bc.x86_64 : connectez-vous en tant que **root** et exécutez la commande suivante :

```
yum install bc.x86_64
```

## Distribution basée sur ATP (Debian) {#distribution-based-on-apt--debian-}

Pour installer Adobe Campaign sur un système d’exploitation Debian 64 bits, suivez les étapes ci-après :

1. Récupérez le package Adobe Campaign. Le nom du fichier est **nlserver6-v7-XXXX-linux-2.6-amd64.deb**, où **XXXX** est le numéro de build d’Adobe Campaign.

   >[!CAUTION]
   >
   >Vérifiez que vous utilisez bien le nom de fichier correct pour votre version d’Adobe Campaign dans les exemples de commandes de cette section.

1. Pour l’installer, connectez-vous en tant que **root** et exécutez la commande suivante (où **XXXX** est le numéro de build d’Adobe Campaign) :

   ```
   apt install ./nlserver6-v7-XXXX-linux-2.6-amd64.deb
   ```


## Personnaliser les paramètres {#personalizing-parameters}

Certains paramètres peuvent être personnalisés via le fichier **customer.sh**.

Si vous effectuez l’installation pour la première fois, le fichier **customer.sh** n’existe peut-être pas encore sur le serveur.

Créez-le et assurez-vous qu&#39;il dispose des droits d&#39;exécution. Dans le cas contraire, saisissez la commande suivante :

```
chmod +x /usr/local/neolane/nl6/customer.sh
```

### Encodage du serveur {#server-encoding}

Par défaut, le serveur est démarré dans un environnement iso8859-15. Néanmoins, le serveur peut être démarré dans un environnement UTF-8.

>[!CAUTION]
>
>Cette modification a une incidence sur les interactions avec le système de fichiers (fichiers chargés via un workflow ou un script JavaScript) et sur le codage des fichiers. Nous vous recommandons donc d&#39;utiliser l&#39;environnement par défaut.

Pour créer une **instance en japonais**, vous devez utiliser un environnement UTF-8.

Pour activer l’environnement UTF-8, utilisez la commande suivante :

```
mkdir -p /usr/local/neolane/nl6 
touch /usr/local/neolane/nl6/unicodeenv
```

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

  Par défaut, le script de configuration de l&#39;environnement Adobe Campaign (`~/nl6/env.sh`) recherche le répertoire d&#39;installation du JDK. Il est toutefois recommandé de spécifier le JDK à utiliser. Pour ce faire, vous pouvez forcer la variable d’environnement **JDK_HOME** à l’aide de la commande suivante :

  ```
  export JDK_HOME=/usr/java/jdkX.Y.Z
  ```

  >[!NOTE]
  >
  >Assurez-vous que la version du JDK utilisée correspond au nom du répertoire.

  Pour tester la configuration du JDK, connectez-vous en tant qu&#39;utilisateur Adobe Campaign système avec la commande suivante :

  ```
  su - neolane
  ```

Vous devez relancer le service Adobe Campaign afin que les changements d&#39;environnement soient pris en compte.

Les commandes sont les suivantes :

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

  Pour plus d&#39;informations, consultez la section [Variables d&#39;environnement](#environment-variables).

* Paramétrage pour Adobe Campaign

  Pour finaliser l&#39;installation du client Oracle pour Adobe Campaign, vous devez créer un lien symbolique pour le fichier **.so** utilisé par Adobe Campaign.

  Pour cela, les commandes sont les suivantes :

  ```
  cd /usr/lib/oracle/10.2.0.4/client/lib
  ln -s libclntsh.so.10.1 libclntsh.so
  ```

En cas de problème, vérifiez que les packages répertoriés dans la documentation d’installation Oracle sont bien installés.

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

```sql
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

```sql
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

```sql
12:18:31 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:18:31 >   Stop requested for 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair', pid=29188, tid=-1224824320)...
12:18:31 >   Stop requested (pid=29188)
12:18:31 >   Web server stopped (pid=29188, tid=-1224824320)...
```

## Mot de passe de l&#39;identifiant internal {#password-for-the-internal-identifier}

Le serveur Adobe Campaign définit un identifiant (ou &#39;login&#39;) technique nommé **internal** qui possède tous les droits, sur toutes les instances. Après une installation récente, cet identifiant n&#39;a pas de mot de passe. Il est obligatoire d&#39;en définir un.

En savoir plus dans [cette section](../../installation/using/configuring-campaign-server.md#internal-identifier).
