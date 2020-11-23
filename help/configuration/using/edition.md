---
solution: Campaign Classic
product: campaign
title: Edition
description: Edition
audience: configuration
content-type: reference
topic-tags: navigation-hierarchy
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 100%

---


# Edition{#edition}

L&#39;écran de création et de configuration des documents de paramétrage de l&#39;arborescence de navigation est accessible à partir du nœud **[!UICONTROL Administration > Paramétrage > Arborescences de navigation]** :

![](assets/d_ncs_integration_navigation_arbo.png)

Le paramétrage de l&#39;arborescence de navigation est réparti entre plusieurs documents XML. Le principe est similaire à celui de l&#39;extension des schémas : tous les documents sont fusionnés pour générer un document unique contenant l&#39;ensemble du paramétrage. Celui-ci n&#39;est pas éditable et peut être visualisé à partir de l&#39;onglet &quot;Aperçu&quot;.

La zone d&#39;édition renseigne le contenu du document XML :

![](assets/d_ncs_integration_navigation_edit.png)

>[!NOTE]
>
>Le contrôle d’édition « Name » vous permet de saisir la clé du document, composée du nom et de l’espace de nommage. Les attributs « name » et « namespace » de l’élément **`<navtree>`** sont automatiquement mis à jour dans le champ de modification XML du schéma.

L&#39;aperçu génère automatiquement le document fusionné contenant le paramétrage complet :

![](assets/d_ncs_integration_navigation_preview.png)

