---
solution: Campaign Classic
product: campaign
title: Comptes externes
description: Découvrez comment créer des comptes externes
audience: platform
content-type: reference
topic-tags: administration-basics
translation-type: tm+mt
source-git-commit: 4efe5f8a9130e7925194e56e088b3745c0cbd11a
workflow-type: tm+mt
source-wordcount: '1706'
ht-degree: 98%

---


# Comptes externes{#external-accounts}

Un ensemble de comptes externes prédéfinis est livré avec Adobe Campaign. Pour établir des connexions avec des systèmes externes, vous pouvez créer des comptes externes.

Les comptes externes sont utilisés par des processus techniques, tels que des workflows techniques ou des workflows des opérations. Lors de la configuration d’un transfert de fichier dans un workflow ou d’un échange de données avec une autre application (Adobe Target, Experience Manager, etc.), vous devez sélectionner un compte externe.

Vous pouvez configurer les types de comptes externes suivants :

* [Compte externe Routage](#routing-external-account)
* [Compte externe FTP](#ftp-external-account)
* [Compte externe de base de données externe](#external-database-external-account)
* [Compte externe Web Analytics](#web-analytics-external-account)
* [Compte externe Facebook Connect](#facebook-connect-external-account)
* [Compte externe d’instance d’exécution](#execution-instance-external-account)
* [Compte externe Adobe Experience Cloud](#adobe-experience-cloud-external-account)
* [Compte externe SFTP](#sftp-external-account)
* [Compte externe Adobe Experience Manager](#adobe-experience-manager-external-account)
* [Compte externe Amazon Simple Storage Service (S3)](#amazon-simple-storage-service--s3--external-account)
* [Compte externe Microsoft Dynamics CRM](#microsoft-dynamics-crm-external-account)
* [Compte externe Salesforce CRM](#salesforce-crm-external-account)

## Création d’un compte externe {#creating-an-external-account}

Pour créer un compte externe, procédez comme suit : Les paramètres détaillés dépendent du type de compte externe.

1. Dans l’**[!UICONTROL Explorateur]** Campaign, sélectionnez **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Plateforme]** &#39;>&#39; **[!UICONTROL Comptes externes]**.

   ![](assets/ext_account_1.png)

1. Cliquez sur le bouton **[!UICONTROL Nouveau]**.

   ![](assets/ext_account_2.png)

1. Définissez un **[!UICONTROL Libellé]** et un **[!UICONTROL Nom interne]**.
1. Sélectionnez le **[!UICONTROL Type]** de compte externe que vous voulez créer.
1. Configurez l’accès au compte en spécifiant les informations de connexion en fonction du type de compte externe choisi.

   Les informations nécessaires sont généralement fournies par le fournisseur du serveur auquel vous vous connectez.

1. Cochez l’option **[!UICONTROL Activé]** pour activer la connexion.
1. Cliquez sur **[!UICONTROL Enregistrer]**.

Le compte externe est créé et ajouté à la liste des comptes externes.

## Compte externe Mails rebonds {#bounce-mails-external-account}

Le compte externe **Mails rebonds** spécifie le compte POP3 externe à utiliser pour se connecter au service de messagerie. Pour plus d’informations sur ce compte externe, consultez cette [page](../../workflow/using/inbound-emails.md).

Tous les serveurs configurés pour l’accès POP3 peuvent être utilisés pour recevoir les mails rebonds.

![](assets/ext_account_6.png)

Pour configurer le compte externe **[!UICONTROL Mails rebonds (defaultPopAccount)]** :

* **[!UICONTROL Serveur]**

   URL du serveur POP3.

* **[!UICONTROL Port]**

   Numéro de port de la connexion POP3. Le port par défaut est 110.

* **[!UICONTROL Compte]**

   Nom de l&#39;utilisateur.

* **[!UICONTROL Mot de passe]**

   Mot de passe du compte de l&#39;utilisateur.

* **[!UICONTROL Chiffrement]**

   Type de chiffrement choisi entre **[!UICONTROL Par défaut]**, **[!UICONTROL POP3 + STARTTLS]**, **[!UICONTROL POP3]** ou **[!UICONTROL POP3S]**.

## Compte externe Routage {#routing-external-account}

Le compte externe **[!UICONTROL Routage]** vous permet de configurer chaque canal disponible dans Adobe Campaign en fonction des packages installés.

![](assets/ext_account_7.png)

Les canaux suivants peuvent être configurés :

* [Email](../../installation/using/deploying-an-instance.md#email-channel-parameters)
* [Mobile (SMS)](../../delivery/using/sms-channel.md#creating-an-smpp-external-account)
* [Phone](../../delivery/using/steps-about-delivery-creation-steps.md#other-channels)
* [Canal Courrier](../../delivery/using/about-direct-mail-channel.md)
* [Agence](../../delivery/using/steps-about-delivery-creation-steps.md#other-channels)
* [Facebook](../../social/using/publishing-on-facebook-walls.md#delegating-write-access-to-adobe-campaign)
* [Twitter](../../social/using/configuring-publishing-on-twitter.md)
* [Canal iOS](../../delivery/using/configuring-the-mobile-application.md)
* [Canal Android](../../delivery/using/configuring-the-mobile-application-android.md)

## Compte externe FTP {#ftp-external-account}

Le compte externe FTP vous permet de configurer et de tester l’accès à un serveur en dehors d’Adobe Campaign. Pour configurer des connexions à des systèmes externes tels que des serveurs FTP 898 utilisés pour les transferts de fichiers, vous pouvez créer vos propres comptes externes. Voir à ce sujet [cette page](../../workflow/using/file-transfer.md).

Pour ce faire, spécifiez dans ce compte externe l’adresse et les informations de connexion utilisées pour établir la connexion au serveur FTP.

![](assets/ext_account_8.png)

* **[!UICONTROL Serveur]**

   Nom du serveur FTP.

* **[!UICONTROL Port]**

   Numéro de port de la connexion FTP. Le port par défaut est 21.

* **[!UICONTROL Compte]**

   Nom de l&#39;utilisateur.

* **[!UICONTROL Mot de passe]**

   Mot de passe du compte de l&#39;utilisateur.

* **[!UICONTROL Chiffrement]**

   Type de chiffrement choisi entre **[!UICONTROL Aucun]** et **[!UICONTROL SSL]**.

Pour savoir où trouver ces informations de connexion, consultez [cette page](https://help.dreamhost.com/hc/en-us/articles/115000675027-FTP-overview-and-credentials).

## Compte externe de base de données externe {#external-database-external-account}

Utilisez le compte externe de type **Base de données externe** pour vous connecter à une base de données externe. En savoir plus sur l’option Federated Data Access (FDA) dans [cette section](../../installation/using/about-fda.md).

Les bases de données externes compatibles avec Campaign sont répertoriées dans la [matrice de compatibilité](../../rn/using/compatibility-matrix.md)

![](assets/ext_account_11.png)

Les paramètres de configuration du compte externe dépendent du moteur de base de données. En savoir plus dans les sections suivantes :

* Configurer l’accès à [Azure Synapse](../../installation/using/configure-fda-synapse.md)
* Configurer l’accès à [Hadoop](../../installation/using/configure-fda-hadoop.md)
* Configurer l’accès à [Oracle](../../installation/using/configure-fda-oracle.md)
* Configurer l’accès à [Netezza](../../installation/using/configure-fda-netezza.md)
* Configurer l’accès à [SAP HANA](../../installation/using/configure-fda-sap-hana.md)
* Configurer l’accès à [Snowflake](../../installation/using/configure-fda-snowflake.md)
* Configurer l’accès à [Sybase IQ](../../installation/using/configure-fda-sybase.md)
* Configurer l’accès à [Teradata](../../installation/using/configure-fda-teradata.md)

## Compte externe Web Analytics {#web-analytics-external-account}

Le compte externe **[!UICONTROL Web Analytics (Adobe Analytics - Connecteur de données)]** vous permet de transférer des données d’Adobe Analytics à Adobe Campaign sous la forme de segments. Inversement, il envoie des indicateurs et des attributs aux campagnes email diffusées par Adobe Campaign à Adobe Analytics - Connecteur de données.

![](assets/ext_account_10.png)

Pour ce compte externe, la formule de calcul pour les URL trackées doit être enrichie, et la connexion entre les deux solutions doit être validée. Voir à ce sujet [cette page](../../platform/using/adobe-analytics-data-connector.md#step-2--create-the-external-account-in-campaign).

## Compte externe Facebook Connect {#facebook-connect-external-account}

Le compte externe **[!UICONTROL Facebook Connect]** vous permet d’afficher du contenu personnalisé dans vos applications Facebook, ce qui facilite l’acquisition de prospects par l’intermédiaire de ce réseau social.

Pour chaque application Facebook, vous devez créer un compte externe de type **[!UICONTROL Facebook Connect]**. Voir à ce sujet [cette page](../../social/using/creating-a-facebook-application.md#configuring-external-accounts).

![](assets/ext_account_12.png)

* **[!UICONTROL Mode d’hébergement]**

   Mode d’hébergement de l’application entre **[!UICONTROL hébergée chez un partenaire]** et **[!UICONTROL hébergée sur cette instance]**.

* **[!UICONTROL ID de l’application]**

   ID de l’application de votre application Facebook.

* **[!UICONTROL Clé secrète]**

   Secret de l’application de votre application Facebook..

Si vous choisissez le mode Hébergée sur cette instance, vous devez coller l’URL sécurisée du canevas dans le champ **Jeux Web Facebook (https)** sur Facebook.

Pour savoir où trouver ces informations de connexion, consultez [cette page](https://developers.facebook.com/docs/facebook-login/access-tokens).

## Compte externe d’instance d’exécution {#execution-instance-external-account}

Si vous possédez une architecture répartie, vous devez spécifier les instances d’exécution liées à l’instance de contrôle et les connecter. Les modèles de messages transactionnels sont déployés sur l’instance d’exécution.

![](assets/ext_account_13.png)

* **[!UICONTROL URL]**

   URL du serveur sur lequel est installée l’instance d’exécution.

* **[!UICONTROL Compte]**

   Nom du compte qui doit correspondre à l’Agent Message Center tel qu’il a été défini dans le dossier de l’opérateur.

* **[!UICONTROL Mot de passe]**

   Mot de passe du compte tel qu’il a été défini dans le dossier de l’opérateur.

Pour plus d’informations sur cette configuration, consultez [cette page](../../message-center/using/creating-a-shared-connection.md#control-instance).

## Compte externe Adobe Experience Cloud {#adobe-experience-cloud-external-account}

Pour vous connecter à la console Adobe Campaign à l’aide d’un Adobe ID, vous devez configurer le compte externe **[!UICONTROL Adobe Experience Cloud (MAC)]**.

![](assets/ext_account_9.png)

* **[!UICONTROL Serveurs IMS]**

   URL de votre serveur IMS. Assurez-vous que les instances de test et de production pointent sur le même point de terminaison de production IMS.

* **[!UICONTROL Scope IMS]**

   Les périmètres définis ici doivent être un sous-ensemble de ceux provisionnés par IMS.

* **[!UICONTROL Identifiant du client IMS]**

   ID de votre client IMS.

* **[!UICONTROL Secret client IMS]**

   Informations de connexion de votre secret client IMS..

* **[!UICONTROL Serveur de rappel]**

   URL d’accès à votre instance Adobe Campaign..

* **[!UICONTROL Identifiant de l’organisation IMS]**

   Identifiant de votre organisation IMS. Pour trouver votre identifiant d’organisation, consultez cette [page](https://docs.adobe.com/content/help/fr-FR/core-services/interface/manage-users-and-products/faq.html) (**Où puis-je trouver mon identifiant de l’organisation IMS ?**).

* **[!UICONTROL Masque de correspondance]**

   Syntaxe qui permettra la synchronisation des noms de configuration dans Enterprise Dashboard avec les groupes dans Adobe Campaign.

* **[!UICONTROL Serveur]**

   URL de votre instance Adobe Experience Cloud.

* **[!UICONTROL Tenant]**

   Nom de votre tenant Adobe Experience Cloud.

Pour plus d’informations sur cette configuration, consultez [cette page](../../integrations/using/configuring-ims.md).

## Compte externe SFTP            {#sftp-external-account}

Le compte externe SFTP vous permet de configurer et de tester l’accès à un serveur en dehors d’Adobe Campaign. Pour configurer des connexions à des systèmes externes tels que des serveurs SFTP utilisés pour les transferts de fichiers, vous pouvez créer vos propres comptes externes. Voir à ce sujet [cette page](../../workflow/using/file-transfer.md).

![](assets/ext_account_4.png)

* **[!UICONTROL Serveur]**

   URL du serveur SFTP.

* **[!UICONTROL Port]**

   Numéro de port de connexion FTP. Le port par défaut est 22.

* **[!UICONTROL Compte]**

   Nom du compte utilisé pour se connecter au serveur SFTP.

* **[!UICONTROL Mot de passe]**

   Mot de passe utilisé pour se connecter au serveur SFTP.

## Compte externe Adobe Experience Manager {#adobe-experience-manager-external-account}

Le compte externe **[!UICONTROL AEM (instance AEM)]** vous permet de gérer le contenu de vos diffusions email, ainsi que vos formulaires directement dans Adobe Experience Manager.

![](assets/ext_account_5.png)

* **[!UICONTROL Serveur]**

   URL du serveur Adobe Experience Manager.

* **[!UICONTROL Port]**

   Nom du compte utilisé pour se connecter à l’instance de création Adobe Experience Manager.

* **[!UICONTROL Mot de passe]**

   Mot de passe utilisé pour se connecter à l’instance de création Adobe Experience Manager.

Voir à ce propos cette [section](../../integrations/using/about-adobe-experience-manager.md).

## Compte externe Amazon Simple Storage Service (S3){#amazon-simple-storage-service--s3--external-account}

Le connecteur Amazon Simple Storage Service (S3) peut être utilisé pour importer ou exporter des données vers Adobe Campaign. Il peut être configuré dans une activité de workflow. Voir à ce sujet [cette page](../../workflow/using/file-transfer.md).

![](assets/ext_account_3.png)

Lors de la configuration de ce nouveau compte externe, vous devez indiquer les informations suivantes :

* **[!UICONTROL Serveur du compte AWS S3]**

   URL du serveur qui doit être renseignée de la manière suivante :

   ```
   <S3bucket name>.s3.amazonaws.com/<s3object path>
   ```

* **[!UICONTROL ID de la clé d’accès AWS]**

   Pour savoir où trouver votre ID de la clé d’accès AWS, consultez [cette page](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys) .

* **[!UICONTROL Clé d’accès secrète à AWS]**

   Pour savoir où trouver votre clé d’accès secrète à AWS, consultez [cette page](https://aws.amazon.com/fr/blogs/security/wheres-my-secret-access-key/).

* **[!UICONTROL Région AWS]**

   Pour en savoir plus sur la région AWS, consultez cette [page](https://aws.amazon.com/fr/about-aws/global-infrastructure/regions_az/).

* La case à cocher **[!UICONTROL Utiliser le cryptage coté serveur]** vous permet de stocker votre fichier en mode crypté dans S3.

Pour savoir où trouver l’ID de la clé d’accès et la clé d’accès secrète, consultez la [documentation](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys) d’Amazon Web Services .

## Compte externe Microsoft Dynamics CRM {#microsoft-dynamics-crm-external-account}

Le compte externe **[!UICONTROL Microsoft Dynamics CRM]** vous permet d’importer et d’exporter des données Microsoft Dynamics vers Adobe Campaign.

Pour en savoir plus sur Campaign - Connecteur Microsoft Dynamics CRM dans cette [page](../../platform/using/crm-ms-dynamics.md).

>[!NOTE]
>
> **[!UICONTROL Les types de]** déploiement sur site et  **[!UICONTROL Office 365]** sont désormais obsolètes. [En savoir plus](../../rn/using/deprecated-features.md).

Avec le type de déploiement **[!UICONTROL API web]** et l’authentification **[!UICONTROL Informations de connexion et mot de passe]**, vous devez fournir les détails suivants :

![](assets/ext_account_14.png)

* **[!UICONTROL Compte]**

   Compte utilisé pour se connecter à Microsoft CRM.

* **[!UICONTROL Serveur]**

   URL de votre serveur Microsoft CRM.

* **[!UICONTROL Identifiant du client]**

   ID du client qui se trouve sur le portail de gestion Microsoft Azure au niveau de la catégorie **[!UICONTROL Mettre à jour votre code]**, dans le champ **[!UICONTROL ID du client]**.

* **[!UICONTROL Version CRM]**

   Version du CRM parmi **[!UICONTROL Dynamics CRM 2007]**, **[!UICONTROL Dynamics CRM 2015]** et **[!UICONTROL Dynamics CRM 2016]**.

Avec le type de déploiement **[!UICONTROL API web]** et l’authentification **[!UICONTROL Certificat]**, vous devez fournir les détails suivants :

![](assets/ext_account_22.png)

* **[!UICONTROL Serveur]**

   URL de votre serveur Microsoft CRM.

* **[!UICONTROL Clé privée (encodée en Base64)]**

   Clé privée encodée en Base64

* **[!UICONTROL Identifiant de clé personnalisé]**

* **[!UICONTROL ID de clé]**

* **[!UICONTROL Identifiant du client]**

   ID du client qui se trouve sur le portail de gestion Microsoft Azure au niveau de la catégorie **[!UICONTROL Mettre à jour votre code]**, dans le champ **[!UICONTROL ID du client]**.

* **[!UICONTROL Version CRM]**

   Version du CRM parmi **[!UICONTROL Dynamics CRM 2007]**, **[!UICONTROL Dynamics CRM 2015]** et **[!UICONTROL Dynamics CRM 2016]**.

Pour plus d’informations sur cette configuration, consultez [cette page](../../platform/using/crm-connectors.md).

## Compte externe Salesforce CRM {#salesforce-crm-external-account}

Le compte externe **[!UICONTROL Salesforce CRM]** vous permet d’importer et d’exporter des données Salesforce vers Adobe Campaign.

![](assets/ext_account_17.png)

Pour configurer le compte externe Salesforce CRM afin de l’utiliser avec Adobe Campaign, vous devez fournir les détails suivants :

* **[!UICONTROL Compte]**

   Compte utilisé pour se connecter à Salesforce CRM.

* **[!UICONTROL Mot de passe]**

   Mot de passe utilisé pour se connecter à Salesforce CRM.

* **[!UICONTROL Identifiant du client]**

   Pour savoir où trouver votre identifiant du client, consultez [cette page](https://help.salesforce.com/articleView?id=000205876&amp;type=1).

* **[!UICONTROL Jeton de sécurité]**

   Pour savoir où trouver votre jeton de sécurité, consultez [cette page](https://help.salesforce.com/articleView?id=000205876&amp;type=1).

* **[!UICONTROL Version de l’API]**

   Version de l’API parmi **[!UICONTROL Version 37]**, **[!UICONTROL Version 21]** et **[!UICONTROL Version 15]**.

Pour ce compte externe, vous devez configurer votre Salesforce CRM à l’aide de l’assistant de configuration.

Pour plus d’informations sur cette configuration, consultez [cette page](../../platform/using/crm-connectors.md).
