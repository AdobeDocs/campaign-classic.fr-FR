---
title: Configurer l’accès à SAP HANA
description: Découvrez comment configurer l'accès à SAP HANA dans FDA
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
source-wordcount: '278'
ht-degree: 71%

---


# Configurer l’accès à SAP HANA {#configure-access-to-sap-hana}

Utilisez l’option Campaign [Federated Data Access](../../installation/using/about-fda.md) (FDA) pour traiter les informations stockées dans des bases de données externes. Suivez les étapes ci-dessous pour configurer l’accès à SAP HANA.

1. Configuration de la base de données [SAP HANA](#sap-config)
1. Configuration du [compte externe](#sap-external) SAP HANA à Campaign

## Pilotes SAP HANA {#sap-config}

La connexion à une base de données externe SAP HANA en FDA requiert certains paramétrages additionnels sur le serveur Adobe Campaign :

1. Installez les pilotes ODBC pour SAP HANA, en fonction du système d’exploitation que vous utilisez :

   * **hdb_client_linux.tgz pour Linux. Une fois le fichier décompressé, lancez la commande hdbinst et suivez les instructions pour terminer l’installation des pilotes.**
   * **Hdb_client_windows.zip** pour Windows. Décompressez le fichier et lancez l’exécutable : **hdbinst.exe**. Suivez les instructions de l’assistant pour terminer l’installation des pilotes.

1. Configurez le pilote ODBC. La configuration peut être réalisée dans les fichiers standard : /etc/odbc.ini pour les paramètres généraux et /etc/odbcinst.ini pour la déclaration des pilotes.

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      
      [HDB]
      Driver=HDBODBC
      servernode=localhost:39013 (this value depend of your server)
      User:SYSTEM
      ```

      « InstallDir » correspond à l’emplacement du fichier **odbcinst.ini**.

   * **/etc/odbcinst.ini**

      ```
      [HDBODBC]
      Description = "SmartCloudPT HANA"
      Driver = /usr/sap/hdbclient/libodbcHDB.so
      ```

1. Définissez les variables d’environnement du serveur Adobe Campaign :

   * **LD_LIBRARY_PATH** : doit inclure le lien vers votre client SAP HANA (/usr/sap/hdbclient/libodbcHDB.so par défaut).
   * **ODBCINI** : emplacement du fichier odbc.ini (par exemple /etc/odbc.ini).

## COMPTE EXTERNE SAP HANA{#sap-external}

Le compte externe SAP HANA vous permet de connecter votre instance Campaign à votre base de données externe SAP HANA.

1. From Campaign **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Cliquez sur **[!UICONTROL Nouveau]**, puis sélectionnez **[!UICONTROL Base de données externe]** comme **[!UICONTROL Type]**.

1. Pour configurer le compte externe **[!UICONTROL SAP Hana]**, vous devez indiquer les informations suivantes :

   * **[!UICONTROL Type]** : SAP Hana

   * **[!UICONTROL Serveur]** : URL du serveur SAP Hana

   * **[!UICONTROL Compte]** : nom de l’utilisateur

   * **[!UICONTROL Mot de passe]** : mot de passe du compte utilisateur
