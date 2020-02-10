---
title: Fichiers temporaires
seo-title: Fichiers temporaires
description: Fichiers temporaires
seo-description: null
page-status-flag: never-activated
uuid: ae7ec619-e93f-41fb-ba7c-fcbcf4cba84f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: f18237b0-ef54-46a6-9c14-34b038f9de18
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2a11a73b0679c0a65dc10f71869bf2a6c6efc008

---


# Fichiers temporaires{#temporary-files}

Si, lorsque vous lancez le système en production, vous obtenez des messages d&#39;erreur (notamment dans les journaux de diffusion), tels que:

**Unable to rename file &#39;/tmp/tmp0000.tmp&#39; to /usr/local/neolane/nl6/bin/..//var/XXX/mta/86510470.xml ;(errno=18, Invalid cross-device link) (iRc=-52)**

La cause est la suivante :

Adobe Campaign génère des fichiers temporaires sous **/tmp**, puis les renomme pour les déplacer sous **/usr/local/neolane/nl6/var**. Cette erreur se produit lorsque les deux dossiers (**/tmp** et **/usr/local/neolane/nl6/var**, qui est en fait un lien symbolique vers **/var/nl6**) correspondent à des devices différents. La commande **df** permet de le vérifier.

Pour corriger ce problème, les fichiers temporaires doivent être générés dans le même device que la destination. Par exemple en exécutant :

```
$ cd ~/nl6/var
$ mkdir tmp
$ vi ~/nl6/customer.sh
```

puis en ajoutant :

```
export TMPDIR=/usr/local/neolane/nl6/var/tmp 
```

