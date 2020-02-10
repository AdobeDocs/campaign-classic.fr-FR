---
title: Migration dans Windows pour Adobe Campaign 7
seo-title: Migration dans Windows pour Adobe Campaign 7
description: Migration dans Windows pour Adobe Campaign 7
seo-description: null
page-status-flag: never-activated
uuid: 74464400-bdd4-42f8-bcbe-ace7095ae4e4
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
discoiquuid: f459dc07-b7db-4526-b428-852b51c9c00e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Migration dans Windows pour Adobe Campaign 7{#migrating-in-windows-for-adobe-campaign}

## Procédure générale {#general-procedure}

Les étapes de migration sous Windows sont les suivantes :

1. Arrêter les services : se référer à l&#39;arrêt [du](#service-stop)service,
1. Sauvegardez la base de données : voir [Sauvegarde de la base de données et installation](#back-up-the-database-and-the-current-installation)actuelle,
1. Migrer la plateforme : voir [Déploiement d’Adobe Campaign v7](#deploying-adobe-campaign-v7),
1. Migrer le serveur de redirection (IIS) : voir [Migration du serveur de redirection (IIS)](#migrating-the-redirection-server--iis-),
1. Redémarrage du service : reportez-vous à la section [Redémarrage des services](#re-starting-the-services),
1. Supprimer et nettoyer la version précédente d’Adobe Campaign : reportez-vous à la page [Suppression et nettoyage de la version](#deleting-and-cleansing-adobe-campaign-previous-version)précédente d’Adobe Campaign.

## Arrêt des services {#service-stop}

Arrêtez d&#39;abord tous les processus accédant à la base de données, sur toutes les machines concernées.

1. Les serveurs utilisant le module de redirection (service **webmdl**) doivent être arrêtés. Pour IIS, exécutez la commande suivante :

   ```
   iisreset /stop
   ```

1. Le module **mta** et ses modules fils (**mtachild**) doivent être arrêtés correctement à l&#39;aide des commandes :

   ```
   nlserver stop mta@<instance name>
   nlserver stop mtachild@<instance name>
   ```

1. Arrêtez les services Adobe Campaign sur tous les serveurs. Connectez-vous en tant qu&#39;administrateur et exécutez la commande :

   ```
   net stop nlserver6
   ```

   Si vous migrez à partir de la version v5.11, exécutez la commande suivante :

   ```
   net stop nlserver5
   ```

1. Sur chaque serveur, vérifiez que les services Adobe Campaign ont bien été arrêtés. Connectez-vous en tant qu&#39;administrateur et exécutez la commande :

   ```
   tasklist /FI "IMAGENAME eq nlserver*"
   ```

   La liste des processus actifs ainsi que leur identifiant (PID) correspondant apparaît.

   ```
   Image Name                     PID Session Name        Session#    Mem Usage
   ========================= ======== ================ =========== ============
   nlserver.exe                  3192 Console                    1     13,108 K
   ```

1. Si un ou plusieurs processus Adobe Campaign sont encore actifs ou bloqués au bout de quelques minutes, forcez leur arrêt. Connectez-vous en tant qu&#39;administrateur et exécutez la commande :

   ```
   taskkill /IM nlserver* /T
   ```

1. Si certains processus sont toujours actifs au bout de quelques minutes, vous pouvez forcer leur fermeture à l&#39;aide de la commande :

   ```
   taskkill /F /IM nlserver* /T
   ```

## Sauvegarde de la base et de l&#39;installation existante {#back-up-the-database-and-the-current-installation}

La procédure dépend de votre version précédente d&#39;Adobe Campaign :

### Migration à partir d&#39;Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5-11}

1. Sauvegardez la base de données Adobe Campaign.
1. Sauvegardez le répertoire **Neolane v5**, à l&#39;aide de la commande suivante :

   ```
   ren "Neolane v5" "Neolane v5.back"
   ```

   >[!CAUTION]
   >
   >Par mesure de précaution, nous vous recommandons vivement de zipper le dossier **Neolane v5.back**, et de le conserver à un autre emplacement que le serveur, sur un support sécurisé.

1. Dans la console de gestion des services Windows, désactivez le démarrage automatique du service Serveur Applicatif 5.11. Vous pouvez également utiliser la commande suivante :

   ```
   sc config nlserver5 start= disabled
   ```

1. Modifiez le **fichier config-`<instance name>`.xml** (dans **Neolane v5. back** folder) pour empêcher le **mta**, **wfserver**, **stat**, etc. à partir du démarrage automatique. Par exemple, remplacez **autoStart** par **_autoStart**.

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

### Migration à partir d&#39;Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6-02}

1. Sauvegardez la base de données Adobe Campaign.
1. Sauvegardez le répertoire **Neolane v6**, à l&#39;aide de la commande suivante :

   ```
   ren "Neolane v6" "Neolane v6.back"
   ```

   >[!CAUTION]
   >
   >Par mesure de précaution, nous vous recommandons vivement de zipper le dossier **Neolane v6.back**, et de le conserver à un autre emplacement que le serveur, sur un support sécurisé.

1. Dans la console de gestion des services Windows, désactivez le démarrage automatique du service Serveur Applicatif 6.02. Vous pouvez également utiliser la commande suivante :

   ```
   sc config nlserver6 start= disabled
   ```

1. Modifiez le **fichier config-`<instance name>`.xml** (dans **Neolane v6. back** folder) pour empêcher le **mta**, **wfserver**, **stat**, etc. à partir du démarrage automatique. Par exemple, remplacez **autoStart** par **_autoStart**.

   ```
   <?xml version='1.0'?>
   <serverconf>
     <shared>
       <dataStore hosts="myServer*" lang="en_US">
         <dataSource name="default">
           <dbcnx encrypted="1" login="myLogin" password="myPassword" provider="postgresql" server="myServer"/>
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

### Migration à partir d&#39;Adobe Campaign v6.1 {#migrating-from-adobe-campaign-v6-1}

1. Sauvegardez la base de données Adobe Campaign.
1. Sauvegardez le répertoire **Adobe Campaign v6**, à l&#39;aide de la commande suivante :

   ```
   ren "Adobe Campaign v6" "Adobe Campaign v6.back"
   ```

   >[!CAUTION]
   >
   >Par mesure de précaution, nous vous recommandons vivement de zipper le dossier **Adobe Campaign v6.back**, et de le conserver à un autre emplacement que le serveur, sur un support sécurisé.

1. Dans la console de gestion des services Windows, désactivez le démarrage automatique du service Serveur Applicatif 6.11. Vous pouvez également utiliser la commande suivante :

   ```
   sc config nlserver6 start= disabled
   ```

## Déploiement d&#39;Adobe Campaign v7 {#deploying-adobe-campaign-v7}

Le déploiement d&#39;Adobe Campaign se déroule en deux parties :

* L&#39;installation du build v7 : cette opération doit être effectuée sur chaque serveur.
* Le postupgrade : cette commande doit être lancée sur chaque instance.

Les étapes de déploiement d&#39;Adobe Campaign sont les suivantes :

1. Installez la version la plus récente d’Adobe Campaign v7 en exécutant le fichier d’installation **setup.exe** . For more on installing the Adobe Campaign server in Windows, refer to [this section](../../installation/using/installing-the-server.md).

   ![](assets/migration_wizard_1_7.png)

   >[!NOTE]
   >
   >Par défaut, Adobe Campaign v7 est installé dans le répertoire **C:\Program Files\Adobe\Adobe Campaign v7**.

1. Pour mettre à disposition le programme d&#39;installation de la console cliente, copiez le fichier **setup-client-7.0.XXXX.exe** dans le répertoire d&#39;installation d&#39;Adobe Campaign : **C:\Program Files\Adobe\Adobe Campaign v7\datakit\nl\eng\jsp**.

   >[!NOTE]
   >
   >Pour plus d&#39;informations sur l&#39;installation d&#39;Adobe Campaign sous Windows, consultez [cette section](../../installation/using/installing-the-server.md).

1. Préparez l&#39;instance à sa première utilisation à l&#39;aide des commandes suivantes :

   ```
   net start nlserver6-v7
   net stop nlserver6-v7
   ```

   >[!NOTE]
   >
   >Ces commandes permettent de créer le système de fichiers interne d&#39;Adobe Campaign v7 : répertoire **conf** (avec les fichiers **config-default.xml** et
**serverConf.xml**), répertoire **var**, etc.

1. Copiez et collez (écrasez) les fichiers de paramétrage et sous-dossiers de chaque instance via le fichier de sauvegarde **Neolane v5.back**, **Neolane v6.back** ou **Adobe Campaign v6.back** (selon la version à partir de laquelle vous migrez, voir [cette section](#back-up-the-database-and-the-current-installation)).
1. En fonction de la version à partir de laquelle vous migrez, exécutez les commandes suivantes :

   ```
   copy "Neolane v5.back"/conf/config-<instance name>.xml "Adobe Campaign v7"/conf/
   copy "Neolane v5.back"/customers/* "Adobe Campaign v7"/customers/
   copy "Neolane v5.back"/var/* "Adobe Campaign v7"/var/
   ```

   ```
   copy "Neolane v6.back"/conf/config-<instance name>.xml "Adobe Campaign v7"/conf/
   copy "Neolane v6.back"/customers/* "Adobe Campaign v7"/customers/
   copy "Neolane v6.back"/var/* "Adobe Campaign v7"/var/
   ```

   ```
   copy "Adobe Campaign v6.back"/conf/config-<instance name>.xml "Adobe Campaign v7"/conf/
   copy "Adobe Campaign v6.back"/customers/* "Adobe Campaign v7"/customers/
   copy "Adobe Campaign v6.back"/var/* "Adobe Campaign v7"/var/
   ```

   >[!CAUTION]
   >
   >Pour la première des commandes ci-dessous, ne copiez pas le fichier **config-default.xml**.

1. Dans les fichiers **serverConf.xml** et **config-default.xml** d&#39;Adobe Campaign v7, appliquez les paramétrages spécifiques dont vous disposiez dans la version précédente d&#39;Adobe Campaign. Pour le fichier **serverConf.xml**, utilisez le fichier **Neolane v5/conf/serverConf.xml.diff**, **Neolane v6/conf/serverConf.xml.diff** ou **Adobe Campaign v6/conf/serverConf.xml.diff**.

   >[!NOTE]
   >
   >Lors du report des paramétrages de la version précédente d&#39;Adobe Campaign vers Adobe Campaign v7, assurez-vous que les chemins vers les répertoires physiques pointent bien vers Adobe Campaign v7 (et pas Neolane v5, Neolane v6 ni Adobe Campaign v6).

1. Rechargez la configuration d&#39;Adobe Campaign v7 à l&#39;aide de la commande suivante :

   ```
   nlserver config -reload
   ```

1. Démarrez le processus de postupgrade à l&#39;aide de la commande suivante :

   ```
   nlserver config -postupgrade -instance:<instance name>
   ```

>[!CAUTION]
>
>Ne redémarrez pas les services Adobe Campaign à ce stade. Des modifications doivent préalablement être effectuées sur IIS.

## Migration du serveur de redirection (IIS) {#migrating-the-redirection-server--iis-}

A ce stade, le serveur IIS doit être arrêté. Reportez-vous à [Service stop](#service-stop).

1. Ouvrez la console **Internet Information Services (IIS) Manager**.
1. Modifiez les liaisons (ports d&#39;écoute) du site utilisé pour la version précédente d&#39;Adobe Campaign :

   * Right-click the site used for Adobe Campaign previous version and select **[!UICONTROL Edit bindings]**.
   * For each type of listen port (**[!UICONTROL http]** and/or **[!UICONTROL https]**), select the appropriate line and click **[!UICONTROL Edit]**.
   * Saisissez un autre port que celui qui est renseigné. Par défaut, le port d&#39;écoute est 80 pour le http et 443 pour le https. Vérifiez que le nouveau port est disponible.

      ![](assets/_migration_iis_3_611.png)

      >[!NOTE]
      >
      >Si votre serveur IIS embarque plusieurs sites web pour Adobe Campaign configurés de manière avancée (port commun et adresses IP différentes), veuillez vous rapprocher de votre administrateur.

1. Créez un nouveau site web pour Adobe Campaign v7 :

   * Cliquez avec le bouton droit sur le **[!UICONTROL Sites]** dossier et sélectionnez **[!UICONTROL Add Web Site...]**.

      ![](assets/_migration_iis_4.png)

   * Renseignez le nom du site, par exemple **Adobe Campaign v7**.
   * Le chemin d’accès au répertoire de base du site Web n’est pas utilisé, mais le **[!UICONTROL Physical access path]** champ doit être saisi. Entrez le chemin d&#39;accès IIS par défaut : **C:\inetpub\wwwroot**.
   * Cliquez sur le bouton **[!UICONTROL Connect as...]** en tant que et assurez-vous que l’ **[!UICONTROL Application user]** option est sélectionnée.
   * Vous pouvez laisser les valeurs par défaut dans les **[!UICONTROL IP address]** champs et **[!UICONTROL Port]** . Si vous souhaitez utiliser d’autres valeurs, assurez-vous que l’adresse IP et/ou le port sont disponibles.
   * Cochez la **[!UICONTROL Start Web site immediately]** case.

      ![](assets/_migration_iis_5_7.png)

1. Exécutez le script **iis_neolane_setup.vbs** permettant de configurer automatiquement le paramétrage des ressources utilisées par le serveur Adobe Campaign sur le répertoire virtuel créé précédemment.

   * Ce fichier se trouve dans le répertoire **`[Adobe Campaign v7]`\tomcat-7\conf file **, où&#x200B;**`[Adobe Campaign v7]`**est le chemin d’accès au répertoire d’installation d’Adobe Campaign. La commande d’exécution du script est la suivante (pour les administrateurs) :

      ```
      cd C:\Program Files (x86)\Adobe Campaign\Adobe Campaign v7\tomcat-7\conf
      cscript iis_neolane_setup.vbs
      ```

   * Cliquez sur **[!UICONTROL OK]** pour confirmer l&#39;exécution du script.

      ![](assets/s_ncs_install_iis7_parameters_step2_7.png)

   * Saisissez le numéro du site Web que vous avez créé précédemment pour Adobe Campaign v7 et cliquez sur **[!UICONTROL OK]**.

      ![](assets/s_ncs_install_iis7_parameters_step3_7.png)

   * Un message de confirmation doit s&#39;afficher :

      ![](assets/s_ncs_install_iis7_parameters_step7_7.png)

   * In the **[!UICONTROL Content view]** tab, make sure the Website configuration is correctly configured with Adobe Campaign resources:

      ![](assets/s_ncs_install_iis7_parameters_step6_7.png)

      >[!NOTE]
      >
      >Si l&#39;arborescence n&#39;est pas affichée, redémarrez le Gestionnaire de service Internet (IIS).
      >
      >Les étapes suivantes de configuration de IIS sont décrites dans [cette section](../../installation/using/integration-into-a-web-server-for-windows.md#configuring-the-iis-web-server).

## Zones de sécurité {#security-zones}

Si vous effectuez une migration depuis la version 6.02 ou une version antérieure, vous devez configurer vos zones de sécurité avant de démarrer les services. For more information, refer to [Security](../../migration/using/general-configurations.md#security).

## Redémarrage des services {#re-starting-the-services}

Sur chacun des serveurs suivants, démarrez IIS puis les services Adobe Campaign :

1. Serveur de tracking/redirection.
1. Serveur de mid-sourcing.
1. Serveur marketing.

Before going on to the next step, run a full test of the new installation, make sure there are no regressions and that everything works by following all the recommendations in the [General configurations](../../migration/using/general-configurations.md) section.

## Suppression et nettoyage de la version précédente d&#39;Adobe Campaign {#deleting-and-cleansing-adobe-campaign-previous-version}

La procédure dépend de votre version précédente d&#39;Adobe Campaign :

### Adobe Campaign v5 {#adobe-campaign-v5}

Avant de supprimer et nettoyer l&#39;installation d&#39;Adobe Campaign v5, il est impératif de suivre les recommandations ci-dessous :

* Effectuez une validation complète de la nouvelle installation par les équipes fonctionnelles.
* Ne procédez à la désinstallation d&#39;Adobe Campaign v5 qu&#39;une fois que vous êtes certain qu&#39;un retour arrière n&#39;est pas nécessaire.

1. Dans IIS, supprimez le site web **Neolane v5** puis le pool d&#39;applications **Neolane v5**.
1. Renommez le dossier **Neolane v5.back** en **Neolane v5**.
1. Désinstallez Adobe Campaign v5 à l&#39;aide de l&#39;assistant d&#39;ajout/suppression de programme.

   ![](assets/migration_wizard_2.png)

1. Supprimez le service Windows **nlserver5** à l&#39;aide de la commande suivante :

   ```
   sc delete nlserver5
   ```

1. Redémarrez le serveur.

### Adobe Campaign v6.02 {#adobe-campaign-v6-02}

Avant de supprimer et nettoyer l&#39;installation d&#39;Adobe Campaign v6.02, il est impératif de suivre les recommandations ci-dessous :

* Effectuez une validation complète de la nouvelle installation par les équipes fonctionnelles.
* Ne procédez à la désinstallation d&#39;Adobe Campaign v6.02 qu&#39;une fois que vous êtes certain qu&#39;un retour arrière n&#39;est pas nécessaire.

1. Dans IIS, supprimez le site web **Neolane v6** puis le pool d&#39;applications **Neolane v6**.
1. Renommez le dossier **Neolane v6.back** en **Neolane v6**.
1. Désinstallez Adobe Campaign v6.02 à l&#39;aide de l&#39;assistant d&#39;ajout/suppression de programme.

   ![](assets/migration_wizard_2.png)

1. Redémarrez le serveur.

### Adobe Campaign v6.1 {#adobe-campaign-v6-1}

Avant de supprimer et nettoyer l&#39;installation d&#39;Adobe Campaign v6, il est impératif de suivre les recommandations ci-dessous :

* Effectuez une validation complète de la nouvelle installation par les équipes fonctionnelles.
* Ne procédez à la désinstallation d&#39;Adobe Campaign v6 qu&#39;une fois que vous êtes certain qu&#39;un retour arrière n&#39;est pas nécessaire.

1. Dans IIS, supprimez le site web **Adobe Campaign v6** puis le pool d&#39;applications **Adobe Campaign v6**.
1. Renommez le dossier **Adobe Campaign v6.back** en **Adobe Campaign v6**.
1. Désinstallez Adobe Campaign v6 à l&#39;aide de l&#39;assistant d&#39;ajout/suppression de programme.

   ![](assets/migration_wizard_2.png)

1. Redémarrez le serveur.

