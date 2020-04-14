---
title: Campaign Classic fonctionnalités obsolètes et supprimées
description: Ce de page  des fonctionnalités obsolètes et supprimées de  Classic
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
source-git-commit: 10419ee0fb466bddd05ab67087ccdbfdda1e48c8

---


# Deprecated and removed features {#deprecated-and-removed-features}

Adobe évalue constamment les fonctionnalités des produits pour identifier celles qui devraient être remplacées par des solutions plus modernes afin d’offrir une plus grande valeur ajoutée, et ce en prenant toujours en compte la rétrocompatibilité Comme  Adobe Campaign Classic fonctionne avec des outils tiers, la compatibilité est mise à jour régulièrement afin de n’implémenter que les versions prises en charge. Les versions qui ne sont plus compatibles avec  Adobe Campaign Classic sont répertoriées ci-dessous.

Pour communiquer la suppression ou le remplacement imminent des capacités Campaign Classic, les règles suivantes s’appliquent :

* L’annonce de l’obsolescence vient en premier. Les fonctionnalités obsolètes sont encore disponibles pour les utilisateurs existants, elles ne seront plus améliorées ni documentées.
* La suppression de fonctionnalités obsolètes aura lieu au plus tôt dans la version suivante. La date de suppression prévue est annoncée sur cette page.

Cette procédure laisse aux clients au moins un cycle de publication pour s’adapter à une nouvelle version ou au successeur d’une fonctionnalité supprimée avant la suppression définitive.

>[!NOTE]
>Les versions et nouvelles fonctionnalités d’Adobe Campaign sont répertoriées dans les [Notes de mise à jour](../../rn/using/latest-release.md).


## Deprecated features {#deprecated-features}

Cette section les fonctionnalités et fonctionnalités qui ont été marquées comme obsolètes avec les dernières versions Campaign Classic.

En règle générale, les fonctionnalités qui doivent être supprimées dans une version ultérieure sont définies comme étant obsolètes dans un premier temps et une solution de remplacement est fournie. Ces fonctions et fonctionnalités ne sont plus disponibles pour les nouveaux clients de Campaign Standard ou ne doivent pas être utilisées dans le cadre d’une nouvelle implémentation. Elles sont également supprimées de la documentation du produit.

Il est conseillé aux clients d’évaluer dans quelle mesure ils utilisent la fonctionnalité dans leur déploiement actuel et d’envisager de modifier leur implémentation pour utiliser la solution de remplacement proposée. Référez-vous aux dates de suppression prévues pour planifier les mises à jour de votre environnement et de vos projets en conséquence.

### Adobe Campaign 18.6 release {#ac-18-6-release}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Zone</strong></td>
   <td><strong>Fonctionnalité</strong></td> 
   <td><strong>Remplacement</strong></td> 
  </tr> 
   <tr> 
   <td>Sécurité SDK JavaScript<br> </td>
   <td>decryptString<br> </td>
   <td><p>Pour des raisons de sécurité, l’API decryptString n’est plus disponible par défaut pour les nouvelles installations.</p> 
   <p>Dans le contexte d’une mise à niveau vers la version 18.6 (et ultérieure), cette API n’est plus activée et a été remplacée par la fonction decryptPassword.</p><br> </td>
  </tr> 
 </tbody> 
</table>

### Adobe Campaign 18.4 release {#ac-18-4-release}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Zone</strong></td>
   <td><strong>Fonctionnalité</strong></td> 
   <td><strong>Remplacement</strong></td> 
  </tr> 
   <tr> 
   <td>Archivage des emails<br> </td>
   <td>Archivage<br>basé sur des fichiers</td>
   <td><p>L’archivage des e-mails est désormais disponible via une adresse de courriel BCC dédiée. <a href="../../installation/using/email-archiving.md">En savoir plus</a>.</p> 
   <p><em>Date de  de suppression du : Version Campaign 20.2 - Juin 2020</em></p><br> </td>
  </tr> 
   <tr> 
   <td>Gestion<br>des pistes</td>
   <td>Leads<br> </td>
   <td><p>Le module Gestion des pistes de  Adobe Campaign Classic a simplifié le processus de création et de maintenance du cycle de vie de la gestion des pistes. Des fonctionnalités similaires peuvent être mises en oeuvre par le biais d’autres flux de travail natifs   et modifications de modèles de données.</p> 
   <p><em>Date de  de suppression du : Version Campaign 20.2 - Juin 2020</em></p><br> </td>
  </tr> 
 </tbody> 
</table>


## Compatibilité obsolète {#deprecated-compatibility}

### Adobe Campaign 20.1 release {#compat-20-1-release}

À compter de la version de février 20.1, le système suivant est obsolète pour Campaign Classic. La compatibilité prendra fin dans la version 20.2 - juin 2020.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Zone</strong></td>
   <td><strong>Remplacement</strong></td> 
  </tr> 
   <tr> 
   <td>Console cliente Campaign Classic 32 bits<br> </td>
   <td><p>Console cliente Campaign Classic 64 bits</p><br> </td>
  </tr> 
 </tbody> 
</table>

### Adobe Campaign 19.2 release  {#compat-19-2-release}

À compter de la version de l&#39;automne 19.2, les systèmes d’exploitation suivants sont obsolètes pour Campaign Classic. La compatibilité ne sera plus assurée à partir de la fin de l’année 2020.

* Serveur Web : Apache 2.2. En [savoir plus](https://wiki.centos.org/About/Product)
* Système d’exploitation : CentOS 6. [En savoir plus](https://wiki.centos.org/About/Product)

Reportez-vous à la [matrice de compatibilité](https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix.html) pour effectuer une mise à jour vers une nouvelle version ou passer à un nouveau système.

## Fonctions supprimées {#removed-features}

Cette section les fonctionnalités et fonctionnalités qui ont été supprimées de Campaign Standard.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Zone - Fonction</strong></td>
   <td><strong>Remplacement</strong></td> 
   <td><strong>Version</strong></td> 
  </tr> 
   <tr> 
   <td>Documentation des API Campaign - fichier<br>jsapi.chm</td>
   <td>Campaign Classic APIs are now available in a dedicated page. If you were using the jsapi.chm file, you should now refer to <a href="https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html">the new online version</a>.</td>
   <td>&lt;19.1</td>
  </tr> 
  <tr> 
   <td>Orchestration Campaign - Marketing prédictif</td>
   <td>Une grande partie des capacités de marketing prédictif dans  Adobe Campaign Classic a été la consommation de modèles prédictifs. Bien que le flux de travail de marketing prédictif   soit supprimé dans une version à venir, le  continuera de prendre en charge la consommation et l’utilisation de modèles prédictifs à partir de sources externes par le biais d’autresde flux de travail.</td>
   <td>18.10</td>
  </tr> 
  <tr> 
   <td>  - Microsites</td>
   <td>Améliorer la sécurité en limitant l'accès aux domaines dédiés uniquement sur  fichiers de configuration Adobe Campaign. Vous pouvez toujours utiliser des URL personnalisées dans Campaign en utilisant des alias DNS. <a href="https://helpx.adobe.com/fr/campaign/kb/domain-name-delegation.html">En savoir plus</a>.</td>
   <td>18.10</td>
  </tr> 
  <tr> 
   <td>Notifications Push - Connecteur<br>binaire iOS</td>
   <td>Selon la recommandation d’Apple, Adobe supprimera le connecteur binaire iOS hérité. Le connecteur HTTP/2 plus performant et plus efficace est déjà disponible.</td>
   <td>18.10</td>
  </tr> 
   <tr> 
   <td>mobile - Messages MMS et WAP Push</td>
   <td>Les  MMS et Wap Push ne sont plus disponibles. À titre de remplacement, vous pouvez tirer parti des <a href="../../delivery/using/sms-channel.md"></a> SMS <a href="../../delivery/using/about-mobile-app-channel.md">et</a> Push.</td>
   <td>18.4</td>
  </tr> 
   <tr> 
   <td>mobile  - LINE v1</td>
   <td>Le package LINE Connect n’est plus disponible pour l’installation dans  Adobe Campaign Classic. Adobe recommande d’utiliser le nouveau package de  LINE pour envoyer des messages LINE. <a href="../../delivery/using/line-channel.md">En savoir plus</a>.</td>
   <td>18.4</td>
  </tr> 
 </tbody> 
</table>

## Fin de compatibilité {#end-of-compatibility}

>[!CAUTION]
>
> Adobe Campaign Classic est compatible avec tous les systèmes et outils répertoriés dans la matrice [de](https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix.html)compatibilité. Lorsque des versions spécifiques de ces systèmes et outils tiers atteignent la fin de vie (EOL) avec leurs créateurs respectifs,  Adobe Campaign n’est plus compatible avec ces versions : elles sont déclarées comme obsolètes, puis sont supprimées de notre matrice de compatibilité dans la version suivante du produit. Assurez-vous que vous utilisez les versions prises en charge des systèmes répertoriés dans la matrice de compatibilité pour éviter tout problème.

### Console client {#client-console-eol}

 console client Adobe Campaign Classic ne peut plus s’exécuter sur les systèmes suivants, car ils ont été abandonnés par leur éditeur. Les clients qui exécutent Campaign Console client sur l’une de ces versions doivent effectuer la mise à niveau vers la version la plus récente avant la date  de suppression du. Reportez-vous à la matrice [de](https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix.html)compatibilité.

* Windows Server 2003, 2008, 2008 R2
* Windows XP, Vista

### Systèmes d&#39;exploitation {#o-s-eol}

Depuis la version 19.1,  Adobe Campaign n’est plus compatible avec les systèmes d’exploitation suivants.

* Debian 7. [En savoir plus](https://wiki.debian.org/DebianReleases).
* RHEL 6.x. En [savoir plus](https://access.redhat.com/support/policy/updates/errata).
* Windows Server 2008. [En savoir plus](https://support.microsoft.com/en-us/lifecycle/search/1163).
* SLES 11. [En savoir plus](https://www.suse.com/lifecycle).

### Serveurs Web {#web-server-eol}

Depuis la version du printemps 19.1,  Adobe Campaign n’est plus compatible avec le serveur Web suivant.

* Microsoft IIS 7. [En savoir plus](https://support.microsoft.com/en-us/lifecycle/search/810).

### Tools {#tools-eol}

Depuis la version du printemps 19.1,  Adobe Campaign n’est plus compatible avec les outils suivants.

* JDK Java 7. [En savoir plus](http://www.oracle.com/technetwork/java/javase/eol-135779.html).
* Libre Office 3.5 / 4.3 / 5.x, sauf s&#39;il est intégré dans un autre outil. [En savoir plus](https://wiki.documentfoundation.org/ReleasePlan/Archive#End-of-Life_Releases).

### Moteurs de base de données {#dbe-eol}

Adobe ne prend pas en charge les moteurs de base de données suivants, car ils ont été abandonnés par leur éditeur. Les clients exécutant ces versions doivent effectuer la mise à niveau vers la version la plus récente ou passer à une autre version.

Reportez-vous à [Campaign Classic Matrice](https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix.html) de compatibilité pour accéder au des versions compatibles.

**FEDERATED DATA ACCESS ()**

A compter de la version 19.1 Spring,  Adobe Campaign n’est plus compatible avec les serveurs de l’ suivants.

* Oracle 11G. [En savoir plus](http://www.oracle.com/us/support/library/lifetime-support-technology-069183.pdf).
* PostgreSQL 9.3. En [savoir plus](https://www.postgresql.org/support/versioning).
* MySQL 5.5. &lt;[En savoir plus](http://www.fromdual.com/support-for-mysql-from-oracle).
* DB2 9.5. En [savoir plus](http://www-01.ibm.com/support/docview.wss?uid=swg21168270).
* Teradata 14 - 14.1. En [savoir plus](https://community.teradata.com/t5/Database/Teradata-Database-Product-Life-Cycle/td-p/35068).

Campaign Classic n&#39;est pas compatible avec les serveurs suivants dans Federated Data Access ().

* DB2 UDB 9.5, 9.7. Une version plus récente de DB2 est prise en charge par Federated Data Access (). [En savoir plus](http://www-01.ibm.com/support/docview.wss?uid=swg21168270).
* Oracle 9i, 10G R2. Les versions plus récentes d’Oracle sont prises en charge par Federated Data Access (). [En savoir plus](http://www.oracle.com/us/support/library/lifetime-support-technology-069183.pdf).
* PostgreSQL 8.3, 8.4, 9.0, 9.1, 9.2. Les versions plus récentes de PostgreSQL sont prises en charge par Federated Data Access (). [En savoir plus](https://www.postgresql.org/support/versioning).
* MSSQL 2000, 2005, 2008 R2. Les versions plus récentes de SQL Server sont prises en charge par Federated Data Access (). [En savoir plus](https://support.microsoft.com/en-us/lifecycle/search/1044).
* MySQL 5.1. Les versions plus récentes de MySQL sont prises en charge par Federated Data Access (). [En savoir plus](https://en.wikipedia.org/wiki/InfiniDB).
* InfiniDB a atteint la fin de sa vie. [En savoir plus](https://www.mysql.com/support).
* Teradata 13, 13.1. Les versions plus récentes de Teradata sont prises en charge par Federated Data Access (). [En savoir plus](https://www.info.teradata.com/download.cfm?ItemID=1007255).
* Netezza 6.02, 7.0. Netezza a atteint la fin de sa vie. [En savoir plus](https://en.wikipedia.org/wiki/Netezza).
* AsterData 5.0. AsterData a atteint la fin de sa vie. [En savoir plus](https://en.wikipedia.org/wiki/Aster_Data_Systems).
* Sybase IQ 15.2, 15.4, 15.5 et Sybase ASE 15.0. Les versions plus récentes de Sybase sont prises en charge par Federated Data Access (). [En savoir plus](https://sites.google.com/site/dbatipsandtricks/time-tracker).
* Hadoop via HiveSQL : Hadoop 2.7.3, HiveSQL 1.2.1.  Adobe Campaign Classic prendra toujours en charge les versions répertoriées de Hadoop via HiveSQL via Federated Data Access (le), mais ces versions sont fusionnées avec : HortonWorks (HDP 2.4.X, 2.5.x, 2.6.x) et HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)

**SERVEUR RDBMS**

 Adobe Campaign n’est pas compatible avec les serveurs RDBMS suivants :
* Oracle 10GR2, 11G
* PostgreSQL 9.0 à 9.3
* SQL Server 2005
* MySQL 5.1
* DB2 UDB 9.7
