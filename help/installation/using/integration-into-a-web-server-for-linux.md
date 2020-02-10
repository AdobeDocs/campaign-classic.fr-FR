---
title: Intégration à un serveur Web pour Linux
seo-title: Intégration à un serveur Web pour Linux
description: Intégration à un serveur Web pour Linux
seo-description: null
page-status-flag: never-activated
uuid: 7b18d176-4458-46a8-8da4-3621f90c6b13
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
discoiquuid: 752ba848-aee9-4bb0-b2c5-490f3124f74e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: abddb3cdfcee9e41cab2e7e662d5bfd5d53d6f7e

---


# Intégration à un serveur Web pour Linux{#integration-into-a-web-server-for-linux}

Adobe Campaign inclut Apache Tomcat pour agir comme point d&#39;entrée dans le code du serveur applicatif via HTTP (et SOAP).

Vous pouvez utiliser ce Tomcat intégré pour servir des requêtes HTTP.

Dans ce cas :

* le port d’écoute par défaut est 8080. Pour le modifier, reportez-vous à [Configuration de Tomcat](../../installation/using/configuring-campaign-server.md#configuring-tomcat).
* Le client console puis se connecte à l’aide d’une URL telle que :

   ```
   http://<computer>:8080
   ```

Cependant, pour des raisons de sécurité et d&#39;administration, il est conseillé d&#39;utiliser un véritable serveur Web comme point d&#39;entrée principal pour le trafic HTTP lorsque la machine qui fait tourner Adobe Campaign est exposée sur Internet et que vous voulez donner un accès à la console depuis l&#39;extérieur de votre réseau.

Un serveur Web permet également d&#39;assurer la confidentialité des données avec le protocole HTTPS.

De même, vous devez utiliser un serveur Web lorsque vous souhaitez utiliser les fonctionnalités de tracking, disponibles seulement en tant que module d&#39;extension d&#39;un serveur Web.

>[!NOTE]
>
>Si vous n’utilisez pas la fonctionnalité de suivi, vous pouvez effectuer une installation standard d’Apache ou IIS avec une redirection vers Campaign. Le module d&#39;extension du serveur Web de suivi n&#39;est pas requis.

## Configuration du serveur Web Apache sous Debian {#configuring-the-apache-web-server-with-debian}

Cette procédure s&#39;applique si vous avez installé Apache sous une distribution basée sur APT.

Les étapes sont les suivantes :

1. Désactivez les modules chargés par défaut à l&#39;aide de la commande suivante :

   ```
   a2dismod auth_basic authn_file authz_default authz_user autoindex cgi dir env negotiation userdir
   ```

   Assurez-vous que les modules **alias**, **authz_host** et **mime** sont toujours activés. Pour cela, utilisez la commande suivante :

   ```
   a2enmod  alias authz_host mime
   ```

1. Create the file **nlsrv.load** in **/etc/apache2/mods-available** and insert the following content:

   Sous Debian 7 :

   ```
   LoadModule requesthandler22_module /usr/local/[INSTALL]/nl6/lib/libnlsrvmod.so
   ```

   Sous Debian 8 :

   ```
   LoadModule requesthandler24_module /usr/local/[INSTALL]/nl6/lib/libnlsrvmod.so
   ```

1. Create the file **nlsrv.conf** in **/etc/apache2/mods-available** using the following command:

   ```
   ln -s /usr/local/[INSTALL]/nl6/tomcat-7/conf/apache_neolane.conf /etc/apache2/mods-available/nlsrv.conf
   ```

1. Activez ce module avec la commande suivante :

   ```
    a2enmod nlsrv
   ```

   Si vous utilisez le module **mod_rewrite** pour les pages Adobe Campaign, vous devez renommer les fichiers **nlsrv.load** et **nlsrv.conf** en **zz-nlsrv.load et zz-nlsrv.conf.****** Pour activer le module, exécutez la commande suivante :

   ```
   a2enmod zz-nlsrv
   ```

1. Edit the **/etc/apache2/envvars** file, add the following lines:

   ```
   # Added Neolane
   if [ "$LD_LIBRARY_PATH" != "" ]; then export LD_LIBRARY_PATH="/usr/local/neolane/nl6/lib:$LD_LIBRARY_PATH"; else export LD_LIBRARY_PATH=/usr/local/neolane/nl6/lib; fi
   export USERPATH=/usr/local/neolane
   ```

   Enregistrez ces modifications.

1. Ajoutez ensuite les utilisateurs Adobe Campaign dans le groupe d&#39;utilisateurs Apache et inversement, en effectuant une commande du type :

   ```
   usermod neolane -G www-data
   usermod www-data -G neolane
   ```

1. Redémarrez Apache :

   ```
   invoke-rc.d apache2 restart
   ```

## Configuration du serveur web Apache sous RHEL {#configuring-apache-web-server-in-rhel}

Cette procédure s&#39;applique si vous avez installé et sécurisé Apache sous une distribution basée sur packages RPM (RHEL, CentOS et Suse).

Les étapes sont les suivantes :

1. In the `httpd.conf` file, activate the following Apache modules:

   ```
   alias
   authz_host
   mime
   ```

1. Désactivez les modules suivants :

   ```
   auth_basic
   authn_file
   authz_default
   authz_user
   autoindex
   cgi
   dir
   env
   negotiation
   userdir
   ```

Commentez les fonctions liées aux modules désactivés :

    &quot;
    
    
    
    
    
    
    
    
    
    
    DirectoryIndexOptionsAddIconByEncodingAddIconByTypeAddIconDefaultIconDefaultIconReaderNameHeaderIndexIgnoreLanguagePriorityForceLanguagePriority
    &quot;

1. Créez un fichier de configuration spécifique à Adobe Campaign dans le `/etc/httpd/conf.d/` dossier.

Par exemple `CampaignApache.conf`.

1. For **RHEL6**, add the following instructions in the file:

   ```
   LoadModule requesthandler22_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
   Include /usr/local/neolane/nl6/tomcat-7/conf/apache_neolane.conf
   ```

For **RHEL7**, add the following instructions in the file:

LoadModule request thandler24_module /usr/local/neolane/nl6/lib/libnlsrvmod.soInclure /usr/local/neolane/nl6/tomcat-7/conf/apache_neolane.conf

1. For **RHEL6**:

Add the following instructions in the `/etc/sysconfig/httpd` file:

    &quot;
    #Neolane/Adobe Campaign
    Configuration if [ &quot;$LD_LIBRARY_PATH&quot; != &quot;&quot; ]; exporter ensuite LD_LIBRARY_PATH=&quot;/usr/local/neolane/nl6/lib:$LD_LIBRARY_PATH&quot;; else export LD_LIBRARY_PATH=/usr/local/neolane/nl6/lib;
    fiexport USERPATH=/usr/local/néolane
    &quot;

For **RHEL7**:

Add the `/etc/systemd/system/httpd.service` file with the following content:

    &quot;
    .include /usr/lib/systemd/system/httpd.service
    
    [Service]
    Environment=USERPATH=/usr/local/neolane LD_LIBRARY_PATH=/usr/local/neolane/nl6/lib
    &quot;

Mettez à jour le module utilisé par systemd :

    &quot;
    systemctl daemon-reload
    &quot;

1. Ajoutez ensuite les utilisateurs Adobe Campaign dans le groupe d&#39;utilisateurs Apache et inversement, en effectuant la commande :

   ```
   usermod -a -G neolane apache
   usermod -a -G apache neolane
   ```
Les noms des groupes à utiliser dépendent de votre configuration Apache.

1. Démarrez Apache et le serveur Adobe Campaign:

Pour RHEL6 :

    &quot;
    /etc/init.d/httpd start
    /etc/init.d/nlserver start
    &quot;

Pour RHEL7 :

    &quot;
    systemctl start
    httpdsystemctl start nlserver
    &quot;

## Lancement du serveur Web et test de la configuration{#launching-the-web-server-and-testing-the-configuration}

Vous pouvez à présent tester la configuration en démarrant Apache. Le module Adobe Campaign doit alors afficher sa bannière sur la console (deux bannières sous certains systèmes d&#39;exploitation) :

```
 /etc/init.d/apache start
```

Les informations affichées sont alors les suivantes :

```
12:26:28 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:26:28 >   Web server start (pid=29698, tid=-1212463424)...
12:26:28 >   Server started
12:26:28 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:26:28 >   Web server start (pid=29698, tid=-1212463424)...
12:26:28 >   Server started
```

Vérifiez ensuite qu&#39;il répond correctement en soumettant une URL de test.

Pour cela, vous pouvez tester depuis la ligne de commande en exécutant :

```
 telnet localhost 80  
```

En retour, vous devez obtenir :

```
Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
````

Puis saisissez :

```
GET /r/test
````

Les informations affichées sont alors les suivantes :

```
<redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='' localHost='XXXX'/>
Connection closed by foreign host.
````

You can also request the URL [`http://<computer>`](http://machine/r/test) from a Web browser.