---
solution: Campaign Classic
product: campaign
title: Structure d’un schéma de données
description: Structure d’un schéma de données
audience: configuration
content-type: reference
topic-tags: editing-schemas
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 100%

---


# Structure d’un schéma de données{#structure-of-a-data-schema}

La structure d&#39;un schéma de données est présentée sous la forme d&#39;une arborescence. Pour la visualiser graphiquement dans la console cliente Adobe Campaign, sélectionnez le schéma visé et cliquez sur le sous-onglet **[!UICONTROL Structure]**.

![](assets/d_ncs_integration_schema_arbo.png)

Par convention, les champs sont affichés en premier (Actif, Activé, etc.) et par ordre alphabétique, puis viennent les élements de structuration (Adresse postale, Localisation) et enfin les liens (Infos sur l&#39;email, Dossier, etc.).

Les clés primaires sont identifiées par une clé rouge et les clés étrangères par une clé jaune.

Les liens sont différenciés graphiquement en fonction de leur appartenance à la table. Ceux qui partent de la table, c&#39;est-à-dire ceux qui possèdent la clé étrangère dans la table, sont affichés en premier (Infos sur l&#39;email, Dossier, Pays). Les liens &quot;reverse&quot; de collection (Abonnement, Commandes, etc.) sont affichés à la fin.
