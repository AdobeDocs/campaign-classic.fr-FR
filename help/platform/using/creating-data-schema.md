---
title: Accès à une base de données externe
seo-title: Accès à une base de données externe
description: Accès à une base de données externe
seo-description: null
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9a26ec7ed1c8463270ac9f97079f49e00d5b258e

---


# Créer le schéma des données {#creating-the-data-schema}

Pour créer un schéma sur une base de données externe :

1. Cliquez sur le **[!UICONTROL New]** bouton au-dessus de la liste des schémas de données et choisissez **[!UICONTROL Access external data]**.

   ![](assets/wf_new_schema_fda.png)

1. Saisissez le nom du schéma et sa description et sélectionnez le compte externe permettant la connexion à la base de données. Vous avez ainsi accès à la liste des tables disponibles dans la base externe. Sélectionnez la table contenant les données à collecter.

   ![](assets/wf_new_schema_select_table_fda.png)

1. Cliquez sur **[!UICONTROL OK]** pour confirmer. Adobe Campaign détecte automatiquement la structure du tableau sélectionné et génère le schéma logique. Notez qu’Adobe Campaign ne génère pas de liens.

1. Click **[!UICONTROL Save]** to confirm creation.

   >[!CAUTION]
   >
   >Avec Snowflake, une clé primaire est obligatoire.

   ![](assets/wf_new_schema_generate_fda.png)

Les index sont crées automatiquement lors d&#39;un mapping de table (mapping standard ou FDA).
