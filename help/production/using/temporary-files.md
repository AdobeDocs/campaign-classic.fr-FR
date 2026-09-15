---
product: campaign
title: Fichiers temporaires
description: Fichiers temporaires
feature: Monitoring
badge-v7-prem: label="On-premise/hybrid only" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: e77800f5-c0ae-446d-8ff3-bc8a18c97dbd
TQID: https://experienceleague.adobe.com/eZnGm-WK-etrLLbJ-aeuSqakYAfPNBQd2q3JlEd4rE8
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
feature_v2: []
subfeature_v2:
  - id: c03a11ff-bdf9-4e5b-b279-f468b4293464
    internal-label: Performance Monitoring
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
    internal-label: Monitoring guidelines
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 100%
---
# Fichiers temporaires{#temporary-files}



Lorsque vous lancez le système en production, vous pouvez obtenir des messages d’erreur (notamment dans les logs de diffusion), tels que :

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
