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
source-git-commit: 1b76fb1694545f4be02a63e4c670b81db632c5ee
workflow-type: tm+mt
source-wordcount: '3702'
ht-degree: 98%

---


# Mises à jour de la documentation{#documentation-updates}

Cette page répertorie toutes les nouvelles fonctionnalités et mises à jour de la documentation par mois et par version de Campaign.

Vous pouvez également consulter les [notes de mise à jour d’Adobe Campaign Classic](../../rn/using/latest-release.md) pour accéder à d’autres mises à jour.

## Septembre 2020 {#september-2020}

Une note a été ajoutée pour indiquer que le nombre de profils Principaux est disponible uniquement pour les instances Marketing. [En savoir plus](../../platform/using/about-profiles.md#active-profiles)

Un nouvel exemple d’édition de schéma a été ajouté pour lier un champ à un tableau de référence existant. [En savoir plus](../../configuration/using/examples-of-schemas-edition.md#uc-link)

## Août 2020 {#aug-2020}

Découvrez les bonnes pratiques en matière de conception de diffusion et d’envoi avec Campaign dans une section dédiée. [En savoir plus](../../delivery/using/delivery-best-practices.md)

La landing page des bonnes pratiques en matière de délivrabilité a été améliorée pour faciliter l’accès aux sous-sections. [En savoir plus](../../delivery/using/deliverability-key-points.md)

Des vidéos pratiques sont désormais disponibles concernant les rubriques suivantes :

* [Configuration de la gestion de la fatigue à l’aide de règles de typologie et de filtres prédéfinis](../../campaign/using/about-campaign-typologies.md)

* [Création d’un email dans une campagne](../../campaign/using/marketing-campaign-deliveries.md)

* [Création d’une newsletter multilingue avec du contenu conditionnel](../../delivery/using/conditional-content.md)

* [Configuration et déploiement d’un modèle de diffusion](../../delivery/using/creating-a-delivery-template.md)

* [Activation et utilisation d’AMP pour les emails](../../delivery/using/defining-interactive-content.md)

* [Personnalisation des emails à l’aide de blocs de contenu dynamique](../../delivery/using/personalization-blocks.md)

* [Personnalisation des emails à l’aide de champs de personnalisation](../../delivery/using/personalization-fields.md)

* [Gestion de l’adresse de contrôle et des BAT dans un email](../../delivery/using/steps-defining-the-target-population.md)

* [Configuration d’une diffusion récurrente](../../workflow/using/recurring-delivery.md)

* [Configuration d’une diffusion au fil de l’eau](../../workflow/using/continuous-delivery.md)

Des informations ont été ajoutées concernant les vérifications et actions à effectuer lors de l’obtention de l&#39;erreur « Impossible de résoudre le nom d’hôte » après la connexion à un serveur FTP. [En savoir plus](../../platform/using/sftp-server-usage.md)

De nouveaux cas pratiques ont été référencés dans la liste des [cas pratiques de workflows](../../workflow/using/about-workflow-use-cases.md) :

* Automatisation de la création, de l’édition et de la publication de contenu
* Configuration d’un processus de validation de destinataire avant l’envoi d’une diffusion
* Appeler une variable d&#39;instance dans une requête
* Application d’un pourcentage fractionné à une population

La section **[!UICONTROL Rendez-vous]** a été enrichie d’informations supplémentaires sur son utilisation, ainsi que d’une note concernant l’utilisation des variables. [En savoir plus](../../workflow/using/and-join.md)

## Juillet 2020 {#july-2020}

Un cas pratique sur la mise à jour automatique d’une liste à l’aide d’une requête incrémentale a été ajouté aux cas pratiques de workflow. [En savoir plus](../../workflow/using/about-workflow-use-cases.md)

Les [Notes de mise à jour](../../rn/using/latest-release.md) ont été réorganisées : une [page d’aperçu](../../rn/using/latest-release.md) a été ajoutée avec des informations sur les statuts de build, le processus de mise à niveau, les recommandations et des liens importants. Une page dédiée aux [versions Gold Standard](../../rn/using/gold-standard.md) a également été ajoutée et la [matrice de compatibilité](../../rn/using/compatibility-matrix.md) a été intégrée.

Une nouvelle section a été ajoutée avec des directives relatives à la surveillance Campaign Classic. [En savoir plus](../../production/using/monitoring-guidelines.md)

La section Confidentialité et consentement a été améliorée avec des informations plus détaillées et des liens utiles. [En savoir plus](../../platform/using/privacy-and-recommendations.md).

La page Gestion de la confidentialité dans Campaign Classic a été mise à jour avec des informations sur le champ « réglementation » qui est maintenant disponible lors de l&#39;utilisation de l’API permettant de configurer le processus de demande automatique d’accès à des informations personnelles. [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/acc-privacy.html#ManagingPrivacyRequests)

La page de présentation de la gestion des données personnelles a été mise à jour pour inclure des informations sur la loi thaïlandaise sur la protection des données personnelles (PDPA) et la loi brésilienne sur la protection des données (Lei Geral de Proteção de Dados - LGPD) – [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/campaign-privacy-overview.html#whatisgdpr)

Des informations ont été ajoutées sur les logs de sous-workflows et sur le comportement en cas d’erreur. [En savoir plus](../../workflow/using/sub-workflow.md)

Des bonnes pratiques ont été ajoutées dans la section sur l’activité **[!UICONTROL Planificateur]**. [En savoir plus](../../workflow/using/scheduler.md)

## Juin 2020 {#june-2020}

La section Suppression d’une adresse mise en quarantaine a été mise à jour. Cela inclut la clarification des cas dans lesquels les adresses sont automatiquement supprimées de la liste de quarantaine. [En savoir plus](../../delivery/using/understanding-quarantine-management.md#removing-a-quarantined-address)

Des cas d’utilisation ont été ajoutés pour [crypter](../../workflow/using/how-to-use-workflow-data.md#use-case-gpg-encrypt) et [décrypter](../../workflow/using/importing-data.md#use-case-gpg-decrypt) des données à l’aide du Panneau de contrôle et des workflows Campaign.

Les termes « whiteliste » et « blackliste » ont été supprimés de la documentation Adobe Campaign. Certaines occurrences de ces termes peuvent toujours apparaître dans l’interface utilisateur du produit, les noms d’option et le code interne, mais elles seront remplacées dans les prochaines versions de Campaign par « liste bloquée » et « liste autorisée ».

La page sur l&#39;intégration des Triggers Experience Cloud et Adobe Campaign Classic a été déplacée [ici](../../integrations/using/about-triggers.md).

## july 2020 {#release-20-2}

**Nouvelles fonctionnalités incluses dans la version 20.2**

Prise en charge des émoticônes - [En savoir plus](../../delivery/using/customizing-emoticon-list.md)

Connecteur FDA Azure Synapse - [En savoir plus](../../platform/using/specific-configuration-database.md#configure-access-to-azure-synapse)

Loi sur la protection de la vie privée en Thaïlande et au Brésil - [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/acc-privacy.html#ManagingPrivacyRequests)

**Autres mises à jour de la documentation accompagnant cette version**

La nouvelle option qui permet d’annuler la publication d’un modèle de message transactionnel
est présentée dans [cette section](../../message-center/using/template-unpublication.md).

Les nouvelles options destinées à définir des limites lors de l’envoi d’emails incluant des images téléchargées à partir d’une URL personnalisée et des pièces jointes ont été ajoutées à la liste des options de Campaign Classic. [En savoir plus](../../installation/using/configuring-campaign-options.md#delivery)

La nouvelle option **Préparer les fragments de diffusion dans la base de données** est documentée dans [cette section](../../delivery/using/steps-validating-the-delivery.md#improving-delivery-analysis).

La section Valider la diffusion a été clarifiée et mise à jour. [En savoir plus](../../delivery/using/steps-validating-the-delivery.md)

Les paramètres liés au nouveau mécanisme de signature des liens de tracking ont été ajoutés à la section [Fichier de configuration du serveur](../../installation/using/the-server-configuration-file.md).

Mise à jour de la matrice de compatibilité. [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix.html)

La section Workflow de nettoyage a été mise à jour. [En savoir plus](../../production/using/database-cleanup-workflow.md)

Les points d’entrée réseau de Campaign ont été déplacés vers cette [section](../../installation/using/campaign-network-endpoints.md).

La section d’installation de Spam Assassin a été mise à jour avec le nouveau nom du fichier d’installation. [En savoir plus](../../installation/using/configuring-spamassassin.md#installing-spamassassin)

La section relative à la duplication des environnements a été mise à jour. [En savoir plus](../../production/using/duplicating-environments.md#step-2---export-the-target-environment-configuration--dev-)

## Mai 2020 {#may-2020}

La section Supervision de la délivrabilité a été déplacée et améliorée. [En savoir plus](../../delivery/using/monitoring-deliverability.md)

La section Résolution des problèmes de délivrabilité a été déplacée et améliorée. [En savoir plus](../../delivery/using/deliverability-faq.md)

Les directives relatives à la délivrabilité lors du démarrage d’une nouvelle section de plate-forme ont été améliorées. [En savoir plus](../../delivery/using/starting-new-platform.md)

La section Envoi d’emails transactionnels avec des pièces jointes a été déplacée et mise à jour. [En savoir plus](../../message-center/using/transactional-email-with-attachments.md)

La section Bonnes pratiques relatives aux packages de données a été déplacée et mise à jour. [En savoir plus](../../platform/using/working-with-data-packages.md#data-package-best-practices)

## Avril 2020 {#april-2020}

La table des droits FDA a été déplacée vers la documentation intitulée Accès à une base externe (FDA). [En savoir plus](../../platform/using/remote-database-access-rights.md)

Le FAQ a été mis à jour avec des conseils relatifs au vidage du cache local (soft et hard). [En savoir plus](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear)

Les bonnes pratiques relatives au modèle de données ont été améliorées avec des informations supplémentaires concernant les index. [En savoir plus](../../configuration/using/data-model-best-practices.md#indexes)

La section décrivant le modèle de données intégré d’Adobe Campaign a été mise à jour en détaillant davantage chaque tableau. [En savoir plus](../../configuration/using/data-model-description.md)

Les cas d’utilisation des workflows ont été actualisés et réorganisés en sections thématiques. [En savoir plus](../../workflow/using/about-workflow-use-cases.md)

Les sections [Qualification des emails bounce](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification)et [Règles de gestion des emails](../../delivery/using/understanding-delivery-failures.md#email-management-rules) ont été mises à jour pour les améliorer.

L’article sur le MTA amélioré d’Adobe Campaign a été mis à jour. Il ne s’applique désormais qu’à Campaign Classic. [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/acc-campaign-enhanced-mta.html)

## Mars 2020 {#march-2020}

Les bonnes pratiques relatives au modèle de données ont été mises à jour avec de nouvelles sections, notamment [Séquences](../../configuration/using/data-model-best-practices.md#sequences), [Performances](../../configuration/using/data-model-best-practices.md#performance) et [Tables volumineuses](../../configuration/using/data-model-best-practices.md#large-tables). [En savoir plus](../../configuration/using/data-model-best-practices.md)

Une nouvelle section relative au modèle de données intégré d’Adobe Campaign et aux interactions des tables d’usine est maintenant disponible. [En savoir plus](../../configuration/using/data-model-description.md)

Des liens essentiels supplémentaires ont été ajoutés à la page d’accueil de la documentation. [En savoir plus](../../campaign-classic-home.md)

Un cas pratique a été ajouté concernant l’intégration d’une offre dynamique d’Adobe Target dans un email d’Adobe Campaign. [En savoir plus](../../integrations/using/inserting-a-dynamic-image.md)

Une nouvelle section relative aux différentes langues disponibles dans Adobe Campaign est maintenant disponible. [En savoir plus](../../platform/using/adobe-campaign-workspace.md#languages)

Les directives relatives à la gestion des accès ont été mises à jour pour détailler davantage les droits nommés. [En savoir plus](../../platform/using/access-management.md#named-rights)

## Février 2020 {#february-2020}

Une nouvelle section contenant une présentation des bonnes pratiques et des recommandations essentielles pour la conception du modèle de données Adobe Campaign est maintenant disponible. [En savoir plus](../../configuration/using/data-model-best-practices.md)

Une nouvelle section est disponible à propos du paramétrage technique des emails. [En savoir plus](../../installation/using/email-deliverability.md)

Le document FAQ relatif à la délivrabilité a été mis à jour en détaillant davantage le message d’erreur « quotas atteints ». [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/acc-deliverability-faq.html#FAQ)

AMP for Email est désormais pris en charge par les nouveaux fournisseurs de messagerie : la documentation correspondante a été mise à jour. [En savoir plus](../../delivery/using/defining-interactive-content.md)

La section relative à l’archivage des emails a été améliorée. [En savoir plus](../../installation/using/email-archiving.md#recommendations-and-limitations)

## Janvier 2020 {#release-20-1}

**Nouvelles fonctionnalités incluses dans la version 20.1**

Connecteur FDA Snowflake - [En savoir plus](../../platform/using/specific-configuration-database.md#configure-access-to-snowflake)

Améliorations apportées au connecteur FDA Hadoop - [En savoir plus](../../platform/using/specific-configuration-database.md#configure-access-to-hadoop-3)

**Autres mises à jour de la documentation accompagnant cette version**

Les guides [d’installation](../../installation/using/before-reading.md), de [production](../../production/using/foreword.md) et de [configuration](../../configuration/using/additional-parameters.md) ont été mis à jour avec la nouvelle unité systemd utilisée par le démarrage du service nlserver. Vous pouvez encore utiliser /etc/init.d/nlserver6, mais Adobe recommande maintenant d’appliquer la commande systemctl pour interagir avec le service nlserver.

Le guide d’installation a été mis à jour et synchronisé avec la dernière version de la matrice de compatibilité. Les nouveaux systèmes pris en charge ont été ajoutés. Les systèmes obsolètes et non pris en charge ont été supprimés. [En savoir plus](../../installation/using/before-reading.md)

La matrice de compatibilité a été mise à jour en y intégrant les connecteurs FDA Hadoop 3.0 et Snowflake. [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix.html)

Une bonne pratique concernant l’affinité IP a été ajoutée au guide d’installation. [En savoir plus](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

La section Workflow de nettoyage de la base a été mise à jour. Les valeurs numériques de lot indiquées correspondent désormais à la mise en œuvre du code. [En savoir plus](../../production/using/database-cleanup-workflow.md)

Une limitation de FDA via HTTP a été ajoutée au guide de messagerie transactionnelle. [En savoir plus](../../production/using/database-cleanup-workflow.md)

Des informations ont été ajoutées concernant la nouvelle option qui permet de définir un délai d’expiration pour les activités de workflow **[!UICONTROL Code JavaScript]** et **[!UICONTROL Code Advanced JavaScript]**. [En savoir plus](../../workflow/using/sql-code-and-javascript-code.md)

Des informations ont été ajoutées concernant la nouvelle vue **[!UICONTROL Démarrage en attente]** disponible dans le nœud **[!UICONTROL Administration]** > **[!UICONTROL Suivi]** > **[!UICONTROL Statut des workflows]**. [En savoir plus](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

Le guide [Envoi de notifications push](../../delivery/using/about-mobile-app-channel.md) a été déplacé, réorganisé et amélioré avec des informations plus précises.

Le nouveau paramètre de configuration du rapport des URL a été documenté [ici](../../reporting/using/properties-of-the-report.md#defining-additional-settings).

La page **Matrice des fonctionnalités On-premise et hébergées de Campaign Classic** a été mise à jour en indiquant les nouveaux connecteurs FDA. [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/acc-on-prem-vs-hosted.html)

La page **Matrice des fonctionnalités de Campaign Classic** a été mise à jour. [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix.html)

Le nouveau workflow **[!UICONTROL Nettoyage de la table Nmsaddress]** a été documenté [ici](../../production/using/database-cleanup-workflow.md#cleanup-of-nmsaddress).

Une limitation a été ajoutée pour l’utilisation d’une activité de requête dans un workflow. [En savoir plus](../../workflow/using/query.md).

Une nouvelle section a été ajoutée pour préciser les règles améliorées de validation des adresses email pour placer une adresse en quarantaine en cas d’erreur de type Soft. [En savoir plus](../../delivery/using/understanding-quarantine-management.md#soft-error-management)

Le paramètre du fichier de configuration indiquant si une instance utilise ou non le MTA amélioré est maintenant documenté. [En savoir plus](../../installation/using/the-server-configuration-file.md#mta)

La section Délivrabilité a été déplacée, réorganisée et améliorée, et son contenu mis à jour. [En savoir plus](../../delivery/using/about-deliverability.md)

Une nouvelle section concernant les notions de base des modèles de données d&#39;Adobe Campaign Classic et l&#39;accès à la description de chaque table est désormais disponible. [En savoir plus](../../configuration/using/about-data-model.md)

L&#39;article relatif à l&#39;agent de transfert d&#39;emails (MTA) amélioré d&#39;Adobe Campaign a été mis à jour. Il contient des informations plus détaillées sur l&#39;installation d&#39;un package de typologie spécifique sur les instances qui n&#39;ajoutent pas les en-têtes MTA amélioré nécessaires à chaque message. [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/acc-campaign-enhanced-mta.html#impacts)

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

**Nouvelles fonctionnalités incluses dans la version 19.2**

California Consumer Privacy Act (CCPA) – [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/acc-privacy.html)

Contenu interactif avec AMP - [En savoir plus](../../delivery/using/defining-interactive-content.md)

Surveillance en ligne des workflows - [En savoir plus](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

Messagerie SMS sécurisée (TLS) - [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/sms-connector-protocol-and-settings.html)

**Autres mises à jour de la documentation accompagnant cette version**

La documentation relative à l&#39;agent de transfert d&#39;emails (MTA) amélioré d&#39;Adobe Campaign est désormais disponible. [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/acc-campaign-enhanced-mta.html)

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

La documentation du panneau de contrôle a été intégrée au nouvel ensemble de documentation collaborative – [En savoir plus](https://docs.adobe.com/content/help/fr-FR/control-panel/using/control-panel-home.html)

Mise à jour du guide de prise en main des bonnes pratiques de diffusion – [En savoir plus](../../delivery/using/delivery-best-practices.md)

## Octobre 2019 {#october-2019}

Mise à jour de la liste des messages d’erreur de Campaign Standard et Campaign Classic – [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

Amélioration et enrichissement du guide de prise en main du RGPD. Il s’agit maintenant d’une documentation sur la gestion de la vie privée, incluant le RGPD et la CCPA – [En savoir plus](https://helpx.adobe.com/content/help/fr/campaign/kb/campaign-privacy.html)

Une nouvelle page de résolution des problèmes a été ajoutée concernant le suivi dans Campaign Classic. [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/classic-tracking-troubleshooting.html).

Une nouvelle page de bonnes pratiques relatives au connecteur de données d&#39;Adobe Analytics a été ajoutée. [En savoir plus sur le connecteur de données d&#39;Adobe Analytics](../../platform/using/adobe-analytics-data-connector.md)

Le guide de prise en main des bonnes pratiques de diffusion a été déplacé et mis à jour – [En savoir plus](../../delivery/using/delivery-best-practices.md)

Une recommandation a été ajoutée à la documentation du canal SMS. Elle permet d&#39;éviter des problèmes lors de l&#39;utilisation de plusieurs comptes externes en ayant recours au connecteur SMPP générique étendu avec le même compte fournisseur. [En savoir plus](../../delivery/using/sms-channel.md#automatic-reply)

Des informations ont été ajoutées dans la documentation de l&#39;activité Planificateur pour décrire comment empêcher les exécutions simultanées d&#39;un workflow. [En savoir plus](../../workflow/using/scheduler.md)

Les étapes de configuration du rendu du message (Inbox Rendering) pour les installations on-premise ont été ajoutées à la documentation. [En savoir plus](../../delivery/using/inbox-rendering.md#activating-inbox-rendering)

## Septembre 2019 {#september-2019}

Une nouvelle page a été ajoutée au sujet d&#39;instructions générales concernant la maintenance de Campaign Classic. [En savoir plus](../../production/using/monitoring-guidelines.md)

Les informations relatives à la surveillance des workflows ont été centralisées dans une nouvelle section dédiée. [En savoir plus](../../workflow/using/monitoring-workflow-execution.md).

Une nouvelle page a été ajoutée concernant les directives générales relatives au tracking dans Adobe Campaign Standard. [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/acc-tracking.html).

Les bonnes pratiques pour améliorer les performances des workflows et des diffusions ont été mises à jour. [En savoir plus sur les workflows](../../workflow/using/workflow-best-practices.md) et [les diffusions](../../delivery/using/monitoring-a-delivery.md#best-practices-performance).

## Mai 2019 {#release-19-1}

**Nouvelles fonctionnalités incluses dans la version 19.1**

Panneau de contrôle – [En savoir plus](https://docs.adobe.com/content/help/fr-FR/control-panel/using/control-panel-home.html)

Suivi - [En savoir plus](../../production/using/audit-trail.md)

**Autres mises à jour de la documentation accompagnant cette version**

Un nouveau FAQ relatif à l&#39;upgrade de build a été créé. [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/build-upgrade-faq.html)

Mise à jour de la [matrice de compatibilité](https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix.html). La liste des systèmes de base de données pris en charge a été mise à jour, ainsi que les versions Android/iOS et les SDK associés. La [matrice de compatibilité 19.0](https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix-19-0.html) a été archivée.

La page « Fonctionnalités obsolètes et supprimées de Campaign Classic » a été mise à jour. [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/deprecated-and-removed-features.html)

La description du fichier de configuration du serveur a été ajoutée au guide d&#39;installation. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_The_server_configuration_file.html)

Une section décrivant les étapes d&#39;installation et de configuration des modèles hébergés et hybrides a été ajoutée. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/INS_Hybrid_and_Hosted_models_Introduction.html)

Une section décrivant les étapes de désinstallation du serveur Campaign a été ajoutée. [En savoir plus](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_Uninstalling_Campaign.html)

Les guides de prise en main concernant la [sécurité](https://docs.campaign.adobe.com/doc/AC/getting_started/FR/security.html), la [délivrabilité](https://docs.adobe.com/content/help/fr-FR/campaign-classic/using/sending-messages/deliverability-management/about-deliverability.html) et la [confidentialité](https://helpx.adobe.com/fr/campaign/kb/acc-privacy.html) ont été mis à jour.

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

Les vidéos relatives aux fonctionnalités ont été déplacées [ici](https://docs.adobe.com/content/help/fr-FR/campaign-classic-learn/tutorials/overview.html).

Deux notes techniques ont été ajoutées sur [Teradata](https://helpx.adobe.com/fr/campaign/kb/campaign_fda_teradata.html) et [MySQL 5.7](https://helpx.adobe.com/fr/campaign/kb/campaign_fda_mysql.html).
