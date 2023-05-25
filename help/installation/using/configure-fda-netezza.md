---
product: campaign
title: Configurer l’accès à Netezza
description: Découvrez comment configurer l’accès à Netezza dans FDA
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: b148d34b-4060-4c54-9cb2-9e712a7c17d7
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: ht
source-wordcount: '389'
ht-degree: 100%

---

# Configurer l’accès à Netezza {#configure-access-to-netezza}



Utilisez l’option Campaign [Federated Data Access](../../installation/using/about-fda.md) (FDA) pour traiter les informations stockées dans des bases de données externes. Suivez les étapes ci-dessous pour configurer l’accès à Netezza.

1. Installation et configuration des [pilotes Netezza](#netezza-config)
1. Configuration du [compte externe](#netezza-external) Netezza dans Campaign

## Configuration de Netezza {#netezza-config}

La connexion à une base de données externe Netezza en FDA requiert les paramétrages additionnels ci-dessous sur le serveur Adobe Campaign :

1. Installez les pilotes ODBC pour Netezza, en fonction du système d&#39;exploitation que vous utilisez :

   * **nz-linuxclient-v7.2.0.0.tar.gz pour Linux. Sélectionnez le dossier correspondant à votre système d&#39;exploitation (linux ou linux64) et lancez la commande unpack. Vous pouvez laisser l&#39;installation s&#39;effectuer dans le répertoire par défaut proposé : &quot;/usr/local/nz&quot;.**
   * **nz-winclient-v7.2.0.0.zip pour Windows. Décompressez le fichier et lancez le script exécutable correspondant à votre système d&#39;exploitation : nzodbcsetup.exe ou nzodbcsetup64.exe. Suivez les indications de l&#39;assistant pour finaliser l&#39;installation des pilotes.**

1. Configurez le pilote ODBC. La configuration peut être réalisée dans les fichiers standard : **/etc/odbc.ini** pour les paramètres généraux et **/etc/odbcinst.ini** pour la déclaration des pilotes.

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      ```

      « InstallDir » correspond à l’emplacement du fichier odbcinst.ini.

   * **/etc/odbcinst.ini**

      ```
      [ODBC Drivers]
      NetezzaSQL = Installed
      
      [NetezzaSQL]
      Driver           = /usr/local/nz/lib/libnzsqlodbc3.so
      Setup            = /usr/local/nz/lib/libnzsqlodbc3.so
      APILevel         = 1
      ConnectFunctions = YYN
      Description      = Netezza ODBC driver
      DriverODBCVer    = 03.51
      DebugLogging     = false
      LogPath          = /tmp
      UnicodeTranslationOption = utf8
      CharacterTranslationOption = all
      PreFetch         = 256
      Socket           = 16384
      ```

1. Définissez les variables d’environnement du serveur Adobe Campaign :

   * **LD_LIBRARY_PATH** : /usr/local/nz/lib et /usr/local/nz/lib64. &quot;/usr/local/nz&quot; correspond au répertoire d’installation proposé par défaut lors de l’installation des pilotes. Indiquez ici le répertoire que vous avez sélectionné pour l’installation.
   * **ODBCINI** : emplacement du fichier odbc.ini (par exemple /etc/odbc.ini).
   * **NZ_ODBC_INI_PATH** : emplacement du fichier odbc.ini. Netezza requiert également cette seconde variable pour l’utilisation du fichier odbc.ini.

## Compte externe Netezza {#netezza-external}

Le compte externe Netezza vous permet de connecter l’instance Campaign à la base de données externe Netezza.

1. Dans l’**[!UICONTROL Explorateur]** Campaign, cliquez sur **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Plateforme]** &#39;>&#39; **[!UICONTROL Comptes externes]**.

1. Cliquez sur **[!UICONTROL Nouveau]**, puis sélectionnez **[!UICONTROL Base de données externe]** comme **[!UICONTROL Type]**.

1. Pour configurer le compte externe **[!UICONTROL Netezza]**, vous devez indiquer les informations suivantes :

   * **[!UICONTROL Type]** : Netezza

   * **[!UICONTROL Serveur]** : URL du serveur Netezza

   * **[!UICONTROL Compte]** : nom de l’utilisateur

   * **[!UICONTROL Mot de passe]** : mot de passe du compte utilisateur

   * **[!UICONTROL Base de données]** : nom de la base de données

>[!NOTE]
>
>Les opérations sur les schémas comportant des clés primaires générées automatiquement ne sont pas prises en charge.
>
>La table utilise la clause **Organize on** sur le premier index défini dans le schéma. Comme cette clause est limitée de 1 à 4 colonnes avec Netezza, cet index ne peut pas contenir plus de 4 colonnes.
