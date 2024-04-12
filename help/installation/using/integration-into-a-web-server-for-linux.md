---
product: campaign
title: Intégration à un serveur Web pour Linux
description: Découvrez comment intégrer Campaign dans un serveur Web (Linux)
feature: Installation, Instance Settings
badge-v7-prem: label="On-premise et hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: 4f8ea358-a38d-4137-9dea-f398e60c5f5d
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 100%

---

# Intégration à un serveur Web pour Linux{#integration-into-a-web-server-for-linux}



Adobe Campaign inclut Apache Tomcat pour agir comme point d&#39;entrée dans le code du serveur applicatif via HTTP (et SOAP).

Vous pouvez utiliser ce Tomcat intégré pour servir des requêtes HTTP.

Dans ce cas :

* le port d’écoute par défaut est 8080. Pour savoir comment le modifier, consultez [cette section](configure-tomcat.md).
* Vos consoles clientes se connectent alors en utilisant une URL de type :

  ```
  http://<computer>:8080
  ```

Cependant, pour des raisons de sécurité et d&#39;administration, il est conseillé d&#39;utiliser un véritable serveur Web comme point d&#39;entrée principal pour le trafic HTTP lorsque la machine qui fait tourner Adobe Campaign est exposée sur Internet et que vous voulez donner un accès à la console depuis l&#39;extérieur de votre réseau.

Un serveur Web permet également d&#39;assurer la confidentialité des données avec le protocole HTTPS.

De même, vous devez utiliser un serveur Web lorsque vous souhaitez utiliser les fonctionnalités de tracking, disponibles seulement en tant que module d&#39;extension d&#39;un serveur Web.

>[!NOTE]
>
>Si vous n’utilisez pas la fonctionnalité de tracking, vous pouvez effectuer une installation standard d’Apache ou IIS avec une redirection vers Campaign. Le module d’extension du serveur Web de tracking n’est pas requis.

## Configuration du serveur Web Apache sous Debian {#configuring-the-apache-web-server-with-debian}

Cette procédure s&#39;applique si vous avez installé Apache sous une distribution basée sur APT.

Les étapes sont les suivantes :

1. Désactivez les modules chargés par défaut à l&#39;aide de la commande suivante :

   ```
   a2dismod auth_basic authn_file authz_default authz_user autoindex cgi dir env negotiation userdir
   ```

   Assurez-vous que les modules **alias**, **authz_host** et **mime** sont toujours activés. Pour cela, utilisez la commande suivante :

   ```
   a2enmod  alias authz_host mime
   ```

1. Créez le fichier **nlsrv.load** dans **/etc/apache2/mods-available** et insérez le contenu suivant :

   Sous Debian 8 :

   ```
   LoadModule requesthandler24_module /usr/local/[INSTALL]/nl6/lib/libnlsrvmod.so
   ```

1. Créez le fichier **nlsrv.conf** dans **/etc/apache2/mods-available** à l’aide de la commande suivante :

   ```
   ln -s /usr/local/[INSTALL]/nl6/conf/apache_neolane.conf /etc/apache2/mods-available/nlsrv.conf
   ```

1. Activez ce module avec la commande suivante :

   ```
    a2enmod nlsrv
   ```

   Si vous utilisez le module **mod_rewrite** pour les pages Adobe Campaign, vous devez renommer les fichiers **nlsrv.load** et **nlsrv.conf** en **zz-nlsrv.load** et **zz-nlsrv.conf**. Pour activer ce module, exécutez la commande suivante :

   ```
   a2enmod zz-nlsrv
   ```

1. Modifiez le fichier **/etc/apache2/envvars**, ajoutez les lignes suivantes :

   ```
   # Added Neolane
   if [ "$LD_LIBRARY_PATH" != "" ]; then export LD_LIBRARY_PATH="/usr/local/neolane/nl6/lib:$LD_LIBRARY_PATH"; else export LD_LIBRARY_PATH=/usr/local/neolane/nl6/lib; fi
   export USERPATH=/usr/local/neolane
   ```

   Enregistrez ces modifications.

1. Ajoutez ensuite les utilisateurs Adobe Campaign dans le groupe d&#39;utilisateurs Apache et inversement, en effectuant une commande du type :

   ```
   usermod neolane -G www-data
   usermod www-data -G neolane
   ```

1. Redémarrez Apache :

   ```
   invoke-rc.d apache2 restart
   ```

## Configuration du serveur web Apache sous RHEL {#configuring-apache-web-server-in-rhel}

Cette procédure s&#39;applique si vous avez installé et sécurisé Apache sous une distribution basée sur packages RPM (RHEL, CentOS et Suse).

Les étapes sont les suivantes :

1. Dans le fichier `httpd.conf`, activez les modules Apache suivants :

   ```
   alias
   authz_host
   mime
   ```

1. Désactivez les modules suivants :

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

   Commentez les fonctions liées aux modules désactivés :

   ```
   DirectoryIndex
   IndexOptions    
   AddIconByEncoding    
   AddIconByType    
   AddIcon    
   DefaultIcon    
   ReadmeName    
   HeaderName    
   IndexIgnore    
   LanguagePriority    
   ForceLanguagePriority
   ```

1. Créez un fichier de configuration spécifique à Adobe Campaign dans le dossier `/etc/httpd/conf.d/`. Par exemple `CampaignApache.conf`

1. Pour **RHEL7**, ajoutez les instructions suivantes dans le fichier :

   ```
   LoadModule requesthandler24_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
   Include /usr/local/neolane/nl6/conf/apache_neolane.conf
   ```

1. Pour **RHEL7** :

   Ajoutez le fichier `/etc/systemd/system/httpd.service` avec le contenu suivant :

   ```
   .include /usr/lib/systemd/system/httpd.service
   
   [Service]
   Environment=USERPATH=/usr/local/neolane LD_LIBRARY_PATH=/usr/local/neolane/nl6/lib
   ```

   Mettez à jour le module utilisé par systemd :

   ```
   systemctl daemon-reload
   ```

1. Ajoutez ensuite les utilisateurs Adobe Campaign dans le groupe d&#39;utilisateurs Apache et inversement, en effectuant la commande :

   ```
   usermod -a -G neolane apache
   usermod -a -G apache neolane
   ```

   Les noms des groupes à utiliser dépendent de votre configuration Apache.

1. Démarrez Apache et le serveur Adobe Campaign:

   Pour RHEL7 :

   ```
   systemctl start httpd
   systemctl start nlserver
   ```

## Lancement du serveur Web et test de la configuration{#launching-the-web-server-and-testing-the-configuration}

Vous pouvez à présent tester la configuration en démarrant Apache. Le module Adobe Campaign doit alors afficher sa bannière sur la console (deux bannières sous certains systèmes d&#39;exploitation) :

```
 /etc/init.d/apache start
```

Les informations affichées sont alors les suivantes :

```
12:26:28 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:26:28 >   Web server start (pid=29698, tid=-1212463424)...
12:26:28 >   Server started
12:26:28 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:26:28 >   Web server start (pid=29698, tid=-1212463424)...
12:26:28 >   Server started
```

Vérifiez ensuite qu&#39;il répond correctement en soumettant une URL de test.

Pour cela, vous pouvez tester depuis la ligne de commande en exécutant :

```
 telnet localhost 80  
```

En retour, vous devez obtenir :

```
Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
```

Puis saisissez :

```
GET /r/test
```

Les informations affichées sont alors les suivantes :

```
<redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='' localHost='XXXX'/>
Connection closed by foreign host.
```

Vous pouvez également appeler l’URL `https://myserver.adobe.com/r/test` depuis un navigateur web.
