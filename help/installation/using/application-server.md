---
product: campaign
title: Serveur applicatif
description: Serveur applicatif
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 87103c31-1530-4f8d-ab3a-6ff73093b80c
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 100%

---

# Serveur applicatif{#application-server}



Les couches d&#39;accès pour le moteur de base de données que vous utilisez doivent être installées sur votre serveur et accessibles depuis le compte Adobe Campaign.

## Java Development Kit - JDK {#java-development-kit---jdk}

Le module de génération de pages Web dynamiques repose sur la technologie JSP 1.2. A cet effet, un moteur Tomcat (d&#39;origine Apache) est inclus dans l&#39;application. Il nécessite la présence d&#39;un Java Development Kit (JDK), installé sur tous les serveurs sur lesquels l&#39;application Adobe Campaign sera installée.

Vous devez installer un JDK sur les machines sur lesquelles vous comptez lancer le serveur applicatif Adobe Campaign (processus **nlserver web**), car il intègre un container de servlets Apache Tomcat utilisées pour la génération des pages web dynamiques (reporting, formulaires web, etc.).

L&#39;application a été validée pour le JDK développé par Oracle ainsi que pour **OpenJDK**.

Les versions prises en charge sont détaillées dans la [matrice de compatibilité](../../rn/using/compatibility-matrix.md) de Campaign.

>[!NOTE]
>
>Il est possible d&#39;installer la version adéquate du JDK en plus d&#39;une autre version qui serait déjà utilisée par d&#39;autres applications sur la machine.
>  
>Lors de l&#39;installation, il n&#39;est pas obligatoire de faire l&#39;intégration avec les navigateurs Web.
>
>Sur une machine exécutant uniquement les agents de diffusion (processus **nlserver mta**) ou le serveur de workflow (processus **nlserver wfserver**), l&#39;installation du JDK n&#39;est pas nécessaire.

Pour télécharger le JDK Java, accédez à l’adresse : [https://www.oracle.com/technetwork/java/javase/downloads/index.html](https://www.oracle.com/technetwork/java/javase/downloads/index.html).

**Avertissement : vous devez télécharger un JDK (Java Development Kit) et non un JRE (Java Runtime Environment).**

>[!CAUTION]
>
>Afin de préserver le bon fonctionnement de votre plateforme et conserver la compatibilité avec la version installée, vous devez impérativement désactiver les fonctions de mises à jour automatiques du JDK sous Windows et Linux.

Pour installer le JDK dans un environnement Linux, il est préférable d&#39;utiliser un gestionnaire de paquets.

Pour Debian 8 et 9, utilisez la commande suivante :

```
aptitude install openjdk-8-jdk
```

Pour RHEL 7, utilisez la commande suivante :

```
yum install java-1.8.0-openjdk
```

## OpenSSL {#openssl}

Sous Linux, OpenSSL doit être installé. Adobe Campaign prend en charge OpenSSL version 1.0.2 ou ultérieure.

## Export des rapports {#exporting-reports}

Adobe Campaign permet d&#39;exporter les rapports de la plateforme aux formats Microsoft Excel et Adobe PDF. Pour le format Microsoft Excel, Adobe Campaign utilise **LibreOffice**. Pour le format Adobe PDF, Adobe Campaign utilise le convertisseur **PhantomJS**. PhantomJS est fourni dans le package d&#39;usine, et LibreOffice doit être installé sur la ou les machines sur lesquelles s&#39;exécute le serveur applicatif Adobe Campaign (processus **nlserver web**).

>[!NOTE]
>
>Pour Linux, vous devez ajouter des polices. Voir à ce sujet la section [Polices de caractères pour les statistiques MTA](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#fonts-for-mta-statistics).

## SpamAssassin {#spamassassin}

SpamAssassin permet d&#39;attribuer un score aux emails afin de déterminer si un message risque d&#39;être considéré comme indésirable par les outils anti-spams utilisés à sa réception. Son installation est facultative.

La qualification des emails par SpamAssassin comme indésirables repose intégralement sur l&#39;utilisation d&#39;un ensemble de règles de filtrage et de scores. La mise à jour de ces règles, au moins une fois par jour, est donc indispensable pour que votre installation de SpamAssassin et son intégration dans Adobe Campaign soient pleinement opérationnelles et garantissent la pertinence des scores attribués à vos diffusions avant leur envoi. Cette mise à jour est de la responsabilité de l&#39;administrateur du serveur qui héberge SpamAssassin.

La version minimale prise en charge est : **3.4**

SpamAssassin nécessite un accès internet HTTP (tcp/80).

Les étapes d’installation et de configuration de SpamAssassin sont présentées dans la section [Paramétrage de SpamAssassin](../../installation/using/configuring-spamassassin.md).
