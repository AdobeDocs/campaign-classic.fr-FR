---
title: Commandes usuelles
seo-title: Commandes usuelles
description: Commandes usuelles
seo-description: null
page-status-flag: never-activated
uuid: f06df8c0-d4ec-4d6b-84d5-f46d852388a3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: 90718075-87a7-4e9a-935b-571010908e79
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 5f3ceab5ee82587d9f1829792bdabf2209f793cd

---


# Commandes usuelles{#usual-commands}

Cette section propose la liste des commandes usuelles sous Adobe Campaign.

La commande **nlserver** est la commande d&#39;entrée de l&#39;ensemble de l&#39;applicatif Adobe Campaign.

This command has the following syntax: **nlserver **`<command>`****`<arguments>`****

The parameter **`<command>`** corresponds to the module.

>[!NOTE]
>
>* In any case, you can add the **-noconsole** argument to delete comments displayed once the modules are started.
>* Conversely, you can add the argument **-verbose** to display more information.
>



## Commandes de monitoring {#monitoring-commands-}

>[!NOTE]
>
>To list all modules, you need to use the **nlserver pdump** command.

You can add the parameter **-who** to list the connections in progress (database and application).

```
nlserver pdump -who
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
web@default (9984) - 50.1 Mo
watchdog (2273) - 6.6 Mo
syslogd@default (9931) - 7.0 Mo
trackinglogd@default (9985) - 45.6 Mo
mta@test (9986) - 9.6 Mo
wfserver@test (9987) - 8.8 Mo

Connections ------------------------------------------------------
Last Access IP Instance Login 
DD/MM/YYYY HH:MM:SS 127.0.0.1 default formation_fr|tracking
DD/MM/YYYY HH:MM:SS 127.0.0.1 default internal|monitoring

Connection pool --------------------------------------------------
Datasource Server Provider Login 
default xxxxx myserver myprovider test400
```

Une autre commande utile est la commande **nlserver monitor**. Elle permet de lister le fichier XML de monitoring (obtenu dans le client Adobe Campaign ou par la page web **monitor.jsp**).

Vous pouvez lui adjoindre le paramètre **-missing** pour lister les modules absents (erreur dans ces modules, arrêt des modules, etc.)

```
nlserver monitor -missing
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
inMail@test
mta@test
wfserver@test
```

Cela correspond aux modules ayant un démarrage automatique mais qui ne sont pas lancés.

## Commandes de lancement des modules {#module-launch-commands}

La syntaxe pour lancer les modules sera toujours de la forme :

```
nlserver start <module>@<INSTANCE>
```

```
nlserver stop <module>@<INSTANCE>
```

>[!NOTE]
>
>**`<instance>`** correspond au nom d&#39;instance, tel que renseigné dans les fichiers de configuration, ou **default** pour les modules mono-instance.

## Arrêter les services {#shut-down-services}

Pour arrêter les services Adobe Campaign, vous pouvez utiliser une des commandes suivantes :

* Si vous avez un accès root ou administrateur :

   * Sous Linux :

      ```
      /etc/init.d/nlserver6 stop
      ```

   * Sous Windows :

      ```
      net stop nlserver6
      ```

* Sinon, dans le compte Adobe Campaign :

   ```
   nlserver shutdown 
   ```

## Redémarrer les services {#restart-services}

De même, afin de démarrer Adobe Campaign vous pouvez utiliser une des commandes suivantes :

* Si vous avez un accès root ou administrateur :

   * Sous Linux :/etc/init.d de démarrage de nlserver6
   * Sous Windows :net start nlserver6

* Otherwise, in the Adobe Campaign account: **nlserver watchdog -svc -noconsole**

## La commande config {#the-config-command}

The **config** command lets you manage server configuration, including the reconfiguration of the database connection.

Use the **config** command of the **nlserver** executable file with the **-setdblogin** parameter.

```
nlserver config -setdblogin:<[dbms:]account[:database][/password]@server>
```

```
nlserver config -setdblogin:PostgreSQL:<accountName>:test6@dbserver
```

Vous devez saisir le mot de passe.

To change the **internal** password: **nlserver config -internalpassword**

>[!CAUTION]
>
>Pour vous connecter avec l’identifiant **Internal**, vous devez impérativement avoir défini un mot de passe. Voir à ce sujet [cette section](../../installation/using/campaign-server-configuration.md#internal-identifier).

>[!NOTE]
>
>* In general, instead of modifying the configuration files by hand, you can use the **config** command
>* To get the list of parameters, use the **-?** parameter : config **nlserver -?**
>* Dans le cas d&#39;une base Oracle, il ne faut pas préciser le compte. La syntaxe sera donc la suivante :
>
>  
nlserver config -setdblogin:Oracle:test6@dbserver


