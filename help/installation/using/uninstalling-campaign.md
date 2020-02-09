---
title: Désinstaller Campaign
seo-title: Désinstaller Campaign
description: Désinstaller Campaign
seo-description: null
page-status-flag: never-activated
uuid: 4e95a576-a2fe-41dd-a03d-e4a3120f8788
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: appendices
discoiquuid: 702253cc-3e1a-44ad-9340-b8588ee86bad
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

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
