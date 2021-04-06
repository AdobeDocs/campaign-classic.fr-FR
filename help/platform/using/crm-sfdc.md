---
solution: Campaign Classic
product: campaign
title: Campaign - Salesforce CRM Connector
description: Connecter Campaign et Salesforce.com
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 236e8d355b8cd89a0ebe88d5fca7ff78ca62db8e
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 56%

---


# Connecter Campaign et Microsoft Dynamics 365{#connect-to-msdyn}

Dans cette page, vous apprendrez comment connecter le Campaign Classic à **Salesforce**.

La synchronisation des données s&#39;effectue via une activité de workflow dédiée. [En savoir plus](../../platform/using/crm-data-sync.md).


Le compte externe   vous permet d&#39;importer et d&#39;exporter des données Salesforce vers Adobe Campaign.
Pour configurer CRM Connector for Salesforce, procédez comme suit :

1. Créez un compte externe à partir du nœud **[!UICONTROL Administration > Plateforme > Comptes externes]** de l&#39;arborescence d&#39;Adobe Campaign.
1. Sélectionnez **[!UICONTROL Salesforce.com]**.
1. Saisissez les paramètres pour activer la connexion.

   ![](assets/ext_account_17.png)

   Pour configurer le compte externe Salesforce CRM afin de l&#39;utiliser avec Adobe Campaign, vous devez fournir les détails suivants :

   * **[!UICONTROL Compte]**
utilisé pour se connecter à Salesforce CRM.

   * **[!UICONTROL Mot de]**
passeMot de passe utilisé pour se connecter à Salesforce CRM.

   * **[!UICONTROL Identifiant]**
du clientPour savoir où trouver votre identifiant de client, reportez-vous à cette  [page](https://help.salesforce.com/articleView?id=000205876&amp;type=1).

   * **[!UICONTROL Jeton de sécuritéPour savoir où trouver votre jeton de sécurité, reportez-vous à cette]**
page [ ](https://help.salesforce.com/articleView?id=000205876&amp;type=1).

   * ****
version de l&#39;APISélectionnez la version de l&#39;API.
1. Exécutez l&#39;assistant de configuration pour générer la table CRM disponible : l&#39;assistant de configuration vous permet de collecter des tables et de créer le schéma correspondant.

   ![](assets/crm_connectors_sfdc_launch.png)

   >[!NOTE]
   >
   >Pour valider la configuration, vous devez procéder à une déconnexion/reconnexion à la console Adobe Campaign.

1. Vérifiez le schéma généré dans Adobe Campaign, sous le noeud **[!UICONTROL Administration > Paramétrage > Schéma de données]**.

   Exemple pour le schéma **Salesforce** :

   ![](assets/crm_connectors_sfdc_table.png)

1. Une fois le schéma créé, vous pouvez synchroniser automatiquement les énumérations de Salesforce à Adobe Campaign.

   Pour ce faire, cliquez sur **[!UICONTROL Synchronisation des énumérations...]** et sélectionnez la énumération Adobe Campaign correspondant à la énumération Salesforce.



   ![](assets/crm_connectors_sfdc_enum.png)

   >[!NOTE]
   >
   >Vous pouvez remplacer toutes les valeurs d&#39;une énumération Adobe Campaign par celles du CRM : pour cela, sélectionnez **[!UICONTROL Oui]** dans la colonne **[!UICONTROL Remplacer]**.


   Cliquez sur **[!UICONTROL Suivant]** puis **[!UICONTROL Démarrer]** pour lancer l&#39;import de la liste.

1. Vérifiez les valeurs importées sous le menu **[!UICONTROL Administration > Plateforme > Enumérations]**.

   ![](assets/crm_connectors_sfdc_exe.png)

   >[!NOTE]
   >
   > Plusieurs énumérations de sélection ne sont pas prises en charge.

Campaign et Salesforce.com sont maintenant connectés. Vous pouvez configurer la synchronisation des données entre les deux systèmes.

Pour synchroniser les données entre les données Adobe Campaign et SFDC, vous devez créer un flux de travail et utiliser l’activité **[!UICONTROL Connecteur de gestion de la relation client]**.

![](assets/crm_connectors_sfdc_wf.png)

Pour en savoir plus sur la synchronisation des données, consultez [cette page](../../platform/using/crm-data-sync.md).

