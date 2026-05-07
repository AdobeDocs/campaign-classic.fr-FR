---
product: campaign
title: Structure d’un schéma de données
description: Structure d’un schéma de données
feature: Custom Resources
role: Developer
exl-id: 86036f2f-ec7c-413e-b1e1-10a71a06cd6d
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 22%

---

# Structure d’un schéma de données{#structure-of-a-data-schema}

La structure d’un schéma de données est présentée sous la forme d’une arborescence. Pour le visualiser graphiquement dans la console cliente Adobe Campaign, sélectionnez le schéma ciblé et cliquez sur le sous-onglet **[!UICONTROL Structure]**.

![](assets/d_ncs_integration_schema_arbo.png)

Par convention, les champs sont affichés en premier (Actif, Activé, etc.) et par ordre alphabétique. Les éléments de structure viennent ensuite (Adresse postale, Emplacement), et enfin les liens (Informations sur l’e-mail, Dossier, etc.).

Les clés primaires sont identifiées par une clé rouge et les clés étrangères par une clé jaune.

Les liens sont différenciés graphiquement selon qu’ils appartiennent ou non au tableau. Ceux qui commencent à partir du tableau, c’est-à-dire ceux dont la clé étrangère se trouve dans le tableau, s’affichent en premier (informations sur l’e-mail, dossier, pays). Liens de collection « reverse » (Abonnement, Commandes, etc.) s’affichent à la fin.
