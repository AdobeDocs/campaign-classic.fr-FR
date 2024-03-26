---
product: campaign
title: Fichiers temporaires
description: Fichiers temporaires
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
badge-v7-prem: label="On-premise et hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: e77800f5-c0ae-446d-8ff3-bc8a18c97dbd
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 63%

---

# Fichiers temporaires{#temporary-files}



Lorsque vous lancez le système en production, vous pouvez obtenir des messages d&#39;erreur (notamment dans les logs de diffusion), tels que :

*Unable to rename file &#39;/tmp/tmp0000.tmp&#39; to /usr/local/neolane/nl6/bin/..//var/XXX/mta/86510470.xml ;(errno=18, Invalid cross-device link) (iRc=-52)*

La cause est la suivante :

Adobe Campaign génère des fichiers temporaires sous **/tmp**, puis les renomme pour les déplacer vers **/usr/local/neolane/nl6/var**. Cette erreur se produit lorsque les deux dossiers (**/tmp** et **/usr/local/neolane/nl6/var**, qui est en fait un lien symbolique vers **/var/nl6**) correspondent à différents appareils. La variable **df** est utilisée pour la vérification.

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
