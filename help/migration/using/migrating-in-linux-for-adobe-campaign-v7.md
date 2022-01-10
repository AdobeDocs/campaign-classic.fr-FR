---
product: campaign
title: Migration d’une plateforme Linux vers Adobe Campaign v7
description: Découvrez comment migrer une plateforme Linux vers Adobe Campaign v7
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
exl-id: 9dc0699c-0fbf-4f8e-81f7-8ca3d7e98798
source-git-commit: 63aca25a8d1ae24ef83849b35a44d1b37cfa5e96
workflow-type: tm+mt
source-wordcount: '1858'
ht-degree: 93%

---

# Migration d&#39;une plateforme Linux vers Campaign v7{#migrating-in-linux-for-adobe-campaign-v}

![](../../assets/v7-only.svg)

Les étapes de migration sous Linux sont les suivantes :

1. Arrêter tous les services - [En savoir plus](#service-stop).
1. Enregistrer la base de données - [En savoir plus](#back-up-the-database).
1. Désinstallation des packages de version précédente d’Adobe Campaign - [En savoir plus](#uninstalling-adobe-campaign-previous-version-packages).
1. Migration de la plateforme - [En savoir plus](#deploying-adobe-campaign-v7).
1. Redémarrage du service - [En savoir plus](#re-starting-services).

## Arrêt des services {#service-stop}

Arrêtez d&#39;abord tous les processus accédant à la base de données, sur toutes les machines concernées.

1. Connectez-vous en tant que **root**.
1. Les serveurs utilisant le module de redirection (service **webmdl**) doivent être arrêtés. Pour Apache, exécutez la commande suivante :

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

1. Si un ou plusieurs processus Adobe Campaign sont encore actifs ou bloqués au bout de quelques minutes, forcez leur arrêt.

   ```
   killall nlserver
   ```

1. Si certains processus sont toujours actifs au bout de quelques minutes, vous pouvez forcer leur fermeture à l&#39;aide de la commande :

   ```
   killall -9 nlserver
   ```

## Sauvegarde de votre base de données {#back-up-the-database}

La procédure dépend de votre version précédente d&#39;Adobe Campaign :

### Pour Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5-11}

1. Sauvegardez la base de données Adobe Campaign.
1. Connectez-vous en tant que **neolane** et sauvegardez le répertoire **nl5** à l&#39;aide de la commande suivante :

   ```
   su - neolane
   mv nl5 nl5.back
   ```

   >[!IMPORTANT]
   >
   >Par mesure de précaution, nous vous recommandons vivement de zipper le dossier **nl5.back**, et de le conserver à un autre emplacement que le serveur, sur un support sécurisé.

1. Éditez le fichier **config-`<instance name>`.xml** (dans le dossier **nl5.back**), pour éviter le démarrage automatique des services **mta**, **wfserver**, **stat**, etc. Par exemple, remplacez **autoStart** par **_autoStart** (comme pour **neolane**).

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

### Pour Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6-02}

1. Sauvegardez la base de données Adobe Campaign.
1. Connectez-vous en tant que **neolane** et sauvegardez le répertoire **nl6** à l&#39;aide de la commande suivante :

   ```
   su - neolane
   mv nl6 nl6.back
   ```

   >[!IMPORTANT]
   >
   >Par mesure de précaution, nous vous recommandons vivement de zipper le dossier **nl6.back**, et de le conserver à un autre emplacement que le serveur, sur un support sécurisé.

1. Éditez le fichier **config-`<instance name>`.xml** (dans le dossier **nl6.back**), pour éviter le démarrage automatique des services **mta**, **wfserver**, **stat**, etc. Par exemple, remplacez **autoStart** par **_autoStart** (comme pour **Adobe Campaign**).

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

### Pour Adobe Campaign v6.1 {#migrating-from-adobe-campaign-v6-1}

1. Sauvegardez la base de données Adobe Campaign.
1. Connectez-vous en tant que **neolane** et sauvegardez le répertoire **nl6** à l&#39;aide de la commande suivante :

   ```
   su - neolane
   mv nl6 nl6.back
   ```

   >[!IMPORTANT]
   >
   >Par mesure de précaution, nous vous recommandons vivement de zipper le dossier **nl6.back**, et de le conserver à un autre emplacement que le serveur, sur un support sécurisé.

## Désinstallation des packages de version précédente d’Adobe Campaign {#uninstalling-adobe-campaign-previous-version-packages}

La procédure dépend de votre version précédente d&#39;Adobe Campaign :

### Pour les packages v5 {#uninstalling-adobe-campaign-v5-packages}

1. Connectez-vous en tant que **root**.
1. Identifiez les packages Adobe Campaign installés à l&#39;aide de la commande suivante.

   * Sous **Debian** :

      ```
      dpkg -l | grep nl
      ```

      La liste des packages installés apparaît :

      ```
      ii  nlserver5                       5762                     nlserver5-5762
      ii  nlthirdparty5                   5660                     nlthirdparty5-5660
      ```

   * Sous **Red Hat** :

      ```
      rpm -qa | grep nl
      ```

1. Désinstallez les packages Adobe Campaign v5.

   * Sous **Debian** :

      ```
      dpkg --purge nlserver5 nlthirdparty5
      ```

   * Sous **Red Hat** :

      ```
      rprm -ev nlserver5 nlthirdparty5
      ```

### Pour les packages v6 {#uninstalling-adobe-campaign-v6-packages}

Cette section montre comment désinstaller les packages Adobe Campaign v6.02 ou v6.1.

1. Connectez-vous en tant que **root**.
1. Identifiez les packages Adobe Campaign installés à l&#39;aide de la commande suivante.

   * Sous **Debian** :

      ```
      dpkg -l | grep nl
      ```

      La liste des packages installés apparaît :

      ```
      ii  nlserver6                       XXXX                     nlserver6-XXXX
      ii  nlthirdparty6                   XXXX                     nlthirdparty6-XXXX
      ```

   * Sous **Red Hat** :

      ```
      rpm -qa | grep nl
      ```

1. Désinstallez les packages Adobe Campaign v6.

   * Sous **Debian** :

      ```
      dpkg --purge nlserver6 nlthirdparty6
      ```

   * Sous **Red Hat** :

      ```
      rprm -ev nlserver6 nlthirdparty6
      ```

## Déploiement d’Adobe Campaign v7 {#deploying-adobe-campaign-v7}

La procédure dépend de votre version précédente d&#39;Adobe Campaign :

### Depuis Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5_11-1}

Le déploiement d&#39;Adobe Campaign se déroule en deux parties :

* L&#39;installation des packages Adobe Campaign v7 : cette opération doit être effectuée sur chaque serveur.
* Le postupgrade : cette commande doit être lancée sur chaque instance.

Les étapes de déploiement d&#39;Adobe Campaign sont les suivantes :

1. Installez les packages Adobe Campaign v7 les plus récents à l&#39;aide de la commande suivante :

   * Sous **Debian** :

      ```
      dpkg -i nlserver6-XXXX-linux-2.6-intel.deb
      ```

   * Sous **Red Hat** :

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
   >Pour plus d&#39;informations sur l&#39;installation d&#39;Adobe Campaign sous Linux, consultez [cette section](../../installation/using/installing-campaign-standard-packages.md).

1. Modifiez le fichier **.bashrd** correspondant à l&#39;utilisateur **neolane**. Connectez-vous en tant que **neolane** et exécutez la commande suivante :

   ```
   su - neolane
   vim ~/.bashrc
   ```

   >[!NOTE]
   >
   >Lorsque vous vous connectez en tant que **neolane**, le message suivant apparaît : **nl5/env.sh : No such file or directory**. L&#39;apparition de ce message à ce stade est normale.

   A la fin du fichier, remplacez **nl5/env.sh** par **nl6/env.sh**.

1. Reconnectez-vous en tant que **root** et préparez l&#39;instance à sa première utilisation à l&#39;aide des commandes suivantes :

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
   >Ces commandes permettent de créer le système de fichiers interne d&#39;Adobe Campaign v6 : répertoire **conf** (avec les fichiers **config-default.xml** et **serverConf.xml**), répertoire **var**.

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

1. Dans les fichiers **serverConf.xml** et **config-default.xml** d&#39;Adobe Campaign v7, appliquez les configurations spécifiques dont vous disposiez pour Adobe Campaign v5. Pour le fichier **serverConf.xml**, utilisez le fichier **nl5/conf/serverConf.xml.diff**.

   >[!NOTE]
   >
   >Lors du report des paramétrages Adobe Campaign v5 vers Adobe Campaign v7, assurez-vous que les chemins vers les répertoires physiques pointent bien vers Adobe Campaign v7 et pas Adobe Campaign v5.

1. La migration n&#39;étant pas une installation générique, vous devez forcer le redémarrage du service **trackinglogd**. Pour cela, ouvrez le fichier **nl6/conf/config-default.xml** et assurez-vous que le service **trackinglogd** est bien activé (uniquement sur le ou les serveurs de tracking/redirection) :

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!IMPORTANT]
   >
   >Si le service **trackinglogd** n&#39;est pas démarré sur le serveur de tracking, aucune information de tracking ne sera remontée.

1. Rechargez la configuration d&#39;Adobe Campaign v7 à l&#39;aide de la commande suivante :

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
   >Nous vous recommandons vivement de mettre à niveau votre base en mode « multi timezone ». Pour plus d&#39;informations à propos des options de fuseaux horaires, consultez la section [Fuseaux horaires](../../migration/using/general-configurations.md#time-zones).

>[!IMPORTANT]
>
>Ne redémarrez pas les services Adobe Campaign à ce stade. Des modifications doivent préalablement être effectuées sur Apache.

### Depuis Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6_02-1}

Le déploiement d&#39;Adobe Campaign se déroule en deux parties :

* L&#39;installation des packages Adobe Campaign v7 : cette opération doit être effectuée sur chaque serveur.
* Le postupgrade : cette commande doit être lancée sur chaque instance.

Les étapes de déploiement d&#39;Adobe Campaign sont les suivantes :

1. Installez les packages Adobe Campaign v7 les plus récents à l&#39;aide de la commande suivante :

   * Sous **Debian** :

      ```
      dpkg -i nlserver6-XXXX-amd64_debX.deb
      ```

   * Sous **Red Hat** :

      ```
      rpm -Uvh nlserver6-XXXX-x86_64_rhX.rpm
      ```
   >[!IMPORTANT]
   >
   >Il est impératif que l&#39;installation des packages réussisse pour passer à l&#39;étape suivante.

   >[!NOTE]
   >
   >Adobe Campaign v7 est installé par défaut dans le même répertoire qu&#39;Adobe Campaign v6.02 : **/usr/local/neolane/nl6/**.

1. Pour mettre à disposition le programme d&#39;installation de la console cliente, copiez-le dans le répertoire d&#39;installation d&#39;Adobe Campaign :

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >Pour plus d&#39;informations sur l&#39;installation d&#39;Adobe Campaign sous Linux, consultez [cette section](../../installation/using/installing-campaign-standard-packages.md).

1. La migration n&#39;étant pas une installation générique, vous devez forcer le redémarrage du service **trackinglogd**. Pour cela, ouvrez le fichier **nl6/conf/config-default.xml** et assurez-vous que le service **trackinglogd** est bien activé (uniquement sur le ou les serveurs de tracking/redirection) :

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!IMPORTANT]
   >
   >Si le service **trackinglogd** n&#39;est pas démarré sur le serveur de tracking, aucune information de tracking ne sera remontée.

1. Accédez au dossier de sauvegarde **nl6.back** et copiez (écrasez) les fichiers de configuration et les sous-dossiers de chaque instance. Connectez-vous en tant que **neolane** et exécutez la commande suivante :

   ```
   su - neolane
   
   cp nl6.back/conf/config*.xml nl6/conf/
   cp nl6.back/customer.sh nl6/
   cp -r nl6.back/customers/* nl6/customers/
   cp -r nl6.back/var/* nl6/var/
   ```

1. Rechargez la configuration d&#39;Adobe Campaign v7 à l&#39;aide de la commande suivante :

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
   >Le mode « multi timezone » n&#39;était disponible, en v6.02, que pour les moteurs de base de données PostgreSQL. Il est à présent proposé quelle que soit la version de votre moteur de base. Nous vous recommandons fortement de transformer votre base en base « multi timezone ». Pour plus d&#39;informations à propos des options de fuseaux horaires, consultez la section [Fuseaux horaires](../../migration/using/general-configurations.md#time-zones).

### Depuis Adobe Campaign v6.1 {#migrating-from-adobe-campaign-v6_1-1}

Le déploiement d&#39;Adobe Campaign se déroule en deux parties :

* L&#39;installation des packages Adobe Campaign v7 : cette opération doit être effectuée sur chaque serveur.
* Le postupgrade : cette commande doit être lancée sur chaque instance.

Les étapes de déploiement d&#39;Adobe Campaign sont les suivantes :

1. Installez les packages Adobe Campaign v7 les plus récents à l&#39;aide de la commande suivante :

   * Sous **Debian** :

      ```
      dpkg -i nlserver6-XXXX-amd64_debX.deb
      ```

   * Sous **Red Hat** :

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
   >Pour plus d&#39;informations sur l&#39;installation d&#39;Adobe Campaign sous Linux, consultez [cette section](../../installation/using/installing-campaign-standard-packages.md).

1. Accédez au dossier de sauvegarde **nl6.back** et copiez (écrasez) les fichiers de configuration et les sous-dossiers de chaque instance. Connectez-vous en tant que **neolane** et exécutez la commande suivante :

   ```
   su - neolane
   
   cp nl6.back/conf/config*.xml nl6/conf/
   cp nl6.back/customer.sh nl6/
   cp -r nl6.back/customers/* nl6/customers/
   cp -r nl6.back/var/* nl6/var/
   ```

1. Rechargez la configuration d&#39;Adobe Campaign v7 à l&#39;aide de la commande suivante :

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

À ce stade, Apache doit être arrêté. Pour plus d&#39;informations, consultez la section [Arrêt des services](#service-stop).

1. Connectez-vous en tant que **root**.
1. Modifiez les variables d&#39;environnement d&#39;Apache afin de les faire pointer vers le répertoire **nl6**.

   * Sous **Debian** :

      ```
      vi /etc/apache2/envvars
      ```

   * Sous **Red Hat** :

      ```
      vi /usr/local/apache2/bin/envvars
      ```

1. Exécutez ensuite les commandes suivantes :

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

   * Sous **Red Hat** :

      Dans le répertoire **/usr/local/apache2/conf**, éditez le fichier **httpd.conf** et remplacez **nl5** par **nl6** dans les lignes ci-dessous.

      Sous **RHEL 7 / Debian 8** :

      ```
      LoadModule requesthandler24_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
      Include /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf
      ```

1. Dans le fichier **alias.conf**, les occurrences de **nl5** doivent être remplacées par **nl6**. Sous Debian, la commande est la suivante :

   ```
   vi /etc/apache2/mods-available/alias.conf
   ```

## Zones de sécurité {#security-zones}

Si vous migrez depuis une v6.02 ou antérieure, vous devez paramétrer vos zones de sécurité avant de redémarrer les services. Voir à ce sujet la section [Sécurité](../../migration/using/general-configurations.md#security).

## Redémarrage des services {#re-starting-services}

La procédure dépend de votre version précédente d&#39;Adobe Campaign :

### Pour Adobe Campaign v5 {#migrating-from-adobe-campaign-v5_11-2}

Dans les fichiers **config-`<instance name>`.xml**, réactivez le démarrage automatique des services **mta**, **wfserver**, **stat**, etc. 

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

Avant de passer à l&#39;étape suivante, testez complètement la nouvelle installation, validez la non-régression et assurez-vous que tout est fonctionnel, en suivant toutes les recommandations données dans la section [Paramétrages généraux](../../migration/using/general-configurations.md).

### Pour Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6_02-2}

Dans les fichiers **config-`<instance name>`.xml**, réactivez le démarrage automatique des services **mta**, **wfserver**, **stat**, etc. 

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

Testez complètement la nouvelle installation, validez la non-régression et assurez-vous que tout est fonctionnel, en suivant toutes les recommandations de la section [Paramétrages généraux](../../migration/using/general-configurations.md).

### Pour Adobe Campaign v6.1 {#migrating-from-adobe-campaign-v6_1-2}

Sur chacun des serveurs suivants, démarrez Apache puis les services Adobe Campaign :

1. Serveur de tracking/redirection.
1. Serveur de mid-sourcing.
1. Serveur marketing.

Testez complètement la nouvelle installation, validez la non-régression et assurez-vous que tout est fonctionnel, en suivant toutes les recommandations de la section [Paramétrages généraux](../../migration/using/general-configurations.md).

## Suppression de la version précédente d’Adobe Campaign {#deleting-and-cleansing-adobe-campaign-v5}

>[!NOTE]
>
>Cette section s&#39;applique uniquement lors de la migration à partir d&#39;Adobe Campaign v5.11.

Avant de supprimer et nettoyer l&#39;installation d&#39;Adobe Campaign v5, il est impératif de suivre les recommandations ci-dessous :

* Effectuez une validation complète de la nouvelle installation par les équipes fonctionnelles.
* Ne procédez à la désinstallation d&#39;Adobe Campaign v5 qu&#39;une fois que vous êtes certain qu&#39;un retour arrière n&#39;est pas nécessaire.

Supprimez le répertoire **nl5.back**. Connectez-vous en tant que **neolane** et exécutez la commande suivante :

```
su - neolane
rm -rf nl5.back
```

Redémarrez le serveur.
