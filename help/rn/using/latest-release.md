---
product: campaign
title: Dernière version
description: Notes de mise à jour de la dernière version de Campaign Classic v7
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Overview
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 88ee8d1575f6397a35fb6f7412cd08119a75c131
workflow-type: ht
source-wordcount: '962'
ht-degree: 100%

---

# Dernière version{#latest-release}



Cette page répertorie les nouvelles fonctionnalités, les améliorations et les correctifs apportés à la **dernière version de Campaign Classic v7**. Chaque nouvelle build est fournie avec un statut matérialisé par une couleur. En savoir plus sur les statuts de build de Campaign Classic v7 dans [cette page](rn-overview.md).

## ![](assets/do-not-localize/green_2.png) Version 7.3.3 - Build 9359 {#release-7-3-3}

>[!CAUTION]
>
>La mise à niveau de la console cliente est obligatoire. Découvrez comment mettre à niveau votre console cliente sur cette [page](../../installation/using/installing-the-client-console.md).

_20 mars 2023_

**Amélioration de la sécurité**

* Afin d’améliorer la sécurité, Tomcat a été mis à jour de la version 8.5.81 vers la version 8.5.85. (NEO-56936)

**Améliorations**

* Le workflow de facturation a été amélioré pour optimiser les performances. (NEO-47658)
* Le workflow de tracking a été amélioré afin d’optimiser les performances en cas de diffusion de taille importante. (NEO-45064)
* La gestion du tracking a été améliorée afin de résoudre les problèmes éventuels liés aux paramètres dynamiques dans les URL. La version 3 de la gestion du tracking gère désormais les URL de type ajax (avec des paramètres après un symbole « # ») et empêche les outils tiers de modifier les URL de tracking. Pour appliquer cette modification, vous devez contacter Adobe. (NEO-46535)

<!--To apply this change, the marketing, tracking and mid servers need to be updated to 7.3.3. To enable the new tracking management mode, set the `emailLinksVersion` parameter to '3' in the configuration file of the marketing server. (NEO-46535)-->

**Correctifs**

* Correction d’un problème qui empêchait l’envoi de notifications push de BAT iOS depuis l’instance de pilotage (contexte des messages transactionnels). (NEO-54713)
* Correction d’un problème qui empêchait le défilement dans l’onglet **Modifier** de Digital Content Editor (DCE). (NEO-54474)
* Correction d’un problème en raison duquel deux activités d’enrichissement utilisaient le même identifiant de nom dans leur liaison, ce qui entraînait l’utilisation des liens de la première activité d’enrichissement par la seconde. (NEO-48851)

## ![](assets/do-not-localize/orange_2.png) Version 7.3.2 - Build 9356 {#release-7-3-2}

_21 novembre 2022_

>[!CAUTION]
>
>La mise à niveau de la console cliente est obligatoire. Découvrez comment mettre à niveau votre console cliente sur cette [page](../../installation/using/installing-the-client-console.md).

**Mises à jour de compatibilité**

* Adobe Campaign est désormais compatible avec PostgreSQL 14. Pour plus d’informations, consultez cette [note technique](../../technotes/using/tech-stack-upgrade.md).

* Compte tenu de la fin de vie de Microsoft Internet Explorer 11, le moteur de rendu HTML des tableaux de bord dans la console cliente utilise désormais Edge Chromium. (NEO-20741)

En savoir plus sur la [matrice de compatibilité de Campaign](../../rn/using/compatibility-matrix.md#RDBMSservers).

**Améliorations**

* Le connecteur Google BigQuery prend désormais entièrement en charge les champs booléens. (NEO-49181)
* Vous pouvez désormais configurer la durée de validité des cookies IMS dans la section `Configuration for the redirection service` du fichier serverConf.xml. Les cookies suivants sont concernés : `uuid230`, `nllastdelid` et `AMCV_` (NEO-42541).
* L’adresse IP peut désormais être masquée dans la requête « /r/test » en définissant `showSourceIP` sur « false » dans le nœud de redirection du fichier serverConf.xml. [En savoir plus](../../installation/using/the-server-configuration-file.md#redirection-redirection) (NEO-46656).

**Fonctionnalités obsolètes**

* Le marketing social avec Facebook est désormais obsolète. Vous pouvez utiliser l’intégration de Twitter pour publier sur les médias sociaux ou utiliser Adobe pour créer un canal personnalisé.
* Le connecteur ACS (offre Prime) est désormais obsolète. Vous pouvez utiliser les fonctionnalités d’exportation/importation de Campaign pour extraire et injecter des données dans les deux produits.

En savoir plus dans la page [Fonctionnalités obsolètes et supprimées](deprecated-features.md).

**Autres modifications**

* Amélioration des journaux web : les avertissements `logonEscalation` s’affichent désormais uniquement pour les utilisateurs et utilisatrices disposant de privilèges d’administration. (NEO-47167)
* Pour éviter les erreurs, le workflow **Collecter les données pour le service Carte thermique** (collectDataHeatMapService) est désormais arrêté par défaut. (NEO-33959)
* Plusieurs améliorations ont été apportées afin d’optimiser l’utilisation du processeur pour le tableau de bord des campagnes. (NEO-46417)
* Pour éviter les blocages, la méthode JS loadLibraryDebug a été supprimée. (NEO-46968)
* Les autres références à la bibliothèque log4j ont été supprimées dans l’installation de Campaign sous Windows. (NEO-44851)

**Correctifs**

* Correction d’un problème qui empêchait l’utilisation de l’option de workflow **Fusionner les lignes sélectionnées**. (NEO-48488)
* Correction d’un problème qui empêchait la mise à jour correcte de l’indicateur de diffusion **Succès** lors de l’utilisation du MTA amélioré d’Adobe Campaign. (NEO-50462)
* Correction d’un problème lors de la réinitialisation de la validation du contenu dans une diffusion par e-mail, qui empêchait la revalidation de celui-ci. (NEO-44259)
* Correction d’un problème en raison duquel le bouton **Validation de la diffusion** n’était pas affiché. (NEO-47547)
* Correction d’un problème de performances dans l’onglet HTML d’une diffusion, qui pouvait se produire lors de l’utilisation d’un code HTML volumineux. (NEO-47440)
* Correction d’un problème qui affectait les mises à jour du statut des logs de diffusion sur l’instance MID, lorsque l’option `FeatureFlag_GZIP_Compression` était activée. (NEO-49183)
* Correction d’un problème qui empêchait l’envoi de notifications d’applications mobiles iOS à partir d’une instance d’exécution lors de l’utilisation de l’authentification par jeton. (NEO-45961)
* Correction d’un problème entraînant le blocage du workflow **Actualisation pour la délivrabilité** (deliverabilityUpdate) lorsque les broadlogs étaient trop nombreux pour être synchronisés. (NEO-48287)
* Correction d’un problème de type d’événement qui entraînait le blocage du workflow **Synchronisation de Message Center** (mcSynch).
* Correction d’un problème qui pouvait entraîner une erreur lors de l’ajout de l’indicateur **Destinataires ayant ouvert** (estimatedRecipientOpen) dans les données additionnelles d’une activité de workflow **Requête**. (NEO-46665)
* Correction d’un problème lié au workflow **Facturation** qui échouait lorsque les packages de contrôle et d’exécution de Message Center étaient installés sur la même instance. (NEO-47674)
* Correction d’un problème lié au workflow **Facturation** qui échouait lorsqu’il existait des tables avec la clé primaire définie sous la forme d’une chaîne au lieu d’un nombre entier. (NEO-46254)
* Correction d’un problème avec les filtres des cartes thermiques lorsque le nom du workflow était trop long. (NEO-46301)
* Correction d’un problème apparu dans la version 7.3.1 sur le connecteur Snowflake FDA en raison duquel les enregistrements étaient supprimés lors de l’utilisation de « Jointure simple de cardinalité 0 ou 1 » pendant l’enrichissement. (NEO-48737)
* Correction d’un problème avec le connecteur Snowflake FFDA lors de l’utilisation du paramètre de tri dans une activité de workflow **Partage**. (NEO-45899)
* Correction d’un problème au cours duquel l’enregistrement de la configuration du compte externe était impossible. Le compte externe est désormais automatiquement enregistré une fois le test de connexion effectué, pour les connecteurs dotés de fonctionnalités d’analyse (Snowflake et Google BigQuery). (NEO-47636)
* Correction d’un problème qui empêchait l’insertion d’un type de données « Time » dans une activité de workflow **Mise à jour des données** sur MSSQL. (NEO-47763)
* Correction d’un problème qui entraînait le blocage du processus MTA lorsque le fuseau horaire du moteur n’était pas défini (spécifique à MSSQL). (NEO-46619)
* Correction d’un problème lié à l’importation de fichiers HTML lorsque les nœuds d’image (img) contenaient des URL avec des champs de personnalisation. (NEO-48396)
* Correction d’une erreur HTTP 500 lors de la tentative de connexion à une instance dans laquelle le nœud `limit` n’était pas configuré dans le fichier serverConf.xml.
* Correction d’un problème qui entraînait une erreur « Discordance des jeux de caractères » lors de l’utilisation de certaines fonctions, telles que `to_nclob`, avec une base de données Oracle Unicode où NChar n’était pas activé. (NEO-49361)
* Correction d’un problème qui entraînait une erreur lorsqu’un utilisateur ou une utilisatrice disposant de droits d’accès en lecture sur le dossier nmsDeliveryMapping essayait de lancer une campagne ou un workflow. (NEO-48230)
* Correction d’un problème qui empêchait le bon fonctionnement de la fonction `JSPContext.sqlExecWithOneParam`. (NEO-50066)
* Correction de diverses erreurs de redirection. (NEO-50030)
