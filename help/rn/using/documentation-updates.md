---
title: Mises à jour de la documentation d'Adobe Campaign Classic
description: Cette page répertorie toutes les nouvelles fonctionnalités et mises à jour de la documentation pour chaque version d'Adobe Campaign Classic.
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0b3622bb0ac95eff61e2d96332e67623dffa68be

---


# Mises à jour de la documentation{#documentation-updates}

Découvrez l&#39;ensemble des mises à jour les plus récentes de la documentation d&#39;Adobe Campaign Classic.

Cette page répertorie toutes les nouvelles fonctionnalités et mises à jour de la documentation pour chaque version d&#39;Adobe Campaign Classic.

Vous pouvez également consulter les [notes de mise à jour d&#39;Adobe Campaign Classic](../../rn/using/latest-release.md).

## Avril 2020 {#april-2020}

La table des droits  du a été déplacée vers la documentation Accès à une base de données externe (). [En savoir plus](../../platform/using/remote-database-access-rights.md)

La FAQ a été mise à jour avec des conseils sur la façon de vider le cache logiciel et dur. [En savoir plus](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear)

La section des meilleures pratiques relatives aux modèles de données a été améliorée avec des informations supplémentaires sur les index. [En savoir plus](../../configuration/using/data-model-best-practices.md#indexes)

La section décrivant le modèle de données  Adobe Campaign prédéfini a été mise à jour avec plus de détails sur chaque tableau prêt à l&#39;emploi et des liens vers les modules pertinents. [En savoir plus](../../configuration/using/data-model-description.md)

Les cas d&#39;utilisation du guide &quot;Automatisation avec &quot; ont été réorganisés en sections thématiques. [En savoir plus](../../workflow/using/using-the-local-approval-activity.md)

Les sections de qualification [du courrier](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification) Rebond et des règles [de gestion des](../../delivery/using/understanding-delivery-failures.md#email-management-rules) courriels ont été améliorées grâce à des informations mises à jour.

L’article  Adobe Campaign MTA amélioré a été mis à jour. Elle ne s&#39;applique désormais qu&#39;aux Campaign Classic. [En savoir plus](https://helpx.adobe.com/campaign/kb/acc-campaign-enhanced-mta.html)

## Mars 2020 {#march-2020}

La page des bonnes pratiques du modèle de données a été mise à jour avec de nouvelles sections, notamment [Séquences](../../configuration/using/data-model-best-practices.md#sequences), [Performances](../../configuration/using/data-model-best-practices.md#performance) et Tableaux [de](../../configuration/using/data-model-best-practices.md#large-tables)grande taille. [En savoir plus](../../configuration/using/data-model-best-practices.md)

Une nouvelle section décrivant le modèle de données  Adobe Campaign prédéfinies et l’interaction de tableaux prêts à l’emploi est désormais disponible. [En savoir plus](../../configuration/using/data-model-description.md)

Des ressources supplémentaires ont été ajoutées au  de documentation. [En savoir plus](../../campaign-classic-home.md)

Un exemple d’utilisation a été ajouté sur la manière d’intégrer un   d’Adobe dans un courrier électronique en. [En savoir plus](../../integrations/using/inserting-a-dynamic-image.md)

Une nouvelle section détaillant les différentes langues disponibles dans  Adobe Campaign est maintenant disponible. [En savoir plus](../../platform/using/adobe-campaign-workspace.md#languages)

La page de gestion d&#39;accès a été mise à jour avec plus d&#39;informations sur les  de. [En savoir plus](../../platform/using/access-management.md#named-rights)

## Février 2020 {#february-2020}

Une nouvelle section présentant les meilleures pratiques et les recommandations clés lors de la conception du modèle de données Adobe Campaign  est maintenant disponible. [En savoir plus](../../configuration/using/data-model-best-practices.md)

La section &quot;Envoi du courrier électronique&quot; a été renommée &quot;Configurations techniques des courriers électroniques&quot;. [En savoir plus](../../installation/using/email-deliverability.md)

Le  FAQ sur la délivrabilité a été mis à jour avec plus de détails sur le message d&#39;erreur &quot;quotas satisfaits&quot;. [En savoir plus](https://helpx.adobe.com/campaign/kb/acc-deliverability-faq.html#FAQ)

AMP for Email étant désormais pris en charge par trois fournisseurs de messagerie (Gmail, Outlook et Mail.ru), la section décrivant comment définir le contenu interactif avec AMP a été mise à jour. [En savoir plus](../../delivery/using/defining-interactive-content.md)

La section Archivage du courrier électronique a été clarifiée. [En savoir plus](../../installation/using/email-archiving.md#recommendations-and-limitations)

## 20.1 - 17/02/2020{#release-20-1}

**Nouvelles fonctionnalités de cette version**

Snowflake  Connector - [Lire la suite](../../platform/using/specific-configuration-database.md#configure-access-to-snowflake)

Améliorations apportées au connecteur Hadoop - [En savoir plus](../../platform/using/specific-configuration-database.md#configure-access-to-hadoop-3)

**Autres mises à jour de la documentation accompagnant cette version**

Les guides [d&#39;installation](../../installation/using/before-reading.md), de [production](../../production/using/foreword.md) et de [configuration](../../configuration/using/additional-parameters.md) ont été mis à jour avec la nouvelle unité système utilisée par le démarrage du service nlserver. Vous pouvez toujours utiliser /etc/init.d/nlserver6, mais nous vous recommandons maintenant d’utiliser la commande systemctl pour interagir avec le service nlserver.

Le guide d’installation a été mis à jour et synchronisé avec la dernière version de la matrice de compatibilité. De nouveaux systèmes pris en charge ont été ajoutés. Les occurrences de systèmes obsolètes et non pris en charge ont été supprimées. [En savoir plus](../../installation/using/before-reading.md)

La matrice de compatibilité a été mise à jour avec les connecteurs de Hadoop 3.0 et Snowflake. [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix.html)

Une bonne pratique sur le  IP a été ajoutée au guide d’installation. [En savoir plus](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

La section Processus de nettoyage de base de données a été mise à jour. Les chiffres de lot fournis reflètent désormais l’implémentation du code. [En savoir plus](../../production/using/database-cleanup-workflow.md)

Une limitation du  sur HTTP a été ajoutée au guide de messagerie transactionnelle. [En savoir plus](../../production/using/database-cleanup-workflow.md)

Des informations ont été ajoutées sur la nouvelle option qui vous permet de définir un délai d’expiration pour le **[!UICONTROL JavaScript code]** **[!UICONTROL Advanced JavaScript code]** et le flux de travail  . [En savoir plus](../../workflow/using/sql-code-and-javascript-code.md)

Des informations ont été ajoutées sur la nouvelle  **[!UICONTROL Start Pending]** de disponible dans le noeud **[!UICONTROL Administration]** > **[!UICONTROL Audit]** > **[!UICONTROL Workflows Status]** . [En savoir plus](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

Le guide [Envoi de notifications](../../delivery/using/about-mobile-app-channel.md) Push a été déplacé, réorganisé et amélioré avec des informations plus précises.

Le nouveau paramètre pour la configuration du rapport des URL a été documenté [ici](../../reporting/using/properties-of-the-report.md#defining-additional-settings).

La page de la matrice **des fonctionnalités hébergées et sur site** Campaign Classic a été mise à jour avec les nouveaux connecteurs de  de. [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/acc-on-prem-vs-hosted.html)

La page de la matrice **des fonctionnalités** Campaign Classic a été mise à jour. [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix.html)

Le nouveau **[!UICONTROL Cleanup of Nmsaddress]** processus a été documenté [ici](../../production/using/database-cleanup-workflow.md#cleanup-of-nmsaddress).

Une limitation a été ajoutée lors de l’utilisation d’un    dans un flux de travail. [En savoir plus](../../workflow/using/query.md).

Une nouvelle section a été ajoutée pour détailler les règles améliorées de validation des adresses électroniques afin d’envoyer une adresse au en cas d’erreur logicielle. [En savoir plus](../../delivery/using/understanding-quarantine-management.md#soft-error-management)

Le paramètre du fichier de configuration indiquant qu’une instance utilise ou non la MTA améliorée est maintenant documenté. [En savoir plus](../../installation/using/the-server-configuration-file.md#mta)

## Janvier 2020 {#january-2020}

La section Délivrabilité a été déplacée, réorganisée et améliorée, et son contenu mis à jour. [En savoir plus](../../delivery/using/about-deliverability.md)

Une nouvelle section concernant les notions de base des modèles de données d&#39;Adobe Campaign Classic et l&#39;accès à la description de chaque table est désormais disponible. [En savoir plus](../../configuration/using/about-data-model.md)

L&#39;article relatif à l&#39;agent de transfert d&#39;emails (MTA) amélioré d&#39;Adobe Campaign a été mis à jour. Il contient des informations plus détaillées sur l&#39;installation d&#39;un package de typologie spécifique sur les instances qui n&#39;ajoutent pas les en-têtes MTA amélioré nécessaires à chaque message. [En savoir plus](https://helpx.adobe.com/campaign/kb/acc-campaign-enhanced-mta.html#impacts)

Les cas d&#39;utilisation liés à la conception de requêtes ont été réorganisés en sections distinctes. [En savoir plus](../../workflow/using/querying-recipient-table.md)

Une nouvelle section sur les conseils et astuces relatifs à la gestion des offres et à l&#39;utilisation du module Interaction dans Adobe Campaign Classic est désormais disponible. [En savoir plus](../../interaction/using/interaction-best-practices.md#tips-managing-offers)

La documentation Interaction a été enrichie de liens vers plusieurs vidéos permettant de mieux comprendre comment gérer les offres. [En savoir plus](../../interaction/using/interaction-and-offer-management.md)

L&#39;article relatif aux bonnes pratiques permettant d&#39;optimiser les requêtes exécutées sur votre instance a été intégré à la documentation. [En savoir plus](../../workflow/using/query.md#optimizing-queries)

Le guide concernant le reporting a été mis à jour et réorganisé. [En savoir plus](../../reporting/using/about-adobe-campaign-reporting-tools.md)

Un exemple d&#39;utilisation d&#39;une variable d&#39;instance dans un workflow a été ajouté. [En savoir plus](../../workflow/using/javascript-scripts-and-templates.md)

## Décembre 2019 {#december-2019}

L&#39;option &quot;WdbcOptions_TempDbName&quot; a été ajoutée à la liste des options de Campaign. [En savoir plus](../../installation/using/configuring-campaign-options.md)

La page relative à la matrice FDA a été déplacée [ici](../../platform/using/remote-database-access-rights.md).

La page Matrice des droits d&#39;accès a été déplacée [ici](https://docs.adobe.com/content/help/fr-FR/campaign-classic/using/getting-started/administration-basics/assets/accessrights.pdf).

La section décrivant comment définir du contenu interactif avec AMP a été déplacée. [En savoir plus](../../delivery/using/defining-interactive-content.md)

## 19.2 - 12/02/2019{#release-19-2}

**Nouvelles fonctionnalités de cette version**

California Consumer Privacy Act (CCPA) – [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/acc-privacy.html)

Contenu interactif avec AMP - [En savoir plus](../../delivery/using/defining-interactive-content.md)

Surveillance en ligne des workflows - [En savoir plus](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

Messagerie SMS sécurisée (TLS) - [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/sms-connector-protocol-and-settings.html)

**Autres mises à jour de la documentation accompagnant cette version**

La documentation relative à l&#39;agent de transfert d&#39;emails (MTA) amélioré d&#39;Adobe Campaign est désormais disponible. [En savoir plus](https://helpx.adobe.com/campaign/kb/acc-campaign-enhanced-mta.html)

Une nouvelle section a été ajoutée pour expliquer comment résoudre les problèmes liés à un workflow qui reste dans l&#39;état &quot;Démarrer dès que possible&quot; au cours d&#39;une campagne. [En savoir plus](../../production/using/workflow-execution.md#start-as-soon-as-possible-in-campaigns)

Les nouvelles options &quot;NmsOperation_DeliveryPreparingWindow&quot; et &quot;WdbcKillSessionPolicy&quot; ont été ajoutées à la liste des options de Campaign. [En savoir plus](../../installation/using/configuring-campaign-options.md)

Un nouveau document décrivant les notions de base des modèles de données d&#39;Adobe Campaign Classic est désormais disponible. [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/acc-datamodel.html)

La nouvelle option **Durée maximale d&#39;exécution de la personnalisation** des propriétés de diffusion est documentée dans cette [section](../../delivery/using/personalization-fields.md#timing-out-personalization).

Les exemples d&#39;appels d&#39;API utilisant une requête **HttpServletRequest** avec logon() et query() ont été mis à jour. [En savoir plus](../../configuration/using/web-service-calls.md).

Une recommandation pour l&#39;attribut **sqlDefault** de la définition de schéma a été ajoutée. [En savoir plus](../../configuration/using/elements-and-attributes.md#attribute-description).

L&#39;intégration entre Adobe Campaign et Adobe Real-time Customer Data Platform est maintenant référencée dans le guide **Intégration avec Adobe Experience Cloud**. [En savoir plus](../../integrations/using/about-campaign-integrations.md).

## Novembre 2019 {#november-2019}

Un avertissement a été ajouté aux sections [Multiplexage du serveur de mid-sourcing](../../installation/using/mid-sourcing-server.md#multiplexing-the-mid-sourcing-server) et [Support de plusieurs instances de pilotage](../../message-center/using/transactional-messaging-architecture.md#supporting-several-control-instances), indiquant que ces déploiements ne sont pas pris en charge pour les clients hybrides et intégralement hébergés.

Une nouvelle section a été ajoutée pour décrire comment forcer le codage des caractères lors de l&#39;envoi d&#39;un email. [En savoir plus](../../delivery/using/sending-messages.md#character-encoding)

La section Gestion des accès a été mise à jour avec le droit de **protection des informations personnelles**. [En savoir plus](../../platform/using/access-management.md#named-rights)

Des informations ont été ajoutées pour indiquer que le contenu des champs de personnalisation ne peut pas dépasser 1 024 caractères. [En savoir plus](../../delivery/using/personalization-fields.md)

La documentation du panneau de contrôle a été intégrée au nouvel ensemble de documentation collaborative. [En savoir plus](https://docs.adobe.com/content/help/fr-FR/control-panel/using/control-panel-home.html)

Mise à jour du guide de prise en main des bonnes pratiques de diffusion –  [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/delivery-best-practices.html)

## Octobre 2019 {#october-2019}

Mise à jour de la liste des messages d’erreur de Campaign Standard et Campaign Classic –  [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

Amélioration et enrichissement du guide de prise en main du RGPD. Il s’agit maintenant d’une documentation sur la gestion de la vie privée, incluant le RGPD et la CCPA –  [En savoir plus](https://helpx.adobe.com/content/help/fr/campaign/kb/campaign-privacy.html)

Une nouvelle page de résolution des problèmes a été ajoutée concernant le suivi dans Campaign Classic. [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/classic-tracking-troubleshooting.html).

Une nouvelle page de bonnes pratiques relatives au connecteur de données d&#39;Adobe Analytics a été ajoutée. [En savoir plus sur le connecteur de données d&#39;Adobe Analytics](../../platform/using/adobe-analytics-data-connector.md)

Le guide de prise en main des bonnes pratiques de diffusion a été déplacé et mis à jour. [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/delivery-best-practices.html)

Une recommandation a été ajoutée à la documentation du canal SMS. Elle permet d&#39;éviter des problèmes lors de l&#39;utilisation de plusieurs comptes externes en ayant recours au connecteur SMPP générique étendu avec le même compte fournisseur. [En savoir plus](../../delivery/using/sms-channel.md#automatic-reply)

Des informations ont été ajoutées dans la documentation de l&#39;activité Planificateur pour décrire comment empêcher les exécutions simultanées d&#39;un workflow. [En savoir plus](../../workflow/using/scheduler.md)

Les étapes de configuration du rendu du message (Inbox Rendering) pour les installations on-premise ont été ajoutées à la documentation. [En savoir plus](../../delivery/using/inbox-rendering.md#activating-inbox-rendering)

## Septembre 2019 {#september-2019}

Une nouvelle page a été ajoutée au sujet d&#39;instructions générales concernant la maintenance de Campaign Classic. [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/acc-maintenance.html)

Les informations relatives à la surveillance des workflows ont été centralisées dans une nouvelle section dédiée. [En savoir plus](../../workflow/using/monitoring-workflow-execution.md).

Une nouvelle page a été ajoutée concernant les directives générales relatives au tracking dans Adobe Campaign Standard. [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/acc-tracking.html).

Les bonnes pratiques pour améliorer les performances des workflows et des diffusions ont été mises à jour. [En savoir plus sur les workflows](../../workflow/using/workflow-best-practices.md) et [les diffusions](../../delivery/using/monitoring-a-delivery.md#best-practices-performance).

## 19.1 - 30/05/2019{#release-19-1}

**Nouvelles fonctionnalités de cette version**

Panneau de contrôle – [En savoir plus](https://docs.adobe.com/content/help/fr-FR/control-panel/using/control-panel-home.html)

Suivi - [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/PRO_Production_procedures_Audit_trail.html)

**Autres mises à jour de la documentation accompagnant cette version**

Une nouvelle FAQ relative à l&#39;upgrade de build a été créée. [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/build-upgrade-faq.html)

La [matrice de compatibilité](https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix.html) a été mise à jour. La liste des systèmes de base de données pris en charge a été mise à jour, ainsi que les versions Android/iOS et les SDK associés. La [matrice de compatibilité 19.0](https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix-19-0.html) a été archivée.

La page « Fonctionnalités obsolètes et supprimées de Campaign Classic » a été mise à jour. [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/deprecated-and-removed-features.html)

La description du fichier de configuration du serveur a été ajoutée au guide d&#39;installation. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_The_server_configuration_file.html)

Une section décrivant les étapes d&#39;installation et de configuration des modèles hébergés et hybrides a été ajoutée. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/INS_Hybrid_and_Hosted_models_Introduction.html)

Une section décrivant les étapes de désinstallation du serveur Campaign a été ajoutée. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_Uninstalling_Campaign.html)

The [security](https://docs.campaign.adobe.com/doc/AC/getting_started/FR/security.html), [deliverability](https://docs.adobe.com/content/help/fr-FR/campaign-classic/using/sending-messages/deliverability-management/about-deliverability.html) and [privacy](https://helpx.adobe.com/fr/campaign/kb/acc-privacy.html) getting started guides have been updated.

La description de l&#39;option de workflow de pré-processus a été mise à jour pour refléter les modifications de produit. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Action_activities.html#Data_loading__file_)

La note technique Marketing Cloud Triggers a été mise à jour. [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/triggers-and-campaign.html)

La liste des messages d&#39;erreur a été mise à jour. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

Ajout d&#39;informations supplémentaires sur les méthodes d&#39;authentification SOAP pour la messagerie transactionnelle. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/MCE_Introduction_Event_description.html)

Les étapes de configuration d&#39;Apache ont été mises à jour. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/INS_Installing_Campaign_in_Linux__Integration_into_a_Web_server.html#Configuring_Apache_web_server_in_RHEL)

Une nouvelle page contenant la liste des points d&#39;entrée de Campaign Standard et Classic a été ajoutée. [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/campaign-endpoints.html)

L&#39;article relatif aux bonnes pratiques concernant le package Données a été mis à jour. [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/data-package-best-practices.html)

La documentation Gestion des offres a été mise à jour avec une nouvelle section contenant un récapitulatif des bonnes pratiques. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/ITA_Interaction_Overview_Interaction_best_practices.html)

Un nouvel article relatif à l&#39;utilisation du catalogue d&#39;offres d&#39;Adobe Campaign Classic a été créé dans la base de connaissances. [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/offer-best-practices.html)

La section activité Sous-workflow a été enrichie en y incorporant un exemple d&#39;utilisation. [En savoir plus](../../workflow/using/sub-workflow.md)

L&#39;article [Matrice des fonctionnalités de Campaign Classic on-premise/hébergé](https://helpx.adobe.com/fr/campaign/kb/acc-on-prem-vs-hosted.html) de la base de connaissances a été mis à jour avec des informations relatives à l&#39;archivage des emails.

La documentation sur les messages transactionnels a été mise à jour avec une note concernant la publication de modèles. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/MCE_Template_publication.html)

La section Mails rebonds non traités a été mise à jour en y ajoutant des détails sur les champs Adresse de transfert et Adresse pour les erreurs. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/INS_Initial_configuration_Deploying_an_instance.html#Unprocessed_bounce_mails)

Une nouvelle section sur les bonnes pratiques relatives aux workflows a été ajoutée. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Workflow_best_practices.html#Execution_and_performance)

Ajout de deux nouvelles options à la liste des options de Campaign : XtkSecurity_Restrict_EditXML et NmsOperation_OperationMgtDebug.
[En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_Configuring_Campaign_options.html)

Ajout d&#39;informations sur les différents comptes externes disponibles dans Campaign Classic et sur la manière de les configurer.
[En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/PTF_Administration_basics_External_accounts.html)

Mise à jour de la section connecteur de données Analytics pour refléter les modifications de l&#39;interface.
[En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Adobe_Analytics_Data_Connector.html)

Ajout d&#39;informations sur le rapport de billing.
[En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/PRO_Production_procedures_Monitoring_processes.html#Billing_report)

Mise à jour de la documentation sur l&#39;intégration des audiences partagées.
[En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Configuring_shared_audiences_integration_in_Adobe_Campaign.html)

Les notes techniques suivantes ont été mises à jour : [Paramètres et protocole du connecteur SMS](https://helpx.adobe.com/fr/campaign/kb/sms-connector-protocol-and-settings.html) et [Génération automatique de séquence](https://helpx.adobe.com/fr/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence).

La section Workflows techniques a été mise à jour. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/WKF_Technical_workflows_About_technical_workflows.html)

La procédure de configuration des noms de domaines Campaign a été améliorée et mise à jour. [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/domain-name-delegation.html)

La procédure de migration des applications Android entre Google Cloud Messaging (GCM) et Firebase Cloud Messaging (FCM) a été mise à jour. [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/migrate-to-fcm.html)

Le Guide de dimensionnement du matériel pour Campaign a été mis à jour. [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/hardware-sizing-guide.html)

Des informations ont été ajoutées concernant le Query Banding pour le compte externe Teradata. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/PTF_Administration_basics_External_accounts.html#External_database_external_account)

## Janvier 2019{#release-doc-16-01-2019}

La note technique Marketing Cloud Triggers a été mise à jour. [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/triggers-and-campaign.html)

Une note a été ajoutée dans la section d&#39;approbation des offres pour indiquer que la mention « Contenu validé » signifie que le processus de validation du contenu a été effectué, et ce, que toutes les offres aient été activées/validées ou non. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/ITA_Managing_an_offer_catalog_Approving_and_activating_an_offer.html#Approving_offer_content)

Une nouvelle section a été ajoutée dans le guide d&#39;installation. Elle récapitule les options du nœud Administration / Plateforme / Options. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_Configuring_Campaign_options.html)

Des informations ont été ajoutées concernant l&#39;utilisation des adresses de contrôle pour protéger votre liste de messagerie. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_Using_seed_addresses_About_seed_addresses.html)

Les étapes clés de la création et de l&#39;envoi d&#39;une diffusion ont été regroupées dans une nouvelle section, avec des références aux différents canaux, le cas échéant. [En savoir plus](../../delivery/using/steps-about-delivery-creation-steps.md)

La section [Archivage des emails](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html) a été déplacée, réorganisée et améliorée avec des informations plus précises :

* Les bonnes pratiques ont été ajoutées concernant les paramètres des emails par connexion et des adresses IP d&#39;envoi en Cci. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Best_practices)

* Nous avons mis à jour les étapes d&#39;upgrade vers le nouveau système d&#39;archivage des emails (Cci) si vous utilisiez déjà ce type d&#39;archivage avec un build antérieur (avant Adobe Campaign 17.2 – build 8795). [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Updated_email_archiving_system__BCC_)

Un cas d&#39;utilisation a été ajouté au guide Automatiser avec des workflows : envoi d&#39;alertes personnalisées aux opérateurs. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Sending_personalized_alerts_to_operators.html)

La section « Migration vers une nouvelle version » a été mise à jour. La documentation ne détaille désormais que les étapes d&#39;une migration vers Adobe Campaign Classic v7 depuis une version antérieure, car il n&#39;est plus possible de migrer vers Adobe Campaign v6.11. En [savoir plus](https://docs.campaign.adobe.com/doc/AC/en/MIG_Migration_overview_About_migration.html)

La section « Reprises après une diffusion temporairement en échec » a été clarifiée. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_delivery_failures.html#Retries_after_a_delivery_temporary_failure)

Des liens vers la section « Digital Content Editor » ont été ajoutés à la section « Définir le contenu de l&#39;email ». [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Defining_the_email_content.html#Message_content)

La section « Architecture des messages transactionnels » a été mise à jour avec un avertissement indiquant que les instances de contrôle et d&#39;exécution ne peuvent pas être installées sur le même ordinateur. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/MCE_Introduction_Transactional_messaging_architecture.html)

La section « Surveillance des workflows » a été mise à jour avec une note pour les builds 8700 et 8977 (18.10), y compris un lien vers la note technique relative à la procédure d&#39;installation du package Carte thermique des workflows pour ces builds. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/PRO_Production_procedures_Monitoring_processes.html#About_the_Workflow_HeatMap)

Ajout d&#39;un cas d&#39;utilisation pour expliquer comment envoyer un email avec des champs de données personnalisés à l&#39;aide de l&#39;activité Enrichissement dans un workflow. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Email_enrichment_with_custom_date_fields.html)

Les vidéos relatives aux fonctionnalités ont été déplacées [ici](https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/overview.html).

Deux notes techniques ont été ajoutées sur [Teradata](https://helpx.adobe.com/fr/campaign/kb/campaign_fda_teradata.html) et [MySQL 5.7](https://helpx.adobe.com/fr/campaign/kb/campaign_fda_mysql.html).

## 18.10 - 11/05/2018{#release-18-10}

**Nouvelles fonctionnalités de cette version**

Améliorations des notifications push - [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_push_notifications_Setting_up_mobile_app_channel.html#Integrating_the_SDK_into_the_mobile_application)

Activité Gestion des données SQL - [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Action_activities.html#SQL_Data_Management)

Surveillance des workflows - [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/PRO_Production_procedures_Monitoring_processes.html#Workflow_monitoring)

**Autres mises à jour de la documentation accompagnant cette version**

Les API de Campaign Classic sont maintenant disponibles dans une [page dédiée](https://docs.campaign.adobe.com/doc/AC/en/jsapi/index.html). Si vous utilisiez le fichier jsapi.chm, vous devez à présent vous référer à la nouvelle version en ligne.

Mise à jour de la matrice de comptabilité. [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix.html)

La page « Fonctionnalités obsolètes et supprimées de Campaign Classic » a été mise à jour. [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/deprecated-and-removed-features.html)

Un avertissement a été ajouté dans les [notes de mise à jour](https://docs.adobe.com/content/help/fr-FR/campaign-classic/using/release-notes/latest-release.html) et les [anciennes notes de mise à jour](https://docs.campaign.adobe.com/doc/AC/en/RN_legacy.html) pour les builds rappelés. Des builds cumulatifs concernant les versions 17.9, 18.4 et 18.6 ont également été ajoutés.

Les guides de prise en main relatifs à la [sécurité](https://docs.campaign.adobe.com/doc/AC/getting_started/FR/security.html), la [délivrabilité](https://docs.adobe.com/content/help/fr-FR/campaign-classic/using/sending-messages/deliverability-management/about-deliverability.html) et [les upgrades de build](https://docs.campaign.adobe.com/doc/AC/getting_started/FR/buildUpgrade.html) ont été mis à jour.

The [Privacy](https://helpx.adobe.com/fr/campaign/kb/acc-privacy.html) getting started guide has been updated with information on how to invoke the API externally and how to use queryDef to query for the status and download the GDPR file.

Ajout d&#39;un cas d&#39;utilisation de la messagerie transactionnelle pour ajouter à la volée des pièces jointes d&#39;email aux envois sortants. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/MCE_Use_case_Purpose.html)

Mise à jour de la section concernant la résolution des problèmes de seuils de connexions. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/PRO_Troubleshooting_Connection_thresholds.html)

Une section a été ajoutée concernant la configuration d&#39;une connexion proxy. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html#Proxy_connection_configuration)

Mise à jour de la section concernant la restriction des commandes externes autorisées. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html#Restricting_authorized_external_commands)

Ajout d&#39;une section concernant la résolution des problèmes relatifs à l&#39;utilisation du protocole SFTP. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/PTF_Importing_and_exporting_data_SFTP_server_usage.html)

La section de présentation du guide Envoyer les messages a été réorganisée. Des informations ont été ajoutées sur le processus global de création de diffusions et leurs différents types. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_About_deliveries_and_channels_Communication_channels.html)

La liste des messages d&#39;erreur a été mise à jour. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

Déplacement de la section portant sur l&#39;utilisation des adresses de contrôle vers le chapitre de présentation du guide Envoyer les messages. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_Using_seed_addresses_About_seed_addresses.html)

Ajout d&#39;un nouveau cas d&#39;utilisation de workflow : gestion des mises à jour à partir d&#39;exécutions de workflows simultanés. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Coordinating_data_updates.html)

La section « Inbox rendering » a été mise à jour en y ajoutant des informations supplémentaires sur le programme Litmus et une procédure plus détaillée. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_Inbox_rendering.html#Multiplexing_the_mid-sourcing_server)

La section « SpamAssassin » a été améliorée. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_SpamAssassin.html)

Un cas d&#39;utilisation a été ajouté à la section « Gestion de la fatigue marketing avec les règles de pression ». [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/CMP_Campaign_Optimization_Pressure_rules.html#Sending_only_the_highest-weighted_messages)

Un nouveau cas d&#39;utilisation décrivant la création d&#39;un workflow de diffusion cross-canal est désormais disponible. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Cross-channel_delivery_workflow.html)

Certaines recommandations ont été ajoutées à la section « Archiver les emails ». [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_deliverability.html#Activating_emails_BCC_archiving)

Une nouvelle recommandation a été ajoutée concernant la résolution d&#39;écran minimale pour une utilisation optimale d&#39;Adobe Campaign. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Adobe_Campaign_workspace.html#Screen_resolution)

Le guide d&#39;intégration d&#39;Experience Manager a été mis à jour et quelques éclaircissements ont été ajoutés à la configuration de cette intégration. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/ITG_Adobe_Experience_Manager_About_Adobe_Experience_Manager.html)

Ajout d&#39;informations relatives à la différence entre la liste de type Groupe et la liste de type Liste. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/PTF_Profile_management_Creating_and_managing_lists.html#About_lists_in_Adobe_Campaign)

Mise à jour du code nécessaire pour envoyer un extrait de rapport en tant que pièce jointe par email. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Sending_a_report_to_a_list.html#Step_3-_Creating_the_workflow)

Ajout d&#39;un exemple de création d&#39;une requête pour filtrer les destinataires qui n&#39;ont ouvert aucun email au cours des 7 derniers jours. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Designing_queries.html#Recipients_who_did_not_open_any_delivery)

Mise à jour du guide d&#39;intégration Partage d&#39;audiences avec Adobe Experience Cloud. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Sharing_audiences_with_Adobe_Experience_Cloud.html)

La page d&#39;aide des questions courantes contient désormais des informations sur les langues disponibles pour Campaign, la traduction des formulaires Web et les emails multilingues. [En savoir plus](../../platform/using/common-questions.md)

Les différences entre les instances en anglais américain et en anglais britannique sont maintenant répertoriées dans une section dédiée. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Adobe_Campaign_workspace.html#Formats_and_units)

La page d&#39;aide [Questions courantes](../../platform/using/common-questions.md) renvoie désormais à la page des messages d&#39;erreur.

Des informations concernant le mode de tracking &quot;Ouvrir&quot; ont été ajoutées. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_Tracking_messages_Personalizing_URL_tracking.html)

Ajout d&#39;informations sur la résolution minimale pour les applications Web et les formulaires Web. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/WEB_Web_forms_About_web_forms.html)

Le guide d&#39;intégration des solutions Adobe Experience Cloud et Campaign a été mis à jour et réorganisé. [En savoir plus](../../integrations/using/about-campaign-integrations.md)

Une section relative à l&#39;utilisation des variables Texte dans les formulaires Web a été ajoutée. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/WEB_Web_forms_Static_elements_in_a_web_form.html#Using_text_variables)

Les modes de tracking des URL des messages sont maintenant détaillés. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_Tracking_messages_How_to_configure_tracked_links.html)

La section de création d&#39;une instance a été réorganisée. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/INS_Initial_configuration_Creating_an_instance_and_logging_on.html)

L&#39;envoi d&#39;emails sur un mobile japonais est maintenant documenté dans une nouvelle section. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Defining_the_email_content.html#Sending_emails_on_Japanese_mobiles)

La section « Optimiser la personnalisation » a été mise à jour en y incorporant des informations complémentaires. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_Personalizing_deliveries_Personalization_fields.html#Optimizing_personalization)

## 18.6 - 07/09/2018{#release-18-6}

**Nouvelles fonctionnalités de cette version**

Mise à jour de la matrice de comptabilité. [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix.html)

La documentation JSAPI a été mise à jour. [En savoir plus](https://support.neolane.net/webApp/extranetLogin)

La page Fonctionnalités obsolètes et supprimées a été mise à jour. [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/deprecated-and-removed-features.html)

**Autres mises à jour de la documentation accompagnant cette version**

Les guides de l&#39;utilisateur de Campaign Classic ont été renommés afin de simplifier la navigation, d&#39;améliorer l&#39;expérience utilisateur, l&#39;accès aux informations et l&#39;auto-assistance. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/fr/browseAC.html)

La liste des fonctions disponibles dans l&#39;éditeur d&#39;expression a été mise à jour. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/PTF_Creating_queries_Defining_filter_conditions.html#List_of_functions)

Le guide Prise en main sur la sécurité a été mis à jour avec des informations expliquant comment protéger les pages contenant des informations personnelles. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/getting_started/FR/security.html)

La liste des messages d&#39;erreur a été mise à jour. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

Une section de résolution de problèmes a été ajoutée dans la documentation d&#39;intégration IMS. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/ITG_Connecting_via_an_Adobe_ID_IMS_troubleshooting.html)

Le guide de prise en main de l&#39;upgrade de build a été mis à jour. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/getting_started/FR/buildUpgrade.html)

La section de configuration de l&#39;affinité IP a été mise à jour. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Mid-sourcing_server.html#Multiplexing_the_mid-sourcing_server)

Une section de résolution de problèmes de performance et de débit a été ajoutée. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/PRO_Troubleshooting_Performance_and_throughput_issues.html)

La liste des blocs de personnalisation intégrés a été mise à jour avec des exemples. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_Personalizing_deliveries_Personalization_blocks.html#Out-of-the-box_personalization_blocks)

La liste des raisons d&#39;échec des diffusions a été mise à jour. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_delivery_failures.html#Delivery_failure_types_and_reasons)

Une nouvelle section relative à la gestion des définitions de package a été ajoutée. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/PTF_Administration_basics_Working_with_data_packages.html#Managing_package_definitions)

La section concernant l&#39;intégration de Campaign avec Adobe Analytics - Connecteurs de données a été améliorée et réorganisée. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Adobe_Analytics_Data_Connector.html)

Une nouvelle section Tutoriels a été ajoutée, avec des liens vers des guides détaillés et des vidéos pratiques. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Tutorials.html)

Une nouvelle note technique sur le protocole et les paramètres du connecteur SMS a été créée. [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/sms-connector-protocol-and-settings.html)

Le guide de prise en main des bonnes pratiques de diffusion a été mis à jour. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/getting_started/FR/deliveryBestPractices.html)

La configuration du compte Microsoft Dynamics 365 avec déploiement de l&#39;API Web a été mise à jour. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_CRM_Connectors.html#Example_for_Microsoft_Dynamics)

La procédure d&#39;installation d&#39;Adobe Campaign Classic sur une plateforme Windows a été mise à jour. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/INS_Installing_Campaign_in_Windows__Installing_the_server.html)

La période de partage d&#39;audiences entre Adobe Experience Cloud et Campaign Classic a été détaillée. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Importing_and_exporting_audiences.html)

L&#39;article de la base de connaissances complet concernant la liste Campaign Classic a été mis à jour. [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/article-list.html)

Une nouvelle note technique concernant l&#39;amélioration des performances et les bonnes pratiques est disponible en ligne. [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/best-practices-for-performance-improvement.html)

Un exemple de test A/B a été mis à jour. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_A-B_testing.html)

La page relative aux questions courantes/FAQ de Campaign Classic a été mise à jour. [En savoir plus](../../platform/using/common-questions.md)

## 18.4 - 24/04/2018{#release-18-4}

**Nouvelles fonctionnalités de cette version**

Règlement général sur la protection des données de l&#39;UE (RGPD) – [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/acc-privacy.html)

Profils actifs - [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/PTF_Profile_management_About_profiles.html#Active_profiles)

Amélioration du connecteur push Android - [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_push_notifications_Setting_up_mobile_app_channel.html#Android_connectors)

**Autres mises à jour de la documentation accompagnant cette version**

Les notes de mise à jour ont été améliorées pour assurer une meilleure expérience utilisateur et incluent désormais tous les correctifs relatifs aux demandes des clients.  [En savoir plus](https://docs.adobe.com/content/help/fr-FR/campaign-classic/using/release-notes/latest-release.html)

Une nouvelle page a été ajoutée avec les questions les plus courantes concernant Campaign Classic. [En savoir plus](../../platform/using/common-questions.md)

La liste des messages d&#39;erreur a été mise à jour. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

La note technique Marketing Cloud Triggers a été mise à jour. [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/triggers-and-campaign.html)

Une note technique a été ajoutée expliquant comment installer et déployer le package concernant la protection des informations personnelles (RGPD) pour les anciennes versions de Campaign Classic. [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/how-to-install-gdpr-package-on-legacy-versions.html)

Une note technique relative au nouveau mécanisme de génération automatique de séquence a été ajoutée. [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/sequence_auto_generation.html)

La documentation JSAPI a été mise à jour. [En savoir plus](https://support.neolane.net/webApp/extranetLogin)

Mise à jour de la matrice de comptabilité. [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix.html)

Une nouvelle page répertoriant les fonctionnalités et versions obsolètes est désormais disponible. [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/deprecated-and-removed-features.html)

Certaines limites connues et bonnes pratiques concernant le SGBDR ont été ajoutées. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/INS_Prerequisites_and_recommendations__Database.html)

En savoir plus sur les bonnes pratiques concernant l&#39;utilisation du protocole SFTP. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/PTF_Importing_and_exporting_data_SFTP_server_usage.html)

La liste des workflows techniques a été mise à jour. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/WKF_Technical_workflows_About_technical_workflows.html)

La liste des articles de la base de connaissances (précédemment connue sous le nom de « notes techniques ») est maintenant disponible ici. [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/article-list.html)

Les [vidéos pratiques](https://docs.campaign.adobe.com/doc/AC/en/Videos/Videos.html) ont été mises à jour.

La documentation LINE a été mise à jour suite à l&#39;obsolescence du package LINE. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_messages_on_mobiles_LINE_channel.html)

Mise à jour de la documentation concernant le calcul des indicateurs de rapport. [En savoir plus](../../reporting/using/indicator-calculation.md)

Ajout d&#39;informations sur l&#39;alignement du fichier de fuseau horaire avec Oracle. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/MIG_Configuration_General_configurations.html#Oracle)

Ajout d&#39;une nouvelle section « Suivre les diffusions » contenant des informations actualisées sur les échecs de diffusions et la gestion des mises en quarantaine. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Monitoring_a_delivery.html)

Réorganisation de la section « Blocs de personnalisation » avec de nouvelles informations concernant les blocs de personnalisation d&#39;usine.
[En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_Personalizing_deliveries_Personalization_blocks.html)

Réorganisation de la section Archiver les emails avec de nouvelles informations concernant la configuration des fichiers ```config-<instance name>.xml```. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Activating_email_archiving__on_premise_)

Mise à jour des informations concernant le workflow technique du Message Center (Pilotage). [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/WKF_Technical_workflows_Message_Center__Control_.html)

Ajout d&#39;informations sur les limites de débit lors de la configuration d&#39;un relais SMTP. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html#Personalizing_delivery_parameters)

## 17.12 - 14/12/2017{#release-doc-14-12-2017}

La documentation d&#39;[Adobe Campaign Classic](https://helpx.adobe.com/fr/support/campaign/classic.html) a été réorganisée afin d&#39;en améliorer l&#39;utilisation.

Une nouvelle section Tutoriels a été ajoutée pour faciliter l&#39;accès à des ressources d&#39;aide, des cas pratiques, des exemples et des vidéos concernant les principales fonctionnalités de Campaign. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Tutorials.html)

Une nouvelle section Tutoriels a été ajoutée pour vous aider à surveiller le statut de votre diffusion, mais aussi les erreurs possibles, et apprendre à les corriger. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Monitoring_a_delivery.html)

La liste des messages d&#39;erreur a été mise à jour. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

La note technique Marketing Cloud Triggers a été mise à jour. [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/triggers-and-campaign.html)

Le guide de migration de Campaign Classic a été ajouté à la collection. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/MIG_Migration_overview_About_migration.html)

La matrice de compatibilité de Campaign a été mise à jour. [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix.html)

Le cas échéant, les instructions de configuration et d&#39;installation mentionnent désormais le modèle d&#39;hébergement appliqué. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/fr/INS_Parametrages_additionnels_Configuration_du_serveur_Campaign.html)

Nouvel article de la base de connaissances pour mettre en évidence la configuration et les différences de fonctionnalités entre les déploiements On-premise, hybrides et Managed Services. [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/acc-on-prem-vs-hosted.html)

Ajout d&#39;instructions décrivant comment installer un package standard. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/INS_Initial_configuration_Installing_packages.html)

Ajout d&#39;informations sur la configuration de l&#39;intégration avec Audience Manager ou People core service. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Configuring_shared_audiences_integration_in_Adobe_Campaign.html)

Mise à jour de la documentation d&#39;installation pour indiquer que pgcrypto est désormais nécessaire pour l&#39;installation de Campaign en cas d&#39;utilisation de PostSQL. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/INS_Installing_Campaign_in_Linux__Prerequisites.html#Database_access_layers)

## 17.9 - 25/09/2017{#release-17-9}

**Nouvelles fonctionnalités de cette version**

Améliorations apportées à ACS Connector

Connecteur SAP HANA - [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Accessing_an_external_database.html#SAP_HANA)

Connecteur Hadoop via HiveSQL - [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Accessing_an_external_database.html#Hadoop)

Canal LINE : améliorations de la messagerie - [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_messages_on_mobiles_LINE_channel.html)

**Autres mises à jour de la documentation accompagnant cette version**

De nouveaux exemples de requêtes ont été ajoutés. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Designing_queries.html#Filtering_duplicated_recipients)

Le guide des bonnes pratiques de diffusion a été mis à jour. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/getting_started/FR/deliveryBestPractices.html)

Un exemple de test A/B a été mis à jour avec des instructions manquantes. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_A-B_testing.html)

Les vidéos pratiques ont été mises à jour. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/Videos/Videos.html)

Mise à jour de la section relative à l&#39;archivage des emails. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html)

Précisions à propos de l&#39;utilisation du planificateur dans un workflow. [En savoir plus](../../workflow/using/scheduler.md)

Ajout des bonnes pratiques relatives aux workflows en pause. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Executing_a_workflow.html)

Nouvelle procédure concernant le prétraitement du fichier pour l&#39;importation et le post-traitement lors de l&#39;exportation de données dans un workflow. Consulter [cette section](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Importing_data.html).

Le mécanisme de quarantaine de la documentation relative aux messages SMS a été mis à jour pour refléter les spécificités de la gestion des erreurs concernant le connecteur SMPP générique étendu. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_quarantine_management.html#SMS_quarantines).

La documentation de Mobile App Channel a été améliorée en y incorporant une procédure détaillée pour l&#39;envoi de notifications enrichies sur Android. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_push_notifications_Setting_up_mobile_app_channel.html#Rich_notifications).

La documentation Inbox rendering a été mise à jour. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_Inbox_rendering.html).

La documentation relative à la mise en place du tracking Web a été améliorée en y ajoutant des notes et un exemple mis à jour. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/CFG_Setting_up_web_tracking_Additional_parameters.html#Redirection_server_configuration).

La documentation du canal SMS a été mise à jour. Quelques éclaircissements ont été ajoutés à la section Réponse automatique s&#39;appliquant au connecteur SMPP générique étendu. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_messages_on_mobiles_SMS_channel.html#Creating_an_SMPP_external_account).

La documentation du module Social Marketing a été mise à jour. [En savoir plus](../../social/using/about-social-marketing.md).

Une nouvelle note technique relative au rodage des adresses IP a été ajoutée. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/Technotes/AdobeCampaign_Deliverability_IP_Warming_overview.pdf).

Une nouvelle section de prise en main de l&#39;upgrade de build a été ajoutée. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/getting_started/FR/buildUpgrade.html).

## Mai 2017{#release-doc-30-05-2017}

Disponibilité d&#39;un nouveau guide de prise en main : il présente certaines des bonnes pratiques que vous pouvez appliquer pour la diffusion de vos communications avec Adobe Campaign, depuis la création et le ciblage jusqu&#39;à l&#39;envoi et le suivi – [En savoir plus](https://docs.campaign.adobe.com/doc/AC/getting_started/FR/deliveryBestPractices.html)

Mise à jour du guide de prise en main sur la sécurité. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/getting_started/FR/security.html)

Mise à jour de la [documentation « Archiver les emails »](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html) avec la section [« Email Cci »](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Configuring_the_BCC_email_address__on_premise_) et les [étapes détaillées pour activer la fonctionnalité](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Sending_messages.html#Archiving_emails).

Ajout et mise à jour de certaines vidéos. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/Videos/Videos.html)

Découvrez comment envoyer une diffusion à des destinataires chargés depuis un fichier externe sans mettre à jour la base de données. [En savoir plus](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients)

Mise à jour de l&#39;exemple sur le double opt-in. [En savoir plus](../../web/using/use-cases--web-forms.md)

## Mars 2017{#release-doc-31-03-2017}

Délivrabilité : mise à jour du [guide de prise en main](https://docs.adobe.com/content/help/fr-FR/campaign-classic/using/sending-messages/deliverability-management/about-deliverability.html). La documentation sur la délivrabilité contient maintenant une [présentation](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_About_deliverability.html) plus détaillée et une description [du processus et des principales étapes d&#39;implémentation](../../delivery/using/deliverability-key-points.md).

Déplacement et enrichissement de la section &quot;Envoyer par vagues&quot; avec des exemples, des recommandations et des cas pratiques détaillés.    [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Sending_messages.html#Sending_using_multiple_waves)

Ajout d&#39;un tableau décrivant les erreurs propres aux messages SMS à la section &quot;Gestion des quarantaines&quot;. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_quarantine_management.html#SMS_quarantines)

Workflows : ajout d&#39;un exemple de workflow multicanal. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Action_activities.html#Cross-channel_deliveries)

Marketing Cloud Triggers : ajout d&#39;une technote sur la configuration et l&#39;utilisation du service dans Adobe Campaign. [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/triggers-and-campaign.html)

Réorganisation et enrichissement du guide Workflow. Trouvez facilement des informations sur la [création](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Building_a_workflow.html) et l&#39;[exécution](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Executing_a_workflow.html) d&#39;un workflow. Découvrez comment [cibler](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Targeting_data.html) et [gérer](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Targeting_data.html#Data_Management) vos données, [importer](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Importing_data.html)[](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_How_to_use_workflow_data.html#Updating_the_database)[ des données et utiliser des données de workflow pour mettre à jour la base de données ou envoyer des diffusions](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_How_to_use_workflow_data.html#Delivering_via_a_workflow).

Disponibilité d&#39;un exemple de création de [workflow d&#39;import](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_How_to_use_workflow_data.html#Delivering_via_a_workflow) suite aux [bonnes pratiques d&#39;import.
](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Importing_data.html#Import_best_practices)
Mise à jour du guide d&#39;installation pour cette nouvelle version. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/INS_Architecture_and_hosting_models_General_architecture.html)

Mise à jour de la matrice de comptabilité. [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix.html)

L&#39;inclusion de coupons à vos envois d&#39;emails offrent une valeur ajoutée aux destinataires. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_Personalizing_deliveries_Personalized_coupons.html)

## Adobe Campaign v7 - 16/03/2017{#release-17-2}

**Nouvelles fonctionnalités de cette version**

ACS Connector

API Web pour Microsoft Dynamics - [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_CRM_Connectors.html#Example_for_Microsoft_Dynamics)

Méthode BCC d&#39;archivage des emails - [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Updated_email_archiving_system__BCC_)

Connecteur Amazon Simple Storage Service (S3) – [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Event_activities.html#File_transfer)

