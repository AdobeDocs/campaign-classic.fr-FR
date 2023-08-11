---
product: campaign
title: Structure d’un schéma de données
description: Structure d’un schéma de données
feature: Custom Resources
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: 86036f2f-ec7c-413e-b1e1-10a71a06cd6d
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: ht
source-wordcount: '149'
ht-degree: 100%

---

# Structure d’un schéma de données{#structure-of-a-data-schema}

La structure d’un schéma de données est présentée sous la forme d’une arborescence. Pour la visualiser graphiquement dans la console client Adobe Campaign, sélectionnez le schéma ciblé et cliquez sur le sous-onglet **[!UICONTROL Structure]**.

![](assets/d_ncs_integration_schema_arbo.png)

Par convention, les champs (Actif, Activé, etc.) sont affichés en premier et par ordre alphabétique. Les éléments de structure viennent ensuite (Adresse postale, Emplacement) et enfin les liens (Informations sur l’e-mail, Dossier, etc.).

Les clés primaires sont identifiées par une clé rouge et les clés étrangères par une clé jaune.

Les liens sont différenciés graphiquement en fonction de leur appartenance à la table. Ceux qui commencent à partir de la table, c’est-à-dire ceux qui possèdent la clé étrangère dans la table, s’affichent en premier (Informations sur l’e-mail, Dossier, Pays). Les liens de collection « Inverse » (Abonnement, Commandes, etc.) sont affichés à la fin.
