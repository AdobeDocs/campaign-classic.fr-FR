---
product: campaign
title: Dernière version
description: Notes de mise à jour de la dernière version de Campaign Classic v7
feature: Overview
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 02ab5f4520179fcce8eedbe3dcc7b08cb9cfe0d2
workflow-type: tm+mt
source-wordcount: '2991'
ht-degree: 93%

---

# Dernière version{#latest-release}

![](../../assets/v7-only.svg)

Cette page répertorie les nouvelles fonctionnalités, les améliorations et les correctifs apportés à la **dernière version de Campaign Classic v7**. Chaque nouvelle build est fournie avec un statut matérialisé par une couleur. En savoir plus sur les statuts de build de Campaign Classic v7 dans [cette page](rn-overview.md).

## ![](assets/do-not-localize/green_2.png) Version 7.3.3 - Build 9359 {#release-7-3-3}

>[!CAUTION]
>
> Cette version n’est disponible que pour les utilisateurs de Cloud Services gérés pour l’instant. Elle sera bientôt disponible pour les déploiements on-premise et hybrides.
>
>La mise à niveau de la console cliente est obligatoire. Découvrez comment mettre à niveau votre console cliente sur cette [page](../../installation/using/installing-the-client-console.md).

>[!NOTE]
>
>Cette version est GA pour les utilisateurs de Cloud Services gérés uniquement.

_9 mars 2023_

**Amélioration de la sécurité**

* Pour optimiser la sécurité, Tomcat a été mis à jour de la version 8.5.81 à la version 8.5.85. (NEO-56936)

**Améliorations**

* Le workflow Facturation a été amélioré pour optimiser les performances. (NEO-47658)
* Le workflow de tracking a été amélioré afin d&#39;optimiser les performances en cas de diffusion de taille importante. (NEO-45064)
* La gestion du suivi a été améliorée afin de résoudre les problèmes éventuels liés aux paramètres dynamiques dans les URL. La version 3 de la gestion du suivi gère désormais les URL de type ajax (avec des paramètres après un &quot;#&quot;) et empêche les outils tiers de modifier les URL de suivi. Pour appliquer cette modification, vous devez contacter Adobe. (NEO-46535)

<!--To apply this change, the marketing, tracking and mid servers need to be updated to 7.3.3. To enable the new tracking management mode, set the `emailLinksVersion` parameter to '3' in the configuration file of the marketing server. (NEO-46535)-->

**Correctifs**

* Correction d’un problème qui empêchait l’envoi de notifications push de BAT iOS depuis l’instance de pilotage (contexte des messages transactionnels). (NEO-54713)
* Correction d’un problème qui empêchait le défilement dans la variable **Modifier** de Digital Content Editor (DCE). (NEO-54474)
* Correction d’un problème en raison duquel deux activités d’enrichissement utilisaient le même identifiant dans leur liaison, ce qui entraînait l’utilisation des liens de la première activité d’enrichissement par la seconde. (NEO-48851)

## ![](assets/do-not-localize/green.png) Version 7.3.2 - Build 9356 {#release-7-3-2}

_21 novembre 2022_

>[!CAUTION]
>
>La mise à niveau de la console cliente est obligatoire. Découvrez comment mettre à niveau votre console cliente sur cette [page](../../installation/using/installing-the-client-console.md).

>[!NOTE]
>
>Cette version est GA pour les déploiements on-premise et hybrides uniquement.

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

## ![](assets/do-not-localize/orange_2.png) Version 7.3.1 - Build 9352 {#release-7-3-1}

_1er juillet 2022_

**Nouveautés**

<table> 
<thead>
<tr> 
<th> <strong>Notifications sensibles à l’heure</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>Avec iOS 15, Apple a ajouté une notion de notification urgente qui permet à la personne qui développe l’application de contourner le mode Focus lorsqu’une notification est considérée comme urgente et doit atteindre l’utilisateur ou l’utilisatrice en temps réel.</p>
<p>Découvrez comment créer une notification urgente dans la <a href="../../delivery/using/create-notifications-ios.md">documentation détaillée</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

**Mises à jour de compatibilité**

* Le SDK Adobe Campaign prend maintenant en charge Android 12 et iOS 15 pour les notifications push.
* Adobe Campaign est désormais compatible avec MySQL 8.
* Adobe Campaign est désormais compatible avec Windows 11.
* Adobe Campaign est désormais compatible avec Debian 11. Pour plus d’informations, consultez cette [note technique](../../technotes/using/tech-stack-upgrade.md).

Reportez-vous à la [matrice de compatibilité de Campaign](../../rn/using/compatibility-matrix.md#OperatingSystems).

**Améliorations**

* Compte tenu de la fin de vie d’Internet Explorer 11, le moteur de rendu HTML pour Adobe Services (page de connexion) dans la console cliente utilise désormais Edge Chromium. Notez que Microsoft Internet Explorer 11 est toujours le moteur de rendu de HTML pour les tableaux de bord dans la console cliente.  En outre, l’installation du runtime de Microsoft Edge Webview 2 est désormais requise pour toute installation de la console cliente (à partir de la version de build 7.3 de Campaign Classic). [En savoir plus](../../installation/using/installing-the-client-console.md)
* La gestion des connexions de base de données dans Adobe Campaign a été améliorée afin d’optimiser la stabilité.
* L’authentification OAuth 2.0 de Microsoft Exchange Online pour POP3 est désormais prise en charge dans Campaign. [En savoir plus](../../installation/using/external-accounts.md#bounce-mails-external-account)
* Correction de divers problèmes lors de l’utilisation d’une activité de workflow d’enrichissement avec des données externes. (NEO-38069)
* Le connecteur FDA SAP Hana a été mis à jour pour fonctionner avec la dernière version de la base de données SAP Hana (2.x).
* Le connecteur FDA Teradata a été mis à jour pour fonctionner avec la dernière version de Teradata (17).
* Dans la version 20.2, la prise en charge de l’authentification basée sur les jetons pour les diffusions iOS a été introduite pour les nouvelles diffusions et les modèles de diffusion. Dans la version 7.2, un correctif a été ajouté au postupgrade pour appliquer la prise en charge de l’authentification basée sur les jetons à un maximum de 10 000 diffusions et modèles de diffusion créés précédemment. Dans la version 7.3, le correctif a été amélioré et la limite a été supprimée.

**Correctifs**

* Correction d’une erreur de la build précédente qui empêchait le redimensionnement de la page de connexion IMS. (NEO-30085)
* Correction d’une erreur qui se produisait lors de l’installation du package du gestionnaire de contenu sur une instance existante. (NEO-32349)
* Correction d’un problème dans le menu **Campagnes** où un message « opération en cours » s’affichait en continu. (NEO-44904)
* Avec Adobe Analytics activé, correction d’un problème en raison duquel le BID (Broadlog ID, identifiant du broadlog) et le CID (identifiant de campagne) étaient supprimés de l’URL lors de l’envoi d’un e-mail avec une URL sans enregistrer la diffusion. (NEO-38678)
* Correction d’un problème lors du téléchargement d’une image dans le dossier Ressources publiques d’une instance avec une configuration spécifique à Message Center. Le message d’erreur suivant s’affiche : « Impossible de télécharger les images sur les serveurs de tracking ». (NEO-38546, NEO-45572)
* Correction d’un problème en raison duquel le système se bloquait lors de la régénération de la configuration en cas de fichiers de configuration erronés. (NEO-38752)
* Correction d’un problème qui empêchait la mise à jour correcte des indicateurs de diffusion. (NEO-44827)
* Correction d’un problème qui entraînait une erreur de postupgrade lors de l’utilisation de requêtes complexes. (NEO-43648)
* Correction d’un problème qui empêchait le fonctionnement de l’aperçu webApps. (NEO-43242)
* Correction d’un problème qui entraînait l’échec de la préparation de la diffusion lors de l’utilisation d’un fichier de mapping de ciblage externe dans un workflow avec une activité Chargement de données (fichier). (NEO-43691)
* Correction d’un problème qui entraînait des blocages et nécessitait un redémarrage complet de l’instance. (NEO-44645)
* Correction d’un problème qui empêchait le chargement de la carte thermique des workflows de charger n’importe quel résultat. (NEO-43360)
* Correction d’un problème qui entraînait des difficultés de connexion lors de l’utilisation du connecteur externe FDA. (NEO-42722)
* Correction d’un problème lié aux bons à tirer lors de l’utilisation de la substitution d’adresse et de l’exclusion d’une population témoin. (NEO-39695)
* Correction d’un problème qui entraînait des échecs de workflow en raison d’un problème de connecteur Snowflake. (NEO-46299)
* Correction d’un problème qui bloquait la console cliente en raison d’un caractère non valide dans un bloc de personnalisation. (NEO-45761)
* Correction d’un problème qui entraînait des difficultés de connexion lors de la création d’un compte externe pour Snowflake en tant que base de données externe. (NEO-45744)
* Correction d’un problème qui entraînait l’affichage d’informations de tableau protégées par un attribut visibleIf. (NEO-37865)
* Correction d’un problème qui pouvait afficher le message d’erreur « $ non défini » lors de la phase d’analyse de la diffusion. (NEO-32940)
* Correction d’un problème en raison duquel les diffusions étaient associées à un eventType incorrect. (NEO-45743)
* Correction d’un problème qui entraînait des blocages en raison de vidages principaux intermittents. (NEO-30549)
* Correction d’un problème qui entraînait des blocages lors de l’utilisation d’un code HTML erroné dans une diffusion. (NEO-40385)
* Correction d’un problème qui empêchait les personnes ne disposant pas de privilèges d’administration d’accéder à l’onglet **Analyse** dans les propriétés de la diffusion. (NEO-34025)
* Correction d’un problème qui empêchait le téléchargement d’une image en mode bloc à partir d’un serveur externe pendant la préparation des messages. (NEO-40307)
* Correction d’une erreur qui entraînait l’envoi de la diffusion à un plus grand nombre de destinataires que prévu. (NEO-45108)

## ![](assets/do-not-localize/green_2.png) Version 7.2.2 - Build 9349 {#release-7-2-2}

_1er mars 2022_

>[!NOTE]
>
> Cette build est compatible avec la console cliente v7.2.1.

**Correctifs**

* Correction dʼun problème lors de la configuration du compte externe **Web Analytics** en raison duquel le statut de lʼintégration affichait toujours « Intégration réussie », même lorsque des erreurs se produisaient. (NEO-36672)
* Correction de plusieurs erreurs de postupgrade liées au mécanisme d’identification des séquences lorsque les identifiants sont négatifs. (NEO-43205, NEO-42846, NEO-42845)
* Correction d’un problème lors de l’utilisation du compte externe **Web Analytics** avec des diffusions récurrentes et continues, qui entraînait une perte partielle des données du compte externe. (NEO-38548)
* Correction dʼune erreur qui ralentissait le postupgrade lors de la mise à jour du tableau NmsActiveContact. (NEO-43206)
* Correction d’un problème qui entraînait lʼéchec du postupgrade lorsque des dossiers prêts à lʼemploi étaient déplacés du nœud **Administration** vers tout autre emplacement. (NEO-42875)
* Correction dʼun problème lors de lʼutilisation dʼune activité de workflow **Mise à jour des données** qui pouvait empêcher la mise à jour du schéma du destinataire avec les données de ce dernier provenant dʼune base de données externe Google Cloud. (NEO-42343)
* Correction d’un problème lié au connecteur Adobe Analytics lors du postupgrade. (NEO-43318, NEO-38136)
* Correction d’un problème de remplacement du CUID par « VALUE_TO_CHANGE » lors du postupgrade. (NEO-43267)
* Correction dʼun problème qui entraînait des erreurs lors de la synchronisation des instances de midsourcing et marketing sur une configuration multi-mid. (NEO-10432)
* Correction d’un problème lors de l’actualisation du workflow de délivrabilité qui entraînait une erreur lorsque plus de 1 000 broadlogs étaient présents en même temps. (NEO-40276)
* Correction d’un problème qui empêchait la mise à jour automatique des indicateurs de diffusion Taux d’ouverture et Taux de clics. (NEO-43253)

## ![](assets/do-not-localize/limited_2.png) Version 7.2.1 - Build 9346 {#release-7-2-1}

_10 janvier 2022_

**Amélioration de la sécurité**

Plusieurs améliorations de sécurité ont été apportées aux comptes FDA :

* Lors de la configuration de votre compte externe FDA, vous pouvez désormais vous connecter à votre compte Snowflake à l’aide de l’authentification par paire de clés pour une sécurité d’authentification renforcée. [En savoir plus](../../installation/using/configure-fda-snowflake.md)
* Lors de la configuration de votre compte externe FDA, vous pouvez désormais vous connecter à votre compte Azure Synapse Analytics à l’aide de l’identité gérée affectée par le système. [En savoir plus](../../installation/using/configure-fda-synapse.md#azure-external)
* Toutes les références à la bibliothèque log4j ont été supprimées de Campaign pour assurer une sécurité optimale.

**Mises à jour de compatibilité**

Adobe Campaign est désormais compatible avec Windows Server 2019. Reportez-vous à la [matrice de compatibilité de Campaign](../../rn/using/compatibility-matrix.md#OperatingSystems).

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

* Suite à leur abandon, les activités d’action Microsoft CRM, Salesforce et Oracle CRM On Demand ont été supprimées de l’interface. Pour configurer la synchronisation des données entre Adobe Campaign et un système CRM, vous pouvez utiliser l’activité Connecteur CRM. [En savoir plus](../../workflow/using/crm-connector.md)
* Le champ **[!UICONTROL Identifiant chiffré]** a été ajouté au schéma des visiteurs (nms:visitor). Ce champ est calculé et doit être utilisé pour les applications web. Cela s’applique lorsque le canal LINE est configuré sur l’instance de midsourcing.
* Les sources de données CRM peuvent désormais être utilisées avec l’activité **Modifier la source de données**.
* Une nouvelle option a été ajoutée dans les propriétés de **Gestion des erreurs** des activités de workflow : l’option **Abandon en cas d’erreur** arrête automatiquement le workflow. Vous ne pouvez pas le redémarrer par la suite (NEO-29661). [En savoir plus](../../workflow/using/advanced-parameters.md#in-case-of-errors)
* Une séquence dédiée est désormais utilisée pour générer les clés primaires de la table nmsGroup, qui sert à créer des groupes statistiques de destinataires. Auparavant, la séquence XtkNewId était utilisée. (NEO-30832)
* Ajout de la prise en charge des opérations de mise à jour par lots à l’aide de l’activité du connecteur CRM.
* Amélioration des performances pour le temps de traitement des messages transactionnels. (NEO-40370)

**Correctifs**

* Correction d’un problème lors de la création d’une diffusion qui entraînait une erreur dans l’onglet **Images** de la fenêtre **Tracking &amp; Images**. Ce problème se produisait lors de l’utilisation d’une configuration de proxy automatique. (NEO-33260)
* Correction d’un problème qui empêchait le téléchargement d’un fichier sur un serveur Debian 10 (HTTPS) en mode synchrone.
* Correction d’une erreur qui empêchait les enregistrements de la table des statistiques de diffusions (`nmsDeliveryLogStats`) d’être purgés de l’instance de midsourcing pendant le nettoyage de la base de données après la suppression des diffusions associées. (NEO-31034)
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
* Correction d’une erreur qui remplaçait le symbole « &amp; » dans une URL par la référence d’entité de caractère (`&amp;`) empêchant l’accès à l’URL associée à un code QR. (NEO-28621)
* Correction d’un problème en raison duquel un compte externe était créé lors de chaque création d’un workflow de campagne et d’une activité de diffusion associée à un compte Web Analytics. Ce problème était dû à un ID manquant dans l’objet de diffusion webAnalyticsAccount. (NEO-39691)
* Correction dʼun problème en raison duquel lʼactivité du workflow de **Lecture de liste** ne fonctionnait pas lorsque la liste était identifiée dans la base de données par un identifiant négatif. (NEO-39607)
* Correction d’un problème qui entraînait l’échec du workflow **Midsourcing (logs de diffusion)**. (NEO-39662)
* Correction d’un problème qui vous empêchait de prévisualiser les diffusions e-mail jointes à un workflow. (NEO-37840)
* Correction d’un problème qui entraînait la suppression de tables valides contenant des valeurs de liste par le workflow de nettoyage de la base de données. (NEO-34911)
* Correction dʼun problème qui entraînait le blocage du workflow de facturation sur les instances marketing.
