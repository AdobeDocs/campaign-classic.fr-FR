---
product: campaign
title: Matrice de compatibilité pour Campaign [!DNL Gold Standard]
description: 'Matrice de compatibilité Campaign Classic pour la version  [!DNL Gold Standard] '
feature: Vue d’ensemble
role: User
level: Beginner
exl-id: 5c0ccaf6-7f82-4e4b-9247-261dbd0f127c
source-git-commit: 6c28e6cd78ce7a8ee5c0dc7e671de780787b9f57
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 99%

---

# [!DNL Gold Standard] Matrice de compatibilité{#compatibility-matrix-gs}

Ce document répertorie tous les systèmes et composants pris en charge pour les builds **Adobe Campaign Classic[!DNL Gold Standard]** 19.1. Les produits et versions ne faisant pas partie de cette liste ne sont pas compatibles avec cette version d&#39;Adobe Campaign.

## Remarques importantes{#important-notes-gs}

Sauf mention contraire, toutes les versions mineures sont prises en charge.

Adobe Campaign Classic est compatible avec tous les systèmes et outils répertoriés dans cette page. Lorsque des versions spécifiques de ces systèmes et outils tiers arrivent en fin de vie (EOL) avec leurs créateurs respectifs, Adobe Campaign n&#39;est plus compatible avec celles-ci. Elles sont alors supprimées de notre matrice de compatibilité pour la version suivante du produit. Pour éviter tout problème, vérifiez que vous disposez des versions prises en charge des systèmes répertoriés dans la matrice de compatibilité.

## Systèmes d&#39;exploitation{#OperatingSystems-gs}

<table> 
<tbody> 
<tr> 
<td>CentOs</td>
<td>
<p>8.x (64 bits)</p>
<p>7.x (64 bits)</p>
</td>
</tr>
<tr>
<td>Debian</td>
<td>
<p>9 (64 bits)</p>
<p>8 (64 bits)</p>
</td>
</tr>
<tr>
<td>RHEL</td>
<td>
<p>7.x (64 bits)</p>
<p><strong>Important :</strong> si vous utilisez RHEL, vous devez désactiver SELinux ou demander à vos architectes d'écrire des règles SELinux personnalisées pour vérifier qu'un SELinux activé ne pose pas de problème pour les opérations de Campaign.</p>
</td>
</tr>
<tr>
<td>Windows Server </td>
<td>
<p>2016</p>
<p>2012 R2</p>
<p>2012</p>
</td>
</tr>
</tbody>
</table>

## Serveurs web{#WebServers-gs}

<table>
<tbody>
<tr>
<td>Microsoft IIS </td>
<td>
<p>10.0 sur Windows Server 2016</p>
<p>8.5 sur Windows Server 2012 R2</p>
<p>8.0 sur Windows Server 2012 - Windows 8</p>
</td>
</tr>
<tr>
<td>Apache</td>
<td>
<p>2.4 pour RHEL7 - CentOS 7, Debian 8/9, Windows (64 bits)</p>
<p>2.2 pour RHEL6 - CentOS 6 uniquement (64 bits)</p>
</td>
</tr>
</tbody>
</table>

## Outils{#Tools-gs}

<table>
<tbody>
<tr>
<td>Java Development Kit (JDK)</td>
<td>
<p>8</p>
<p>L'application a été validée pour le JDK développé par Oracle ainsi que pour OpenJDK.</p>
</td>
</tr>
<tr>
<td>Libre Office</td>
<td>
<p>6 (et versions antérieures en cas d'incorporation dans votre système)</p>
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

## Serveurs SGBDR{#RDBMSservers-gs}

>[!NOTE]
>
>Le pilote SGBDR doit correspondre à la version du serveur SGBDR.

<table>
<tbody>
<tr>
<td>Oracle</td>
<td>
<p>18c</p>
<p>12c</p>
<p>11g R2</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>11.x</p>
<p>10.x</p>
<p>9.6.x</p>
<p>9.5.x</p>
<p>9.4.x</p>
<p>Remarque : vous pouvez également utiliser Amazon RDS pour PostgreSQL avec les versions indiquées ci-dessus.</p>
</td>
</tr>
<tr>
<td>SQL Server </td>
<td>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 - SP1 et SP2</p>
<p>Avertissement : Microsoft SQL Server n'est pas pris en charge en tant que base de données principale lorsque le serveur Campaign est exécuté sous Linux.</p>
</td>
</tr>
<tr>
<td>DB2 UDB</td>
<td>
<p>9.7</p>
<p>Avertissement : DB2 UDB n'est pas autorisé pour les nouvelles installations.</p>
</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>PostgreSQL est le serveur de base de données par défaut pour les environnements hébergés.

## Connecteurs CRM{#CRMconnectors-gs}

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
<p>API version 21</p>
<p>API version 15</p>
</td>
</tr>
<tr>
<td>Microsoft Dynamics </td>
<td>
<p>API Soap - On-premise : 2007, 2015, 2016</p>
<p>API Soap - Online : 2015, 2016</p>
<p>API Web - On-premise et Online : 365, 2016, 2016 Mise à jour 1</p>
</td>
</tr>
</tbody>
</table>

## Federated Data Access (FDA){#FederatedDataAccessFDA-gs}

<table>
<tbody>
<tr>
<td>Amazon Redshift</td>
<td><p> </p>
</td>
</tr>
<tr>
<td>Oracle</td>
<td>
<p>12c</p>
<p>11g</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>11.x</p>
<p>10.x</p>
<p>9.6.x</p>
<p>9.4.x</p>
</td>
</tr>
<tr><td>SQL Server </td>
<td>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 SP1 et SP2</p>
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
<p>16.20</p>
<p>16</p>
<p>15.10</p>
<p>15.0</p>
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
<p>IQ 16</p>
<p>ASE 15.7</p>
</td>
</tr>
<tr>
<td>SAP HANA</td>
<td>
<p>SPS 12 version 1</p>
</td>
</tr>
<tr><td>Hadoop via HiveSQL</td>
<td>
<p>HortonWorks HDP 2.4.X, 2.5.x, 2.6.x</p>
<p>HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)</p>
</td>
</tr>
</tbody>
</table>


## Console cliente {#ClientConsoleoperatingsystems}

:warning: Les systèmes d&#39;exploitation et le navigateur ci-après sont nécessaires pour utiliser la console cliente Campaign.

### Systèmes d’exploitation

<table>
<tbody>
<tr>
<td>Microsoft Windows Server</td>
<td>
<p>2016</p>
<p>2012</p>
</td>
</tr>
<tr>
<td>Microsoft Windows</td>
<td>
<p>8</p>
<p>10 (recommandé pour les instances japonaises)</p>
</td>
</tr>
</tbody>
</table>

### Navigateur

<table>
<tbody>
<tr>
<td>
<p>Microsoft Internet Explorer </p>
</td>
<td>
<p>11</p>
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
<p>7.x, 8.x, 9.0</p>
<p>avec SDK Mobile version 1.0.27.</p>
</td>
</tr>
<tr>
<td>iOS</td>
<td>
<p>iOS 9 - 14</p>
<p>avec SDK Mobile version 1.0.26, compatible avec les versions 32 et 64 bits.</p>
</td>
</tr>
</tbody>
</table>

## Navigateurs{#Browsers}

Les navigateurs ci-après sont compatibles avec Campaign pour un accès à internet.

<table>
<tbody>
<tr>
<td>
<p>Microsoft Edge</p>
</td>
<td>
<p>Dernière version</p>
</td>
</tr>
<tr>
<td>
<p>Mozilla Firefox</p>
</td>
<td>
<p>Dernière version</p>
</td>
</tr>
<tr>
<td>
<p>Google Chrome</p>
</td>
<td>
<p>Dernière version</p>
</td>
</tr>
<tr>
<td>
<p>Safari</p>
</td>
<td>
<p>Dernière version</p>
</td>
</tr>
<tr>
<td>
<p>Microsoft Internet Explorer </p>
</td>
<td>
<p>11</p>
</td>
</tr>
</tbody>
</table>

## Autres informations similaires{#Morelikethis-gs}

* [Notes de mise à jour d&#39;Adobe Campaign Classic](../../rn/using/latest-release.md)
* [Guide d&#39;installation](../../installation/using/general-architecture.md)
* [Fonctionnalités et systèmes obsolètes](../../rn/using/deprecated-features.md)
* [Procédure d&#39;upgrade de build](https://helpx.adobe.com/fr/campaign/kb/acc-build-upgrade.html)
