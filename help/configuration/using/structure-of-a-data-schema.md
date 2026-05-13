---
product: campaign
title: Structure d’un schéma de données
description: Structure d’un schéma de données
feature: Custom Resources
role: Developer
exl-id: 86036f2f-ec7c-413e-b1e1-10a71a06cd6d
TQID: https://experienceleague.adobe.com/bp-x2YrBY5WzNVTXJjpzdZgG45vNPPG9-z339I9U5Lw
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2: id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 143
ht-degree: 22%

---

# Structure d’un schéma de données{#structure-of-a-data-schema}

La structure d’un schéma de données est présentée sous la forme d’une arborescence. Pour le visualiser graphiquement dans la console cliente Adobe Campaign, sélectionnez le schéma ciblé et cliquez sur le sous-onglet **[!UICONTROL Structure]**.

![](assets/d_ncs_integration_schema_arbo.png)

Par convention, les champs sont affichés en premier (Actif, Activé, etc.) et par ordre alphabétique. Les éléments de structure viennent ensuite (Adresse postale, Emplacement), et enfin les liens (Informations sur l’e-mail, Dossier, etc.).

Les clés primaires sont identifiées par une clé rouge et les clés étrangères par une clé jaune.

Les liens sont différenciés graphiquement selon qu’ils appartiennent ou non au tableau. Ceux qui commencent à partir du tableau, c’est-à-dire ceux dont la clé étrangère se trouve dans le tableau, s’affichent en premier (informations sur l’e-mail, dossier, pays). Liens de collection « reverse » (Abonnement, Commandes, etc.) s’affichent à la fin.
