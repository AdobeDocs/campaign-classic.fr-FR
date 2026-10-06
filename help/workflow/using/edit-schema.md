---
product: campaign
title: Edition du schéma
description: En savoir plus sur l’activité de workflow d’édition du schéma
feature: Workflows, Targeting Activity
hide: true
exl-id: d26966a8-b5db-4fa4-85ec-7ebd770c4ef3
TQID: 'https://experienceleague.adobe.com/cxBDJJXifg7C4vtB5MPBYSluRpgnbsBkDiuSsnIHDYo'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
    internal-label: HeatMap
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
    internal-label: Execution activities
  - id: d1110311-2ca4-442b-be37-088a6db845ee
    internal-label: Data Management activities
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
  - id: ff84ab2f-a7c2-4ced-a3c8-5113f4348d99
    internal-label: Targeting Activity
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 100%
---
# Modification du schéma{#edit-schema}



Les données peuvent être transformées, normalisées et, au besoin, enrichies dans le workflow à l’aide de l’activité **[!UICONTROL Modifier le schéma]**. Celle-ci est généralement utilisée pour normaliser la structure des données : vous pouvez renommer les colonnes de sortie ou modifier leur contenu, par exemple en calculant la moyenne des valeurs d’un champ ou d’un agrégat.

Cette activité ne modifie en rien les données de la table de travail, mais uniquement le schéma de cette dernière, c&#39;est-à-dire la vision logique des données.

![](assets/wf_manipulation_box.png)

Vous pouvez également créer des jointures avec d&#39;autres tables de travail, à partir de l&#39;onglet **[!UICONTROL Liens]**.

![](assets/wf_manipulation_box_link_tab.png)

La section inférieure permet de paramétrer la liste des conditions de jointure, c&#39;est-à-dire des critères utilisés pour réconcilier les données des deux tables.
