---
title: 'Administration '
seo-title: 'Administration '
description: 'Administration '
seo-description: null
page-status-flag: never-activated
uuid: 376efec1-1647-43b4-b72f-2603214c7cc6
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: 860be8be-f28c-4836-b4fb-e91c6a4616c6
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 779d9162b7296339a796512838612ede1186ddcc

---


# Administration{#administration}

Le démarrage automatique des modules Adobe Campaign (**web**, **mta**, **wfserver**, etc.) est assuré par le service **nlserver**.

L&#39;installation d&#39;Adobe Campaign paramètre automatiquement la machine afin que le service **nlserver** démarre pendant la séquence de boot.

Les commandes suivantes permettent de démarrer/arrêter manuellement le service Adobe Campaign :

* Sous Windows :

   * **net start nlserver6**
   * **net stop nlserver6**

* Sous Linux (en tant que root) :

   * **/etc/init.d de démarrage de nlserver6**
   * **/etc/init.d/nlserver6 stop**

Voici une liste des commandes usuelles d&#39;administration accessibles sous Linux (en tant qu&#39;**Adobe Campaign**) :

* Display all started Adobe Campaign modules: **/etc/init.d/nlserver6 pdump** or **/etc/init.d/nlserver6 status**

   >[!NOTE]
   >
   >Adding the **-who** parameter to the **pdump** command lets you collect information on current connections (users and processes).\
   >La commande **/etc/init.d/nlserver6 status** (sans le paramètre &quot;-who&quot;) renverra :
   >
   >    * 0 si tous les processus sont en cours d&#39;exécution.
   >    * 1 si un processus est manquant.
   >    * 2 si aucun processus n&#39;est en cours.
   >    * une autre valeur en cas d&#39;erreur.


* Démarrer/arrêter un module multi-instance ou mono-instance (**web**, **trackinglogd**, **syslogd**, **mta**, **wfserver**, **inmail**) :

   **nlserver start`<module>[@<instance>]`**

   **nlserver stop`<module>[@<instance>][-immediate][-noconsole]`**

   You can also use the **nlserver restart`<module>[@<instance>]`**command to restart a module.

   Exemple:

   **nlserver start web**

   **nlserver start mta@my_instance**

   **nlserver stop syslogan**

   **nlserver stop wfserver@my_instance**

   **nlserver stop web-directly**

   **web de redémarrage du serveur nlserver**

   >[!NOTE]

   >* Si l&#39;instance n&#39;est pas précisée, il s&#39;agira de l&#39;instance &quot;default&quot;.
   >    
   >    
   >    * Utilisez l&#39;option **-immediate** en cas d&#39;urgence pour forcer l&#39;arrêt immédiat du processus (équivalent à la commande **kill -9** Unix).
   * Utilisez l&#39;option **-noconsole** pour vous assurer que le module lancé n&#39;affichera rien sur la console. Ses journaux seront écrits sur le disque via le module **syslogd** .
   * Use the **-verbose** option to display additional information on process actions.


      Exemple:


      **nlserver restart web -verbose**


      **nlserver start mta@moninstance -verbose**


      This option adds additional logs. We recommend starting the processes again without the **-verbose** option once you have found the desired information, to avoid overloading logs.


* Démarrer tous les processus Adobe Campaign (équivalent à un démarrage du service **nlserver6**) :

   **nlserver watchdog -noconsole**

* Arrêter tous les processus Adobe Campaign (équivalent à un arrêt du service **nlserver6**) :

   **nlserver shutdown**

* Reload the **nlserver web** module configuration (and the web server extension module, where applicable) when the **serverConf.xml** and **config-`<instance>  .xml </instance>`**files have been edited.

   **nlserver config -reload**

   >[!NOTE]
   Certaines modifications de la configuration ne sont pas prises en compte dynamiquement et nécessitent un arrêt/démarrage complet d&#39;Adobe Campaign.

