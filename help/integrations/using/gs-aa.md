---
product: campaign
title: Utiliser Adobe Campaign et Adobe Analytics
description: Utiliser Adobe Campaign et Adobe Analytics
feature: Analytics Integration
role: User, Admin
level: Beginner
exl-id: 985cf088-7546-4875-8e11-cafe5bd3e323
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: ht
source-wordcount: '0'
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
