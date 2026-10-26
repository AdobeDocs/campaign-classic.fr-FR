---
product: campaign
title: Images absentes
description: Images absentes
feature: Monitoring
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 6ccda57d-f7a3-4501-b2f4-59fcb05f9013
TQID: 'https://experienceleague.adobe.com/GDlcjvzSGP70FlVGHmnhJHsqC3SFG5Y-kQOohR00j8c'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: c03a11ff-bdf9-4e5b-b279-f468b4293464
    internal-label: Performance Monitoring
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
    internal-label: Monitoring guidelines
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: ht
source-wordcount: '111'
ht-degree: 100%
---
# Images absentes{#images-missing}



Dans la version 17.9, plusieurs fichiers (en particulier des icônes) ont été déplacés.

Pour les clientes et clients hébergés, cela n’a aucun impact. Pour les installations on-premise, veuillez lire les informations suivantes.

**Utilisateurs d&#39;Apache :**

Si les utilisateurs d’Apache utilisent le fichier **apache_neolane.conf** fourni, le déplacement des fichiers n’a aucun impact.

**Utilisateurs d&#39;IIS :**

Pour les utilisateurs et utilisatrices d’IIS (sous Windows), plusieurs icônes seront absentes de la console après la mise à jour du build. D’autres étapes de mise à jour d’IIS sont nécessaires :

1. Après la mise à jour du build, double-cliquez sur le fichier **iis_neolane_setup.vbs** situé dans le répertoire d’installation de Campaign. Le chemin par défaut est C:\Program Files (x86)\Adobe\Adobe Campaign v7\conf
1. Redémarrez le site IIS qui a été mis à jour au cours de létape précédente.
