---
product: campaign
title: Chargement (SGBD)
description: En savoir plus sur l’activité de workflow de chargement (SGBD)
feature: Workflows, Data Management Activity
hide: true
exl-id: 6e24d5fe-4830-49b4-a0fe-624c5644c920
source-git-commit: 720a5f4edf534788f7fd143a476c25e58a6f1586
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 63%

---

# Chargement (SGBD){#data-loading-rdbms}



L&#39;activité **[!UICONTROL Chargement (SGBD)]** permet d&#39;accéder directement une base externe et de n&#39;en collecter que les données nécessaires au ciblage.

Pour améliorer les performances, il est recommandé de préférer l&#39;utilisation de l&#39;activité de requête (où peuvent être utilisées des données d&#39;une base externe). Voir à ce sujet la section [Accès à une base externe (FDA)](accessing-an-external-database-fda.md);

Le principe de fonctionnement est le suivant :

1. Sélectionnez la source de données dans la liste et saisissez le nom de la table contenant les données à extraire.

   ![](assets/s_advuser_wf_sgbd_sample_1.png)

   Le nom de la table renseigné dans le champ correspondant est utilisé comme modèle pour la collecte des données dans la base externe. Le nom de la table traitée par le workflow peut être calculé ou transmis par la transition entrante de l’activité de chargement des données. Pour sélectionner la table à utiliser, cliquez sur le lien **[!UICONTROL Avancé..]**. et choisissez l&#39;option **[!UICONTROL Spécifié par la transition]** ou **[!UICONTROL Explicite]**.

   ![](assets/s_advuser_wf_sgbd_sample_5.png)

1. Cliquez sur le lien **[!UICONTROL Sélectionner les colonnes à extraire...]** afin de choisir les données qui doivent être collectées dans la base.

   ![](assets/s_advuser_wf_sgbd_sample_2.png)

1. Vous pouvez définir un filtre sur ces données. Pour cela, cliquez sur le lien **[!UICONTROL Éditer la requête...]** .

   Les données ainsi collectées peuvent être utilisées tout au long du cycle de vie du workflow.
