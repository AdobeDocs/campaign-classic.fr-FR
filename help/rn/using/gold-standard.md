---
product: campaign
title: "versions [!DNL Gold Standard]"
description: Notes de mise à jour et matrice de compatibilité pour Campaign Classic  [!DNL Gold Standard]
feature: Release Notes
role: User
level: Beginner
hidefromtoc: true
hide: true
exl-id: 9e3a11b1-3070-4d90-91d5-7c559bdd500e
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: ht
source-wordcount: '1774'
ht-degree: 100%

---

# Versions [!DNL Gold Standard]{#gold-standard}



Vous trouverez dans cette page des notes de mise à jour et une matrice de compatibilité pour les versions [!DNL Gold Standard].

## Notes de mise à jour de [!DNL Gold Standard]


### [!DNL Gold Standard] version 12{#gs-12}

[!BADGE Obsolète]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=fr#rn-statuses" tooltip="Obsolète"}

_7 septembre 2021_

Le build 9032@554dbcd comprend le correctif suivant :

* Correction d’un problème qui entraînait une erreur 500 lors de l’ouverture du lien vers une application web dans une diffusion LINE avec tracking activé.

_27 août 2021_

Le build 9032@99a3894 comprend les correctifs suivants :

* La fonctionnalité de signature de suivi a été améliorée afin d’éviter les erreurs liées à la manière dont les outils tiers (clients de messagerie, navigateurs Internet, etc.) gèrent les caractères spéciaux. Les paramètres d’URL sont désormais chiffrés.
* Correction d’un problème lié aux sélecteurs de date qui entraînait l’affichage d’un message d’erreur de blocage dans une console. (NEO-36345)

### [!DNL Gold Standard] version 11{#gs-11}

[!BADGE Obsolète]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=fr#rn-statuses" tooltip="Obsolète"}

_14 avril 2021_

Le build 9032@d030c36 comprend le correctif suivant :

* Correction d&#39;une régression de la console cliente qui provoquait des messages d&#39;erreur persistants sur l&#39;écran de connexion IMS. (NEO-34821)
* Cette version de console est requise pour conserver [l’accès IMS](../../technotes/using/ims-updates.md).

**La mise à niveau de la console uniquement est obligatoire. Aucune mise à niveau du serveur n&#39;est requise.**

>[!CAUTION]
>
> * Si vous vous connectez à Campaign avec votre Adobe ID, par le biais du service Adobe IDentity Management (IMS), la mise à niveau est obligatoire pour que le serveur Campaign et la console cliente puissent se connecter à Campaign après le **30 juin 2021**. [En savoir plus](../../technotes/using/ims-updates.md)
> * Cette version s&#39;accompagne d&#39;un [correctif de sécurité](https://helpx.adobe.com/fr/security/products/campaign/apsb21-04.html) : la mise à niveau est obligatoire pour renforcer la sécurité de votre environnement.
> * Si vous utilisez l’intégration Experience Cloud Triggers via l’authentification OAuth, vous devez migrer vers Adobe I/O comme décrit [sur cette page](../../integrations/using/about-triggers.md#implement). Lʼancien mode dʼauthentification oAuth avec Campaign [a été retiré](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411?profile.language=fr) en **septembre 2021**. Les environnements hébergés bénéficient dʼune extension jusquʼau **23 février 2022**. En tant que client on-premise ou hybride, contactez l’assistance clientèle d’Adobe pour étendre l’assistance jusqu’en février 2022. Vous devez fournir [l’AppID de l’application OAuth](../../integrations/using/configuring-pipeline.md#step-optional) à Adobe.
>
>Pour en savoir plus, rendez-vous dans la [[!DNL Gold Standard] section](../../rn/using/gold-standard.md)

_2 mars 2021_

Le build 9032@10c2709 comprend le correctif suivant :

* Correction d’une régression qui empêchait l’utilisation de certains composants de la console, tels que le sélecteur de date et la gestion des images dans les diffusions. (NEO-31453, NEO-31454)

**La mise à niveau de la console uniquement est obligatoire. Aucune mise à niveau du serveur n&#39;est requise.**

>[!NOTE]
>
> Connectez-vous à la [distribution logicielle Adobe](https://experience.adobe.com/#/downloads/content/software-distribution/fr/campaign.html) pour télécharger la nouvelle version. Découvrez comment proposer la mise à jour de la console à tous les utilisateurs finaux [sur cette page](../../installation/using/client-console-availability-for-windows.md).

_22 décembre 2020_

Le build 9032@d3b452f comprend les améliorations et correctifs suivants :

* Le protocole de connexion a été mis à jour pour suivre le nouveau mécanisme dʼauthentification IMS.

* L’authentification de l’intégration des Triggers basée à lʼorigine sur la configuration de lʼauthentification oAUTH pour accéder au pipeline a été modifiée et déplacée vers Adobe I/O. [En savoir plus](../../integrations/using/about-triggers.md#implement)

* Après la [fin de la prise en charge du protocole binaire hérité des APN iOS](https://developer.apple.com/news/?id=c88acm2b), toutes les instances utilisant ce protocole sont mises à jour vers le protocole HTTP/2 durant la mise à niveau.

* Correction d&#39;un problème de sécurité afin de renforcer la protection contre les problèmes SSRF (Server Side Request Forgery). (NEO-27777)

* Correction d&#39;un problème en raison duquel les workflows échouaient lors de l&#39;exécution d&#39;une activité d&#39;**enrichissement**. (NEO-17338)

### [!DNL Gold Standard] version 10{#gs-10}

[!BADGE Obsolète]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=fr#rn-statuses" tooltip="Obsolète"}

_7 juillet 2020_

Le build 9032@efd8a94 comprend le correctif suivant :

Correction d’un problème qui empêchait le tracking de fonctionner lorsque la fonction de signature était désactivée. (NEO-26411)

>[!CAUTION]
>
>Nous vous recommandons de mettre à niveau la console cliente avec celle disponible dans cette version. Pour plus d’informations, consultez [cette page](../../installation/using/installing-the-client-console.md)

### [!DNL Gold Standard] version 9{#gs-9}

[!BADGE Obsolète]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=fr#rn-statuses" tooltip="Obsolète"}

_22 juin 2020_

Le build 9032@800be2e comprend les correctifs suivants :

* Le connecteur HTTP2 iOS a été amélioré (mises à jour tierces et gestion des erreurs). (NEO-25904, NEO-25903, NEO-25799)

Les correctifs suivants sont liés au mécanisme de sécurité des liens de tracking (apprenez-en davantage dans la [liste de contrôle Sécurité et confidentialité](https://helpx.adobe.com/fr/campaign/kb/acc-security.html#signature-mechanism)) :

* Correction d&#39;un problème qui empêchait le suivi des « clics de notification » de fonctionner (notifications push iOS et Android). (NEO-25965)
* Correction d’un problème qui pouvait empêcher d’ouvrir/de cliquer sur les URL de tracking lors de l’utilisation de certaines anciennes versions d’Outlook.  (NEO-25688)
* Correction d’un problème qui empêchait le suivi des URL à l’aide de fragments dans les paramètres de personnalisation (balises d’ancrage avec signe dièse) de fonctionner. (NEO-25774)
* Correction d’un problème lié au service anti-hameçonnage. (NEO-25283)
* Correction d’un problème de suivi lors de l’utilisation de formules de tracking personnalisées spécifiques. (NEO-25277)


### [!DNL Gold Standard] version 8{#gs-8}

[!BADGE Obsolète]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=fr#rn-statuses" tooltip="Obsolète"}

_29 avril 2020_

Le build 9032@3a9dc9c comprend les correctifs suivants :

* Amélioration de la sécurité des liens de tracking dans les emails. Cette option est activée par défaut pour tous les clients. Une autre fonctionnalité de sécurité améliorée est disponible. Il est possible de l’activer en contactant l&#39;Assistance clientèle. Pour plus d’informations sur la fonctionnalité et la procédure d’activation pour les clients non hébergés, consultez la [liste de contrôle de sécurité et de confidentialité](https://helpx.adobe.com/fr/campaign/kb/acc-security.html#signature-mechanism).

>[!CAUTION]
>
>Si vous rencontrez des problèmes avec les notifications push lors de l’utilisation de liens de tracking, ou avec les diffusions lors de l’utilisation de balises d’ancrage, nous vous recommandons de désactiver le nouveau mécanisme de signature pour les liens de tracking. [La procédure est détaillée dans cette page](https://helpx.adobe.com/fr/campaign/kb/acc-security.html#signature-mechanism)

* Correction d’un problème qui empêchait l’affichage des images sur les diffusions LINE. (NEO-23207)
* Correction d’un problème lié à l’activité **Transfert de fichier** qui empêchait le fonctionnement de l’authentification par clé SFTP sur Debian 9. (NEO-23183)
* Correction d’un problème qui pouvait avoir un impact sur une notification push lorsqu’elle était envoyée à une fréquence élevée. (NEO-20516)
* Correction d’un problème de gestion des réponses aux offres qui pouvait entraîner des blocages du serveur web. (NEO-19482)
* Correction d’une erreur de la gestion de LibreOffice qui empêchait l’export de rapports. (NEO-20982)
* Correction d’un problème qui entraînait une erreur lors de la mise à niveau de nombreux workflows à l’aide d’une activité de questionnaire.
* Amélioration de la gestion de LibreOffice pour éviter tout échec lors de la prévisualisation des emails avec des fichiers .odt.
* Amélioration de la gestion de la connexion Apache pour éviter toute latence sur le service web.
* Amélioration de l’affichage de la balise de version (7 chiffres) dans le menu **À propos**.
* Correction d’une régression de la gestion des listes qui empêchait la publication des offres.
* Correction d’une régression qui entraînait le blocage du workflow de nettoyage.
* Correction d’une régression mineure dans les logs du workflow de nettoyage.

### [!DNL Gold Standard] version 6{#gs-6}

[!BADGE Obsolète]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=fr#rn-statuses" tooltip="Obsolète"}

_9 mars 2020_

Le build 9032@19f73c5 comprend le correctif suivant :

* Correction d’un problème de comptes externes, lié à l’utilisation de FTP sur SSL. (NEO-20498)

### [!DNL Gold Standard] version 5{#gs-5}

[!BADGE Obsolète]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=fr#rn-statuses" tooltip="Obsolète"}

_17 décembre 2019_

Le build 9032@d6b8062 comprend le correctif suivant :

* Correction d’un problème de suivi sur les canaux de communication suivants : mobile (SMS, MMS), notification push (iOS, Android) et réseaux sociaux (Facebook, X, anciennement Twitter). (NEO-19595)

### [!DNL Gold Standard] version 4{#gs-4}

[!BADGE Obsolète]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=fr#rn-statuses" tooltip="Obsolète"}

_11 décembre 2019_

Le build 9032@bc4a935 comprend le correctif suivant :

* Correction d’un problème de performances lors de l’envoi de messages avec une base de données MSSQL. (NEO-17558)

### [!DNL Gold Standard] version 3{#gs-3}

[!BADGE Obsolète]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=fr#rn-statuses" tooltip="Obsolète"}

_20 novembre 2019_

Le build 9032@3468c7b comprend les correctifs suivants :

* Correction d’un problème de connexion via l’authentification IMS. (NEO-17312)
* Correction d’un problème lors de l’affichage de rapports cumulatifs sur plusieurs diffusions. (NEO-18165)
* Correction d’un problème susceptible de bloquer ou de provoquer le blocage du serveur web.

### [!DNL Gold Standard] version 2{#gs-2}

[!BADGE Obsolète]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=fr#rn-statuses" tooltip="Obsolète"}

_19 septembre 2019_

Le build 9032@cee805c comprend les correctifs suivants :

* Correction d’un problème lors de l’utilisation du connecteur CRM pour Salesforce. (NEO-17712)
* Correction d’un problème d’index qui pouvait entraîner des problèmes de performances lors de l’envoi de messages transactionnels.

### Version 19.1.4 - Build 9032{#release-19-1-4-build-9032}

[!BADGE Obsolète]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=fr#rn-statuses" tooltip="Obsolète"}

_13 août 2019_

La version 19.1.4 initiale comprend les correctifs suivants :

* Correction d’un problème lié à l’activité du planificateur qui générait des messages d’erreur indésirables lors de la configuration de l’assistant. Annulation de la mise à jour à partir de NEO-11662. (NEO-17097)
* Correction d&#39;une régression causée par NEO-12727 qui entraînait l&#39;arrêt des workflows lorsqu&#39;une activité de test était exécutée deux fois. (NEO-16835)
* Correction d&#39;un problème qui entraînait le renvoi d&#39;un code HTTP erroné (HTTP 200 OK à la place de HTTP 403 Interdit) lorsqu&#39;un jeton de session non valide ou ayant expiré était utilisé dans les appels d&#39;API. (NEO-16826)
* Correction d&#39;un problème lié à la clé DKIM qui n&#39;était plus incorporée dans les emails, ce qui entraînait des problèmes de délivrabilité. (NEO-16804)
* Correction de divers problèmes liés à la planification des workflows. Les workflows étaient planifiés pour être exécutés une fois par jour sans tenir compte de la configuration du planificateur. (NEO-16619, NEO-16426)


## Matrice de compatibilité de [!DNL Gold Standard]{#compatibility-matrix-gs}

Cette section répertorie tous les systèmes et composants pris en charge pour les builds **Adobe Campaign Classic[!DNL Gold Standard]** 19.1. Les produits et versions ne faisant pas partie de cette liste ne sont pas compatibles avec cette version d’Adobe Campaign.

>[!CAUTION]
>Sauf mention contraire, toutes les versions mineures sont prises en charge.
>
>Adobe Campaign Classic est compatible avec tous les systèmes et outils répertoriés dans cette page. Lorsque des versions spécifiques de ces systèmes et outils tiers arrivent en fin de vie (EOL) avec leurs créateurs respectifs, Adobe Campaign n’est plus compatible avec celles-ci. Elles sont alors supprimées de notre matrice de compatibilité pour la version suivante du produit. Pour éviter tout problème, vérifiez que vous disposez des versions prises en charge des systèmes répertoriés dans la matrice de compatibilité.
>

### Systèmes d’exploitation{#OperatingSystems-gs}

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
<td>Windows Server</td>
<td>
<p>2016</p>
<p>2012 R2</p>
<p>2012</p>
</td>
</tr>
</tbody>
</table>

### Serveurs web{#WebServers-gs}

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

### Outils{#Tools-gs}

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

### Serveurs SGBDR{#RDBMSservers-gs}

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
<td>SQL Server</td>
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

### Connecteurs CRM{#CRMconnectors-gs}

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

### Federated Data Access (FDA){#FederatedDataAccessFDA-gs}

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
<tr><td>SQL Server</td>
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

### Console cliente {#ClientConsoleoperatingsystems}

`:warning:` Les systèmes d&#39;exploitation et le navigateur ci-après sont nécessaires pour utiliser la console cliente Campaign.

#### Systèmes d’exploitation

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

#### Navigateur

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

### SDK mobile{#MobileSDK}

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

### Navigateurs{#Browsers}

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
