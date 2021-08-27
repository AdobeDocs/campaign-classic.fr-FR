---
product: campaign
title: Accès à une base de données externe
description: Accès à une base de données externe
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 8702499b-1700-4d1f-a0e0-f7a9dfb4b88f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 100%

---

# Créer le schéma des données {#creating-the-data-schema}

![](../../assets/v7-only.svg)

Pour créer un schéma sur une base de données externe :

1. Cliquez sur le bouton **[!UICONTROL Nouveau]** au-dessus de la liste des schémas de données et sélectionnez **[!UICONTROL Accéder à des données externes]**.

   ![](assets/wf_new_schema_fda.png)

1. Saisissez le nom du schéma et sa description, puis sélectionnez le compte externe permettant la connexion à la base de données. Vous avez ainsi accès à la liste des tables disponibles dans la base externe. Sélectionnez la table contenant les données à collecter.

   ![](assets/wf_new_schema_select_table_fda.png)

1. Cliquez sur **[!UICONTROL OK]** pour valider. Adobe Campaign détecte automatiquement la structure de la table sélectionnée et génère le schéma logique. Veuillez noter qu&#39;Adobe Campaign ne génère pas de liens.

1. Cliquez sur **[!UICONTROL Enregistrer]** pour en valider la création.

   >[!CAUTION]
   >
   >Avec Snowflake, une clé primaire est obligatoire.

   ![](assets/wf_new_schema_generate_fda.png)

Les index sont crées automatiquement lors d&#39;un mapping de table (mapping standard ou FDA).
