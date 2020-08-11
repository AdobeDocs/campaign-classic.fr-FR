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
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 63f07746d39fff22a98b3cd4ab7f2294da778ab3
workflow-type: tm+mt
source-wordcount: '1468'
ht-degree: 100%

---


# Fonctionnalités obsolètes et supprimées {#deprecated-and-removed-features}

Adobe évalue constamment les fonctionnalités des produits pour identifier celles qui devraient être remplacées par des solutions plus modernes afin d’offrir une plus grande valeur ajoutée, et ce en prenant toujours en compte la rétrocompatibilité Comme Adobe Campaign Classic fonctionne avec des outils tiers, la compatibilité est régulièrement mise à jour pour ne mettre en œuvre que des versions prises en charge. Les versions devenues incompatibles avec Adobe Campaign Classic sont répertoriées ci-dessous et dans la [matrice de compatibilité](https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix.html).

Lors de l’annonce de la suppression ou du remplacement imminent de fonctionnalités de Campaign Classic, les règles suivantes s’appliquent :

* L’annonce de l’obsolescence vient en premier. Les fonctionnalités obsolètes sont encore disponibles et prises en charge pour les utilisateurs existants, mais elles ne seront plus améliorées ni documentées.
* La suppression de fonctionnalités obsolètes aura lieu au plus tôt dans la version suivante. La date de suppression prévue est annoncée sur cette page.

Cette procédure laisse aux clients au moins un cycle de publication pour s’adapter à une nouvelle version ou au successeur d’une fonctionnalité supprimée avant la suppression définitive.

>[!NOTE]
>Les versions et nouvelles fonctionnalités d’Adobe Campaign sont répertoriées dans les [Notes de mise à jour](../../rn/using/latest-release.md).

## Fonctionnalités obsolètes {#deprecated-features}

Cette section répertorie les fonctions et fonctionnalités qui ont été désignées comme étant obsolètes dans les dernières versions de Campaign Classic.

En règle générale, les fonctionnalités qui doivent être supprimées dans une version ultérieure sont définies comme étant obsolètes dans un premier temps. Ces fonctions et fonctionnalités ne sont plus disponibles pour les nouveaux clients de Campaign Classic ou ne doivent pas être utilisées dans le cadre d’une nouvelle implémentation. Elles sont également supprimées de la documentation du produit.

Il est conseillé aux clients d’évaluer dans quelle mesure ils utilisent la fonctionnalité dans leur déploiement actuel et d’envisager de modifier leur implémentation. Référez-vous aux dates de suppression prévues pour planifier les mises à jour de votre environnement et de vos projets en conséquence.

<table> 
 <tbody> 
   <tr>
   <td><strong>Fonctionnalité</strong></td>
   <td><strong>Remplacement</strong></td> 
  </tr>
   <tr>
  <td>Connecteurs SMS<br></td>
  <td><p> À compter de la version 20.2, les connecteurs SMS suivants sont obsolètes.<p>
   <ul>
   <li>NetSize</li>
   <li>SMPP générique (SMPP version 3.4 avec prise en charge du mode binaire)</li>
   <li>Sybase365 (SAP SMS 365)</li>
   <li>CLX Communications</li>
   <li>Tele2</li>
   <li>O2</li>
   <li>iOS</li>
   </ul>
  <p>Si vous utilisez l’un de ces connecteurs, vous devez adapter votre implémentation en conséquence. <a href="../../delivery/using/sms-channel.md">En savoir plus</a></p> 
  <p>Découvrez comment effectuer la migration des anciens connecteurs dans <a href="https://helpx.adobe.com/fr/campaign/kb/sms-connector.html">cette note technique</a>.</p>
  <p><em>Date de suppression prévue : 2021</em></p>
  </td> 
 </tr>
  <tr>  
   <td>Canal fax<br></td>
   <td><p>À compter de la version 20.2, le canal fax est obsolète.</p> 
   <p>Si vous utilisez ce canal, vous devez adapter votre implémentation en conséquence. <a href="../../delivery/using/steps-about-delivery-creation-steps.md">En savoir plus</a> sur les canaux de Campaign.</p>
   <p><em>Date de suppression prévue : 2021</em></p></td>
  </tr>
 </tbody> 
</table>

## Fonctionnalités supprimées {#removed-features}

Cette section répertorie les fonctionnalités supprimées de Campaign Classic.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Domaine - Fonctionnalité</strong></td>
   <td><strong>Remplacement</strong></td> 
  </tr> 
   <tr> 
   <td>Archivage des emails basé sur les fichiers<br></td>
   <td><p>Depuis la version 20.2 de Campaign, l’archivage des emails basé sur les fichiers n’est plus disponible. L’archivage des emails est désormais disponible par le biais d’une adresse de messagerie Cci dédiée. <a href="../../installation/using/email-archiving.md">En savoir plus</a></p></td>
  </tr> 
   <tr> 
   <td>Gestion des leads</td>
   <td><p>À compter de la version 20.2 de Campaign, le module Gestion des leads n’est plus disponible. Il est possible de mettre en œuvre des fonctionnalités similaires à l’aide d’autres activités de workflow natives et des modifications de modèles de données.</p></td>
   </tr>
   <tr>
   <td>Documentation des API de Campaign - fichier jsapi.chm</td>
   <td>Depuis la version 19.1 de Campaign, les API de Campaign Classic sont disponibles dans une page dédiée. Si vous utilisiez l’ancien fichier jsapi.chm, vous devez maintenant vous référer à <a href="https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html">la nouvelle version en ligne</a>.</td>
  </tr> 
  <tr> 
   <td>Orchestration de campagnes - Marketing prédictif</td>
   <td>À compter de la version 18.10 de Campaign, les fonctionnalités de marketing prédictif ne sont plus disponibles.</td>
  </tr> 
  <tr> 
   <td>Applications web - Microsites</td>
   <td>À compter de la version 18.10 de Campaign, les microsites ne sont plus disponibles. Vous pouvez améliorer la sécurité en limitant l’accès aux seuls domaines dédiés des fichiers de configuration d’Adobe Campaign et utiliser des URL personnalisées dans Campaign à l’aide d’alias DNS. <a href="https://helpx.adobe.com/fr/campaign/kb/domain-name-delegation.html">En savoir plus</a></td>
  </tr> 
  <tr> 
   <td>Notifications push - Connecteur binaire iOS</td>
   <td>Selon la recommandation d’Apple, Adobe a supprimé l’ancien connecteur binaire iOS à compter de la version 18.10 de Campaign. Le connecteur HTTP/2, plus performant et plus efficace, est déjà disponible.</td>
  </tr> 
  <tr> 
   <td>API decryptString</td>
   <td><p>À compter de la version 18.6 de Campaign, pour des raisons de sécurité, l’API <em>decryptString</em> n’est plus disponible par défaut pour les nouvelles installations.</p> 
   <p>Dans le contexte d’un postupgrade vers la version 18.6 (et versions ultérieures), cette API n’est plus activée et a été remplacée par la fonction <em>decryptPassword. </em> <a href="https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/f-decryptPassword.html?hl=decrypt">En savoir plus</a></p></td>
  </tr> 
   <tr> 
   <td>Canal mobile - Messages MMS et WAP Push</td>
   <td>À compter de la version 18.4 de Campaign, les canaux MMS et Wap Push ne sont plus disponibles. À titre de remplacement, vous pouvez tirer parti des diffusions <a href="../../delivery/using/sms-channel.md">SMS</a> et <a href="../../delivery/using/about-mobile-app-channel.md">Push</a>.</td>
  </tr> 
   <tr> 
   <td>Canal mobile - LINE v1</td>
   <td>À compter de la version 18.4 de Campaign, le package LINE Connect n’est plus disponible. Adobe recommande d’utiliser le nouveau package Canal LINE pour le remplacer. <a href="../../delivery/using/line-channel.md">En savoir plus</a></td>
  </tr> 
 </tbody> 
</table>

## Compatibilité obsolète {#deprecated-compatibility}

Les systèmes suivants sont désormais obsolètes pour Campaign Classic : Reportez-vous à la [matrice de compatibilité](https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix.html) pour effectuer une mise à jour vers une nouvelle version ou passer à un nouveau système avant la fin de la compatibilité.

### Adobe Campaign version 20.2 {#compat-20-2-release}

À compter de la version 20.2, le système suivant est obsolète pour Campaign Classic. La compatibilité prendra fin avec la version 20.3 - Septembre 2020.

* Console cliente : Windows 7
* Anciens connecteurs SMS (voir la section Fonctions obsolètes ci-dessous)

### Adobe Campaign version 19.2 {#compat-19-2-release}

À compter de la version 19.2, les systèmes d’exploitation suivants sont obsolètes pour Campaign Classic. La compatibilité ne sera plus assurée à partir de la fin de l’année 2020.

* Serveur Web : Apache 2.2.
* Système d’exploitation : CentOS 6.

Reportez-vous à la [matrice de compatibilité](https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix.html) pour effectuer une mise à jour vers une nouvelle version ou passer à un nouveau système.

## Fin de compatibilité {#end-of-compatibility}

>[!CAUTION]
>
>Adobe Campaign Classic est compatible avec tous les systèmes et outils répertoriés dans la [matrice de compatibilité](https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix.html). Lorsque des versions spécifiques de ces systèmes et outils tiers arrivent en fin de vie (EOL) avec leurs créateurs respectifs, Adobe Campaign n’est plus compatible avec celles-ci : elles sont déclarées obsolètes, puis supprimées de la matrice de compatibilité pour la version suivante du produit. Pour éviter tout problème, vérifiez que vous disposez des versions prises en charge des systèmes répertoriés dans la matrice de compatibilité.

### Console cliente {#client-console-eol}

La console cliente d’Adobe Campaign Classic ne peut plus s’exécuter sur les systèmes suivants, car ils ont été abandonnés par leur éditeur. Les clients qui utilisent la console cliente de Campaign sur l’une de ces versions doivent effectuer la mise à niveau vers la version la plus récente avant la date de suppression prévue. Reportez-vous à la [matrice de compatibilité](https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix.html).

* Windows Server 2003, 2008, 2008 R2
* Windows XP, Vista

>[!NOTE]
>À compter de la version 20.1 de Campaign, la console cliente 32 bits de Campaign Classic n’est plus compatible avec les dernières versions de Campaign. Vous devez utiliser la console cliente 64 bits.


### Systèmes d’exploitation {#o-s-eol}

Depuis la version 19.1, Adobe Campaign n’est plus compatible avec les systèmes d’exploitation ci-après.

* Debian 7. [En savoir plus](https://wiki.debian.org/DebianReleases)
* RHEL 6.x. [En savoir plus](https://access.redhat.com/support/policy/updates/errata)
* Windows Server 2008. [En savoir plus](https://support.microsoft.com/en-us/lifecycle/search/1163)
* SLES 11. [En savoir plus](https://www.suse.com/lifecycle)

### Serveurs web {#web-server-eol}

Depuis la version 19.1 du printemps, Adobe Campaign n’est plus compatible avec les serveurs web ci-après.

* Microsoft IIS 7. [En savoir plus](https://support.microsoft.com/fr-fr/lifecycle/search/810)

### Outils {#tools-eol}

Depuis la version 19.1 du printemps, Adobe Campaign n’est plus compatible avec les outils ci-après.

* Java JDK 7. [En savoir plus](http://www.oracle.com/technetwork/java/javase/eol-135779.html)
* Libre Office 3.5 / 4.3 / 5.x, sauf intégré dans un autre outil. [En savoir plus](https://wiki.documentfoundation.org/ReleasePlan/Archive#End-of-Life_Releases)

### Moteurs de base de données {#dbe-eol}

Adobe ne prend pas en charge les moteurs de base de données ci-après, car ils ont été abandonnés par leur éditeur. Les clients utilisant ces versions doivent effectuer la mise à niveau vers la version la plus récente ou passer à une autre.

Consultez la [matrice de compatibilité de Campaign Classic](https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix.html) pour accéder à la liste des versions compatibles.

**FEDERATED DATA ACCESS (FDA)**

Depuis la version 19.1 du printemps, Adobe Campaign n’est plus compatible avec les serveurs FDA ci-après.

* PostgreSQL 9.3. [En savoir plus](https://www.postgresql.org/support/versioning)
* MySQL 5.5. [En savoir plus](http://www.fromdual.com/support-for-mysql-from-oracle)
* DB2 9.5. [En savoir plus](http://www-01.ibm.com/support/docview.wss?uid=swg21168270)
* Teradata 14 – 14.1. [En savoir plus](https://community.teradata.com/t5/Database/Teradata-Database-Product-Life-Cycle/td-p/35068)

Campaign Classic n’est pas compatible avec les serveurs ci-après dans Federated Data Access (FDA).

* DB2 UDB 9.5, 9.7. Une version plus récente de DB2 est prise en charge via Federated Data Access (FDA). [En savoir plus](http://www-01.ibm.com/support/docview.wss?uid=swg21168270)
* Oracle 9i, 10G R2. Les versions plus récentes d’Oracle sont prises en charge via Federated Data Access (FDA). [En savoir plus](http://www.oracle.com/us/support/library/lifetime-support-technology-069183.pdf)
* PostgreSQL 8.3, 8.4, 9.0, 9.1, 9.2. Les versions plus récentes de PostgreSQL sont prises en charge via Federated Data Access (FDA). [En savoir plus](https://www.postgresql.org/support/versioning)
* MSSQL 2000, 2005, 2008 R2. Les versions plus récentes de SQL Server sont prises en charge via Federated Data Access (FDA). [En savoir plus](https://support.microsoft.com/en-us/lifecycle/search/1044)
* MySQL 5.1. Les versions plus récentes de MySQL sont prises en charge via Federated Data Access (FDA). [En savoir plus](https://en.wikipedia.org/wiki/InfiniDB)
* InfiniDB a atteint sa fin de vie. [En savoir plus](https://www.mysql.com/support)
* Teradata 13, 13.1. Des versions plus récentes de Teradata sont prises en charge via Federated Data Access (FDA). [En savoir plus](https://www.info.teradata.com/download.cfm?ItemID=1007255)
* Netezza 6.02, 7.0. Netezza a atteint sa fin de vie. [En savoir plus](https://en.wikipedia.org/wiki/Netezza)
* AsterData 5.0. AsterData a atteint sa fin de vie. [En savoir plus](https://en.wikipedia.org/wiki/Aster_Data_Systems)
* Sybase IQ 15.2, 15.4, 15.5 et Sybase ASE 15.0. Des versions plus récentes de Sybase sont prises en charge par Federated Data Access (FDA). [En savoir plus](https://sites.google.com/site/dbatipsandtricks/time-tracker)
* Hadoop via HiveSQL : Hadoop 2.7.3, HiveSQL 1.2.1. Adobe Campaign Classic continuera à prendre en charge les versions répertoriées de Hadoop via HiveSQL par le biais de Federated Data Access (FDA), mais ces versions sont fusionnées avec : HortonWorks (HDP 2.4.X, 2.5.x, 2.6.x) et HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)

**SERVEUR SGBDR**

Adobe Campaign n’est pas compatible avec les serveurs SGBDR suivants :
* Oracle 10GR2
* PostgreSQL 9.0 à 9.3
* SQL Server 2005
* MySQL 5.1
* DB2 UDB 9.7
