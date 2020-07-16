---
title: Matrice de compatibilité
description: Matrice de compatibilité
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 5e8598fd445f6e2ebd891af1e15c07eb836cd647
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 46%

---


# Matrice de compatibilité{#compatibility-matrix}

This document lists all systems and components supported for the latest build of **Adobe Campaign Classic (v6.11 and v7)**. Les produits et versions ne faisant pas partie de cette liste ne sont pas compatibles avec Adobe Campaign.

## Remarques importantes{#important-notes}

Cette matrice est régulièrement mise à jour avec les nouveaux éléments pris en charge ajoutés et les éléments déconseillés supprimés.

Sauf mention contraire, toutes les versions mineures sont prises en charge.

Adobe Campaign Classic est compatible avec tous les systèmes et outils répertoriés dans cette page. À mesure que des versions spécifiques de ces systèmes et outils tiers atteignent la fin de vie (fin de vie) avec leurs créateurs respectifs, l&#39;Adobe Campaign ne sera plus compatible avec ces versions et sera supprimé de notre matrice de compatibilité dans la prochaine version du produit. Pour éviter tout problème, vérifiez que vous disposez des versions prises en charge des systèmes répertoriés dans la matrice de compatibilité.

Pour en savoir plus sur les éléments obsolètes, consultez [cette page](../../rn/using/deprecated-features.md).

## Systèmes d’exploitation{#OperatingSystems}

<table> 
<tbody> 
<tr> 
<td>CentOs</td>
<td>
<p>7.x (64 bits)</p>
</td>
</tr>
<tr>
<td>Debian</td>
<td>
<p>8 (64 bits)</p>
<p>9 (64 bits)</p>
<p>10 (64 bits)</p>
</td>
</tr>
<tr>
<td>RHEL</td>
<td>
<p>7.x (64 bits)</p>
<p><strong>Important :</strong> Si vous utilisez RHEL, vous devez être prêt à désactiver SELinux ou à demander à vos architectes d'écrire des règles SELinux personnalisées pour vérifier qu'un SELinux activé ne pose pas de problème avec les opérations Campaign.</p>
</td>
</tr>
<tr>
<td>Windows Server </td>
<td>
<p>2012</p>
<p>2012 R2</p>
<p>2016</p>
</td>
</tr>
</tbody>
</table>

## Web Servers{#WebServers}

<table>
<tbody>
<tr>
<td>Microsoft IIS </td>
<td>
<p>8.0 sur Windows Server 2012 - Windows 8</p>
<p>8.5 sous Windows Server 2012 R2</p>
<p>10.0 sous Windows Server 2016</p>
</td>
</tr>
<tr>
<td>Apache</td>
<td>
<p>2.4 pour RHEL7 - CentOS 7, Debian 8/9, Windows (64 bits)</p>
</td>
</tr>
</tbody>
</table>

## Outils{#Tools}

<table>
<tbody>
<tr>
<td>Kit de développement Java (JDK)</td>
<td>
<p>8</p>
<p>9</p>
<p>L'application a été validée pour le JDK développé par Oracle ainsi que pour OpenJDK.</p>
</td>
</tr>
<tr>
<td>Libre Office</td>
<td>
<p>6 (et versions antérieures si elles sont incorporées dans votre système)</p>
</td>
</tr>
<tr>
<td>SpamAssassin</td>
<td>
<p>3.4.x</p>
</td>
</tr>
</tbody>
</table>

## Pilotes RDBMS{#RDBMSdrivers}

Les pilotes RDBMS suivants sont pris en charge :

* Oracle SQL*Net 11

* Oracle SQL*Net 12

* PostgreSQL (libpq)

* SQLServer

* DB2 (pilote ODBC)


>[!NOTE]
>
>Le pilote RDBMS doit correspondre à la version du serveur RDBMS.

## Serveurs RDBMS{#RDBMSservers}

<table>
<tbody>
<tr>
<td>Oracle</td>
<td>
<p>11g R2</p>
<p>12c</p>
<p>18c</p>
<p>19c</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>9.4.x</p>
<p>9.5.x</p>
<p>9.6.x</p>
<p>10.x</p>
<p>11.x</p>
<p>Remarque : vous pouvez également utiliser Amazon RDS pour PostgreSQL avec les versions indiquées ci-dessus.</p>
</td>
</tr>
<tr>
<td>SQL Server </td>
<td>
<p>2012 - SP1 et SP2</p>
<p>2014</p>
<p>2016</p>
<p>2017</p>
<p>Avertissement : Microsoft SQL Server n'est pas pris en charge en tant que base de données principale lorsque le serveur Campaign est en cours d'exécution sous Linux. Reportez-vous au guide <a href="https://docs.campaign.adobe.com/doc/AC/en/INS_Prerequisites_and_recommendations__Database.html#Microsoft_SQL_Server">d'</a>installation.</p>
</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>PostgreSQL est le serveur de base de données par défaut pour les environnements hébergés.

## Connecteurs CRM{#CRMconnectors}

<table>
<tbody>
<tr>
<td>API du connecteur Salesforce</td>
<td>
<p>API version 37</p>
</td>
</tr>
<tr>
<td>API SFDC</td>
<td>
<p>API version 15</p>
<p>API version 21</p>
</td>
</tr>
<tr><td>API Oracle On Demand</td>
<td>
<p>API des services Web v1.0</p>
</td>
</tr>
<tr>
<td>MS Dynamics</td>
<td>
<p>API Soap - Sur site : 2007, 2015, 2016</p>
<p>API Soap - Online : 2015, 2016</p>
<p>API Web - Sur site et en ligne : Mise à jour 1 du 36 mai 2016</p>
</td>
</tr>
</tbody>
</table>

## Federated Data Access (FDA){#FederatedDataAccessFDA}

<table>
<tbody>
<tr>
<td>Microsoft Azure Synapse Analytics</td>
<td> </td>
</tr>
<tr>
<td>Amazon Redshift</td>
<td><p> </p>
</td>
</tr>
<tr>
<td>Oracle</td>
<td>
<p>11g</p>
<p>12c</p>
<p>18c</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>9.4.x</p>
<p>9.5.x</p>
<p>9.6.x</p>
<p>10.x</p>
<p>11.x</p>
</td>
</tr>
<tr><td>SQL Server </td>
<td>
<p>2012 SP1 et SP2</p>
<p>2014</p>
<p>2016</p>
<p>2017</p>
</td>
</tr>
<tr><td>MySQL</td>
<td>
<p>5.7</p>
</td>
</tr>
<tr>
<td>Teradata</td>
<td>
<p>15.0</p>
<p>15.10</p>
<p>16</p>
<p>16.20</p>
</td>
</tr>
<tr>
<td>Netezza</td>
<td>
<p>7.2</p>
</td>
</tr>
<tr>
<td>Sybase</td>
<td>
<p>IQ 16</p>
<p>ASE 15.7</p>
</td>
</tr>
<tr>
<td>SAP HANA</td>
<td>
<p>version 1 SP12 ou ultérieure</p>
</td>
</tr>
<tr><td>Hadoop via HiveSQL</td>
<td>
<p>HortonWorks HDP 2.4.X, 2.5.x, 2.6.x</p>
<p>HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)</p>
<p>Cloudera CDH6.x</p>
</td>
</tr>
<tr>
<td>Snowflake</td>
<td> </td>
</tr>
</tbody>
</table>

## Systèmes d’exploitation de la console cliente{#ClientConsoleoperatingsystems}

<table>
<tbody>
<tr>
<td>Windows Server </td>
<td>
<p>2012</p>
<p>2016</p>
</td>
</tr>
<tr>
<td>Windows</td>
<td>
<p>8</p>
<p>10 (recommandé pour les instances japonaises)</p>
</td>
</tr>
</tbody>
</table>

## SDK Mobile{#MobileSDK}

<table>
<tbody>
<tr>
<td>Android</td>
<td>
<p>7.x</p>
<p>8.x</p>
<p>9.0</p>
<p>avec SDK mobile version 1.0.27.</p>
</td>
</tr>
<tr>
<td>iOS</td>
<td>
<p>iOS 9</p>
<p>iOS 10</p>
<p>iOS 11</p>
<p>iOS 12</p>
<p>iOS 13</p>
<p>avec SDK mobile version 1.0.26, compatible avec les versions 32 et 64 bits.</p>
</td>
</tr>
</tbody>
</table>

## Navigateurs{#Browsers}

La version 11 d’Internet Explorer est prise en charge.

Pour les navigateurs suivants, la dernière version est prise en charge :

* Microsoft Edge

* Firefox

* Chrome

* Safari

## Intégrations Experience Cloud{#ExperienceCloudintegrations}

For integrations with Adobe solutions, refer to this [section](https://docs.adobe.com/content/help/fr-FR/campaign-classic/using/integrating-with-adobe-experience-cloud/about-campaign-integrations.html#experience-cloud-integrations).

## Plus comme suit{#Morelikethis}

* [Notes de mise à jour d’Adobe Campaign Classic](https://docs.adobe.com/content/help/fr-FR/campaign-classic/using/release-notes/latest-release.html)
* [Guide d’installation](https://docs.adobe.com/content/help/fr-FR/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/general-architecture.html)
* [Fonctionnalités et systèmes obsolètes](https://helpx.adobe.com/fr/campaign/kb/deprecated-and-removed-features.html)
* [Procédure d’upgrade de build](https://helpx.adobe.com/fr/campaign/kb/acc-build-upgrade.html)
* [Matrice de compatibilité Campaign Classic pour la version 19.0](https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix-19-0.html)
* [Matrice de compatibilité Campaign Classic pour la version 19.1](https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix-19-1.html)

