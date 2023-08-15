---
product: campaign
title: Images absentes
description: Images absentes
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 6ccda57d-f7a3-4501-b2f4-59fcb05f9013
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 100%

---

# Images absentes{#images-missing}



Dans la version 17.9, plusieurs fichiers (en particulier des icônes) ont été déplacés.

Pour les clients hébergés, ce déplacement n&#39;a aucun impact. Pour les installations on-premise, veuillez lire les informations suivantes.

**Utilisateurs d&#39;Apache :**

Si les utilisateurs d&#39;Apache utilisent le fichier **apache_neolane.conf** fourni, le déplacement des fichiers n&#39;a aucun impact..

**Utilisateurs d&#39;IIS :**

Pour les utilisateurs d&#39;IIS (sous Windows), plusieurs icônes seront absentes de la console après la mise à jour du build. D&#39;autres étapes de mise à jour d&#39;IIS sont nécessaires :

1. Après la mise à jour du build, double-cliquez sur le fichier **iis_neolane_setup.vbs** situé dans le répertoire d’installation de Campaign. Le chemin par défaut est C:\Program Files (x86)\Adobe\Adobe Campaign v7\conf
1. Redémarrez le site IIS qui a été mis à jour au cours de l&#39;étape précédente.
