---
title: Mises à jour de la documentation Adobe Campaign Classic
description: Cette page répertorie toutes les nouvelles fonctionnalités et mises à jour de la documentation pour chaque version d’Adobe Campaign Classic.
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
source-git-commit: cc6f0f2989977c5a199dbfd413c6a2bac4628545

---


# Mises à jour de la documentation{#documentation-updates}

Découvrez toutes les dernières mises à jour de la documentation Adobe Campaign Classic.

Cette page répertorie toutes les nouvelles fonctionnalités et mises à jour de la documentation pour chaque version d’Adobe Campaign Classic.

You can also consult the [Adobe Campaign Classic Release Notes](../../rn/using/latest-release.md).

## 20.1 - 17/02/2020{#release-20-1}

**Nouvelles fonctionnalités de cette version**

Snowflake FDA Connector - [Lire la suite](../../platform/using/specific-configuration-database.md#configure-access-to-snowflake)

Améliorations du connecteur Hadoop FDA - [En savoir plus](../../platform/using/specific-configuration-database.md#configure-access-to-hadoop-3)

**Autres mises à jour de la documentation accompagnant cette version**

Les guides [d&#39;installation](../../installation/using/before-reading.md), de [production](../../production/using/foreword.md) et de [configuration](../../configuration/using/additional-parameters.md) ont été mis à jour avec la nouvelle unité système utilisée par le démarrage du service nlserver. Vous pouvez toujours utiliser /etc/init.d/nlserver6, mais nous vous recommandons maintenant d’utiliser la commande systemctl pour interagir avec le service nlserver.

Le guide d’installation a été mis à jour et synchronisé avec la dernière version de la matrice de compatibilité. De nouveaux systèmes pris en charge ont été ajoutés. Les occurrences de systèmes obsolètes et non pris en charge ont été supprimées. [En savoir plus](../../installation/using/before-reading.md)

La matrice de compatibilité a été mise à jour avec les connecteurs Hadoop 3.0 et Snowflake FDA. [En savoir plus](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

Une bonne pratique sur l’affinité IP a été ajoutée au guide d’installation. [En savoir plus](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

La section Processus de nettoyage de base de données a été mise à jour. Les chiffres de lot fournis reflètent désormais l’implémentation du code. [En savoir plus](../../production/using/database-cleanup-workflow.md)

Une limitation de la FDA sur HTTP a été ajoutée au guide de messagerie transactionnelle. [En savoir plus](../../production/using/database-cleanup-workflow.md)

Des informations ont été ajoutées sur la nouvelle option qui vous permet de définir un délai d’expiration pour le code **** JavaScript et les activités de flux de travail du code **[!UICONTROL JavaScript]** avancé. [En savoir plus](../../workflow/using/sql-code-and-javascript-code.md)

Des informations ont été ajoutées sur la nouvelle vue **[!UICONTROL Démarrer en attente]** disponible dans le noeud **[!UICONTROL Administration]** > **[!UICONTROL Audit]** **[!UICONTROL > État des flux de travail.]** [En savoir plus](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

Le guide [Envoi de notifications](../../delivery/using/about-mobile-app-channel.md) Push a été déplacé, réorganisé et amélioré avec des informations plus précises.

Le nouveau paramètre pour la configuration du rapport des URL a été documenté [ici](../../reporting/using/properties-of-the-report.md#defining-additional-settings).

La page de la matrice **des fonctionnalités hébergées et sur site de** Campaign Classic a été mise à jour avec les nouveaux connecteurs de la FDA. [En savoir plus](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html)

La page de la matrice **des fonctionnalités de** Campaign Classic a été mise à jour. [En savoir plus](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

Le nouveau **[!UICONTROL processus de nettoyage de Nmsaddress]** a été documenté [ici](../../production/using/database-cleanup-workflow.md#cleanup-of-nmsaddress).

Une limitation a été ajoutée lors de l’utilisation d’une activité de requête dans un processus. [En savoir plus](../../workflow/using/query.md).

Une nouvelle section a été ajoutée pour détailler les règles améliorées de validation des adresses électroniques afin d’envoyer une adresse en quarantaine en cas d’erreur logicielle. [En savoir plus](../../delivery/using/understanding-quarantine-management.md#soft-error-management)

Le paramètre du fichier de configuration indiquant qu’une instance utilise ou non la MTA améliorée est maintenant documenté. [En savoir plus](../../installation/using/the-server-configuration-file.md#mta)

## February 2020 {#february-2020}

AMP for Email étant désormais pris en charge par trois fournisseurs de messagerie (Gmail, Outlook et Mail.ru), la section décrivant comment définir le contenu interactif avec AMP a été mise à jour. [En savoir plus](../../delivery/using/defining-interactive-content.md)

La section Archivage du courrier électronique a été clarifiée. [En savoir plus](../../installation/using/email-archiving.md#recommendations-and-limitations)

## Janvier 2020 {#january-2020}

La section Livraison a été déplacée, réorganisée et améliorée avec du contenu mis à jour. [En savoir plus](../../delivery/using/about-deliverability.md)

Une nouvelle section décrivant les bases des modèles de données Adobe Campaign Classic et comment accéder à la description de chaque tableau est désormais disponible. [En savoir plus](../../configuration/using/about-data-model.md)

L’article MTA amélioré d’Adobe Campaign a été mis à jour avec des informations plus détaillées sur l’installation d’un package de typologie spécifique sur les instances qui n’ajoutent pas les en-têtes MTA améliorés requis à chaque message. [En savoir plus](https://helpx.adobe.com/campaign/kb/campaign-enhanced-mta.html#impacts)

Les cas d&#39;utilisation liés à la conception de requêtes ont été réorganisés en sections distinctes. [En savoir plus](../../workflow/using/querying-recipient-table.md)

Une nouvelle section sur les conseils et astuces relatifs à la gestion des offres et à l’utilisation du module Interaction dans Adobe Campaign Classic est désormais disponible. [En savoir plus](../../interaction/using/interaction-best-practices.md#tips-managing-offers)

La documentation de l’interaction a été enrichie de liens vers plusieurs vidéos qui aident à mieux comprendre comment gérer les offres. [En savoir plus](../../interaction/using/interaction-and-offer-management.md)

L’article des meilleures pratiques sur la manière d’optimiser les requêtes exécutées sur votre instance a été intégré à la documentation. [En savoir plus](../../workflow/using/query.md#optimizing-queries)

Le guide des rapports a été mis à jour et réorganisé. [En savoir plus](../../reporting/using/about-adobe-campaign-reporting-tools.md)

Un exemple d’utilisation d’une variable d’instance dans un processus a été ajouté. [En savoir plus](../../workflow/using/javascript-scripts-and-templates.md)

## Décembre 2019 {#december-2019}

L&#39;option &quot;WdbcOptions_TempDbName&quot; a été ajoutée à la liste des options de campagne. [En savoir plus](../../installation/using/configuring-campaign-options.md)

La page Matrice de la FDA a été déplacée [ici](/help/rn/using/assets/fda_rdbms_rights.pdf).

La page Matrice des droits d’accès a été déplacée [ici](https://docs.adobe.com/content/help/en/campaign-classic/using/getting-started/administration-basics/assets/accessrights.pdf).

La section décrivant comment définir du contenu interactif avec AMP a été déplacée. [En savoir plus](../../delivery/using/defining-interactive-content.md)

## 19.2 - 02/12/2019{#release-19-2}

**Nouvelles fonctionnalités de cette version**

California Consumer Privacy Act (CCPA) – [En savoir plus](https://helpx.adobe.com/campaign/kb/acc-privacy.html)

Contenu interactif avec AMP - [En savoir plus](../../delivery/using/defining-interactive-content.md)

Surveillance en direct du flux de travail - [En savoir plus](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

Messagerie SMS sécurisée (TLS) - [En savoir plus](https://helpx.adobe.com/campaign/kb/sms-connector-protocol-and-settings.html)

**Autres mises à jour de la documentation accompagnant cette version**

La documentation MTA améliorée d’Adobe Campaign est désormais disponible. [En savoir plus](https://helpx.adobe.com/campaign/kb/campaign-enhanced-mta.html)

Une nouvelle section a été ajoutée sur la manière de résoudre les problèmes liés à un flux de travail qui reste à l’état &quot;Démarrer dès que possible&quot; dans une campagne. [En savoir plus](../../production/using/workflow-execution.md#start-as-soon-as-possible-in-campaigns)

Les nouvelles options &quot;NmsOperation_DeliveryPreparingWindow&quot; et &quot;WdbcKillSessionPolicy&quot; ont été ajoutées à la liste des options de campagne. [En savoir plus](../../installation/using/configuring-campaign-options.md)

Un nouveau document décrivant les bases des modèles de données Adobe Campaign Classic est désormais disponible. [En savoir plus](https://helpx.adobe.com/campaign/kb/acc-datamodel.html)

La nouvelle option **Durée** d’exécution maximale de la personnalisation dans les propriétés de diffusion est documentée dans cette [section](../../delivery/using/personalization-fields.md#timing-out-personalization).

Les exemples d’appels d’API utilisant une requête **HttpServletRequest** avec logon() et query() ont été mis à jour. [En savoir plus](../../configuration/using/web-service-calls.md).

Une recommandation pour l&#39;attribut **sqlDefault** dans la définition de schéma a été ajoutée. [En savoir plus](../../configuration/using/elements-and-attributes.md#attribute-description).

L’intégration entre Adobe Campaign et la plateforme de données clientes en temps réel d’Adobe est maintenant référencée dans le guide **Intégration d’Adobe Experience Cloud** . [En savoir plus](../../integrations/using/about-campaign-integrations.md).

## November 2019 {#november-2019}

Un avertissement a été ajouté aux sections [Multiplexing the mid-sourcing server](../../installation/using/mid-sourcing-server.md#multiplexing-the-mid-sourcing-server) et [Support de plusieurs instances](../../message-center/using/transactional-messaging-architecture.md#supporting-several-control-instances) de contrôle, indiquant que ces déploiements ne sont pas pris en charge pour les clients hôtes et hybrides complets.

Une nouvelle section a été ajoutée pour décrire comment forcer le codage des caractères utilisé lors de l’envoi d’un courrier électronique. [En savoir plus](../../delivery/using/sending-messages.md#character-encoding)

La section Gestion de l&#39;accès a été mise à jour avec le droit **des données de** confidentialité. [En savoir plus](../../platform/using/access-management.md#named-rights)

Des informations ont été ajoutées pour indiquer que le contenu des champs de personnalisation ne peut pas dépasser 1 024 caractères. [En savoir plus](../../delivery/using/personalization-fields.md)

La documentation du panneau de contrôle a été intégrée au nouvel ensemble de documentation collaborative. [En savoir plus](https://docs.adobe.com/content/help/en/control-panel/using/control-panel-home.html)

Mise à jour du guide de prise en main des bonnes pratiques de diffusion –  [En savoir plus](https://helpx.adobe.com/campaign/kb/delivery-best-practices.html)

## October 2019 {#october-2019}

Mise à jour de la liste des messages d&#39;erreur de Campaign Standard et Campaign Classic –  [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

Amélioration et enrichissement du guide de prise en main du RGPD. Il s&#39;agit maintenant d&#39;une documentation sur la gestion de la vie privée, incluant le RGPD et la CCPA –  [En savoir plus](https://helpx.adobe.com/content/help/en/campaign/kb/campaign-privacy.html)

Une nouvelle page de dépannage a été ajoutée pour le suivi dans Campaign Classic. [En savoir plus](https://helpx.adobe.com/campaign/kb/classic-tracking-troubleshooting.html).

Une nouvelle page de bonnes pratiques pour Adobe Analytics Data Connector a été ajoutée. [En savoir plus sur Adobe Analytics Data Connector](../../platform/using/adobe-analytics-data-connector.md)

Le guide de prise en main des bonnes pratiques de diffusion a été déplacé et mis à jour. [En savoir plus](https://helpx.adobe.com/campaign/kb/delivery-best-practices.html)

Une recommandation a été ajoutée à la documentation du canal SMS afin d’éviter des problèmes lors de l’utilisation de plusieurs comptes externes exploitant le connecteur SMPP générique étendu avec le même compte fournisseur. [En savoir plus](../../delivery/using/sms-channel.md#automatic-reply)

Des informations ont été ajoutées dans la documentation de l’activité du planificateur sur la manière d’empêcher les exécutions simultanées d’un flux de travail. [En savoir plus](../../workflow/using/scheduler.md)

Les étapes de configuration du rendu de la boîte de réception pour les installations sur site ont été ajoutées à la documentation. [En savoir plus](../../delivery/using/inbox-rendering.md#activating-inbox-rendering)

## Septembre 2019 {#september-2019}

Une nouvelle page a été ajoutée afin de fournir des instructions générales pour la maintenance de Campaign Classic. [En savoir plus](https://helpx.adobe.com/campaign/kb/acc-maintenance.html)

Les informations relatives à la surveillance des processus ont été centralisées dans une nouvelle section dédiée. [En savoir plus](../../workflow/using/monitoring-workflow-execution.md).

Une nouvelle page sur les instructions générales relatives au suivi dans Adobe Campaign Classic a été ajoutée. [En savoir plus](https://helpx.adobe.com/campaign/kb/acc-tracking.html).

Les meilleures pratiques pour améliorer les performances des flux de travail et des livraisons ont été mises à jour. [En savoir plus sur les processus](../../workflow/using/workflow-best-practices.md) et [plus sur les livraisons](../../delivery/using/monitoring-a-delivery.md#best-practices-performance).

## 19.1 - 30/05/2019{#release-19-1}

**Nouvelles fonctionnalités de cette version**

Panneau de contrôle – [En savoir plus](https://docs.adobe.com/content/help/en/control-panel/using/control-panel-home.html)

Piste d’audit - [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/PRO_Production_procedures_Audit_trail.html)

**Autres mises à jour de la documentation accompagnant cette version**

Une nouvelle FAQ sur la mise à niveau de la version a été créée. [En savoir plus](https://helpx.adobe.com/campaign/kb/build-upgrade-faq.html)

The [Compatibility matrix](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html) has been updated. La liste des systèmes de base de données pris en charge a été mise à jour, ainsi que les versions Android/iOS et les SDK associés. The [19.0 Compatibility matrix](https://helpx.adobe.com/campaign/kb/compatibility-matrix-19-0.html) has been archived.

La page &quot;Fonctions obsolètes et supprimées de Campaign Classic&quot; a été mise à jour. [En savoir plus](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)

La description du fichier de configuration du serveur a été ajoutée au guide d&#39;installation. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_The_server_configuration_file.html)

Une section décrivant les étapes d’installation et de configuration des modèles hébergés et hybrides a été ajoutée. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/INS_Hybrid_and_Hosted_models_Introduction.html)

Une section décrivant les étapes de désinstallation du serveur Campaign a été ajoutée. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_Uninstalling_Campaign.html)

Les guides [de prise en main de la sécurité](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html), de la [délivrabilité](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html) et de la confidentialité [](https://helpx.adobe.com/campaign/kb/acc-privacy.html) ont été mis à jour.

La description de l’option de processus de pré-processus a été mise à jour afin de refléter les modifications de produit. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Action_activities.html#Data_loading__file_)

La note technique Triggers Marketing Cloud a été mise à jour. [En savoir plus](https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html)

La liste des messages d&#39;erreur a été mise à jour. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

Ajout d’informations supplémentaires sur les méthodes d’authentification SOAP pour la messagerie transactionnelle. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/MCE_Introduction_Event_description.html)

Les étapes de configuration d&#39;Apache ont été mises à jour. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/INS_Installing_Campaign_in_Linux__Integration_into_a_Web_server.html#Configuring_Apache_web_server_in_RHEL)

Une nouvelle page a été ajoutée, avec la liste des points de fin pour Campaign Standard et Classic. [En savoir plus](https://helpx.adobe.com/campaign/kb/campaign-endpoints.html)

L’article sur les bonnes pratiques du module de données a été mis à jour. [En savoir plus](https://helpx.adobe.com/campaign/kb/data-package-best-practices.html)

La documentation Gestion des offres a été mise à jour avec une nouvelle section répertoriant les meilleures pratiques. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/ITA_Interaction_Overview_Interaction_best_practices.html)

Un nouvel article de la base de connaissances sur l’utilisation du catalogue d’offres dans Adobe Campaign Classic a été créé. [En savoir plus](https://helpx.adobe.com/campaign/kb/offer-best-practices.html)

La section Activité du sous-processus a été améliorée avec un exemple d’utilisation. [En savoir plus](../../workflow/using/sub-workflow.md)

L’article de la base de connaissances de la matrice [de la fonctionnalité hébergée et sur site de](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html) Campaign Classic a été mis à jour avec des informations relatives à l’archivage des courriers électroniques.

La documentation sur les messages transactionnels a été mise à jour avec une note concernant la publication de modèles. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/MCE_Template_publication.html)

La section Courriers de rebonds non traités a été mise à jour avec plus de détails sur les champs Adresse et Adresse de transfert pour les erreurs. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/INS_Initial_configuration_Deploying_an_instance.html#Unprocessed_bounce_mails)

Une nouvelle section sur les meilleures pratiques de planification des processus a été ajoutée. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Workflow_best_practices.html#Execution_and_performance)

Ajout de deux nouvelles options à la liste des options de campagne : XtkSecurity_Restrict_EditXML et NmsOperation_OperationMgtDebug.
[En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_Configuring_Campaign_options.html)

Ajout d’informations sur les différents comptes externes disponibles dans Campaign Classic et sur la manière de les configurer.
[En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/PTF_Administration_basics_External_accounts.html)

Mise à jour de la section Connecteur de données Analytics afin de refléter les modifications de l’interface.
[En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Adobe_Analytics_Data_Connector.html)

Ajout d’informations sur le rapport Facturation.
[En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/PRO_Production_procedures_Monitoring_processes.html#Billing_report)

Mise à jour de la documentation sur l’intégration des audiences partagées.
[En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Configuring_shared_audiences_integration_in_Adobe_Campaign.html)

Les notes techniques suivantes ont été mises à jour : Protocole et paramètres [du connecteur](https://helpx.adobe.com/campaign/kb/sms-connector-protocol-and-settings.html) SMS et génération [automatique de la](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)séquence.

La section Processus techniques a été mise à jour. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/WKF_Technical_workflows_About_technical_workflows.html)

La procédure de configuration des noms de domaine de campagne a été améliorée et mise à jour. [En savoir plus](https://helpx.adobe.com/campaign/kb/domain-name-delegation.html)

La procédure de migration des applications Android de Google Cloud Messaging (GCM) vers Firebase Cloud Messaging (FCM) a été mise à jour. [En savoir plus](https://helpx.adobe.com/campaign/kb/migrate-to-fcm.html)

Le Guide de dimensionnement matériel de la campagne a été mis à jour. [En savoir plus](https://helpx.adobe.com/campaign/kb/hardware-sizing-guide.html)

Des informations ont été ajoutées sur la bande de requête pour le compte externe Teradata. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/PTF_Administration_basics_External_accounts.html#External_database_external_account)

## Janvier 2019{#release-doc-16-01-2019}

La note technique Triggers Marketing Cloud a été mise à jour. [En savoir plus](https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html)

Une note a été ajoutée dans la section d’approbation des offres pour indiquer que la mention &quot;Contenu approuvé&quot; indique que le processus d’approbation du contenu a été effectué, que toutes les offres aient été activées/approuvées ou non. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/ITA_Managing_an_offer_catalog_Approving_and_activating_an_offer.html#Approving_offer_content)

Une nouvelle section a été ajoutée dans le guide d&#39;installation, répertoriant les options du noeud Administration / Plateforme / Options. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_Configuring_Campaign_options.html)

Des informations ont été ajoutées sur l&#39;utilisation des adresses de départ pour protéger votre liste d&#39;envoi. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_Using_seed_addresses_About_seed_addresses.html)

Les étapes clés lors de la création et de l’envoi d’une diffusion ont été regroupées dans une nouvelle section, avec des références aux différents canaux, le cas échéant. [En savoir plus](../../delivery/using/steps-about-delivery-creation-steps.md)

La section Archivage [des](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html) courriels a été déplacée, réorganisée et améliorée avec des informations plus précises :

* Des bonnes pratiques ont été ajoutées en ce qui concerne les courriers électroniques par connexion et les paramètres d’IP d’envoi par carte de crédit client. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Best_practices)

* Nous avons mis à jour les étapes de mise à niveau vers le nouveau système d’archivage des e-mails (BCC) si vous utilisiez déjà l’archivage des e-mails avec une version antérieure (avant Adobe Campaign 17.2 - build 8795). [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Updated_email_archiving_system__BCC_)

Un cas d’utilisation a été ajouté au guide Automatisation avec les processus : Envoi d’alertes personnalisées aux opérateurs. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Sending_personalized_alerts_to_operators.html)

La section &quot;Migration vers une nouvelle version&quot; a été mise à jour. La documentation ne détaille désormais que les étapes d’une migration vers Adobe Campaign Classic v7 depuis une version antérieure, car il n’est plus possible de migrer vers Adobe Campaign v6.11. En [savoir plus](https://docs.campaign.adobe.com/doc/AC/en/MIG_Migration_overview_About_migration.html)

La section &quot;Tentatives après un échec temporaire de livraison&quot; a été clarifiée. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_delivery_failures.html#Retries_after_a_delivery_temporary_failure)

Des liens vers la section &quot;Editeur de contenu numérique&quot; ont été ajoutés à la section &quot;Définition du contenu du courrier électronique&quot;. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Defining_the_email_content.html#Message_content)

La section &quot;Architecture de messagerie transactionnelle&quot; a été mise à jour avec un avertissement indiquant que les instances de contrôle et d’exécution ne peuvent pas être installées sur le même ordinateur. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/MCE_Introduction_Transactional_messaging_architecture.html)

La section &quot;Surveillance du flux de travail&quot; a été mise à jour avec une note pour les versions 8700 à 8977 (18.10), y compris un lien vers la note technique sur la façon d’installer le package de Carte de chaleur de flux de travail pour ces versions. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/PRO_Production_procedures_Monitoring_processes.html#About_the_Workflow_HeatMap)

Ajout d’un cas d’utilisation sur la manière d’envoyer un courrier électronique avec des champs de données personnalisés à l’aide de l’activité d’enrichissement dans un processus. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Email_enrichment_with_custom_date_fields.html)

Les vidéos de fonctionnalités ont été déplacées [ici](https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/overview.html).

Deux notes techniques ont été ajoutées sur [Teradata](https://helpx.adobe.com/campaign/kb/campaign_fda_teradata.html) et [MySQL 5.7](https://helpx.adobe.com/campaign/kb/campaign_fda_mysql.html).

## 18.10 - 05/11/2018{#release-18-10}

**Nouvelles fonctionnalités de cette version**

Push notification improvements - [Read more](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_push_notifications_Setting_up_mobile_app_channel.html#Integrating_the_SDK_into_the_mobile_application)

Activité de gestion des données SQL - [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Action_activities.html#SQL_Data_Management)

Surveillance du flux de travail - [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/PRO_Production_procedures_Monitoring_processes.html#Workflow_monitoring)

**Autres mises à jour de la documentation accompagnant cette version**

Les API de Campaign Classic sont maintenant disponibles dans une [page dédiée](https://docs.campaign.adobe.com/doc/AC/en/jsapi/index.html). Si vous utilisiez le fichier jsapi.chm, vous devez à présent vous référer à la nouvelle version en ligne.

Mise à jour de la matrice de comptabilité. [En savoir plus](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

La page &quot;Fonctions obsolètes et supprimées de Campaign Classic&quot; a été mise à jour. [En savoir plus](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)

Dans les notes [de](https://docs.campaign.adobe.com/doc/AC/en/RN.html) mise à jour et les notes [de mise à jour](https://docs.campaign.adobe.com/doc/AC/en/RN_legacy.html)héritées, un avertissement a été ajouté pour les versions qui ont été rappelées. Des versions cumulatives pour les versions 17.9, 18.4 et 18.6 ont également été ajoutées.

Les guides [de prise en main de la mise à niveau](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html)de la sécurité [, de la](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html) délivrabilité [et de la](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) génération ont été mis à jour.

Le guide de prise en main de la [confidentialité](https://helpx.adobe.com/campaign/kb/acc-privacy.html) a été mis à jour avec des informations sur la manière d’appeler l’API en externe et d’utiliser queryDef pour rechercher l’état et télécharger le fichier GDPR.

Ajout d’un cas d’utilisation de la messagerie transactionnelle pour ajouter à la volée des pièces jointes de courrier électronique aux messages sortants. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/MCE_Use_case_Purpose.html)

Mise à jour de la section de dépannage des seuils de connexion. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/PRO_Troubleshooting_Connection_thresholds.html)

Une section a été ajoutée sur la configuration d’une connexion proxy. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html#Proxy_connection_configuration)

Mise à jour de la section sur la restriction des commandes externes autorisées. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html#Restricting_authorized_external_commands)

Ajout d’une section de dépannage relative à l’utilisation du protocole SFTP. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/PTF_Importing_and_exporting_data_SFTP_server_usage.html)

La section d’aperçu du guide Envoi de messages a été réorganisée. Des informations ont été ajoutées sur le processus global de création de distribution et les différents types de distribution. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_About_deliveries_and_channels_Communication_channels.html)

La liste des messages d&#39;erreur a été mise à jour. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

Déplacement de la section sur l’utilisation des adresses de départ vers le chapitre Présentation du guide des messages d’envoi. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_Using_seed_addresses_About_seed_addresses.html)

Ajout d’un nouveau cas d’utilisation du processus : Gestion des mises à jour à partir d’exécutions de flux de travail simultanées. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Coordinating_data_updates.html)

La section &quot;Rendu de la boîte de réception&quot; a été mise à jour avec des informations supplémentaires sur le programme Litmus et une procédure plus détaillée. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_Inbox_rendering.html#Multiplexing_the_mid-sourcing_server)

La section &quot;SpamAssassin&quot; a été améliorée. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_SpamAssassin.html)

Un cas d’utilisation a été ajouté à la section &quot;Gestion de la fatigue marketing avec les règles de pression&quot;. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/CMP_Campaign_Optimization_Pressure_rules.html#Sending_only_the_highest-weighted_messages)

Un nouveau cas d’utilisation décrivant la création d’un processus de diffusion cross-canal est désormais disponible. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Cross-channel_delivery_workflow.html)

Certaines recommandations ont été ajoutées à la section &quot;Archivage des courriels&quot;. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_deliverability.html#Activating_emails_BCC_archiving)

Une nouvelle recommandation a été ajoutée concernant la résolution d’écran minimale pour une utilisation optimale d’Adobe Campaign. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Adobe_Campaign_workspace.html#Screen_resolution)

Le guide d’intégration d’Experience Manager a été mis à jour et quelques éclaircissements ont été ajoutés à la configuration de cette intégration. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/ITG_Adobe_Experience_Manager_About_Adobe_Experience_Manager.html)

Ajout d’informations sur la différence entre la liste des types de groupe et la liste des types de liste. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/PTF_Profile_management_Creating_and_managing_lists.html#About_lists_in_Adobe_Campaign)

Mise à jour du code pour envoyer un extrait de rapport en tant que pièce jointe par courrier électronique. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Sending_a_report_to_a_list.html#Step_3-_Creating_the_workflow)

Ajout d’un exemple de création d’une requête pour filtrer les destinataires qui n’ont pas ouvert de courrier électronique au cours des 7 derniers jours. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Designing_queries.html#Recipients_who_did_not_open_any_delivery)

Mise à jour du guide d’intégration Partage d’audiences avec Adobe Experience Cloud. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Sharing_audiences_with_Adobe_Experience_Cloud.html)

La page d’aide des questions courantes contient désormais des informations sur les langues disponibles pour Campaign, la traduction des formulaires Web et les courriers électroniques multilingues. [En savoir plus](../../platform/using/common-questions.md)

La différence entre les instances Anglais (Etats-Unis) et Anglais (Royaume-Uni) est maintenant répertoriée dans une section dédiée. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Adobe_Campaign_workspace.html#Formats_and_units)

La page d’aide Questions [](../../platform/using/common-questions.md) courantes renvoie désormais à la page des messages d’erreur.

Des informations sur le mode de suivi &quot;Ouvrir&quot; ont été ajoutées. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_Tracking_messages_Personalizing_URL_tracking.html)

Ajoutez des informations sur la résolution minimale pour les applications Web et les formulaires Web. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/WEB_Web_forms_About_web_forms.html)

Le guide d’intégration des solutions Adobe Experience Cloud et Campaign a été mis à jour et réorganisé. [En savoir plus](../../integrations/using/about-campaign-integrations.md)

Une section sur l’utilisation des variables de texte dans les formulaires Web a été ajoutée. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/WEB_Web_forms_Static_elements_in_a_web_form.html#Using_text_variables)

Les modes de suivi des URL dans les messages sont maintenant détaillés. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_Tracking_messages_How_to_configure_tracked_links.html)

La section de création d’instance a été réorganisée. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/INS_Initial_configuration_Creating_an_instance_and_logging_on.html)

L’envoi de courriers électroniques sur des téléphones mobiles japonais est maintenant documenté dans une nouvelle section. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Defining_the_email_content.html#Sending_emails_on_Japanese_mobiles)

La section &quot;Optimisation de la personnalisation&quot; a été mise à jour avec des informations complémentaires. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_Personalizing_deliveries_Personalization_fields.html#Optimizing_personalization)

## 18.6 - 09/07/2018{#release-18-6}

**Nouvelles fonctionnalités de cette version**

Mise à jour de la matrice de comptabilité. [En savoir plus](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

La documentation JSAPI a été mise à jour. [En savoir plus](https://support.neolane.net/webApp/extranetLogin)

La page Fonctions obsolètes et supprimées a été mise à jour. [En savoir plus](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)

**Autres mises à jour de la documentation accompagnant cette version**

Les guides de l’utilisateur de Campaign Classic ont été renommés afin de simplifier la navigation, d’améliorer l’expérience utilisateur, l’accès aux informations et l’auto-assistance. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/browseAC.html)

La liste des fonctions disponibles dans l’éditeur d’expression a été mise à jour. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/PTF_Creating_queries_Defining_filter_conditions.html#List_of_functions)

Le guide Prise en main de la sécurité a été mis à jour avec des informations sur la manière de protéger les pages contenant des PI. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html)

La liste des messages d&#39;erreur a été mise à jour. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

Une section de dépannage a été ajoutée dans la documentation d’intégration IMS. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/ITG_Connecting_via_an_Adobe_ID_IMS_troubleshooting.html)

Le guide de mise à niveau a été mis à jour. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html)

La section de configuration des affinités IP a été mise à jour. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Mid-sourcing_server.html#Multiplexing_the_mid-sourcing_server)

Une section de dépannage Performances et Débit a été ajoutée. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/PRO_Troubleshooting_Performance_and_throughput_issues.html)

La liste des blocs de personnalisation intégrés a été mise à jour avec des exemples. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_Personalizing_deliveries_Personalization_blocks.html#Out-of-the-box_personalization_blocks)

La liste des raisons d&#39;échec de livraison a été mise à jour. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_delivery_failures.html#Delivery_failure_types_and_reasons)

Une nouvelle section sur la gestion des définitions de package a été ajoutée. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/PTF_Administration_basics_Working_with_data_packages.html#Managing_package_definitions)

L’intégration de Campaign avec la section Connecteur de données Adobe Analytics a été améliorée et réorganisée. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Adobe_Analytics_Data_Connector.html)

Une nouvelle section Tutoriels a été ajoutée, avec des liens vers des guides pas à pas et des vidéos pratiques. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Tutorials.html)

Une nouvelle note technique sur le protocole et les paramètres du connecteur SMS a été créée. [En savoir plus](https://helpx.adobe.com/campaign/kb/sms-connector-protocol-and-settings.html)

Le guide de mise en route des bonnes pratiques de livraison a été mis à jour. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliveryBestPractices.html)

La configuration du compte Microsoft Dynamics 365 avec déploiement de l&#39;API Web a été mise à jour. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_CRM_Connectors.html#Example_for_Microsoft_Dynamics)

La procédure d’installation d’Adobe Campaign Classic sur une plateforme Windows a été mise à jour. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/INS_Installing_Campaign_in_Windows__Installing_the_server.html)

La période de partage d’audience entre Adobe Experience Cloud et Campaign Classic a été détaillée. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Importing_and_exporting_audiences.html)

L’article de la base de connaissances complet pour la liste Campaign Classic a été mis à jour. [En savoir plus](https://helpx.adobe.com/campaign/kb/article-list.html)

Une nouvelle note technique sur l’amélioration des performances et les meilleures pratiques est disponible en direct. [En savoir plus](https://helpx.adobe.com/campaign/kb/best-practices-for-performance-improvement.html)

Un exemple de test A/B a été mis à jour. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_A-B_testing.html)

La page de questions fréquentes/FAQ de Campaign Classic a été mise à jour. [En savoir plus](../../platform/using/common-questions.md)

## 18.4 - 24/04/2018{#release-18-4}

**Nouvelles fonctionnalités de cette version**

Règlement général sur la protection des données de l&#39;UE (RGPD) – [En savoir plus](https://helpx.adobe.com/campaign/kb/acc-privacy.html)

Profils actifs - [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/PTF_Profile_management_About_profiles.html#Active_profiles)

Amélioration du connecteur Push Android - [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_push_notifications_Setting_up_mobile_app_channel.html#Android_connectors)

**Autres mises à jour de la documentation accompagnant cette version**

Les notes de mise à jour ont été améliorées pour une meilleure expérience utilisateur et incluent désormais tous les correctifs liés aux demandes des clients.  [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/RN.html)

Une nouvelle page a été ajoutée avec les questions les plus courantes sur Campaign Classic. [En savoir plus](../../platform/using/common-questions.md)

La liste des messages d&#39;erreur a été mise à jour. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

La note technique Triggers Marketing Cloud a été mise à jour. [En savoir plus](https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html)

Une note technique a été ajoutée sur la manière d’installer et de déployer le package Privacy (GDPR) sur les versions héritées de Campaign Classic. [En savoir plus](https://helpx.adobe.com/campaign/kb/how-to-install-gdpr-package-on-legacy-versions.html)

Une note technique sur le nouveau mécanisme de génération automatique de séquence a été ajoutée. [En savoir plus](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html)

La documentation JSAPI a été mise à jour. [En savoir plus](https://support.neolane.net/webApp/extranetLogin)

Mise à jour de la matrice de comptabilité. [En savoir plus](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

Une nouvelle page répertoriant les fonctionnalités et versions obsolètes est désormais disponible. [En savoir plus](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)

Certaines limites connues et pratiques exemplaires concernant le SGBDR ont été ajoutées. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/INS_Prerequisites_and_recommendations__Database.html)

Découvrez les meilleures pratiques concernant l’utilisation du protocole SFTP. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/PTF_Importing_and_exporting_data_SFTP_server_usage.html)

La liste des processus techniques a été mise à jour. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/WKF_Technical_workflows_About_technical_workflows.html)

La liste des articles de la base de connaissances (précédemment connue sous le nom de &quot;technotes&quot;) est maintenant disponible ici. [En savoir plus](https://helpx.adobe.com/campaign/kb/article-list.html)

Les vidéos [](https://docs.campaign.adobe.com/doc/AC/en/Videos/Videos.html) Comment faire ont été mises à jour.

La documentation LINE a été mise à jour après l&#39;amortissement du package LINE. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_messages_on_mobiles_LINE_channel.html)

Mise à jour de la documentation sur le calcul des indicateurs de rapport. [En savoir plus](../../reporting/using/indicator-calculation.md)

Ajout d’informations sur l’alignement du fichier Timezone avec Oracle. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/MIG_Configuration_General_configurations.html#Oracle)

Ajout d’une nouvelle section &quot;Suivi des livraisons&quot; contenant des informations à jour sur les échecs de livraison et la gestion des mises en quarantaine. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Monitoring_a_delivery.html)

Réorganisation de la section &quot;Blocs de personnalisation&quot; avec de nouvelles informations sur les blocs de personnalisation prêts à l’emploi.
[En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_Personalizing_deliveries_Personalization_blocks.html)

Réorganisation de la section Archivage des courriers électroniques avec de nouvelles informations sur la configuration des ```config-<instance name>.xml``` fichiers. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Activating_email_archiving__on_premise_)

Mise à jour des informations sur le processus technique du Centre de messages (Control). [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/WKF_Technical_workflows_Message_Center__Control_.html)

Ajout d’informations sur les limites de débit lors de la configuration d’un relais SMTP. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html#Personalizing_delivery_parameters)

## 17.12 - 14/12/2017{#release-doc-14-12-2017}

La documentation [d’](https://helpx.adobe.com/support/campaign/classic.html) Adobe Campaign Classic a été réorganisée afin d’en améliorer l’utilisation.

Une nouvelle section Didacticiels a été ajoutée afin de faciliter l’accès aux principales fonctionnalités de la campagne et d’aider à la documentation, aux instructions, aux échantillons et aux vidéos. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Tutorials.html)

Une nouvelle section a été ajoutée pour vous aider à surveiller votre état de remise, mais aussi les erreurs possibles et apprendre à les corriger. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Monitoring_a_delivery.html)

La liste des messages d&#39;erreur a été mise à jour. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

La note technique Triggers Marketing Cloud a été mise à jour. [En savoir plus](https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html)

Le guide de migration de Campaign Classic a été ajouté à la collection. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/MIG_Migration_overview_About_migration.html)

La matrice de compatibilité des campagnes a été mise à jour. [En savoir plus](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

Le cas échéant, les instructions de configuration et d’installation mentionnent maintenant le modèle d’hébergement auquel elles s’appliquent. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html)

Nouvel article de la base de connaissances pour mettre en évidence la configuration et les différences de fonctionnalités entre les déploiements sur site, hybride et de services gérés. [En savoir plus](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html)

Ajout d’instructions sur la manière d’installer un pack standard. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/INS_Initial_configuration_Installing_packages.html)

Ajout d’informations sur la configuration de l’intégration avec Audience Manager ou le service principal Personnes. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Configuring_shared_audiences_integration_in_Adobe_Campaign.html)

Mise à jour de la documentation d&#39;installation pour indiquer que pgcrypto est désormais requis pour l&#39;installation de Campaign en cas d&#39;utilisation de PostSQL. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/INS_Installing_Campaign_in_Linux__Prerequisites.html#Database_access_layers)

## 17.9 - 25/09/2017{#release-17-9}

**Nouvelles fonctionnalités de cette version**

Améliorations apportées au connecteur ACS

Connecteur SAP HANA - [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Accessing_an_external_database.html#SAP_HANA)

Hadoop Connector via HiveSQL - [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Accessing_an_external_database.html#Hadoop)

Canal LIGNE : Améliorations de la messagerie - [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_messages_on_mobiles_LINE_channel.html)

**Autres mises à jour de la documentation accompagnant cette version**

De nouveaux exemples de requête ont été ajoutés. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Designing_queries.html#Filtering_duplicated_recipients)

Le guide des bonnes pratiques de livraison a été mis à jour. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliveryBestPractices.html)

L’exemple de test A/B a été mis à jour avec des instructions manquantes. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_A-B_testing.html)

Des vidéos pratiques ont été mises à jour. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/Videos/Videos.html)

Mise à jour de la section d’archivage des e-mails. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html)

Clarifier l’utilisation du planificateur dans un processus. [En savoir plus](../../workflow/using/scheduler.md)

Il est recommandé d’ajouter la procédure Pause au processus. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Executing_a_workflow.html)

Nouvelle procédure concernant le prétraitement du fichier lors de l’importation et du post-traitement lors de l’exportation de données dans un flux de travail. Lis [ici](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Importing_data.html).

Le mécanisme de quarantaine de la documentation des messages SMS a été mis à jour pour refléter les spécificités de la gestion des erreurs pour le connecteur SMPP générique étendu. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_quarantine_management.html#SMS_quarantines).

La documentation sur les canaux d’applications mobiles a été améliorée grâce à une procédure détaillée pour l’envoi de notifications enrichies sur Android. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_push_notifications_Setting_up_mobile_app_channel.html#Rich_notifications).

La documentation du rendu de la boîte de réception a été mise à jour. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_Inbox_rendering.html).

La documentation relative à la configuration du suivi Web a été améliorée par un exemple et des notes mis à jour. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/CFG_Setting_up_web_tracking_Additional_parameters.html#Redirection_server_configuration).

La documentation du canal SMS a été mise à jour et quelques éclaircissements ont été ajoutés à la section de réponse automatique s&#39;appliquant au connecteur SMPP générique étendu. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_messages_on_mobiles_SMS_channel.html#Creating_an_SMPP_external_account).

La documentation de Social Marketing a été mise à jour. [En savoir plus](../../social/using/about-social-marketing.md).

Une nouvelle note technique sur le réchauffement de la propriété intellectuelle a été ajoutée. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/Technotes/AdobeCampaign_Deliverability_IP_Warming_overview.pdf).

Une nouvelle prise en main de la mise à niveau de la version a été ajoutée. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html).

## May 2017{#release-doc-30-05-2017}

Disponibilité d&#39;un nouveau guide de prise en main : il présente certaines des bonnes pratiques que vous pouvez appliquer pour la diffusion de vos communications avec Adobe Campaign, depuis la création et le ciblage jusqu&#39;à l&#39;envoi et le suivi – [En savoir plus](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliveryBestPractices.html)

Mise à jour du guide de prise en main sur la sécurité. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html)

The [&quot;Archiving emails&quot; documentation&quot;](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html) has been updated with the [&quot;Email BCC&quot;](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Configuring_the_BCC_email_address__on_premise_) section and the [detailed steps to activate the feature](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Sending_messages.html#Archiving_emails).

Ajout et mise à jour de certaines vidéos. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/Videos/Videos.html)

Découvrez comment envoyer une diffusion à des destinataires chargés depuis un fichier externe sans mettre à jour la base de données. [En savoir plus](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients)

Mise à jour de l&#39;exemple sur le double opt-in. [En savoir plus](../../web/using/use-cases--web-forms.md)

## March 2017{#release-doc-31-03-2017}

Délivrabilité : mise à jour du [guide de prise en main](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html). La documentation sur la délivrabilité contient maintenant une [présentation](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_About_deliverability.html) plus détaillée et une description [du processus et des principales étapes d&#39;implémentation](../../delivery/using/deliverability-key-points.md).

Déplacement et enrichissement de la section &quot;Envoyer par vagues&quot; avec des exemples, des recommandations et des cas pratiques détaillés.    [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Sending_messages.html#Sending_using_multiple_waves)

Ajout d&#39;un tableau décrivant les erreurs propres aux messages SMS à la section &quot;Gestion des quarantaines&quot;. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_quarantine_management.html#SMS_quarantines)

Workflows : ajout d&#39;un exemple de workflow multicanal. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Action_activities.html#Cross-channel_deliveries)

Marketing Cloud Triggers : ajout d&#39;une technote sur la configuration et l&#39;utilisation du service dans Adobe Campaign. [En savoir plus](https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html)

Réorganisation et enrichissement du guide Workflow. Trouvez facilement des informations sur la [création](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Building_a_workflow.html) et l&#39;[exécution](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Executing_a_workflow.html) d&#39;un workflow. Découvrez comment [cibler](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Targeting_data.html) et [gérer](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Targeting_data.html#Data_Management) vos données, [importer](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Importing_data.html)[](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_How_to_use_workflow_data.html#Updating_the_database)[ des données et utiliser des données de workflow pour mettre à jour la base de données ou envoyer des diffusions](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_How_to_use_workflow_data.html#Delivering_via_a_workflow).

Disponibilité d&#39;un exemple de création de [workflow d&#39;import](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_How_to_use_workflow_data.html#Delivering_via_a_workflow) suite aux [bonnes pratiques d&#39;import.
](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Importing_data.html#Import_best_practices)
Mise à jour du guide d&#39;installation pour cette nouvelle version. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/INS_Architecture_and_hosting_models_General_architecture.html)

Mise à jour de la matrice de comptabilité. [En savoir plus](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

L&#39;inclusion de coupons à vos envois d&#39;emails offrent une valeur ajoutée aux destinataires. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/DLV_Personalizing_deliveries_Personalized_coupons.html)

## Adobe Campaign v7 - 16/03/2017{#release-17-2}

**Nouvelles fonctionnalités de cette version**

ACS Connector

API Web pour Microsoft Dynamics - [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_CRM_Connectors.html#Example_for_Microsoft_Dynamics)

Archivage des courriers électroniques méthode BCC - [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Updated_email_archiving_system__BCC_)

Connecteur Amazon Simple Storage Service (S3) – [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Event_activities.html#File_transfer)

