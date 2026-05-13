---
product: campaign
title: Campaign - Connecteur CRM Salesforce
description: Découvrez comment connecter Campaign et Salesforce
feature: Salesforce Integration
exl-id: 94a1f00d-e952-4edd-9012-f71c87b897ca
hide: true
TQID: https://experienceleague.adobe.com/LeUJ-F5dAECUrtkbvgwL0BN88Alofnh2rBWe7hIVGgI
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 361
ht-degree: 85%

---

# Connecter Campaign et Salesforce.com{#connect-to-sfdc}



Sur cette page, vous allez découvrir comment connecter Campaign Classic à **Salesforce**.

La synchronisation des données s&#39;effectue via une activité de workflow dédiée. [En savoir plus](../../platform/using/crm-data-sync.md).


Le compte externe vous permet d’importer et d’exporter des données Salesforce vers Adobe Campaign.
Pour configurer le connecteur CRM pour Salesforce, procédez comme suit :

1. Créez un compte externe à partir du nœud **[!UICONTROL Administration > Plateforme > Comptes externes]** de l’arborescence d’Adobe Campaign.
1. Sélectionnez **[!UICONTROL Salesforce.com]**.
1. Saisissez les paramètres pour activer la connexion.

   ![](assets/ext_account_17.png)

   Pour configurer le compte externe Salesforce CRM afin de l’utiliser avec Adobe Campaign, vous devez fournir les détails suivants :

   * **[!UICONTROL Compte]**
Compte utilisé pour se connecter à Salesforce CRM

   * **[!UICONTROL Mot de passe]**
Mot de passe utilisé pour se connecter au CRM Salesforce.

   * **[!UICONTROL Identifiant client]**
Pour savoir où trouver votre identifiant client, consultez cette [page](https://help.salesforce.com/articleView?id=000205876&type=1).

   * **[!UICONTROL Jeton de sécurité]**
Pour savoir où trouver votre jeton de sécurité, consultez cette [page](https://help.salesforce.com/articleView?id=000205876&type=1).

   * Version de l’API **&#x200B;**
Sélectionnez la version de l’API.
1. Exécutez l’assistant de configuration pour générer le tableau CRM disponible : l’assistant de configuration vous permet de collecter des tableaux et de créer le schéma correspondant.

   ![](assets/crm_connectors_sfdc_launch.png)

   >[!NOTE]
   >
   >Pour valider la configuration, vous devez procéder à une déconnexion/reconnexion à la console Adobe Campaign.

1. Vérifiez le schéma généré dans Adobe Campaign, sous le noeud **[!UICONTROL Administration > Paramétrage > Schéma de données]**.

   Exemple pour le schéma **Salesforce** :

   ![](assets/crm_connectors_sfdc_table.png)

1. Une fois le schéma créé, vous pouvez synchroniser automatiquement les énumérations entre Salesforce et Adobe Campaign.

   Pour cela, cliquez sur le lien **[!UICONTROL Synchronisation des énumérations...]** et choisissez l’énumération d’Adobe Campaign correspondant à celle de Salesforce.



   ![](assets/crm_connectors_sfdc_enum.png)

   >[!NOTE]
   >
   >Vous pouvez remplacer toutes les valeurs d&#39;une énumération Adobe Campaign par celles du CRM : pour cela, sélectionnez **[!UICONTROL Oui]** dans la colonne **[!UICONTROL Remplacer]**.


   Cliquez sur **[!UICONTROL Suivant]** puis **[!UICONTROL Démarrer]** pour lancer l&#39;import de la liste.

1. Vérifiez les valeurs importées sous le menu **[!UICONTROL Administration > Plateforme > Énumérations]**.

   ![](assets/crm_connectors_sfdc_exe.png)

   >[!NOTE]
   >
   > La sélection multiple d’énumérations n’est pas prise en charge.

Campaign et Salesforce.com sont maintenant connectés. Vous pouvez configurer la synchronisation des données entre les deux systèmes.

Pour synchroniser les données entre Adobe Campaign et SFDC, vous devez créer un workflow et utiliser l’activité **[!UICONTROL Connecteur CRM]**.

![](assets/crm_connectors_sfdc_wf.png)

Pour en savoir plus sur la synchronisation des données, consultez [cette page](../../platform/using/crm-data-sync.md).
