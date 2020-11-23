---
solution: Campaign Classic
product: campaign
title: Fichiers temporaires
description: Fichiers temporaires
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 100%

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

