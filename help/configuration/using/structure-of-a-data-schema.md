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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Structure d’un schéma de données{#structure-of-a-data-schema}

La structure d’un schéma de données s’affiche sous la forme d’une arborescence. Pour l’afficher sous forme graphique dans la console client Adobe Campaign, sélectionnez le schéma ciblé et cliquez sur le **[!UICONTROL Structure]** sous-onglet.

![](assets/d_ncs_integration_schema_arbo.png)

Par convention, les champs sont affichés en premier (Actif, Activé, etc.) et par ordre alphabétique, puis viennent les élements de structuration (Adresse postale, Localisation) et enfin les liens (Infos sur l&#39;email, Dossier, etc.).

Les clés primaires sont identifiées par une clé rouge et les clés étrangères par une clé jaune.

Les liens sont différenciés graphiquement en fonction de leur appartenance à la table. Ceux qui partent de la table, c&#39;est-à-dire ceux qui possèdent la clé étrangère dans la table, sont affichés en premier (Infos sur l&#39;email, Dossier, Pays). Les liens &quot;reverse&quot; de collection (Abonnement, Commandes, etc.) sont affichés à la fin.
