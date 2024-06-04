---
product: campaign
title: Serveur applicatif
description: Serveur applicatif
feature: Installation
badge-v7-prem: label="On-Premise/hybride uniquement" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 87103c31-1530-4f8d-ab3a-6ff73093b80c
source-git-commit: 7e1c3b256cf43232e49d9daa0bf44d1e114b565b
workflow-type: tm+mt
source-wordcount: '622'
ht-degree: 59%

---

# Serveur applicatif{#application-server}

Les couches d&#39;accès pour le moteur de base de données que vous utilisez doivent être installées sur votre serveur et accessibles depuis le compte Adobe Campaign.

## Java Development Kit - JDK {#java-development-kit---jdk}

Java Development Kit, ou JDK, est un kit de développement logiciel. Il s’agit du composant de base qui permet le développement d’applications Java et Java.

Le module de génération de pages Web dynamiques repose sur la technologie JSP 1.2. A cet effet, un moteur Tomcat (d&#39;origine Apache) est inclus dans l&#39;application. Il nécessite la présence d&#39;un Java Development Kit (JDK), installé sur tous les serveurs sur lesquels l&#39;application Adobe Campaign sera installée.

Vous devez installer un JDK sur les machines sur lesquelles vous comptez lancer le serveur applicatif Adobe Campaign (processus **nlserver web**), car il intègre un container de servlets Apache Tomcat utilisées pour la génération des pages web dynamiques (reporting, formulaires web, etc.).

L&#39;application a été validée pour le JDK développé par Oracle ainsi que pour **OpenJDK**.

Les versions prises en charge sont détaillées dans la [matrice de compatibilité](../../rn/using/compatibility-matrix.md) de Campaign.


### Recommandations

Lors de l’installation et de la mise à niveau de votre kit de développement Java, appliquez les recommandations suivantes :

* Java Development Kit peut être installé à l’aide de la version appropriée du JDK déjà utilisée par d’autres applications sur l’ordinateur.

* Lors de l’installation du JDK, l’intégration avec les navigateurs Web n’est pas requise.

* Sur une machine qui exécute uniquement les agents de diffusion (**nlserver mta** processus) ou le serveur de workflow (**nlserver wfserver** ), l’installation d’un JDK n’est pas requise.

* Afin de préserver le fonctionnement optimal de votre plateforme et de conserver la compatibilité avec la version installée, vous devez impérativement désactiver les fonctions de mise à jour automatique du JDK sous Windows et Linux.

* Lors de la mise à niveau de votre version Java, vous devez d’abord désinstaller la version précédente. Les deux versions de Java installées sur le même ordinateur peuvent provoquer des conflits.

  En tant que client On-premise, vous pouvez vérifier la variable `LD_LIBRARY_PATH` [variable d&#39;environnement](installing-packages-with-linux.md#environment-variables) est défini sur la dernière version (par exemple, java11). S’il est défini sur une version précédente (par exemple, Java8), il doit ensuite être mis à jour. Pour JDK 11, le chemin pour localiser les bibliothèques JDK est : `/usr/lib/jvm/java-11-openjdk-amd64/lib`.


### Etapes d&#39;installation

Java Development Kit est spécifique à la plateforme : des programmes d’installation distincts sont nécessaires pour chaque système d’exploitation.

Pour télécharger le JDK, connectez-vous à [Oracle de site web](https://www.oracle.com/technetwork/java/javase/downloads/index.html){target="_blank"}.

>[!CAUTION]
>
> Veillez à télécharger un kit de développement Java (JDK) et non un environnement d’exécution Java (JRE).


Pour installer le JDSL dans un environnement Linux, Adobe recommande d’utiliser un gestionnaire de packages.

Pour Debian, utilisez la commande suivante :

```sql
aptitude install openjdk-8-jdk
```

Pour RHEL, utilisez la commande suivante :

```sql
yum install java-1.8.0-openjdk
```


## OpenSSL {#openssl}

Sous Linux, OpenSSL doit être installé. Adobe Campaign prend en charge OpenSSL version 1.0.2 ou ultérieure.

## Exporter des rapports {#exporting-reports}

Vous pouvez utiliser Adobe Campaign pour exporter des rapports vers Microsoft Excel et Adobe PDF.

* Pour le format Excel Microsoft, Adobe Campaign repose sur **LibreOffice**.

* Pour le format Adobe PDF, Adobe Campaign utilise le convertisseur **PhantomJS**. PhantomJS est fourni dans le package d&#39;usine, et LibreOffice doit être installé sur la ou les machines sur lesquelles s&#39;exécute le serveur applicatif Adobe Campaign (processus **nlserver web**).

>[!NOTE]
>
>Pour Linux, vous devez ajouter des polices. Voir à ce sujet la section [Polices de caractères pour les statistiques MTA](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#fonts-for-mta-statistics).

## SpamAssassin {#spamassassin}

SpamAssassin permet d&#39;attribuer un score aux emails afin de déterminer si un message risque d&#39;être considéré comme indésirable par les outils anti-spams utilisés à sa réception. Son installation est facultative.

La qualification des emails par SpamAssassin comme indésirables repose intégralement sur l&#39;utilisation d&#39;un ensemble de règles de filtrage et de scores. La mise à jour de ces règles, au moins une fois par jour, est donc indispensable pour que votre installation de SpamAssassin et son intégration dans Adobe Campaign soient pleinement opérationnelles et garantissent la pertinence des scores attribués à vos diffusions avant leur envoi. Cette mise à jour est de la responsabilité de l&#39;administrateur du serveur qui héberge SpamAssassin.

La version minimale prise en charge est : **3.4**

SpamAssassin nécessite un accès internet HTTP (tcp/80).

Les étapes d’installation et de configuration de SpamAssassin sont présentées dans la section [Paramétrage de SpamAssassin](../../installation/using/configuring-spamassassin.md).
