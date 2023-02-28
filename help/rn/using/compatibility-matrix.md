---
product: campaign
title: Matrice de compatibilité pour Campaign Classic
description: Matrice de compatibilité Campaign Classic
feature: Overview
role: User
level: Beginner
exl-id: b8c1f287-06f4-4c34-8cca-b0c7676abbc2
source-git-commit: 84c6dacb96bd0853be9eaef0dfa7e36116f8a46a
workflow-type: tm+mt
source-wordcount: '779'
ht-degree: 90%

---

# Matrice de compatibilité{#compatibility-matrix}

![](../../assets/v7-only.svg)

Ce document répertorie tous les systèmes et composants pris en charge pour [le dernier build](../../rn/using/latest-release.md) d’**Adobe Campaign Classic v7**. Les produits et versions ne faisant pas partie de cette liste ne sont pas compatibles avec Adobe Campaign.

Si vous êtes un utilisateur [!DNL Gold Standard], reportez-vous à la [[!DNL Gold Standard] matrice de compatibilité](../../rn/using/gold-standard.md#compatibility-matrix-gs).

## Remarques importantes{#important-notes}

Sauf mention contraire, toutes les versions mineures sont prises en charge.

Dans son [dernier build](../../rn/using/latest-release.md), Adobe Campaign Classic est compatible avec tous les systèmes et outils répertoriés dans cette page. Lorsque des versions spécifiques de ces systèmes et outils tiers arrivent en fin de vie (EOL) avec leurs créateurs respectifs, Adobe Campaign n&#39;est plus compatible avec celles-ci. Elles sont alors supprimées de notre matrice de compatibilité pour la version suivante du produit. Pour éviter tout problème, vérifiez que vous disposez des versions prises en charge des systèmes répertoriés dans la matrice de compatibilité.

Pour en savoir plus sur les éléments obsolètes, consultez [cette page](../../rn/using/deprecated-features.md).

>[!CAUTION]
>
>Cette matrice est régulièrement mise à jour avec les nouveaux éléments pris en charge ajoutés et les éléments déconseillés supprimés.

## Systèmes d&#39;exploitation{#OperatingSystems}

<table> 
<tbody> 
<tr> 
<td>CentOs</td>
<td>
<p>7.x</p>
<p><strong>Important :</strong> si vous utilisez RHEL, vous devez désactiver SELinux ou demander à vos architectes d'écrire des règles SELinux personnalisées pour vérifier qu'un SELinux activé ne pose pas de problème pour les opérations de Campaign.</p>
<p>8.x</br><strong>Important :</strong> CentOS Linux 8 atteindra la fin de vie (EOL) le 31 décembre 2021. Pour plus d’informations à ce sujet, consultez la page <a href="../../rn/using/deprecated-features.md">Fonctionnalités obsolètes</a>.</p>
</td>
</tr>
<tr>
<td>Debian</td>
<td>
<p>11 (à partir de Campaign v7.3)</p>
<p>10</p>
<p>9</p>
</td>
</tr>
<tr>
<td>RHEL</td>
<td>
<p>8.x</p>
<p>7.x</p>
<p><strong>Important :</strong> si vous utilisez RHEL, vous devez désactiver SELinux ou demander à vos architectes d'écrire des règles SELinux personnalisées pour vérifier qu'un SELinux activé ne pose pas de problème pour les opérations de Campaign.</p>
</td>
</tr>
<tr>
<td>Windows Server </td>
<td>
<p>2019 (à partir de Campaign v7.2)</p>
<p>2016</p>
<p>2012 R2</p>
<p>2012</p>
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
<p>10.0 sur Windows Server 2016  et 2019</p>
<p>8.5 sur Windows Server 2012 R2</p>
<p>8.0 sur Windows Server 2012 - Windows 8</p>
</td>
</tr>
<tr>
<td>Apache</td>
<td>
<p>2.4 pour RHEL7 - CentOS 7, Debian 8/9, Windows</p>
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
<p>11</p>
<p>9</p>
<p>8</p>
<p>Campaign prend en charge le Java Development Kit (JDK) développé par Oracle et OpenJDK.</p>
</td>
</tr>
<tr>
<td>Libre Office</td>
<td>
<p>7 (et versions antérieures en cas dʼincorporation dans votre système)</p>
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

## Systèmes de gestion de base de données relationnelle (SGBDR){#RDBMSservers}

<table>
<tbody>
<tr>
<td>Oracle</td>
<td>
<p>19c</p>
<p>18c</p>
<p>12c</p>
<p>11g R2</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>14.x (à partir de Campaign v7.3.2)</p>
<p>13.x</p>
<p>12.x</p>
<p>11.x</p>
<p>10.x</p>
<p><strong>Remarque :</strong> vous pouvez également utiliser Amazon RDS pour PostgreSQL avec les versions indiquées ci-dessus.</p>
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
<p><strong>Important :</strong> Microsoft SQL Server nʼest pas pris en charge en tant que base de données principale lorsque le serveur Campaign est exécuté sous Linux. <a href="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/install-campaign-on-prem/installing-campaign-in-linux-/prerequisites-of-campaign-installation-in-linux.html#database-access-layers">En savoir plus</a>.</p>
</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>* Le pilote SGBDR doit correspondre à la version du serveur SGBDR.
>
>* PostgreSQL constitue le SGBDR pour les environnements hébergés.


## Connecteurs CRM{#CRMconnectors}

Les systèmes de gestion de la relation client (CRM) compatibles avec Adobe Campaign sont répertoriés ci-dessous. [En savoir plus](../../platform/using/crm-connectors.md) sur les connecteurs CRM disponibles dans Campaign.

<table>
<tbody>
<tr>
<td>API du connecteur Salesforce</td>
<td>
<p>API version 49</p>
</td>
</tr>
<tr>
<td>Connecteur Microsoft Dynamics </td>
<td>
<p>API web</p>
</td>
</tr>
</tbody>
</table>

## Federated Data Access (FDA){#FederatedDataAccessFDA}

Les bases de données externes compatibles avec le [module Adobe Campaign Federated Data Access](../../installation/using/about-fda.md) sont répertoriées ci-dessous. La compatibilité dépend de votre [modèle d’hébergement](../../installation/using/hosting-models.md).

Les environnements **Managed Services** (hébergé), **Hybride** et **On-premise** peuvent connecter Campaign aux systèmes de base de données externes suivants :

<table>
<tbody>
<td><strong>Système de la base de données</strong></td>
<td><strong>Version de la base de données</strong></td>
<td><strong>Version de Campaign</strong></td>
<tr>
<td>Amazon Redshift</td>
<td><p> </p>
<td>v7.0 19.1.4 minimum</td>
</td>
</tr>
<tr>
<td>Google BigQuery</td>
<td> </td>
<td>7.2 minimum</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>14.x</p>
<p>13.x</p>
<p>12.x</p>
<p>11.x</p>
<p>10.x</p>
</td>
<td>v7.0 19.1.4 minimum</td>
</tr>
<tr>
<td>Snowflake</td>
<td> </td>
<td>7.2 minimum</td>
</tr>
<tr>
<td>Vertica Analytics</td>
<td> </td>
<td>v7.0 19.1.4 minimum</td>
</tr>
</tbody>
</table>

En complément, les environnements **hybrides** et **On-premise** peuvent connecter Campaign aux systèmes de base de données externes suivants. Ces systèmes ne sont **pas compatibles** avec les environnements (hébergés) de Campaign **Managed Services**.

<table>
<tbody>
<td><strong>Système de la base de données</strong></td>
<td><strong>Version de la base de données</strong></td>
<td><strong>Version de Campaign</strong></td>
<tr>
<td>Microsoft Azure Synapse Analytics</td>
<td> </td>
<td>v7.0 19.1.4 minimum</td>
</tr>
<tr><td>MySQL</td>
<td>
<p>8 (à partir de Campaign v7.3)</p>
<p>5.7</p>
</td>
<td>
<p>v7.3 minimum</p>
<p>V7.0 minimum</p>
</td>
</tr>
<tr>
<td>Netezza</td>
<td>
<p>7.2</p>
</td>
<td>V7.0 minimum</td>
</tr>
<tr>
<td>Oracle</td>
<td>
<p>19c</p>
<p>18c</p>
<p>12c</p>
<p>11g</p>
</td>
<td>V7.0 minimum</td>
</tr>
<tr>
<td>SAP HANA</td>
<td>
<p>SPS 12 version 1</p>
</td>
<td>V7.0 minimum</td>
</tr>
<tr><td>SQL Server </td>
<td>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 SP1 et SP2</p>
</td>
<td>V7.0 minimum</td>
</tr>
<tr>
<td>Sybase</td>
<td>
<p>IQ 16</p>
<p>ASE 15.7</p>
</td>
<td>V7.0 minimum</td>
</tr>
<tr>
<td>Teradata</td>
<td>
<p>17</p>
<p>16.20</p>
<p>16</p>
<p>15.10</p>
<p>15.0</p>
</td>
<td>V7.0 minimum</td>
</tr>
<tr><td>Hadoop via HiveSQL</td>
<td>
<p>HortonWorks HDP 2.4.X, 2.5.x, 2.6.x</p>
<p>HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)</p>
<p>Cloudera CDH6.x</p>
</td>
<td>V7.0 minimum</td>
</tr>
</tbody>
</table>



## Console cliente {#ClientConsoleoperatingsystems}

Les systèmes dʼexploitation et le navigateur ci-après sont **nécessaires** pour utiliser la [Console cliente Campaign](../../installation/using/installing-the-client-console.md).

### Systèmes d’exploitation

<table>
<tbody>
</tr>
<tr>
<td>Microsoft Windows</td>
<td>
<p>11 (à partir de Campaign v7.3)</p>
<p>10</p>
<p>8</p>
</td>
</tr>
<tr>
<td>Microsoft Windows Server</td>
<td>
<p>2019 (à partir de Campaign v7.2.1)</p>
<p>2016</p>
<p>2012</p>
</td>
</tbody>
</table>

### Runtime de Microsoft WebView2

Runtime de Microsoft Edge WebView2 La dernière version est obligatoire pour la console cliente Campaign.

Téléchargez Microsoft Edge WebView2 à partir de [Site du développeur de Microsoft](http://www.adobe.com/go/acc-ms-webview2-runtime-download_fr).


## SDK mobile{#MobileSDK}

Vous pouvez utiliser Campaign pour [envoyer des notifications push](../../delivery/using/about-mobile-app-channel.md) sur les systèmes dʼexploitation répertoriés ci-dessous, à lʼaide du [SDK mobile](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md) associé.

<table>
<tbody>
<tr>
<td>Google Android</td>
<td>
<p>12 (à partir de Campaign v7.3), 9.0, 8.x, 7.x</p>
<p>avec SDK Mobile version 1.1.1</p>
</td>
</tr>
<tr>
<td>Apple iOS</td>
<td>
<p>iOS 9 - 15</p>
<p>avec SDK Mobile version 1.0.26, compatible avec les versions 32 et 64 bits. iOS 15 est pris en charge à partir de Campaign v7.3</p>
</td>
</tr>
</tbody>
</table>

## Navigateurs{#Browsers}

Les navigateurs suivants, dans leur dernière version, sont compatibles avec Campaign pour [Accès Web](../../campaign/using/accessing-marketing-campaigns.md#using-the-web-interface-).

* Google Chrome
* Microsoft Edge
* Mozilla Firefox
* Safari



## Autres informations similaires{#Morelikethis}

* [Notes de mise à jour d&#39;Adobe Campaign Classic](../../rn/using/latest-release.md)
* [Architecture générale de Campaign](../../installation/using/general-architecture.md)
* [Recommandations relatives au dimensionnement du matériel](../../technotes/using/hardware-sizing.md)
* [Fonctionnalités et systèmes obsolètes](../../rn/using/deprecated-features.md)
* [Procédure d&#39;upgrade de build](../../production/using/build-upgrade.md)
