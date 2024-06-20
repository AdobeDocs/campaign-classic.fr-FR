---
product: campaign
title: Matrice de compatibilité pour Campaign Classic
description: Matrice de compatibilité Campaign Classic
feature: Release Notes
role: User
level: Beginner
exl-id: b8c1f287-06f4-4c34-8cca-b0c7676abbc2
source-git-commit: b23632d0718d62d61e94e636937b93aa39bbe43f
workflow-type: tm+mt
source-wordcount: '840'
ht-degree: 64%

---

# Matrice de compatibilité {#compatibility-matrix}

Dans son [dernier build](../../rn/using/latest-release.md), Adobe Campaign Classic v7 est compatible avec tous les systèmes et outils répertoriés dans cette page. Lorsque des versions spécifiques de ces systèmes et outils tiers arrivent en fin de vie (EOL) avec leurs créateurs respectifs, Adobe Campaign n&#39;est plus compatible avec celles-ci. Elles sont alors supprimées de notre matrice de compatibilité pour la version suivante du produit. Pour éviter tout problème, vérifiez que vous utilisez les versions prises en charge des systèmes répertoriés dans cette matrice de compatibilité. Pour en savoir plus sur les éléments obsolètes, consultez [cette page](../../rn/using/deprecated-features.md).

Sauf mention contraire, toutes les versions mineures sont prises en charge.

>[!CAUTION]
>
>Cette matrice est régulièrement mise à jour avec de nouveaux systèmes et outils pris en charge ajoutés et supprimés.

## Systèmes d’exploitation {#OperatingSystems}

En tant que client ou cliente on-premise/hybride, vous devez installer Adobe Campaign sur l’un des systèmes d’exploitation répertoriés ci-dessous. Découvrez les étapes de l’installation de Campaign Classic v7 dans [cette page](../../installation/using/application-server.md).

<table> 
<tbody> 
<td><strong>Système d'exploitation</strong></td>
<td><strong>Version du système d’exploitation</strong></td>
<td><strong>Version minimale de Campaign</strong></td>
<tr> 
<td>CentOs</td>
<td>
<p>7.x</p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td>Debian</td>
<td>
<p>11</p>
<p>10</p>
</td>
<td>
<p>v7.3</p>
<p></p>
</td>
</tr>
<tr>
<td>RHEL</td>
<td>
<p>9.x</p>
<p>8.x</p>
<p>7.x</p>
</td>
<td>
<p>v7.4</p>
<p></p>
<p></p>
</td>
</tr>
<tr>
<td>Windows Server </td>
<td>
<p>2022</p>
<p>2019</p>
<p>2016</p>
</td>
<td>
<p>v7.4</p>
<p>v7.2</p>
<p></p>
</td>
</tr>
</tbody>
</table>

>[!IMPORTANT]
>
>Si vous utilisez RHEL, vous devez accepter de désactiver [SELinux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#selinux) ou demander à vos architectes d’écrire des règles SELinux personnalisées pour vérifier qu’un SELinux activé ne pose pas de problème avec les opérations Campaign.

## Serveurs web {#WebServers}

En tant que client ou cliente on-premise/hybride, en fonction de votre système d’exploitation, vous devez intégrer Campaign dans l’un des serveurs web répertoriés ci-dessous. Découvrez les étapes de configuration des serveurs web dans [cette page](../../installation/using/integration-into-a-web-server-for-windows.md) pour Windows et [cette page](../../installation/using/integration-into-a-web-server-for-linux.md) pour Linux.

<table>
<tbody>
<tr>
<td>Microsoft IIS</td>
<td>
<p>10.0 sur Windows Server</p>
</td>
</tr>
<tr>
<td>Apache</td>
<td>
<p>2,4</p>
</td>
</tr>
</tbody>
</table>

## Outils {#Tools}

En tant que client ou cliente on-premise/hybride, vous devez installer et configurer les outils répertoriés ci-dessous. [En savoir plus](../../installation/using/application-server.md).

<table>
<tbody>
<td><strong>Outil</strong></td>
<td><strong>Version</strong></td>
<td><strong>Version de Campaign minimale</strong></td>
<tr>
<td><p>Java Development Kit (JDK)</p>
<p>En savoir plus sur <a href="../../installation/using/application-server.md#jdk" target="_blank">cette page</a>.</p>
</td>
<td>
<p>11</p>
<p>9</p>
<p>8</p>
<p></p>
</td>
<td>
<p>obligatoire à partir de la version 7.4.1</p>
<p>jusqu’à v7.4.1</p>
<p>jusqu’à v7.4.1</p>
</tr>
<tr>
<td><p>Libre Office</p></td>
<td>
<p>7 (et versions antérieures en cas dʼincorporation dans votre système)</p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td><p>SpamAssassin</p></td>
<td>
<p>3.4.x</p>
</td>
<td>
<p></p>
</td>
</tbody>
</table>

## Systèmes de gestion de base de données relationnelle (SGBDR) {#RDBMSservers}

En tant que client ou cliente on-premise/hybride, vous devez installer et configurer l’une des bases de données répertoriées ci-dessous. [En savoir plus](../../installation/using/creating-and-configuring-the-database.md).


<table>
<tbody>
<td><strong>Système de la base de données</strong></td>
<td><strong>Version de la base de données</strong></td>
<td><strong>Version minimale de Campaign</strong></td>
<tr>
<td>Oracle</td>
<td>
<p>23c</p>
<p>19c</p>
<p>18c</p>
<p>12c</p>
<p>11g R2</p>
</td>
<td>
<p>v7.4</p>
<p></p>
<p></p>
<p></p>
<p></p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>14.x</p>
<p>13.x</p>
<p>12.x</p>
<p>11.x</p>
</td>
<td>
<p>v7.3.2</p>
<p></p>
<p></p>
<p></p>
</td>
</tr>
<tr>
<td>Microsoft SQL Server</td>
<td>
<p>2022</p>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
</td>
<td>
<p>v7.4</p>
<p></p>
<p></p>
<p></p>
<p></p>
</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>* Le pilote SGBDR doit correspondre à la version du serveur SGBDR.
>
>* Microsoft SQL Server n’est pas pris en charge en tant que base de données principale lorsque le serveur Campaign est en cours d’exécution sous Linux. [En savoir plus](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#database-access-layers).
>
>* Vous pouvez également utiliser Amazon RDS pour PostgreSQL avec les versions spécifiées ci-dessus.
>
>* PostgreSQL constitue le SGBDR pour les environnements de services cloud hébergés/gérés.


## Connecteurs CRM {#CRMconnectors}

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
<td><strong>Version minimale de Campaign</strong></td>
<tr>
<td>Amazon Redshift</td>
<td><p> </p>
<td>v7.0 19.1.4</td>
</td>
</tr>
<tr>
<td>Google BigQuery</td>
<td> </td>
<td>v7.2</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>14.x</p>
<p>13.x</p>
<p>12.x</p>
<p>11.x</p>
</td>
<td>v7.0 19.1.4</td>
</tr>
<tr>
<td>Snowflake</td>
<td> </td>
<td>v7.2</td>
</tr>
<tr>
<td>Vertica Analytics</td>
<td> </td>
<td>v7.0 19.1.4 </td>
</tr>
</tbody>
</table>

En complément, les environnements **hybrides** et **On-premise** peuvent connecter Campaign aux systèmes de base de données externes suivants. Ces systèmes ne sont **pas compatibles** avec les environnements (hébergés) de Campaign **Managed Services**.

<table>
<tbody>
<td><strong>Système de la base de données</strong></td>
<td><strong>Version de la base de données</strong></td>
<td><strong>Version minimale de Campaign</strong></td>
<tr>
<td>Microsoft Azure Synapse Analytics</td>
<td> </td>
<td></td>
</tr>
<tr><td>MySQL</td>
<td>
<p>8</p>
<p>5.7</p>
</td>
<td>
<p>v7.3</p>
<p></p>
</td>
</tr>
<tr>
<td>Netezza</td>
<td>
<p>v7.2</p>
</td>
<td></td>
</tr>
<tr>
<td>Oracle</td>
<td>
<p>23c</p>
<p>19c</p>
<p>18c</p>
<p>12c</p>
<p>11g</p>
</td>
<td>
<p>v7.4</p>
<p></p>
<p></p>
<p></p>
<p></p>
</td>
</tr>
<tr>
<td>SAP HANA</td>
<td>
<p>SPS 12 version 1</p>
</td>
<td></td>
</tr>
<tr><td>SQL Server</td>
<td>
<p>2022 (à partir de Campaign v7.4)</p>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 SP1 et SP2</p>
</td>
<td></td>
</tr>
<tr>
<td>Sybase</td>
<td>
<p>IQ 16</p>
<p>ASE 15.7</p>
</td>
<td></td>
</tr>
<tr>
<td>Teradata</td>
<td>
<p>17.x</p>
<p>16.x (dernière version)</p>
</td>
<td></td>
</tr>
<tr><td>Hadoop via HiveSQL</td>
<td>
<p>HortonWorks HDP 2.4.X, 2.5.x, 2.6.x</p>
<p>HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)</p>
<p>Cloudera CDH6.x</p>
</td>
<td></td>
</tr>
</tbody>
</table>


## Console cliente {#ClientOS}

Les systèmes dʼexploitation et le navigateur ci-après sont **nécessaires** pour utiliser la [Console cliente Campaign](../../installation/using/installing-the-client-console.md).

### Systèmes d’exploitation

<table>
<tbody>
<td><strong>Système</strong></td>
<td><strong>Version du système d’exploitation</strong></td>
<td><strong>Version de Campaign minimale</strong></td>
<tr>
<td>Microsoft Windows</td>
<td>
<p>11</p>
<p>10</p>
</td>
<td>
<p>v7.3</p>
<p></p>
<p></p>
</tr>
<tr>
<td>Microsoft Windows Server</td>
<td>
<p>2022</p>
<p>2019</p>
<p>2016</p>
</td>
<td>
<p>v7.4.1</p>
<p>v7.2.1</p>
<p></p>
</tbody>
</table>

### Runtime de Microsoft WebView2 {#webview}

La dernière version du Runtime Microsoft Edge WebView2 est obligatoire pour la console cliente Campaign.

Téléchargez Microsoft Edge WebView2 à partir du [site Microsoft Developer](https://www.adobe.com/go/acc-ms-webview2-runtime-download_fr).


## SDK mobile {#MobileSDK}

Vous pouvez utiliser Campaign pour [envoyer des notifications push ;](../../delivery/using/about-mobile-app-channel.md), via le SDK Mobile Adobe Experience Platform en configurant l’extension Adobe Campaign dans l’interface utilisateur de collecte de données.

Le SDK Campaign est [obsolète](deprecated-features.md) Démarrage de Campaign v7.4. Pour garantir une transition fluide pour une mise en oeuvre existante vers le SDK AEP Mobile, vous pouvez toujours l’utiliser sur les systèmes d’exploitation répertoriés ci-dessous.<!--, using the associated [mobile SDK](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md)-->.


<table>
<tbody>
<tr>
<td>Google Android</td>
<td>
<p>7 à 14</p>
<p>avec SDK Mobile version 1.1.1.</p>
<p>Android 13 et 14 sont pris en charge à partir de Campaign v7.4.</p>
<p>Android 12 est pris en charge à partir de Campaign v7.3.</p>
</td>
</tr>
<tr>
<td>Apple iOS</td>
<td>
<p>iOS 9 - 17</p>
<p>avec SDK Mobile version 1.0.26.</p>
<p>Apple iOS 15 est pris en charge à partir de Campaign v7.3. </p>
<p>Apple iOS 16 et 17 sont pris en charge à partir de Campaign v7.4.</p>
</td>
</tr>
</tbody>
</table>

## Navigateurs {#Browsers}

Les navigateurs suivants, dans leur dernière version, sont compatibles avec Campaign pour un [accès web](../../campaign/using/accessing-marketing-campaigns.md#using-the-web-interface-).

* Google Chrome
* Microsoft Edge
* Mozilla Firefox
* Safari



>[!MORELIKETHIS]
>
>* [Notes de mise à jour d&#39;Adobe Campaign Classic](../../rn/using/latest-release.md)
>* [Architecture générale de Campaign](../../installation/using/general-architecture.md)
>* [Recommandations relatives au dimensionnement du matériel](../../technotes/using/hardware-sizing.md)
>* [Fonctionnalités et systèmes obsolètes](../../rn/using/deprecated-features.md)
>* [Procédure d&#39;upgrade de build](../../production/using/build-upgrade.md)
