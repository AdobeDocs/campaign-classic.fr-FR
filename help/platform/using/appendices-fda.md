---
title: Annexes
seo-title: Annexes de FDA
description: Annexes de FDA
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
source-git-commit: 353f5df040087175c9f211308704f1af1844ef2c
workflow-type: tm+mt
source-wordcount: '1418'
ht-degree: 1%

---


# Annexes {#fda-appendices}

## Teradata configurations supplémentaires {#teradata-configuration}

### Compatibilité {#teradata-compatibility}

**Basé sur Unicode**

| Version de base de données | Version du pilote | Version minimale de Campaign requise | Remarque |
|:-:|:-:|:-:|:-:|
| 15 | 15 | Campaign Classic 17.9 | Sous Linux : Les Requêtes avec horodatage peuvent échouer (corrigées dans la version 8937 pour 18.4 et 8977 pour 18.10) En mode débogage, des avertissements relatifs à une mauvaise utilisation de la mémoire dans le pilote peuvent se produire. |
| 15 | 16 | Campaign Classic 17.9 | Configuration recommandée pour une base de données Teradata 15 sous Linux. |
| 16 | 16 | Campaign Classic 18.10 | Les caractères Unicode avec des paires de substitution ne sont pas entièrement pris en charge. L’utilisation de caractères de substitution dans les données doit fonctionner. L’utilisation de substituts dans une condition de filtrage d’une requête ne fonctionnera pas sans cette modification. |
| 16 | 15 | non pris en charge |   |

**Basé dans Latin1**

Les versions antérieures à Adobe Campaign Classic 17.9 prenaient uniquement en charge la base de données Teradata Latin-1.

À partir d’Adobe Campaign Classic 17.9, nous prenons désormais en charge la base de données Teradata par défaut dans Unicode.

Les clients dont la base de données Teradata Latin-1 est migrée vers une version récente du Campaign Classic devront ajouter le paramètre APICharSize=1 dans les options du compte externe.

### Configuration de la base de données {#database-configuration}

#### Configuration utilisateur {#user-configuration}

Les droits suivants sont requis : créer/déposer/exécuter des procédures personnalisées, créer/déposer/insérer/sélectionner des tables. Vous devrez peut-être également créer des fonctions de mode utilisateur si vous souhaitez utiliser les fonctions md5 et sha2 sur votre instance d’Adobe Campaign.

Assurez-vous de configurer le fuseau horaire approprié. Il doit correspondre à ce qui sera défini dans le compte externe créé dans l’instance d’Adobe Campaign.

L&#39;Adobe Campaign ne définit pas de mode de protection (de secours) sur les objets qu&#39;il va créer dans la base de données. Vous devrez peut-être définir une valeur par défaut pour l’utilisateur que l’Adobe Campaign utilisera pour se connecter à la base de données Teradata à l’aide de la requête suivante :

| désactiver les abandons par défaut |
| :-: |
| ```MODIFY USER $login$ AS NO FALLBACK;``` |

#### Installation de MD5 {#md5-installation}

Si vous souhaitez utiliser les fonctions md5 dans votre instance d’Adobe Campaign, vous devez installer la fonction de mode utilisateur sur votre base de données Teradata à partir de cette [page](https://downloads.teradata.com/download/extensibility/md5-message-digest-udf) (md5_20080530.zip).

La sha1 du fichier téléchargé est la suivante : 65cc0bb6935f72fcd84fef1ebcd64c00115dfd1e.

Pour installer md5 :

1. Décompressez le fichier md5_20080530.zip.

1. Accédez au répertoire md5/src.

1. Connectez-vous à votre base de données Teradata à l’aide de bteq.

1. Exécutez la commande bteq suivante :

   ```
   .run file = hash_md5.btq
   ```

#### Installation SHA2 {#sha2-installation}

Si vous souhaitez utiliser les fonctions sha2 dans votre instance d’Adobe Campaign, vous devrez installer la fonction de mode utilisateur sur votre base de données Teradata à partir de cette [page](https://github.com/akuroda/teradata-udf-sha2/archive/v1.0.zip) (teradata-udf-sha2-1.0.zip).

Le sha1 du fichier téléchargé se présente comme suit : e87438d37424836358bd3902cf1adeb629349780.

Pour installer sha2 :

1. Décompressez le fichier teradata-udf-sha2-1.0.zip.

1. Accédez au répertoire teradata-udf-sha2-1.0/src.

1. Connectez-vous à votre base de données Teradata à l’aide de bteq.

1. Exécutez les deux commandes bteq suivantes :

   ```
   .run file = hash_sha256.sql
   .run file = hash_sha512.sql
   ```

#### Installation de UDF_UTF16TO8 {#UDF-UTF16TO8-installation}

Si vous souhaitez utiliser les fonctions udf_utf16to8 dans votre instance d’Adobe Campaign, vous devez installer la fonction de mode utilisateur sur votre base de données Teradata à partir du kit **d’outils** Teradata Unicode de cette [page](https://downloads.teradata.com/download/tools/unicode-tool-kit) (utk_release1.7.0.0.zip).

Le sha1 du fichier téléchargé se présente comme suit : e58235f434f52c71316a577cb48e20b97d24f470.

Pour installer udf_utf16to8 :

1. Décompressez le fichier utk_release1.7.0.0.zip.

1. Recherchez udf_utf16to8.o dans les fichiers extraits et accédez au répertoire qui contient le fichier. Il doit être nommé utk_release1.7.0.0/utk_release1.7.0.0/04 TranslationUDFs/01 Teradata UDFs/suselinux-x8664/udf_installation/.

1. Connectez-vous à votre base de données Teradata à l’aide de bteq.

1. Saisissez la commande bteq suivante :

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
   
### Configuration du serveur Campaign pour Linux {#campaign-server-linux}

Les éléments suivants sont requis pour l&#39;installation du pilote :

* Pilote ODBC Teradata, qui se trouve dans cette [page](https://downloads.teradata.com/download/connectivity/odbc-driver/linux)

* Outils et utilitaires de métadonnées (utilisés pour le chargement en masse), disponibles dans cette [page](https://downloads.teradata.com/download/tools/teradata-tools-and-utilities-linux-installation-package-0)

Noms de fichiers et sha1 :

* tdodbc1620__linux_indep.16.20.00-1.tar.gz 121fdd978b56fe1304fc5cb7819741b0847f 44fd

* TeradataToolsAndUtilitiesBase_linux_indep.16.20.01.00.tar.gz b 29d0af5ffd8dcf68a9dbbaa6f8639387b19c563

S&#39;il n&#39;existe aucun package pour votre distribution Linux, vous pouvez installer comme expliqué sur CentOS 7 (par exemple en utilisant docker), puis copier le contenu de /opt/teradata sur votre serveur d&#39;Adobes Campaign.

#### Installation du pilote ODBC {#odbc-installation}

Pour installer le pilote ODBC :

1. Extrayez le fichier tdodbc1620__linux_indep.16.20.00.00-1.tar.gz.

1. Accédez au répertoire tdodbc1620.

1. Vous devrez peut-être corriger le script de configuration :

   ```
   "sed -i s/16.10/16.20/ setup_wrapper.sh".
   ```

1. Exécutez le fichier setup_wrapper.sh.

#### Installation des outils et utilitaires de métadonnées {#teradata-tools-installation}

Pour installer les outils :

1. Extrayez le fichier TeradataToolsAndUtilitiesBase_linux_indep.16.20.01.00.tar.gz.

1. Accédez au répertoire TeradataToolsAndUtilitiesBase/Linux/i386-x8664/tdicu.

1. Exécutez le fichier setup_wrapper.sh.

1. Accédez au répertoire TeradataToolsAndUtilitiesBase/Linux/i386-x8664/cliv2.

1. Exécutez le fichier setup_wrapper.sh.

1. Accédez au répertoire TeradataToolsAndUtilitiesBase/Linux/i386-x8664/tptbase.

1. Exécutez le fichier setup_wrapper.sh.

1. Un fichier libtelapi.so doit être disponible dans /opt/teradata/client/16.20/lib64.

#### Configuration du pilote {#driver-configuration}

To learn more on driver configuration, refer to this [section](../../platform/using/legacy-connectors.md#configure-access-to-teradata).

#### Variables d&#39;environnement {#environment-varaiables}

Pour en savoir plus sur les variables d&#39;environnement du serveur d&#39;Adobe Campaign, consultez cette [section](../../platform/using/legacy-connectors.md#configure-access-to-teradata).

### Configuration du serveur Campaign pour Windows #campaign-server-windows}

Vous devez d’abord télécharger les outils et utilitaires de métadonnées pour Windows. Vous pouvez le télécharger à partir de cette [page](https://downloads.teradata.com/download/tools/teradata-tools-and-utilities-windows-installation-package)

Assurez-vous d&#39;installer le pilote ODBC et la base de transport parallèle Teradata. Il installera telapi.dll utilisé pour charger en masse la base de données Teradata.

Assurez-vous que le chemin d&#39;accès du pilote et des utilitaires se trouve dans la variable PATH que nlserver aura pendant l&#39;exécution. Par défaut, le chemin d’accès est C:\Program Files (x86)\Teradata\Client\15.10\bin on Windows 32 bits or C:\Programme Files\Teradata\Client\15.10\bin on 64 bit).

### Dépannage des Comptes externes {#external-account-troubleshooting}

Si l’erreur suivante s’affiche lors du test de la connexion **TIM-030008 Date &#39;2&#39; : caractère(s) manquant(s) (iRc=-53)** assurez-vous que le pilote ODBC est correctement installé et que LD_LIBRARY_PATH (Linux) / PATH (Windows) est défini pour le serveur Campaign.

Erreur ODBC **ODB-240000 :[Nom de source de données Microsoft][ODBC Driver Manager]introuvable et aucun pilote par défaut spécifié.** survient avec Windows si vous utilisez un pilote 16.X. L&#39;Adobe Campaign s&#39;attend à ce que les métadonnées soient nommées &quot;{teradata}&quot; dans odbcinst.ini.
Si vous disposez d&#39;une version 18.10 du serveur d&#39;Adobes Campaign, vous pouvez ajouter ODBCDriverName=&quot;Teradata Database ODBC Driver 16.10&quot; dans les options du compte externe. Le numéro de version peut changer, le nom exact peut être trouvé en exécutant odbcad32.exe et en accédant à l&#39;onglet Drivers (Pilotes).
Pour la version inférieure à 18.10, vous devrez copier la section Teradata de odbcinst.ini créée par l&#39;installation du pilote dans une nouvelle section appelée Teradata,regedit peut être utilisée dans ce cas.

Si votre base est en latin1, vous devrez ajouter APICharSize=1 dans les options.

### Time zone {#timezone}

Les métadonnées utilisent un nom de fuseau horaire qui n’est pas standard. Vous pouvez trouver la liste sur le site [](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/oGKvgl7gCeBMTGrp59BnwA)Teradata. L&#39;Adobe Campaign essaiera de convertir le fuseau horaire donné dans la configuration externe en un élément que Teradata comprend. Si aucune correspondance n’est trouvée, le fuseau horaire GMT+X (ou GMT-X) le plus proche est trouvé pour la session, avec un avertissement dans le journal.

La conversion est effectuée en lisant un fichier appelé teradata_timezones.txt qui doit se trouver dans le répertoire de données suivant : /usr/local/neolane/nl6/datakit sous linux. Si vous modifiez ce fichier, veillez à contacter l’équipe d’Adobes Campaign pour apporter la modification au code source, sinon ce fichier sera remplacé lors de la prochaine mise à jour de Campaign.

Le fuseau horaire utilisé pour la connexion est indiqué lors de l&#39;exécution de nlserver avec le commutateur -verbose, par exemple :

```
15:04:04 >   ODB-240007 Teradata: will use 'Europe Central' as session time zone.
```

Si le fuseau horaire utilisé n&#39;est pas correct, une option nommée &quot;TimeZoneName&quot; peut être ajoutée sur le compte externe. Dans ce cas, utilisez la valeur de métadonnées, par exemple &quot;TimeZoneName=Europe Central&quot;.

Lors de l’utilisation du chargement en vrac, ou &quot;chargement rapide&quot; dans les documents de métadonnées, Campaign ne peut pas indiquer le fuseau horaire. Par conséquent, il est recommandé de définir le fuseau horaire par défaut de l’utilisateur que Campaign utilisera pour se connecter :

```
MODIFY USER $login$ AS TIME ZONE = 'Europe Central';
```

## Configuration de MySQL 5.7 {#mysql-57-configuration}

### Paramétrage du serveur {#server-configuration-mysql}

La configuration du serveur ne nécessite aucune procédure d’installation spécifique. L’Adobe Campaign doit fonctionner avec une base de données latin1, MySQL par défaut ou une base de données unicode.

### Installation du pilote {#driver-installation-mysql}

#### Debian {#debian-mysql}

Téléchargez mysql-apt-config.deb à partir de cette [page](https://dev.mysql.com/doc/mysql-apt-repo-quick-guide/en).

Installez la bibliothèque cliente :

```
$ dpkg -i mysql-apt-config_*_all.deb # choose mysql-5.7 in the configuration menu
$ apt update
$ apt install libmysqlclient20
```

#### Windows [#windows-mysql}

Téléchargez le connecteur C à partir de cette [page](https://dev.mysql.com/downloads/connector/c). Nous vous recommandons de télécharger la version 5.7.

Assurez-vous que le répertoire contenant libmysqlclient.dll est ajouté à la variable d&#39;environnement PATH que nlserver utilisera.

#### CentOS {#centos-mysql}

Téléchargez mysql57-community-release.noarch.rpm à partir de cette [page](https://dev.mysql.com/downloads/repo/yum).

Installez la bibliothèque cliente :

$ yum install mysql57-community-release-el7-9.noarch.rpm$ yum install mysql-community-libs

### Configuration du Compte externe {#external-account-mysql}

La configuration du compte externe ne nécessite aucune étape spécifique. Assurez-vous que le fuseau horaire et Utiliser les données Unicode sont définis en fonction de votre base de données.
