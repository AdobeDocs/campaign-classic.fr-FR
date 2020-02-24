---
title: À propos du modèle de données Adobe Campaign Classic
description: Ce document décrit les bases du modèle de données Adobe Campaign Classic.
page-status-flag: never-activated
uuid: faddde15-59a1-4d2c-8303-5b3e470a0c51
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5957b39e-c2c6-40a2-b81a-656e9ff7989c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2ce2a1a55e244180a4e62d6f3b5a5ed5bb8aff6e

---


# À propos du modèle de données Campaign Classic{#about-data-model}

Cette section décrit les principes de base du modèle de données Adobe Campaign Classic pour une meilleure compréhension des tableaux intégrés et de leur interaction.

Le modèle de données conceptuel de la base de données Adobe Campaign se compose d’un ensemble de tables intégrées et de leur interaction.

Pour accéder à la description de chaque tableau, accédez à **[!UICONTROL Admin > Configuration > Schémas]** de données, sélectionnez une ressource dans la liste et cliquez sur l’onglet **[!UICONTROL Documentation]** .

![](assets/data-model_documentation-tab.png)

Pour plus d&#39;informations sur la description du modèle de données par défaut de Campaign Classic, reportez-vous à ce [document](https://final-docs.campaign.adobe.com/doc/AC/en/technicalResources/_Datamodel_Description_of_the_main_tables.html).

La structure physique et logique des données véhiculées dans l&#39;application est décrite en XML et respecte une grammaire propre à Adobe Campaign appelée schéma. Pour en savoir plus sur les schémas Adobe Campaign, lisez cette [section](../../configuration/using/about-schema-reference.md).

## Présentation {#data-model-overview}

Adobe Campaign repose sur une base de données relationnelle contenant des tables liées entre elles.

La structure de base du modèle de données Adobe Campaign peut être décrite comme suit.

## Table des destinataires {#recipient-table}

Le modèle de données repose sur un tableau principal qui est par défaut le tableau Destinataire (**NmsRecipient**). Ce tableau permet de stocker tous les profils marketing.

Pour plus d’informations sur le tableau Destinataire, voir cette [section](../../configuration/using/default-recipient-table.md).

## Table de livraison {#delivery-table}

Le modèle de données comprend également une partie dédiée au stockage de toutes les activités marketing. Généralement, il s&#39;agit du tableau Livraison (**NmsDelivery**). Chaque enregistrement de ce tableau représente une action de remise ou un modèle de remise. Il contient tous les paramètres nécessaires pour effectuer des livraisons telles que la cible, le contenu, etc.

## Journaux des tableaux {#log-tables}

Une autre partie du modèle de données permet de stocker temporairement tous les journaux associés à l’exécution des campagnes.

Les journaux de diffusion sont tous des messages envoyés aux destinataires ou aux périphériques sur tous les canaux. Le tableau des journaux de livraison principal (**NmsBroadLog**) contient les journaux de livraison pour tous les destinataires.
La table principale des journaux de suivi (**NmsTrackingLog**) stocke les journaux de suivi pour tous les destinataires. Les journaux de suivi se rapportent aux réactions des destinataires, telles que les ouvertures de courrier électronique et les clics. Chaque réaction correspond à un journal de suivi.
Les journaux de remise et de suivi sont supprimés après une certaine période, spécifiée dans Adobe Campaign et modifiable. Il est donc vivement recommandé d’exporter les journaux régulièrement.

## Tableaux techniques {#technical-tables}

Enfin, une partie du modèle de données est constituée de données techniques utilisées pour le processus applicatif, y compris les opérateurs et les droits d’utilisateur (**NmsGroup**), les dossiers (**XtkFolder**).