---
title: Annexes
seo-title: Annexes FDA
description: Annexes FDA
seo-description: null
page-status-flag: never-activated
uuid: 2596fabc-679a-45c8-a62a-165c221654b7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: a84a73a9-9930-449f-8b81-007a0e9d5233
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 3b752b283a14bc75954fe46da5a21970c1e17fa1
workflow-type: tm+mt
source-wordcount: '1416'
ht-degree: 100%

---


# Annexes {#fda-appendices}

## Paramétrages complémentaires de Teradata {#teradata-configuration}

### Compatibilité {#teradata-compatibility}

**Basé sur Unicode**

| Version de la base de données | Version du pilote | Version minimale de Campaign requise | Remarque |
|:-:|:-:|:-:|:-:|
| 15 | 15 | Campaign Classic 17.9 | Sous Linux : les requêtes avec horodatage peuvent échouer (corrigées dans la build 8937 pour 18.4 et dans la build 8977 pour 18.10) En mode debug, des avertissements relatifs à une mauvaise utilisation de la mémoire dans le pilote peuvent s’afficher. |
| 15 | 16 | Campaign Classic 17.9 | Configuration recommandée pour une base de données Teradata 15 sous Linux. |
| 16 | 16 | Campaign Classic 18.10 | Les caractères Unicode avec des paires de substitution ne sont pas entièrement pris en charge. L’utilisation de caractères de substitution dans les données doit fonctionner. L’utilisation de substituts dans les critères de filtrage d’une requête ne fonctionnera pas sans cette modification. |
| 16 | 15 | non pris en charge |   |

**Basé sur Latin1**

Les versions antérieures à Adobe Campaign Classic 17.9 prenaient uniquement en charge la base de données Teradata Latin-1.

A partir d’Adobe Campaign Classic 17.9, nous prenons désormais en charge la base de données Teradata par défaut en Unicode.

Les clients dont la base de données Teradata Latin-1 est migrée vers une version récente de Campaign Classic devront ajouter le paramètre APICharSize=1 dans les options du compte externe.

### Configuration de la base de données {#database-configuration}

#### Configuration utilisateur {#user-configuration}

Les droits suivants sont requis : créer/déposer/exécuter des procédures personnalisées, créer/déposer/insérer/sélectionner des tables. Vous devrez peut-être également créer des fonctions de mode utilisateur si vous souhaitez utiliser les fonctions md5 et sha2 sur votre instance d’Adobe Campaign.

Assurez-vous de configurer le fuseau horaire approprié. Il doit correspondre à ce qui sera défini dans le compte externe créé dans l’instance d’Adobe Campaign.

Adobe Campaign ne définit pas de mode de protection (fallback) sur les objets qu’il va créer dans la base de données. Vous devrez peut-être définir une valeur par défaut pour l’utilisateur qu’Adobe Campaign utilisera pour se connecter à la base de données Teradata à l’aide de la requête suivante :

| désactiver le fallback par défaut |
| :-: |
| ```MODIFY USER $login$ AS NO FALLBACK;``` |

#### Installation de MD5 {#md5-installation}

Si vous souhaitez utiliser les fonctions md5 dans votre instance d’Adobe Campaign, vous devez installer la fonction de mode utilisateur sur votre base de données Teradata à partir de cette [page](https://downloads.teradata.com/download/extensibility/md5-message-digest-udf) (md5_20080530.zip).

La fonction sha1 du fichier téléchargé se présente comme suit : 65cc0bb6935f72fcd84fef1ebcd64c00115dfd1e.

Pour installer md5 :

1. Décompressez le fichier md5_20080530.zip.

1. Accédez au répertoire md5/src.

1. Connectez-vous à votre base de données Teradata à l’aide de bteq.

1. Exécutez la commande bteq suivante :

   ```
   .run file = hash_md5.btq
   ```

#### Installation SHA2 {#sha2-installation}

Si vous souhaitez utiliser les fonctions sha2 dans votre instance d’Adobe Campaign, vous devrez installer la fonction de mode utilisateur sur votre base de données Teradata à partir de cette [page](https://github.com/akuroda/teradata-udf-sha2/archive/v1.0.zip) (teradata-udf-sha2-1.0.zip).

La fonction sha1 du fichier téléchargé se présente comme suit : e87438d37424836358bd3902cf1adeb629349780.

Pour installer sha2 :

1. Décompressez le fichier teradata-udf-sha2-1.0.zip.

1. Accédez au répertoire teradata-udf-sha2-1.0/src.

1. Connectez-vous à votre base de données Teradata à l’aide de bteq.

1. Exécutez les deux commandes bteq suivantes :

   ```
   .run file = hash_sha256.sql
   .run file = hash_sha512.sql
   ```

#### Installation de UDF_UTF16TO8 {#UDF-UTF16TO8-installation}

Si vous souhaitez utiliser les fonctions udf_utf16to8 dans votre instance d’Adobe Campaign, vous devez installer la fonction de mode utilisateur sur votre base de données Teradata à partir **de la boîte à outils Teradata Unicode** de cette [page](https://downloads.teradata.com/download/tools/unicode-tool-kit) (utk_release1.7.0.0.zip).

La fonction sha1 du fichier téléchargé se présente comme suit : e58235f434f52c71316a577cb48e20b97d24f470.

Pour installer udf_utf16to8 :

1. Décompressez le fichier utk_release1.7.0.0.zip.

1. Recherchez udf_utf16to8.o dans les fichiers extraits et accédez au répertoire qui contient le fichier. Il doit être nommé utk_release1.7.0.0/utk_release1.7.0.0/04 TranslationUDFs/01 Teradata UDFs/suselinux-x8664/udf_installation/.

1. Connectez-vous à votre base de données Teradata à l’aide de bteq.

1. Saisissez la commande bteq suivante :

   ```
   REPLACE FUNCTION udf_utf16to8 (
   inputString VARCHAR(8000) CHARACTER SET UNICODE
   ) RETURNS VARCHAR(16000) CHARACTER SET LATIN
   LANGUAGE C
   NO SQL
   EXTERNAL NAME 'CO!i18n103!udf_utf16to8.o!F!udf_utf16to8'
   PARAMETER STYLE SQL;
   
   -- Test: should return 410042
   SELECT CAST(Char2HexInt(UDF_UTF16to8(_UNICODE'004100000042'XC)) AS VARCHAR(100));
   ```

### Configuration du serveur Campaign pour Linux {#campaign-server-linux}

Les éléments suivants sont requis pour l’installation du pilote :

* Pilote ODBC Teradata disponible sur cette [page](https://downloads.teradata.com/download/connectivity/odbc-driver/linux)

* Outils et utilitaires de Teradata (utilisés pour le chargement en masse), disponibles sur cette [page](https://downloads.teradata.com/download/tools/teradata-tools-and-utilities-linux-installation-package-0)

Noms de fichiers et sha1 :

* tdodbc1620__linux_indep.16.20.00.00-1.tar.gz 121fdd978b56fe1304fc5cb7819741b0847f44fd

* TeradataToolsAndUtilitiesBase__linux_indep.16.20.01.00.tar.gz b 29d0af5ffd8dcf68a9dbbaa6f8639387b19c563

S’il n’existe aucun package pour votre distribution Linux, vous pouvez suivre la procédure d’installation de CentOS 7 (par exemple en utilisant docker), puis copier le contenu de /opt/teradata sur votre serveur Adobe Campaign.

#### Installation du pilote ODBC {#odbc-installation}

Pour installer le pilote ODBC :

1. Extrayez le fichier tdodbc1620__linux_indep.16.20.00.00-1.tar.gz.

1. Accédez au répertoire tdodbc1620.

1. Vous devrez peut-être corriger le script de configuration :

   ```
   "sed -i s/16.10/16.20/ setup_wrapper.sh".
   ```

1. Exécutez setup_wrapper.sh.

#### Installation des outils et utilitaires Teradata {#teradata-tools-installation}

Pour installer les outils :

1. Extrayez le fichier TeradataToolsAndUtilitiesBase__linux_indep.16.20.01.00.tar.gz.

1. Accédez au répertoire TeradataToolsAndUtilitiesBase/Linux/i386-x8664/tdicu.

1. Exécutez setup_wrapper.sh.

1. Accédez au répertoire TeradataToolsAndUtilitiesBase/Linux/i386-x8664/cliv2.

1. Exécutez setup_wrapper.sh.

1. Accédez au répertoire TeradataToolsAndUtilitiesBase/Linux/i386-x8664/tptbase.

1. Exécutez setup_wrapper.sh.

1. Un fichier libtelapi.so doit être disponible dans /opt/teradata/client/16.20/lib64.

#### Configuration du pilote {#driver-configuration}

Pour plus d’informations sur la configuration du pilote, consultez cette [section](../../platform/using/legacy-connectors.md#configure-access-to-teradata).

#### Variables d’environnement {#environment-varaiables}

Pour en savoir plus sur les variables d’environnement du serveur d’Adobe Campaign, consultez cette [section](../../platform/using/legacy-connectors.md#configure-access-to-teradata).

### Configuration du serveur Campaign pour Windows {#campaign-server-windows}

Vous devez d’abord télécharger les outils et utilitaires Teradata pour Windows. Vous pouvez les télécharger à partir de cette [page](https://downloads.teradata.com/download/tools/teradata-tools-and-utilities-windows-installation-package)

Assurez-vous d’installer le pilote ODBC et la base de transport parallèle Teradata. Elle installera le fichier telapi.dll utilisé pour charger en masse la base de données Teradata.

Assurez-vous que le chemin d’accès du pilote et des utilitaires se trouve dans la variable PATH dont nlserver disposera pendant l’exécution. Par défaut, le chemin d’accès est C:\Program Files (x86)\Teradata\Client\15.10\bin sur Windows 32 bits or C:\Program Files\Teradata\Client\15.10\bin sur 64 bits).

### Résolution des problèmes liés au compte externe {#external-account-troubleshooting}

Si l’erreur suivante s’affiche lors du test de la connexion **TIM-030008 Date ’2’ : caractère(s) manquant(s) (iRc=-53)** assurez-vous que le pilote ODBC est correctement installé et que LD_LIBRARY_PATH (Linux) / PATH (Windows) est défini pour le serveur Campaign.

L’erreur **ODB-240000 ODBC : nom de source de données[Microsoft][ODBC Driver Manager]introuvable et aucun pilote par défaut spécifié.** survient avec Windows si vous utilisez un pilote 16.X. Adobe Campaign s’attend à ce que les données Teradata soient nommées ’{teradata}’ dans odbcinst.ini.
Si vous disposez de la version 18.10 du serveur d’Adobe Campaign, vous pouvez ajouter ODBCDriverName=&quot;Teradata Database ODBC Driver 16.10&quot; dans les options du compte externe. Le numéro de version peut changer, le nom exact peut être trouvé en exécutant odbcad32.exe et en accédant à l’onglet Pilotes.
Pour toute version antérieure à la version 18.10, vous devrez copier la section Teradata de odbcinst.ini créée par l’installation du pilote dans une nouvelle section appelée Teradata. Regedit peut être utilisé dans ce cas.

Si votre base est en latin1, vous devrez ajouter APICharSize=1 dans les options.

### Fuseau horaire {#timezone}

Teradata utilise un nom de fuseau horaire qui n’est pas standard. Vous pouvez trouver la liste sur le [site Teradata](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/oGKvgl7gCeBMTGrp59BnwA). Adobe Campaign essaiera de convertir le fuseau horaire donné dans la configuration externe en un élément que Teradata comprend. Si aucune correspondance n’est trouvée, le fuseau horaire GMT+X (ou GMT-X) le plus proche sera trouvé pour la session et un avertissement sera ajouté au journal.

La conversion est effectuée via la lecture du fichier appelé teradata_timezones.txt qui doit se trouver dans le répertoire de données suivant : /usr/local/neolane/nl6/datakit sous Linux. Si vous modifiez ce fichier, veillez à contacter l’équipe d’Adobe Campaign pour apporter la modification au code source, sans quoi, ce fichier sera remplacé lors de la prochaine mise à jour de Campaign.

Le fuseau horaire utilisé pour la connexion est indiqué lors de l’exécution de nlserver avec le commutateur -verbose, par exemple :

```
15:04:04 >   ODB-240007 Teradata: will use 'Europe Central' as session time zone.
```

Si le fuseau horaire utilisé n’est pas correct, une option nommée « TimeZoneName » peut être ajoutée sur le compte externe. Dans ce cas, utilisez la valeur Teradata, par exemple « TimeZoneName=Europe Central ».

Lors de l’utilisation du chargement en masse, ou « chargement rapide » dans les documents Teradata, Campaign ne peut pas indiquer le fuseau horaire. Par conséquent, il est recommandé de définir le fuseau horaire par défaut de l’utilisateur que Campaign utilisera pour se connecter :

```
MODIFY USER $login$ AS TIME ZONE = 'Europe Central';
```

## Configuration de MySQL 5.7 {#mysql-57-configuration}

### Configuration du serveur {#server-configuration-mysql}

La configuration du serveur ne nécessite aucune procédure d’installation spécifique. Adobe Campaign doit fonctionner avec une base de données latin1, MySQL par défaut, ou une base de données Unicode.

### Installation du pilote {#driver-installation-mysql}

#### Debian {#debian-mysql}

Téléchargez mysql-apt-config.deb à partir de cette [page](https://dev.mysql.com/doc/mysql-apt-repo-quick-guide/en).

Installez la bibliothèque cliente :

```
$ dpkg -i mysql-apt-config_*_all.deb # choose mysql-5.7 in the configuration menu
$ apt update
$ apt install libmysqlclient20
```

#### Windows {#windows-mysql}

Téléchargez le connecteur C à partir de cette [page](https://dev.mysql.com/downloads/connector/c). Nous vous recommandons de télécharger la version 5.7.

Assurez-vous que le répertoire contenant libmysqlclient.dll est ajouté à la variable d’environnement PATH que nlserver utilisera.

#### CentOS {#centos-mysql}

Téléchargez mysql57-community-release.noarch.rpm à partir de cette [page](https://dev.mysql.com/downloads/repo/yum).

Installez la bibliothèque cliente :

$ yum install mysql57-community-release-el7-9.noarch.rpm
$ yum install mysql-community-libs

### Configuration du compte externe {#external-account-mysql}

La configuration du compte externe ne nécessite aucune étape spécifique. Assurez-vous que le fuseau horaire et l’option Utiliser les données Unicode sont correctement définis par rapport à votre base de données.
