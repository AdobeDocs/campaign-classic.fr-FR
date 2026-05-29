---
product: campaign
title: Utiliser Adobe Campaign et Adobe Analytics
description: Utiliser Adobe Campaign et Adobe Analytics
feature: Analytics Integration
role: User, Admin
level: Beginner
exl-id: 985cf088-7546-4875-8e11-cafe5bd3e323
TQID: https://experienceleague.adobe.com/YuvP0m31wL-WlocUXU3rWovOiwLiA5XrEsnBLlW3nY8
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
level_v2:
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
subfeature_v2:
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
  - id: df0d6518-6f49-46e2-b46e-3bcc513f553f
  - id: eb007b6d-6e57-46ab-9485-3f24d6102304
  - id: b1fd1501-3105-4d6b-b4d4-9af53126df75
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 212
ht-degree: 100%

---

# Utiliser Adobe Campaign et Adobe Analytics {#adobe-analytics-connector-gs}

Le connecteur Adobe Analytics permet à Adobe Campaign et Adobe Analytics d’interagir par le biais du package **[!UICONTROL Connecteurs Web Analytics]**. Il transmet des données à Adobe Campaign sous la forme de segments portant sur le comportement des utilisateurs et utilisatrices suite à une campagne. Réciproquement, il envoie des indicateurs et des attributs de campagnes diffusées par Adobe Campaign à Adobe Analytics.

## Conditions préalables et mécanismes de sécurisation {#adobe-analytics-connector-guardrails}

Avant de commencer à utiliser le connecteur Adobe Campaign-Adobe Analytics, tenez compte des mécanismes de sécurisation et conditions préalables suivants.

* Pour cette intégration, une connexion à Campaign avec Adobe Identity Management System (IMS) est requise. [En savoir plus](../../integrations/using/about-adobe-id.md).

* Le connecteur Adobe Analytics n’est pas compatible avec les messages transactionnels (Message Center).

* Le module complémentaire de connecteur Web Analytics doit être installé sur votre environnement, via le package dédié.

   * Pour les implémentations hybrides et On-premise, assurez-vous de suivre les étapes d’approvisionnement décrites sur cette [page](adobe-analytics-provisioning.md).
   * En tant qu’utilisateur ou utilisatrice Hoster ou Managed Cloud Services, contactez Adobe pour connecter Campaign aux services et aux solutions Adobe Experience Cloud.


## Configuration et utilisation {#adobe-analytics-connector-usage}

Pour activer cette intégration, vous devez créer votre compte technique Adobe, comme décrit sur [cette page](oauth-technical-account.md).

Découvrez comment utiliser Adobe Campaign et Adobe Analytics dans la [Documentation d’Adobe Campaign v8](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/connect/ac-aa){target="_blank"}.
