---
title: Déploiement Stand-alone
seo-title: Déploiement Stand-alone
description: Déploiement Stand-alone
seo-description: null
page-status-flag: never-activated
uuid: 48ce793e-cb9f-4102-898f-758512cb9bf2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: deployment-types-
discoiquuid: 9834638f-a8bb-4969-9f8d-99b8d9fdb1ca
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 6b631f8456ad1f61cec1630334d76752f6af9866

---


# Déploiement Stand-alone{#standalone-deployment}

Cette configuration regroupe tous les composants sur une seule machine :

* processus applicatif (web),
* processus de diffusion (mta),
* processus de redirection (tracking),
* processus de workflow et tâches planifiées (wfserver),
* processus des mails rebonds (inMail),
* processus de statistiques (stat).

La communication générale entre les processus est réalisée conformément au schéma suivant :

![](assets/s_900_ncs_install_standaloneconfig.png)

Ce type de configuration est parfaitement adapté lorsque les listes gérées contiennent moins de 100 000 destinataires, et avec, par exemple, les couches logicielles suivantes :

* Linux,
* Apache,
* PostgreSQL,
* Qmail.

Lorsque le volume s&#39;accroît, une variante de cette architecture déporte le serveur de base de données sur une autre machine, pour de meilleures performances.

>[!NOTE]
>
>Un serveur de base de données préexistant peut être utilisé, sous réserve qu&#39;il dispose de ressources suffisantes.

## Caractéristiques {#features}

### Avantages {#advantages}

* Totalement stand-alone et coût de configuration faible (aucune licence payante si l&#39;on utilise les composants logiciels, tous Open Source, listés ci-dessus).
* Installation et configuration réseau simplifiées.

### Inconvénients {#disadvantages}

* Une machine critique en cas d&#39;incident.
* Débit limité pendant les diffusions des messages (selon notre expérience, de l&#39;ordre de quelques dizaines de milliers de mails par heure).
* Ralentissement possible de l&#39;application pendant les diffusions.
* Le serveur applicatif doit être accessible depuis l&#39;extérieur (en étant placé dans la DMZ, par exemple), puisqu&#39;il accueille le serveur de redirection.

## Etapes d&#39;installation et de configuration {#installation-and-configuration-steps}

### Prérequis {#prerequisites}

* JDK,
* Serveur Web (IIS, Apache),
* Accès à un serveur de base de données,
* Boîte pour les mails rebonds accessible en POP3,
* Création de deux alias DNS :

   * un premier alias exposé au grand public pour le tracking et pointant vers la machine sur son IP publique ;
   * un deuxième alias exposé aux utilisateurs métier pour l&#39;accès console et pointant vers la même machine.

* Pare-feu configuré pour ouvrir les ports STMP (25), DNS (53), HTTP (80), HTTPS (443), SQL (1521 pour Oracle, 5432 pour PostgreSQL, etc.). Pour plus d&#39;informations, reportez-vous à la section Configuration [du](../../installation/using/network-configuration.md)réseau.

Dans les exemples présentés ci-dessous, les paramètres de l&#39;instance sont les suivants :

* Nom de l&#39;instance : **demo**
* DNS mask: **console.campaign.net*** (only for client console connections and for reports)
* Database: **campaign:demo@dbsrv**

### Installer et configurer (mono-machine) {#installing-and-configuring--single-machine-}

Les étapes sont les suivantes :

1. Respectez la procédure d&#39;installation du serveur Adobe Campaign : package **nlserver** sous Linux ou **setup.exe** sous Windows.

   Pour plus d&#39;informations, reportez-vous aux [Conditions préalables à l&#39;installation de Campaign sous Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md) (Linux) et [Conditions préalables à l&#39;installation de Campaign sous Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) (Windows).

1. Une fois l&#39;installation du serveur Adobe Campaign terminée, démarrez le serveur applicatif (web) avec la commande **nlserver web -tomcat** (le module web permet de lancer Tomcat en mode serveur web autonome en écoute sur le port 8080) et vérifiez que Tomcat démarre correctement :

   ```
   12:08:18 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   12:08:18 >   Starting Web server module (pid=28505, tid=-1225184768)...
   12:08:18 >   Tomcat started
   12:08:18 >   Server started
   ```

   >[!NOTE]
   >
   >The first time the Web module is executed it creates the **config-default.xml** and **serverConf.xml** files in the **conf** directory under the installation folder. Tous les paramètres disponibles dans le fichier **serverConf.xml** sont répertoriés dans cette [section](../../installation/using/the-server-configuration-file.md).

   Appuyez sur **Ctrl+C** pour arrêter le serveur.

   Voir à ce propos les sections suivantes :

   * Pour Linux : [Premier démarrage du serveur](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server),
   * Pour Windows : [Premier démarrage du serveur](../../installation/using/installing-the-server.md#first-start-up-of-the-server).

1. Changez le mot de passe **internal** à partir de la commande :

   ```
   nlserver config -internalpassword
   ```

   For more on this, refer to [Internal identifier](../../installation/using/campaign-server-configuration.md#internal-identifier).

1. Créez l’instance de **démonstration** avec les masques DNS pour le suivi (dans ce cas, **tracking.campaign.net**) et l’accès aux consoles client (dans ce cas, **console.campaign.net**). Il existe deux façons de procéder :

   * Créer l&#39;instance via la console :

      ![](assets/install_create_new_connexion.png)

      Pour plus d’informations, reportez-vous à la section [Création d’une instance et connexion](../../installation/using/creating-an-instance-and-logging-on.md).

      or

   * Créer l&#39;instance en ligne de commande :

      ```
      nlserver config -addinstance:demo/tracking.campaign.net*,console.campaign.net*
      ```

      For more on this, refer to [Creating an instance](../../installation/using/command-lines.md#creating-an-instance).

1. Modifiez le fichier **config-demo.xml** (créé à l’étape précédente en regard du fichier **config-default.xml**) et assurez-vous que les processus **mta** (diffusion), **wfserver (flux de travail), inMail (messages de rebonds) etstat(statistiques) sont activés.********** Configurez ensuite l’adresse du serveur de statistiques :

   ```
   <?xml version='1.0'?>
   <serverconf>  
     <shared>    
       <!-- add lang="eng" to dataStore to force English for the instance -->    
       <dataStore hosts="tracking.campaign.net*,console.campaign.net*">      
         <mapping logical="*" physical="default"/>    
       </dataStore>  </shared>  
       <mta autoStart="true" statServerAddress="localhost"/>
       <wfserver autoStart="true"/>  
       <inMail autoStart="true"/>  
       <sms autoStart="false"/>  
       <listProtect autoStart="false"/>
   </serverconf>
   ```

   For more on this, refer to [Enabling processes](../../installation/using/campaign-server-configuration.md#enabling-processes).

1. Edit the **serverConf.xml** file and specify the delivery domain, then specify the IP (or host) addresses of the DNS servers used by the MTA module to answer MX type DNS queries.

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >Le paramètre **nameServers** n&#39;est utile que sous Windows.

   For more on this, refer to [Campaign server configuration](../../installation/using/campaign-server-configuration.md).

1. Copiez le programme de configuration de la console client (**setup-client-7.XX**, **YYYY.exe** pour v7 ou **setup-client-6.XX**, **YYY.exe pour v6.1) dans le dossier /datakit/nl/eng/jsp.******

   Voir à ce propos les sections suivantes :

   * Pour Linux : Disponibilité de la console [client pour Linux](../../installation/using/client-console-availability-for-linux.md)
   * Pour Windows : Disponibilité de la console [client pour Windows](../../installation/using/client-console-availability-for-windows.md)

1. Suivez la procédure d&#39;intégration du serveur Web (IIS, Apache) décrite dans les sections suivantes :

   * Pour Linux : [Intégration à un serveur Web pour Linux](../../installation/using/integration-into-a-web-server-for-linux.md)
   * Pour Windows : [Intégration à un serveur Web pour Windows](../../installation/using/integration-into-a-web-server-for-windows.md)

1. Démarrez le site web et testez la redirection à partir de l&#39;URL : https://tracking.campaign.net/r/test.

   Le navigateur doit afficher le message suivant :

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="localhost"/>
   ```

   Voir à ce propos les sections suivantes :

   * For Linux: [Launching the Web server and testing the configuration](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration)
   * For Windows: [Launching the Web server and testing the configuration](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration)

1. Démarrez le serveur Adobe Campaign (**net start nlserver6** sous Windows, **/etc/init.d/nlserver6 start** sous Linux) et lancez à nouveau la commande **nlserver pdump** afin de vérifier la présence de tous les modules actifs.

   >[!NOTE]
   >
   >À compter de la version 20.1, nous vous recommandons d’utiliser plutôt la commande suivante (pour Linux) : nlserver de démarrage **systemctl**

   ```
   12:09:54 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   syslogd@default (7611) - 9.2 MB
   stat@demo (5988) - 1.5 MB
   inMail@demo (7830) - 11.9 MB
   watchdog (27369) - 3.1 MB
   mta@demo (7831) - 15.6 MB
   wfserver@demo (7832) - 11.5 MB
   web@default (28671) - 40.5 MB
   ```

   Cette commande permet aussi de connaître la version et le numéro de build du serveur Adobe Campaign installé sur la machine.

1. Testez le module **nlserver web** à partir de l&#39;URL : https://console.campaign.net/nl/jsp/logon.jsp

   Cette URL permet d&#39;accéder à la page de téléchargement du programme d&#39;installation client.

   Saisissez l&#39;identifiant (login) **internal** avec son mot de passe associé à partir de la page intermédiaire de contrôle d&#39;accès.

   ![](assets/s_ncs_install_access_client.png)

   Voir à ce propos les sections suivantes :

   * Pour Linux : Disponibilité de la console [client pour Linux](../../installation/using/client-console-availability-for-linux.md)
   * Pour Windows : Disponibilité de la console [client pour Windows](../../installation/using/client-console-availability-for-windows.md)

1. Lancez la console cliente Adobe Campaign (récupérée à partir de la page de téléchargement de l&#39;étape précédente ou lancée directement sur le serveur pour une installation Windows), paramétrez l&#39;URL de connexion du serveur avec l&#39;URL https://console.campaign.net et connectez-vous avec l&#39;identifiant (login) **internal**.

   Reportez-vous à [Création d’une instance et connexion](../../installation/using/creating-an-instance-and-logging-on.md) et identificateur [](../../installation/using/campaign-server-configuration.md#internal-identifier)interne.

   L&#39;assistant de création de base de données s&#39;affiche lors de la première connexion :

   ![](assets/s_ncs_install_db_oracle_creation01.png)

   Suivez les étapes de l&#39;assistant et créez la base de données associée à l&#39;instance de connexion.

   Pour plus d’informations, reportez-vous à la section [Création et configuration de la base de données](../../installation/using/creating-and-configuring-the-database.md).

   Une fois la création de la base de données terminée, vous devez vous déconnecter.

1. Log back on to the client console using the **admin** login without a password and start the deployment wizard ( **[!UICONTROL Tools > Advanced]** menu) to finish configuring the instance.

   Pour plus d’informations, voir [Déploiement d’une instance](../../installation/using/deploying-an-instance.md).

   Les paramètres principaux à renseigner sont les suivants :

   * Envoi d&#39;email : les adresses expéditeur, de réponse et la boîte d&#39;erreur pour les mails rebonds.
   * Tracking : renseignez l&#39;URL externe utilisée pour la redirection et l&#39;URL interne puis cliquez sur **Enregistrement auprès du ou des serveurs de tracking** et validez sur l&#39;instance **demo** du serveur de tracking.

      For more on this, refer to [Tracking configuration](../../installation/using/deploying-an-instance.md#tracking-configuration).

      ![](assets/s_ncs_install_deployment_wiz_09.png)

      Le serveur Adobe Campaign étant le serveur applicatif et de redirection, l&#39;URL interne utilisée pour la collecte des logs de tracking et le transfert des URL est une connexion interne directe sur Tomcat (https://localhost:8080).

   * Gestion des mails rebonds : renseignez les paramètres de gestion des mails rebonds (ne pas tenir compte de la section **Mails rebonds non traités**).
   * Accès depuis Internet : renseignez les deux URL d&#39;accès pour les rapports ou les formulaires Web et les pages miroir.

      ![](assets/d_ncs_install_web_url.png)

