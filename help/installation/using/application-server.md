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
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '649'
ht-degree: 100%

---

# Serveur applicatif{#application-server}

Les couches d&#39;accès pour le moteur de base de données que vous utilisez doivent être installées sur votre serveur et accessibles depuis le compte Adobe Campaign.

## Java Development Kit - JDK {#jdk}

Le kit de développement Java, ou JDK, est un kit de développement logiciel. Il s’agit du composant de base qui permet l’utilisation de Java et le développement d’applications Java.

Le module de génération de pages Web dynamiques utilise la technologie JSP. À cet effet, un moteur Tomcat (d’origine Apache) est inclus dans l’application. Il nécessite la présence d&#39;un Java Development Kit (JDK), installé sur tous les serveurs sur lesquels l&#39;application Adobe Campaign sera installée.

Vous devez installer un JDK sur les machines sur lesquelles vous comptez lancer le serveur applicatif Adobe Campaign (processus **nlserver web**), car il intègre un container de servlets Apache Tomcat utilisées pour la génération des pages web dynamiques (reporting, formulaires web, etc.).

L&#39;application a été validée pour le JDK développé par Oracle ainsi que pour **OpenJDK**.

Les versions prises en charge sont détaillées dans la [matrice de compatibilité](../../rn/using/compatibility-matrix.md) de Campaign.


>[!AVAILABILITY]
>
>* À compter de la version v7.4.1, Campaign requiert au moins **Java JDK 11**. Si votre serveur Campaign est installé dans un environnement Windows, le Java Runtime (JRE) n’est plus détecté automatiquement. La variable d’environnement JRE_HOME doit être définie sur le dossier dans lequel Campaign peut localiser le fichier `bin/server/jvm.dll`. Par exemple, si votre JDK 11 est installé sous le dossier `C:\Program Files\Java\jdk-11`, votre JRE_HOME doit être `C:\Program Files\Java\jdk-11`.
>
>* À compter de la version 7.4.1, Tomcat 10.1 est la version par défaut.
>

### Recommandations

Lors de l’installation et de la mise à niveau de votre kit de développement Java, appliquez les recommandations suivantes :

* Le kit de développement Java peut être installé en utilisant la version adéquate du JDK déjà utilisée par d’autres applications sur la machine.

* Lors de l’installation du JDK, l’intégration aux navigateurs web n’est pas requise.

* Sur une machine exécutant uniquement des agents de diffusion (processus **nlserver mta**) ou le serveur de workflow (processus **nlserver wfserver**), l’installation du JDK n’est pas nécessaire.

* Lors de la mise à niveau de votre version de Java, vous devez d’abord désinstaller la version précédente. Deux versions de Java installées sur la même machine peuvent provoquer des conflits.

  En tant que client ou cliente On-premise, vous pouvez vérifier si la `LD_LIBRARY_PATH` [variable d’environnement](installing-packages-with-linux.md#environment-variables) est définie sur la dernière version (par exemple, java11). Si celle-ci est définie sur une version précédente (par exemple, Java8), elle doit alors être mise à jour. Pour JDK 11, le chemin de l’emplacement des bibliothèques JDK est : `/usr/lib/jvm/java-11-openjdk-amd64/lib`.


### Étapes d’installation

Le kit de développement Java est spécifique à la plateforme : des programmes d’installation différents sont nécessaires pour chaque système d’exploitation.

Pour télécharger le JDK, connectez-vous au [site web d’Oracle](https://www.oracle.com/technetwork/java/javase/downloads/index.html){target="_blank"}.

>[!CAUTION]
>
> Assurez-vous de télécharger un kit de développement Java (JDK) et non un environnement d’exécution Java (JRE).


Pour installer le JDSL dans un environnement Linux, il est préférable d’utiliser un gestionnaire de packages.

Pour Debian, utilisez la commande suivante :

```sql
apt install openjdk-11-jdk-headless
```

Pour RHEL, utilisez la commande suivante :

```sql
dnf install java-11-openjdk-headless
```



## Exporter des rapports {#exporting-reports}

Vous pouvez utiliser Adobe Campaign pour exporter des rapports aux formats Microsoft Excel et Adobe PDF.

* Pour le format Microsoft Excel, Adobe Campaign utilise **LibreOffice**.

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
