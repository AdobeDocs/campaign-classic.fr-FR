---
title: Migration sous Linux pour Adobe Campaign v7
seo-title: Migration sous Linux pour Adobe Campaign v7
description: Migration sous Linux pour Adobe Campaign v7
seo-description: null
page-status-flag: never-activated
uuid: 47870ea4-b07b-4db7-8094-7a8b6f4b6936
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
discoiquuid: 8f6519e8-5c8d-4974-b193-a9f1cf78b3a3
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9f7cf3d530f141a661df5fcc8cbcf0bb4c8d3e89

---


# Migration sous Linux pour Adobe Campaign v7{#migrating-in-linux-for-adobe-campaign-v}

## Procédure générale {#general-procedure}

Les étapes de migration sous Linux sont les suivantes :

1. Arrêter les services : voir Arrêt [du service](#service-stop).
1. Enregistrez la base de données : voir [Sauvegarde de la base de données et installation](#back-up-the-database-and-the-existing-installation)existante.
1. Désinstallez les anciens packs de version d’Adobe Campaign : voir [Désinstallation des packs](#uninstalling-adobe-campaign-previous-version-packages)de version précédente d’Adobe Campaign.
1. Migrer la plateforme : voir [Déploiement d’Adobe Campaign v7](#deploying-adobe-campaign-v7).
1. Redémarrage du service : voir [Redémarrage des services](#re-starting-services).

## Arrêt des services {#service-stop}

Arrêtez d&#39;abord tous les processus accédant à la base de données, sur toutes les machines concernées.

1. Connectez-vous en tant que **root**.
1. Les serveurs utilisant le module de redirection (service **webmdl**) doivent être arrêtés. Pour Apache, exécutez la commande suivante :

   ```
   /etc/init.d/apache2 stop
   ```

1. Reconnectez-vous en tant que **root**.
1. Arrêtez les services de la version précédente d&#39;Adobe Campaign sur tous les serveurs.

   ```
   /etc/init.d/nlserver6 stop
   ```

   Si vous migrez à partir de la version v5.11, exécutez la commande suivante :

   ```
   /etc/init.d/nlserver5 stop
   ```

1. Sur chaque serveur, vérifiez que les services Adobe Campaign ont bien été arrêtés.

   ```
   ps waux | grep nlserver
   ```

   La liste des processus actifs ainsi que leur identifiant (PID) correspondant apparaît.

1. Si un ou plusieurs processus Adobe Campaign sont encore actifs ou bloqués au bout de quelques minutes, forcez leur arrêt.

   ```
   killall nlserver
   ```

1. Si certains processus sont toujours actifs au bout de quelques minutes, vous pouvez forcer leur fermeture à l&#39;aide de la commande :

   ```
   killall -9 nlserver
   ```

## Sauvegarde de la base et de l&#39;installation existante {#back-up-the-database-and-the-existing-installation}

La procédure dépend de votre version précédente d&#39;Adobe Campaign :

### Migration à partir d&#39;Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5-11}

1. Sauvegardez la base de données Adobe Campaign.
1. Connectez-vous en tant que **neolane** et sauvegardez le répertoire **nl5** à l&#39;aide de la commande suivante :

   ```
   su - neolane
   mv nl5 nl5.back
   ```

   >[!IMPORTANT]
   >
   >Par mesure de précaution, nous vous recommandons vivement de zipper le dossier **nl5.back**, et de le conserver à un autre emplacement que le serveur, sur un support sécurisé.

1. Modifiez le **fichier`<instance name>`config-** .xml **(dans le dossier** nl5.back **) afin d’éviter les** mta, wfserver, statetc. ******** à partir du démarrage automatique. Par exemple, remplacez **autoStart** par **_autoStart** (toujours comme **néolane**).

   ```
   <?xml version='1.0'?>
   <serverconf>
     <shared>
       <dataStore hosts="myServer*" lang="en_US">
         <dataSource name="default">
           <dbcnx encrypted="1" login="myLogin" password="myPassword"  provider="postgresql" server="myServer"/>
         </dataSource>
       </dataStore>
     </shared>
   
     <mta _autoStart="true" statServerAddress="myStatServer"/>
     <stat _autoStart="true"/>
     <wfserver _autoStart="true"/>
     <inMail _autoStart="true"/>
     <sms _autoStart="false"/>
   </serverconf>
   ```

### Migration à partir d&#39;Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6-02}

1. Sauvegardez la base de données Adobe Campaign.
1. Connectez-vous en tant que **neolane** et sauvegardez le répertoire **nl6** à l&#39;aide de la commande suivante :

   ```
   su - neolane
   mv nl6 nl6.back
   ```

   >[!IMPORTANT]
   >
   >Par mesure de précaution, nous vous recommandons vivement de zipper le dossier **nl6.back**, et de le conserver à un autre emplacement que le serveur, sur un support sécurisé.

1. Modifiez le **fichier`<instance name>`config-** .xml **(dans le dossier** nl6.back **) afin d’empêcher les** variables mta, wfserver, stat, etc. ******** à partir du démarrage automatique. Par exemple, remplacez **autoStart** par **_autoStart** (toujours sous **Adobe Campaign**).

   ```
   <?xml version='1.0'?>
   <serverconf>
     <shared>
       <dataStore hosts="myServer*" lang="en_US">
         <dataSource name="default">
           <dbcnx encrypted="1" login="myLogin" password="myPassword"  provider="postgresql" server="myServer"/>
         </dataSource>
       </dataStore>
     </shared>
   
     <mta _autoStart="true" statServerAddress="myStatServer"/>
     <stat _autoStart="true"/>
     <wfserver _autoStart="true"/>
     <inMail _autoStart="true"/>
     <sms _autoStart="false"/>
   </serverconf>
   ```

### Migration à partir d&#39;Adobe Campaign v6.1 {#migrating-from-adobe-campaign-v6-1}

1. Sauvegardez la base de données Adobe Campaign.
1. Connectez-vous en tant que **neolane** et sauvegardez le répertoire **nl6** à l&#39;aide de la commande suivante :

   ```
   su - neolane
   mv nl6 nl6.back
   ```

   >[!IMPORTANT]
   >
   >Par mesure de précaution, nous vous recommandons vivement de zipper le dossier **nl6.back**, et de le conserver à un autre emplacement que le serveur, sur un support sécurisé.

## Désinstallation des packages de version précédente d&#39;Adobe Campaign {#uninstalling-adobe-campaign-previous-version-packages}

La procédure dépend de votre version précédente d&#39;Adobe Campaign :

### Désinstallation des packages Adobe Campaign v5 {#uninstalling-adobe-campaign-v5-packages}

1. Connectez-vous en tant que **root**.
1. Identifiez les packages Adobe Campaign installés à l&#39;aide de la commande suivante.

   * Sous **Debian** :

      ```
      dpkg -l | grep nl
      ```

      La liste des packages installés apparaît :

      ```
      ii  nlserver5                       5762                     nlserver5-5762
      ii  nlthirdparty5                   5660                     nlthirdparty5-5660
      ```

   * Sous **Red Hat** :

      ```
      rpm -qa | grep nl
      ```

1. Désinstallez les packages Adobe Campaign v5.

   * Sous **Debian** :

      ```
      dpkg --purge nlserver5 nlthirdparty5
      ```

   * Sous **Red Hat** :

      ```
      rprm -ev nlserver5 nlthirdparty5
      ```

### Désinstallation des packages Adobe Campaign v6 {#uninstalling-adobe-campaign-v6-packages}

Cette section montre comment désinstaller les packages Adobe Campaign v6.02 ou v6.1.

1. Connectez-vous en tant que **root**.
1. Identifiez les packages Adobe Campaign installés à l&#39;aide de la commande suivante.

   * Sous **Debian** :

      ```
      dpkg -l | grep nl
      ```

      La liste des packages installés apparaît :

      ```
      ii  nlserver6                       XXXX                     nlserver6-XXXX
      ii  nlthirdparty6                   XXXX                     nlthirdparty6-XXXX
      ```

   * Sous **Red Hat** :

      ```
      rpm -qa | grep nl
      ```

1. Désinstallez les packages Adobe Campaign v6.

   * Sous **Debian** :

      ```
      dpkg --purge nlserver6 nlthirdparty6
      ```

   * Sous **Red Hat** :

      ```
      rprm -ev nlserver6 nlthirdparty6
      ```

## Déploiement d&#39;Adobe Campaign v7 {#deploying-adobe-campaign-v7}

La procédure dépend de votre version précédente d&#39;Adobe Campaign :

### Migration à partir d&#39;Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5_11-1}

Le déploiement d&#39;Adobe Campaign se déroule en deux parties :

* L&#39;installation des packages Adobe Campaign v7 : cette opération doit être effectuée sur chaque serveur.
* Le postupgrade : cette commande doit être lancée sur chaque instance.

Les étapes de déploiement d&#39;Adobe Campaign sont les suivantes :

1. Installez les packages Adobe Campaign v7 les plus récents à l&#39;aide de la commande suivante :

   * Sous **Debian** :

      ```
      dpkg -i nlserver6-XXXX-linux-2.6-intel.deb
      ```

   * Sous **Red Hat** :

      ```
      rpm -Uvh nlserver6-XXXX-0.x86_64.rpm
      ```
   >[!IMPORTANT]
   >
   >Il est impératif que l&#39;installation des packages réussisse pour passer à l&#39;étape suivante.

   >[!NOTE]
   >
   >Lors de la migration depuis une v5.11, Adobe Campaign est installé par défaut dans le répertoire : **/usr/local/neolane/nl6/.**
   >
   >Après l&#39;installation des packages, le message suivant apparaît : **&#39;WdbcTimeZone&#39; option is missing**. L&#39;apparition de ce message à ce stade est normale.

1. Pour mettre à disposition le programme d&#39;installation de la console cliente, copiez-le dans le répertoire d&#39;installation d&#39;Adobe Campaign :

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >Pour plus d&#39;informations sur l&#39;installation d&#39;Adobe Campaign sous Linux, consultez [cette section](../../installation/using/installing-campaign-standard-packages.md).

1. Modifiez le fichier **.bashrd** correspondant à l&#39;utilisateur **neolane**. Connectez-vous en tant que **neolane** et exécutez la commande suivante :

   ```
   su - neolane
   vim ~/.bashrc
   ```

   >[!NOTE]
   >
   >Lorsque vous vous connectez en tant que **neolane**, le message suivant apparaît : **nl5/env.sh : No such file or directory**. L&#39;apparition de ce message à ce stade est normale.

   A la fin du fichier, remplacez **nl5/env.sh** par **nl6/env.sh**.

1. Reconnectez-vous en tant que **root** et préparez l&#39;instance à sa première utilisation à l&#39;aide des commandes suivantes :

   ```
   /etc/init.d/nlserver6 start   
   Starting nlserver6: [  OK  ]
   ```

   ```
   /etc/init.d/nlserver6 stop
   Stopping nlserver6: [  OK  ]
   ```

   >[!NOTE]
   >
   >Ces commandes permettent de créer le système de fichiers interne d&#39;Adobe Campaign v6 : répertoire **conf** (avec les fichiers **config-default.xml** et
**serverConf.xml**), répertoire **var**.

1. Effectuez une copie (par écrasement), depuis le dossier de sauvegarde **nl5.back**, des fichiers de configuration et des sous-dossiers de chaque instance. Connectez-vous en tant que **neolane** et exécutez la commande suivante :

   >[!IMPORTANT]
   >
   >Pour la première des commandes ci-dessous, ne copiez pas le fichier **config-default.xml**.

   ```
   su - neolane
   
   cp nl5.back/conf/config-<instance name>.xml nl6/conf/
   cp nl5.back/customer.sh nl6/
   cp -r nl5.back/customers/* nl6/customers/
   cp -r nl5.back/var/* nl6/var/
   ```

1. Dans les fichiers Adobe Campaign v7 **serverConf.xml** et **config-default.xml** , appliquez les configurations spécifiques dont vous disposiez pour Adobe Campaign v5. Pour le fichier **serverConf.xml** , utilisez le fichier **nl5/conf/serverConf.xml.diff** .

   >[!NOTE]
   >
   >Lors du report des paramétrages Adobe Campaign v5 vers Adobe Campaign v7, assurez-vous que les chemins vers les répertoires physiques pointent bien vers Adobe Campaign v7 et pas Adobe Campaign v5.

1. La migration n&#39;étant pas une installation générique, vous devez forcer le redémarrage du service **trackinglogd**. Pour cela, ouvrez le fichier **nl6/conf/config-default.xml** et assurez-vous que le service **trackinglogd** est bien activé (uniquement sur le ou les serveurs de tracking/redirection) :

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!IMPORTANT]
   >
   >Si le service **trackinglogd** n&#39;est pas démarré sur le serveur de tracking, aucune information de tracking ne sera remontée.

1. Rechargez la configuration d&#39;Adobe Campaign v7 à l&#39;aide de la commande suivante :

   ```
   nlserver config -reload
   ```

1. Démarrez le processus de postupgrade à l&#39;aide de la commande suivante (toujours en tant que **neolane**) :

   ```
   su - neolane
   nlserver config -timezone:<time zone> -postupgrade -instance:<instance name>
   ```

   >[!IMPORTANT]
   >
   >Vous devez impérativement spécifier le fuseau horaire à utiliser comme référence au moment du postupgrade (à l&#39;aide de l&#39;option **-timezone**). Dans cet exemple, nous utilisons le fuseau horaire Europe/Paris : **-timezone:&quot;Europe/Paris&quot;**.

   >[!NOTE]
   >
   >Nous vous recommandons vivement de mettre à niveau votre base en &quot;multi-fuseau horaire&quot;. Pour plus d&#39;informations sur les options de fuseau horaire, consultez la section Fuseaux [](../../migration/using/general-configurations.md#time-zones) horaires.

>[!IMPORTANT]
>
>Ne redémarrez pas les services Adobe Campaign à ce stade. Des modifications doivent préalablement être effectuées sur Apache.

### Migration à partir d&#39;Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6_02-1}

Le déploiement d&#39;Adobe Campaign se déroule en deux parties :

* L&#39;installation des packages Adobe Campaign v7 : cette opération doit être effectuée sur chaque serveur.
* Le postupgrade : cette commande doit être lancée sur chaque instance.

Les étapes de déploiement d&#39;Adobe Campaign sont les suivantes :

1. Installez les packages Adobe Campaign v7 les plus récents à l&#39;aide de la commande suivante :

   * Sous **Debian** :

      ```
      dpkg -i nlserver6-XXXX-amd64_debX.deb
      ```

   * Sous **Red Hat** :

      ```
      rpm -Uvh nlserver6-XXXX-x86_64_rhX.rpm
      ```
   >[!IMPORTANT]
   >
   >Il est impératif que l&#39;installation des packages réussisse pour passer à l&#39;étape suivante.

   >[!NOTE]
   >
   >Adobe Campaign v7 est installé par défaut dans le même répertoire qu&#39;Adobe Campaign v6.02 : **/usr/local/neolane/nl6/**.

1. Pour mettre à disposition le programme d&#39;installation de la console cliente, copiez-le dans le répertoire d&#39;installation d&#39;Adobe Campaign :

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >Pour plus d&#39;informations sur l&#39;installation d&#39;Adobe Campaign sous Linux, consultez [cette section](../../installation/using/installing-campaign-standard-packages.md).

1. La migration n&#39;étant pas une installation générique, vous devez forcer le redémarrage du service **trackinglogd**. Pour cela, ouvrez le fichier **nl6/conf/config-default.xml** et assurez-vous que le service **trackinglogd** est bien activé (uniquement sur le ou les serveurs de tracking/redirection) :

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!IMPORTANT]
   >
   >Si le service **trackinglogd** n&#39;est pas démarré sur le serveur de tracking, aucune information de tracking ne sera remontée.

1. Accédez au dossier de sauvegarde **nl6.back** et copiez (écrasez) les fichiers de configuration et les sous-dossiers de chaque instance. Connectez-vous en tant que **néolane** et exécutez la commande suivante :

   ```
   su - neolane
   
   cp nl6.back/conf/config*.xml nl6/conf/
   cp nl6.back/customer.sh nl6/
   cp -r nl6.back/customers/* nl6/customers/
   cp -r nl6.back/var/* nl6/var/
   ```

1. Rechargez la configuration d&#39;Adobe Campaign v7 à l&#39;aide de la commande suivante :

   ```
   nlserver config -reload
   ```

1. Démarrez le processus de postupgrade à l&#39;aide de la commande suivante (toujours en tant que **neolane**) :

   ```
   su - neolane
   nlserver config -postupgrade -instance:<instance name>
   ```

   >[!NOTE]
   >
   >Le mode &quot;multi-fuseau&quot; n&#39;était disponible que dans la version 6.02 pour les moteurs de base de données PostgreSQL. Il est maintenant disponible quelle que soit la version du moteur de base de données utilisée.Nous vous recommandons vivement de mettre à niveau votre base en &quot;multi-fuseau horaire&quot;. Pour plus d&#39;informations sur les options de fuseau horaire, consultez la section Fuseaux [](../../migration/using/general-configurations.md#time-zones) horaires.

### Migration à partir d&#39;Adobe Campaign v6.1 {#migrating-from-adobe-campaign-v6_1-1}

Le déploiement d&#39;Adobe Campaign se déroule en deux parties :

* L&#39;installation des packages Adobe Campaign v7 : cette opération doit être effectuée sur chaque serveur.
* Le postupgrade : cette commande doit être lancée sur chaque instance.

Les étapes de déploiement d&#39;Adobe Campaign sont les suivantes :

1. Installez les packages Adobe Campaign v7 les plus récents à l&#39;aide de la commande suivante :

   * Sous **Debian** :

      ```
      dpkg -i nlserver6-XXXX-amd64_debX.deb
      ```

   * Sous **Red Hat** :

      ```
      rpm -Uvh nlserver6-XXXX-x86_64_rhX.rpm
      ```
   >[!IMPORTANT]
   >
   >Il est impératif que l&#39;installation des packages réussisse pour passer à l&#39;étape suivante.

   >[!NOTE]
   >
   >Adobe Campaign v7 est installé par défaut dans le répertoire : **/usr/local/neolane/nl6/.**

1. Pour mettre à disposition le programme d&#39;installation de la console cliente, copiez-le dans le répertoire d&#39;installation d&#39;Adobe Campaign :

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >Pour plus d&#39;informations sur l&#39;installation d&#39;Adobe Campaign sous Linux, consultez [cette section](../../installation/using/installing-campaign-standard-packages.md).

1. Accédez au dossier de sauvegarde **nl6.back** et copiez (écrasez) les fichiers de configuration et les sous-dossiers de chaque instance. Connectez-vous en tant que **néolane** et exécutez la commande suivante :

   ```
   su - neolane
   
   cp nl6.back/conf/config*.xml nl6/conf/
   cp nl6.back/customer.sh nl6/
   cp -r nl6.back/customers/* nl6/customers/
   cp -r nl6.back/var/* nl6/var/
   ```

1. Rechargez la configuration d&#39;Adobe Campaign v7 à l&#39;aide de la commande suivante :

   ```
   nlserver config -reload
   ```

1. Démarrez le processus de postupgrade à l&#39;aide de la commande suivante (toujours en tant que **neolane**) :

   ```
   su - neolane
   nlserver config -postupgrade -instance:<instance name>
   ```

## Migration du serveur de redirection (Apache) {#migrating-the-redirection-server--apache-}

>[!NOTE]
>
>Cette section s&#39;applique uniquement lors de la migration à partir d&#39;Adobe Campaign v5.11.

A ce stade, Apache doit être arrêté. Reportez-vous à : Arrêt [du service](#service-stop).

1. Connectez-vous en tant que **root**.
1. Modifiez les variables d&#39;environnement d&#39;Apache afin de les faire pointer vers le répertoire **nl6**.

   * Sous **Debian** :

      ```
      vi /etc/apache2/envvars
      ```

   * Sous **Red Hat** :

      ```
      vi /usr/local/apache2/bin/envvars
      ```

1. Exécutez ensuite les commandes suivantes :

   * Sous **Debian** :

      Dans le fichier **nlsrv.load**, remplacez toutes les occurrences de **nl5** par **nl6**.

      ```
      vi /etc/apache2/mods-available/nlsrv.load
      ```

      Supprimez le lien du fichier **nlsrv.conf** et recréez-le.

      ```
      rm /etc/apache2/mods-available/nlsrv.conf 
      ln -s /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf /etc/apache2/
      mods-available/nlsrv.conf
      ```

   * Sous **Red Hat** :

      Dans le répertoire **/usr/local/apache2/conf**, éditez le fichier **httpd.conf** et remplacez **nl5** par **nl6** dans les lignes ci-dessous.

      Sous **RHEL 7 / Debian 8** :

      ```
      LoadModule requesthandler24_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
      Include /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf
      ```

1. Dans le fichier **alias.conf**, les occurrences de **nl5** doivent être remplacées par **nl6**. Sous Debian, la commande est la suivante :

   ```
   vi /etc/apache2/mods-available/alias.conf
   ```

## Zones de sécurité {#security-zones}

Si vous effectuez une migration depuis la version 6.02 ou une version antérieure, vous devez configurer vos zones de sécurité avant de démarrer les services. For more information, refer to [Security](../../migration/using/general-configurations.md#security).

## Redémarrage des services {#re-starting-services}

La procédure dépend de votre version précédente d&#39;Adobe Campaign :

### Migration à partir d&#39;Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5_11-2}

In the **config-`<instance name>`.xml** files, reactivate the automatic startup of the **mta**, **wfserver**, **stat**, etc. services.

```
<?xml version='1.0'?>
<serverconf>
  <shared>
    <dataStore hosts="myServer*" lang="en_US">
      <dataSource name="default">
        <dbcnx encrypted="1" login="myLogin" password="myPassword"  provider="postgresql" server="myServer"/>
      </dataSource>
    </dataStore>
  </shared>

  <mta autoStart="true" statServerAddress="localhost"/>
  <stat autoStart="true"/>
  <wfserver autoStart="true"/>
  <inMail autoStart="true"/>
  <sms autoStart="false"/>
</serverconf>
```

Sur chacun des serveurs suivants, démarrez Apache puis les services Adobe Campaign :

1. Serveur de tracking/redirection.
1. Serveur de mid-sourcing.
1. Serveur marketing.

Before going on to the next step, run a full test of the new installation, make sure there are no regressions and that everything works by following all the recommendations in the [General configurations](../../migration/using/general-configurations.md) section.

### Migration à partir d&#39;Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6_02-2}

In the **config-`<instance name>`.xml** files, reactivate the automatic startup of the **mta**, **wfserver**, **stat**, etc. services.

```
<?xml version='1.0'?>
<serverconf>
  <shared>
    <dataStore hosts="myServer*" lang="en_US">
      <dataSource name="default">
        <dbcnx encrypted="1" login="myLogin" password="myPassword"  provider="postgresql" server="myServer"/>
      </dataSource>
    </dataStore>
  </shared>

  <mta autoStart="true" statServerAddress="myStatServer"/>
  <stat autoStart="true"/>
  <wfserver autoStart="true"/>
  <inMail autoStart="true"/>
  <sms autoStart="false"/>
</serverconf>
```

Sur chacun des serveurs suivants, démarrez Apache puis les services Adobe Campaign :

1. Serveur de tracking/redirection.
1. Serveur de mid-sourcing.
1. Serveur marketing.

Fully test the new installation, check that it does not regress and make sure that everything is working correctly by following all the recommendations in the [General configurations](../../migration/using/general-configurations.md) section.

### Migration à partir d&#39;Adobe Campaign v6.1 {#migrating-from-adobe-campaign-v6_1-2}

Sur chacun des serveurs suivants, démarrez Apache puis les services Adobe Campaign :

1. Serveur de tracking/redirection.
1. Serveur de mid-sourcing.
1. Serveur marketing.

Fully test the new installation, check that it does not regress and make sure that everything is working correctly by following all the recommendations in the [General configurations](../../migration/using/general-configurations.md) section.

## Suppression et nettoyage d&#39;Adobe Campaign v5 {#deleting-and-cleansing-adobe-campaign-v5}

>[!NOTE]
>
>Cette section s&#39;applique uniquement lors de la migration à partir d&#39;Adobe Campaign v5.11.

Avant de supprimer et nettoyer l&#39;installation d&#39;Adobe Campaign v5, il est impératif de suivre les recommandations ci-dessous :

* Effectuez une validation complète de la nouvelle installation par les équipes fonctionnelles.
* Ne procédez à la désinstallation d&#39;Adobe Campaign v5 qu&#39;une fois que vous êtes certain qu&#39;un retour arrière n&#39;est pas nécessaire.

Supprimez le répertoire **nl5.back**. Connectez-vous en tant que **neolane** et exécutez la commande suivante :

```
su - neolane
rm -rf nl5.back
```

Redémarrez le serveur.
