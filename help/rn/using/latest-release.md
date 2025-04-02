---
product: campaign
title: Dernière version
description: Notes de mise à jour de la dernière version de Campaign Classic v7
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 86bc3bdfe628cc694e47a4670e99225e05b3df1b
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 100%

---

# Dernière version {#latest-release}

Cette page répertorie les nouvelles fonctionnalités, les améliorations et les correctifs apportés à la **dernière version de Campaign Classic v7**. Chaque nouvelle build est fournie avec un statut matérialisé par une couleur. En savoir plus sur les statuts de build de Campaign Classic v7 dans [cette page](rn-overview.md).

## Version 7.4.2 - Build 9390 {#release-7-4-2}

[!BADGE Disponibilité générale]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=fr#rn-statuses" tooltip="Disponibilité générale"}

_jeudi 2 avril 2025_

<!--
### Compatibility updates {#comp-7-4-2}

This release comes with the following compatibility updates:

* JQuery library update: fixes multiple UI issues (reports, web apps)
* PostgreSQL 15 and 16

-->

### Améliorations de la sécurité {#security-7-4-2}

Cette version comprend plusieurs correctifs de sécurité.

La connexion aux solutions et applications Adobe par le biais du compte externe **[!UICONTROL Adobe Experience Cloud]** a été mise à jour pour renforcer la sécurité.

### Correctifs {#release-7-4-2-fixes}

Cette version comprend les correctifs principaux suivants :

* Connexion TLS/SMPP : correction des problèmes de stabilité SMPP

* Correctifs BigQuery Google :

   * Correction des régressions sur les types de données booléens
   * Correction des problèmes de paramètres du proxy
   * Correction des régressions sur les types de données de date et heure
   * Correction de la stabilité de la charge en masse (bulk load)
   * Amélioration des tests internes sur les versions ODBC
   * Correction d’un problème lié aux caractères spéciaux sur la chaîne de connexion
   * Suppression du délai d’expiration par défaut (5 minutes) sur les requêtes BigQuery Google

* MTA (Mail Transfer Agent) : correction du blocage d’un enfant MTA orphelin au statut **[!UICONTROL Démarrage en attente]**.

Les problèmes suivants ont également été corrigés dans cette version :

NEO-47269, NEO-59059, NEO-62455, NEO-65774, NEO-66462, NEO-66989, NEO-77898, NEO-78843, NEO-79373, NEO-79598, NEO-80145, NEO-80245, NEO-80434, NEO-80683, NEO-81222, NEO-81433, NEO-81864, NEO-82351, NEO-82781, NEO-82838, NEO-82923, NEO-83252, NEO-83809, NEO-83826, NEO-84024, NEO-84553, NEO-85150

