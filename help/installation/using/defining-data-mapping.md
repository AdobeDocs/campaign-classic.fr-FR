---
product: campaign
title: Définition du mapping des données externe
description: Découvrez comment mapper des données dans une base de données externe
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: a7253ca7-47e5-4def-849d-3ce1c9b948fb
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: ht
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

1. Sélectionnez ensuite les extensions qui seront prises en compte. Le type d&#39;extension dépend des paramètres et options de votre plateforme (consultez votre contrat de licence).

   ![](assets/wf_new_mapping_define_extensions.png)

   Cliquez sur le bouton **[!UICONTROL Enregistrer]** pour lancer la création du mapping de diffusion : toutes les tables liées sont créées automatiquement, selon les paramètres sélectionnés.
