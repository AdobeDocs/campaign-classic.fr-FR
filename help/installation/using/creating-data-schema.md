---
product: campaign
title: Créer un schéma de données pour FDA
description: Découvrir comment créer le schéma de données pour FDA
feature: Installation, Instance Settings, Federated Data Access
exl-id: 8702499b-1700-4d1f-a0e0-f7a9dfb4b88f
TQID: 'https://experienceleague.adobe.com/eC7jDm92g943ymcfEQjaeevS7qzIJWJR0zCtnP2Ny7o'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
    internal-label: Schemas
  - id: 7f0a1ee5-eeb8-5478-a9cd-b1896f033118
    internal-label: Instance Settings
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
    internal-label: PI
  - id: e656c701-3899-4db3-989c-de0980ddfffa
    internal-label: Installation
  - id: ee3dfd63-9a21-4961-9f24-ea3385284a21
    internal-label: Federated Data Access
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: ht
source-wordcount: '201'
ht-degree: 100%
---
# Créer le schéma des données {#creating-the-data-schema}



Pour créer un schéma sur une base de données externe :

1. Cliquez sur le bouton **[!UICONTROL Nouveau]** au-dessus de la liste des schémas de données et sélectionnez **[!UICONTROL Accéder à des données externes]**.

   ![](assets/wf_new_schema_fda.png)

1. Saisissez un **[!UICONTROL Espace de noms]** et un **[!UICONTROL Nom]** pour le schéma, puis sélectionnez le **[!UICONTROL Compte externe]** qui permettra la connexion à la base de données. Cela permet d’accéder à la liste des tables disponibles dans la base externe.

   ![](assets/wf_new_schema_select_table_fda.png)

1. Dans le champ **[!UICONTROL Nom de la table]**, choisissez la table contenant les données à collecter.

   Snowflake vous permet de sélectionner vos vues ici si l’utilisateur de la base de données a reçu les privilèges appropriés. Notez que lorsque vous utilisez des vues, Adobe Campaign ne peut pas générer automatiquement le schéma XML. Vous devez donc le créer vous-même. Pour plus d’informations sur les vues, consultez la [documentation Snowflake](https://docs.snowflake.com/fr/user-guide/views-introduction.html).

   ![](assets/wf_new_schema_select_table_fda.png)

1. Cliquez sur **[!UICONTROL Ok]** pour valider. Adobe Campaign détecte automatiquement la structure de la table sélectionnée et génère le schéma logique. Veuillez noter qu&#39;Adobe Campaign ne génère pas de liens.

1. Cliquez sur **[!UICONTROL Enregistrer]** pour en valider la création.

   >[!CAUTION]
   >
   >Avec Snowflake, une clé primaire est obligatoire.

   ![](assets/wf_new_schema_generate_fda.png)

Les index sont crées automatiquement lors d&#39;un mapping de table (mapping standard ou FDA).
