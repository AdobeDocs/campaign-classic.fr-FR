---
product: campaign
title: Edition du schéma
description: En savoir plus sur l’activité de workflow d’édition du schéma
audience: workflow
content-type: reference
topic-tags: targeting-activities
exl-id: d26966a8-b5db-4fa4-85ec-7ebd770c4ef3
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 100%

---

# Modification du schéma{#edit-schema}

![](../../assets/common.svg)

Les données peuvent être transformées, normalisées et, au besoin, enrichies dans le workflow en utilisant l&#39;activité **[!UICONTROL Edition du schéma]**. Elle est généralement utilisée pour normaliser la structure des données : vous pouvez renommer les colonnes de sortie ou modifier leur contenu, par exemple en calculant la moyenne des valeurs d&#39;un champ ou un agrégat.

Cette activité ne modifie en rien les données de la table de travail, mais uniquement le schéma de cette dernière, c&#39;est-à-dire la vision logique des données.

![](assets/wf_manipulation_box.png)

Vous pouvez également créer des jointures avec d&#39;autres tables de travail, à partir de l&#39;onglet **[!UICONTROL Liens]**.

![](assets/wf_manipulation_box_link_tab.png)

La section inférieure permet de paramétrer la liste des conditions de jointure, c&#39;est-à-dire des critères utilisés pour réconcilier les données des deux tables.
