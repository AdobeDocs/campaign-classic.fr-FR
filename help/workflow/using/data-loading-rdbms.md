---
product: campaign
title: Chargement (SGBD)
description: En savoir plus sur l’activité de workflow de chargement (SGBD)
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
feature: Workflows, Data Management Activity
exl-id: 6e24d5fe-4830-49b4-a0fe-624c5644c920
source-git-commit: 668cee663890fafe27f86f2afd3752f7e2ab347a
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 66%

---

# Chargement (SGBD){#data-loading-rdbms}



L&#39;activité **[!UICONTROL Chargement (SGBD)]** permet d&#39;accéder directement une base externe et de n&#39;en collecter que les données nécessaires au ciblage.

Pour améliorer les performances, il est recommandé de préférer l&#39;utilisation de l&#39;activité de requête (où peuvent être utilisées des données d&#39;une base externe). Voir à ce sujet la section [Accès à une base externe (FDA)](accessing-an-external-database-fda.md);

Le principe de fonctionnement est le suivant :

1. Sélectionnez la source de données dans la liste et saisissez le nom de la table contenant les données à extraire.

   ![](assets/s_advuser_wf_sgbd_sample_1.png)

   Le nom de la table renseignée dans le champ correspondant sert de modèle pour collecter les données dans la base externe. Le nom de la table traitée par le workflow peut être calculé ou véhiculé par la transition entrante de l&#39;activité de chargement de données. Pour sélectionner le tableau à utiliser, cliquez sur le bouton **[!UICONTROL Avancé..]**. et sélectionnez l’option **[!UICONTROL Spécifié par la transition]** ou **[!UICONTROL Explicite]**.

   ![](assets/s_advuser_wf_sgbd_sample_5.png)

1. Cliquez sur le lien **[!UICONTROL Sélectionner les colonnes à extraire...]** afin de choisir les données qui doivent être collectées dans la base.

   ![](assets/s_advuser_wf_sgbd_sample_2.png)

1. Vous pouvez définir un filtre sur ces données. Pour ce faire, cliquez sur le bouton **[!UICONTROL Modifier la requête....]** lien.

   Les données ainsi collectées peuvent être utilisées tout au long du cycle de vie du workflow.
