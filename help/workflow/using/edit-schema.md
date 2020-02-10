---
title: Edition du schéma
seo-title: Edition du schéma
description: Edition du schéma
seo-description: null
page-status-flag: never-activated
uuid: abd77902-98b7-4ab7-a240-dd6b3bb247bb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 733576d2-505f-4598-89eb-a10e7331bf7e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Edition du schéma{#edit-schema}

Les données peuvent être transformées, normalisées et, si nécessaire, enrichies dans le flux de travail à l’aide de l’ **[!UICONTROL Edit schema]** activité. Il est généralement utilisé pour normaliser la structure des données : vous pouvez renommer les colonnes de sortie ou modifier leur contenu, en calculant par exemple les valeurs moyennes d’un champ ou d’un agrégat.

Cette activité ne modifie en rien les données de la table de travail, mais uniquement le schéma de cette dernière, c&#39;est-à-dire la vision logique des données.

![](assets/wf_manipulation_box.png)

You can also create joins with other worktables, via the **[!UICONTROL Links]** tab.

![](assets/wf_manipulation_box_link_tab.png)

La section inférieure permet de paramétrer la liste des conditions de jointure, c&#39;est-à-dire des critères utilisés pour réconcilier les données des deux tables.
