---
title: Fonctions Campaign Classic obsolètes et supprimées
description: Cette page listes a été abandonnée et a supprimé les fonctionnalités d’Adobe Campaign Classic.
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
ht-degree: 26%

---


# Fonctionnalités obsolètes et supprimées {#deprecated-and-removed-features}

Adobe évalue constamment les fonctionnalités des produits pour identifier celles qui devraient être remplacées par des solutions plus modernes afin d’offrir une plus grande valeur ajoutée, et ce en prenant toujours en compte la rétrocompatibilité Comme Adobe Campaign Classic fonctionne avec des outils tiers, la compatibilité est mise à jour régulièrement, afin de mettre en oeuvre uniquement les versions prises en charge. Les versions qui ne sont plus compatibles avec Adobe Campaign Classic sont répertoriées ci-dessous.

Pour communiquer la suppression ou le remplacement imminent des fonctionnalités Campaign Classic, les règles suivantes s’appliquent :

* L’annonce de l’obsolescence vient en premier. Les fonctionnalités obsolètes sont encore disponibles pour les utilisateurs existants, elles ne seront plus améliorées ni documentées.
* La suppression de fonctionnalités obsolètes aura lieu au plus tôt dans la version suivante. La date de suppression prévue est annoncée sur cette page.

Cette procédure laisse aux clients au moins un cycle de publication pour s’adapter à une nouvelle version ou au successeur d’une fonctionnalité supprimée avant la suppression définitive.

>[!NOTE]
>Les versions et nouvelles fonctionnalités d’Adobe Campaign sont répertoriées dans les [Notes de mise à jour](../../rn/using/latest-release.md).


## Deprecated features {#deprecated-features}

Cette section liste les fonctionnalités qui ont été marquées comme obsolètes avec les dernières versions de Campaign Classic.

En règle générale, les fonctionnalités qui doivent être supprimées dans une version ultérieure sont définies comme étant obsolètes dans un premier temps et une solution de remplacement est fournie. Ces fonctionnalités ne sont plus disponibles pour les nouveaux clients Campaign Classic ou ne doivent pas être utilisées pour une nouvelle mise en oeuvre. Elles sont également supprimées de la documentation du produit.

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
   <td><p>Pour des raisons de sécurité, l’API <em>decryptString</em> n’est plus disponible par défaut pour les nouvelles installations.</p> 
   <p>In the context of a postupgrade to 18.6 (and later), this API is no longer activated, and has been replaced by the <em>decryptPassword</em> function.</p><br> </td>
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
   <td>Archivage basé sur des fichiers<br> </td>
   <td><p>L’archivage des e-mails est désormais disponible par le biais d’une adresse de messagerie Cci dédiée. <a href="../../installation/using/email-archiving.md">En savoir plus</a>.</p> 
   <p><em>Date de suppression de la Cible : Version Campaign 20.2 - juin 2020</em></p><br> </td>
  </tr> 
   <tr> 
   <td>Gestion des pistes<br> </td>
   <td>Leads<br> </td>
   <td><p>Le module de gestion des pistes d'Adobe Campaign Classic a simplifié le processus de création et de gestion de l'ensemble du cycle de vie de la gestion des pistes. Des fonctionnalités similaires peuvent être implémentées via d’autres activités de processus natives et des modifications de modèles de données.</p> 
   <p><em>Date de suppression de la Cible : Version Campaign 20.2 - juin 2020</em></p><br> </td>
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

* Web Server : Apache 2.2. [En savoir plus](https://wiki.centos.org/About/Product)
* Système d’exploitation : CentOS 6. [En savoir plus](https://wiki.centos.org/About/Product)

Reportez-vous à la [matrice de compatibilité](https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix.html) pour effectuer une mise à jour vers une nouvelle version ou passer à un nouveau système.

## Removed features {#removed-features}

Cette section liste les fonctionnalités qui ont été supprimées de Campaign Classic.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Zone - Fonction</strong></td>
   <td><strong>Remplacement</strong></td> 
   <td><strong>Version</strong></td> 
  </tr> 
   <tr> 
   <td>Documentation des API Campaign - fichier jsapi.chm<br> </td>
   <td>Campaign Classic APIs are now available in a dedicated page. If you were using the jsapi.chm file, you should now refer to <a href="https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html">the new online version</a>.</td>
   <td>19.1</td>
  </tr> 
  <tr> 
   <td>Orchestration Campaign - Marketing prédictif</td>
   <td>Une grande partie des capacités de marketing prédictif de Adobe Campaign Classic a été la consommation de modèles prédictifs. Bien que l’activité du processus de marketing prédictif soit supprimée dans une prochaine version, Adobe Campaign continuera à prendre en charge la consommation et l’utilisation de modèles prédictifs provenant de sources externes par le biais d’autres activités de processus.</td>
   <td>18.10</td>
  </tr> 
  <tr> 
   <td>Applications web - Microsites</td>
   <td>Améliorer la sécurité en limitant l'accès aux seuls domaines dédiés sur les fichiers de configuration Adobe Campaign. Vous pouvez toujours utiliser des URL personnalisées dans Campaign en utilisant des alias DNS. <a href="https://helpx.adobe.com/fr/campaign/kb/domain-name-delegation.html">En savoir plus</a>.</td>
   <td>18.10</td>
  </tr> 
  <tr> 
   <td>Notifications Push - Connecteur binaire iOS<br> </td>
   <td>Selon la recommandation d’Apple, Adobe supprimera le connecteur binaire iOS hérité. Le connecteur HTTP/2 plus performant et plus efficace est déjà disponible.</td>
   <td>18.10</td>
  </tr> 
   <tr> 
   <td>canal mobile - Messages MMS et WAP Push</td>
   <td>Les canaux MMS et Wap Push ne sont plus disponibles. À titre de remplacement, vous pouvez tirer parti des <a href="../../delivery/using/sms-channel.md">diffusions</a> SMS <a href="../../delivery/using/about-mobile-app-channel.md">et</a> Push.</td>
   <td>18.4</td>
  </tr> 
   <tr> 
   <td>canal mobile - LINE v1</td>
   <td>Le package LINE Connect n’est plus disponible pour l’installation dans Adobe Campaign Classic. Adobe recommande d’utiliser le nouveau package de Canal LINE pour envoyer des messages LINE. <a href="../../delivery/using/line-channel.md">En savoir plus</a>.</td>
   <td>18.4</td>
  </tr> 
 </tbody> 
</table>

## Fin de compatibilité {#end-of-compatibility}

>[!CAUTION]
>
>Adobe Campaign Classic est compatible avec tous les systèmes et outils répertoriés dans la matrice [de](https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix.html)compatibilité. Lorsque des versions spécifiques de ces systèmes et outils tiers atteignent la fin de vie (EOL) avec leurs créateurs respectifs, Adobe Campaign n’est plus compatible avec ces versions : elles sont déclarées comme obsolètes, puis sont supprimées de notre matrice de compatibilité dans la prochaine version du produit. Assurez-vous que vous utilisez les versions prises en charge de tous les systèmes répertoriés dans la matrice de compatibilité pour éviter tout problème.

### Console client {#client-console-eol}

Adobe Campaign Classic Client Console ne peut plus s’exécuter sur les systèmes suivants, car ils ont été abandonnés par leur éditeur. Les clients exécutant Campaign Client Console sur l’une de ces versions doivent effectuer la mise à niveau vers la version la plus récente avant la date de suppression de la cible. Reportez-vous à la matrice [de](https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix.html)compatibilité.

* Windows Server 2003, 2008, 2008 R2
* Windows XP, Vista

### Systèmes d&#39;exploitation {#o-s-eol}

Depuis la version 19.1, Adobe Campaign n’est plus compatible avec les systèmes d’exploitation suivants.

* Debian 7. [En savoir plus](https://wiki.debian.org/DebianReleases).
* RHEL 6.x. [En savoir plus](https://access.redhat.com/support/policy/updates/errata).
* Windows Server 2008. [En savoir plus](https://support.microsoft.com/en-us/lifecycle/search/1163).
* SLES 11. [En savoir plus](https://www.suse.com/lifecycle).

### Serveurs Web {#web-server-eol}

Depuis la version du printemps 19.1, Adobe Campaign n’est plus compatible avec le serveur Web suivant.

* Microsoft IIS 7. [En savoir plus](https://support.microsoft.com/en-us/lifecycle/search/810).

### Tools {#tools-eol}

Depuis la version du printemps 19.1, Adobe Campaign n’est plus compatible avec les outils suivants.

* JDK Java 7. [En savoir plus](http://www.oracle.com/technetwork/java/javase/eol-135779.html).
* Libre Office 3.5 / 4.3 / 5.x, sauf quand il est intégré dans un autre outil. [En savoir plus](https://wiki.documentfoundation.org/ReleasePlan/Archive#End-of-Life_Releases).

### Moteurs de base de données {#dbe-eol}

Adobe ne prend pas en charge les moteurs de base de données suivants, car ils ont été abandonnés par leur éditeur. Les clients exécutant ces versions doivent effectuer la mise à niveau vers la version la plus récente ou passer à une autre.

Consultez la matrice [de compatibilité](https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix.html) Campaign Classic pour accéder à la liste des versions compatibles.

**FEDERATED DATA ACCESS (FDA)**

Depuis la version du printemps 19.1, Adobe Campaign n’est plus compatible avec les serveurs de FDA suivants.

* Oracle 11G. [En savoir plus](http://www.oracle.com/us/support/library/lifetime-support-technology-069183.pdf).
* PostgreSQL 9.3. [En savoir plus](https://www.postgresql.org/support/versioning).
* MySQL 5.5. &lt;[En savoir plus](http://www.fromdual.com/support-for-mysql-from-oracle).
* DB2 9.5. [En savoir plus](http://www-01.ibm.com/support/docview.wss?uid=swg21168270).
* Teradonnées 14 - 14.1. [En savoir plus](https://community.teradata.com/t5/Database/Teradata-Database-Product-Life-Cycle/td-p/35068).

Campaign Classic n&#39;est pas compatible avec les serveurs suivants dans Federated Data Access (FDA).

* DB2 UDB 9.5, 9.7. Une version plus récente de DB2 est prise en charge via Federated Data Access (FDA). [En savoir plus](http://www-01.ibm.com/support/docview.wss?uid=swg21168270).
* Oracle 9i, 10G R2. Les versions plus récentes d&#39;Oracle sont prises en charge via Federated Data Access (FDA). [En savoir plus](http://www.oracle.com/us/support/library/lifetime-support-technology-069183.pdf).
* PostgreSQL 8.3, 8.4, 9.0, 9.1, 9.2. Les versions plus récentes de PostgreSQL sont prises en charge via Federated Data Access (FDA). [En savoir plus](https://www.postgresql.org/support/versioning).
* MSSQL 2000, 2005, 2008 R2. Les versions plus récentes de SQL Server sont prises en charge via Federated Data Access (FDA). [En savoir plus](https://support.microsoft.com/en-us/lifecycle/search/1044).
* MySQL 5.1. Les versions plus récentes de MySQL sont prises en charge via Federated Data Access (FDA). [En savoir plus](https://en.wikipedia.org/wiki/InfiniDB).
* InfiniDB a atteint la fin de sa vie. [En savoir plus](https://www.mysql.com/support).
* Teradata 13, 13.1. Des versions plus récentes de Teradata sont prises en charge via Federated Data Access (FDA). [En savoir plus](https://www.info.teradata.com/download.cfm?ItemID=1007255).
* Netezza 6.02, 7.0. Netezza atteint la fin de sa vie. [En savoir plus](https://en.wikipedia.org/wiki/Netezza).
* AsterData 5.0. AsterData a atteint la fin de sa vie. [En savoir plus](https://en.wikipedia.org/wiki/Aster_Data_Systems).
* Sybase IQ 15.2, 15.4, 15.5 et Sybase ASE 15.0. Des versions plus récentes de Sybase sont prises en charge par Federated Data Access (FDA). [En savoir plus](https://sites.google.com/site/dbatipsandtricks/time-tracker).
* Hadoop via HiveSQL : Hadoop 2.7.3, HiveSQL 1.2.1. Adobe Campaign Classic continuera à prendre en charge les versions répertoriées de Hadoop via HiveSQL via Federated Data Access (FDA), mais ces versions sont fusionnées avec : HortonWorks (HDP 2.4.X, 2.5.x, 2.6.x) et HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)

**SERVEUR RDBMS**

Adobe Campaign n&#39;est pas compatible avec les serveurs RDBMS suivants :
* Oracle 10GR2, 11G
* PostgreSQL 9.0 à 9.3
* SQL Server 2005
* MySQL 5.1
* DB2 UDB 9.7
