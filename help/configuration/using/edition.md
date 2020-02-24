---
title: Edition
seo-title: Edition
description: Edition
seo-description: null
page-status-flag: never-activated
uuid: df9298fc-5f62-4afb-8118-ca7e3987e81f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: navigation-hierarchy
discoiquuid: 820be231-af76-44ce-8f4d-cd5eae1eb169
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Edition{#edition}

L&#39;écran de création et de configuration des documents de paramétrage de l&#39;arborescence de navigation est accessible à partir du nœud **[!UICONTROL Administration > Paramétrage > Arborescences de navigation]** :

![](assets/d_ncs_integration_navigation_arbo.png)

Le paramétrage de l&#39;arborescence de navigation est réparti entre plusieurs documents XML. Le principe est similaire à celui de l&#39;extension des schémas : tous les documents sont fusionnés pour générer un document unique contenant l&#39;ensemble du paramétrage. Celui-ci n&#39;est pas éditable et peut être visualisé à partir de l&#39;onglet &quot;Aperçu&quot;.

La zone d&#39;édition renseigne le contenu du document XML :

![](assets/d_ncs_integration_navigation_edit.png)

>[!NOTE]
>
>Le contrôle d’édition &quot;Name&quot; vous permet de saisir la clé du document, composée du nom et de l’espace de noms. Les attributs &quot;name&quot; et &quot;namespace&quot; de l’ **`<navtree>`** élément sont automatiquement mis à jour dans le champ de modification XML du schéma.

L&#39;aperçu génère automatiquement le document fusionné contenant le paramétrage complet :

![](assets/d_ncs_integration_navigation_preview.png)

