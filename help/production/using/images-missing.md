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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Images absentes{#images-missing}

Dans la version 17.9, plusieurs fichiers (en particulier des icônes) ont été déplacés.

Pour les clients hébergés, ce déplacement n&#39;a aucun impact. Pour les installations on-premise, veuillez lire les informations suivantes.

**Utilisateurs d&#39;Apache :**

Si les utilisateurs d&#39;Apache utilisent le fichier **apache_neolane.conf** fourni, le déplacement des fichiers n&#39;a aucun impact.

**Utilisateurs d&#39;IIS :**

Pour les utilisateurs d&#39;IIS (sous Windows), plusieurs icônes seront absentes de la console après la mise à jour du build. D&#39;autres étapes de mise à jour d&#39;IIS sont nécessaires :

1. Après la mise à jour de la compilation, double-cliquez sur **is_neolane_setup.vbs** situé dans le répertoire d’installation de Campaign. Le chemin par défaut est C:Program Files (x86)AdobeAdobe Campaign v7tomcat-7conf
1. Redémarrez le site IIS qui a été mis à jour au cours de l&#39;étape précédente.

