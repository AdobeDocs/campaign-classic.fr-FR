---
title: Fonctionnalités obsolètes et supprimées de Campaign Classic
description: Cette page répertorie les fonctionnalités obsolètes et supprimées d’Adobe Campaign Classic
page-status-flag: never-activated
uuid: null
contentOwner: simonetn
products: SG_CAMPAIGN/CLASSIC
audience: rn
content-type: reference
topic-tags: campaign-classic-deprecated-features
discoiquuid: null
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: be148d7cd55097b9014d2f4d3b095c65a5ca8c54
workflow-type: tm+mt
source-wordcount: '1389'
ht-degree: 97%

---


# Fonctionnalités obsolètes et supprimées {#deprecated-and-removed-features}

Adobe évalue constamment les fonctionnalités des produits pour identifier celles qui devraient être remplacées par des solutions plus modernes afin d’offrir une plus grande valeur ajoutée, et ce en prenant toujours en compte la rétrocompatibilité Comme Adobe Campaign Classic fonctionne avec des outils tiers, la compatibilité est régulièrement mise à jour pour ne mettre en œuvre que des versions prises en charge. Les versions devenues incompatibles avec Adobe Campaign Classic sont répertoriées ci-dessous.

Lors de l’annonce de la suppression ou du remplacement imminent de fonctionnalités de Campaign Classic, les règles suivantes s’appliquent :

* L’annonce de l’obsolescence vient en premier. Les fonctionnalités obsolètes sont encore disponibles pour les utilisateurs existants, elles ne seront plus améliorées ni documentées.
* La suppression de fonctionnalités obsolètes aura lieu au plus tôt dans la version suivante. La date de suppression prévue est annoncée sur cette page.

Cette procédure laisse aux clients au moins un cycle de publication pour s’adapter à une nouvelle version ou au successeur d’une fonctionnalité supprimée avant la suppression définitive.

>[!NOTE]
>Les versions et nouvelles fonctionnalités d’Adobe Campaign sont répertoriées dans les [Notes de mise à jour](../../rn/using/latest-release.md).


## Fonctionnalités obsolètes {#deprecated-features}

Cette section répertorie les fonctions et fonctionnalités qui ont été désignées comme étant obsolètes dans les dernières versions de Campaign Classic.

En règle générale, les fonctionnalités qui doivent être supprimées dans une version ultérieure sont définies comme étant obsolètes dans un premier temps et une solution de remplacement est fournie. Ces fonctionnalités ne sont plus disponibles pour les nouveaux clients Campaign Classic ou ne doivent pas être utilisées pour une nouvelle mise en oeuvre. Elles sont également supprimées de la documentation du produit.

Il est conseillé aux clients d’évaluer dans quelle mesure ils utilisent la fonctionnalité dans leur déploiement actuel et d’envisager de modifier leur implémentation pour utiliser la solution de remplacement proposée. Référez-vous aux dates de suppression prévues pour planifier les mises à jour de votre environnement et de vos projets en conséquence.

### Adobe Campaign version 18.6 {#ac-18-6-release}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Domaine</strong></td>
   <td><strong>Fonctionnalité</strong></td> 
   <td><strong>Remplacement</strong></td> 
  </tr> 
   <tr> 
   <td>Sécurité SDK JavaScript<br> </td>
   <td>decryptString<br> </td>
   <td><p>Pour des raisons de sécurité, l’API <em>decryptString</em> n’est plus disponible par défaut pour les nouvelles installations.</p> 
   <p>Dans le contexte d’un postupgrade vers la version 18.6 (et versions ultérieures), cette API n’est plus activée et a été remplacée par la fonction <em>decryptPassword</em>.</p><br> </td>
  </tr> 
 </tbody> 
</table>

### Adobe Campaign version 18.4 {#ac-18-4-release}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Domaine</strong></td>
   <td><strong>Fonctionnalité</strong></td> 
   <td><strong>Remplacement</strong></td> 
  </tr> 
   <tr> 
   <td>Archivage des emails<br> </td>
   <td>Archivage basé sur des fichiers<br> </td>
   <td><p>L’archivage des emails est désormais disponible par le biais d’une adresse de messagerie Cci dédiée. <a href="../../installation/using/email-archiving.md">En savoir plus</a>.</p> 
   <p><em>Date prévue de suppression : Campaign version 20.2 - juin 2020</em></p><br> </td>
  </tr> 
   <tr> 
   <td>Gestion des leads<br> </td>
   <td>Leads<br> </td>
   <td><p>Le package de gestion des leads d’Adobe Campaign Classic a simplifié le processus de création et de maintenance de l’ensemble du cycle de vie de la gestion des leads. Il est possible de mettre en œuvre des fonctionnalités similaires à l’aide d’autres activités de workflow natives et des modifications de modèles de données.</p> 
   <p><em>Date prévue de suppression : Campaign version 20.2 - juin 2020</em></p><br> </td>
  </tr> 
 </tbody> 
</table>


## Compatibilité obsolète {#deprecated-compatibility}

### Adobe Campaign version 20.1 {#compat-20-1-release}

À compter de la version de février 20.1, le système suivant est obsolète pour Campaign Classic. La compatibilité prendra fin avec la version 20.2 - juin 2020.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Domaine</strong></td>
   <td><strong>Remplacement</strong></td> 
  </tr> 
   <tr> 
   <td>Console cliente Campaign Classic 32 bits<br> </td>
   <td><p>Console cliente Campaign Classic 64 bits</p><br> </td>
  </tr> 
 </tbody> 
</table>

### Adobe Campaign version 19.2 {#compat-19-2-release}

À compter de la version de l&#39;automne 19.2, les systèmes d’exploitation suivants sont obsolètes pour Campaign Classic. La compatibilité ne sera plus assurée à partir de la fin de l’année 2020.

* Server web : Apache 2.2. [En savoir plus](https://wiki.centos.org/About/Product)
* Système d’exploitation : CentOS 6. [En savoir plus](https://wiki.centos.org/About/Product)

Reportez-vous à la [matrice de compatibilité](https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix.html) pour effectuer une mise à jour vers une nouvelle version ou passer à un nouveau système.

## Fonctionnalités supprimées {#removed-features}

Cette section liste les fonctionnalités qui ont été supprimées de Campaign Classic.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Domaine - Fonctionnalité</strong></td>
   <td><strong>Remplacement</strong></td> 
   <td><strong>Version</strong></td> 
  </tr> 
   <tr> 
   <td>Documentation des API de Campaign - fichier jsapi.chm<br> </td>
   <td><a href="https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html">Les API de Campaign Classic sont maintenant disponibles dans une page dédiée. Si vous utilisiez le fichier jsapi.chm, vous devez à présent vous référer à la nouvelle version en ligne</a>.</td>
   <td>19.1</td>
  </tr> 
  <tr> 
   <td>Orchestration de campagnes - Marketing prédictif</td>
   <td>Une grande partie des fonctionnalités de marketing prédictif d’Adobe Campaign Classic repose sur la consommation de modèles prédictifs. Bien que l’activité de workflow de marketing prédictif soit supprimée dans une prochaine version, Adobe Campaign continuera à prendre en charge la consommation et l’utilisation de modèles prédictifs provenant de sources externes par le biais d’autres activités de workflow.</td>
   <td>18.10</td>
  </tr> 
  <tr> 
   <td>Applications web - Microsites</td>
   <td>Il s’agit d’améliorer la sécurité en limitant l’accès aux seuls domaines dédiés pour les fichiers de configuration d’Adobe Campaign. Vous pouvez toujours utiliser des URL personnalisées dans Campaign en utilisant des alias DNS. <a href="https://helpx.adobe.com/fr/campaign/kb/domain-name-delegation.html">En savoir plus</a>.</td>
   <td>18.10</td>
  </tr> 
  <tr> 
   <td>Notifications push - Connecteur binaire iOS<br> </td>
   <td>Selon la recommandation d’Apple, Adobe supprimera l’ancien connecteur binaire iOS. Le connecteur HTTP/2, plus performant et plus efficace, est déjà disponible.</td>
   <td>18.10</td>
  </tr> 
   <tr> 
   <td>Canal mobile - Messages MMS et WAP Push</td>
   <td>Les canaux MMS et Wap Push ne sont plus disponibles. À titre de remplacement, vous pouvez tirer parti des diffusions <a href="../../delivery/using/sms-channel.md">SMS</a> et <a href="../../delivery/using/about-mobile-app-channel.md">Push</a>.</td>
   <td>18.4</td>
  </tr> 
   <tr> 
   <td>Canal mobile - LINE v1</td>
   <td>Le package LINE Connect n’est plus disponible pour une installation dans Adobe Campaign Classic. Adobe recommande d’utiliser le nouveau package de canal LINE pour envoyer des messages LINE. <a href="../../delivery/using/line-channel.md">En savoir plus</a>.</td>
   <td>18.4</td>
  </tr> 
 </tbody> 
</table>

## Fin de compatibilité {#end-of-compatibility}

>[!CAUTION]
>
>Adobe Campaign Classic est compatible avec tous les systèmes et outils répertoriés dans la [matrice de compatibilité](https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix.html). Lorsque des versions spécifiques de ces systèmes et outils tiers arrivent en fin de vie (EOL) avec leurs créateurs respectifs, Adobe Campaign n’est plus compatible avec celles-ci : elles sont déclarées obsolètes, puis supprimées de la matrice de compatibilité pour la version suivante du produit. Pour éviter tout problème, vérifiez que vous disposez des versions prises en charge des systèmes répertoriés dans la matrice de compatibilité.

### Console cliente {#client-console-eol}

La console cliente d’Adobe Campaign Classic ne peut plus s’exécuter sur les systèmes suivants, car ils ont été abandonnés par leur éditeur. Les clients qui utilisent la console cliente de Campaign sur l’une de ces versions doivent effectuer la mise à niveau vers la version la plus récente avant la date de suppression prévue. Reportez-vous à la [matrice de compatibilité](https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix.html).

* Windows Server 2003, 2008, 2008 R2
* Windows XP, Vista

### Systèmes d’exploitation {#o-s-eol}

Depuis la version 19.1, Adobe Campaign n’est plus compatible avec les systèmes d’exploitation ci-après.

* Debian 7. [En savoir plus](https://wiki.debian.org/DebianReleases).
* RHEL 6.x. [En savoir plus](https://access.redhat.com/support/policy/updates/errata).
* Windows Server 2008. [En savoir plus](https://support.microsoft.com/en-us/lifecycle/search/1163).
* SLES 11. [En savoir plus](https://www.suse.com/lifecycle).

### Serveurs web {#web-server-eol}

Depuis la version 19.1 du printemps, Adobe Campaign n’est plus compatible avec les serveurs web ci-après.

* Microsoft IIS 7. [En savoir plus](https://support.microsoft.com/fr-fr/lifecycle/search/810).

### Outils {#tools-eol}

Depuis la version 19.1 du printemps, Adobe Campaign n’est plus compatible avec les outils ci-après.

* Java JDK 7. [En savoir plus](http://www.oracle.com/technetwork/java/javase/eol-135779.html).
* Libre Office 3.5 / 4.3 / 5.x, sauf intégré dans un autre outil. [En savoir plus](https://wiki.documentfoundation.org/ReleasePlan/Archive#End-of-Life_Releases).

### Moteurs de base de données {#dbe-eol}

Adobe ne prend pas en charge les moteurs de base de données ci-après, car ils ont été abandonnés par leur éditeur. Les clients utilisant ces versions doivent effectuer la mise à niveau vers la version la plus récente ou passer à une autre.

Consultez la [matrice de compatibilité de Campaign Classic](https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix.html) pour accéder à la liste des versions compatibles.

**FEDERATED DATA ACCESS (FDA)**

Depuis la version 19.1 du printemps, Adobe Campaign n’est plus compatible avec les serveurs FDA ci-après.

* Oracle 11G. [En savoir plus](http://www.oracle.com/us/support/library/lifetime-support-technology-069183.pdf).
* PostgreSQL 9.3. [En savoir plus](https://www.postgresql.org/support/versioning).
* MySQL 5.5. &lt;[En savoir plus](http://www.fromdual.com/support-for-mysql-from-oracle).
* DB2 9.5. [En savoir plus](http://www-01.ibm.com/support/docview.wss?uid=swg21168270).
* Teradata 14 – 14.1. [En savoir plus](https://community.teradata.com/t5/Database/Teradata-Database-Product-Life-Cycle/td-p/35068).

Campaign Classic n’est pas compatible avec les serveurs ci-après dans Federated Data Access (FDA).

* DB2 UDB 9.5, 9.7. Une version plus récente de DB2 est prise en charge via Federated Data Access (FDA). [En savoir plus](http://www-01.ibm.com/support/docview.wss?uid=swg21168270).
* Oracle 9i, 10G R2. Les versions plus récentes d’Oracle sont prises en charge via Federated Data Access (FDA). [En savoir plus](http://www.oracle.com/us/support/library/lifetime-support-technology-069183.pdf).
* PostgreSQL 8.3, 8.4, 9.0, 9.1, 9.2. Les versions plus récentes de PostgreSQL sont prises en charge via Federated Data Access (FDA). [En savoir plus](https://www.postgresql.org/support/versioning).
* MSSQL 2000, 2005, 2008 R2. Les versions plus récentes de SQL Server sont prises en charge via Federated Data Access (FDA). [En savoir plus](https://support.microsoft.com/en-us/lifecycle/search/1044).
* MySQL 5.1. Les versions plus récentes de MySQL sont prises en charge via Federated Data Access (FDA). [En savoir plus](https://en.wikipedia.org/wiki/InfiniDB).
* InfiniDB a atteint sa fin de vie. [En savoir plus](https://www.mysql.com/support).
* Teradata 13, 13.1. Des versions plus récentes de Teradata sont prises en charge via Federated Data Access (FDA). [En savoir plus](https://www.info.teradata.com/download.cfm?ItemID=1007255).
* Netezza 6.02, 7.0. Netezza a atteint sa fin de vie. [En savoir plus](https://en.wikipedia.org/wiki/Netezza).
* AsterData 5.0. AsterData a atteint sa fin de vie. [En savoir plus](https://en.wikipedia.org/wiki/Aster_Data_Systems).
* Sybase IQ 15.2, 15.4, 15.5 et Sybase ASE 15.0. Des versions plus récentes de Sybase sont prises en charge par Federated Data Access (FDA). [En savoir plus](https://sites.google.com/site/dbatipsandtricks/time-tracker).
* Hadoop via HiveSQL : Hadoop 2.7.3, HiveSQL 1.2.1. Adobe Campaign Classic continuera à prendre en charge les versions répertoriées de Hadoop via HiveSQL par le biais de Federated Data Access (FDA), mais ces versions sont fusionnées avec : HortonWorks (HDP 2.4.X, 2.5.x, 2.6.x) et HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)

**SERVEUR SGBDR**

Adobe Campaign n’est pas compatible avec les serveurs SGBDR suivants :
* Oracle 10GR2, 11G
* PostgreSQL 9.0 à 9.3
* SQL Server 2005
* MySQL 5.1
* DB2 UDB 9.7
