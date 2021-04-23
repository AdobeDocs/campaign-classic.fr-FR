---
solution: Campaign Classic
product: campaign
title: Désinstaller Campaign
description: Découvrez comment désinstaller Campaign
audience: installation
content-type: reference
topic-tags: appendices
exl-id: e2b026ba-aaf3-443d-8c36-c908288a14fd
translation-type: ht
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: ht
source-wordcount: '36'
ht-degree: 100%

---

# Désinstaller Campaign{#uninstalling-campaign}

>[!CAUTION]
>
>Ces procédures désinstalleront définitivement Adobe Campaign. Toutes les données seront perdues.

**RHEL :**

```
rpm -e nlserver6-v7
userdel -r neolane
groupdel neolane
rm -rf /user/local/neolane
```

**Debian :**

```
apt purge nlserver6-v7
userdel -r neolane
groupdel neolane
rm -rf /user/local/neolane
```

**Windows :**

Consultez cette [page](../../migration/using/migrating-in-windows-for-adobe-campaign-7.md#deleting-and-cleansing-adobe-campaign-previous-version). N’oubliez pas de supprimer le dossier d’installation de Campaign.
