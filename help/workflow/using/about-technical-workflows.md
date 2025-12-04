---
product: campaign
title: Workflows techniques
description: En savoir plus sur les workflows techniques disponibles avec les packages Campaign Classic
feature: Workflows
hide: true
hidefromtoc: true
exl-id: 9aed2665-cd4b-419c-b9f2-ea04fc1d8f01
source-git-commit: 2186b8a30449cb023cb07305ba64d53f2c8adab1
workflow-type: tm+mt
source-wordcount: '1714'
ht-degree: 100%

---

# Workflows techniques{#about-technical-workflows}



## À propos des workflows techniques {#overview}

Les workflows présentés dans cette section sont installés avec les différents packages natifs d’Adobe Campaign. Ces packages, ainsi que les workflows techniques associés, dépendent de votre contrat de licence. Les packages natifs sont détaillés dans [cette section](../../installation/using/installing-campaign-standard-packages.md).

Par défaut, les workflows techniques sont disponibles dans un sous-dossier du nœud suivant : **[!UICONTROL Administration]** > **[!UICONTROL Exploitation]** > **[!UICONTROL Workflows techniques]**.

Notez que les workflows techniques ne peuvent être démarrés et modifiés que par les opérateurs disposant de droits d&#39;administration. Pour plus d’informations sur les autorisations, reportez-vous à cette [section](../../platform/using/access-management-groups.md#default-groups).

>[!NOTE]
>
>Les workflows techniques associés au module Message Center module sont disponibles par défaut dans le nœud **[!UICONTROL Administration]** > **[!UICONTROL Exploitation]** > **[!UICONTROL Message Center]** > **[!UICONTROL Workflows techniques]**.

Pour plus d&#39;informations sur la façon d&#39;utiliser les workflows techniques, voir la [section dédiée](monitoring-technical-workflows.md).

## Liste des workflows techniques {#list-technical-workflows}

| Workflow technique | Package | Description |
|------|--------|-----------|
| **Gestion des alias** (aliasCleansing) | Diffusion | Ce workflow réalise l’uniformisation des valeurs des énumérations. Par défaut, il se déclenche tous les jours à 3h00. |
| **Facturation** (billing) | Diffusion | Ce workflow transmet par email le rapport d&#39;activité du système à l&#39;opérateur &#39;billing&#39;. Il est déclenché le 25 de chaque mois sur l&#39;instance Marketing. |
| **Calcul des statistiques Twitter** (statsTwitter) | Réseaux sociaux (marketing social) - Campaign v7 uniquement | Ce workflow calcule les statistiques liées aux republications et aux visites sur X (anciennement Twitter). |
| **Traitements sur les opérations** (operationMgt) | Campagnes marketing (Campaign) | Ce workflow gère les traitements sur les opérations marketing (démarrage du ciblage, extraction des fichiers, etc.). Il crée également les workflows relatifs aux opérations récurrentes et périodiques. |
| **Collecter les données pour le service Carte thermique** (collectDataHeatMapService) | Installé par défaut | Ce workflow récupère les données requises par le service Carte thermique. |
| **Collecter les demandes d&#39;accès à des informations personnelles** (collectPrivacyRequests) | Règlement sur la protection des informations personnelles | Ce workflow génère les données du destinataire stockées dans Adobe Campaign et les met à disposition sur l’écran de la demande d’accès. |
| **Calcul des coûts** (budgetMgt) | Campagnes marketing (Campaign) | Ce workflow lance le calcul des lignes de dépenses et des coûts sur les budgets, les plans, programmes, opérations, diffusions et tâches. |
| **Nettoyage de la base de données** (cleanup) | Diffusion | Ce workflow est le workflow de maintenance de la base de données : il procède aux différents calculs des statistiques et traitements, et supprime les données obsolètes de la base de données selon la configuration définie dans l’assistant de déploiement. Par défaut, il se déclenche tous les jours à 4H00. Pour plus d’informations, consultez [cette page](../../production/using/database-cleanup-workflow.md#monitoring-campaign-classic). |
| **Nettoyage des utilisateurs LINE bloqués** (deleteBlockedLineUsersV2) | Canal LINE | Ce workflow assure la suppression des données des utilisateurs LINE V2 s’ils ont bloqué le compte officiel LINE pendant 180 jours. |
| **Supprimer les données des demandes d’accès à des informations personnelles** (deletePrivacyRequestsData) | Règlement sur la protection des informations personnelles | Ce workflow supprime les données du destinataire stockées dans Adobe Campaign. |
| **Indicateurs de diffusion** (deliveryIndicators) | Plateforme de Mid-sourcing | Ce workflow met à jour les indicateurs de tracking des diffusions. Par défaut, ce workflow se déclenche toutes les heures. |
| **Traitements dans les forums de discussion** (newsgroupMgt) | Ressources marketing (MRM) | Ce workflow gère l&#39;envoi des notifications dans les forums de discussion. Il se déclenche lorsqu&#39;il reçoit un signal de validation |
| **Traitements sur le marketing distribué** (centralLocalMgt) | Marketing central/local (Marketing distribué) | Ce workflow exécute les traitements relatifs à l’utilisation du module de marketing distribué. Il lance la création des opérations en local et gère les notifications relatives aux commandes et à la mise à disposition des kits de campagne. |
| **Purge des événements** (webAnalyticsPurgeWebEvents) | Connecteurs Web Analytics | Ce workflow permet de supprimer du champ de la base tous les événements selon la période paramétrée dans le champ Durée de vie. |
| **Export d’audiences vers Adobe Experience Cloud** (exportSharedAudience) | Intégration avec Adobe Experience Cloud | Ce workflow permet d’exporter des audiences en tant qu’audiences/segments partagés. Ces audiences peuvent être exploitées dans les différentes solutions d’Adobe Experience Cloud que vous utilisez. |
| **Prévisionnel** (forecasting) | Diffusion | Ce workflow effectue l’analyse des diffusions enregistrées dans le calendrier prévisionnel (création des logs prévisionnels). Par défaut, il se déclenche tous les jours à 1h00. |
| **Calcul de l&#39;agrégat full (cube propositionrcp)** (agg_nmspropositionrcp_full) | Moteur d’offres (Interaction) | Ce workflow met à jour l&#39;agrégat Complet (full) du cube Proposition d&#39;offre. Par défaut, il se déclenche tous les jours à 6H00. Cet agrégat capture les dimensions suivantes : Canal, Diffusion, Offre marketing et Date. Le cube Proposition d’offre est ensuite utilisé pour générer des rapports basés sur des offres. Vous pouvez en savoir plus sur les cubes dans [cette section](../../reporting/using/ac-cubes.md). |
| **Identification des contacts convertis** (webAnalyticsFindConverted) | Connecteurs Web Analytics | Ce workflow répertorie les visiteurs du site ayant concrétisé leur achat après une campagne de remarketing. Les données récupérées par ce workflow sont accessibles dans le rapport Efficacité du remarketing (voir cette page). |
| **Import d’audiences depuis Adobe Experience Cloud** (importSharedAudience) | Intégration avec Adobe Experience Cloud | Ce workflow permet d’importer dans Adobe Campaign des audiences/segments provenant de différentes solutions d’Adobe Experience Cloud. |
| **Traitements sur les diffusions dans les opérations** (deliveryMgt) | Campagnes marketing (Campaign) | Ce workflow déclenche les diffusions validées et lance les post-traitements du prestataire pour une diffusion externe. Il envoie également des notifications de validation et des rappels. |
| **Traitements sur les prestataires** (supplierMgt) | Campagnes marketing (Campaign) | Ce workflow démarre les traitements du prestataire (email au routeur et post-traitement) une fois que les diffusions ont été validées. |
| **Mise à jour du jeton d&#39;accès LINE V2** (updateLineV2AccessToken) | Canal LINE - Campaign v7 uniquement | Ce workflow actualise le jeton d’accès à la version LINE V2. |
| **Migration du MID vers l’identifiant utilisateur Line** (MIDToUserIDMigration) | Canal LINE | Ce workflow génère les ID des utilisateurs LINE V2 pour la migration de LINE V1 vers LINE V2. |
| **Notifications de ressource marketing** (assetMgt) | Ressources marketing (MRM) | Ce workflow gère les notifications associées à la validation et à la publication des ressources marketing. |
| **Message Center &lt;nom_compte_externe>** (mcSynch_&lt;nom_compte_externe>) | Contrôle des messages transactionnels (Message Center - Pilotage) | Ce workflow : <ul><li>récupère la liste des événements traités par la ou les opérations,</li><li>se synchronise avec la table NmsBroadLogMsg afin de récupérer les qualifications des messages de diffusion,</li><li>récupère les logs de diffusion d&#39;événements dès que la synchronisation avec la table NmsBroadLogMsg est terminée,</li><li>se synchronise avec la table NmsTrackingUrl afin de récupérer le tracking des URL de diffusion,</li><li>récupère les URL de tracking des événements dès que la synchronisation avec la table NmsTrackingUrl est terminée,</li><li>permet de récupérer toutes les adresses email mises en quarantaine toutes les trois heures après l&#39;envoi d&#39;une diffusion.</li></ul> |
| **Calcul de l&#39;agrégat intégral de MessageCenter** (agg_messageCenter_full) | Contrôle des messages transactionnels (Message Center - Pilotage) | Ce workflow met à jour l’agrégat intégral du cube Message Center. Il est déclenché tous les jours à 3h du matin par défaut. Cet agrégat capture les dimensions suivantes : Canal, Date, Statut et Type d&#39;événement. Le cube Message Center est ensuite utilisé pour générer des rapports basés sur des événements. Vous pouvez en savoir plus sur les cubes dans [cette section](../../reporting/using/ac-cubes.md) |
| **Mid-sourcing (compteurs des diffusions)** (defaultMidSourcingDlv) | Emission vers Mid-sourcing | Ce workflow collecte les informations de comptage des diffusions sur le serveur de midsourcing. Les informations de comptage comprennent les indicateurs généraux de diffusion tels que le nombre de diffusions envoyées, etc. Les informations de tracking comme les ouvertures ne sont pas incluses. Par défaut, il se déclenche toutes les dix minutes. |
| **Mid-sourcing (logs de diffusion)** (defaultMidSourcingLog) | Emission vers Mid-sourcing | Ce workflow collecte les logs des diffusions sur le serveur de mid-sourcing. Par défaut, il se déclenche toutes les heures. |
| **Gestion des opt-out NMAC** (mobileAppOptOutMgt) | Canal des applications mobiles | Ce workflow met à jour les désinscriptions aux notifications sur les appareils mobiles. Par défaut, il se déclenche toutes les 6 heures entre 1 h 00 et minuit. Pour plus d&#39;informations, voir à ce sujet [cette section](../../delivery/using/delivery-failures-quarantine.md#push-notification-quarantines). |
| **Notification d&#39;offre** (offerMgt) | Diffusion | Toutes les heures, ce workflow déploie les offres validées sur l&#39;environnement en ligne, ainsi que toutes les catégories contenues dans le catalogue d&#39;offres. |
| **Nettoyage des workflows en pause** (cleanupPausedWorkflows) | Diffusion | Ce workflow analyse les workflows en pause dont le niveau de priorité est défini sur normal et déclenche des avertissements et des notifications lorsqu&#39;ils sont en pause depuis trop longtemps. Après un mois, les workflows techniques en pause sont arrêtés de manière inconditionnelle. Par défaut, ce workflow est déclenché tous les lundis à 5h00. Pour plus d’informations, voir [Gérer les workflows en pause](monitoring-workflow-execution.md#handling-of-paused-workflows). |
| **Nettoyage des demandes d&#39;accès à des informations personnelles** (cleanupPrivacyRequests) | Règlement sur la protection des informations personnelles | Ce workflow supprime les fichiers de demande d’accès qui ont plus de 90 jours. |
| **Traitement des événements batch** (batchEventsProcessing) | Exécution des messages transactionnels (Message Center - Exécution) | Ce workflow permet de répartir les événements batch dans une file d&#39;attente avant qu&#39;ils ne soient associés à un modèle de message. |
| **Traitement des événements temps réel** (rtEventsProcessing) | Exécution des messages transactionnels (Message Center - Exécution) | Ce workflow permet de répartir les événements temps réel dans une file d&#39;attente avant qu&#39;ils ne soient associés à un modèle de message. |
| **Synchronisation des propositions** (propositionSynch) | Contrôle du moteur d’offres avec l’instance d’exécution | Ce workflow synchronise les propositions entre les instances marketing et d’exécution utilisées pour les interactions. |
| **Récupération des événements web** (webAnalyticsGetWebEvents) | Connecteurs Web Analytics | Toutes les heures, ce workflow télécharge les segments portant sur le comportement des internautes sur un site donné, les inclut dans la base de données Adobe Campaign et lance le workflow de re-marketing. |
| **Agrégats du reporting** (reportingAggregates) | Diffusion | Ce workflow met à jour les agrégats utilisés dans les rapports. Par défaut, il se déclenche tous les jours à 2H00. |
| **Envoi des indicateurs et des attributs de campagne** (webAnalyticsSendMetrics) | Connecteurs Web Analytics | Ce workflow permet d&#39;envoyer les indicateurs des campagnes par e-mail d&#39;Adobe Campaign vers Adobe Experience Cloud Suite via le connecteur Adobe® Analytics. Les indicateurs concernés sont les suivants : Envoyé (iSent), Nombre total d&#39;ouvertures (iTotalRecipientOpen), Nombre total de destinataires ayant cliqué (iTotalRecipientClick), Erreurs (iError), Opt-Out (opt-out) (iOptOut). |
| **Stock : commandes et alertes** (stockMgt) | Campagnes marketing (Campaign) | Ce workflow lance le calcul des stocks sur les lignes de commande et gère les seuils d&#39;alerte. |
| **Synchronisation des fans Facebook** (syncFacebookFans) | Réseaux sociaux (marketing social) - Campaign v7 uniquement | Ce workflow importe les fans Facebook dans Adobe Campaign tous les jours à 7H00. |
| **Synchronisation des pages Facebook** (syncFacebook) | Réseaux sociaux (marketing social) - Campaign v7 uniquement | Ce workflow synchronise les pages Facebook avec Adobe Campaign tous les jours à 7H00. |
| **Synchronisation des pages Twitter** (syncTwitter) | Réseaux sociaux (marketing social) - Campaign v7 uniquement | Ce workflow importe les personnes abonnées X dans Adobe Campaign tous les jours à 7h00. |
| **Notification des tâches** (taskMgt) | Ressources marketing (MRM) - Campaign v7 uniquement | Ce workflow permet d’envoyer les messages de notification relatifs aux tâches dans les opérations marketing. |
| **Suivi** (suivi) | Diffusion | Ce workflow réalise la récupération et la consolidation des informations de tracking. Il assure également le re-calcul des statistiques de tracking et de diffusions, notamment celles utilisées par les workflows d&#39;archivage de Message Center. Par défaut, il se déclenche toutes les heures. |
| **Mise à jour du statut des événements** (updateEventsStatus) | Exécution des messages transactionnels (Message Center - Exécution) | Ce workflow permet d&#39;attribuer un statut à l&#39;événement. Les statuts d&#39;un événement sont les suivants :<ul><li>En attente : l&#39;événement se trouve dans la file d&#39;attente. Aucun modèle de message ne lui a encore été associé.</li><li>En attente de diffusion : l&#39;événement est dans la file d&#39;attente, un modèle de message lui a été associé et il est en cours de traitement par la diffusion.</li><li>Envoyé : ce statut est copié depuis les logs de diffusion. Il signifie que la diffusion a été envoyée.</li><li>Ignoré par la diffusion : ce statut est copié depuis les logs de diffusion. Il signifie que la diffusion a été ignorée.</li><li>Erreur de diffusion : ce statut est copié depuis les logs de diffusion. Il signifie que la diffusion a échoué.</li><li>Evénement non pris en charge : l&#39;association de l&#39;événement à un modèle de message a échoué. L&#39;événement ne sera pas retraité.</li></ul> |
| **Actualiser pour la délivrabilité** (deliverabilityUpdate) | Diffusion | Ce workflow s’exécute de nuit et gère les règles de qualification des e-mails de rebond, ainsi que la liste des domaines et des MX. Pour ce faire, le port HTTPS doit être ouvert sur la plateforme. |