---
product: campaign
title: Dernière version
description: Dernières notes de mise à jour de Campaign Classic v7
feature: Overview
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: e4dfdd32c07753ee9e202ab4e4bf815485e47d8b
workflow-type: tm+mt
source-wordcount: '1034'
ht-degree: 17%

---

# Dernière version{#latest-release}

![](../../assets/v7-only.svg)

Cette page répertorie les nouvelles fonctionnalités, les améliorations et les correctifs apportés par **dernière version de Campaign Classic v7**. Chaque nouvelle version est fournie avec un état matérialisé par une couleur. En savoir plus sur les statuts de build de Campaign Classic v7 dans [cette page](rn-overview.md).

## ![](assets/do-not-localize/green_2.png) Version 7.2.1 - Build 9346 {#release-7-2-1}

_10 janvier 2022_

**Amélioration de la sécurité**

Plusieurs améliorations ont été apportées à la sécurité des comptes FDA :

* Les pilotes ODBC sont désormais directement installés avec des tiers Adobe Campaign. Les étapes manuelles ne sont plus nécessaires pour installer ces pilotes.
* Lors de la configuration de votre compte externe FDA, vous pouvez désormais vous connecter à votre compte de Snowflake à l’aide de l’authentification par paire de clés pour une sécurité d’authentification améliorée. [En savoir plus](../../installation/using/configure-fda-snowflake.md)
* Lors de la configuration de votre compte externe FDA, vous pouvez désormais vous connecter à votre compte Azure synapse Analytics à l’aide de l’identité gérée affectée par le système. [En savoir plus](../../installation/using/configure-fda-synapse.md#azure-external)


**Améliorations**

* Connecteur Microsoft Dynamics CRM 365

   Des correctifs critiques ont été appliqués concernant l’API web de Microsoft Dynamics Connector :

   * Correction d’un problème, lors d’un import déclenché par un workflow, en raison duquel les valeurs nulles des champs de type chaîne étaient enregistrées comme nulles au lieu de valeurs vides.
   * Correction d’un problème qui entraînait l’erreur suivante pour l’import ou l’export de données à l’aide d’appels API web : &quot;URI non valide : Le schéma d’URI est trop long.&quot;
   * Correction de divers problèmes lors de l’importation, à partir de Microsoft Dynamics 365, de données contenant des champs de recherche.

* Connecteur FDA Google BigQuery

   * Google BigQuery FDA Connector est désormais disponible pour les déploiements hébergés. [En savoir plus](../../installation/using/configure-fda-google-big-query.md)
   * Ajout de la prise en charge de l’activation des connexions à un serveur proxy pour le connecteur FDA Google BigQuery. Les options de proxy requises peuvent être définies via le champ Options dans la configuration du compte externe. [En savoir plus](../../installation/using/configure-fda-google-big-query.md#google-external)

**Autres changements**

* Suite à leur abandon, les activités d’action Microsoft CRM, Salesforce, Oracle CRM On Demand ont été supprimées de l’interface. Pour paramétrer la synchronisation des données entre Adobe Campaign et un système CRM, vous pouvez utiliser l&#39;activité Connecteur CRM . [En savoir plus](../../workflow/using/crm-connector.md)
* Le **[!UICONTROL Identifiant crypté]** a été ajouté au schéma des visiteurs (nms:visitor). Ce champ est calculé et doit être utilisé pour les applications web. Cela s&#39;applique lorsque le canal Ligne est paramétré sur l&#39;instance de mid-sourcing.
* Les sources de données CRM peuvent désormais être utilisées avec la variable **Modification de la source de données** activité.
* Une nouvelle option a été ajoutée dans la variable **Gestion des erreurs** propriétés des activités de workflow : Le **Abandon en erreur** arrête automatiquement le workflow. Vous ne pourrez pas le redémarrer par la suite (NEO-29661). [En savoir plus](../../workflow/using/advanced-parameters.md#in-case-of-errors)
* Une séquence dédiée est désormais utilisée pour générer les Principales clés de la table nmsGroup, qui sert à créer des groupes statistiques de destinataires. Auparavant, la séquence xtknownId était utilisée. (NEO-30832)
* Ajout de la prise en charge des opérations de mise à jour par lots à l’aide de l’activité Connecteur CRM .

**Correctifs**

* Correction d’un problème lors de la création d’une diffusion qui entraînait une erreur dans la variable **Images** de l’onglet **Tracking &amp; images** fenêtre. Cela se produisait lors de l’utilisation d’une configuration de proxy automatique. (NEO-33260)
* Correction d&#39;une erreur qui pouvait vous empêcher de télécharger un fichier sur un serveur Debian 10 (HTTPS) en mode synchrone.
* Correction d&#39;une erreur qui pouvait empêcher les enregistrements de la table des statistiques de diffusions (`nmsDeliveryLogStats`) d&#39;être purgée de l&#39;instance de mid-sourcing lors du nettoyage de la base après la suppression des diffusions associées. (NEO-31034)
* Correction d’un problème qui empêchait l’envoi de notifications d’application mobile sur iOS lors de l’utilisation de l’authentification par jeton (NEO-38640).
* Correction d’un problème qui entraînait l’affichage de messages d’erreur de script lors de la création et de la configuration de rapports (NEO-38393).
* Correction d&#39;une erreur qui entraînait l&#39;échec du workflow de tracking sur l&#39;Oracle en raison de la mise à jour simultanée de volumes élevés d&#39;indicateurs de diffusion (NEO-39653).
* Correction d&#39;une erreur qui empêchait l&#39;envoi d&#39;une diffusion en raison d&#39;une erreur lors de l&#39;exécution d&#39;une typologie de contrôle (NEO-39833).
* Correction d&#39;une erreur dans les landing pages qui empêchait l&#39;affichage correct des caractères spéciaux dans les pages de HTML des réponses aux questionnaires en ligne (NEO-39438).
* Correction d’un problème qui empêchait le fonctionnement de la console du Campaign Classic lors d’un clic droit sur l’un des dossiers de l’onglet Explorateur (NEO-38884).
* Correction d&#39;une erreur lors de l&#39;utilisation d&#39;un modèle de diffusion précédemment créé lié à un compte Web Analytics dans une nouvelle diffusion où la configuration Web Analytics était manquante. (NEO-28666)
* Correction dʼun problème en raison duquel les diffusions mobiles jointes à un workflow ne pouvaient pas être prévisualisées.
* Correction d&#39;une erreur qui empêchait la redirection des URL de tracking personnalisées lorsque le mécanisme de signature des URL pour les liens de tracking était activé.
* Correction d’un problème qui entraînait des échecs de postupgrade en raison d’un problème de gestion des index.
* Correction d’une erreur qui se produisait lors de l’utilisation des types de données de champ de recherche avec Microsoft Dynamics CRM dans **Importer** ou **Exporter** activités de workflow.
* Correction d’un problème qui empêchait la connexion à la console en raison d’un problème de configuration du proxy. (NEO-38388)
* Correction dʼun problème de régression qui empêchait la fonctionnalité **Purger le dossier** de fonctionner correctement. (NEO-37459)
* Correction d’un problème qui entraînait une erreur de requête erronée lors de l’utilisation de champs de données XML avec le compte CRM Microsoft Dynamics si le xml référencé contenait des guillemets doubles.
* Correction dʼun problème en raison duquel les problèmes de délai dʼexpiration du réseau étaient incorrectement enregistrés en tant que problèmes dʼinterruption de script au lieu dʼerreurs de réseau. Ce problème se produisait dans le cas de requêtes HTTP incluses dans les activités JavaScript. (NEO-38079)
* Correction dʼun problème en raison duquel des résultats incorrects étaient renvoyés lors de lʼexécution des fonctions Amazon Redshift HoursDiff et MinutesDiff lors de la tentative dʼextraction du composant dʼheure.(NEO-31673)
* Correction d’un problème qui empêchait la variable **Hot Clics** rapport à partir du chargement pour les diffusions depuis le build 9182. (NEO-28900)
* Correction d’une erreur qui remplaçait le symbole &amp; dans une URL par la référence d’entité de caractère (`&amp;`) empêchant les utilisateurs d’accéder à l’URL associée à un code QR. (NEO-28621)
* Correction d’un problème qui créait un nouveau compte externe chaque fois qu’un utilisateur créait un nouveau workflow de campagne et une activité de diffusion associée à un compte Web Analytics. Cela était dû à un ID manquant dans l’objet de diffusion webAnalyticsAccount . (NEO-39691)
* Correction dʼun problème en raison duquel lʼactivité du workflow de **Lecture de liste** ne fonctionnait pas lorsque la liste était identifiée dans la base de données par un identifiant négatif. (NEO-39607)
* Correction d’un problème en raison duquel pouvait entraîner la variable **Mid-sourcing (logs de diffusion)** échec du workflow. (NEO-39662)
* Correction d’un problème qui empêchait la prévisualisation des diffusions email jointes à un workflow. (NEO-37840)
* Correction d’un problème en raison duquel des tables valides contenant des valeurs de liste étaient supprimées par le workflow de nettoyage de la base de données. (NEO-34911)
* Correction dʼun problème qui entraînait le blocage du workflow de facturation sur les instances marketing.
