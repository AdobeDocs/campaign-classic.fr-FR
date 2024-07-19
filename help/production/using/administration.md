---
product: campaign
title: Administration
description: Administration
feature: Monitoring
badge-v7-prem: label="On-Premise/hybride uniquement" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 12a255fe-66f9-40ce-b19e-c24322c2e009
source-git-commit: b7dedddc080d1ea8db700fabc9ee03238b3706cc
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 100%

---

# Administration{#administration}

Le démarrage automatique des modules Adobe Campaign (**web**, **mta**, **wfserver**, etc.) est assuré par le service **nlserver**.

L&#39;installation d&#39;Adobe Campaign paramètre automatiquement la machine afin que le service **nlserver** démarre pendant la séquence de boot.

Les commandes suivantes permettent de démarrer/arrêter manuellement le service Adobe Campaign :

* Sous Windows :

   * **net start nlserver6**
   * **net stop nlserver6**

* Sous Linux (en tant que root) :

   * **/etc/init.d/nlserver6 start**
   * **/etc/init.d/nlserver6 stop**

>[!NOTE]
>
>À compter de la version 20.1, nous vous recommandons d’utiliser plutôt la commande suivante (pour Linux) : **systemctl start nlserver** / **systemctl stop nlserver**

Voici une liste des commandes usuelles d&#39;administration accessibles sous Linux (en tant qu&#39;**Adobe Campaign**) :

* Afficher tous les modules Adobe Campaign démarrés : **/etc/init.d/nlserver6 pdump** ou **/etc/init.d/nlserver6 status**

  >[!NOTE]
  >
  >Si vous ajoutez le paramètre **-who** après la commande **pdump**, vous récupérez les informations sur les connexions en cours (utilisateurs et traitements).\
  >La commande **/etc/init.d/nlserver6 status** (sans le paramètre &quot;-who&quot;) renverra :
  >
  >    * 0 si tous les processus sont en cours d&#39;exécution.
  >    * 1 si un processus est manquant.
  >    * 2 si aucun processus n&#39;est en cours.
  >    * une autre valeur en cas d&#39;erreur.
  >

* Démarrer/arrêter un module multi-instance ou mono-instance (**web**, **trackinglogd**, **syslogd**, **mta**, **wfserver**, **inmail**) :

  **nlserver start`<module>[@<instance>]`**

  **nlserver stop`<module>[@<instance>][-immediate][-noconsole]`**

  Vous pouvez également utiliser la commande **nlserver restart`<module>[@<instance>]`** pour redémarrer un module.

  Exemple:

  **nlserver start web**

  **nlserver start mta@my_instance**

  **nlserver stop syslogd**

  **nlserver stop wfserver@my_instance**

  **nlserver stop web -immediate**

  **nlserver restart web**

  >[!NOTE]
  >
  >* Si l&#39;instance n&#39;est pas précisée, il s&#39;agira de l&#39;instance &quot;default&quot;.
  >* Utilisez l&#39;option **-immediate** en cas d&#39;urgence pour forcer l&#39;arrêt immédiat du processus (équivalent à la commande **kill -9** Unix).
  >* Utilisez l’option **-noconsole** pour assurer que le module lancé n’affiche rien sur la console. Ses logs seront écrits sur le disque via le module **syslogd**.
  >* Utilisez l’option **-verbose** pour afficher davantage d&#39;informations sur les actions du processus.
  >
  >   Exemple:
  >
  >   **nlserver restart web -verbose**
  >
  >   **nlserver start mta@moninstance -verbose**
  >
  >   Cette option ajoute des logs supplémentaires. Nous vous conseillons de redémarrer les processus sans l&#39;option **-verbose** après avoir obtenu vos informations afin de ne pas surcharger les logs.

* Démarrer tous les processus Adobe Campaign (équivalent à un démarrage du service **nlserver6**) :

  **nlserver watchdog -noconsole**

* Arrêter tous les processus Adobe Campaign (équivalent à un arrêt du service **nlserver6**) :

  **nlserver shutdown**

* Charger à nouveau la configuration du module **nlserver web** (et le cas échéant le module d’extension du serveur web) lorsque les fichiers **serverConf.xml** et **config-`<instance>  .xml </instance>`** ont été édités.

  **nlserver config -reload** 

  >[!NOTE]
  >
  >Certaines modifications de la configuration ne sont pas prises en compte dynamiquement et nécessitent un arrêt/démarrage complet d&#39;Adobe Campaign.
