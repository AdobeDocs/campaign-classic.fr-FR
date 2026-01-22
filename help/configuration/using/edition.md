---
product: campaign
title: Modifier l'arborescence de navigation de l'Explorateur Campaign
description: Modifier l'arborescence de navigation de l'Explorateur Campaign
feature: Application Settings
role: Developer
exl-id: 204d4a24-267c-4976-90d9-7bf5bee8d116
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: ht
source-wordcount: '135'
ht-degree: 100%

---


# Modifier l&#39;arborescence de navigation de l&#39;Explorateur Campaign{#edition}

L&#39;écran de création et de configuration des documents de paramétrage de l&#39;arborescence de navigation est accessible à partir du nœud **[!UICONTROL Administration > Paramétrage > Arborescences de navigation]** :

![](assets/d_ncs_integration_navigation_arbo.png)

La configuration de l’arborescence de navigation est répartie entre plusieurs documents XML. Le principe est semblable à celui de l’extension des schémas : tous les documents sont fusionnés pour générer un document unique contenant l’ensemble de la configuration. Celui-ci n’est pas modifiable et peut être visualisé à partir de l’onglet « Aperçu ».

La zone d&#39;édition renseigne le contenu du document XML :

![](assets/d_ncs_integration_navigation_edit.png)

>[!NOTE]
>
>Le contrôle d’édition « Name » vous permet de saisir la clé du document, composée du nom et de l’espace de noms. Les attributs « name » et « namespace » de l’élément **`<navtree>`** sont automatiquement mis à jour dans le champ de modification XML du schéma.

L&#39;aperçu génère automatiquement le document fusionné contenant le paramétrage complet :

![](assets/d_ncs_integration_navigation_preview.png)
