---
product: campaign
title: Partage d'audiences avec Adobe Experience Cloud
description: Partage d'audiences avec Adobe Experience Cloud
feature: Audiences, People Core Service Integration
badge-v8: label="S’applique également à la version 8" type="Positive" tooltip="S’applique également à Campaign v8"
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: 1c90e913-3375-476c-ab60-89f20239eb0d
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 90%

---

# Partage d&#39;audiences avec Adobe Experience Cloud{#sharing-audiences-with-adobe-experience-cloud}



>[!CAUTION]
>
>Pour partager des audiences avec les solutions Adobe Experience Cloud, vous devez implémenter Adobe IDentity Management System. [En savoir plus sur l’IMS](../../integrations/using/about-adobe-id.md).

Avec Adobe Campaign, vous pouvez partager des audiences et des segments avec les solutions Adobe Experience Cloud et les core services. Deux options sont disponibles :

1. Envoyer des données de segment Adobe Experience Platform à Adobe Campaign. Pour mettre en œuvre cette intégration, vous devez connecter à Campaign votre plateforme de données clientes en temps réel (RTCDP). [En savoir plus dans cette section](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html?lang=fr).

1. Intégrer **Adobe Campaign** à **People core service** (aussi appelé **Profiles &amp; Audiences core service**) ou Adobe Audience Manager. Vous pourrez alors :

   * importer dans Adobe Campaign des audiences/segments provenant de différentes solutions d&#39;Adobe Experience Cloud. L&#39;import d&#39;audiences peut être réalisé depuis les listes dans Adobe Campaign.

   * Exportez des listes sous la forme d’audiences partagées Adobe Experience Cloud. Ces audiences peuvent être utilisées dans les différentes solutions Adobe Experience Cloud que vous utilisez. L&#39;export d&#39;audiences peut être réalisé à la suite d&#39;un ciblage dans un workflow, à l&#39;aide d&#39;une activité dédiée **[!UICONTROL Mise à jour d&#39;audience partagée]**.

L’intégration prend en charge deux types d’identifiants Adobe Experience Cloud :

* **Identifiant visiteur** : ce type d’identifiant permet de réconcilier des visiteurs Adobe Experience Cloud avec des destinataires Adobe Campaign.
* **Identifiant déclaré** : ce type d’identifiant permet de réconcilier tous les types de données avec les éléments de la base de données Adobe Campaign. Dans Adobe Campaign, il est représenté sous la forme d’une clé de réconciliation prédéfinie.

  >[!NOTE]
  >
  > Désormais, la source de données des ID déclarés peut également être utilisée avec l’intégration People Core Service.
  >
  >Si vous utilisez l’intégration de People Core Service et que vous souhaitez ajouter l’intégration d’Audience Manager, vous aurez besoin de l’aide d’un consultant Adobe Audience Manager. Ce dernier vous aidera à éviter de perdre toutes les synchronisations d’ID collectées lors de la transition vers l’utilisation de cette source de données d’ID déclarés dans un contexte Adobe Audience Manager.
