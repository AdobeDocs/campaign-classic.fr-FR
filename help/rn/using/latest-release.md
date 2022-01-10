---
product: campaign
title: Dernière version
description: Latest Campaign Classic v7 Release Notes
feature: Overview
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 630a62c5e5c9782c5c55fdebd651493a2d68fc54
workflow-type: tm+mt
source-wordcount: '1058'
ht-degree: 16%

---

# Dernière version{#latest-release}

![](../../assets/v7-only.svg)

**** Every new build comes with a status which is materialized by a color. [](rn-overview.md)

## ![](assets/do-not-localize/green_2.png) Version 7.2.1 - Build 9346 {#release-7-2-1}

__

**Amélioration de la sécurité**

Several security improvements have been made to FDA accounts:

* ODBC drivers are now directly installed with Adobe Campaign Third Parties. Manual steps are no longer required to install these drivers.
* When configuring your FDA external account, you can now login to your Snowflake account using Key pair authentication for enhanced authentication security. [En savoir plus](../../installation/using/configure-fda-snowflake.md)
* When configuring your FDA external account, you can now login to your Azure Synapse Analytics account using the System-assigned managed identity. [En savoir plus](../../installation/using/configure-fda-synapse.md#azure-external)
* All references to the log4j library have been removed from Campaign to ensure optimal security.

**Améliorations**

* Microsoft Dynamics CRM 365 Connector

   Critical fixes have been applied regarding the Microsoft Dynamics Connector web API:

   * Fixed an issue, during an import triggered by a workflow, which caused the null values of string-type fields to be saved as Null instead of empty values.
   * Fixed an issue which led to the following error for data import or export using web API calls: &quot;Invalid URI: The URI scheme is too long&quot;.
   * Fixed various issues when importing, from Microsoft Dynamics 365, data containing lookup fields.

* Google BigQuery FDA Connector

   * Google BigQuery FDA Connector is now available for Hosted deployments. [En savoir plus](../../installation/using/configure-fda-google-big-query.md)
   * Added support to enable connections to a proxy server for Google BigQuery FDA connector. Required proxy options can be set through the Options field in the external account configuration. [En savoir plus](../../installation/using/configure-fda-google-big-query.md#google-external)

**Autres changements**

* Following their deprecation, Microsoft CRM, Salesforce, Oracle CRM On Demand action activities have been removed from the interface. To configure the data synchronization between Adobe Campaign and a CRM system, you can use the CRM connector activity. [En savoir plus](../../workflow/using/crm-connector.md)
* **** Ce champ est calculé et doit être utilisé pour les applications web. This applies when the Line channel is configured on the mid-sourcing instance.
* ****
* ******** You will not be able to restart it afterwards (NEO-29661). [En savoir plus](../../workflow/using/advanced-parameters.md#in-case-of-errors)
* A dedicated sequence is now used to generate the primary keys for the nmsGroup table, which is used to create statistical groups of recipients. Previously, the xtknewId sequence was used. (NEO-30832)
* Added support for batch update operations using the CRM connector activity.
* Improved performance for transactional messaging processing time. (NEO-40370)

**Correctifs**

* ******** This occurred when using an auto proxy configuration. (NEO-33260)
* Fixed an issue which could prevent you from uploading a file on a Debian 10 server (HTTPS) in synchronous mode.
* `nmsDeliveryLogStats` (NEO-31034)
* Fixed an issue which prevented you from sending mobile app notifications on iOS while using token-based authentication (NEO-38640).
* Fixed an issue which could display script error messages when trying to create and configure reports (NEO-38393).
* Fixed an issue which could cause the tracking workflow to fail on Oracle due to high volumes of delivery indicators being updated simultaneously (NEO-39653).
* Fixed an issue which could prevent a delivery from being sent due to an error occurring while executing a control typology (NEO-39833).
* Fixed an issue in landing pages which could prevent special characters from displaying correctly in the HTML pages of online survey responses (NEO-39438).
* Fixed an issue which could prevent the Campaign Classic console from working when right-clicking on any of the folders from the Explorer tab (NEO-38884).
* Fixed an error when using a previously created delivery template linked to a Web Analytics account in a new delivery where the Web Analytics configuration was missing. (NEO-28666)
* Correction dʼun problème en raison duquel les diffusions mobiles jointes à un workflow ne pouvaient pas être prévisualisées.
* Fixed an error that prevented personalized tracking URLs from being redirected when the URL signature mechanism for tracking links was enabled.
* Fixed an issue that could cause postupgrade failures due to an index management issue.
* ********
* Fixed an issue which could prevent you from login to the console due to a proxy configuration issue. (NEO-38388)
* Correction dʼun problème de régression qui empêchait la fonctionnalité **Purger le dossier** de fonctionner correctement. (NEO-37459)
* Fixed an issue which led to a bad request error when using xml-data fields with the Microsoft Dynamics CRM account if the referenced xml contained double quotes.
* Correction dʼun problème en raison duquel les problèmes de délai dʼexpiration du réseau étaient incorrectement enregistrés en tant que problèmes dʼinterruption de script au lieu dʼerreurs de réseau. Ce problème se produisait dans le cas de requêtes HTTP incluses dans les activités JavaScript. (NEO-38079)
* Correction dʼun problème en raison duquel des résultats incorrects étaient renvoyés lors de lʼexécution des fonctions Amazon Redshift HoursDiff et MinutesDiff lors de la tentative dʼextraction du composant dʼheure.(NEO-31673)
* **** (NEO-28900)
* `&amp;` (NEO-28621)
* Fixed an issue which created a new external account everytime a user created a new campaign workflow and a delivery activity linked to a Web Analytics account. This was caused by a missing ID in the webAnalyticsAccount delivery object. (NEO-39691)
* Correction dʼun problème en raison duquel lʼactivité du workflow de **Lecture de liste** ne fonctionnait pas lorsque la liste était identifiée dans la base de données par un identifiant négatif. (NEO-39607)
* **** (NEO-39662)
* Fixed an issue that could prevent you from previewing email deliveries that were attached to a workflow. (NEO-37840)
* Fixed an issue that could cause valid tables that contained list values to be deleted by the database cleanup workflow. (NEO-34911)
* Correction dʼun problème qui entraînait le blocage du workflow de facturation sur les instances marketing.
