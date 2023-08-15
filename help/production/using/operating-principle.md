---
product: campaign
title: Principe de fonctionnement
description: Principe de fonctionnement
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
badge-v7-prem: label="On-premise et hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 1c032ef9-af11-4947-90c6-76cb9434ae85
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 100%

---

# Principe de fonctionnement{#operating-principle}



La plateforme Adobe Campaign repose techniquement sur plusieurs modules.

Il existe de nombreux modules Adobe Campaign. Certains fonctionnent en continu, d&#39;autres sont démarrés ponctuellement pour effectuer des actions d&#39;administration (par exemple : configurer la connexion à la base de données) ou lancer une tâche récurrente (par exemple : consolider les informations de tracking).

On distingue trois types de modules Adobe Campaign :

* Modules multi-instances : un seul processus est exécuté pour toutes les instances. Cela s’applique aux modules suivants : **web**, **syslogd**, **trackinglogd** et **watchdog** (activités à partir du fichier **config-default.xml**).
* Modules mono-instances : un processus est exécuté par instance. Cela s’applique aux modules suivants : **mta**, **wfserver**, **inMail**, **sms** et **stat** (activités du fichier **config-`<instance>`.xml**).
* Les modules utilitaires : il s&#39;agit de modules démarrés occasionnellement pour réaliser des opérations ponctuelles ou récurrentes (**cleanup**, **config**, remontée des logs de tracking, etc.).

L&#39;administration de ces modules est assurée par l&#39;outil ligne de commande **nlserver** installé dans le répertoire **bin** du dossier d&#39;installation.

La syntaxe générale de l&#39;outil **nlserver** est la suivante :

**nlserver `<command>``<command arguments>`**

Pour connaître la liste des modules disponibles, lancez la commande **nlserver**.

Les modules disponibles sont décrits dans le tableau suivant :

| La commande | Description |
|---|---|
| aliasCleansing | Normalisation des valeurs d&#39;énumération |
| billing | Transmission du rapport d&#39;activité du système à billing@neolane.net |
| cleanup | Nettoyage de la base de données : supprime les données obsolètes de la base de données et lance une mise à jour des statistiques utilisées par l&#39;optimiseur du moteur de base de données |
| config | Modification de la configuration du serveur |
| export | Export en ligne de commande : permet de lancer en ligne de commande un modèle d&#39;export créé depuis le client Adobe Campaign |
| fileconvert | Conversion de fichier à taille fixe |
| import | Import en ligne de commande : permet de lancer en ligne de commande un modèle d&#39;import créé depuis le client Adobe Campaign |
| inMail | Analyseur des mails entrants |
| installsetup | Mise à disposition du fichier d&#39;installation du client |
| javascript | Exécution de scripts JavaScript, ayant accès aux APIs SOAP |
| job | Traitement ligne de commande |
| merge | Fusion de formulaires |
| midSourcing | Récupération des informations des envois en mode mid-sourcing |
| monitor | Affichage, au format XML, de l&#39;état des processus serveur et des tâches planifiées, par instance |
| mta | Message Transfert Agent principal |
| package | Import ou export de fichier de package d&#39;entités |
| pdump | Affichage de l&#39;état des processus serveur |
| prepareda | Préparer une action de diffusion |
| restart | Redémarrage partiel du serveur |
| runwf | Exécution d&#39;une instance de workflow |
| shutdown | Arrêt complet du système |
| sms | Traitement des notifications SMS |
| sql | Exécution de scripts SQL |
| start | Démarrages additionnels |
| stat | Maintient les statistiques des connexions des MTA |
| stop | Arrêt partiel du système |
| submitda | Soumettre une action de diffusion |
| syslogd | Serveur d&#39;écriture des logs et traces |
| tracking | Consolidation et récupération des logs de tracking |
| trackinglogd | Serveur d&#39;écriture et de purge des logs de tracking |
| watchdog | Module de démarrage et suivi |
| web | Serveur applicatif (HTTP et SOAP) |
| wfserver | Serveur de workflows |

>[!IMPORTANT]
>
>Il existe un dernier module : le module de tracking et de relais vers le serveur applicatif qui, pour des raisons de performances, s&#39;intègre sous la forme d&#39;une librairie dynamique via des mécanismes natifs à un serveur Web IIS ou Apache. Il n&#39;existe pas de commande Adobe Campaign permettant de démarrer ou d&#39;administrer ce module, vous devez donc utiliser les commandes d&#39;administration du serveur Web.

L&#39;usage d&#39;un module et la syntaxe de ses paramètres sont affichés à partir de la commande : **nlserver.`[module]`-?**

Exemple:

**nlserver config -?**

```
Usage: nlserver [-verbose:<verbose mode>] [-?|h|H] [-version] [-noconsole]
 [-tracefile:<file>] [-tracefilter:<[type|!type],...>]
 [-instance:<instance>] [-low] [-high] [-queryplans] [-detach]
 [-internalpassword:<[password/newpassword]>] [-postupgrade]
 [-nogenschema] [-force] [-allinstances]
 [-addinstance:<instance/DNS masks[/language]>]
 [-setdblogin:<[dbms:]account[:database][/password]@server>]
 [-monoinstance]
 [-addtrackinginstance:<instance/masks DNS[/databaseId/[/language[/password]]]>]
 [-trackingpassword:<[password][/newpassword]>]
 [-setproxy:<protocol/server:port[/login]>] [-reload]
 [-applyxsl:<schema/file.xsl>] [-filter:<file>]
 [-setactivationkey:<activation key>]
 [-getactivationkey:<client identifier>]
-verbose : verbose mode
-? : display this help message
-version : display version number
-noconsole : no longer display logs and traces on the console
-tracefile : name of trace file to be generated (without extension)
-tracefilter : filter for the traces to be generated e.g.: wdbc,soap,!xtkquery.
-instance : instance to be used (default instance if this option is not present).
-low : start up with low priority
-high : start up with high priority (not recommended)
-queryplans : generate traces with the execution plans of SQL queries.
-detach : detaches the process from its parent (internal option)
-internalpassword : changes the password of the server internal account.
-postupgrade : updates the database following upgrade to a higher version. 
-nogenschema : does not recompute the schemas during database update
-force : updates the database even if this has already been done with the current build 
-allinstances : updates the database over all configured instances
-addinstance : adds a new instance.
-setdblogin : sets the parameters for connection to the database of an instance. The DBMS can be 'oracle', 'postgresql', 'mssql' or 'odbc' (default=postgresql)
-monoinstance : initializes for a single instance ().
-addtrackinginstance : adds a new tracking instance.
-trackingpassword : changes the tracking password of an instance
-setproxy : sets the parameters for connection to a proxy server. The protocol can be 'http', 'https' or 'all'.
-reload : asks the server to reload the configuration of the instances. 
-applyxsl : applies an XSL stylesheet to all entities of a schema. 
-filter : applies the XTK filter contained in the file during loading of the schema entities.
-setactivationkey : sets the activation key
```
