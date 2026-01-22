---
product: campaign
title: Partage d'audiences avec Adobe Experience Cloud
description: Partage d'audiences avec Adobe Experience Cloud
feature: Audiences
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: 1c90e913-3375-476c-ab60-89f20239eb0d
source-git-commit: b11185da8236d6100d98eabcc9dc1cf2cffa70af
workflow-type: ht
source-wordcount: '245'
ht-degree: 100%

---

# Partage d&#39;audiences avec Adobe Experience Cloud {#sharing-audiences-with-adobe-experience-cloud}


>[!CAUTION]
>
>Pour partager des audiences avec les solutions Adobe Experience Cloud, vous devez implémenter Adobe IDentity Management System. [En savoir plus sur l’IMS](../../integrations/using/about-adobe-id.md).

Avec Adobe Campaign, vous pouvez partager des audiences et des segments avec les services Adobe Experience Cloud. Deux options sont disponibles :

1. Envoyer des données de segment Adobe Experience Platform à Adobe Campaign. Pour mettre en œuvre cette intégration, vous devez connecter à Campaign votre plateforme de données clientes en temps réel (RTCDP). [En savoir plus dans cette section](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html?lang=fr){target="_blank"}.

1. Intégrez **Adobe Campaign** aux **Audiences Experience Cloud** ou **Adobe Audience Manager**. Vous pourrez alors :

   * importer dans Adobe Campaign des audiences/segments provenant de différentes solutions d’Adobe Experience Cloud. L’import d’audiences peut être réalisé depuis les listes dans Adobe Campaign ;

   * exporter des listes sous la forme d’audiences partagées Adobe Experience Cloud. Ces audiences peuvent être exploitées dans les différentes solutions d’Adobe Experience Cloud que vous utilisez. L’export d’audiences peut être réalisé à la suite d’un ciblage dans un workflow, à l’aide d’une activité dédiée **[!UICONTROL Mise à jour d’audience partagée]**.

L’intégration prend en charge deux types d’identifiants Adobe Experience Cloud :

* **Identifiant visiteur** : ce type d’identifiant permet de réconcilier des visiteurs Adobe Experience Cloud avec des destinataires Adobe Campaign.
* **Identifiant déclaré** : ce type d’identifiant permet de réconcilier tous les types de données avec les éléments de la base de données Adobe Campaign. Dans Adobe Campaign, il est représenté sous la forme d’une clé de réconciliation prédéfinie.

  >[!NOTE]
  >
  > Désormais, la source de données des ID déclarés peut également être utilisée avec l’intégration d’Experience Cloud Assets.
  >
