---
product: campaign
title: Dernière version
description: Notes de mise à jour de la dernière version de Campaign Classic v7
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: cdbcfc5aa0614e41ce76cb777fec58fbd01797d2
workflow-type: ht
source-wordcount: '908'
ht-degree: 100%

---

# Dernière version {#latest-release}

Cette page répertorie les nouvelles fonctionnalités, les améliorations et les correctifs apportés à la **dernière version de Campaign Classic v7**. Chaque nouvelle build est fournie avec un statut matérialisé par une couleur. En savoir plus sur les statuts de build de Campaign Classic v7 dans [cette page](rn-overview.md).

## Version 7.4.2  {#release-7-4-2}

### Build 9391 {#build-9391}

[!BADGE Disponibilité limitée]{type=Informative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=fr#rn-statuses" tooltip="Disponibilité limitée"}

_12 mai 2025_

Ce build comprend les correctifs suivants :

* Correction d’un problème de postupgrade rencontré dans les configurations autres qu’Oracle. (NEO-87012)
* Correction d’un problème de serveur principal TLS/HTTPS affectant à la fois la console cliente et le serveur. (NEO-87432)

### Build 9390 {#build-9390}

[!BADGE Disponibilité générale]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=fr#rn-statuses" tooltip="Disponibilité générale"}

_2 avril 2025_

<!--
### Compatibility updates {#comp-7-4-2}

This release comes with the following compatibility updates:

* JQuery library update: fixes multiple UI issues (reports, web apps)
* PostgreSQL 15 and 16

-->

**Améliorations de la sécurité**

Cette version comprend plusieurs correctifs de sécurité.

La connexion aux solutions et applications Adobe par le biais du compte externe **[!UICONTROL Adobe Experience Cloud]** a été mise à jour pour renforcer la sécurité.

**Corrections majeures**

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


**Autres corrections**

Les problèmes suivants ont également été corrigés dans cette version :

* Correction d’un problème empêchant l’activité **Chargement de données (fichier)** de charger les fichiers vers le serveur<!--after an upgrade to version 8.3.8-->. Il est désormais possible de charger des fichiers sans rencontrer de progression bloquée ni d’erreurs dans la console. (NEO-47269)

* Correction des erreurs de segmentation dans Apache <!--following an upgrade to Adobe Campaign Classic 7.2.2 build 9349-->. Ce correctif empêche la génération des fichiers principaux et assure un fonctionnement stable du serveur. (NEO-59059)

* Résolution d’un problème de connectivité avec la base de données Google BigQuery <!--after upgrading to version 7.3.3 build 9359-->. Il est désormais possible de tester les connexions avec succès à l’aide du compte externe GCP. (NEO-62455)

* Compatibilité améliorée pour la mise à jour des colonnes Boolean et Datetime dans les tableaux Google BigQuery via Federated Data Access (FDA). Ce correctif garantit la gestion appropriée des types de données lors des opérations d’insertion/de mise à jour. (NEO-65774)

* Correction d’une vulnérabilité d’injection de ressources qui permettait l’injection d’éléments HTML dans des points d’entrée e-mail par des tiers malveillants. Cette amélioration de la sécurité empêche tout accès non autorisé et toute tentative d’hameçonnage. (NEO-66462)

* Correction d’erreurs intermittentes lors de l’insertion de données dans les tableaux Google BigQuery en raison de problèmes liés au contenu HTTP ou au codage de transfert. Ce correctif garantit la stabilité des workflows de chargement de données. (NEO-66989)

* Correction d’une vulnérabilité de traversée de chemin dans la méthode `File.list()` au sein des workflows. Cette amélioration de la sécurité empêche les accès non autorisés aux répertoires et protège les fichiers sensibles. (NEO-77898)

* Correction d’un problème où les logs de diffusion SMS ne passaient pas correctement au statut « reçu sur mobile ». Cette amélioration garantit la précision des rapports de diffusion. (NEO-78843)

* Résolution des erreurs de connexion dans Adobe Campaign Classic lors de l’utilisation d’Azure Federated Data Access (FDA). Il est désormais possible de se connecter via la console cliente. (NEO-79373)

* Correction d’un crash dans les workflows causé par la méthode `CCurlAzureBlobStorage::UploadStream()`. Cette amélioration garantit une exécution stable des workflows. (NEO-79598)

* Activation de deux indicateurs de compilation critiques (`ControlFlowGuard` et `StackProtection`) sur Windows afin de renforcer la sécurité du produit et de réduire les risques d’exploitation. (NEO-80145)

* Correction d’un problème où les statuts d’événement étaient envoyés de manière incorrecte alors que le broadlog était en échec. Cette amélioration garantit une création de rapports précis sur les événements. (NEO-80245)

* Le jeton d’actualisation et le jeton d’accès OAuth pour POP3 sont désormais enregistrés dans la base de données et l’erreur `Authentication failure: unknown user name or bad password` n’apparaît plus après expiration du jeton d’actualisation. (NEO-80683)

* Une option `XApiKey` est désormais utilisée comme valeur de l’identifiant client pour se connecter à Adobe Analytics, à la place de l’identifiant client du compte externe Marketing Cloud (MAC). (NEO-80434)

* Correction d’un problème où les comptes inMail rencontraient des erreurs d’authentification en raison de l’expiration du jeton. Il est désormais possible de tester la connexion et de redémarrer le serveur pour résoudre des problèmes similaires. (NEO-80683)

* Amélioration des fonctionnalités de l’API analytique en garantissant que toutes les requêtes utilisent une clé API cohérente (Campaign1) pour l’authentification, même en cas de changement d’identifiant client aléatoire. Cela garantit un suivi analytique fluide. (NEO-80434)

* Amélioration du connecteur FDA (Federated Data Access) pour BigQuery en permettant d’ajuster la période de délai d’expiration des requêtes. Cette amélioration empêche les erreurs de délai d’expiration lors de requêtes longues. (NEO-81222)

* Mise à jour du processus de mise à niveau de la version Campaign <!--7.4.1--> pour inclure les dépendances requises. Cette amélioration simplifie le processus de mise à niveau. (NEO-81433)

* Correction d’un problème de crash de la console lors de l’utilisation d’un sous-workflow avec un champ `enum`. Cette amélioration garantit une exécution stable des workflows. (NEO-81864)

* Correction d’un problème où les processus enfant MTA restaient bloqués, empêchant l’utilisation des créneaux de diffusion. Ce correctif garantit le bon fonctionnement des diffusions par notification push et WhatsApp. (NEO-82351)

* Correction d’un problème où les diffusions restaient bloquées en attente de personnalisation à cause d’activités de diffusion en pause. Cette amélioration assure le bon déroulement des diffusions. (NEO-82781)

* Amélioration de la connexion IMS en exploitant le point d’entrée CampaignIO pour l’authentification. Cette amélioration simplifie le processus de connexion. (NEO-82838)

* Nouvelle correction des erreurs de délai d’expiration liées à Federated Data Access (FDA) à Google BigQuery pour garantir une exécution stable des requêtes après le déploiement du correctif. (NEO-82923)

* Correction d’un problème d’espace lors du chargement de grands volumes de données dans les tableaux Teradata. Cette amélioration garantit la stabilité des opérations de chargement de données. (NEO-83252)

* Correction d’un problème d’échec des requêtes GCP dû à des comparaisons incohérentes entre les dates et les horodatages <!--after upgrading to version 9383-->. Cette amélioration garantit la compatibilité des requêtes. (NEO-83826)

* Correction des échecs de diffusion causés par la reprise d’activités de diffusion en pause. Ce correctif garantit la réussite de l’exécution de la diffusion. (NEO-83809)

* Correction des erreurs d’authentification avec le connecteur FDA (Federated Data Access) pour Snowflake lors de l’utilisation de l’authentification par clé privée. Cette amélioration garantit des connexions réussies à la base de données. (NEO-84024)

* Mise en œuvre de modifications du système de surveillance (watchdog) pour résoudre le blocage des créneaux MTA enfant causé par des processus figés. Cette amélioration garantit le bon déroulement des opérations de diffusion. (NEO-84553)

* Renforcement des vérifications d’attente JavaScript pour corriger le blocage des créneaux MTA enfant causé par des processus en cours d’exécution. Ce correctif garantit la stabilité des opérations de diffusion. (NEO-85150)

