---
product: campaign
title: Définition du mapping des données externe
description: Découvrez comment mapper des données dans une base de données externe
feature: Installation, Instance Settings
exl-id: a7253ca7-47e5-4def-849d-3ce1c9b948fb
TQID: 'https://experienceleague.adobe.com/9mE5BjrDg-E4FDyFFL0GVAVPof0rlSSOlzyj2zk21ag'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
    internal-label: Schemas
  - id: 7f0a1ee5-eeb8-5478-a9cd-b1896f033118
    internal-label: Instance Settings
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
    internal-label: PI
  - id: e656c701-3899-4db3-989c-de0980ddfffa
    internal-label: Installation
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 100%
---
# Définition du mapping des données externe {#defining-data-mapping}



Adobe Campaign permet de définir un mapping sur les données d&#39;une table externe.

Pour cela, une fois que le schéma de la table externe a été créé, vous devez créer un nouveau mapping de diffusion afin d&#39;utiliser les données contenues dans cette table en tant que cible des actions de diffusions.

Pour cela, les étapes sont les suivantes :

1. Créez un nouveau mapping de diffusion et sélectionnez la dimension de ciblage, par exemple le schéma que vous venez de créer.

   ![](assets/wf_new_mapping_create_fda.png)

1. Indiquez les champs où sont stockées les informations nécessaires à la diffusion (nom, prénom, email, adresse postale, etc.).

   ![](assets/wf_new_mapping_define_join.png)

1. Indiquez les paramètres relatifs au stockage des informations, et notamment le suffixe des schémas d&#39;extension, afin de les identifier facilement.

   ![](assets/wf_new_mapping_define_names.png)

   Vous pouvez choisir de stocker ou non les exclusions (**excludelog**), avec les messages (**broadlog**) ou dans une table distincte.

   Vous pouvez également gérer ou non le tracking pour ce mapping de diffusion (**trackinglog**).

1. Sélectionnez ensuite les extensions à prendre en compte. Le type d’extension dépend des paramètres et options de votre plateforme (consultez votre contrat de licence).

   ![](assets/wf_new_mapping_define_extensions.png)

   Cliquez sur le bouton **[!UICONTROL Enregistrer]** pour lancer la création du mapping de diffusion : toutes les tables liées sont créées automatiquement, selon les paramètres sélectionnés.
