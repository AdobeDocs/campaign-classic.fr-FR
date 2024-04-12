---
product: campaign
title: Commandes usuelles
description: Commandes usuelles
feature: Monitoring
badge-v7-prem: label="On-premise et hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 472ccc04-e68e-4ccb-90e9-7d626a4e794f
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 90%

---

# Commandes usuelles{#usual-commands}



Cette section propose la liste des commandes usuelles sous Adobe Campaign.

La commande **nlserver** est la commande d&#39;entrée de l&#39;ensemble de l&#39;applicatif Adobe Campaign.

La syntaxe de cette commande est la suivante : **nlserver **`<command>`****`<arguments>`****

Le paramètre **`<command>`** correspond au module.

>[!NOTE]
>
>* Vous pouvez dans tous les cas adjoindre l&#39;argument **-noconsole** afin de supprimer les commentaires affichés après le lancement des modules.
>* A contrario, vous pouvez ajouter l&#39;argument **-verbose** pour afficher plus d&#39;informations.
>

## Commandes de monitoring {#monitoring-commands-}

>[!NOTE]
>
>Pour lister l&#39;ensemble des modules, vous devez utiliser la commande **nlserver pdump**.

Vous pouvez lui adjoindre le paramètre **-who** permettant de lister les connexions en cours (base de données et applicatif).

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

Une autre commande utile est : **nlserver monitor**. Il répertorie le fichier XML de surveillance (obtenu dans le client Adobe Campaign ou via l’ **monitor.jsp** page web).

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

La syntaxe pour lancer les modules sera toujours de la forme :

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

Pour arrêter les services Adobe Campaign, vous pouvez utiliser une des commandes suivantes :

* Si vous avez un accès root ou administrateur :

   * Sous Linux :

     ```
     /etc/init.d/nlserver6 stop
     ```

     >[!NOTE]
     >
     >À compter de la version 20.1, nous vous recommandons d’utiliser plutôt la commande suivante (pour Linux) : **systemctl stop nlserver**

   * Sous Windows :

     ```
     net stop nlserver6
     ```

* Sinon, dans le compte Adobe Campaign :

  ```
  nlserver shutdown 
  ```

## Redémarrer les services {#restart-services}

De même, afin de démarrer Adobe Campaign vous pouvez utiliser une des commandes suivantes :

* Si vous avez un accès root ou administrateur :

   * Sous Linux : /etc/init.d/nlserver6 start

     >[!NOTE]
     >
     >À compter de la version 20.1, nous vous recommandons d’utiliser plutôt la commande suivante (pour Linux) : **systemctl start nlserver**

   * Sous Windows : net start nlserver6

* Sinon, dans le compte Adobe Campaign : **nlserver watchdog -svc -noconsole**

## La commande config {#the-config-command}

La commande **config** permet de gérer la configuration du serveur, notamment de re-paramétrer la connexion à la base de données.

Utilisez la commande **config** du fichier exécutable **nlserver** avec le paramètre **-setdblogin**.

```
nlserver config -setdblogin:<[dbms:]account[:database][/password]@server>
```

```
nlserver config -setdblogin:PostgreSQL:<accountName>:test6@dbserver
```

Vous devez saisir le mot de passe.

Pour changer le mode de passe **internal** : **nlserver config -internalpassword**

>[!IMPORTANT]
>
>Pour vous connecter avec le **Interne** , vous devez avoir défini un mot de passe au préalable. Pour plus d’informations, consultez [cette section](../../installation/using/configuring-campaign-server.md#internal-identifier).

>[!NOTE]
>
>* D&#39;une manière générale, au lieu de modifier les fichiers de configuration à la main, vous pouvez utiliser la commande **config**.
>* Pour obtenir la liste des paramètres, utilisez le paramètre **-?** : **nlserver config -?**
>* Dans le cas d&#39;une base Oracle, il ne faut pas préciser le compte. La syntaxe sera donc la suivante :
>
>  `nlserver config -setdblogin:Oracle:test6@dbserver`
>
