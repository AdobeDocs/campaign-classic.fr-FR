---
title: ' Version Gold Standard '
seo-title: ' Version Gold Standard '
description: ' Version Gold Standard '
seo-description: null
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
source-git-commit: 7ff58cee4b189c51fbff20880ac800d91f1b0147
workflow-type: tm+mt
source-wordcount: '815'
ht-degree: 80%

---


#  Version Gold Standard {#gold-standard}

En tant qu&#39;utilisateur Gold Standard, vous bénéficiez automatiquement de la mise à jour Gold Standard avec la dernière version stable sans aucune action.

Les clients sur site et les clients hybrides peuvent également bénéficier des versions de Gold Standard.

Il s’agit de notre version de support à long terme. Si vous migrez à partir d’une ancienne version, nous vous recommandons d’effectuer d’abord la mise à niveau vers cette version.

Cette page liste les versions Gold Standard.

Pour plus d&#39;informations sur la mise à niveau vers Gold Standard, reportez-vous à cet [article](https://helpx.adobe.com/fr/campaign/kb/gold-standard.html).

## ![](assets/do-not-localize/green_2.png) Version Gold Standard 10{#gs-10}

_7 juillet 2020_

La version 9032@efd8a94 inclut les correctifs suivants :

* Correction d’un problème qui empêchait le suivi de fonctionner lorsque la fonction de signature était désactivée. (NEO-26411)

>[!CAUTION]
>
>Nous vous recommandons de mettre à niveau la console cliente avec celle disponible dans cette version. Consultez à ce sujet cette [page](../../installation/using/installing-the-client-console.md)

## ![](assets/do-not-localize/red_2.png) Version Gold Standard 9{#gs-9}

_22 juin 2020_

La version 9032@800be2e comprend les correctifs suivants :

* Le connecteur HTTP2 iOS a été amélioré (mises à jour tierces et gestion des erreurs). (NEO-25904, NEO-25903, NEO-25799)

Les correctifs suivants sont liés au mécanisme de sécurité des liens de tracking (voir la [liste de contrôle Sécurité et confidentialité](https://helpx.adobe.com/fr/campaign/kb/acc-security.html#signature-mechanism)) :

* Correction d’un problème qui empêchait le suivi des « clics de notification » de fonctionner (notifications Push iOS et Android). (NEO-25965)
* Correction d’un problème qui pouvait empêcher d’ouvrir/de cliquer sur les URL de tracking lors de l’utilisation de certaines anciennes versions d’Outlook.  (NEO-25688)
* Correction d’un problème qui empêchait le suivi des URL à l’aide de fragments dans les paramètres de personnalisation (balises d’ancrage avec signe dièse) de fonctionner. (NEO-25774)
* Correction d’un problème lié au service anti-hameçonnage. (NEO-25283)
* Correction d’un problème de suivi lors de l’utilisation de formules de tracking personnalisées spécifiques. (NEO-25277)

## ![](assets/do-not-localize/red_2.png) Version Gold Standard 8{#gs-8}

_29 avril 2020_

La version 9032@3a9dc9c comprend les correctifs suivants :

* Amélioration de la sécurité des liens de tracking dans les emails. Cette option est activée par défaut pour tous les clients. Une autre fonctionnalité de sécurité améliorée est disponible. Il est possible de l’activer en contactant le service Assistance clientèle. Pour plus d’informations sur la fonctionnalité et la procédure d’activation pour les clients non hébergés, consultez la [liste de contrôle de sécurité et de confidentialité](https://helpx.adobe.com/fr/campaign/kb/acc-security.html#signature-mechanism).

>[!CAUTION]
>
>Si vous rencontrez des problèmes avec les notifications Push lors de l’utilisation de liens de tracking, ou avec les diffusions lors de l’utilisation de balises d’ancrage, nous vous recommandons de désactiver le nouveau mécanisme de signature pour les liens de tracking. La procédure est détaillée dans cette [page](https://helpx.adobe.com/fr/campaign/kb/acc-security.html#signature-mechanism)

* Correction d’un problème qui empêchait l’affichage des images sur les diffusions LINE. (NEO-23207)
* Correction d’un problème lié à l’activité **Transfert de fichier** qui empêchait le fonctionnement de l’authentification par clé SFTP sur Debian 9. (NEO-23183)
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

## ![](assets/do-not-localize/orange_2.png) Version Gold Standard 6{#gs-6}

_9 mars 2020_

La version 9032@19f73c5 inclut les correctifs suivants :

* Correction d’un problème de comptes externes, lié à l’utilisation de FTP sur SSL. (NEO-20498)

## ![](assets/do-not-localize/orange_2.png) Version Gold Standard 5{#gs-5}

_17 décembre 2019_

La version 9032@d6b8062 inclut les correctifs suivants :

* Correction d’un problème de suivi sur les canaux de communication suivants : mobile (SMS, MMS), push (iOS, Android) et réseaux sociaux (Facebook, Twitter). (NEO-19595)

## ![](assets/do-not-localize/orange_2.png) Version Gold Standard 4{#gs-4}

_11 décembre 2019_

La version 9032@bc4a935 inclut les correctifs suivants :

* Correction d’un problème de performances lors de l’envoi de messages avec une base de données MSSQL. (NEO-17558)

## ![](assets/do-not-localize/orange_2.png) Version Gold Standard 3{#gs-3}

_20 novembre 2019_

La version 9032@3468c7b comprend les correctifs suivants :

* Correction d’un problème de connexion via l’authentification IMS. (NEO-17312)
* Correction d’un problème lors de l’affichage de rapports cumulatifs sur plusieurs diffusions. (NEO-18165)
* Correction d’un problème susceptible de bloquer ou de provoquer le blocage du serveur web.

## ![](assets/do-not-localize/red_2.png) Version Gold Standard 2{#gs-2}

_19 septembre 2019_

La version 9032@cee805c comprend les correctifs suivants :

* Correction d’un problème lors de l’utilisation du connecteur CRM pour Salesforce. (NEO-17712)
* Correction d’un problème d’index qui pouvait entraîner des problèmes de performances lors de l’envoi de messages transactionnels.

## ![](assets/do-not-localize/red_2.png) Version 19.1.4 - Build 9032{#release-19-1-4-build-9032}

_13 août 2019_

La version 19.1.4 initiale comprend les correctifs suivants :

* Correction d&#39;un problème lié à l&#39;activité du planificateur qui générait des messages d&#39;erreur indésirables lors de la configuration de l&#39;assistant. Annulation de la mise à jour à partir de NEO-11662. (NEO-17097)
* Correction d&#39;une régression causée par NEO-12727 qui entraînait l&#39;arrêt des workflows lorsqu&#39;une activité de test était exécutée deux fois. (NEO-16835)
* Correction d&#39;un problème qui entraînait le renvoi d&#39;un code HTTP erroné (HTTP 200 OK à la place de HTTP 403 Interdit) lorsqu&#39;un jeton de session non valide ou ayant expiré était utilisé dans les appels d&#39;API. (NEO-16826)
* Correction d&#39;un problème lié à la clé DKIM qui n&#39;était plus incorporée dans les emails, ce qui entraînait des problèmes de délivrabilité. (NEO-16804)
* Correction de divers problèmes liés à la planification des workflows. Les workflows devaient être exécutés une fois par jour sans tenir compte de la configuration du planificateur. (NEO-16619, NEO-16426)
