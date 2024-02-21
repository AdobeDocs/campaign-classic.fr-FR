---
product: campaign
title: Le fichier de configuration du serveur
description: Le fichier de configuration du serveur
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
audience: installation
content-type: reference
topic-tags: appendices
exl-id: 70cd6a4b-c839-4bd9-b9a7-5a12e59c0cbf
source-git-commit: 668cee663890fafe27f86f2afd3752f7e2ab347a
workflow-type: tm+mt
source-wordcount: '8075'
ht-degree: 76%

---

# Le fichier de configuration du serveur{#the-server-configuration-file}



La configuration globale d’Adobe Campaign est définie dans le fichier **serverConf.xml** qui se trouve dans le répertoire **conf** du répertoire d’installation. Cette section répertorie l’ensemble des nœuds et des paramètres du fichier **serverConf.xml**.

>[!NOTE]
>
>Les configurations côté serveur ne peuvent être exécutées que par Adobe pour les déploiements hébergés par Adobe. Pour en savoir plus sur les différents déploiements, consultez la section [Modèles d&#39;hébergement](../../installation/using/hosting-models.md) ou [cette page](../../installation/using/capability-matrix.md). Les étapes d&#39;installation et de configuration des modèles hébergés et hybrides sont présentées dans cette [section](../../installation/using/hosting-models.md).

Les premiers paramètres se trouvent dans le nœud **shared**. Ils sont liés à l’instance et peuvent être utilisés par toutes les commandes nlserver (nlserver web, nlserver wfserver, etc.). Les autres sections se rapportent à une sous-commande spécifique de nlserver.

**Paramètres partagés**

* [authentication](#authentication)
* [dataStore](#datastore)
* [dnsConfig](#dnsconfig)
* [exec](#exec)
* [htmlToPdf](#htmltopdf)
* [IMS](#ims)
* [javaScript](#javascript)
* [mailExchanger](#mailexchanger)
* [module](#module)
* [monitoring](#monitoring)
* [ooconv](#ooconv)
* [proxyConfig](#proxyconfig)
* [threadPool](#threadpool)
* [urlPermission](#urlpermission)
* [cusHeaders](#cusheaders)
* [xtkJobs](#xtkjobs)

**Autres paramètres**

* [archiving](#archiving)
* [inMail](#inmail)
* [interactiond](#interactiond)
* [mta](#mta)
* [nmac](#nmac)
* [pipelined](#pipelined)
* [repair](#repair)
* [securityZone](#securityzone)
* [sms](#sms)
* [stat](#stat)
* [syslogd](#syslogd)
* [tracking](#tracking)
* [trackinglogd](#trackinglogd)
* [web](#web)
* [wfserver](#wfserver)

## authentication {#authentication}

Voici les différents paramètres du nœud **authentication** :

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Valeur par défaut </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> checkIPConsistent<br /> </td> 
   <td> Activer la vérification des adresses IP.<br /> </td> 
   <td> Booléen<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> defaultMode<br /> </td> 
   <td> Mode d’identification par défaut.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> 'nl'<br /> </td> 
  </tr> 
  <tr> 
   <td> longSessionTimeOutSec<br /> </td> 
   <td> Timeout des sessions longues en secondes.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1296000<br /> </td> 
  </tr> 
  <tr> 
   <td> securityTimeOutSec<br /> </td> 
   <td> Timeout du jeton de sécurité en secondes.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> sessionCacheSec<br /> </td> 
   <td> Durée de mise en cache : cache des informations de session en secondes.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> sessionTimeOutSec<br /> </td> 
   <td> Timeout de session en secondes.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
 </tbody> 
</table>

### XTK {#xtk}

Voici les différents paramètres du nœud **authentication > XTK** :

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Valeur par défaut </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> internalPassword<br /> </td> 
   <td> Mot de passe du compte internal.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> internalSecurityZone<br /> </td> 
   <td> Zone de sécurité du compte internal : zone autorisée pour le compte internal.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> 'lan'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## dataStore {#datastore}

Voici les différents paramètres du nœud **dataStore**. C’est là que vous définissez les sources de données du serveur.

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Valeur par défaut </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> exportDirectory<br /> </td> 
   <td> Répertoire d’export : chemin du répertoire destination pour les données exportées.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/export/' <br /> </td> 
  </tr> 
  <tr> 
   <td> extraSandboxedDirectories<br /> </td> 
   <td> Répertoires en sandbox supplémentaires : autres chemins à ajouter au sandbox (séparés par une virgule).<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> '/home/customers/,/sftp/' <br /> </td> 
  </tr> 
  <tr> 
   <td> formCacheTimeToLive<br /> </td> 
   <td> Délai d’expiration du cache de formulaire : délai en secondes au-delà duquel une entrée de cache est invalidée. O signifie que les entrées du cache ne sont actualisées qu’au moment de la publication.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> hosts<br /> </td> 
   <td> Masques DNS : liste des masques DNS utilisés par cette instance (séparés par des virgules, peut utiliser les caractères * et ? modèles).<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> '*'<br /> </td> 
  </tr> 
  <tr> 
   <td> interactionCacheTimeToLive<br /> </td> 
   <td> Délai d’expiration du cache JSSP d’interaction : délai en secondes au-delà duquel une entrée de cache est invalidée. Une valeur négative signifie que le cache est toujours invalidé. Les valeurs "0", vides ou non valides sont considérées comme 60.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> lang<br /> </td> 
   <td> Langue de l'instance (énumération). Les valeurs possibles sont 'fr_FR' (Français), 'en_GB' (Anglais (UK)), 'en_US' (Anglais (US)), 'de_DE' (Deutsch) et 'ja_JP' (Japonais).<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> 'en_US'<br /> </td> 
  </tr> 
  <tr> 
   <td> uploadDirectory<br /> </td> 
   <td> Répertoire d’upload : chemin du répertoire destination pour les données téléchargées.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/upload/' <br /> </td> 
  </tr> 
  <tr> 
   <td> uploadAllowlist<br /> </td> 
   <td> Fichiers autorisés à être téléchargés séparés par des ','. La chaîne doit être une expression régulière Java valide. Voir la section <a href="file-res-management.md" target="_blank">Limitation des fichiers téléchargeables</a>.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> '.+' <br /> </td> 
  </tr> 
  <tr> 
   <td> useVault<br /> </td> 
   <td> Stocker les secrets dans Vault : utiliser Hashicorp Vault.<br /> </td> 
   <td> Booléen<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultSecretPath<br /> </td> 
   <td> Chemin d’accès du secret dans Vault<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> '/v1/secret/campaign/'<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultTokenPath<br /> </td> 
   <td> Chemin d’accès local du fichier contenant le jeton de coffre. $(HOME) peut être utilisé dans ce chemin (mais pas d’autres variables d’environnement).<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> '$(HOME)/.vaulttoken'<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultUrl<br /> </td> 
   <td> URL de Hashicorp Vault <br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> viewCacheTimeToLive<br /> </td> 
   <td> Délai de validité du cache des vues : délai en secondes au-delà duquel une entrée du cache est invalidée. Une valeur négative signifie que le cache est toujours invalidé. Les valeurs "0", vides ou non valides sont considérées comme 60.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> workingDirectory<br /> </td> 
   <td> Chemin du répertoire de travail.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> workingDirectory : chemin du répertoire de travail. Valeur par défaut : '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/workspace/'<br /> </td> 
  </tr> 
 </tbody> 
</table>

### proxyAdjust {#proxyadjust}

Voici les différents paramètres du nœud **dataStore > proxyAdjust**. Les URL correspondant à l’expression régulière seront regénérées à partir de l’URL définie dans urlBase.

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> urlBase<br /> </td> 
   <td> Base à utiliser lors de la génération d’URL externes. Ex : https://server.domain.com<br /> </td> 
   <td> Chaîne <br /> </td> 
  </tr> 
  <tr> 
   <td> urlRegEx<br /> </td> 
   <td> Expression régulière pour correspondre aux URL. Ex : http://server\.lan\.net.*<br /> </td> 
   <td> Chaîne <br /> </td> 
  </tr> 
 </tbody> 
</table>

### dataSource {#datasource}

Voici les différents paramètres du nœud **dataStore > dataSource**.

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Valeur par défaut </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> name<br /> </td> 
   <td> Nom de la source de données<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> default<br /> </td> 
  </tr> 
 </tbody> 
</table>

Dans le nœud **dataStore > dataSource > dbcnx**, configurez les paramètres de connexion :

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Valeur par défaut<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> NChar<br /> </td> 
   <td> Stockage unicode<br /> </td> 
   <td> Booléen<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> dbSchema<br /> </td> 
   <td> Espace de travail<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> chiffré<br /> </td> 
   <td> Mot de passe chiffré<br /> </td> 
   <td> Booléen<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> login<br /> </td> 
   <td> Compte<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> password<br /> </td> 
   <td> Mot de passe<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> provider<br /> </td> 
   <td> Type (énumération). Les valeurs possibles sont 'Oracle', 'MSSQL' (Microsoft SQL Server), 'PostgreSQL' (PostgreSQL,), 'Teradata', 'DB2', 'MySQL', 'Netezza', 'AsterData', 'SAPHANA' (SAP HANA), 'RedShift' (Amazon Redshift), 'ODBC' (ODBC (Sybase ASE, Sybase IQ)), 'Relay' (relais HTTP vers base distante).<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> 'Oracle'<br /> </td> 
  </tr> 
  <tr> 
   <td> server<br /> </td> 
   <td> Serveur<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> timezone<br /> </td> 
   <td> Fuseau horaire : voir la section <a href="../../installation/using/time-zone-management.md" target="_blank">Gestion des fuseaux horaires</a>.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> unicodeData<br /> </td> 
   <td> Données unicode en base<br /> </td> 
   <td> Booléen<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> useTimestampTZ<br /> </td> 
   <td> Champs de date avec fuseau horaire : voir la section <a href="../../installation/using/time-zone-management.md" target="_blank">Gestion des fuseaux horaires</a>.<br /> </td> 
   <td> Booléen<br /> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

Dans le nœud **dataStore > dataSource > sqlParams**, configurez les paramètres SQL :

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> funcPrefix<br /> </td> 
   <td> Préfixe pour les fonctions<br /> </td> 
   <td> Chaîne <br /> </td> 
  </tr> 
 </tbody> 
</table>

Dans le nœud **dataStore > dataSource > pool**, configurez les paramètres du pool de connexions associé :

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> aliveTestDelaySec<br /> </td> 
   <td> Délai entre les tests de validité de la connexion.<br /> </td> 
   <td> Court<br /> </td> 
  </tr> 
  <tr> 
   <td> freeCnx<br /> </td> 
   <td> Nombre de connexions libres conservées dans le pool.<br /> </td> 
   <td> Court<br /> </td> 
  </tr> 
  <tr> 
   <td> maxCnx<br /> </td> 
   <td> Nombre maximum de connexions autorisées avant de refuser une nouvelle connexion. Voir <a href="https://helpx.adobe.com/fr/campaign/kb/how-to-increase-the-maximum-number-of-database-connections-from-.html">technote</a>.<br /> </td> 
   <td> Court<br /> </td> 
  </tr> 
  <tr> 
   <td> maxIdleDelaySec<br /> </td> 
   <td> Durée maximale d’inactivité de la connexion. 0 signifie valeur par défaut.<br /> </td> 
   <td> Court<br /> </td> 
  </tr> 
 </tbody> 
</table>

### virtualDir {#virtualdir}

Voici les différents paramètres du nœud **dataStore > virtualDir**. Il s’agit de la configuration du mapping entre les répertoires virtuels et réels.

Pour plus d&#39;informations, voir la section [Gestion des ressources publiques](file-res-management.md).

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> name<br /> </td> 
   <td> Nom du répertoire virtuel <br /> </td> 
   <td> Chaîne <br /> </td> 
  </tr> 
  <tr> 
   <td> path<br /> </td> 
   <td> Chemin complet du répertoire réel<br /> </td> 
   <td> Chaîne <br /> </td> 
  </tr> 
 </tbody> 
</table>

Voici la configuration par défaut :

```
<virtualDir name="images" path="$(XTK_INSTALL_DIR)/var/res/img/"/>
<virtualDir name="formCache" path="$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/formCache/"/>
<virtualDir name="publicFileRes" path="$(XTK_INSTALL_DIR)/var/res/$(INSTANCE_NAME)"/>
```

### preprocessCommand {#preprocesscommand}

Voici les différents paramètres du nœud **dataStore > preprocessCommand**. Il s’agit des commandes autorisées pour le pré-traitement de l’activité de workflow « Chargement du fichier ».

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> command<br /> </td> 
   <td> La ligne de commande <br /> </td> 
   <td> Chaîne <br /> </td> 
  </tr> 
  <tr> 
   <td> label<br /> </td> 
   <td> Libellé de ligne de commande<br /> </td> 
   <td> Chaîne <br /> </td> 
  </tr> 
  <tr> 
   <td> name<br /> </td> 
   <td> Nom de ligne de commande<br /> </td> 
   <td> Chaîne <br /> </td> 
  </tr> 
 </tbody> 
</table>

Voici la configuration par défaut :

```
<preprocessCommand command="" label="None" name="none"/>
<preprocessCommand command="zcat &quot;$fileName&quot;" label="Decompression" name="zcat"/><preprocessCommand command="gpg --decrypt &quot;$fileName&quot;" label="Decrypt" name="gpg"/>
```

## dnsConfig {#dnsconfig}

Voici les différents paramètres du nœud **dnsConfig** (configuration DNS).

Pour plus d’informations, consultez cette [section](../../installation/using/configuring-campaign-server.md).

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Valeur par défaut </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> localDomain<br /> </td> 
   <td> Domain name : default domain name. Utilisé par la commande SMTP HELO. Par défaut, utilise les paramètres réseau de la première interface réseau déclarée sous Windows ; ou analyse le fichier file/etc/resolv.conf sous Linux (entrée domain ou search). <br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> nameServers<br /> </td> 
   <td> Serveur DNS : liste séparée par des virgules des serveurs de noms de domaine (DNS). Voir la note ci-dessous.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> retry<br /> </td> 
   <td> Nombre de tentatives pour une requête DNS.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Timeout en millisecondes pour une requête DNS.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5000<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Remarque sur **nameSevers** : par défaut, utilise le réseau
>paramètres de la première interface réseau déclarée dans Windows
>non définie dans UNIX. Définit les serveurs de noms de domaine (DNS)
>utilisé par le MTA pour obtenir le Mail Exchanger déclaré pour
>un domaine.
>
>Si cette valeur n&#39;est pas définie, le MTA recherche ces informations dans la configuration du réseau hôte. Si plusieurs DNS sont possibles, les différentes adresses DNS doivent être séparées par une virgule (exemple : 212.155.207.1,212.155.207.2). Si votre serveur de diffusion comporte plusieurs interfaces réseau, la liste DNS utilisée par le MTA est la première. Dans ce cas, nous vous recommandons de spécifier le paramètre **nameServer** pour éviter toute ambiguïté.

>[!CAUTION]
>
>Si votre configuration d’hôte réseau utilise DHCP, le MTA ne trouvera pas la liste DNS fournie par DHCP. Dans ce cas, nous vous recommandons de spécifier la liste DNS dans les paramètres réseau du panneau de configuration de Windows.

## exec {#exec}

Voici les différents paramètres du nœud **exec** (exécution des commandes).

Pour plus d&#39;informations, voir la section [Restreindre les commandes externes autorisées](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands).

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> blacklistFile<br /> </td> 
   <td> Chemin d'accès au fichier contenant les commandes à ajouter à la liste autorisée. <br /> </td> 
   <td> Chaîne <br /> </td> 
  </tr> 
  <tr> 
   <td> user<br /> </td> 
   <td> Exécuter des commandes en tant qu’utilisateur différent.<br /> </td> 
   <td> Chaîne <br /> </td> 
  </tr> 
 </tbody> 
</table>

## htmlToPdf {#htmltopdf}

Voici les différents paramètres du nœud **htmlToPdf**. Il s’agit de la configuration du service de conversion de pages web en document PDF.

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Valeur par défaut </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> command<br /> </td> 
   <td> Ligne de commande à lancer pour effectuer la conversion (en mode 'other').<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessusCount<br /> </td> 
   <td> Max. Nombre maximum de processus de conversion qui peuvent exister simultanément sur une même machine.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> mode<br /> </td> 
   <td> Outil à utiliser pour la conversion. Les valeurs possibles sont : phantomjs, wkhtmltopdf, other, disabled<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> 'phantomjs' <br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Timeout pour une conversion : durée maximale de conversion en secondes. Au-delà de ce seuil, le processus de conversion est arrêté et une erreur est générée.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 120<br /> </td> 
  </tr> 
  <tr> 
   <td> verbose<br /> </td> 
   <td> Mode verbeux : lancer en mode verbeux afin de diagnostiquer d’éventuelles erreurs.<br /> </td> 
   <td> Booléen<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> waitTime<br /> </td> 
   <td> Délai lors de l’attente d’un processus : délai en secondes, lorsque tous les processus sont utilisés en même temps et en attendant la libération d’un processus. Si ce délai est dépassé, la conversion est arrêtée et une erreur est générée. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 15<br /> </td> 
  </tr> 
 </tbody> 
</table>

Exemple pour phantomjs :

```
phantomjs - -ignore-ssl-errors=true '$(XTK_INSTALL_DIR)/bin/htmlToPdf.js' '-out:{outPdf}' '-post:{postFile}' '-url:{originUrl}' -sessiontoken:{sessiontoken} -format:{format} -orientation:{orientation} -marginTop:{marginTop} -marginLeft:{marginLeft} -marginRight:{marginRight} -marginBottom:{marginBottom}
```

## IMS {#ims}

Voici les différents paramètres du nœud **IMS**. Il s&#39;agit de la configuration pour Campaign se connectant à un autre service à l&#39;aide de [IMS](../../integrations/using/about-adobe-id.md).

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Valeur par défaut </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> authIMSClientId<br /> </td> 
   <td> Identifiant du client<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSClientSecret<br /> </td> 
   <td> Clé secrète (chiffrée en AES)<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSCode<br /> </td> 
   <td> Code d'autorisation (chiffrée en AES)<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSEndpoint<br /> </td> 
   <td> URL du serveur IMS<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> 'https://ims-na1.adobelogin.com'<br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSTAClientId<br /> </td> 
   <td> Identifiant du client du compte technique<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSTAClientSecret<br /> </td> 
   <td> Clé secrète de compte technique (chiffrée en AES)<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSTAId<br /> </td> 
   <td> Identifiant du compte technique<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSTAPrivateKey<br /> </td> 
   <td> Clé privée de compte technique (chiffrée en AES)<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## JavaScript {#javascript}

Voici les différents paramètres du nœud **javaScript**. Il s’agit de la configuration de l’interpréteur JavaScript.

Pour plus d’informations, consultez la [documentation sur le compte-rendu de performances](../../reporting/using/actions-on-reports.md#memory-allocation).

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Valeur par défaut </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxMB<br /> </td> 
   <td> Taille maximum en méga-octets avant de déclencher le garbage collector.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 512 <br /> </td> 
  </tr> 
  <tr> 
   <td> stackSizeKB<br /> </td> 
   <td> Taille en kilo-octets de chaque bloc de pile. Il s’agit d’un paramètre d’optimisation de la gestion de la mémoire que la plupart des utilisateurs ne doivent pas ajuster. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 8<br /> </td> 
  </tr> 
 </tbody> 
</table>

## mailExchanger {#mailexchanger}

Voici les différents paramètres du nœud **mailExchanger**. Il s’agit de la configuration du serveur SMTP.

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Valeur par défaut </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> mxAddress<br /> </td> 
   <td> Serveur SMTP : adresse IP du serveur SMTP pour le transfert des emails.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> mxPort<br /> </td> 
   <td> Port TCP du serveur SMTP pour le transfert des emails.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

## module {#module}

Voici les différents paramètres du nœud **module**. Il s’agit de la configuration du module de restriction des espaces de noms xtk.

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Valeur par défaut </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> defaultNameSpace<br /> </td> 
   <td> Espace de noms par défaut lors de la création d’une nouvelle entité.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> 'cus'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## monitoring {#monitoring}

Voici les différents paramètres du nœud **monitoring**. Il s’agit de la configuration du service de surveillance.

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Valeur par défaut </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxPreparationJobsSec<br /> </td> 
   <td> Durée maximale de préparation : durée en secondes au-delà de laquelle une action de diffusion ne doit plus être en préparation.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 3600<br /> </td> 
  </tr> 
  <tr> 
   <td> unixScript<br /> </td> 
   <td> Script Unix à exécuter par le service de surveillance.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> winScript<br /> </td> 
   <td> Script Windows à exécuter par le service de surveillance.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## ooconv {#ooconv}

Voici les différents paramètres du nœud **ooconv**. Il s’agit de la configuration du serveur de conversion de documents.

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Valeur par défaut </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxConversions<br /> </td> 
   <td> Nombre maximum de conversions qu’un serveur OpenOffice est autorisé à effectuer. Au-delà de ce nombre, le serveur est redémarré.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxServerIdleSec<br /> </td> 
   <td> Durée maximum d’inactivité du serveur OpenOffice avant arrêt.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 7200<br /> </td> 
  </tr> 
  <tr> 
   <td> portRange<br /> </td> 
   <td> Intervalle de ports sur lesquels les serveurs OpenOffice sont démarrés en écoute.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> 8101-8110<br /> </td> 
  </tr> 
  <tr> 
   <td> url<br /> </td> 
   <td> URL du serveur de conversion de document.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> 'http://localhost:8080/nl/jsp/ooconv.jsp'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## proxyConfig {#proxyconfig}

Voici les différents paramètres du nœud **proxyConfig**. Il s’agit de la configuration des paramètres de proxy.

Pour plus d&#39;informations, voir la section [Paramétrage de la connexion au proxy](file-res-management.md).

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Valeur par défaut </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> enabled<br /> </td> 
   <td> Utiliser un serveur proxy.<br /> </td> 
   <td> Booléen<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> override<br /> </td> 
   <td> Exceptions : liste des adresses pour lesquelles ignorer les paramètres de proxy.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> 'localhost*' <br /> </td> 
  </tr> 
  <tr> 
   <td> useSingleProxy<br /> </td> 
   <td> Serveur proxy unique : utiliser la même configuration pour tous les types de proxy.<br /> </td> 
   <td> Booléen<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### HTTP Proxy / Secure proxy {#http-proxy---secure-proxy-}

Dans le nœud **proxyConfig > HTTP Proxy / Secure proxy**, configurez les paramètres suivants.

Pour plus d&#39;informations, voir la section [Paramétrage de la connexion au proxy](file-res-management.md).

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> address<br /> </td> 
   <td> Adresse du serveur proxy<br /> </td> 
   <td> Chaîne <br /> </td> 
  </tr> 
  <tr> 
   <td> login<br /> </td> 
   <td> Login pour la connexion au serveur proxy<br /> </td> 
   <td> Chaîne <br /> </td> 
  </tr> 
  <tr> 
   <td> password<br /> </td> 
   <td> Mot de passe pour la connexion au serveur proxy<br /> </td> 
   <td> Chaîne <br /> </td> 
  </tr> 
  <tr> 
   <td> port<br /> </td> 
   <td> Port du serveur proxy<br /> </td> 
   <td> Court<br /> </td> 
  </tr> 
 </tbody> 
</table>

## threadPool {#threadpool}

Voici les différents paramètres du nœud **threadPool**.

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Valeur par défaut </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxThreadCount<br /> </td> 
   <td> Nombre maximal de threads dans le pool. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## urlPermission {#urlpermission}

Voici les différents paramètres du nœud **urlPermission**. Il s’agit de la liste des URL auxquelles le code JavaScript peut accéder.

Liste de domaines et d’expressions régulières spécifiant si une URL rencontrée dans le code JavaScript peut ou non être utilisée par le serveur Adobe Campaign.

Si l’URL ne s’y trouve pas, l’action par défaut est réalisée, en fonction du mode spécifié par défaut.

Pour plus d&#39;informations, voir la section [Protection des connexions sortantes](../../installation/using/configuring-campaign-server.md#url-permissions).

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Valeur par défaut </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> action<br /> </td> 
   <td> Action par défaut si l'URL ne figure pas dans la liste autorisée (énumération). Les valeurs possibles sont 'ignore' (autoriser sans message d’avertissement, cela nécessite la désactivation de la protection), 'warn' (autoriser et émettre un message d’avertissement) et 'deny' (interdire l’accès à l’URL).<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> deny<br /> </td> 
  </tr> 
  <tr> 
   <td> debugTrace<br /> </td> 
   <td> Trace de débogage du mécanisme de sélection des URL : émet des messages supplémentaires au cours du processus de vérification des URL.<br /> </td> 
   <td> Booléen<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

## cusHeaders {#cusheaders}

Ce nœud permet d’ajouter des en-têtes spécifiques dans les requêtes effectuées lors du chargement d’un fichier depuis un serveur externe. Les réseaux de diffusion de contenu (CDN) peuvent demander un en-tête spécifique afin de faire confiance au demandeur ou à la demandeuse. Ces en-têtes peuvent être utilisés pour améliorer la confiance dans les requêtes Campaign, en particulier lors du téléchargement de documents personnalisés pour chaque destinataire à l’étape d’exécution de la diffusion. Un nombre élevé de requêtes de téléchargement de ressources peut être interprété comme une attaque DDos. dnsPattern vous permet de définir des valeurs et des noms d’en-tête spécifiques pour différents réseaux CDN en fonction de leur nom de domaine.

```
  <!-- List of custom headers added to request. 
         -->
    <cusHeaders>

    <!-- Pattern of DNS name or domain 
         value :  dnsPattern: All or part of the URL's domain to verify, * is a wild card Default:  -->
      <dnsPattern value="">

    <!-- Header Name and Value 
           headerName :  Header Name 
           headerValue :  Header Value -->
        <headerDef headerName="" headerValue=""/>

      </dnsPattern>

    </cusHeaders> 
```

### url {#url}

Pour chacune des URL, ajoutez un nœud **url** avec les paramètres suivants :

Pour plus d&#39;informations, voir la section [Protection des connexions sortantes](../../installation/using/configuring-campaign-server.md#url-permissions).

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> dnsSuffix<br /> </td> 
   <td> Nom de domaine, ou domaine parent, concerné par l’URL : tout ou partie du domaine de l’URL à vérifier, afin d’accélérer la vérification. L'URL n'est vérifiée par rapport à l'expression régulière que si son domaine contient dsnSuffix.<br /> </td> 
   <td> Chaîne <br /> </td> 
  </tr> 
  <tr> 
   <td> urlRegEx<br /> </td> 
   <td> Expression régulière pour affiner la validation des URL appartenant à ce domaine : expression régulière que l’URL doit vérifier, si elle correspond à dnsSuffix.<br /> </td> 
   <td> Chaîne <br /> </td> 
  </tr> 
 </tbody> 
</table>

Si un enregistrement correspond à **dnsSuffix**, mais pas à **urlRegEx**, l’enregistrement suivant est examiné.

Par exemple, pour autoriser l’accès à toutes les URL du domaine business.com, nous pouvons définir deux enregistrements :

dnsSuffix=&quot;business.com&quot; urlRegEx=&quot;http://.&#42;&quot;

et

dnsSuffix=&quot;business.com&quot; urlRegEx=&quot;https://.&#42;&quot;

Voici la configuration par défaut :

```
<url dnsSuffix="api.omniture.com" urlRegEx="https://api.omniture.com/genesis/i/3.1.*"   />
<url dnsSuffix="omniture.com" urlRegEx="https://api[1-5].omniture.com/genesis/i/3.1.*"  />
<url dnsSuffix="marketing.adobe.com"                     urlRegEx="https://.*"                                    />
<url dnsSuffix="fcm.googleapis.com"                      urlRegEx="https://fcm.googleapis.com/fcm/send.*"       />
<url dnsSuffix="graph.facebook.com"                      urlRegEx="https://.*"                                    />
<url dnsSuffix="api.line.me"                             urlRegEx="https://api.line.me/.*"                      />
<url dnsSuffix="api.twitter.com"                         urlRegEx="https://api.twitter.com/1.1.*"              />
<url dnsSuffix="adobeid-na1.services.adobe.com"          urlRegEx="https://.*"                                    />
<url dnsSuffix="adobeid-na1-stg1.services.adobe.com"     urlRegEx="https://.*"                                    />
<url dnsSuffix="localhost"                               urlRegEx="http://localhost:8080/nms/jsp/.*"              />
<url dnsSuffix="localhost"                               urlRegEx="http://localhost:8080/nl/jsp/.*"               />
<url dnsSuffix="localhost"                               urlRegEx="http://localhost:8080/xtk/jsp/.*"              />
```

## xtkJobs {#xtkjobs}

Voici les différents paramètres du nœud **xtkJobs**. Il s’agit de la configuration des traitements serveur.

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Valeur par défaut </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> purgeLogsPeriod<br /> </td> 
   <td> Période en millisecondes de rafraîchissement de l’état mémoire d’un traitement serveur.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
 </tbody> 
</table>

## archiving {#archiving}

Voici les différents paramètres du nœud **archiving**. Il s’agit de la configuration des opérations d’archivage en arrière-plan.

Pour plus d&#39;informations, voir la section [Activer l&#39;archivage des emails (on-premise)](../../installation/using/email-archiving.md#activating-email-archiving--on-premise-).

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Valeur par défaut </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> acquireLimit<br /> </td> 
   <td> Quantité d’EML à traiter en même temps<br /> </td> 
   <td> Long<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> archivingType<br /> </td> 
   <td> Stratégie d'archivage des messages envoyés (énumération). Les valeurs possibles sont '0' (pas d'archivage) et '1' (transfère l'archivage des messages envoyés vers un serveur SMTP).<br /> </td> 
   <td> Octet<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> args<br /> </td> 
   <td> Paramètres de démarrage<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Démarrage automatique<br /> </td> 
   <td> Booléen<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> compressBatchSize<br /> </td> 
   <td> Taille d’une archive compressée : nombre de fichiers max dans une archive compressée.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 10000<br /> </td> 
  </tr> 
  <tr> 
   <td> compressionFormat<br /> </td> 
   <td> Format de compression utilisé lors de l'archivage (énumération). Les valeurs possibles sont '0' (aucune compression) et '1' (compresse les messages envoyés au format zip).<br /> </td> 
   <td> Octet<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> expirationDelay<br /> </td> 
   <td> Délai avant l’archivage automatique des emails non traités : nombre de jours avant la mise en archive automatique des emails non traités.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> Identifiant du JavaScript à exécuter lors du démarrage du processus.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Alerte consommation mémoire : alerte pour le niveau de RAM en Mo consommée par un processus donné.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Avertissement consommation mémoire : avertissement pour le niveau de RAM en Mo consommée par un processus donné.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> pollDelay<br /> </td> 
   <td> Délai (en secondes) entre chaque événement de mise à jour.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Heure de la journée où le processus est redémarré automatiquement. Pour plus d'informations, consultez la section <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Redémarrage automatique des processus</a>.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeArchivesDelay<br /> </td> 
   <td> Nombre de jours avant la purge des emails non traités.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 7<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorité au début. Les modules de priorité basse sont démarrés en premier et arrêtés en dernier. Le module syslogd doit donc avoir la priorité 0.<br /> </td> 
   <td> Court<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpBccAddress<br /> </td> 
   <td> Destination de la cible d’archivage<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> smtpEnableTLS<br /> </td> 
   <td> Activer le support SMTPS : active la diffusion des emails en mode sécurisé (STARTTLS/SMTPS) si le serveur distant le supporte.<br /> </td> 
   <td> Booléen<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpNbConnection<br /> </td> 
   <td> Nombre de connexions au serveur SMTP d’archivage.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpRelayAddress<br /> </td> 
   <td> Liste séparée par des virgules des noms DNS ou adresses IP des relais SMTP à utiliser. <br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> smtpRelayPort<br /> </td> 
   <td> Port IP du serveur SMTP.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

## inMail {#inmail}

Voici les différents paramètres du nœud **inMail**. Il s’agit de la configuration du module de gestion des emails entrants.

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Valeur par défaut </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Paramètres de démarrage<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Démarrage automatique<br /> </td> 
   <td> Booléen<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> checkInstanceName<br /> </td> 
   <td> Vérifier le nom de l’instance : si vrai, le nom de l’instance Adobe Campaign contenu dans les en-têtes Message-ID doit être le même que celui de l’instance courante. <br /> </td> 
   <td> Booléen<br /> </td> 
   <td> vrai<br /> </td> 
  </tr> 
  <tr> 
   <td> defaultForwardAddress<br /> </td> 
   <td> Adresse de transfert : adresse par défaut de transfert des emails non traités par une règle. <br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> errorForwardAddress<br /> </td> 
   <td> Adresse pour les erreurs : adresse par défaut de transfert des emails invalides (mauvais encoding MIME). <br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> ignoreSize<br /> </td> 
   <td> Ignorer la taille du message : permet d’ignorer la taille d’un message renvoyée par les serveurs POP3. Dans ce cas, le module attend un caractère '.' à la fin des messages. <br /> </td> 
   <td> Booléen<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> inMailPeriodSec<br /> </td> 
   <td> Période de lecture des messages : périodicité d’interrogation des files de messages.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> Identifiant du JavaScript à exécuter lors du démarrage du processus.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxBroadLog<br /> </td> 
   <td> Nombre maximum de logs à mettre à jour : définit le nombre maximum de messages de logs de diffusion conservés en mémoire avant la mise à jour de la base de données.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 20<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMsgPerSession<br /> </td> 
   <td> Nombre maximal de messages à lire au cours d’une session POP3.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 200<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Alerte consommation mémoire : alerte pour le niveau de RAM en Mo consommée par un processus donné.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Avertissement consommation mémoire : avertissement pour le niveau de RAM en Mo consommée par un processus donné.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSessionTTLSec<br /> </td> 
   <td> Durée de la session : durée maximale de la session de traitement des messages.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> popMailPeriodSec<br /> </td> 
   <td> Période d’interrogation des comptes POP3.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> popQueueSize<br /> </td> 
   <td> Taille de la file de messages lus<br /> </td> 
   <td> Long<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> popTimeoutSec<br /> </td> 
   <td> Timeout des communications avec le serveur POP3. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Heure de la journée où le processus est redémarré automatiquement. Pour plus d'informations, consultez la section <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Redémarrage automatique des processus</a>.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> reloadPeriodSec<br /> </td> 
   <td> Périodicité du chargement depuis la base de données des comptes à interroger.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorité au début. Les modules de priorité basse sont démarrés en premier et arrêtés en dernier. Le module syslogd doit donc avoir la priorité 0.<br /> </td> 
   <td> Court<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

### msgDump {#msgdump}

Dans le nœud **inMail > msgDump**, configurez les paramètres suivants. Il s’agit de la configuration de la sauvegarde des messages traités.

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Valeur par défaut </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> dump<br /> </td> 
   <td> Sauvegarder tous les messages entrants au format texte. <br /> </td> 
   <td> Booléen<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> msgPath<br /> </td> 
   <td> Chemin de sauvegarde des messages.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> '/tmp/inMail'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## interactiond {#interactiond}

Voici les différents paramètres du nœud **interactiond**. Il s’agit de la configuration du démon d’écriture des événements Interaction entrants.

Pour plus d&#39;informations, voir la section [Interaction - Mémoire tampon](../../installation/using/interaction-data-buffer.md).

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Valeur par défaut </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Paramètres de démarrage<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Démarrage automatique<br /> </td> 
   <td> Booléen<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> callDataSize<br /> </td> 
   <td> Max. Nombre maximal de caractères stockés en mémoire partagée pour les données d'appel.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> Identifiant du JavaScript à exécuter lors du démarrage du processus<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Alerte consommation mémoire : alerte pour le niveau de RAM en Mo consommée par un processus donné.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Avertissement consommation mémoire : avertissement pour le niveau de RAM en Mo consommée par un processus donné.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSharedEntries<br /> </td> 
   <td> Max. Nombre maximal d'événements stockés en mémoire partagée.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 25000<br /> </td> 
  </tr> 
  <tr> 
   <td> nextOffersSize<br /> </td> 
   <td> Nombre maximal d’offres éligibles classées juste après les propositions, à stocker pour statistiques.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Heure de la journée où le processus est redémarré automatiquement. Pour plus d'informations, consultez la section <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Redémarrage automatique des processus</a>.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorité au début. Les modules de priorité basse sont démarrés en premier et arrêtés en dernier. Le module syslogd doit donc avoir la priorité 0.<br /> </td> 
   <td> Court<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> statsPeriod<br /> </td> 
   <td> Durée d’agrégation en secondes pour les statistiques de temps de réponse. 0 signifie que le stockage des statistiques a été désactivé.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> targetKeySize<br /> </td> 
   <td> Max. Nombre maximal de caractères stockés en mémoire partagée pour l'identification d'un individu.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 16<br /> </td> 
  </tr> 
 </tbody> 
</table>

## mta {#mta}

Voici les différents paramètres du nœud **mta**. Il s’agit du paramétrage des agents de diffusion.

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Valeur par défaut </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Paramètres de démarrage<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> '-tracefilter:nlmta' <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Démarrage automatique<br /> </td> 
   <td> Booléen<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> dataLogPath<br /> </td> 
   <td> Chemin de sauvegarde des emails envoyés : si pas vide, chemin où seront enregistrés tous les fichiers sources des emails envoyés. <br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> debugPath<br /> </td> 
   <td> Répertoire de dump : si non vide, copiez les enveloppes MIME des messages envoyés dans ce répertoire. Utilisé pour le diagnostic des problèmes. <br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> dnsRequestLogDelayMs<br /> </td> 
   <td> Délai des logs de requête DNS : délai en millisecondes pour afficher les logs.<br /> </td> 
   <td> Long<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> errorPeriodSec<br /> </td> 
   <td> Périodicité de la remontée des erreurs : durée exprimée en secondes définissant la périodicité de la remontée des erreurs dans la base de données. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> Identifiant du JavaScript à exécuter lors du démarrage du processus.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> logEmailErrors<br /> </td> 
   <td> Générer des statistiques d’erreur et les enregistrer dans la base de données.<br /> </td> 
   <td> Booléen<br /> </td> 
   <td> vrai<br /> </td> 
  </tr> 
  <tr> 
   <td> logLevel<br /> </td> 
   <td> Afficher le niveau des messages du journal. Niveau de gravité des logs écrits dans la base de données. Les messages de logs générés par le MTA ne sont pas toujours écrits en base. Avec ce paramètre, vous pouvez définir le niveau à partir duquel vous considérez qu'un message doit être écrit dans la base de données. Si vous définissez le niveau 2, les messages des niveaux 1 et 0 sont également écrits, alors que si vous définissez le niveau 1, seuls les messages des niveaux 1 et 0 sont écrits. Les valeurs possibles sont : 0 (erreurs), 1 (avertissement), 2 (informations)<br /> </td> 
   <td> Long<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMemoryMb<br /> </td> 
   <td> Taille maximum en méga-octets de la mémoire qu’un processus mta peut utiliser. Au-delà de cette limite, le processus est relancé afin que la mémoire qu’il utilise soit libérée sur le système.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1024<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Alerte consommation mémoire : alerte pour le niveau de RAM en Mo consommée par un processus donné.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Avertissement consommation mémoire : avertissement pour le niveau de RAM en Mo consommée par un processus donné.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> minConnectionsToLog<br /> </td> 
   <td> Seuil de connexions à prendre en compte. Les statistiques d’erreur ne sont pas générées pour un chemin donné si le nombre total de connexions pour la période spécifiée par errorPeriodSec est strictement inférieur au seuil.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> minErrorsToLog<br /> </td> 
   <td> Seuil d’erreurs à prendre en compte : les statistiques d’erreurs ne seront pas générées pour un chemin donné si le nombre total d’erreurs depuis la durée spécifiée par errorPeriodSec est strictement inférieur à ce seuil.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> minMessagesToLog<br /> </td> 
   <td> Seuil de messages à prendre en compte. Les statistiques d’erreur ne sont pas générées pour un chemin donné si le nombre total de messages envoyés pour la période spécifiée par errorPeriodSec est strictement inférieur au seuil.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> Relais de notification : HostName:Port permettant le relais des notifications.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Heure de la journée où le processus est redémarré automatiquement. Pour plus d'informations, consultez la section <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Redémarrage automatique des processus</a>.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeDataLogDelay<br /> </td> 
   <td> Délai avant la suppression des e-mails archivés : nombre de jours avant la purge des e-mails archivés dans le répertoire spécifié dans dataLogPath.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 15<br /> </td> 
  </tr> 
  <tr> 
   <td> retryLostMessages<br /> </td> 
   <td> Réessayer les messages perdus : les fragments de diffusions seront repris si le processus enfant est mort.<br />
 </td> 
   <td> Booléen<br /> </td> 
   <td> vrai<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorité au début. Les modules de priorité basse sont démarrés en premier et arrêtés en dernier. Le module syslogd doit donc avoir la priorité 0.<br /> </td> 
   <td> Court<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> signEmailLinks<br /> </td> 
   <td> Activez le mécanisme de signature. La sécurité du tracking des liens dans les emails sera ainsi améliorée.<br /> </td> 
   <td> Booléen<br /> </td> 
   <td> vrai<br /> </td> 
  </tr>
  <tr> 
   <td> statServerAddress<br /> </td> 
   <td> Adresse du serveur des statistiques de diffusion, sous la forme
    &lt;dns or ip&gt; 
      <code>[</code> : 
     &lt;port&gt; 
       <code>]</code>. Voir la section 
      <a href="../../installation/using/email-deliverability.md#coordinates-of-the-statistics-server" target="_blank">Coordonnées du serveur de statistiques</a>. 
      <br /> 
     </td> 
   <td> Chaîne <br /> </td> 
   <td> Si non défini, le port par défaut est 7777.<br /> </td> 
  </tr> 
  <tr> 
   <td> statServerTLSSupport<br /> </td> 
   <td> Activer le TLS par domaine : active le TLS configurable par MX (nécessite un serveur de statistiques à jour).<br /> </td> 
   <td> Booléen<br /> </td> 
   <td> vrai <br /> </td> 
  </tr> 
  <!--tr> 
   <td> statServerVersion<br /> </td> 
   <td> Protocol version used: communication protocol version (1 for a v5.11 and 6.0.2 server, 2 for a v6.1 server).<br /> </td> 
   <td> String<br /> </td> 
   <td> If undefined, the latest version is used. <br /> </td> 
  </tr--> 
  <tr> 
   <td> useMomentum<br /> </td> 
   <td> Si la valeur est "true", votre instance utilise le <a href="../../delivery/using/sending-with-enhanced-mta.md" target="_blank">MTA amélioré</a>.<br /> </td> 
   <td> Booléen<br /> </td> 
   <td> <br /> </td>b 
  </tr>
  <tr> 
   <td> verifyMode<br /> </td> 
   <td> Mode de vérification : active le mode vérification (pas d’envoi physique des messages ; utilisé en simulation et tests).<br /> </td> 
   <td> Booléen<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> workingPath<br /> </td> 
   <td> Répertoire de travail : emplacement des fichiers temporaires utilisés par le MTA pour communiquer avec ses processus enfants.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/mta/' <br /> </td> 
  </tr> 
  <tr> 
   <td> xMailer<br /> </td> 
   <td> Champ X-Mailer : valeur du champ d’en-tête SMTP 'X-Mailer'.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> 'nlserver, Build $(PRODUCT_VERSION)'<br /> </td> 
  </tr>  
 </tbody> 
</table>

### cache {#cache}

Dans le nœud **cache**, configurez les paramètres suivants. Il s’agit de la configuration du cache fichier local.

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Valeur par défaut </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxPeriodSec<br /> </td> 
   <td> Recyclé après : période, exprimée en secondes, au-delà de laquelle le fichier est automatiquement supprimé du cache pour libérer de l’espace.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 244800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSizeOnDiskMb<br /> </td> 
   <td> Taille maximum du cache (Mo).<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1024<br /> </td> 
  </tr> 
  <tr> 
   <td> purgePeriodSec<br /> </td> 
   <td> Périodicité de la purge : durée exprimée en secondes définissant la périodicité de réveil du mécanisme de purge du cache.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 3600<br /> </td> 
  </tr> 
 </tbody> 
</table>

### relay {#relay}

Dans le nœud **mta > relay**, configurez les paramètres suivants. Il s’agit de la configuration pour l’utilisation d’un serveur de mail pour assurer la diffusion des messages.

La liste sera gérée de la même manière qu’une liste de MX renvoyée par une requête DNS MX. En règle générale, le premier MX est utilisé tant qu’il est disponible, puis le suivant est utilisé, et ainsi de suite.

Pour plus d&#39;informations, consultez la section [Relais SMTP](../../installation/using/configuring-campaign-server.md#smtp-relay).

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Valeur par défaut </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> address<br /> </td> 
   <td> Liste séparée par des virgules des noms DNS ou adresses IP des relais SMTP à utiliser. <br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> port<br /> </td> 
   <td> Port IP du serveur SMTP.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

### master {#master}

Dans le nœud **mta > master**, configurez les paramètres suivants. Il s’agit de la configuration du serveur principal.

Pour plus d’informations, consultez cette [section](../../installation/using/configuring-campaign-server.md#mta-child-processes).

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Valeur par défaut </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> dataBasePoolPeriodSec<br /> </td> 
   <td> Fréquence d’interrogation des bases de données des tâches à diffuser. Cette valeur indique la fréquence d’interrogation de la base de données (en secondes). Pour obtenir la liste des traitements en attente de diffusion, le MTA sonde régulièrement la base de données. Lorsqu’aucune tâche n’est en attente, la période d’interrogation est définie par cette valeur. Sinon, si une tâche a été transférée à un serveur fils, cette durée d’interrogation est automatiquement réduite à une seconde afin qu’une nouvelle tâche puisse être traitée dès que possible, c’est-à-dire dès qu’un serveur fils est à nouveau disponible. Cela ne signifie pas que la requête de base de données sera effectuée toutes les secondes jusqu’à ce qu’un serveur enfant soit à nouveau disponible. En fait, un accès à la base de données n’est possible que lorsqu’au moins un serveur enfant est disponible.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> dataBaseRetryDelaySec<br /> </td> 
   <td> Délai d’attente après un échec de connexion à la base de données. Un échec de connexion à la base de données est généralement dû au serveur de base de données lui-même. Le serveur peut également être arrêté à des fins de maintenance, par exemple. Le paramètre DataBaseRetryDelay définit la durée entre deux tentatives de connexion en cas d’échec de la connexion à la base de données.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> domainKeysReloadPeriodSec<br /> </td> 
   <td> Délai de validité du cache des clés privées (DomainKeys). Les clés privées utilisées pour signer des emails suite à la recommandation DomainKeys (http://antispam.yahoo.com/domainkeys) sont stockées en tant qu’options dans la base de données. Le paramètre domainKeysReloadPeriodSec définit le nombre de secondes pendant lesquelles le MTA peut conserver ces clés dans un cache. Après ce délai, toutes les clés doivent être rechargées à partir de la base de données.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSpareServers<br /> </td> 
   <td> Nombre maximum de serveurs enfants. Représente le nombre maximum de serveurs en fonctionnement. Il n'est pas souhaitable de fixer un nombre trop élevé sans nécessité, car cela consomme inutilement de la mémoire. Vous pouvez vérifier si ce nombre n'est pas trop élevé en étudiant la mémoire consommée sur votre machine lorsqu'une diffusion est en cours. Celle-ci ne doit jamais excéder de plus d'un tiers la mémoire physiquement disponible sur votre machine, car cela signifie que votre swap est mis à contribution. Pour plus d'informations, consultez la section <a href="../../installation/using/configuring-campaign-server.md#mta-child-processes" target="_blank">Processus MTA enfant</a>.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> minSpareServers<br /> </td> 
   <td> Nombre minimum de serveurs enfants. Le MTA tente de conserver au moins ce nombre de serveurs en cours d'exécution. S’il y en a moins, il redémarre de nouveaux serveurs toutes les secondes jusqu’à ce que cette valeur soit atteinte.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> startSpareServers<br /> </td> 
   <td> Nombre de serveurs enfants au démarrage. Le nombre de serveurs enfants est surveillé dynamiquement ; lorsque le MTA démarre, il crée autant de serveurs enfants que l’indique cette valeur. En règle générale, les serveurs fils ne peuvent pas être démarrés plus rapidement qu’un serveur par seconde pour économiser les ressources de l’hôte. Cependant, lorsque le MTA démarre, cette limitation est annulée afin que les serveurs fils soient disponibles dès que possible.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
 </tbody> 
</table>

### child {#child}

Dans le nœud **mta > child**, configurez les paramètres suivants. Il s’agit de la configuration des serveurs enfants.

Pour plus d&#39;informations, voir la section [Optimisation de l&#39;envoi d&#39;emails](../../installation/using/email-deliverability.md#email-sending-optimization).

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Valeur par défaut </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> extraArgs<br /> </td> 
   <td> Arguments ligne de commande optionnels <br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> idleChildTimeoutSec<br /> </td> 
   <td> Délai d’expiration jusqu’à ce que les serveurs enfants inactifs soient arrêtés. Si le temps d’inactivité d’un serveur fils est supérieur à ce paramètre, il se termine automatiquement pour libérer les ressources de l’hôte.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> maxAgeSec<br /> </td> 
   <td> Durée maximale de rétention des messages. Si un message préparé n’a pas pu être envoyé en raison du ralentissement ou de l’impossibilité de se connecter au MTA cible, le message est abandonné et sera traité lors de la prochaine reprise.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxGCMConnectPerChild<br /> </td> 
   <td> Limite maximale du nombre de requêtes HTTP parallèles sur le serveur FCM initiées par chaque serveur enfant.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 8<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMsgPerChild<br /> </td> 
   <td> Nombre maximum de messages par serveur fils. Chaque enfant MTA traite ce nombre de messages et meurt. Il est important de spécifier un nombre tel que les fuites de mémoire ou de ressource dans le MTA sont inoffensives (généralement quelques milliers). Même s'il n'existe aucune fuite de mémoire connue dans le code MTA, les moteurs JavaScript et XSL intégrés ne sont pas entièrement fiables.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5000000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxWaitingMessages<br /> </td> 
   <td> Messages en attente : nombre maximum de messages préparés en mémoire en attente de diffusion. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 2000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxWorkingSetMb<br /> </td> 
   <td> Taille maximum en méga-octets de la mémoire qu’un processus enfant peut utiliser. Au-delà de cette limite, le processus est arrêté afin que la mémoire qu’il utilise soit libérée sur le système. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 128<br /> </td> 
  </tr> 
  <tr> 
   <td> soapConnectorTimeoutSec<br /> </td> 
   <td> Timeout (en secondes) après lequel une connexion SOAP pour un connecteur de diffusion est abandonnée.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> startWithFirstMX<br /> </td> 
   <td> Toujours commencer avec le MX le plus prioritaire.<br /> </td> 
   <td> Booléen<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> timeToLive<br /> </td> 
   <td> Nombre maximum de tentatives consécutives par reprise.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 48<br /> </td> 
  </tr> 
 </tbody> 
</table>

Dans le nœud **mta > child > smtp**, configurez les paramètres suivants. Il s’agit de la configuration des sessions SMTP.

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Valeur par défaut </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> enableTLS<br /> </td> 
   <td> Active la diffusion des emails en mode sécurisé (STARTTLS/SMTPS) si le serveur distant le supporte.<br /> </td> 
   <td> Booléen<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> idleSessionTimeoutSec<br /> </td> 
   <td> Délai de session inactif. Ce paramètre n’est utilisé que si la session est réutilisée pour transmettre plusieurs messages à un domaine donné. Une fois que le MTA a terminé la transmission du message, la session SMTP qu'il a utilisée n'est pas systématiquement fermée. Si un message est prêt à être envoyé pour ce même domaine, la même session SMTP sera réutilisée et c’est pourquoi la session n’est pas fermée automatiquement. Le paramètre IdleSessionTimeout permet de définir la durée pendant laquelle une session SMTP peut rester active en attendant un autre message. Une fois la durée écoulée, la session est automatiquement fermée.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> initialDelaySec<br /> </td> 
   <td> Délai initial avant de retenter la connexion. Ce délai est doublé chaque fois que la connexion échoue.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSessionsPerChild<br /> </td> 
   <td> Nombre maximal de sessions SMTP par serveur fils. Pour diffuser un message, le MTA initialise une connexion SMTP avec le MTA du destinataire. Le nombre maximal de sessions SMTP actives et simultanées pour un serveur fils donné est limité par cette valeur. Si vous multipliez cette valeur par maxSpareServers, vous obtenez le nombre maximum de messages qui peuvent être traités simultanément par un serveur fils donné.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
 </tbody> 
</table>

Dans le nœud **mta > child > smtp > IPAffinity**, configurez les paramètres suivants. Il s’agit de la configuration de la gestion des affinités avec les adresses IP pour une meilleure maîtrise du trafic SMTP sortant.

Pour plus d&#39;informations, voir les sections [Liste des adresses IP à utiliser](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use) et [Gérer le trafic SMTP sortant avec les affinités](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities).

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> localDomain<br /> </td> 
   <td> Nom de domaine : nom de domaine local associé à l’adresse IP. Utilisé lors de l’émission d’une commande SMTP HELO.<br /> </td> 
   <td> Chaîne <br /> </td> 
  </tr> 
  <tr> 
   <td> name<br /> </td> 
   <td> Nom logique : noms associés à l’affinité par les utilisateurs. Les noms sont séparés par des points-virgules ;<br /> </td> 
   <td> Chaîne <br /> </td> 
  </tr> 
 </tbody> 
</table>

Dans le nœud **mta > child > smtp > IP**, configurez les paramètres suivants.

Pour plus d&#39;informations, voir la section [Liste des adresses IP à utiliser](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use).

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> address<br /> </td> 
   <td> Adresse physique associée. Par exemple : '192.168.0.1'<br /> </td> 
   <td> Chaîne <br /> </td> 
  </tr> 
  <tr> 
   <td> publicId<br /> </td> 
   <td> Identifiant de l’adresse publique associée. Utilisé comme clé pour le serveur de statistiques. Doit être numérique. Voir <a href="../../installation/using/email-deliverability.md#managing-ip-addresses">section</a>.<br /> </td> 
   <td> Long<br /> </td> 
  </tr> 
  <tr> 
   <td> poids<br /> </td> 
   <td> Détermine la fréquence d’utilisation de cette IP par rapport aux autres IPs (plus le poids est élevé plus la fréquence est élevée).<br /> </td> 
   <td> Long<br /> </td> 
  </tr> 
  <tr> 
   <td> includeDomains<br /> </td> 
   <td> Masques des domaines à inclure séparés par une virgule.<br /> </td> 
   <td> Chaîne <br /> </td> 
  </tr> 
  <tr> 
   <td> excludeDomains<br /> </td> 
   <td> Masques des domaines à exclure séparés par une virgule.<br /> </td> 
   <td> Chaîne <br /> </td> 
  </tr> 
  <tr> 
   <td> heloHost<br /> </td> 
   <td> Nom de l’ordinateur associé à l’adresse IP. Utilisé lors de l’émission d’une commande SMTP HELO.<br /> </td> 
   <td> Chaîne <br /> </td> 
  </tr> 
 </tbody> 
</table>

## nmac {#nmac}

Voici les différents paramètres du nœud **nmac**. Il s’agit de la configuration des diffusions de notifications push.

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Valeur par défaut </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> useHTTPProxy<br /> </td> 
   <td> Utiliser le proxy HTTP défini dans shared/proxyHTTP. <br /> </td> 
   <td> Booléen<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### relay {#relay-1}

Voici les différents paramètres du nœud **nmac > relay**. Il s’agit de la configuration d’un relais pour diffuser des messages (connecteur ios http2).

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Valeur par défaut </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> address<br /> </td> 
   <td> Adresse ou nom DNS du relais à utiliser. <br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> port<br /> </td> 
   <td> Port du relais.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 443<br /> </td> 
  </tr> 
  <tr> 
   <td> trustedCertsChain<br /> </td> 
   <td> Chaîne de certificats (fichier PEM). Utile lors de l’utilisation d’un faux serveur.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## pipelined {#pipelined}

Voici les différents paramètres du nœud **pipelined**. Il s’agit de la configuration du module de traitement des événements des Pipeline Services.

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Valeur par défaut </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> appName<br /> </td> 
   <td> Nom de l’application généré dans le Developer Connection au moment d’enregistrer la clé publique. <br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> args<br /> </td> 
   <td> Paramètres de démarrage<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authGatewayEndpoint<br /> </td> 
   <td> URL pour obtenir un 'gateway token'.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> 'https://api.omniture.com' <br /> </td> 
  </tr> 
  <tr> 
   <td> authPrivateKey<br /> </td> 
   <td> Clé privée pour obtenir les jetons (chiffrée en AES avec l’option XtkKey).<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Démarrage automatique <br /> </td> 
   <td> Booléen<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> disableAuth<br /> </td> 
   <td> Désactiver l’authentification : se connecter aux Pipeline Services sans authentification. <br /> </td> 
   <td> Booléen<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> discoverPipelineEndpoint<br /> </td> 
   <td> URL pour découvrir l’URL des Pipeline Services.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> 'https://producer-pipeline-pnw.adobe.net'<br /> </td> 
  </tr> 
  <tr> 
   <td> dumpStatePeriodSec<br /> </td> 
   <td> Période de sauvegarde de l’état : fréquence à laquelle les informations internes du processus sont enregistrées dans un fichier. Inactif si 0. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> forcedPipelineEndpoint<br /> </td> 
   <td> URL d’écoute : forcer l’URL d’écoute des Pipeline Services. <br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> Identifiant du JavaScript à exécuter lors du démarrage du processus.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Alerte consommation mémoire : alerte pour le niveau de RAM en Mo consommée par un processus donné.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Avertissement consommation mémoire : avertissement pour le niveau de RAM en Mo consommée par un processus donné.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> monitorServerPort<br /> </td> 
   <td> Port du serveur d’état : port du serveur HTTP permettant d’interroger l’état du processus. Inactif si 0.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 7781<br /> </td> 
  </tr> 
  <tr> 
   <td> pointerFlushMessageCount<br /> </td> 
   <td> Le pointeur sera stocké en base à chaque fois que ce nombre de messages est traité.<br /> </td> 
   <td> <br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> pointerFlushPeriodSec<br /> </td> 
   <td> Délai avant stockage du pointeur : le pointeur sera stocké en base au moins une fois pendant cette période (utile en cas de faible activité).<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Heure de la journée où le processus est redémarré automatiquement. Pour plus d'informations, consultez la section <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Redémarrage automatique des processus</a>.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> processingJSThreads<br /> </td> 
   <td> Nombre de threads pour le traitement des événements avec un connecteur JavaScript personnalisé.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> processingThreads<br /> </td> 
   <td> Nombre de threads pour le traitement des événements.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> retryPeriodSec<br /> </td> 
   <td> Délai entre traitements dans le cas d’un échec.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> retryValiditySec<br /> </td> 
   <td> Abandonner au bout de cette période : abandonner l’événement si le traitement est toujours en échec après cette période.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorité au début. Les modules de priorité basse sont démarrés en premier et arrêtés en dernier. Le module syslogd doit donc avoir la priorité 0.<br /> </td> 
   <td> Court<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## repair {#repair}

Voici les différents paramètres du nœud **repair**. Il s’agit de la configuration du module de réparation de la base de données.

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Valeur par défaut </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> repairActionDelayMin<br /> </td> 
   <td> Réparation des actions de diffusion : délai en minutes au-delà duquel les actions de diffusion peuvent être traitées par le module de réparation. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
 </tbody> 
</table>

## securityZone {#securityzone}

Voici les différents paramètres du nœud **securityZone**.

Pour plus d’informations, voir la section [Définition des zones de sécurité](../../installation/using/security-zones.md).

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Valeur par défaut </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> allowDebug<br /> </td> 
   <td> Autoriser le mode debug dans les applications Web.<br /> </td> 
   <td> Booléen<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowEmptyPassword<br /> </td> 
   <td> Autoriser l’utilisateur à ne pas avoir de mot de passe.<br /> </td> 
   <td> Booléen<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowHTTP<br /> </td> 
   <td> Autoriser l’utilisation de HTTP pour la connexion des opérateurs.<br /> </td> 
   <td> Booléen<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowSQLInjection<br /> </td> 
   <td> Autoriser l’utilisation de SQLDATA dans les expressions.<br /> </td> 
   <td> Booléen<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowUserPassword<br /> </td> 
   <td> Autoriser des jetons de session de la forme user/password.<br /> </td> 
   <td> Booléen<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> label<br /> </td> 
   <td> Libellé<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> NewLabel()<br /> </td> 
  </tr> 
  <tr> 
   <td> name<br /> </td> 
   <td> Nom interne<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> NewName() <br /> </td> 
  </tr> 
  <tr> 
   <td> sessionTokenOnly<br /> </td> 
   <td> Ne pas utiliser le jeton de sécurité.<br /> </td> 
   <td> Booléen<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> showErrors<br /> </td> 
   <td> Afficher le détail des erreurs.<br /> </td> 
   <td> Booléen<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

Voici la configuration par défaut :

```
<securityZone allowDebug="false" allowHTTP="false" allowSQLInjection="false" label="Public Network" name="public">
  <subNetwork name="all" label="All addresses" mask="*" proxy="127.0.0.1, ::1"/>

  <securityZone allowDebug="true" allowHTTP="false" allowSQLInjection="false" label="Private Network (VPN)"
                name="vpn" showErrors="true">

    <securityZone allowDebug="true" allowEmptyPassword="false" allowHTTP="true" allowUserPassword="false"
                  allowSQLInjection="false" label="Private Network (LAN)" name="lan" sessionTokenOnly="true"
                  showErrors="true">
      <subNetwork name="lan1" label="Lan 1" mask="192.168.0.0/16" proxy="127.0.0.1, ::1"/>
      <subNetwork name="lan2" label="Lan 2" mask="172.16.0.0/12" proxy="127.0.0.1, ::1"/>
      <subNetwork name="lan3" label="Lan 3" mask="10.0.0.0/8" proxy="127.0.0.1, ::1"/>
      <subNetwork name="localhost" label="Localhost" mask="127.0.0.0/8" proxy="127.0.0.1, ::1"/>
      <subNetwork name="lan6"  label="Lan (IPv6)" mask="fc00::/7" proxy="127.0.0.1, ::1"/>
      <subNetwork name="lan6b" label="Lan (IPv6)" mask="fe80::/10" proxy="127.0.0.1, ::1"/>
      <subNetwork name="localhost6" label="Localhost (IPv6)" mask="::1/128" proxy="127.0.0.1, ::1"/>
    </securityZone>

  </securityZone>
</securityZone>
```

### subNetwork {#subnetwork}

Voici les différents paramètres du nœud **securityZone > subNetwork**.

Pour plus d’informations, voir la section [Définition des zones de sécurité](../../installation/using/security-zones.md).

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Valeur par défaut </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> label<br /> </td> 
   <td> Libellé<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> NewLabel()<br /> </td> 
  </tr> 
  <tr> 
   <td> mask<br /> </td> 
   <td> Masque ou adresse<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> name<br /> </td> 
   <td> Nom interne<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> NewName() <br /> </td> 
  </tr> 
  <tr> 
   <td> proxy<br /> </td> 
   <td> Masque ou adresse du (reverse) proxy utilisé par ce sous-réseau pour accéder à l'instance. Dans ce cas, l’en-tête "X-Forwarded-For" sera testé à la place de ce proxy.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> 127.0.0.1 <br /> </td> 
  </tr> 
 </tbody> 
</table>

## sms {#sms}

Voici les différents paramètres du nœud **sms**. Il s’agit de la configuration du module de gestion des SMS entrants.

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Valeur par défaut </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Paramètres de démarrage<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Démarrage automatique<br /> </td> 
   <td> Booléen<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> dataRetentionDays<br /> </td> 
   <td> Durée maximale en jours de rétention des fichiers de travail du connecteur SMPP.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> dataSizeMo<br /> </td> 
   <td> Taille maximale en Mo des fichiers de travail SMPP.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 512<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> Identifiant du JavaScript à exécuter lors du démarrage du processus.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> keepAlivePeriod<br /> </td> 
   <td> Périodicité de la trame de continuité de session : max. période en secondes entre deux images pour signaler que la session de réception est toujours activée.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Alerte consommation mémoire : alerte pour le niveau de RAM en Mo consommée par un processus donné.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Avertissement consommation mémoire : avertissement pour le niveau de RAM en Mo consommée par un processus donné.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> pollPeriod<br /> </td> 
   <td> Périodicité de recherche : périodicité d’interrogation des comptes SMS.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Heure de la journée où le processus est redémarré automatiquement. Pour plus d'informations, consultez la section <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Redémarrage automatique des processus</a>.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> reloadPeriod<br /> </td> 
   <td> Périodicité de chargement des comptes : périodicité du chargement depuis la base de données des comptes à interroger.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorité au début. Les modules de priorité basse sont démarrés en premier et arrêtés en dernier. Le module syslogd doit donc avoir la priorité 0.<br /> </td> 
   <td> Court<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> srReadDelay<br /> </td> 
   <td> Durée en secondes de retard pour le traitement des SR : ne sont ramenés que les SR dont la date de récupération est au moins antérieure à l’instant actuel moins une durée en secondes donnée par srReadDelay. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Timeout des communications avec la passerelle SMS.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
 </tbody> 
</table>

### netsize {#netsize}

Voici les différents paramètres du nœud **sms > netsize.**

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Valeur par défaut </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> netsizeConnectionTimeout<br /> </td> 
   <td> Timeout en secondes lors de l’établissement d’une connexion avec Netsize.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
 </tbody> 
</table>

## stat {#stat}

Voici les différents paramètres du nœud **stat**. Il s’agit de la configuration du module de statistiques des MTA.

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Valeur par défaut </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Paramètres de démarrage<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Démarrage automatique<br /> </td> 
   <td> Booléen<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> Identifiant du JavaScript à exécuter lors du démarrage du processus.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Alerte consommation mémoire : alerte pour le niveau de RAM en Mo consommée par un processus donné.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Avertissement consommation mémoire : avertissement pour le niveau de RAM en Mo consommée par un processus donné.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> port<br /> </td> 
   <td> Port d’écoute du serveur. Voir <a href="../../installation/using/email-deliverability.md#definition-of-the-server-port">section</a>.<br /> </td> 
   <td> Court<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Heure de la journée où le processus est redémarré automatiquement. Pour plus d'informations, consultez la section <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Redémarrage automatique des processus</a>.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorité au début. Les modules de priorité basse sont démarrés en premier et arrêtés en dernier. Le module syslogd doit donc avoir la priorité 0.<br /> </td> 
   <td> Court<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## syslogd {#syslogd}

Voici les différents paramètres du nœud **syslogd**. Il s’agit de la configuration du module de gestion des logs.

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Valeur par défaut </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Paramètres de démarrage<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Démarrage automatique<br /> </td> 
   <td> Booléen<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> Identifiant du JavaScript à exécuter lors du démarrage du processus.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxFileSizeMb<br /> </td> 
   <td> Taille maximum en Mo d’un fichier de log. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> maxNumberOfLoginsFiles<br /> </td> 
   <td> Nombre maximal de fichiers logins.log à conserver. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 365<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Alerte consommation mémoire : alerte pour le niveau de RAM en Mo consommée par un processus donné.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Avertissement consommation mémoire : avertissement pour le niveau de RAM en Mo consommée par un processus donné.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Heure de la journée où le processus est redémarré automatiquement. Pour plus d'informations, consultez la section <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Redémarrage automatique des processus</a>.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorité au début. Les modules de priorité basse sont démarrés en premier et arrêtés en dernier. Le module syslogd doit donc avoir la priorité 0.<br /> </td> 
   <td> Court<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## tracking {#tracking}

Voici les différents paramètres du nœud **tracking**. Il s’agit de la configuration du serveur de tracking.

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Valeur par défaut </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Paramètres de démarrage<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Démarrage automatique<br /> </td> 
   <td> Booléen<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> blockRedirectForUnsignedTrackingLink<br /> </td> 
   <td> Désactivez les URL incorrectement renseignées, générées à partir des builds précédents.<br /> </td> 
   <td> Booléen<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> consolidationPeriodSec<br /> </td> 
   <td> Période de consolidation<br /> </td> 
   <td> Long<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> dedupOpenPeriodMin<br /> </td> 
   <td> Déduplication des ouvertures : déduplication des logs d’ouverture pour limiter les effets liés aux clients mail type Outlook dotés d’un aperçu.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> errorIgnorePercent<br /> </td> 
   <td> Ignorer jusqu’à X % des erreurs : limite la mise à jour des indicateurs de tracking si le pourcentage de journal de tracking non pris en compte n’atteint pas cette valeur. <br /> </td> 
   <td> Octet<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> errorIgnorePeriod<br /> </td> 
   <td> Mise à jour des qualifications d’erreurs : durée maximum de désynchronisation des qualifications des erreurs.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> indicatorsDuration<br /> </td> 
   <td> Calculer les indicateurs pendant : durée depuis la limite de validité d’une diffusion après laquelle les indicateurs consolidés ne sont plus calculés.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 2592000<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> Identifiant du JavaScript à exécuter lors du démarrage du processus <br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> logCountPerRequest<br /> </td> 
   <td> Nombre de logs demandés par appel au serveur de tracking déporté.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Alerte consommation mémoire : alerte pour le niveau de RAM en Mo consommée par un processus donné.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Avertissement consommation mémoire : avertissement pour le niveau de RAM en Mo consommée par un processus donné.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> phishbowlServiceAPIKey<br /> </td> 
   <td> Clé d’API pour l’intégration du point d’entrée du service Phishbowl. Elle permet de protéger la redirection des URL incorrectement renseignées, générées à partir des anciens builds. <br /> </td> 
   <td> Long<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> phishbowlServiceEndpoint<br /> </td> 
   <td> Point d’entrée pour l’intégration du point d’entrée du service Phishbowl. Il permet de protéger la redirection des URL incorrectement renseignées, générées à partir des anciens builds. <br /> </td> 
   <td> Long<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Heure de la journée où le processus est redémarré automatiquement. Pour plus d'informations, consultez la section <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Redémarrage automatique des processus</a>.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorité au début. Les modules de priorité basse sont démarrés en premier et arrêtés en dernier. Le module syslogd doit donc avoir la priorité 0.<br /> </td> 
   <td> Court<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingIgnorePercent<br /> </td> 
   <td> Ignorer jusqu’à X % du tracking : limite la mise à jour des indicateurs de tracking si le pourcentage de journal de tracking non pris en compte n’atteint pas cette valeur.<br /> </td> 
   <td> Octet<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingIgnorePeriod<br /> </td> 
   <td> Mise à jour des indicateurs de tracking : durée maximum de désynchronisation des indicateurs de tracking.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> userAgentCacheSize<br /> </td> 
   <td> Taille du cache pour l’identification des navigateurs.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
 </tbody> 
</table>

## trackinglogd {#trackinglogd}

Voici les différents paramètres du nœud **trackinglogd**. Il s’agit de la configuration du démon d’écriture des logs de tracking.

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Valeur par défaut </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Paramètres de démarrage<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Démarrage automatique<br /> </td> 
   <td> Booléen<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> Identifiant du JavaScript à exécuter lors du démarrage du processus <br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxCreateFileRetry<br /> </td> 
   <td> Tentatives d’écriture max. : nombre maximal de fichiers pouvant être créés en cas d’erreur lors de l’écriture dans les fichiers de logs.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> maxLogsSizeOnDiskMb<br /> </td> 
   <td> Taille maximale des logs : taille maximale des logs sur le disque (en Mo). Ne peut pas être inférieur à 100 Mo. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Alerte consommation mémoire : alerte pour le niveau de RAM en Mo consommée par un processus donné.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Avertissement consommation mémoire : avertissement pour le niveau de RAM en Mo consommée par un processus donné.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSharedLogs<br /> </td> 
   <td> Nb max de logs : nombre maximum de logs stockés en mémoire partagée. Ne peut pas être inférieur à 10 000. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 25000<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Heure de la journée où le processus est redémarré automatiquement. Pour plus d'informations, consultez la section <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Redémarrage automatique des processus</a>.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeLogsPeriod<br /> </td> 
   <td> Nombre de logs avant purge : nombre de logs insérés avant de commencer la purge des fichiers journaux. Ne peut pas être inférieur à 50 000.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 50000<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorité au début. Les modules de priorité basse sont démarrés en premier et arrêtés en dernier. Le module syslogd doit donc avoir la priorité 0.<br /> </td> 
   <td> Court<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> webTrackingParamSize<br /> </td> 
   <td> Nombre maximal de caractères stockés en mémoire partagée pour les paramètres de tracking Web.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 64<br /> </td> 
  </tr> 
 </tbody> 
</table>

## web {#web}

Voici les différents paramètres du nœud **web**. Il s’agit de la configuration du module Web.

Pour plus d’informations, consultez cette [section](configuring-campaign-server.md#default-port-for-tomcat).

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Valeur par défaut </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> JVMOptions<br /> </td> 
   <td> Options de la JVM passées en string.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> MaxThreads<br /> </td> 
   <td> Nombre maximal de threads.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 75<br /> </td> 
  </tr> 
  <tr> 
   <td> MinSpareThreads<br /> </td> 
   <td> Nombre minimal de threads.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> args<br /> </td> 
   <td> Paramètres de démarrage<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Démarrage automatique<br /> </td> 
   <td> Booléen<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> controlPort<br /> </td> 
   <td> Port d’écoute de contrôle du Tomcat : voir la section <a href="configure-tomcat.md" target="_blank">Configurer Tomcat</a>.<br /> </td> 
   <td> Court<br /> </td> 
   <td> 8005<br /> </td> 
  </tr> 
  <tr> 
   <td> httpPort<br /> </td> 
   <td> Port d’écoute HTTP du Tomcat : voir la section <a href="configure-tomcat.md" target="_blank">Configurer Tomcat</a>.<br /> </td> 
   <td> Court<br /> </td> 
   <td> 8080<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> Identifiant du JavaScript à exécuter lors du démarrage du processus.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxDeliveryQueueSize<br /> </td> 
   <td> Taille de la file d’attente des appels à SubmitDelivery : nombre maximum d’appels SOAP à SubmitDelivery pouvant être placés en file d’attente.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 50<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Alerte consommation mémoire : alerte pour le niveau de RAM en Mo consommée par un processus donné.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Avertissement consommation mémoire : avertissement pour le niveau de RAM en Mo consommée par un processus donné.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> Relais de notification : HostName:Port permettant le relais des notifications.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Heure de la journée où le processus est redémarré automatiquement. Pour plus d'informations, consultez la section <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Redémarrage automatique des processus</a>.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorité au début. Les modules de priorité basse sont démarrés en premier et arrêtés en dernier. Le module syslogd doit donc avoir la priorité 0.<br /> </td> 
   <td> Court<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> startSoapRouterInModule<br /> </td> 
   <td> Démarrer le routeur SOAP en mode module.<br /> </td> 
   <td> Booléen<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### jsp {#jsp}

Voici les différents paramètres du nœud **web > jsp**. Il s’agit de la configuration des paramètres utilisés par les JSP.

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Valeur par défaut </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> debug<br /> </td> 
   <td> Exécution de la JSP en mode debug ou non.<br /> </td> 
   <td> Booléen<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> downloadPath<br /> </td> 
   <td> Répertoire de téléchargement : chemin d’accès au répertoire de téléchargement des programmes d’installation pour les consoles clientes.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/datakit/nl/eng/jsp'<br /> </td> 
  </tr> 
  <tr> 
   <td> foFileName<br /> </td> 
   <td> Chemin du fichier .fo.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> soapRouter<br /> </td> 
   <td> URL du routeur SOAP (http://monserveur/xxx, http://jni ou mailto:xxx).<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> 'http://jni'<br /> </td> 
  </tr> 
 </tbody> 
</table>

Le nœud **web > jsp > classpath** contient la liste de tous les Class Paths à utiliser lors du démarrage de la JVM. Voici la configuration par défaut :

```
'$(XTK_INSTALL_DIR)/tomcat-8/bin/bootstrap.jar
          $(XTK_INSTALL_DIR)/tomcat-8/bin/tomcat-juli.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat-coyote.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat-util.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/servlet-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/jsp-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/el-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/annotations-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/catalina.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/websocket-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat7-websocket.jar
          $(XTK_INSTALL_DIR)/java/lib/pdfbox-2.0.4.jar
          $(XTK_INSTALL_DIR)/java/lib/FontBox-0.1.0.jar
          $(XTK_INSTALL_DIR)/java/lib/AGJavaEndpoint.22.jar
          $(XTK_INSTALL_DIR)/java/lib/NSGConstants.jar
          $(XTK_INSTALL_DIR)/java/lib/smpp.jar
          $(XTK_INSTALL_DIR)/java/lib/nlweb.jar
          $(XTK_INSTALL_DIR)/java/lib/jcaptcha-all.jar
          $(XTK_INSTALL_DIR)/java/lib/apns-1.0.0.Beta6-jar-with-dependencies.jar
          $(XTK_INSTALL_DIR)/java/lib/commons-collections-3.2.2.jar
          $(XTK_INSTALL_DIR)/java/lib/jcommon-1.0.16.jar
          $(XTK_INSTALL_DIR)/java/lib/jfreechart-1.0.13.jar
          $(XTK_INSTALL_DIR)/java/lib/barcode4j-light.jar
          $(XTK_INSTALL_DIR)/java/lib/zxing.jar
          $(XTK_INSTALL_DIR)/java/lib/raztec.jar
          $(XTK_INSTALL_DIR)/java/lib/gson-2.7.jar
          $(XTK_INSTALL_DIR)/java/lib/alpn-api-1.1.3.v20160715.jar
          $(XTK_INSTALL_DIR)/java/lib/netty-all-4.1.6.Final.jar
          $(XTK_INSTALL_DIR)/java/lib/netty-tcnative-boringssl-static-1.1.33.Fork22.jar
          $(XTK_INSTALL_DIR)/java/lib/pushy-0.8.1.jar
          $(XTK_INSTALL_DIR)/java/lib/slf4j-api-1.7.21.jar
          $(XTK_INSTALL_DIR)/java/lib/slf4j-simple-1.7.21.jar'
```

### jssp {#jssp}

Voici les différents paramètres du nœud **web > jssp**. Il s’agit de la configuration des paramètres utilisés par les JSSP.

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Valeur par défaut </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> collectsGarbageAfterRequest<br /> </td> 
   <td> Active le garbage collector du contexte JavaScript après chaque requête.<br /> </td> 
   <td> Booléen<br /> </td> 
   <td> vrai<br /> </td> 
  </tr> 
  <tr> 
   <td> timeToLive<br /> </td> 
   <td> Nombre maximum de pages servies par un contexte JavaScript. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
 </tbody> 
</table>

Le nœud **web > jsp > classpath** contient la liste de tous les Class Paths à utiliser lors du démarrage de la JVM.

### relay {#relay-2}

Voici les différents paramètres du nœud **web > relay**. Il s’agit de la configuration du relais de requêtes HTTP entre deux zones.

Pour plus d’informations, consultez cette [section](../../installation/using/deploying-an-instance.md#synchronizing-public-resources).

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Valeur par défaut </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> debugRelay<br /> </td> 
   <td> Démarrer le module de relais HTTP dans le serveur Web en mode debug.<br /> </td> 
   <td> Booléen<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> forbiddenCharsInAuthority<br /> </td> 
   <td> Caractère(s) interdit(s) (domaine) : liste des caractères interdits dans la partie 'autorité' d’une URI.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> '.?#@/:' <br /> </td> 
  </tr> 
  <tr> 
   <td> forbiddenCharsInPath<br /> </td> 
   <td> Caractère(s) interdit(s) (chemin) : liste des caractères interdits dans la partie 'chemin' d’une URI.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> '?#/'<br /> </td> 
  </tr> 
  <tr> 
   <td> modDir<br /> </td> 
   <td> Valeur de l’option du module 'mod_dir' : liste des fichiers à servir lors d’une requête sur un dossier.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> 'index.md' <br /> </td> 
  </tr> 
  <tr> 
   <td> startRelay<br /> </td> 
   <td> Démarrer le module de relais HTTP.<br /> </td> 
   <td> Booléen<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> startRelayInModule<br /> </td> 
   <td> Démarrer le module de relais HTTP dans le serveur Web. <br /> </td> 
   <td> Booléen<br /> </td> 
   <td> vrai<br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Temps d’attente avant effacement de l’URL bannie.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> '60'<br /> </td> 
  </tr> 
 </tbody> 
</table>

Ajoutez un nœud **web > relay > url** pour chaque URL à relayer (prioritaires par ordre d’insertion) avec les paramètres suivants.

Pour plus d&#39;informations, voir la section [Sécurité et relais des pages dynamiques](../../installation/using/configuring-campaign-server.md#dynamic-page-security-and-relays) et [cette section](../../installation/using/deploying-an-instance.md#synchronizing-public-resources).

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Valeur par défaut </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> IPMask<br /> </td> 
   <td> IP autorisées : liste (séparée par des virgules) des adresses IP sources ayant la autorisation d’utiliser le module de relais pour ce masque.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> deny<br /> </td> 
   <td> Ne pas autoriser l’accès à ces URL (renvoie un HTTP 403)<br /> </td> 
   <td> Booléen<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> hostMask<br /> </td> 
   <td> Alias DNS à relayer : liste (séparée par des virgules) de masques d’alias DNS à relayer (ex : '*.adobe.com').<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> httpAllowed<br /> </td> 
   <td> Accès HTTP autorisé quelle que soit la zone de sécurité (comme les webApps). <br /> </td> 
   <td> Booléen<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> relayHost<br /> </td> 
   <td> Ajout du host initial : utiliser l’en-tête HTTP 'Host' de la requête initiale à relayer.<br /> </td> 
   <td> Booléen<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> relayPath<br /> </td> 
   <td> Ajout du chemin initial : compléter l’URL de la page cible avec le chemin complet des URL à relayer. <br /> </td> 
   <td> Booléen<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> status<br /> </td> 
   <td> Statut de la synchronisation d’une ressource publique (énumération). Les valeurs possibles sont 'normal' (exécution normale), 'liste bloquée' (URL ajoutée à la liste bloquée en cas d'erreur 404) et 'spare' (téléchargement du fichier sur les spare server si existant).<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> normal<br /> </td> 
  </tr> 
  <tr> 
   <td> targetUrl<br /> </td> 
   <td> URL de la page cible : voir la section <a href="configure-tomcat.md" target="_blank">Configurer Tomcat</a>.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Délai maximum d’exécution de la requête relayée, exprimé en secondes.<br /> </td> 
   <td> Long<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> urlPath<br /> </td> 
   <td> Masque des URL à relayer (ex : '/nl*', '*.jsp').<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

Voici la configuration par défaut :

```
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true"
     status="normal" targetUrl="http://localhost:7781" timeout="" urlPath="/pipelined/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="false" urlPath="/view/*"/>
<url IPMask="" deny="true" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="false" urlPath="*ooconv.jsp*"/>
<url IPMask="" deny="true" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="false" urlPath="/res/*.jsp*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="*/sc.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="*/interactionProposal.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="*/zoneJson.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nms/jsp/barcode.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nms/jsp/captcha.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nms/jsp/webForm.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/xtk/jsp/zoneinfo.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="*/facebookCallback.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nl/jsp/m.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nl/jsp/s.jsp"/>

<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/nms/jsp/*.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/xtk/jsp/*.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/nl/jsp/*.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="*.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="true" urlPath="/webApp/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/report/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/jssp/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="false" urlPath="/strings/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/interaction/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/barcode/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/lineImage/*"/>

<url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" targetUrl=""
     timeout="" status="spare" httpAllowed="true" urlPath="/favicon.*"/>
<url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" targetUrl=""
     timeout="" status="spare" httpAllowed="true" urlPath="/*.md"/>
<url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" targetUrl=""
     timeout="" status="spare" httpAllowed="true" urlPath="/*.png"/>
<url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" targetUrl=""
     timeout="" status="spare" httpAllowed="true" urlPath="/*.jpg"/>
```

Ajoutez un nœud **web > relay > responseHeader** pour chaque en-tête HTTP à ajouter aux réponses transférées au relais.

Pour plus d&#39;informations, voir la section [Gestion des en-têtes HTTP (HTTP Headers)](../../installation/using/configuring-campaign-server.md#managing-http-headers).

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> name<br /> </td> 
   <td> Nom de l’en-tête<br /> </td> 
   <td> Chaîne <br /> </td> 
  </tr> 
  <tr> 
   <td> valeur<br /> </td> 
   <td> Valeur de l’en-tête <br /> </td> 
   <td> Chaîne <br /> </td> 
  </tr> 
 </tbody> 
</table>

Voici la configuration par défaut :

```
<responseHeader name="X-XSS-Protection" value="1; mode=block"/>
```

### redirection {#redirection}

Voici les différents paramètres du nœud **web > redirection**. Il s’agit de la configuration du service de redirection.

Pour plus d’informations, consultez cette [section](../../installation/using/deploying-an-instance.md#synchronizing-public-resources).

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Valeur par défaut </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> IMSOrgId<br /> </td> 
   <td> Identifiant de l’organisation : identifiant d’organisation unique dans Adobe Experience Cloud, utilisé notamment pour le service VisitorID et le SSO de l’IMS. <br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> P3PCompactPolicy<br /> </td> 
   <td> Valeur décrivant la politique de gestion des cookies permanents (au format P3P compact policy). <br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> 'CAO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV'<br /> </td> 
  </tr> 
  <tr> 
   <td> cookieDomain<br /> </td> 
   <td> Liste des domaines, séparés par des virgules, à configurer afin d’indiquer explicitement votre domaine pour définir un cookie. <br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> databaseId<br /> </td> 
   <td> Identifiant de la base de données associé à l’instance de tracking.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> defLogCount<br /> </td> 
   <td> Nb de logs par appel : nombre de logs retournés par défaut lors de l’appel de la méthode GetTrackingLogs.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> expirationURL<br /> </td> 
   <td> Page des redirections périmées : adresse de la page web utilisée par défaut par le module de redirection lorsque l’action de diffusion a expiré.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxJobsInCache<br /> </td> 
   <td> Nb max de tâches : nombre maximal d’actions de diffusion dans le cache. Ne peut pas être inférieur à 50. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> showSourceIP<br /> </td> 
   <td> Si ce paramètre est défini sur « false », la valeur de sourceIP dans la réponse renvoyée par r/test est une chaîne vide. <br /> </td> 
   <td> Booléen<br /> </td> 
   <td> vrai<br /> </td> 
  </tr> 
  <tr> 
   <td> startRedirection<br /> </td> 
   <td> Démarrer le service de redirection.<br /> </td> 
   <td> Booléen<br /> </td> 
   <td> vrai<br /> </td> 
  </tr> 
  <tr> 
   <td> startRedirectionInModule<br /> </td> 
   <td> Démarrer le service de redirection en mode module.<br /> </td> 
   <td> Booléen<br /> </td> 
   <td> vrai<br /> </td> 
  </tr> 
  <tr> 
   <td> trackWebVisitors<br /> </td> 
   <td> Tracking web : génération des logs pour les pages visitées par des utilisateurs inconnus. <br /> </td> 
   <td> Booléen<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingPassword<br /> </td> 
   <td> Mot de passe utilisé par le serveur de redirection.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

Voici les différents paramètres du nœud **web > redirection > spareServer**.

Pour plus d&#39;informations, voir la section [Tracking redondant](../../installation/using/configuring-campaign-server.md#redundant-tracking).

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Valeur par défaut </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> enabledIf<br /> </td> 
   <td> Pris en compte si : le serveur de tracking est pris en compte si l’expression retourne vrai. <br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> id<br /> </td> 
   <td> Nom<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> url<br /> </td> 
   <td> URL d’un serveur de redirection supplémentaire<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

### spamCheck {#spamcheck}

Voici les différents paramètres du nœud **web > spamCheck**. Il s’agit de la configuration des paramètres de l’évaluation du score anti-spam des emails.

Pour plus d&#39;informations, voir la section [Paramétrage de SpamAssassin](../../installation/using/configuring-spamassassin.md).

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> command<br /> </td> 
   <td> Commande à exécuter pour évaluer le score anti-spam d’un email (ex : 'perl spamcheck.pl').<br /> </td> 
   <td> Chaîne <br /> </td> 
  </tr> 
 </tbody> 
</table>

## wfserver {#wfserver}

Voici les différents paramètres du nœud **wfserver**. Il s’agit de la configuration des processus de workflow.

Pour plus d&#39;informations, voir la section [Workflows en haute disponibilité et affinités](../../installation/using/configuring-campaign-server.md#high-availability-workflows-and-affinities).

<table> 
 <thead> 
  <tr> 
   <th> Paramètre </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Valeur par défaut </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> affinity<br /> </td> 
   <td> Affinité<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> args<br /> </td> 
   <td> Paramètres de démarrage<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Démarrage automatique<br /> </td> 
   <td> Booléen<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> dataBasePoolPeriodSec<br /> </td> 
   <td> Période<br /> </td> 
   <td> Long<br /> </td> 
   <td> 20<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> Identifiant du JavaScript à exécuter lors du démarrage du processus.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Alerte consommation mémoire : alerte pour le niveau de RAM en Mo consommée par un processus donné.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Avertissement consommation mémoire : avertissement pour le niveau de RAM en Mo consommée par un processus donné.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> Relais de notification : HostName:Port permettant le relais des notifications.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Heure de la journée où le processus est redémarré automatiquement. Pour plus d'informations, consultez la section <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Redémarrage automatique des processus</a>.<br /> </td> 
   <td> Chaîne <br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorité au début. Les modules de priorité basse sont démarrés en premier et arrêtés en dernier. Le module syslogd doit donc avoir la priorité 0.<br /> </td> 
   <td> Court<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>
