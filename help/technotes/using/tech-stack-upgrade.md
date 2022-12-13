---
product: campaign
title: Note technique - mises à niveau du système Adobe Campaign
description: Mise à niveau du système Adobe Campaign
exl-id: 78949d94-60b3-44f1-8e5a-d61b5b723e87
source-git-commit: d04b672fe2049d83ba17d3d855e1b609e81cf8c9
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 100%

---

# Mises à niveau de l’environnement Adobe Campaign 2023 {#ac-system-upgrade}

L’infrastructure de Campaign repose sur des systèmes tiers qui doivent être régulièrement mis à jour avec les versions et les correctifs les plus récents. Ces mises à jour sont obligatoires pour assurer la continuité du service et sécuriser les environnements Campaign contre les risques de sécurité. En outre, une mise à niveau de Campaign est nécessaire pour garantir la compatibilité avec les modifications des systèmes tiers.

En tant que **client(e) hébergé(e) ou Managed Cloud Services**, Adobe vous informe de ces mises à niveau lorsqu’elles sont nécessaires. Vous devrez effectuer la mise à niveau de vos environnements conformément aux recommandations afin de garantir leur conformité.

En tant que **client(e) On-premise ou hybride**, Adobe vous recommande vivement de mettre à niveau les versions de votre système et de Campaign selon le même calendrier.

Pour des raisons de sécurité, vous devez [installer la version la plus récente de Campaign](#ac-upgrade), puis mettre à niveau votre [système d’exploitation](#os-upgrade) et/ou votre [Système de gestion de la base de données relationnelle (SGBD)](#pg-upgrade).

>[!NOTE]
>
>Pour toute question sur ces modifications, contactez l’[Assistance clientèle d’Adobe](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). Voir aussi la [FAQ sur la mise à niveau de la version](../../platform/using/faq-build-upgrade.md).

## Mise à niveau de la version de Campaign {#ac-upgrade}

**Cela vous concerne-t-il ?**

Si vous êtes affecté(e) par la [mise à niveau du système d’exploitation](#os-upgrade) et/ou la [mise à niveau du système de la base de données](#pg-upgrade) présentées ci-dessous, vous devez mettre à niveau vos environnements Campaign vers [la dernière version 7.3.2](../../rn/using/latest-release.md#release-7-3-2), compatible avec ces systèmes.

**Comment effectuer la mise à jour ?**

* En tant que client(e) hébergé(e) ou Managed Cloud Services, Adobe vous contactera et mettra à niveau votre version de Campaign.
* En tant que client(e) hybride, Adobe vous informera des dates de mise à niveau planifiées des versions pour votre environnement de mid-sourcing. Vous devez également mettre à niveau votre environnement marketing vers cette même version.
* En tant que client(e) On-premise, vous êtes invité(e) à mettre à niveau vos environnements Campaign vers la version 7.3.2 la plus récente.


## Mise à niveau du système d’exploitation {#os-upgrade}

**Cela vous concerne-t-il ?**

Si vous exécutez Campaign sur un système d’exploitation Debian, vous devez déplacer votre infrastructure Campaign vers **Debian 11** pour bénéficier des dernières mises à jour de sécurité de Debian. Notez que la prise en charge en matière de sécurité de Debian 9 sera disponible jusqu’au 30 juin 2023.

**Comment effectuer la mise à jour ?**

* En tant que client(e) hébergé(e) ou Managed Cloud Services, Adobe vous contactera et mettra à niveau votre environnement.
* En tant que client(e) hybride, Adobe vous informera des dates de mise à niveau planifiées pour votre environnement de mid-sourcing. Si votre environnement marketing fonctionne également sous Debian, vous devez aussi le mettre à niveau vers Debian 11.
* En tant que client(e) On-premise, vous êtes invité(e) à mettre à niveau vos environnements vers Debian 11.

## Mise à niveau du système de la base de données {#pg-upgrade}

**Cela vous concerne-t-il ?**

Si votre système de base de données pour Campaign est PostgreSQL, vous devez effectuer la mise à niveau vers **PostgreSQL 14** pour bénéficier des dernières innovations et mises à jour de sécurité de PostgreSQL. Notez que PostgreSQL 11 atteindra sa fin de vie le 9 novembre 2023.

**Comment effectuer la mise à jour ?**

* En tant que client(e) hébergé(e) ou Managed Cloud Services, Adobe vous contactera et mettra à niveau votre système de base de données de PostgreSQL 11 vers PostgreSQL 14.
* En tant que client(e) hybride, si votre système de base de données marketing est PostgreSQL, vous devez le mettre à niveau vers PostgreSQL 14.
* En tant que client(e) On-premise, vous êtes invité(e) à mettre à niveau votre système de base de données vers PostgreSQL 14.


## Liens utiles

* [Mise à niveau de votre environnement](../../production/using/build-upgrade.md)
* [FAQ sur la mise à niveau des builds](../../platform/using/faq-build-upgrade.md)
* [Télécharger la dernière version de Campaign Classic](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
* [Mise à disposition de la nouvelle console cliente auprès des utilisateurs et des utilisatrices](../../installation/using/client-console-availability-for-windows.md)
