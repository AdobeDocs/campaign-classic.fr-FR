---
product: campaign
title: Fichiers temporaires
description: Fichiers temporaires
feature: Monitoring
badge-v7-prem: label="On-Premise/hybride uniquement" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: e77800f5-c0ae-446d-8ff3-bc8a18c97dbd
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 100%

---

# Fichiers temporaires{#temporary-files}



Lorsque vous lancez le système en production, vous pouvez obtenir des messages d&#39;erreur (notamment dans les logs de diffusion), tels que :

*Unable to rename file &#39;/tmp/tmp0000.tmp&#39; to /usr/local/neolane/nl6/bin/..//var/XXX/mta/86510470.xml ;(errno=18, Invalid cross-device link) (iRc=-52)*

La cause est la suivante :

Adobe Campaign génère des fichiers temporaires sous **/tmp**, puis les renomme pour les déplacer vers **/usr/local/neolane/nl6/var**. Cette erreur se produit lorsque les deux dossiers (**/tmp** et **/usr/local/neolane/nl6/var**, qui est en fait un lien symbolique vers **/var/nl6**) correspondent à des appareils différents. La commande **df** permet de le vérifier.

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
