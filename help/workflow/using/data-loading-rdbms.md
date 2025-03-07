---
product: campaign
title: Chargement (SGBD)
description: En savoir plus sur l’activité de workflow de chargement (SGBD)
feature: Workflows, Data Management Activity
hide: true
hidefromtoc: true
exl-id: 6e24d5fe-4830-49b4-a0fe-624c5644c920
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: ht
source-wordcount: '203'
ht-degree: 100%

---

# Chargement (SGBD){#data-loading-rdbms}



L&#39;activité **[!UICONTROL Chargement (SGBD)]** permet d&#39;accéder directement une base externe et de n&#39;en collecter que les données nécessaires au ciblage.

Pour améliorer les performances, il est recommandé de préférer l&#39;utilisation de l&#39;activité de requête (où peuvent être utilisées des données d&#39;une base externe). Voir à ce sujet la section [Accès à une base externe (FDA)](accessing-an-external-database-fda.md);

Le principe de fonctionnement est le suivant :

1. Sélectionnez la source de données dans la liste et saisissez le nom de la table contenant les données à extraire.

   ![](assets/s_advuser_wf_sgbd_sample_1.png)

   Le nom de la table saisi dans le champ correspondant sert de modèle pour collecter les données dans la base externe. Le nom de la table qui sera effectivement traitée par le workflow peut être calculé ou véhiculé par la transition entrante de l’activité de chargement. Pour sélectionner la table à utiliser, cliquez sur le lien **[!UICONTROL Avancé..]**. et sélectionnez l’option **[!UICONTROL Spécifié par la transition]** ou **[!UICONTROL Explicite]**.

   ![](assets/s_advuser_wf_sgbd_sample_5.png)

1. Cliquez sur le lien **[!UICONTROL Sélectionner les colonnes à extraire...]** afin de choisir les données qui doivent être collectées dans la base.

   ![](assets/s_advuser_wf_sgbd_sample_2.png)

1. Vous pouvez définir un filtre sur ces données. Pour ce faire, cliquez sur le lien **[!UICONTROL Modifier la requête...]**

   Les données ainsi collectées peuvent être utilisées tout au long du cycle de vie du workflow.
