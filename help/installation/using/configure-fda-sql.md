---
product: campaign
title: Configurer l’accès à Microsoft SQL Server
description: Découvrez comment configurer l’accès à Microsoft SQL Server
source-git-commit: 26ae7ff1f0837a9a50057d97b00422a288b9dc7a
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 39%

---

# Configurer l’accès à Microsoft SQL Server {#configure-fda-sql}

![](../../assets/v7-only.svg)

Utiliser Campaign **Federated Data Access** (FDA) pour traiter les informations stockées dans une base externe Microsoft SQL Server. Suivez les étapes ci-dessous pour Configuration de l&#39;accès à [!DNL Microsoft SQL Server].

1. Configurer [!DNL Microsoft SQL Server] on [CentOS](#sql-centos).
1. Configurez [!DNL Microsoft SQL Server] sous [Linux](#sql-linux).
1. Configurer [!DNL Microsoft SQL Server] on [Windows](#sql-windows).
1. Configuration du [compte externe](#sql-external) [!DNL Microsoft SQL Server] dans Campaign

## Microsoft SQL Server sous CentOS {#sql-centos}

>[!NOTE]
>
> [!DNL Microsoft SQL Server] est disponible sur CentOS 7 et 6.

Pour effectuer la configuration de [!DNL Microsoft SQL Server] sur CentOS, procédez comme suit :

1. Téléchargez et installez le pilote ODBC SQL avec la commande suivante :

   ```
   sudo su
   curl https://packages.microsoft.com/config/rhel/7/prod.repo > /etc/yum.repos.d/mssql-release.repo
   exit
   sudo yum remove unixODBC-utf16 unixODBC-utf16-devel #to avoid conflicts
   sudo ACCEPT_EULA=Y yum install msodbcsql
   ```

1. Dans Adobe Campaign, vous pouvez ensuite configurer votre compte externe [!DNL Microsoft SQL Server]. Pour plus d&#39;informations sur la configuration de votre compte externe, voir [cette section](#sql-external).

## Microsoft SQL Server sous Linux {#sql-linux}

>[!NOTE]
>
> Si vous exécutez une ancienne version d’Adobe Campaign (antérieure à la version 7.2.1), vous devez installer `unix ODBC drivers`.

1. Téléchargez le pilote ODBC MS à partir de [cette page](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/msodbcsql17/).

1. Exécutez la commande suivante en tant qu’utilisateur root :

   ```
   # install the mssql odbc that was downloaded
   dpkg -i msodbcsql17_17.7.1.1-1_amd64.deb
   # accept the license terms
   ```

1. Dans Adobe Campaign, vous pouvez ensuite configurer votre compte externe [!DNL Microsoft SQL Server]. Pour plus d&#39;informations sur la configuration de votre compte externe, voir [cette section](#sql-external).

## Microsoft SQL Server sous Windows {#sql-windows}

Pour configurer [!DNL Microsoft SQL Server] sous Windows :

1. Sous Windows, cliquez sur **[!UICONTROL Panneau de Contrôle]** &#39;>&#39; **[!UICONTROL Système et sécurité]** &#39;>&#39; **[!UICONTROL Outils d’administration]**&#39;>&#39; **[!UICONTROL Sources de données ODBC (64 bits)]**.

1. Dans la **[!UICONTROL Sources de données ODBC (64 bits)]** nouvelle fenêtre, cliquez sur **[!UICONTROL Ajouter...]**.

1. Vérifiez si SQL Server Native Client v11 est répertorié dans la variable **[!UICONTROL Créer une source de données]** fenêtre.

1. Si SQL Server Native Client n’est pas répertorié, vous pouvez le télécharger dans [cette page](https://www.microsoft.com/en-my/download/details.aspx?id=36434).

1. Dans Adobe Campaign, vous pouvez ensuite configurer votre compte externe [!DNL Microsoft SQL Server]. Pour plus d&#39;informations sur la configuration de votre compte externe, voir [cette section](#sql-external).

## Compte externe Microsoft SQL Server {#sql-external}

Vous devez créer un compte externe [!DNL Microsoft SQL Server] pour connecter votre instance Campaign à votre base de données [!DNL Microsoft SQL Server] externe.

1. Depuis l&#39;**[!UICONTROL Explorateur]** Campaign, cliquez sur **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Plateforme]** &#39;>&#39; **[!UICONTROL Comptes externes]**.

1. Cliquez sur **[!UICONTROL Nouveau]**.

1. Sélectionnez **[!UICONTROL Base de données externe]** en tant que **[!UICONTROL Type]** de compte externe.

1. Sous **[!UICONTROL Configuration]**, sélectionnez [!DNL Microsoft SQL Server] dans le menu déroulant **[!UICONTROL Type]**.

   ![](assets/sql.png)

1. Configurez la variable **[!UICONTROL Microsoft SQL Server]** authentification de compte externe :

   * **[!UICONTROL Serveur]**: URL de la [!DNL Microsoft SQL Server] serveur.

   * **[!UICONTROL Compte]** : nom de l’utilisateur.

   * **[!UICONTROL Mot de passe]** : mot de passe du compte utilisateur.

   * **[!UICONTROL Base de données]** : nom de la base de données (facultatif).

   * **[!UICONTROL Fuseau horaire]** : Fuseau horaire défini dans [!DNL Microsoft SQL Server]. [En savoir plus](https://docs.microsoft.com/en-us/sql/t-sql/functions/current-timezone-transact-sql?view=sql-server-ver15)

1. Cliquez sur l’onglet **[!UICONTROL Paramètres]**, puis sur le bouton **[!UICONTROL Déployer les fonctions]** pour créer des fonctions.

   >[!NOTE]
   >
   >Pour que toutes les fonctions soient disponibles, vous devez créer les fonctions SQL Adobe Campaign dans la base de données distante. Pour plus d’informations, consultez cette [page](../../configuration/using/adding-additional-sql-functions.md).

1. Cliquez sur **[!UICONTROL Enregistrer]** lorsque la configuration est terminée.

Le connecteur prend en charge les options suivantes :

| Option | Description |
|---|---|
| Authentification | Type d’authentification pris en charge par le connecteur. Current supported value : ActiveDirectoryMSI. <br> Voir à ce sujet l’exemple 8 de la section [Documentation Microsoft](https://docs.microsoft.com/en-us/sql/connect/odbc/using-azure-active-directory?view=sql-server-ver15#example-connection-strings). |
| Chiffrer | Indique si les connexions utilisent le chiffrement TLS sur le réseau. Les valeurs possibles sont **yes/mandatory (18.0 et versions ultérieures)**, **non/facultatif (18.0 et versions ultérieures)**, et **strict (18.0 et versions ultérieures)**. La valeur par défaut est définie sur **oui** dans les versions 18.0 et ultérieures et **non** dans les versions précédentes. <br>Voir à ce sujet la section [Documentation Microsoft](https://docs.microsoft.com/en-us/sql/connect/odbc/dsn-connection-string-attribute?view=azure-sqldw-latest#encrypt). |
| TrustServerCertificate | Active le chiffrement à l’aide d’un certificat de serveur autosigné, lorsqu’il est utilisé avec **Chiffrer**. <br>Valeurs acceptées : **oui** ou **non** (valeur par défaut, ce qui signifie que le certificat du serveur sera validé). |

