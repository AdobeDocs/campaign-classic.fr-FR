---
product: campaign
title: Notes de mise à jour de [!DNL Gold Standard]
description: Notes de mise à jour de Campaign Classic [!DNL Gold Standard]
feature: Vue d’ensemble
role: Business Practitioner
level: Beginner
exl-id: 9e3a11b1-3070-4d90-91d5-7c559bdd500e
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1058'
ht-degree: 100%

---

# Notes de mise à jour de [!DNL Gold Standard]{#gold-standard}

Cette page répertorie les versions de [!DNL Gold Standard]. Pour en savoir plus sur Campaign, reportez-vous à [!DNL Gold Standard][cette page](gs-overview.md).

## ![](assets/do-not-localize/green_2.png) [!DNL Gold Standard] version 11 {#gs-11}

_14 avril 2021_

Le build 9032@d030c36 comprend le correctif suivant :

* Correction d&#39;une régression de la console cliente qui provoquait des messages d&#39;erreur persistants sur l&#39;écran de connexion IMS. (NEO-34821)

**La mise à niveau de la console uniquement est obligatoire. Aucune mise à niveau du serveur n’est requise.**

_2 mars 2021_

Le build 9032@10c2709 comprend le correctif suivant :

* Correction d’une régression qui empêchait l’utilisation de certains composants de la console, tels que le sélecteur de date et la gestion des images dans les diffusions. (NEO-31453, NEO-31454)

**La mise à niveau de la console uniquement est obligatoire. Aucune mise à niveau du serveur n’est requise.**

>[!NOTE]
>
> Connectez-vous à la [distribution logicielle Adobe](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) pour télécharger la nouvelle version. Découvrez comment proposer la mise à jour de la console à tous les utilisateurs finaux [sur cette page](../../installation/using/client-console-availability-for-windows.md).

_22 décembre 2020_

>[!CAUTION]
>
> * Cette version s’accompagne d’un nouveau protocole de connexion : si vous vous connectez à Campaign via Adobe Identity Service (IMS), une mise à niveau est obligatoire pour que le serveur Campaign et la console client puissent se connecter après le **30 juin 2021**.
> * Cette version s’accompagne d’un [correctif de sécurité](https://helpx.adobe.com/security/products/campaign/apsb21-04.html) : la mise à niveau est obligatoire pour renforcer la sécurité de votre environnement.
> * Si vous utilisez l’intégration Experience Cloud Triggers par le biais de l’authentification oAuth, vous devez passer à Adobe I/O comme décrit [sur cette page](../../integrations/using/configuring-adobe-io.md). Le mode d’authentification oAuth hérité avec Campaign sera mis hors service le **30 novembre 2021**.
>
>Pour en savoir plus, consultez le [[!DNL Gold Standard] FAQ sur la mise à niveau vers la version 11](https://helpx.adobe.com/fr/campaign/kb/gold-standard-upgrade.html).

Le build 9032@d3b452f comprend les améliorations et correctifs suivants :

* Le protocole de connexion a été mis à jour pour suivre le nouveau mécanisme dʼauthentification IMS.

* L’authentification de l’intégration des Triggers basée à lʼorigine sur la configuration de lʼauthentification oAUTH pour accéder au pipeline a été modifiée et déplacée vers Adobe I/O. [En savoir plus](../../integrations/using/configuring-adobe-io.md)

* Après la [fin de la prise en charge du protocole binaire hérité des APN iOS](https://developer.apple.com/news/?id=c88acm2b), toutes les instances utilisant ce protocole sont mises à jour vers le protocole HTTP/2 durant la mise à niveau.

* Correction d’un problème de sécurité afin de renforcer la protection contre les problèmes SSRF (Server Side Request Forgery). (NEO-27777)

* Correction d’un problème en raison duquel les workflows échouaient lors de l’exécution d’une activité d’**enrichissement**. (NEO-17338)

## ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] version 10 {#gs-10}

_7 juillet 2020_

Le build 9032@efd8a94 comprend le correctif suivant :

Correction d’un problème qui empêchait le tracking de fonctionner lorsque la fonction de signature était désactivée. (NEO-26411)

>[!CAUTION]
>
>Nous vous recommandons de mettre à niveau la console cliente avec celle disponible dans cette version. Consultez à ce sujet [cette page](../../installation/using/installing-the-client-console.md)

## ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] version 9 {#gs-9}

_22 juin 2020_

Le build 9032@800be2e comprend les correctifs suivants :

* Le connecteur HTTP2 iOS a été amélioré (mises à jour tierces et gestion des erreurs). (NEO-25904, NEO-25903, NEO-25799)

Les correctifs suivants sont liés au mécanisme de sécurité des liens de tracking (apprenez-en davantage dans la [liste de contrôle Sécurité et confidentialité](https://helpx.adobe.com/fr/campaign/kb/acc-security.html#signature-mechanism)) :

* Correction d’un problème qui empêchait le suivi des « clics de notification » de fonctionner (notifications push iOS et Android). (NEO-25965)
* Correction d’un problème qui pouvait empêcher d’ouvrir/de cliquer sur les URL de tracking lors de l’utilisation de certaines anciennes versions d’Outlook.  (NEO-25688)
* Correction d’un problème qui empêchait le suivi des URL à l’aide de fragments dans les paramètres de personnalisation (balises d’ancrage avec signe dièse) de fonctionner. (NEO-25774)
* Correction d’un problème lié au service anti-hameçonnage. (NEO-25283)
* Correction d’un problème de suivi lors de l’utilisation de formules de tracking personnalisées spécifiques. (NEO-25277)


## ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] version 8{#gs-8}

_29 avril 2020_

Le build 9032@3a9dc9c comprend les correctifs suivants :

* Amélioration de la sécurité des liens de tracking dans les emails. Cette option est activée par défaut pour tous les clients. Une autre fonctionnalité de sécurité améliorée est disponible. Il est possible de l’activer en contactant l&#39;Assistance clientèle. Pour plus d’informations sur la fonctionnalité et la procédure d’activation pour les clients non hébergés, consultez la [liste de contrôle de sécurité et de confidentialité](https://helpx.adobe.com/campaign/kb/acc-security.html#signature-mechanism).

>[!CAUTION]
>
>Si vous rencontrez des problèmes avec les notifications push lors de l’utilisation de liens de tracking, ou avec les diffusions lors de l’utilisation de balises d’ancrage, nous vous recommandons de désactiver le nouveau mécanisme de signature pour les liens de tracking. [La procédure est détaillée dans cette page](https://helpx.adobe.com/campaign/kb/acc-security.html#signature-mechanism)

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

## ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] version 6{#gs-6}

_9 mars 2020_

Le build 9032@19f73c5 comprend le correctif suivant :

* Correction d’un problème de comptes externes, lié à l’utilisation de FTP sur SSL. (NEO-20498)

## ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] version 5{#gs-5}

_17 décembre 2019_

Le build 9032@d6b8062 comprend le correctif suivant :

* Correction d’un problème de suivi sur les canaux de communication suivants : mobile (SMS, MMS), push (iOS, Android) et réseaux sociaux (Facebook, Twitter). (NEO-19595)

## ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] version 4{#gs-4}

_11 décembre 2019_

Le build 9032@bc4a935 comprend le correctif suivant :

* Correction d’un problème de performances lors de l’envoi de messages avec une base de données MSSQL. (NEO-17558)

## ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] version 3{#gs-3}

_20 novembre 2019_

Le build 9032@3468c7b comprend les correctifs suivants :

* Correction d’un problème de connexion via l’authentification IMS. (NEO-17312)
* Correction d’un problème lors de l’affichage de rapports cumulatifs sur plusieurs diffusions. (NEO-18165)
* Correction d’un problème susceptible de bloquer ou de provoquer le blocage du serveur web.

## ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] version 2{#gs-2}

_19 septembre 2019_

Le build 9032@cee805c comprend les correctifs suivants :

* Correction d’un problème lors de l’utilisation du connecteur CRM pour Salesforce. (NEO-17712)
* Correction d’un problème d’index qui pouvait entraîner des problèmes de performances lors de l’envoi de messages transactionnels.

## ![](assets/do-not-localize/red_2.png) Version 19.1.4 - Build 9032{#release-19-1-4-build-9032}

_13 août 2019_

Le build 19.1.4 initial comprend les correctifs suivants :

* Correction d&#39;un problème lié à l&#39;activité du planificateur qui générait des messages d&#39;erreur indésirables lors de la configuration de l&#39;assistant. Annulation de la mise à jour à partir de NEO-11662. (NEO-17097)
* Correction d&#39;une régression causée par NEO-12727 qui entraînait l&#39;arrêt des workflows lorsqu&#39;une activité de test était exécutée deux fois. (NEO-16835)
* Correction d&#39;un problème qui entraînait le renvoi d&#39;un code HTTP erroné (HTTP 200 OK à la place de HTTP 403 Interdit) lorsqu&#39;un jeton de session non valide ou ayant expiré était utilisé dans les appels d&#39;API. (NEO-16826)
* Correction d&#39;un problème lié à la clé DKIM qui n&#39;était plus incorporée dans les emails, ce qui entraînait des problèmes de délivrabilité. (NEO-16804)
* Correction de divers problèmes liés à la planification des workflows. Les workflows devaient être exécutés une fois par jour sans tenir compte de la configuration du planificateur. (NEO-16619, NEO-16426)
