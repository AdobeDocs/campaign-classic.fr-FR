---
product: campaign
title: Edition du schéma
description: En savoir plus sur l’activité de workflow d’édition du schéma
feature: Workflows, Targeting Activity
hide: true
exl-id: d26966a8-b5db-4fa4-85ec-7ebd770c4ef3
TQID: https://experienceleague.adobe.com/cxBDJJXifg7C4vtB5MPBYSluRpgnbsBkDiuSsnIHDYo
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 118
ht-degree: 59%

---

# Modification du schéma{#edit-schema}



Les données peuvent être transformées, normalisées et, au besoin, enrichies dans le workflow à l&#39;aide de l&#39;activité **[!UICONTROL Modifier le schéma]**. Elle est généralement utilisée pour normaliser la structure des données : vous pouvez renommer les colonnes de sortie ou modifier leur contenu, par exemple en calculant la moyenne des valeurs d&#39;un champ ou d&#39;un agrégat.

Cette activité ne modifie en rien les données de la table de travail, mais uniquement le schéma de cette dernière, c&#39;est-à-dire la vision logique des données.

![](assets/wf_manipulation_box.png)

Vous pouvez également créer des jointures avec d&#39;autres tables de travail, à partir de l&#39;onglet **[!UICONTROL Liens]**.

![](assets/wf_manipulation_box_link_tab.png)

La section inférieure permet de paramétrer la liste des conditions de jointure, c&#39;est-à-dire des critères utilisés pour réconcilier les données des deux tables.
