---
product: campaign
title: Configurer l’accès à SAP HANA
description: Découvrez comment configurer l'accès à SAP HANA dans FDA
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 39bfe775-e182-4a0b-ad3c-b7a901297c90
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: ht
source-wordcount: '0'
ht-degree: 100%

---

# Configurer l’accès à SAP HANA {#configure-access-to-sap-hana}



Utilisez l’option Campaign [Federated Data Access](../../installation/using/about-fda.md) (FDA) pour traiter les informations stockées dans des bases de données externes. Suivez les étapes ci-dessous pour configurer l’accès à SAP HANA.

1. Configuration de la [base de données SAP HANA](#sap-config)
1. Configuration du [compte externe](#sap-external) SAP HANA dans Campaign

## Pilotes SAP HANA {#sap-config}

La connexion à une base de données externe SAP HANA en FDA requiert certains paramétrages additionnels sur le serveur Adobe Campaign :

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

1. Définissez les variables d’environnement du serveur Adobe Campaign :

   * **LD_LIBRARY_PATH** : doit inclure le lien vers votre client SAP HANA (/usr/sap/hdbclient/libodbcHDB.so par défaut).
   * **ODBCINI** : emplacement du fichier odbc.ini (par exemple /etc/odbc.ini).

## Compte externe SAP HANA{#sap-external}

Le compte externe SAP HANA permet de connecter l’instance Campaign à la base de données externe SAP HANA.

1. Dans l’**[!UICONTROL Explorateur]** Campaign, cliquez sur **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Plateforme]** &#39;>&#39; **[!UICONTROL Comptes externes]**.

1. Cliquez sur **[!UICONTROL Nouveau]**, puis sélectionnez **[!UICONTROL Base de données externe]** comme **[!UICONTROL Type]**.

1. Pour configurer le compte externe **[!UICONTROL SAP Hana]**, vous devez indiquer les informations suivantes :

   * **[!UICONTROL Type]** : SAP Hana

   * **[!UICONTROL Serveur]** : URL du serveur SAP Hana

   * **[!UICONTROL Compte]** : nom de l’utilisateur

   * **[!UICONTROL Mot de passe]** : mot de passe du compte utilisateur
