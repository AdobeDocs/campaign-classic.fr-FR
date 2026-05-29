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
TQID: https://experienceleague.adobe.com/MGzMyGtmzaVGZy6oWHcirPPdSSpu9YYcuR30KIVZ9bc
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2: id: cbcf4d90-26be-46e2-b16a-aebc529dc41eid: df0d6518-6f49-46e2-b46e-3bcc513f553fid: eb007b6d-6e57-46ab-9485-3f24d6102304id: b1fd1501-3105-4d6b-b4d4-9af53126df75
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 256
ht-degree: 87%

---

# Partage d&#39;audiences avec Adobe Experience Cloud {#sharing-audiences-with-adobe-experience-cloud}


>[!CAUTION]
>
>Pour partager des audiences avec les solutions Adobe Experience Cloud, vous devez implémenter Adobe IDentity Management System. [En savoir plus sur l’IMS](../../integrations/using/about-adobe-id.md).

Avec Adobe Campaign, vous pouvez partager des audiences et des segments avec les services Adobe Experience Cloud. Deux options sont disponibles :

1. Envoyer des données de segment Adobe Experience Platform à Adobe Campaign. Pour mettre en œuvre cette intégration, vous devez connecter à Campaign votre plateforme de données clientes en temps réel (RTCDP). [En savoir plus dans cette section](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html?lang=fr){target="_blank"}.

1. Intégrez **Adobe Campaign** aux **Audiences Experience Cloud** ou **Adobe Audience Manager**. Vous pourrez alors :

   * Importez les audiences/segments partagés de différentes solutions Adobe Experience Cloud dans Adobe Campaign. L&#39;import d&#39;audiences peut être réalisé depuis les listes dans Adobe Campaign.

   * exporter des listes sous la forme d’audiences partagées Adobe Experience Cloud ; Ces audiences peuvent être exploitées dans les différentes solutions d’Adobe Experience Cloud que vous utilisez. L’export d’audiences peut être réalisé à la suite d’un ciblage dans un workflow, à l’aide d’une activité dédiée **[!UICONTROL Mise à jour d’audience partagée]**.

L’intégration prend en charge deux types d’identifiants Adobe Experience Cloud :

* **Identifiant visiteur** : ce type d’identifiant permet de réconcilier des visiteurs Adobe Experience Cloud avec des destinataires Adobe Campaign.
* **Identifiant déclaré** : ce type d’identifiant permet de réconcilier tous les types de données avec les éléments de la base de données Adobe Campaign. Dans Adobe Campaign, il est représenté sous la forme d’une clé de réconciliation prédéfinie.

  >[!NOTE]
  >
  > Désormais, la source de données des ID déclarés peut également être utilisée avec l’intégration d’Experience Cloud Assets.
  >
