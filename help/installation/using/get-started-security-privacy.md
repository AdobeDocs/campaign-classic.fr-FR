---
solution: Campaign Classic
product: campaign
title: Prise en main de la sécurité et de la confidentialité
description: En savoir plus sur les éléments clés à vérifier en matière de sécurité et de confidentialité.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: 922603492d2c98d751683d3aa481e9ab19bca70c
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 57%

---


# Prise en main de la sécurité et de la confidentialité {#get-started-security-privacy}

Cette section vous présente les éléments clés à vérifier en matière de sécurité et de confidentialité. Certaines configurations ne peuvent être exécutées que par des clients sur site.

## Confidentialité

<img src="assets/do-not-localize/icon_privacy.svg" width="60px">

La configuration et le renforcement de la confidentialité sont des éléments clés de l&#39;optimisation de la sécurité. Voici quelques bonnes pratiques à suivre en matière de confidentialité :

* Protégez les PII de votre client en utilisant HTTPS au lieu de HTTP.
* Utilisez la limitation de l&#39;affichage des PII pour protéger la confidentialité et empêcher toute utilisation abusive des données.
* Vérifiez que les mots de passe cryptés sont restreints.
* Protégez les pages pouvant contenir des informations personnelles, telles que les pages miroir, les applications web, etc.

[En savoir plus](../../installation/using/privacy.md)

## Gestion des accès

<img src="assets/do-not-localize/icon_access.svg" width="60px">

Gestion des accès est un élément important du renforcement de la sécurité. Voici quelques-unes des meilleures pratiques :

* Créez suffisamment de groupes de sécurité.
* Vérifiez que chaque opérateur dispose des droits d&#39;accès adéquats.
* Evitez d&#39;utiliser l&#39;opérateur admin et d&#39;ajouter trop d&#39;opérateurs au groupe admin.

[En savoir plus](../../installation/using/access-management.md)

## Instructions relatives aux scripts et à l’encodage

<img src="assets/do-not-localize/icon_scripting.svg" width="60px">

Lorsque vous développez en Adobe Campaign (workflows, JavaScript, JSSP, etc.), suivez toujours les consignes suivantes :

* **Scripts** : évitez si possible d’utiliser des instructions SQL. Utilisez des fonctions paramétrables plutôt que la concaténation de chaîne et évitez toute injection SQL en ajoutant les fonctions SQL à utiliser à la liste autorisée.

* **Sécurisez le modèle** de données : utiliser des droits nommés pour limiter les actions des opérateurs, ajouter des filtres système (sysFilter)

* **Ajoutez captchas dans les applications** Web : apprenez à ajouter des casquettes dans vos landings page publics et vos pages d&#39;abonnement.

[En savoir plus](../../installation/using/scripting-coding-guidelines.md)

## Réseau, base de données et SSL/TLS

<img src="assets/do-not-localize/icon_network.svg" width="60px">

Le paramétrage du réseau est un élément très important que vous devez vérifier lorsque vous déployez un type d&#39;architecture on-premise.

Il est également impératif de suivre la sécurité de votre moteur de base de données.

[En savoir plus](../../installation/using/network-database.md)

## Configuration du serveur

<img src="assets/do-not-localize/icon_server.svg" width="60px">

Le paramétrage doit être effectué sur tous les serveurs. Les fichiers de configuration sont du type **serverConf.xml** et **`config-<instance>.xml`**. Voici les éléments essentiels qui doivent être vérifiés :

* **Zone de sécurité** : configurez les zones de sécurité afin qu&#39;elles prennent en compte directement les adresses IP des clients d&#39;un proxy.

* **Protection** du téléchargement de fichiers : limitez les types de fichiers pouvant être téléchargés vers le serveur Adobe Campaign à l’aide d’un nouvel attribut uploadAllowList. Vous pouvez l’utiliser dans le fichier de configuration du serveur.

* **Relais** : affinez le paramétrage des relais en désactivant les règles de relais pour les modules/applications inutilisés.

* **Protection des connexions sortantes** et **restriction des commandes** (côté serveur)

* Vous pouvez également ajouter des en-têtes HTTP supplémentaires et activer les options checkIPConsistent, enableTLS, sessionTimeOutSec, etc. Pour plus d’informations, consultez la [documentation sur la configuration du serveur Campaign](../../installation/using/configuring-campaign-server.md) et la [description du fichier de configuration du serveur ](../../installation/using/the-server-configuration-file.md).

[En savoir plus](../../installation/using/server-configuration.md)

## Configuration du serveur web

<img src="assets/do-not-localize/icon_web.svg" width="60px">

Plusieurs bonnes pratiques doivent être suivies lors de la configuration de votre serveur Web (Apache/IIS) :

* Désactivez l&#39;ancienne version de SSL et les chiffrements.
* Supprimer la méthode de TRACE
* Supprimez la bannière :
* Limiter la taille de la requête pour empêcher le téléchargement de fichiers importants

[En savoir plus](../../installation/using/web-server-configuration.md)
