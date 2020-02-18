---
title: Créer une connexion partagée
seo-title: Créer une connexion partagée
description: Créer une connexion partagée
seo-description: null
page-status-flag: never-activated
uuid: 30d6d23b-72c6-4454-8d6b-a10102f89262
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: instance-configuration
discoiquuid: 7f471ac1-cd6a-4371-977e-52d60ce8d968
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 65043155ab6ff1fe556283991777964bb43c57ce

---


# Créer une connexion partagée{#creating-a-shared-connection}

>[!CAUTION]
>
>* Les extensions de schéma effectuées sur les schémas utilisés par les [workflows techniques de Message Center](../../message-center/using/technical-workflows.md) sur les instances de pilotage ou d&#39;exécution doivent être dupliquées sur les autres instances utilisées par le module des messages transactionnels Adobe Campaign.
>* L&#39;instance de contrôle et la ou les instances d&#39;exécution doivent être installées sur des machines différentes. Elles ne peuvent pas partager la même instance Campaign.
>



## Instance de pilotage {#control-instance}

Si vous disposez d’une architecture ventilée, vous devez spécifier les instances d’exécution liées à l’instance de contrôle et les connecter. Les modèles de message transactionnel sont déployés sur les instances d’exécution. La connexion entre l’instance de contrôle et les instances d’exécution est créée en configurant le **[!UICONTROL Execution instance]** type de comptes externes. Vous devez créer autant de comptes externes que d’instances d’exécution.

>[!NOTE]
>
>Lorsque des instances d’exécution sont utilisées par plusieurs instances de contrôle, les données peuvent être divisées par dossier et par opérateur. Pour plus d’informations, reportez-vous à [Utilisation de plusieurs instances](#using-several-control-instances)de contrôle.

Procédez comme suit pour créer un compte externe de type instance d&#39;exécution :

1. Accédez au **[!UICONTROL Administration > Platform > External accounts]** dossier.
1. Select one of the execution instance type external accounts provided out-of-the-box with Adobe Campaign, right-click and choose **[!UICONTROL Duplicate]** .

   ![](assets/messagecenter_create_extaccount_001.png)

1. Modifiez le libellé selon vos besoins.

   ![](assets/messagecenter_create_extaccount_002.png)

1. Select the **[!UICONTROL Enabled]** option to make the external account operational.

   ![](assets/messagecenter_create_extaccount_003.png)

1. Indiquez l&#39;adresse du serveur sur lequel est installée l&#39;instance d&#39;exécution.

   ![](assets/messagecenter_create_extaccount_004.png)

1. Le compte doit correspondre à l&#39;Agent Message Center tel qu&#39;il est défini dans le dossier des opérateurs. Par défaut, le compte fourni d&#39;usine par Adobe Campaign est **[!UICONTROL mc]** .

   ![](assets/messagecenter_create_extaccount_005.png)

1. Entrez le mot de passe du compte tel qu&#39;il a été défini dans le dossier des opérateurs.

   >[!NOTE]
   >
   >Pour éviter de saisir un mot de passe chaque fois que vous vous connectez à l’instance, vous pouvez spécifier l’adresse IP de l’instance de contrôle dans l’instance d’exécution. For more on this, refer to [Execution instance](#execution-instance).

1. Indiquez la méthode de rapatriement qui doit être utilisée par l&#39;instance d&#39;exécution.

   Les données à récupérer sont transmises par l&#39;instance d&#39;exécution à l&#39;instance de pilotage, afin d&#39;enrichir les historiques des messages transactionnels et des événements.

   ![](assets/messagecenter_create_extaccount_007.png)

   La collecte des données s&#39;effectue soit par un service Web qui utilise un accès en HTTP/HTTPS, soit via le module Federated Data Access (FDA).

   >[!NOTE]
   >
   >Veuillez noter que lorsque vous utilisez FDA sur HTTP, seules les instances d’exécution utilisant une base de données Postgres sont prises en charge. Les bases de données MSSQL ou Oracle ne sont pas prises en charge.

   La deuxième méthode est recommandée si l&#39;instance de pilotage peut avoir un accès direct aux bases de données des instances d&#39;exécution. Dans le cas contraire, choisissez l&#39;accès par service Web. Le compte FDA à spécifier correspond à la connexion vers les bases des différentes instances d&#39;exécution créée sur l&#39;instance de pilotage.

   ![](assets/messagecenter_create_extaccount_008.png)

   Reportez-vous à la section [Accès à une base de données externe](../../platform/using/about-fda.md) pour plus d&#39;informations sur le Federated Data Access (FDA).

1. Click **[!UICONTROL Test the connection]** to make sure the control instance and the execution instance are linked up.

   ![](assets/messagecenter_create_extaccount_006.png)

1. Chaque instance d’exécution doit être associée à un identifiant. Cet identifiant peut être attribué sur chaque instance d’exécution soit manuellement, à l’aide de l’assistant de déploiement (voir [Identification des instances](../../message-center/using/identifying-execution-instances.md)d’exécution), soit automatiquement, en cliquant sur le bouton **Initialiser la connexion** de l’instance de contrôle.

   ![](assets/messagecenter_create_extaccount_006bis.png)

## Instance d&#39;exécution {#execution-instance}

Pour que l&#39;instance de contrôle puisse se connecter à l&#39;instance d&#39;exécution sans avoir à fournir de mot de passe, il suffit de saisir l&#39;adresse IP de l&#39;instance de contrôle dans la section des droits d&#39;accès du Centre **des** messages. Toutefois, les mots de passe vides sont interdits par défaut.

Pour utiliser un mot de passe vide, accédez aux instances d’exécution et définissez une zone de sécurité limitée à l’adresse IP du système d’informations qui diffuse les événements. Cette zone de sécurité doit autoriser les mots de passe vides et accepter les connexions `<identifier> / <password>` de type. Voir à ce propos [cette section](../../installation/using/configuring-campaign-server.md#defining-security-zones).

>[!NOTE]
>
>Lorsque des instances d’exécution sont utilisées par plusieurs instances de contrôle, les données peuvent être divisées par dossier et par opérateur. Pour plus d’informations, reportez-vous à [Utilisation de plusieurs instances](#using-several-control-instances)de contrôle.

1. Accédez au dossier de l’opérateur dans l’instance d’exécution ( **[!UICONTROL Administration > Access management > Operators]** ).
1. Sélectionnez l&#39;agent **Message Center**.

   ![](assets/messagecenter_operator_001.png)

1. Sélectionnez l’ **[!UICONTROL Edit]** onglet, cliquez sur **[!UICONTROL Access rights]** , puis sur le **[!UICONTROL Edit the access parameters...]** lien.

   ![](assets/messagecenter_operator_002.png)

1. Dans la **[!UICONTROL Access settings]** fenêtre, cliquez sur le **[!UICONTROL Add a trusted IP mask]** lien et ajoutez l’adresse IP de l’instance de contrôle.

   ![](assets/messagecenter_operator_003.png)

## Utilisation de plusieurs instances de contrôle {#using-several-control-instances}

Vous pouvez mutualiser un cluster d&#39;exécution entre différentes instances de pilotage. Ce type d&#39;architecture requiert le paramétrage suivant.

Par exemple, si votre entreprise gère deux marques, chacune avec sa propre instance de contrôle : **Contrôle 1** et **Contrôle 2**. Deux instances d’exécution sont également utilisées. Vous devez entrer un opérateur de Centre de messages différent pour chaque instance de contrôle : un opérateur **mc1** pour l’instance **Control 1** et un opérateur **mc2** pour l’instance **Control 2.**

Dans l’arborescence de toutes les instances d’exécution, créez un dossier par opérateur (**Dossier 1** et **Dossier 2**) et limitez l’accès aux données de chaque opérateur à leur dossier.

### Paramétrage des instances de pilotage {#configuring-control-instances}

1. Dans l’instance de contrôle **Control 1** , créez un compte externe par instance d’exécution, puis saisissez l’opérateur **mc1** dans chaque compte externe. L’opérateur **mc1** sera ensuite créé sur toutes les instances d’exécution (voir [Configuration des instances](#configuring-execution-instances)d’exécution).

   ![](assets/messagecenter_multi_control_1.png)

1. Dans l’instance de contrôle **Control 2** , créez un compte externe par instance d’exécution, puis saisissez l’opérateur **mc2** dans chaque compte externe. L’opérateur **mc2** sera ensuite créé sur toutes les instances d’exécution (voir [Configuration des instances](#configuring-execution-instances)d’exécution).

   ![](assets/messagecenter_multi_control_2.png)

   >[!NOTE]
   >
   >For more on configuring a control instance, refer to [Control instance](#control-instance).

### Paramétrage des instances d&#39;exécution {#configuring-execution-instances}

Pour utiliser plusieurs instances de pilotage, ce paramétrage doit être réalisé sur TOUTES les instances d&#39;exécution.

1. Créez un dossier par opérateur dans le **[!UICONTROL Administration > Production > Message Center]** noeud : **Dossier 1** et **Dossier 2**. Pour plus d’informations sur la création de dossiers et de vues, voir [Plateforme](../../platform/using/access-management.md#folders-and-views).

   ![](assets/messagecenter_multi_control_3.png)

1. Créez les opérateurs **mc1** et **mc2** en dupliquant l&#39;opérateur Message Center fourni par défaut (**mc**). La création d&#39;opérateurs est présentée dans [cette section](../../platform/using/access-management.md#operators).

   ![](assets/messagecenter_multi_control_4.png)

   >[!NOTE]
   >
   >**Les opérateurs mc1** et **mc2** doivent avoir **[!UICONTROL Message Center execution]** des droits et ne peuvent pas accéder à la console client Adobe Campaign. Un opérateur doit toujours être lié à une zone de sécurité. Voir à ce propos [cette section](../../installation/using/configuring-campaign-server.md#defining-security-zones).

1. For each operator, check the **[!UICONTROL Restrict to information found in sub-folders of]** box, and select the relevant folder (**Folder 1** for the **mc1** operator and **Folder 2** for the **mc2** operator).

   ![](assets/messagecenter_multi_control_5.png)

1. Attribuez à chaque opérateur des autorisations de lecture et d’écriture pour son dossier. Pour ce faire, cliquez avec le bouton droit sur le dossier et sélectionnez **[!UICONTROL Properties]** . Sélectionnez ensuite l’ **[!UICONTROL Security]** onglet et ajoutez l’opérateur approprié (**mc1** pour **Folder 1** et **mc2** pour Folder 2). **** Vérifiez que les **[!UICONTROL Read/Write data]** cases sont cochées.

   ![](assets/messagecenter_multi_control_6.png)

