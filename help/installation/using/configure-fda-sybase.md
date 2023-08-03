---
product: campaign
title: Configurer l’accès à Sybase IQ
description: Découvrez comment configurer l’accès à Sybase IQ dans FDA
feature: Installation, Federated Data Access
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 0fdf8259-5cab-4a9d-adb3-6c55ec5c8851
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: ht
source-wordcount: '342'
ht-degree: 100%

---

# Configurer l’accès à Sybase IQ {#configure-access-to-sybase-iq}



Utilisez l’option Campaign **Federated Data Access** (FDA) pour traiter les informations stockées dans des bases de données externes. Suivez les étapes ci-dessous pour configurer l’accès à Sybase IQ.

1. Configuration de la [base de données Sybase IQ](#configuring-sybase)
1. Configuration du [compte externe](#sybase-external) Sybase IQ dans Campaign

## Configuration de Sybase IQ {#configuring-sybase}

La connexion à une base de données externe Sybase IQ dans FDA nécessite les paramétrages additionnels ci-dessous sur le serveur Adobe Campaign.

>[!NOTE]
>
>Vérifiez que le package **unixodbc** se trouve sur le serveur.

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

Le compte externe Sybase IQ permet de connecter votre instance Campaign à la base de données externe Sybase IQ.

1. Dans l’**[!UICONTROL Explorateur]** Campaign, cliquez sur **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Plateforme]** &#39;>&#39; **[!UICONTROL Comptes externes]**.

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
