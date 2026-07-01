---
product: campaign
title: Configurer l’accès à Netezza
description: Découvrez comment configurer l’accès à Netezza dans FDA
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: b148d34b-4060-4c54-9cb2-9e712a7c17d7
TQID: https://experienceleague.adobe.com/HiTQ6eoYcjp8pLqNmqLhiDTNhplE4ipnYlWuRFOZvog
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
subfeature_v2: id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
topic_v2: id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: ht
source-wordcount: 391
ht-degree: 100%

---

# Configurer l’accès à Netezza {#configure-access-to-netezza}



Utilisez l’option Campaign [Federated Data Access](../../installation/using/about-fda.md) (FDA) pour traiter les informations stockées dans des bases de données externes. Suivez les étapes ci-dessous pour configurer l’accès à Netezza.

1. Installation et configuration des [pilotes Netezza](#netezza-config)
1. Configuration du [compte externe](#netezza-external) Netezza dans Campaign

## Configuration de Netezza {#netezza-config}

La connexion à une base de données externe Netezza en FDA requiert les paramétrages additionnels ci-dessous sur le serveur Adobe Campaign :

1. Installez les pilotes ODBC pour Netezza, en fonction du système d&#39;exploitation que vous utilisez :

   * **nz-linuxclient-v7.2.0.0.tar.gz** pour Linux.Sélectionnez le dossier correspondant à votre système d’exploitation (linux ou linux64) et lancez la commande unpack.Vous pouvez laisser l’installation s’effectuer dans le répertoire par défaut proposé : « /usr/local/nz ».
   * **nz-winclient-v7.2.0.0.zip** pour Windows.Décompressez le fichier et lancez le script exécutable correspondant à votre système d’exploitation : nzodbcsetup.exe ou nzodbcsetup64.exe.Suivez les instructions de l’assistant pour terminer l’installation des pilotes.

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

   * **LD_LIBRARY_PATH** : /usr/local/nz/lib et /usr/local/nz/lib64.« /usr/local/nz » correspond au référentiel d’installation proposé par défaut lors de l’installation des pilotes.Ici, vous devez spécifier le référentiel que vous avez sélectionné pour l’installation.
   * **ODBCINI** : emplacement du fichier odbc.ini (par exemple /etc/odbc.ini).
   * **NZ_ODBC_INI_PATH** : emplacement du fichier odbc.ini.Netezza requiert également cette seconde variable pour l’utilisation du fichier odbc.ini.

## Compte externe Netezza {#netezza-external}

Le compte externe Netezza vous permet de connecter l’instance Campaign à la base de données externe Netezza.

1. Dans l’**[!UICONTROL Explorateur]** Campaign, cliquez sur **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Plateforme]** &#39;>&#39; **[!UICONTROL Comptes externes]**.

1. Cliquez sur **[!UICONTROL Nouveau]**, puis sélectionnez **[!UICONTROL Base de données externe]** comme **[!UICONTROL Type]**.

1. Pour configurer le compte externe **[!UICONTROL Netezza]**, vous devez indiquer les informations suivantes :

   * **[!UICONTROL Type]** : Netezza

   * **[!UICONTROL Serveur]** : URL du serveur Netezza

   * **[!UICONTROL Compte]** : nom de l’utilisateur

   * **[!UICONTROL Mot de passe]** : mot de passe du compte d’utilisateur

   * **[!UICONTROL Base de données]** : nom de la base de données

>[!NOTE]
>
>Les opérations sur les schémas comportant des clés primaires générées automatiquement ne sont pas prises en charge.
>
>La table utilisera la clause **Organize on** sur le premier index défini dans le schéma.Comme cette clause est limitée entre 1 et 4 colonnes avec Netezza, cet index ne peut pas contenir plus de 4 colonnes.
