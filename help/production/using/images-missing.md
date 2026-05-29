---
product: campaign
title: Images absentes
description: Images absentes
feature: Monitoring
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 6ccda57d-f7a3-4501-b2f4-59fcb05f9013
TQID: https://experienceleague.adobe.com/GDlcjvzSGP70FlVGHmnhJHsqC3SFG5Y-kQOohR00j8c
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
feature_v2: []
subfeature_v2:
  - id: c03a11ff-bdf9-4e5b-b279-f468b4293464
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 111
ht-degree: 65%

---

# Images absentes{#images-missing}



Dans la version 17.9, plusieurs fichiers (en particulier des icônes) ont été déplacés.

Pour les clients hébergés, il n’y a aucun impact. Pour les installations on-premise, lisez ce qui suit.

**Utilisateurs d&#39;Apache :**

Si les utilisateurs d’Apache utilisent le fichier **apache_neolane.conf** fourni, le déplacement des fichiers n’a aucun impact.

**Utilisateurs d&#39;IIS :**

Pour les utilisateurs d&#39;IIS (sous Windows), plusieurs icônes seront manquantes dans la console après la mise à jour de la build. D&#39;autres étapes de mise à jour IIS sont requises :

1. Après la mise à jour du build, double-cliquez sur le fichier **iis_neolane_setup.vbs** situé dans le répertoire d’installation de Campaign. Le chemin par défaut est C:\Program Files (x86)\Adobe\Adobe Campaign v7\conf
1. Redémarrez le site IIS qui a été mis à jour au cours de létape précédente.
