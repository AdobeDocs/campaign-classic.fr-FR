---
title: Structure d’un schéma de données
seo-title: Structure d’un schéma de données
description: Structure d’un schéma de données
seo-description: null
page-status-flag: never-activated
uuid: 83e3995d-fa31-4cb5-acf2-83f17329c99c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: a1a39eaa-6d6f-42c5-a36b-bd1cb3a77dcb
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '147'
ht-degree: 100%

---


# Structure d’un schéma de données{#structure-of-a-data-schema}

La structure d&#39;un schéma de données est présentée sous la forme d&#39;une arborescence. Pour la visualiser graphiquement dans la console cliente Adobe Campaign, sélectionnez le schéma visé et cliquez sur le sous-onglet **[!UICONTROL Structure]**.

![](assets/d_ncs_integration_schema_arbo.png)

Par convention, les champs sont affichés en premier (Actif, Activé, etc.) et par ordre alphabétique, puis viennent les élements de structuration (Adresse postale, Localisation) et enfin les liens (Infos sur l&#39;email, Dossier, etc.).

Les clés primaires sont identifiées par une clé rouge et les clés étrangères par une clé jaune.

Les liens sont différenciés graphiquement en fonction de leur appartenance à la table. Ceux qui partent de la table, c&#39;est-à-dire ceux qui possèdent la clé étrangère dans la table, sont affichés en premier (Infos sur l&#39;email, Dossier, Pays). Les liens &quot;reverse&quot; de collection (Abonnement, Commandes, etc.) sont affichés à la fin.
