---
solution: Campaign Classic
product: campaign
title: Fichiers temporaires
description: Fichiers temporaires
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: ht
source-git-commit: 1fdee02e98ce66ec184d8587d0838557f027cf75
workflow-type: ht
source-wordcount: '130'
ht-degree: 100%

---


# Fichiers temporaires{#temporary-files}

Lorsque vous lancez le système en production, vous pouvez obtenir des messages d&#39;erreur (notamment dans les logs de diffusion), tels que :

*Unable to rename file &#39;/tmp/tmp0000.tmp&#39; to /usr/local/neolane/nl6/bin/..//var/XXX/mta/86510470.xml ;(errno=18, Invalid cross-device link) (iRc=-52)*

La cause est la suivante :

Adobe Campaign génère des fichiers temporaires sous **/tmp**, puis les renomme pour les déplacer sous **/usr/local/neolane/nl6/var**. Cette erreur se produit lorsque les deux dossiers (**/tmp** et **/usr/local/neolane/nl6/var**, qui est en fait un lien symbolique vers **/var/nl6**) correspondent à des devices différents. La commande **df** permet de le vérifier.

Pour corriger ce problème, les fichiers temporaires doivent être générés dans le même appareil que la destination.

Par exemple, exécutez les commandes suivantes :

```
$ cd ~/nl6/var
$ mkdir tmp
$ vi ~/nl6/customer.sh
```

Ajoutez ensuite :

```
export TMPDIR=/usr/local/neolane/nl6/var/tmp 
```
