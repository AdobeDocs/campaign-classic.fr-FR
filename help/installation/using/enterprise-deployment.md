---
title: Déploiement Entreprise
seo-title: Déploiement Entreprise
description: Déploiement Entreprise
seo-description: null
page-status-flag: never-activated
uuid: 2c2b5cef-86cb-4cb5-801a-ca6afeae90bb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: deployment-types-
discoiquuid: 066d0ac1-033c-467b-aa6c-43a97ecd8632
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 6b631f8456ad1f61cec1630334d76752f6af9866

---


# Déploiement Entreprise{#enterprise-deployment}

Il s&#39;agit de la configuration la plus complète. Elle étend la configuration standard pour une sécurité accrue et une disponibilité supérieure :

* serveurs de redirection dédiés, derrière un répartiteur de charge agissant au niveau HTTP ou au niveau TCP, pour une montée en charge et une grande disponibilité,
* deux serveurs applicatifs, pour un meilleur débit et des capacités de fail-over (fonctionnement même en cas de panne d&#39;un serveur), isolés dans le LAN.

La communication générale entre les serveurs et les processus est réalisée conformément au schéma suivant :

![](assets/s_901_ncs_install_enterpriseconfig.png)

Le débit attendu dans ce type de configuration peut être supérieur à 100 000 mails par heure avec le paramétrage et la bande-passante adéquats.

## Caractéristiques {#features}

### Avantages {#advantages}

* Optimisation de la sécurité : seuls les services qui ont besoin d&#39;être exposés à l&#39;extérieur sont installés sur la machine de la DMZ.
* Haute disponibilité plus aisée à garantir : seule la machine visible de l&#39;extérieur doit être gérée pour la haute disponibilité.

### Inconvénients {#disadvantages}

Coûts du matériel et d&#39;administration plus élevés.

### Matériel recommandé {#recommended-equipment}

* Serveurs applicatifs : processeur quad-core à 2 GHz, 4 Go de mémoire, disque en RAID 1 Soft 80 Go SATA.
* Serveurs de redirection : processeur quad-core à 2 GHz, 2 Go de mémoire, disque en RAID 1 Soft 80 Go SATA.

>[!NOTE]
>
>Il est possible de réutiliser un répartiteur de charge déjà déployé pour répartir le trafic vers les serveurs de redirection.

## Etapes d&#39;installation et de configuration {#installation-and-configuration-steps}

### Prérequis {#prerequisites}

* JDK sur les deux serveurs applicatifs,
* Serveur Web (IIS, Apache) sur les deux frontaux,
* Accès à un serveur de base de données sur les deux serveurs applicatifs,
* Boîte pour les mails rebonds accessible en POP3,
* Création de deux alias DNS sur le répartiteur de charge :

   * un premier alias exposé au grand public pour le tracking et pointant vers le répartiteur de charge sur une adresse IP virtuelle (VIP) qui est ensuite distribuée sur les deux serveurs frontaux,
   * un deuxième alias exposé aux utilisateurs métiers pour l&#39;accès console et pointant vers un répartiteur de charge sur une adresse IP virtuelle (VIP) qui est ensuite distribuée sur les deux serveurs applicatifs.

* Pare-feu configuré pour ouvrir les ports STMP (25), DNS (53), HTTP (80), HTTPS (443), SQL (1521 pour Oracle, 5432 pour PostgreSQL, etc.). Pour plus d&#39;informations, reportez-vous à la section Accès [aux](../../installation/using/network-configuration.md#database-access)bases de données.

>[!CAUTION]
>
>Si vos serveurs applicatifs pointent sur une instance de base de données unique, après l&#39;importation d&#39;un package standard sur une instance, le schéma contenu dans le package n&#39;est pas chargé sur l&#39;autre instance.
>  
>Si vos serveurs applicatifs pointent sur une instance de base de données unique, après changement du schéma sur une instance, le schéma n&#39;est pas chargé sur l&#39;autre instance.
>
>Pour résoudre ces problèmes, vous devez redémarrer le processus ‘web@default‘ sur la deuxième instance où l&#39;erreur est survenue.

### Installer et configurer le serveur applicatif n° 1 {#installing-and-configuring-the-application-server-1}

Dans les exemples présentés ci-dessous, les paramètres de l&#39;instance sont les suivants :

* Nom de l&#39;instance : demo
* Masque DNS : tracking.campaign.net*, console.campaign.net* (le serveur applicatif gère les URL pour la connexion des consoles clientes et des rapports, ainsi que les URL des pages miroir et de désinscription)
* Langue : française
* Base de données : campaign:demo@dbsrv

Les étapes d&#39;installation du premier serveur sont les suivantes :

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

   * Pour Linux : [Premier démarrage du serveur](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server)
   * Pour Windows : [Premier démarrage du serveur](../../installation/using/installing-the-server.md#first-start-up-of-the-server)

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

1. Edit the **config-demo.xml** file (created via the previous command and located next to the **config-default.xml** file), check that the **mta** (delivery), **wfserver** (workflow), **inMail** (rebound mails) and **stat** (statistics) processes are enabled, then configure the address of the **app** statistics server:

   ```
   <?xml version='1.0'?>
   <serverconf>  
     <shared>    
       <!-- add lang="eng" to dataStore to force English for the instance -->    
       <dataStore hosts="tracking.campaign.net*,console.campaign.net*">      
         <mapping logical="*" physical="default"/>    
       </dataStore>  </shared>  
       <mta autoStart="true" statServerAddress="app">
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
   * Pour Windows : Disponibilité de la console [client pour Windows](../../installation/using/client-console-availability-for-windows.md).

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

1. Testez le module **nlserver web** à partir de l&#39;URL : [https://console.campaign.net/nl/jsp/logon.jsp](https://tracking.campaign.net/r/test).

   Cette URL permet d&#39;accéder à la page de téléchargement du programme d&#39;installation client.

   Saisissez l&#39;identifiant (login) **internal** avec son mot de passe associé à partir de la page intermédiaire de contrôle d&#39;accès.

   ![](assets/s_ncs_install_access_client.png)

   Voir à ce propos les sections suivantes :

   * Pour Linux : Disponibilité de la console [client pour Linux](../../installation/using/client-console-availability-for-linux.md)
   * Pour Windows : Disponibilité de la console [client pour Windows](../../installation/using/client-console-availability-for-windows.md)

### Installer et configurer le serveur applicatif n° 2 {#installing-and-configuring-the-application-server-2}

Les étapes sont les suivantes :

1. Installez le serveur Adobe Campaign.
1. Copiez les fichiers de l&#39;instance créée sur le serveur applicatif n° 1

   Le nom d&#39;instance du serveur applicatif n°1 doit être conservé.

1. Remplacez le mot de passe **internal** par celui du serveur applicatif N°1.
1. Rattachez la base de données sur l&#39;instance :

   ```
   nlserver config -setdblogin:PostgreSQL:campaign:demo@dbsrv -instance:demo
   ```

1. Edit the **config-demo.xml** file (created via the previous command and located next to the **config-default.xml** file), check that the **mta** (delivery), **wfserver** (workflow), **inMail** (rebound mails) and **stat** (statistics) processes are enabled, then configure the address of the **app** statistics server:

   ```
   <?xml version='1.0'?>
   <serverconf>  
     <shared>    
       <!-- add lang="eng" to dataStore to force English for the instance -->    
       <dataStore hosts="tracking.campaign.net*,console.campaign.net*">      
         <mapping logical="*" physical="default"/>    
       </dataStore>  </shared>  
       <mta autoStart="true" statServerAddress="app">
       <wfserver autoStart="true"/>  
       <inMail autoStart="true"/>  
       <sms autoStart="false"/>  
       <listProtect autoStart="false"/>
   </serverconf>
   ```

   For more on this, refer to [Enabling processes](../../installation/using/campaign-server-configuration.md#enabling-processes).

1. Edit the **serverConf.xml** file and populate the DNS configuration of the MTA module:

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >Le paramètre **nameServers** n&#39;est utile que sous Windows.

   For more on this, refer to [Campaign server configuration](../../installation/using/campaign-server-configuration.md).

1. Démarrez les serveurs Adobe Campaign.

   Voir à ce propos les sections suivantes :

   * Pour Linux : [Premier démarrage du serveur](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server)
   * Pour Windows : [Premier démarrage du serveur](../../installation/using/installing-the-server.md#first-start-up-of-the-server)

### Installer et configurer les serveurs frontaux {#installing-and-configuring-the-frontal-servers}

Les procédures d&#39;installation et de paramétrage sont identiques sur les deux machines.

Les étapes sont les suivantes :

1. Installez le serveur Adobe Campaign,
1. Respectez la procédure d&#39;intégration du serveur Web (IIS, Apache) décrite dans les sections suivantes :

   * Pour Linux : [Intégration dans un serveur Web pour Linux](../../installation/using/integration-into-a-web-server-for-linux.md),
   * Pour Windows : [Intégration dans un serveur Web pour Windows](../../installation/using/integration-into-a-web-server-for-windows.md).

1. Copiez les fichiers **config-demo.xml** et  **serverConf.xml** créés lors de l&#39;installation, puis, dans le fichier  **config-demo.xml**, activez le processus **trackinglogd** et désactivez les processus **mta**, **inmail**, **wfserver** et **stat**.
1. Edit the **serverConf.xml** file and populate the redundant tracking servers in the parameters of the redirection:

   ```
   <spareServer enabledIf="$(hostname)!='front_srv1'" id="1" url="https://front_srv1:8080"/>
   <spareServer enabledIf="$(hostname)!='front_srv2'" id="2" url="https://front_srv2:8080"/>
   ```

1. Démarrez le site web et testez la redirection à partir de l&#39;URL : [https://tracking.campaign.net/r/test](https://tracking.campaign.net/r/test)

   Le navigateur doit afficher les messages suivants (en fonction de l&#39;URL redirigée par le répartiteur de charge) :

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv1"/>
   ```

   or

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv2"/>
   ```

   Voir à ce propos les sections suivantes :

   * For Linux: [Launching the Web server and testing the configuration](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration),
   * For Windows: [Launching the Web server and testing the configuration](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration).

1. Démarrer le serveur Adobe Campaign.

