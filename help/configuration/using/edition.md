---
product: campaign
title: Modifier l'arborescence de navigation de l'Explorateur Campaign
description: Modifier l'arborescence de navigation de l'Explorateur Campaign
feature: Application Settings
role: Developer
exl-id: 204d4a24-267c-4976-90d9-7bf5bee8d116
TQID: https://experienceleague.adobe.com/k8LhZvPSYchAxnQew5eknkDbxHDznzPefl032auuYLc
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
role_v2: id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
subfeature_v2: []
source-git-commit: bb41e9407ab5853b0194bb325bbf3f17bc3ea232
workflow-type: ht
source-wordcount: 135
ht-degree: 100%

---

# Modifier l&#39;arborescence de navigation de l&#39;Explorateur Campaign{#edition}

L&#39;écran de création et de configuration des documents de paramétrage de l&#39;arborescence de navigation est accessible à partir du nœud **[!UICONTROL Administration > Paramétrage > Arborescences de navigation]** :

![](assets/d_ncs_integration_navigation_arbo.png)

La configuration de l’arborescence de navigation est divisée en plusieurs documents XML.Son principe de fonctionnement est similaire à celui de l’extension de schéma : tous les documents sont fusionnés pour générer un document unique contenant l’ensemble de la configuration.Ce document ne peut pas être modifié et s’affiche à partir de l’onglet « Prévisualisation ».

La zone d&#39;édition renseigne le contenu du document XML :

![](assets/d_ncs_integration_navigation_edit.png)

>[!NOTE]
>
>Le contrôle d’édition « Name » vous permet de saisir la clé du document, composée du nom et de l’espace de noms. Les attributs « name » et « namespace » de l’élément **`<navtree>`** sont automatiquement mis à jour dans le champ de modification XML du schéma.

L&#39;aperçu génère automatiquement le document fusionné contenant le paramétrage complet :

![](assets/d_ncs_integration_navigation_preview.png)
