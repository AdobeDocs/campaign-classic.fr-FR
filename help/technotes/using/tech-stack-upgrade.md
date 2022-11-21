---
product: campaign
title: Note technique - Mises à niveau du système Adobe Campaign
description: Mise à niveau du système Adobe Campaign
hide: true
hidefromtoc: true
source-git-commit: 6fc11ea75863abe86e81c4978843e8487cbd83a0
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 11%

---

# Mise à niveau du système Adobe Campaign 2023 {#ac-system-upgrade}

L’infrastructure de Campaign repose sur des systèmes tiers qui doivent être régulièrement mis à jour avec les dernières versions et correctifs. Ces mises à jour sont obligatoires pour assurer la continuité du service et sécuriser les environnements Campaign contre les risques de sécurité. En outre, un upgrade de Campaign est nécessaire pour garantir la compatibilité avec les modifications système tierces.

Comme **Client hébergé ou Cloud Services géré**, Adobe vous informe sur ces mises à niveau lorsqu’elles sont nécessaires. Vous devrez mettre à niveau vos environnements conformément aux recommandations pour garantir la conformité.

En tant que **Client On-premise ou hybride**, Adobe vous recommande vivement de mettre à niveau vos versions système et Campaign selon le même calendrier.

Pour des raisons de sécurité, vous devez [installer le dernier build de Campaign](#ac-upgrade), puis mettez à niveau votre [système d&#39;exploitation](#os-upgrade) et/ou votre [Système de gestion de la base de données des relations (SGBD)](#pg-upgrade).

>[!NOTE]
>
>Pour toute question sur ces modifications, contactez l&#39;[Assistance clientèle d&#39;Adobe](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). Voir aussi [FAQ sur l&#39;upgrade de build](../../platform/using/faq-build-upgrade.md).

## Upgrade de build Campaign {#ac-upgrade}

**Cela vous concerne-t-il ?**

Si vous êtes affecté par la variable [mise à niveau du système d’exploitation](#os-upgrade) et/ou [mise à niveau du système de base de données](#pg-upgrade) présenté ci-dessous, vous devez mettre à niveau vos environnements Campaign vers la dernière version 7.3.2, compatible avec ces systèmes.

**Comment effectuer la mise à jour ?**

* En tant que client hébergé ou Cloud Services géré, Adobe vous contactera et mettra à niveau votre version de Campaign.
* En tant que client hybride, Adobe vous informera des dates d&#39;upgrade de build prévues pour votre environnement de mid-sourcing. Vous devez également mettre à niveau votre environnement marketing vers cette même version.
* En tant que client on-premise, vous êtes invité à mettre à niveau vos environnements Campaign vers le dernier build 7.3.2.


## Mise à niveau du système d’exploitation {#os-upgrade}

**Cela vous concerne-t-il ?**

Si vous exécutez Campaign sur un système d&#39;exploitation Debian, vous devez déplacer votre infrastructure Campaign vers pour bénéficier des dernières mises à jour de sécurité de Debian. **Debian 11**. Notez que Debian 9 a atteint la fin de vie le 30 juin 2022, et ne fournit plus de correctifs de sécurité.

**Comment effectuer la mise à jour ?**

* En tant que client hébergé ou Cloud Services géré, Adobe vous contactera et mettra à niveau votre environnement.
* En tant que client hybride, Adobe vous informera des dates d&#39;upgrade prévues pour votre environnement de mid-sourcing. Si votre environnement marketing fonctionne également sous Debian, vous devez le mettre à niveau vers Debian 11 également.
* En tant que client on-premise, vous êtes invité à mettre à niveau vos environnements vers Debian 11.

## Mise à niveau du système de base de données {#pg-upgrade}

**Cela vous concerne-t-il ?**

Si votre système de base de données pour Campaign est PostgreSQL, pour bénéficier des dernières innovations PostgreSQL et des mises à jour de sécurité, vous devez effectuer la mise à niveau vers **PostgreSQL 14**. Notez que PostreSQL 11 atteindra la fin de vie le 30 novembre 2022.

**Comment effectuer la mise à jour ?**

* En tant que client hébergé ou Cloud Services géré, Adobe vous contactera et mettra à niveau votre système de base de données de PostgreSQL 11 vers PostgreSQL 14.
* En tant que client hybride, si votre système de base de données marketing est PostgreSQL, vous devez le mettre à niveau vers PostgreSQL 14.
* En tant que client on-premise, vous êtes invité à mettre à niveau votre système de base de données vers PostgreSQL 14.


## Liens utiles

* [Mise à niveau de votre environnement](../../production/using/build-upgrade.md)
* [FAQ sur la mise à niveau des builds](../../platform/using/faq-build-upgrade.md)
* [Téléchargez la dernière version du Campaign Classic](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
* [Mise à disposition de la nouvelle console cliente auprès des utilisateurs](../../installation/using/client-console-availability-for-windows.md)
