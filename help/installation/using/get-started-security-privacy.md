---
product: campaign
title: Liste de contrôle relative à la sécurité et à la confidentialité
description: En savoir plus sur les éléments clés à vérifier en matière de sécurité et de confidentialité
feature: Installation, Privacy, Access Management, Privacy Tools
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: ec40498e-e673-4792-8dcf-8bb7e852b532
source-git-commit: 19b40f0b827c4b5b7b6484fe4953aebe61d00d1d
workflow-type: ht
source-wordcount: '445'
ht-degree: 100%

---

# Liste de contrôle relative à la sécurité et à la confidentialité{#get-started-security-privacy}



Cette section présente les éléments clés à contrôler en ce qui concerne la sécurité et la confidentialité. Certaines configurations ne peuvent être exécutées que par les clients On-premise.

## Confidentialité

<img src="assets/do-not-localize/icon_privacy.svg" width="60px">

La configuration et le renforcement de la confidentialité sont des éléments clés en matière d&#39;optimisation de la sécurité. Voici quelques bonnes pratiques à suivre en matière de confidentialité :

* Protégez les PII de votre client en utilisant HTTPS au lieu de HTTP.
* Utilisez la restriction de l’affichage des PII pour protéger la confidentialité et empêcher toute utilisation abusive des données.
* Vérifiez que les mots de passe chiffrés sont restreints.
* Protégez les pages pouvant contenir des informations personnelles, telles que les pages miroir, les applications web, etc.

[En savoir plus](../../installation/using/privacy.md)

## Gestion des accès

<img src="assets/do-not-localize/icon_access.svg" width="60px">

La gestion des accès joue un rôle important dans le renforcement de la sécurité. Vous trouverez ci-dessous quelques-unes des principales bonnes pratiques à appliquer.

* Créez suffisamment de groupes de sécurité.
* Vérifiez que chaque opérateur dispose des droits d&#39;accès adéquats.
* Évitez d&#39;utiliser l&#39;opérateur admin et d&#39;ajouter trop d&#39;opérateurs au groupe admin.

[En savoir plus](../../installation/using/access-management.md)

## Instructions relatives aux scripts et au codage

<img src="assets/do-not-localize/icon_scripting.svg" width="60px">

Lorsque vous effectuez des tâches de développement dans Adobe Campaign (workflows, Javascript, JSSP, autres), suivez toujours ces instructions :

* **Scripts** : évitez si possible d’utiliser des instructions SQL. Utilisez des fonctions paramétrées plutôt que la concaténation de chaîne et évitez toute injection SQL en ajoutant les fonctions SQL à utiliser à la liste autorisée.

* **Sécurisation du modèle de données** : utilisez des droits nommés pour limiter les actions des opérateurs et ajoutez des filtres système (sysFilter).

* **Ajout de captchas dans les applications web** : découvrez comment ajouter des captchas dans vos pages d’inscription et landing pages publiques.

[En savoir plus](../../installation/using/scripting-coding-guidelines.md)

## Réseau, base de données et SSL/TLS

<img src="assets/do-not-localize/icon_network.svg" width="60px">

La configuration du réseau est un élément très important à vérifier lorsque vous déployez un type d’architecture On-premise.

En outre, vous devez impérativement suivre les instructions de sécurité de votre moteur de base de données.

[En savoir plus](../../installation/using/network-database.md)


## Configuration du serveur

<img src="assets/do-not-localize/icon_server.svg" width="60px">

La configuration doit être effectuée sur tous les serveurs. Les fichiers de configuration sont de type **serverConf.xml** et **`config-<instance>.xml`**. Voici les éléments clés à vérifier :

* **Zones de sécurité** : configurez les zones de sécurité afin qu’elles prennent en compte directement les adresses IP des clients d’un proxy.

* **Protection des téléchargements de fichiers** : limitez les types de fichiers pouvant être téléchargés sur le serveur Adobe Campaign grâce à un nouvel attribut uploadAllowList. Vous pouvez l’utiliser dans le fichier de configuration du serveur.

* **Relais** : affinez la configuration des relais en désactivant les règles de relais pour les modules/applications inutilisés.

* **Protection des connexions sortantes** et **restriction des commandes** (côté serveur)

* Vous pouvez également ajouter des en-têtes HTTP supplémentaires et activer les options checkIPConsistent, enableTLS, sessionTimeOutSec, etc. Pour plus d’informations, consultez la [documentation sur la configuration du serveur Campaign](../../installation/using/configuring-campaign-server.md) et la [description du fichier de configuration du serveur](../../installation/using/the-server-configuration-file.md).

[En savoir plus](../../installation/using/server-configuration.md)

## Configuration du serveur web

<img src="assets/do-not-localize/icon_web.svg" width="60px">

Plusieurs bonnes pratiques doivent être suivies lors de la configuration de votre serveur web (Apache/IIS) :

* Désactivez l’ancienne version de SSL et les chiffrements.
* Supprimez la méthode TRACE.
* Supprimez la bannière.
* Limitez la taille des requêtes pour empêcher le téléchargement de fichiers volumineux.

[En savoir plus](../../installation/using/web-server-configuration.md)
