---
solution: Campaign Classic
product: campaign
title: Edition du schéma
description: En savoir plus sur l'activité de flux de travail Modifier le schéma
audience: workflow
content-type: reference
topic-tags: targeting-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 93%

---


# Edition du schéma{#edit-schema}

Les données peuvent être transformées, normalisées et, au besoin, enrichies dans le workflow en utilisant l&#39;activité **[!UICONTROL Edition du schéma]**. Elle est généralement utilisée pour normaliser la structure des données : vous pouvez renommer les colonnes de sortie ou modifier leur contenu, par exemple en calculant la moyenne des valeurs d&#39;un champ ou un agrégat.

Cette activité ne modifie en rien les données de la table de travail, mais uniquement le schéma de cette dernière, c&#39;est-à-dire la vision logique des données.

![](assets/wf_manipulation_box.png)

Vous pouvez également créer des jointures avec d&#39;autres tables de travail, à partir de l&#39;onglet **[!UICONTROL Liens]**.

![](assets/wf_manipulation_box_link_tab.png)

La section inférieure permet de paramétrer la liste des conditions de jointure, c&#39;est-à-dire des critères utilisés pour réconcilier les données des deux tables.
