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
source-git-commit: bc54cef4c44be4c694e062f56685dbb09d2fcf8e
workflow-type: tm+mt
source-wordcount: '618'
ht-degree: 97%

---


# Matrice de compatibilité{#compatibility-matrix}

Ce document répertorie tous les systèmes et composants pris en charge pour le dernier build d’**Adobe Campaign Classic (v6.11 et v7)**. Les produits et versions ne faisant pas partie de cette liste ne sont pas compatibles avec Adobe Campaign.

## Remarques importantes{#important-notes}

Cette matrice est régulièrement mise à jour avec les nouveaux éléments pris en charge ajoutés et les éléments déconseillés supprimés.

Sauf mention contraire, toutes les versions mineures sont prises en charge.

Adobe Campaign Classic est compatible avec tous les systèmes et outils répertoriés dans cette page. Lorsque des versions spécifiques de ces systèmes et outils tiers arrivent en fin de vie (EOL) avec leurs créateurs respectifs, Adobe Campaign n’est plus compatible avec celles-ci. Elles sont alors supprimées de notre matrice de compatibilité pour la version suivante du produit. Pour éviter tout problème, vérifiez que vous disposez des versions prises en charge des systèmes répertoriés dans la matrice de compatibilité.

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
<p><strong>Important :</strong> si vous utilisez RHEL, vous devez désactiver SELinux ou demander à vos architectes d’écrire des règles SELinux personnalisées pour vérifier qu’un SELinux activé ne pose pas de problème pour les opérations de Campaign.</p>
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

## Serveurs web{#WebServers}

<table>
<tbody>
<tr>
<td>Microsoft IIS </td>
<td>
<p>8.0 sur Windows Server 2012 - Windows 8</p>
<p>8.5 sur Windows Server 2012 R2</p>
<p>10.0 sur Windows Server 2016</p>
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
<td>Java Development Kit (JDK)</td>
<td>
<p>8</p>
<p>9</p>
<p>L'application a été validée pour le JDK développé par Oracle ainsi que pour OpenJDK.</p>
</td>
</tr>
<tr>
<td>Libre Office</td>
<td>
<p>6 (et versions antérieures en cas d’incorporation dans votre système)</p>
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

## Pilotes SGBDR{#RDBMSdrivers}

Les pilotes SGBDR suivants sont pris en charge :

* Oracle SQL*Net 11

* Oracle SQL*Net 12

* PostgreSQL (libpq)

* SQLServer

* DB2 (pilote ODBC)


>[!NOTE]
>
>Le pilote SGBDR doit correspondre à la version du serveur SGBDR.

## Serveurs SGBDR{#RDBMSservers}

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
<p>Remarque : vous pouvez également utiliser Amazon RDS pour PostgreSQL avec les versions indiquées ci-dessus.</p>
</td>
</tr>
<tr>
<td>SQL Server </td>
<td>
<p>2012 - SP1 et SP2</p>
<p>2014</p>
<p>2016</p>
<p>2017</p>
<p>Avertissement : Microsoft SQL Server n’est pas pris en charge en tant que base de données principale lorsque le serveur Campaign est exécuté sous Linux. <a href="https://docs.adobe.com/content/help/en/campaign-classic/using/installing-campaign-classic/prerequisites-and-recommendations-/database.html#Microsoft_SQL_Server">En savoir plus</a>.</p>
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
<p>API version 37</p>
</td>
</tr>
<tr>
<td>API SFDC</td>
<td>
<p>API version 15</p>
<p>API version 21</p>
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
<p>API Soap - On-premise : 2007, 2015, 2016</p>
<p>API Soap - Online : 2015, 2016</p>
<p>API Web - On-premise et Online : 365, 2016, 2016 Mise à jour 1</p>
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
<p>5,7</p>
</td>
</tr>
<tr>
<td>Teradata</td>
<td>
<p>15,0</p>
<p>15,10</p>
<p>16</p>
<p>16,20</p>
</td>
</tr>
<tr>
<td>Netezza</td>
<td>
<p>7,2</p>
</td>
</tr>
<tr>
<td>Sybase</td>
<td>
<p>IQ 16</p>
<p>ASE 15.7</p>
</td>
</tr>
<tr>
<td>SAP HANA</td>
<td>
<p>version 1 SP12 ou ultérieure</p>
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
<p>9,0</p>
<p>avec SDK Mobile version 1.0.27.</p>
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
<p>avec SDK Mobile version 1.0.26, compatible avec les versions 32 et 64 bits.</p>
</td>
</tr>
</tbody>
</table>

## Navigateurs{#Browsers}

La version 11 d’Internet Explorer est prise en charge.

Pour les navigateurs suivants, la dernière version est prise en charge :

* Microsoft Edge

* Firefox

* Chrome

* Safari

## Intégrations Experience Cloud{#ExperienceCloudintegrations}

Pour les intégrations avec les solutions Adobe, consultez cette [section](https://docs.adobe.com/content/help/fr-FR/campaign-classic/using/integrating-with-adobe-experience-cloud/about-campaign-integrations.html#experience-cloud-integrations).

## Articles connexes{#Morelikethis}

* [Notes de mise à jour d’Adobe Campaign Classic](https://docs.adobe.com/content/help/fr-FR/campaign-classic/using/release-notes/latest-release.html)
* [Guide d’installation](https://docs.adobe.com/content/help/fr-FR/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/general-architecture.html)
* [Fonctionnalités et systèmes obsolètes](https://helpx.adobe.com/fr/campaign/kb/deprecated-and-removed-features.html)
* [Procédure d’upgrade de build](https://helpx.adobe.com/fr/campaign/kb/acc-build-upgrade.html)
* [Matrice de compatibilité Campaign Classic pour la version 19.0](https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix-19-0.html)
* [Matrice de compatibilité Campaign Classic pour la version 19.1](https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix-19-1.html)

