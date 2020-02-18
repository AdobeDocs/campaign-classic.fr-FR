---
title: Conditions préalables à l'installation de Campaign sous Linux
seo-title: Conditions préalables à l'installation de Campaign sous Linux
description: Conditions préalables à l'installation de Campaign sous Linux
seo-description: null
page-status-flag: never-activated
uuid: 65c7af3f-ca1d-4255-b54a-6a3c83af40ae
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
discoiquuid: 3e2ccb70-6c0c-435f-9c06-f3e5e40367bb
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: de04b5d3ceb883a571ee665f630be931a68a5a3e

---


# Conditions préalables à l&#39;installation de Campaign sous Linux{#prerequisites-of-campaign-installation-in-linux}

## Logiciels prérequis {#software-prerequisites}

Cette section présente les étapes préliminaires de paramétrage indispensables avant de procéder à l&#39;installation d&#39;Adobe Campaign.

La configuration technique et logicielle requise pour l&#39;installation d&#39;Adobe Campaign est présentée dans la [Matrice de compatibilité](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html).

Pour rappel, les composants suivants doivent être installés et correctement paramétrés :

* Apache, voir [Matrice de compatibilité](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html),
* JDK Java et OpenJDK, reportez-vous au kit de développement [Java - JDK](../../installation/using/application-server.md#java-development-kit---jdk),
* Libraries, refer to [Libraries](#libraries),
* calques d&#39;accès à la base de données, reportez-vous aux calques [d&#39;accès à la](#database-access-layers)base de données,
* LibreOffice, voir [Installation de LibreOffice pour Debian](#installing-libreoffice-for-debian) et [Installation de LibreOffice pour CentOS](#installing-libreoffice-for-centos),
* Polices, reportez-vous aux sections [Polices pour les statistiques](#fonts-for-mta-statistics) MTA et [Polices pour les instances](#fonts-for-japanese-instances)japonaises.

>[!NOTE]
>
>Pour l&#39;installation d&#39;un build inférieur ou égal à 8709 sur les plateformes CentOS 7 et Debian 8, le module apache access_compat doit être activé.

### Librairies {#libraries}

Pour installer Adobe Campaign sous Linux, vérifiez que vous disposez des librairies requises.

* La librairie C doit supporter le mode TLS (Thread Local Storage). Ce mode est actif dans la plupart des cas, sauf avec certains kernels dans lesquels le support Xen a été activé.

   Pour le vérifier, vous pouvez par exemple utiliser la commande **uname -a | grep xen**.

   La configuration est correcte lorsque cette commande ne retourne aucune information (ligne vide).

* Vous devez impérativement disposer de la version **0.9.8** ou **1.0** d&#39;OpenSSL.

   Pour les distributions RHEL 7, la version 1.0 d&#39;OpenSSL est requise.

* Pour utiliser Adobe Campaign, la librairie suivante doit être installée : **libicu**.

   Les versions supportées de **libicu** sont les suivantes (distribution 32bits ou 64bits) :

   * RHEL 7, CentOS 7 : libicu50
   * Debian 8 : libicu52
   * Debian 9 : libicu57
   Pour utiliser Adobe Campaign, vous devez avoir installé la bibliothèque libc-ares. Sous RHEL/CentOS, exécutez la commande suivante :

   ```
   yum install c-ares
   ```

   Sur Debian :

   ```
   aptitude install libc-ares2
   ```

### SELinux {#selinux}

Lorsqu&#39;il est utilisé, le module SELinux doit être convenablement configuré.

Pour cela, connectez-vous en tant que root et saisissez la commande suivante :

```
echo 0 >/selinux/enforce
```

In addition to this, in the **/etc/sysconfig/httpd** file, the following line was added to reference the Adobe Campaign environment configuration script:

```
. ~neolane/nl6/env.sh
```

Sous RHEL et CentOS, des problèmes de compatibilité avec les couches clientes des bases de données ont été constatées lorsque SELinux est activé. Pour assurer le bon fonctionnement d&#39;Adobe Campaign, nous vous conseillons de désactiver SELinux.

**Procédez de la manière suivante :**

* Edit the file **/etc/selinux/config**

* Modifiez la ligne SELINUX comme suit :

```
SELINUX=disabled
```

### Polices de caractères pour les statistiques MTA {#fonts-for-mta-statistics}

Pour que les rapports concernant les statistiques MTA (nms/fra/jsp/stat.jsp) s&#39;affichent correctement, vous devez ajouter des polices supplémentaires.

Sous Debian, utilisez la commande :

```
aptitude install xfonts-base xfonts-75dpi ttf-bitstream-vera ttf-dejavu
```

Sous Red Hat, utilisez la commande suivante :

```
yum install xorg-x11-fonts-base xorg-x11-fonts-75dpi bitstream-vera-fonts dejavu-lgc-fonts
```

### Polices de caractères pour les instances japonaises {#fonts-for-japanese-instances}

Des polices de caractères spécifiques sont nécessaires pour les instances japonaises afin de pouvoir exporter les rapports au format PDF.

Sous Debian, utilisez la commande :

```
aptitude install fonts-ipafont
```

Sous Red Hat, utilisez la commande :

```
yum install ipa-gothic-fonts ipa-mincho-fonts
```

### Installation de LibreOffice sous Debian {#installing-libreoffice-for-debian}

Les paramétrages suivants sont nécessaires sous Debian :

1. Installez les packages standard suivants :

   ```
   apt-get install libreoffice-writer libreoffice-calc libreoffice-java-common
   ```

1. Installez les polices suivantes (facultatives mais vivement recommandées pour les instances japonaises) :

   ```
   apt-get install fonts-ipafont
   ```

### Installation de LibreOffice sous CentOS {#installing-libreoffice-for-centos}

Les paramétrages suivants sont nécessaires sous CentOS :

1. Installez les packages standard suivants :

   ```
   yum install libreoffice-headless libreoffice-writer libreoffice-calc
   ```

1. Installez les polices suivantes (facultatives mais vivement recommandées pour les instances japonaises) :

   ```
   yum install ipa-gothic-fonts ipa-mincho-fonts
   ```

## Couches d&#39;accès base de données {#database-access-layers}

Les couches d&#39;accès pour le moteur de base de données que vous utilisez doivent être installées sur votre serveur et accessibles depuis le compte Adobe Campaign. Selon le moteur de base de données utilisé, les versions et modes d&#39;installation peuvent différer.

Les versions des connecteurs CRM compatibles avec Adobe Campaign sont listées dans la [matrice de compatibilité](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html).

Also check the general [Database](../../installation/using/database.md) section.

### PostgreSQL {#postgresql}

Adobe Campaign supports all versions of the PostgreSQL client libraries from version 7.2: (**libpq.so.5**, **libpq.so.4**, **libpq.so.3.2** and **libpq.so.3.1**).

L&#39;utilisation de PostgreSQL avec Adobe Campaign requiert également l&#39;installation des bibliothèques **pgcrypto** correspondantes.

### Oracle {#oracle}

Retrieve the library version for 64-bit Debian, i.e.: **libclntsh.so**, **libclntsh.so.11.1** and **libclntsh.so.10.1**.

Vous pouvez obtenir un package RPM Linux depuis Oracle Technology Network.

>[!NOTE]
>
>If you have already installed the Oracle client but the global environment (for instance: /etc/profile) isn&#39;t properly configured, you can add missing information to the **nl6/customer.sh** script For more on this, refer to [Environment variables](../../installation/using/installing-packages-with-linux.md#environment-variables).

**Résolution de problèmes et bonnes pratiques**

Les problèmes peuvent survenir après la mise à jour ou le changement de version d&#39;un client ou d&#39;un serveur Oracle ou lors de la première installation de l&#39;instance.

Si vous remarquez sur la console cliente qu&#39;il y a des décalages horaires inattendus (une ou plusieurs heures) entre les logs, le dernier traitement de workflow, le traitement suivant, etc, il pourrait y avoir un problème entre la librairie du client Oracle et le serveur Oracle. Pour éviter ces problèmes :

1. Assurez-vous d&#39;utiliser la version **cliente complète**.

   Plusieurs problèmes ont été identifiés lors de l&#39;utilisation de la version Oracle Instant Client. De plus, il est impossible de modifier le fichier de fuseau horaire de cette version.

1. Assurez-vous que la **version cliente** et la **version du serveur de base de données** sont les **mêmes**.

   Le mélange de versions peut causer des problèmes malgré la matrice de compatibilité Oracle et les recommandations d&#39;alignement des versions du client et du serveur.

   Vérifiez également la valeur ORACLE_HOME pour être sûr qu&#39;elle désigne la version cliente attendue (si plusieurs versions sont installées sur la machine).

1. Assurez-vous que le client et le serveur utilisent le même **fichier de fuseau horaire**.

### DB2 {#db2}

The library version supported is **libdb2.so**.

## Etapes de mise en oeuvre {#implementation-steps}

L&#39;installation d&#39;Adobe Campaign sous Linux doit être réalisée dans l&#39;ordre suivant : installation du serveur puis paramétrage des instances.

Le processus d&#39;installation est décrit dans ce chapitre. Les étapes de l&#39;installation sont les suivantes :

* Étape 1 : Pour installer le serveur d’applications, reportez-vous à [Installation de packages avec Linux](../../installation/using/installing-packages-with-linux.md).
* Etape 2 : Intégration à un serveur Web (optionnel, en fonction des composants déployés).

Une fois les étapes d’installation terminées, vous devez configurer les instances, la base de données et le serveur. For more on this, refer to [About initial configuration](../../installation/using/about-initial-configuration.md).
