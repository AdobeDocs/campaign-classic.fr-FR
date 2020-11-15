---
title: Configurer l’accès à Sybase IQ
description: Découvrez comment configurer l'accès à Sybase IQ dans FDA
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
translation-type: tm+mt
source-git-commit: 9bbde65aea6735e30e95e75c2b6ae5445d4a2bdd
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 67%

---


# Configurer l’accès à Sybase IQ {#configure-access-to-sybase-iq}

Utilisez l’option Campaign **Federated Data Access** (FDA) pour traiter les informations stockées dans des bases de données externes. Suivez les étapes ci-dessous pour configurer l&#39;accès à Sybase IQ.

1. Configuration de la base de données [Sybase IQ](#configuring-sybase)
1. Configuration du [compte externe](#sybase-external) Sybase IQ dans Campaign

## Configuration de Sybase IQ {#configuring-sybase}

La connexion à une base de données externe Sybase IQ en FDA nécessite des configurations supplémentaires ci-dessous sur le serveur Adobe Campaign.

>[!NOTE]
>
>Before starting, make sure the **unixodbc** package is on the server.

1. Installez **iq_odbc**. Une erreur peut se produire à la fin de l’installation. Celle-ci peut être ignorée.

1. Installez **iq_client_common**. Une erreur Java peut se produire à la fin de l’installation. Celle-ci peut être ignorée.

1. Configurez le pilote ODBC. La configuration peut être réalisée dans les fichiers standard : /etc/odbc.ini pour les paramètres généraux et /etc/odbcinst.ini pour la déclaration des pilotes :

   * **/etc/odbc.ini**(remplacez les valeurs telles que `<server_alias>` par les vôtres) :

      ```
      [ODBC Data Sources]
      <server_alias>=libdbodbc.so
      
      [<server_alias>]
      Driver=/opt/sybase/IQ-16_0/lib64/libdbodbc16.so
      Description=<description>
      Username=<username>
      Password=<password>
      ServerName=<server_name>
      CommLinks=tcpip(host=<host>)
      ```

   * **/etc/odbcinst.ini**

      ```
      [ODBC DRIVERS]
      SAP SybaseIQ=Installed
      
      [SAP SybaseIQ]
      Driver=/opt/sybase/IQ-16_0/lib64/libdbodbc16.so
      ```

1. Ajoutez le chemin d’accès de la nouvelle bibliothèque libodbc16.so dans la variable LD_LIBRARY_PATH. Pour ce faire :

   * Si vous utilisez un fichier customer.sh pour déclarer le chemin d’accès : ajoutez le chemin d’accès /opt/sybase/IQ-16_0/lib64 pour la variable LD_LIBRARY_PATH.
   * Sinon, utilisez une commande Unix.

## Compte externe Sybase IQ {#sybase-external}

Le compte externe Sybase IQ vous permet de connecter votre instance Campaign à votre base de données externe Sybase IQ.

1. From Campaign **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Cliquez sur **[!UICONTROL Nouveau]**, puis sélectionnez **[!UICONTROL Base de données externe]** comme **[!UICONTROL Type]**.

1. Pour configurer le compte externe **[!UICONTROL Sybase IQ]**, vous devez indiquer les informations suivantes :

   * **[!UICONTROL Type]** : ODBC (Sybase ASE, Sybase IQ)

   * **[!UICONTROL Serveur]** : correspond à la connexion ODBC (`<server_alias>`) définie à l’étape 5. Il ne s’agit pas nécessairement du nom du serveur lui-même.

   * **[!UICONTROL Compte]** : nom de l’utilisateur

   * **[!UICONTROL Mot de passe]** : mot de passe du compte utilisateur

   * **[!UICONTROL Base de données]** : nom de la base de données

>[!NOTE]
>
>Pour Windows, vous devez installer le client Sybase IQ sur le serveur Adobe Campaign et créer une connexion ODBC. Veillez à créer une source de données système lorsque le serveur Adobe Campaign (nlserver) s’exécute en tant que service sous Windows.

