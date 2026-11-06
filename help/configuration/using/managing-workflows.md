---
product: campaign
title: Gestion des workflows
description: Gestion des workflows
feature: Workflows, Configuration
role: Developer
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
exl-id: 617b0050-6b04-4c68-9f63-511baae99f41
TQID: 'https://experienceleague.adobe.com/dpHtLw4PYGg35t-ihmw9LGUSbjgeNloUhGXp9KPJaRU'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
  - id: a14877cc-63b1-41d9-bf0b-5f97cadd0417
    internal-label: Configuration guidelines
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: cce1f22c34cbd13d063850a7ca636a3b0dfc62f6
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 85%
---
# Gestion des workflows{#managing-workflows}



Par défaut, vos nouveaux workflows reposent sur un modèle de workflow préconfiguré et basé sur une table de personnes destinataires (nms:recipient). Pour qu’ils soient automatiquement basés sur la table personnalisée des destinataires référencée dans l’option **Nms_DefaultRcpSchema** (voir la section [Configuration de l’interface](../../configuration/using/configuring-the-interface.md)), vous devez créer un modèle de workflow.

Créez un nouveau modèle de workflow à partir du nœud **[!UICONTROL Ressources > Modèles > Modèles de workflow]**. Dans les propriétés du modèle, les dimensions renseignées correspondent alors à votre table de destinataires externe.

En basant vos nouveaux workflows sur le modèle nouvellement créé, votre table personnalisée sera sélectionnée par défaut au niveau des dimensions de ciblage et de filtrage globales du workflow.

Toutes les activités utilisées dans votre workflow utiliseront ainsi votre table personnalisée sans besoin de paramétrage manuel supplémentaire.

Pour plus d’informations sur les workflows, consultez [cette section](https://experienceleague.adobe.com/en/docs/campaign/automation/workflows/introduction/about-workflows){target="_blank"} (documentation de Campaign v8).

![](assets/cfg_external_table_workflow.png)
