---
product: campaign
title: Prérequis pour l'installation de Campaign sous Linux
description: Prérequis pour l'installation de Campaign sous Linux
feature: Installation, Instance Settings
badge-v7-prem: label="On-Premise/hybride uniquement" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: acbd2873-7b1c-4d81-bc62-cb1246c330af
source-git-commit: f032ed3bdc0b402c8281bc34e6cb29f3c575aaf9
workflow-type: tm+mt
source-wordcount: '829'
ht-degree: 92%

---

# Prérequis pour l’installation de Campaign sous Linux{#prerequisites-of-campaign-installation-in-linux}

## Logiciels prérequis {#software-prerequisites}

Cette section présente les étapes préliminaires de paramétrage indispensables avant de procéder à l&#39;installation d&#39;Adobe Campaign.

La configuration technique et logicielle requise pour l&#39;installation d&#39;Adobe Campaign est présentée dans la [Matrice de compatibilité](../../rn/using/compatibility-matrix.md).

Pour rappel, les composants suivants doivent être installés et correctement paramétrés :

* Apache, voir [Matrice de compatibilité](../../rn/using/compatibility-matrix.md),
* JDK Java et OpenJDK, voir la section [Java Development Kit - JDK](../../installation/using/application-server.md#jdk),
* Librairies, voir la section [Librairies](#libraries),
* Couches d&#39;accès base de données, voir la section [Couches d&#39;accès base de données](#database-access-layers),
* LibreOffice, voir les sections [Installation de LibreOffice sous Debian](#installing-libreoffice-for-debian) et [Installation de LibreOffice sous CentOS](#installing-libreoffice-for-centos),
* Polices, voir les sections [Polices de caractères pour les statistiques MTA](#fonts-for-mta-statistics) et [Polices de caractères pour les instances japonaises](#fonts-for-japanese-instances).


### Librairies {#libraries}

Pour installer Adobe Campaign sous Linux, vérifiez que vous disposez des librairies requises.

* La bibliothèque C doit supporter le mode TLS (Thread Local Storage). Ce mode est actif dans la plupart des cas, sauf avec certains kernels dans lesquels le support Xen a été activé.

  Pour le vérifier, vous pouvez par exemple utiliser la commande **uname -a | grep xen**.

  Si la commande ne renvoie pas de ligne vide, cela signifie que la configuration est correcte.

* Vous devez disposer de la version OpenSSL **1.0.2** ou d’une version ultérieure.

  Pour les distributions RHEL, la version 1.0 d’OpenSSL est requise.

* Pour utiliser Adobe Campaign, la librairie suivante doit être installée : **libicu**.

### SELinux {#selinux}

Lorsqu&#39;il est utilisé, le module SELinux doit être convenablement configuré.

Pour cela, connectez-vous en tant que root et saisissez la commande suivante :

```
echo 0 >/selinux/enforce
```

En complément, dans le fichier **/etc/sysconfig/httpd**, la ligne suivante a été ajoutée afin de référencer le script de configuration de l&#39;environnement Adobe Campaign :

```
. ~neolane/nl6/env.sh
```

Sous RHEL et CentOS, des problèmes de compatibilité avec les couches clientes des bases de données ont été constatées lorsque SELinux est activé. Pour assurer le bon fonctionnement d&#39;Adobe Campaign, nous vous conseillons de désactiver SELinux.

**Procédez de la manière suivante :**

* Éditez le fichier **/etc/selinux/config**

* Modifiez la ligne SELINUX comme suit :

```
SELINUX=disabled
```

### Polices de caractères pour les statistiques MTA {#fonts-for-mta-statistics}

Pour que les rapports concernant les statistiques MTA (nms/fra/jsp/stat.jsp) s&#39;affichent correctement, vous devez ajouter des polices supplémentaires.

Sous Debian, utilisez la commande :

```
apt install xfonts-base xfonts-75dpi ttf-bitstream-vera ttf-dejavu
```

Utilisez la commande suivante pour RHEL :

```
dnf install xorg-x11-fonts-misc xorg-x11-fonts-75dpi dejavu-lgc-sans-fonts  dejavu-sans-fonts dejavu-sans-mono-fonts dejavu-serif-fonts
```

### Polices de caractères pour les instances japonaises {#fonts-for-japanese-instances}

Des polices de caractères spécifiques sont nécessaires pour les instances japonaises afin de pouvoir exporter les rapports au format PDF.

Sous Debian, utilisez la commande :

```
apt install fonts-ipafont
```

Pour RHEL, ajoutez la commande suivante :

```
dnf install epel-release # if required
dnf install vlgothic-fonts
```

### Installation de LibreOffice sous Debian {#installing-libreoffice-for-debian}

Les paramétrages suivants sont nécessaires sous Debian :

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

```
yum install libreoffice-headless libreoffice-writer libreoffice-calc
```

## Couches d&#39;accès base de données {#database-access-layers}

Les couches d&#39;accès pour le moteur de base de données que vous utilisez doivent être installées sur votre serveur et accessibles depuis le compte Adobe Campaign. Selon le moteur de base de données utilisé, les versions et modes d&#39;installation peuvent différer.

Les versions des connecteurs CRM compatibles avec Adobe Campaign sont listées dans la [matrice de compatibilité](../../rn/using/compatibility-matrix.md).

Consultez également section générale [Base de données](../../installation/using/database.md).

### PostgreSQL {#postgresql}

Adobe Campaign prend en charge toutes les versions des bibliothèques clientes PostgreSQL de la version 9.6 : **libpq.so.5**.

L&#39;utilisation de PostgreSQL avec Adobe Campaign requiert également l&#39;installation des bibliothèques **pgcrypto** correspondantes.

### Oracle {#oracle}

Récupérez la version de la bibliothèque pour Debian 64 bits, soit : **libclntsh.so**, **libclntsh.so.19.1**, **libclntsh.so.18.1**, **libclntsh.so.12.1**, **libclntsh.so.11.1** ou **libclntsh.so.10.1**.

Vous pouvez obtenir un package RPM Linux depuis Oracle Technology Network.

>[!NOTE]
>
>Si vous avez déjà installé le client Oracle mais que l&#39;environnement global (par exemple : /etc/profile) n&#39;est pas correctement configuré, vous pouvez ajouter les informations manquantes dans le script **nl6/customer.sh**. Pour plus d&#39;informations, consultez la section [Variables d&#39;environnement](../../installation/using/installing-packages-with-linux.md#environment-variables).

**Résolution de problèmes et bonnes pratiques**

Les problèmes peuvent survenir après la mise à jour ou le changement de version d&#39;un client ou d&#39;un serveur Oracle ou lors de la première installation de l&#39;instance.

Si vous remarquez sur la console cliente qu&#39;il y a des décalages horaires inattendus (une ou plusieurs heures) entre les logs, le dernier traitement de workflow, le traitement suivant, etc, il pourrait y avoir un problème entre la bibliothèque du client Oracle et le serveur Oracle. Pour éviter ces problèmes :

1. Assurez-vous d&#39;utiliser la version **cliente complète**.

   Plusieurs problèmes ont été identifiés lors de l&#39;utilisation de la version Oracle Instant Client. De plus, il est impossible de modifier le fichier de fuseau horaire de cette version.

1. Assurez-vous que la **version cliente** et la **version du serveur de base de données** sont les **mêmes**.

   Le mélange de versions peut causer des problèmes malgré la matrice de compatibilité Oracle et les recommandations d&#39;alignement des versions du client et du serveur.

   Vérifiez également la valeur ORACLE_HOME pour être sûr qu&#39;elle désigne la version cliente attendue (si plusieurs versions sont installées sur la machine).

1. Assurez-vous que le client et le serveur utilisent le même **fichier de fuseau horaire**.

## Étapes de mise en œuvre {#implementation-steps}

L&#39;installation d&#39;Adobe Campaign sous Linux doit être réalisée dans l&#39;ordre suivant : installation du serveur puis paramétrage des instances.

Le processus d&#39;installation est décrit dans ce chapitre. Les étapes de l&#39;installation sont les suivantes :

* Etape 1 : Installation du serveur applicatif, voir la section [Installation de packages avec Linux](../../installation/using/installing-packages-with-linux.md).
* Etape 2 : Intégration à un serveur Web (optionnel, en fonction des composants déployés).

Une fois les étapes d&#39;installation terminées, vous devez configurer les instances, la base de données et le serveur. Voir à ce sujet la section [À propos de la configuration initiale](../../installation/using/about-initial-configuration.md).
