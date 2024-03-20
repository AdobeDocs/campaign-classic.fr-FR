---
product: campaign
title: Fonctionnalités obsolètes et supprimées de Campaign Classic
description: Cette page répertorie les fonctionnalités obsolètes et supprimées d’Adobe Campaign Classic
feature: Release Notes
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
role: User
level: Beginner
exl-id: d60d67de-6618-4f3b-be4a-ad7633ab5645
source-git-commit: f3dc9d56c693f334923d627a28a9e45b92b1c0c3
workflow-type: ht
source-wordcount: '1558'
ht-degree: 100%

---

# Fonctionnalités obsolètes et supprimées {#deprecated-and-removed-features}



Adobe évalue constamment les fonctionnalités des produits pour identifier celles qui devraient être remplacées par des solutions plus modernes afin d’offrir une plus grande valeur ajoutée, et ce en prenant toujours en compte la rétrocompatibilité Comme Adobe Campaign Classic fonctionne avec des outils tiers, la compatibilité est régulièrement mise à jour pour ne mettre en œuvre que des versions prises en charge. Les versions devenues incompatibles avec Adobe Campaign Classic sont répertoriées ci-dessous et dans la [matrice de compatibilité](../../rn/using/compatibility-matrix.md).

Lors de l’annonce de la suppression ou du remplacement imminent de fonctionnalités de Campaign Classic, les règles suivantes s’appliquent :

* L’annonce de l’obsolescence vient en premier. Les fonctionnalités obsolètes sont encore disponibles et prises en charge pour les utilisateurs existants, mais elles ne seront plus améliorées ni documentées.
* La suppression de fonctionnalités obsolètes aura lieu au plus tôt dans la version suivante. La date de suppression prévue est annoncée sur cette page.

Cette procédure laisse aux clients au moins un cycle de publication pour s’adapter à une nouvelle version ou au successeur d’une fonctionnalité supprimée avant la suppression définitive.

>[!NOTE]
>Les versions et nouvelles fonctionnalités d’Adobe Campaign sont répertoriées dans les [Notes de mise à jour](../../rn/using/latest-release.md).

## Fonctionnalités obsolètes {#deprecated-features}

Cette section répertorie les fonctions et fonctionnalités qui ont été désignées comme étant obsolètes dans les dernières versions de Campaign Classic.

En règle générale, les fonctionnalités qui doivent être supprimées dans une version ultérieure sont définies comme étant obsolètes dans un premier temps. Ces fonctions et fonctionnalités ne sont plus disponibles pour les nouveaux clients de Campaign Classic ou ne doivent pas être utilisées dans le cadre d’une nouvelle implémentation. Elles sont également supprimées de la documentation du produit.

Il est conseillé aux clients d’évaluer dans quelle mesure ils utilisent la fonctionnalité dans leur déploiement actuel et d’envisager de modifier leur implémentation. Référez-vous aux dates de suppression prévues pour planifier les mises à jour de votre environnement et de vos projets en conséquence.

<table> 
 <tbody> 
   <tr>
   <td><strong>Fonctionnalité</strong></td>
   <td><strong>Détails</strong></td>
  </tr>
<tr>
 <td>Marketing des médias sociaux avec Facebook</td>
 <td>Le marketing social avec Facebook est désormais obsolète. Vous pouvez utiliser l’intégration de X (anciennement Twitter) pour publier sur les médias sociaux ou utiliser Adobe pour créer un canal personnalisé.
 <p></p>
  <!--p>Target removal date: End of 2023</p-->
  </td>
</tr>
<tr>
 <td>Connecteur ACS</td>
 <td>Le connecteur ACS (offre Prime) est désormais obsolète. Vous pouvez utiliser les fonctionnalités d’exportation/importation de Campaign pour extraire et injecter des données dans les deux produits.<p></p>
  <!--p>Target removal date: End of 2023</p-->
  </td>
</tr>
 </tbody> 
</table>

## Fonctionnalités supprimées {#removed-features}

Cette section répertorie les fonctionnalités supprimées de Campaign Classic.

<table> 
 <tbody>
  <tr> 
   <td><strong>Fonctionnalité</strong></td>
   <td><strong>Détails</strong></td>
  <tr>  
      <tr>
  <td>Adobe Analytics - Data Connector<br></td>
   <td><p>Le Adobe Analytics Data Connector a été supprimé le 17 août 2022. Il avait été abandonné avec la version 21.1.3 de Campaign.</p>
   <p>Si vous utilisez ce connecteur, vous devez adapter votre implémentation en conséquence. <a href="../../platform/using/adobe-analytics-connector.md">En savoir plus</a></p>
  </td>
 </tr>
    <tr>
  <td>Rapport de surveillance de la délivrabilité technique<br></td>
   <td><p>Le rapport de surveillance de la délivrabilité technique n’est plus disponible. Il avait été abandonné avec la version 21.1.3 de Campaign.</p>
   <!--p>If needed, you can receive this report daily by email until the feature removal date. To request it, open a specific <a href="https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html">Support Case</a> and specify the name of the instance and the email address(es) to send the report to.</p--> 
  </td>
 </tr>
  <tr>
  <td>Authentification OAuth (OAuth et JWT)<br></td>
  <td><p> L’authentification de l’intégration Triggers basée à l’origine sur la configuration de l’authentification oAUTH pour accéder au pipeline a été modifiée et déplacée vers Adobe I/O. Ce mode d’authentification est devenu obsolète à partir de la version 20.3 de Campaign.<p>
  <p>Si vous utilisiez l’intégration Triggers, découvrez comment adapter votre implémentation <a href="../../integrations/using/configuring-adobe-io.md">sur cette page</a>.</p> 
  <p>Pour plus d’informations sur l’abandon de l’authentification OAuth, consultez cette <a href="https://github.com/AdobeDocs/analytics-1.4-apis/blob/master/docs/APIEOL.md">page</a></p> 
  <!--p><em>Target removal date: October 20, 2021. Hosted environments benefit from an extension until May 25, 2022. </em></p-->
  </td>
  </tr>
   <td>Reporting<br></td>
   <td><p>Après la fin de vie de Flash Player d’Adobe, le rapport d’évaluation et le moteur de rendu des graphiques ne sont plus disponibles. <a href="../../reporting/using/creating-a-new-report.md">Apprenez-en davantage</a></p>
  </tr>
  <tr>  
   <td>Canal fax<br></td>
   <td><p>À compter de la version 21.1.3 de Campaign, le canal Fax n’est plus disponible. <a href="../../delivery/using/steps-about-delivery-creation-steps.md">En savoir plus</a></p>
  </tr>
  <tr>
  <td>Domaine Demdex<br></td>
  <td><p> Depuis la version Campaign 21.1.3, le domaine demdex utilisé pour importer et exporter des audiences vers Adobe Experience Cloud n’est plus disponible. <a href="../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md">En savoir plus</a></p> 
  </td>
  </tr>
   <tr> 
   <td>Authentification Windows NT<br></td>
   <td><p>À compter de la version 20.3 de Campaign, l’authentification Windows NT a été supprimée des méthodes d’authentification disponibles lors de la configuration d’une nouvelle base de données avec Microsoft SQL Server. <a href="../../installation/using/creating-and-configuring-the-database.md#step-1---selecting-the-database-engine">En savoir plus</a></p></td>
  </tr>
   <tr> 
   <td>Archivage des emails basé sur les fichiers<br></td>
   <td><p>Depuis la version 20.2 de Campaign, l’archivage des emails basé sur les fichiers n’est plus disponible. L’archivage des emails est désormais disponible par le biais d’une adresse de messagerie Cci dédiée. <a href="../../installation/using/email-archiving.md">En savoir plus</a></p></td>
  </tr> 
   <tr> 
   <td>Gestion des prospects</td>
   <td><p>À compter de la version 20.2 de Campaign, le module Gestion des leads n’est plus disponible. Il est possible de mettre en œuvre des fonctionnalités similaires à l’aide d’autres activités de workflow natives et des modifications de modèles de données.</p></td>
   </tr>
   <tr>
   <td>Documentation des API de Campaign - fichier jsapi.chm</td>
   <td>Depuis la version 19.1 de Campaign, les API de Campaign Classic sont disponibles dans une page dédiée. Si vous utilisiez l’ancien fichier jsapi.chm, vous devez maintenant vous référer à <a href="https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=fr">la nouvelle version en ligne</a>.</td>
  </tr> 
  <tr> 
   <td>Orchestration de campagnes - Marketing prédictif</td>
   <td>À compter de la version 18.10 de Campaign, les fonctionnalités de marketing prédictif ne sont plus disponibles.</td>
  </tr> 
  <tr> 
   <td>Applications Web - Microsites</td>
   <td>À compter de la version 18.10 de Campaign, les microsites ne sont plus disponibles. Vous pouvez améliorer la sécurité en limitant lʼaccès aux seuls domaines dédiés des fichiers de configuration dʼAdobe Campaign et utiliser des URL personnalisées dans Campaign à lʼaide dʼalias DNS.</td>
  </tr> 
  <tr> 
   <td>Notifications push - Connecteur binaire iOS</td>
   <td>Selon la recommandation d’Apple, Adobe a supprimé l’ancien connecteur binaire iOS à compter de la version 18.10 de Campaign. Le connecteur HTTP/2, plus performant et plus efficace, est déjà disponible.</td>
  </tr> 
  <tr> 
   <td>API decryptString</td>
   <td><p>À compter de la version 18.6 de Campaign, pour des raisons de sécurité, l’API <em>decryptString</em> n’est plus disponible par défaut pour les nouvelles installations.</p> 
   <p>Dans le contexte d’un postupgrade vers la version 18.6 (et versions ultérieures), cette API n’est plus activée et a été remplacée par la fonction <em>decryptPassword. </em> <a href="https://experienceleague.adobe.com/developer/campaign-api/api/f-decryptPassword.html?hl=decrypt">En savoir plus</a></p></td>
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

<!--## Deprecated compatibility {#deprecated-compatibility}

The following systems are deprecated for Campaign Classic. Please refer to the [Compatibility matrix](../../rn/using/compatibility-matrix.md) to upgrade to a newer version or move to a new system before the compatibility ends.-->

## Fin de compatibilité {#end-of-compatibility}

>[!CAUTION]
>
>Adobe Campaign Classic est compatible avec tous les systèmes et outils répertoriés dans la [matrice de compatibilité](../../rn/using/compatibility-matrix.md). Lorsque des versions spécifiques de ces systèmes et outils tiers arrivent en fin de vie (EOL) avec leurs créateurs respectifs, Adobe Campaign n’est plus compatible avec celles-ci : elles sont déclarées obsolètes, puis supprimées de la matrice de compatibilité pour la version suivante du produit. Pour éviter tout problème, vérifiez que vous disposez des versions prises en charge des systèmes répertoriés dans la matrice de compatibilité.

### Console cliente {#client-console-eol}

La console cliente d’Adobe Campaign Classic ne peut plus s’exécuter sur les systèmes suivants, car ils ont été abandonnés par leur éditeur. Les clients qui utilisent la console cliente de Campaign sur l’une de ces versions doivent effectuer la mise à niveau vers la version la plus récente avant la date de suppression prévue. Reportez-vous à la [matrice de compatibilité](../../rn/using/compatibility-matrix.md).

* Windows Server 2003, 2008, 2008 R2
* Windows 7, XP, Vista

>[!NOTE]
>À compter de la version 20.1 de Campaign, la console cliente 32 bits de Campaign Classic n’est plus compatible avec les dernières versions de Campaign. Vous devez utiliser la console cliente 64 bits.

### Systèmes d’exploitation {#o-s-eol}


* À partir de la version 22.1, Adobe Campaign n’est plus compatible avec CentOs 8.x (64 bits). CentOS Linux 8 a atteint sa fin de vie (EOL) le 31 décembre 2021. [En savoir plus](https://www.centos.org/centos-linux-eol/).

  Si vous utilisiez ce système d’exploitation, adaptez votre implémentation en conséquence. CentOS 7.x (64 bits) et RHEL 8.x/7.x (64 bits) sont toujours pris en charge.

* À partir de la version 21.1.3, Adobe Campaign n’est plus compatible avec Debian 8.

* Depuis la version 19.1, Adobe Campaign n’est plus compatible avec les systèmes d’exploitation ci-après.

   * CentOS 6. [En savoir plus](https://wiki.centos.org/Download)
   * Debian 7. [En savoir plus](https://wiki.debian.org/DebianReleases)
   * RHEL 6.x. [En savoir plus](https://access.redhat.com/support/policy/updates/errata)
   * Windows Server 2008. [En savoir plus](https://support.microsoft.com/en-us/lifecycle/search/1163)
   * SLES 11. [En savoir plus](https://www.suse.com/lifecycle)

### Serveurs web {#web-server-eol}

Depuis la version 19.1 du printemps, Adobe Campaign n’est plus compatible avec les serveurs web ci-après.

* Apache 2.2. [En savoir plus](https://httpd.apache.org/)
* Microsoft IIS 7. [En savoir plus](https://support.microsoft.com/fr-fr/lifecycle/search/810)

### Outils {#tools-eol}

Depuis la version 19.1 du printemps, Adobe Campaign n’est plus compatible avec les outils ci-après.

* Java JDK 7. [En savoir plus](https://www.oracle.com/technetwork/java/javase/eol-135779.html)
* Libre Office 3.5 / 4.3 / 5.x, sauf si intégré dans un autre outil. [En savoir plus](https://wiki.documentfoundation.org/ReleasePlan/Archive#End-of-Life_Releases)

### Moteurs de base de données {#dbe-eol}

Adobe ne prend pas en charge les moteurs de base de données ci-après, car ils ont été abandonnés par leur éditeur. Les clients utilisant ces versions doivent effectuer la mise à niveau vers la version la plus récente ou passer à une autre.

Consultez la [matrice de compatibilité de Campaign ](../../rn/using/compatibility-matrix.md) pour accéder à la liste des versions compatibles.

**FEDERATED DATA ACCESS (FDA)**

À compter de la version 20.2, Adobe Campaign n’est plus compatible avec les serveurs FDA suivants :

* DB2 UDB 10.5

Depuis la version 19.1 du printemps, Adobe Campaign n’est plus compatible avec les serveurs FDA ci-après:

* PostgreSQL 9.3.
* MySQL 5.5.
* DB2 9.5.
* Teradata 14 – 14.1.

Campaign Classic n’est pas compatible avec les serveurs ci-après dans Federated Data Access (FDA). Veuillez utiliser des versions ou des systèmes plus récents.

* DB2 UDB 9.5, 9.7.
* Oracle 9i, 10G R2.
* Les versions de PostgreSQL jusqu&#39;à la version 9.6 ont atteint la fin de vie.
* MSSQL 2000, 2005, 2008 R2.
* MySQL 5.1.
* InfiniDB a atteint sa fin de vie.
* Teradata 13, 13.1.
* Netezza 6.02, 7.0. Netezza a atteint sa fin de vie.
* AsterData 5.0. AsterData a atteint sa fin de vie.
* Sybase IQ 15.2, 15.4, 15.5 et Sybase ASE 15.0.
* Hadoop via HiveSQL : Hadoop 2.7.3, HiveSQL 1.2.1. Adobe Campaign Classic prend encore en charge les versions répertoriées de Hadoop via HiveSQL par le biais de Federated Data Access (FDA), mais ces versions sont fusionnées avec : HortonWorks (HDP 2.4.X, 2.5.x, 2.6.x) et HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6).

**SERVEUR SGBDR**

Depuis la version 19.1 du printemps, Adobe Campaign n’est plus compatible avec les serveurs de systèmes de gestion de base de données relationnelle (SGBDR) ci-après:

* Oracle 10GR2
* PostgreSQL 9.0 à 9.3
* SQL Server 2005
* MySQL 5.1
* DB2 UDB 9.7

Les versions de PostgreSQL jusqu&#39;à la version 9.6 ont atteint la fin de vie. Elles ne sont donc pas prises en charge par Adobe Campaign.

### Connecteurs SMS {#sms-eol}

À compter de la version 20.2, les connecteurs SMS suivants sont obsolètes. Adobe Campaign n’est pas compatible avec :

* SMPP générique (SMPP version 3.4 avec prise en charge du mode binaire)
* Sybase365 (SAP SMS 365)
* CLX Communications
* Tele2
* O2
* iOS

### Connecteurs CRM {#crm-connectors}

À compter de la version 21.1 de Campaign, les connecteurs CRM suivants ne sont plus compatibles avec Campaign :

* API Soap - On-premise : 2007, 2015, 2016
* API Soap - Online : 2015, 2016
* API Web - Microsoft Dynamics CRM 2016
* API Web - Microsoft Dynamics CRM 2016 Update 1
* API Oracle On Demand
