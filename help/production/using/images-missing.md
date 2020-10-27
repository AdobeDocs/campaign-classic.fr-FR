---
title: Images absentes
seo-title: Images absentes
description: Images absentes
seo-description: null
page-status-flag: never-activated
uuid: 0dc73ea0-70bc-476d-bdff-2e62d6929f21
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: e001db7a-7c53-477e-a534-ce4d83d68559
translation-type: tm+mt
source-git-commit: d509dc584cd4ae17c6dda85c09fceee8c6162dba
workflow-type: tm+mt
source-wordcount: '114'
ht-degree: 88%

---


# Images absentes{#images-missing}

Dans la version 17.9, plusieurs fichiers (en particulier des icônes) ont été déplacés.

Pour les clients hébergés, ce déplacement n&#39;a aucun impact. Pour les installations on-premise, veuillez lire les informations suivantes.

**Utilisateurs d&#39;Apache :**

Si les utilisateurs d&#39;Apache utilisent le fichier **apache_neolane.conf** fourni, le déplacement des fichiers n&#39;a aucun impact.

**Utilisateurs d&#39;IIS :**

Pour les utilisateurs d&#39;IIS (sous Windows), plusieurs icônes seront absentes de la console après la mise à jour du build. D&#39;autres étapes de mise à jour d&#39;IIS sont nécessaires :

1. Après la mise à jour du build, double-cliquez sur le fichier **iis_neolane_setup.vbs** situé dans le répertoire d’installation de Campaign. Le chemin par défaut est C:\Program Files (x86)\Adobe\Adobe Campaign v7\conf
1. Redémarrez le site IIS qui a été mis à jour au cours de l&#39;étape précédente.

