---
product: campaign
title: Dernière version
description: Notes de mise à jour de la dernière version de Campaign Classic v7
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 458821770c6233ec1893d4efe60169516b311bdd
workflow-type: tm+mt
source-wordcount: '870'
ht-degree: 26%

---

# Dernière version {#latest-release}

Cette page répertorie les nouvelles fonctionnalités, les améliorations et les correctifs apportés à la **dernière version de Campaign Classic v7**. Chaque nouvelle build est fournie avec un statut matérialisé par une couleur. En savoir plus sur les statuts de build de Campaign Classic v7 dans [cette page](rn-overview.md).

## Version 7.4.2 - Build 9390 {#release-7-4-2}

[!BADGE Disponibilité générale]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=fr#rn-statuses" tooltip="Disponibilité générale"}

_2 avril 2025_

<!--
### Compatibility updates {#comp-7-4-2}

This release comes with the following compatibility updates:

* JQuery library update: fixes multiple UI issues (reports, web apps)
* PostgreSQL 15 and 16

-->

### Améliorations de la sécurité {#security-7-4-2}

Cette version comprend plusieurs correctifs de sécurité.

La connexion aux solutions et applications Adobe par le biais du compte externe **[!UICONTROL Adobe Experience Cloud]** a été mise à jour pour renforcer la sécurité.

### Correctifs majeurs {#release-7-4-2-fixes}

Cette version comprend les correctifs principaux suivants :

* Connexion TLS/SMPP : correction des problèmes de stabilité SMPP

* Correctifs BigQuery Google :

   * Correction des régressions sur les types de données booléens
   * Correction des problèmes de paramètres du proxy
   * Correction des régressions sur les types de données de date et heure
   * Correction de la stabilité de la charge en masse (bulk load)
   * Amélioration des tests internes sur les versions ODBC
   * Correction d’un problème lié aux caractères spéciaux sur la chaîne de connexion
   * Suppression du délai d’expiration par défaut (5 minutes) sur les requêtes BigQuery Google

* MTA (Mail Transfer Agent) : correction du blocage d’un enfant MTA orphelin au statut **[!UICONTROL Démarrage en attente]**.


### Autres correctifs {#release-7-4-2-other-fixes}

Les problèmes suivants ont également été corrigés dans cette version :

* Correction d’un problème en raison duquel l’activité **Chargement de données (fichier)** ne parvenait pas à charger les fichiers sur le serveur<!--after an upgrade to version 8.3.8-->. Les utilisateurs peuvent désormais charger des fichiers sans rencontrer de progression bloquée ou d’erreurs de console. (NEO-47269)

* Résolution des erreurs d’erreur de segmentation dans Apache <!--following an upgrade to Adobe Campaign Classic 7.2.2 build 9349-->. Ce correctif empêche la génération des fichiers principaux et assure un fonctionnement stable du serveur. (NEO-59059)

* Correction d’un problème de connectivité avec le <!--after upgrading to version 7.3.3 build 9359--> de base de données BigQuery Google. Les utilisateurs peuvent désormais tester les connexions avec succès à l’aide du compte externe GCP. (NEO-62455)

* Amélioration de la compatibilité pour les mises à jour des colonnes Boolean et Datetime dans les tableaux BigQuery Google à l’aide de Federated Data Access (FDA). Ce correctif garantit la gestion appropriée des types de données lors des opérations d’insertion/mise à jour. (NEO-65774)

* Correction d’une vulnérabilité d’injection de ressources qui permettait aux attaquant(e)s d’injecter des éléments HTML dans des points d’entrée email. Cette amélioration de la sécurité empêche tout accès non autorisé et toute tentative d’hameçonnage. (NEO-66462)

* Résolution des erreurs intermittentes lors de l’insertion de données dans les tables BigQuery Google en raison de problèmes de contenu HTTP ou de codage de transfert. Ce correctif garantit la stabilité des workflows de chargement des données. (NEO-66989)

* Correction d’une vulnérabilité de traversée de chemin dans la méthode `File.list()` des workflows. Cette amélioration de la sécurité empêche l’accès non autorisé aux répertoires et protège les fichiers sensibles. (NEO-77898)

* Correction d’un problème en raison duquel les logs de diffusion SMS ne se mettaient pas correctement à jour vers le statut « reçu sur mobile ». Cette amélioration garantit la précision des rapports de diffusion. (NEO-78843)

* Résolution des erreurs de connexion dans Adobe Campaign Classic lors de l’utilisation d’Azure Federated Data Access (FDA). Les utilisateurs peuvent désormais se connecter via la console cliente. (NEO-79373)

* Correction d&#39;un crash des workflows provoqué par la méthode `CCurlAzureBlobStorage::UploadStream()`. Cette amélioration garantit une exécution stable du workflow. (NEO-79598)

* Activation de deux indicateurs de compilation critiques (`ControlFlowGuard` et `StackProtection`) sous Windows pour améliorer la sécurité du produit et réduire les risques d&#39;exploitation. (NEO-80145)

* Correction d’un problème en raison duquel les statuts d’événement étaient envoyés incorrectement lorsque le broadlog était dans un état d’échec. Cette amélioration garantit la précision des rapports d’événement. (NEO-80245)

* L’actualisation OAuth POP3 et le jeton d’accès sont désormais enregistrés dans la base de données et `Authentication failure: unknown user name or bad password`’erreur ne s’affiche plus après l’expiration du jeton d’actualisation. (NEO-80683)

* Une option `XApiKey` est désormais utilisée comme valeur pour que l’identifiant client se connecte à Adobe Analytics au lieu d’utiliser l’identifiant client du compte externe Marketing Cloud (MAC). (NEO-80434)

* Correction d’un problème en raison duquel les utilisateurs d’inMail rencontraient des erreurs d’authentification dues à l’expiration des jetons. Les utilisateurs peuvent maintenant tester la connexion et redémarrer le serveur pour résoudre des problèmes similaires. (NEO-80683)

* Amélioration de la fonctionnalité de l’API Analytics en veillant à ce que tous les appels Analytics utilisent une clé API cohérente (Campaign1) pour l’authentification, même lorsque vous passez à un identifiant client aléatoire. Cela garantit un suivi analytique transparent. (NEO-80434)

* Amélioration du connecteur BigQuery Federated Data Access (FDA) en permettant aux utilisateurs d’ajuster le délai d’expiration des requêtes. Cette amélioration évite les erreurs de délai d’expiration lors de requêtes longues. (NEO-81222)

* Mise à jour du processus de mise à niveau de la version de Campaign <!--7.4.1--> pour inclure les dépendances requises. Cette amélioration simplifie le processus de mise à niveau pour les utilisateurs et utilisatrices. (NEO-81433)

* Correction d&#39;un problème de blocage de la console lors de l&#39;utilisation d&#39;un sous-workflow en combinaison avec un champ `enum`. Cette amélioration garantit une exécution stable du workflow. (NEO-81864)

* Correction d’un problème en raison duquel les processus enfants du MTA étaient bloqués, bloquant les emplacements de diffusion. Ce correctif garantit le bon fonctionnement des opérations de diffusion pour les communications push et WhatsApp. (NEO-82351)

* Correction d’un problème où les diffusions étaient bloquées dans la personnalisation en attente en raison d’activités de diffusion en pause. Cette amélioration garantit la réussite de l’exécution de la diffusion. (NEO-82781)

* Amélioration de la fonctionnalité de connexion IMS en utilisant le point d’entrée Campaign IO pour l’authentification. Cette amélioration simplifie le processus de connexion. (NEO-82838)

* Erreurs de délai d’expiration BigQuery Federated Data Access (FDA) Google retraitées afin d’assurer une exécution de requête stable après le déploiement du correctif. (NEO-82923)

* Correction d’un problème d’espace lors du chargement de gros volumes de données dans les tables Teradata. Cette amélioration garantit la stabilité des opérations de chargement des données. (NEO-83252)

* Correction d’un problème en raison duquel les requêtes GCP échouaient en raison de comparaisons de dates et d’horodatages <!--after upgrading to version 9383-->. Cette amélioration garantit la compatibilité des requêtes. (NEO-83826)

* Correction des échecs de diffusion causés par la reprise des activités de diffusion en pause. Ce correctif garantit la réussite de l’exécution de la diffusion. (NEO-83809)

* Correction des erreurs d’authentification avec le connecteur Snowflake Federated Data Access (FDA) lors de l’utilisation de l’authentification par clé privée. Cette amélioration garantit le succès des connexions à la base de données. (NEO-84024)

* Mise en œuvre de modifications de surveillance pour résoudre le blocage des emplacements d’enfant MTA causé par des processus bloqués. Cette amélioration garantit le bon déroulement des opérations de diffusion. (NEO-84553)

* L’attente JavaScript augmentée vérifie les blocages de slot d’enfant MTA causés par des processus en état de fonctionnement. Ce correctif garantit la stabilité des opérations de diffusion. (NEO-85150)

