---
product: campaign
title: Dernière version
description: Notes de mise à jour de la dernière version de Campaign Classic v7
feature: Overview
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: fc49c0ec80c8741b01ea150c3bc7362b73357607
workflow-type: tm+mt
source-wordcount: '1037'
ht-degree: 100%

---

# Dernière version{#latest-release}

![](../../assets/v7-only.svg)

Cette page répertorie les nouvelles fonctionnalités, les améliorations et les correctifs apportés à la **dernière version de Campaign Classic v7**. Chaque nouvelle build est fournie avec un statut matérialisé par une couleur. En savoir plus sur les statuts de build de Campaign Classic v7 dans [cette page](rn-overview.md).

## ![](assets/do-not-localize/green_2.png) Version 7.2.1 - Build 9346 {#release-7-2-1}

_10 janvier 2022_

**Amélioration de la sécurité**

Plusieurs améliorations de sécurité ont été apportées aux comptes FDA :

* Lors de la configuration de votre compte externe FDA, vous pouvez désormais vous connecter à votre compte Snowflake à l’aide de l’authentification par paire de clés pour une sécurité d’authentification renforcée. [En savoir plus](../../installation/using/configure-fda-snowflake.md)
* Lors de la configuration de votre compte externe FDA, vous pouvez désormais vous connecter à votre compte Azure Synapse Analytics à l’aide de l’identité managée affectée par le système. [En savoir plus](../../installation/using/configure-fda-synapse.md#azure-external)
* Toutes les références à la bibliothèque log4j ont été supprimées de Campaign pour assurer une sécurité optimale.

**Améliorations**

* Connecteur Microsoft Dynamics CRM 365

   Des correctifs importants ont été appliqués concernant l’API web du connecteur Microsoft Dynamics :

   * Correction d’un problème, lors d’une importation déclenchée par un workflow, en raison duquel les valeurs nulles des champs de type chaîne étaient enregistrées comme nulles au lieu de valeurs vides.
   * Correction d’un problème qui entraînait l’erreur suivante pour l’importation ou l’exportation de données à l’aide d’appels API web : « URI non valide : le schéma d’URI est trop long ».
   * Correction de divers problèmes lors de l’importation de données contenant des champs de recherche depuis Microsoft Dynamics 365.

* Connecteur FDA Google BigQuery

   * Le connecteur FDA Google BigQuery est désormais disponible pour les déploiements hébergés. [En savoir plus](../../installation/using/configure-fda-google-big-query.md)
   * Ajout de la prise en charge de l’établissement de connexions à un serveur proxy pour le connecteur FDA Google BigQuery. Les options de proxy requises peuvent être définies dans le champ Options de la configuration du compte externe. [En savoir plus](../../installation/using/configure-fda-google-big-query.md#google-external)

**Autres changements**

* Suite à leur abandon, les activités d’action Microsoft CRM, Salesforce et Oracle CRM On Demand ont été supprimées de l’interface. Pour paramétrer la synchronisation des données entre Adobe Campaign et un système CRM, vous pouvez utiliser l’activité Connecteur CRM. [En savoir plus](../../workflow/using/crm-connector.md)
* Le champ **[!UICONTROL Identifiant chiffré]** a été ajouté au schéma des visiteurs (nms:visitor). Ce champ est calculé et doit être utilisé pour les applications web. Cela s’applique lorsque le canal LINE est paramétré sur l’instance de mid-sourcing.
* Les sources de données CRM peuvent désormais être utilisées avec l’activité **Modifier la source de données**.
* Une nouvelle option a été ajoutée dans les propriétés de **Gestion des erreurs** des activités de workflow : l’option **Abandon en cas d’erreur** arrête automatiquement le workflow. Vous ne pouvez pas le redémarrer par la suite (NEO-29661). [En savoir plus](../../workflow/using/advanced-parameters.md#in-case-of-errors)
* Une séquence dédiée est désormais utilisée pour générer les clés primaires de la table nmsGroup, qui sert à créer des groupes statistiques de destinataires. Auparavant, la séquence XtkNewId était utilisée. (NEO-30832)
* Ajout de la prise en charge des opérations de mise à jour par lots à l’aide de l’activité du connecteur CRM.
* Amélioration des performances pour le temps de traitement des messages transactionnels. (NEO-40370)

**Correctifs**

* Correction d’un problème lors de la création d’une diffusion qui entraînait une erreur dans l’onglet **Images** de la fenêtre **Tracking &amp; Images**. Ce problème se produisait lors de l’utilisation d’une configuration de proxy automatique. (NEO-33260)
* Correction d’un problème qui empêchait le téléchargement d’un fichier sur un serveur Debian 10 (HTTPS) en mode synchrone.
* Correction d’une erreur qui empêchait les enregistrements de la table des statistiques de diffusions (`nmsDeliveryLogStats`) d’être purgés de l’instance de mid-sourcing pendant le nettoyage de la base de données après la suppression des diffusions associées. (NEO-31034)
* Correction d’un problème qui empêchait l’envoi de notifications d’application mobile sur iOS lors de l’utilisation de l’authentification basée sur les jetons (NEO-38640).
* Correction d’un problème qui entraînait l’affichage de messages d’erreur de script lors de la création et de la configuration de rapports (NEO-38393).
* Correction d’un problème qui entraînait l’échec du workflow de tracking sur Oracle en raison de la mise à jour simultanée de volumes élevés d’indicateurs de diffusion (NEO-39653).
* Correction d’un problème qui empêchait l’envoi d’une diffusion en raison d’une erreur survenant lors de l’exécution d’une typologie de contrôle (NEO-39833).
* Correction d’un problème au niveau des landing pages qui empêchait les caractères spéciaux de s’afficher correctement dans les pages HTML des réponses aux questionnaires en ligne (NEO-39438).
* Correction d’un problème qui empêchait le fonctionnement de la console Campaign Classic lors d’un clic droit sur l’un des dossiers de l’onglet Explorateur (NEO-38884).
* Correction d’une erreur lors de l’utilisation d’un modèle de diffusion précédemment créé lié à un compte Web Analytics dans une nouvelle diffusion où la configuration Web Analytics était manquante. (NEO-28666)
* Correction d’un problème qui vous empêchait de prévisualiser les diffusions mobiles jointes à un workflow.
* Correction d’une erreur qui empêchait la redirection des URL de tracking personnalisées lorsque le mécanisme de signature des URL pour les liens de tracking était activé.
* Correction d’un problème qui entraînait des échecs de postupgrade en raison d’un problème de gestion des index.
* Correction d’une erreur qui se produisait lors de l’utilisation des types de données de champ de recherche avec Microsoft Dynamics CRM dans les activités de workflow d’**importation** ou d’**exportation**.
* Correction d’un problème qui empêchait de se connecter à la console en raison d’un problème de configuration du proxy. (NEO-38388)
* Correction dʼun problème de régression qui empêchait la fonctionnalité **Purger le dossier** de fonctionner correctement. (NEO-37459)
* Correction d’un problème qui entraînait une erreur de requête incorrecte lors de l’utilisation de champs de données XML avec le compte Microsoft Dynamics CRM si le XML référencé contenait des guillemets doubles.
* Correction dʼun problème en raison duquel les problèmes de délai dʼexpiration du réseau étaient incorrectement enregistrés en tant que problèmes dʼinterruption de script au lieu dʼerreurs de réseau. Ce problème se produisait dans le cas de requêtes HTTP incluses dans les activités JavaScript. (NEO-38079)
* Correction dʼun problème en raison duquel des résultats incorrects étaient renvoyés lors de lʼexécution des fonctions Amazon Redshift HoursDiff et MinutesDiff lors de la tentative dʼextraction du composant dʼheure.(NEO-31673)
* Correction d’un problème qui empêchait le chargement du rapport **Hot Clicks** pour les diffusions depuis la build 9182. (NEO-28900)
* Correction d’une erreur qui remplaçait le symbole &amp; dans une URL par la référence d’entité de caractère (`&amp;`) empêchant les utilisateurs d’accéder à l’URL associée à un code QR. (NEO-28621)
* Correction d’un problème en raison duquel un compte externe était créé chaque fois qu’un utilisateur créait un workflow de campagne et une activité de diffusion associée à un compte Web Analytics. Ce problème était dû à un ID manquant dans l’objet de diffusion webAnalyticsAccount. (NEO-39691)
* Correction dʼun problème en raison duquel lʼactivité du workflow de **Lecture de liste** ne fonctionnait pas lorsque la liste était identifiée dans la base de données par un identifiant négatif. (NEO-39607)
* Correction d’un problème qui entraînait l’échec du workflow **mid-sourcing (logs de diffusion)**. (NEO-39662)
* Correction d’un problème qui vous empêchait de prévisualiser les diffusions e-mail jointes à un workflow. (NEO-37840)
* Correction d’un problème qui entraînait la suppression de tables valides contenant des valeurs de liste par le workflow de nettoyage de la base de données. (NEO-34911)
* Correction dʼun problème qui entraînait le blocage du workflow de facturation sur les instances marketing.
