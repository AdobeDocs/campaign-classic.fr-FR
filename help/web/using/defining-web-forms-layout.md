---
title: Définir la disposition des formulaires web
seo-title: Définir la disposition des formulaires web
description: Définir la disposition des formulaires web
seo-description: null
page-status-flag: never-activated
uuid: ae8659d0-3608-44dd-93ec-33c418a66ad0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-forms
discoiquuid: 67d1d39b-3a5f-4ed6-8fcf-570891043b10
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# Définir la disposition des formulaires web{#defining-web-forms-layout}

## Créer des conteneurs {#creating-containers}

Les conteneurs permettent de regrouper les champs d&#39;une page et d&#39;en paramétrer la mise en page. Ils permettent d&#39;organiser les éléments dans la page.

For each page of the form, containers are created via the **[!UICONTROL Containers]** button of the toolbar.

![](assets/s_ncs_admin_survey_containers_add.png)

Utilisez un conteneur pour regrouper des éléments de la page sans ajouter d’étiquette au rendu final. Les éléments sont regroupés dans la sous-arborescence du conteneur. Les conteneurs standard vous permettent de gérer la mise en page.

Par exemple :

![](assets/s_ncs_admin_survey_containers_std_arbo.png)

La position des libellés est appliquée aux éléments placés sous le conteneur dans la hiérarchie. Il peut être surchargé pour chaque élément si nécessaire. Ajoutez ou supprimez des colonnes pour modifier la disposition. See [Positioning the fields on the page](#positioning-the-fields-on-the-page).

Dans l&#39;exemple ci-dessus, le rendu sera le suivant :

![](assets/s_ncs_admin_survey_containers_std_ex.png)

## Placer les champs de la page {#positioning-the-fields-on-the-page}

La mise en page du formulaire Web est définie au niveau de la page, au niveau de chaque conteneur et peut être surchargée pour chaque contrôle.

Les pages sont organisées en colonnes : chaque page contient un certain nombre de colonnes. Chaque champ de la page occupe **n** cellules. Les conteneurs s&#39;étendent eux aussi sur un certain nombre de colonnes et les champs qu&#39;ils contiennent s&#39;étendent sur un certain nombre de cellules.

Par défaut, les pages sont construites sur une seule colonne et chaque élément occupe une cellule. Ainsi, les zones sont affichées les unes en dessous des autres, chacune occupant toute la ligne, comme ci-dessous :

![](assets/s_ncs_admin_survey_container_ex.png)

Dans l&#39;exemple suivant, le paramétrage par défaut a été conservé. La page est construite sur une seule colonne et contient quatre conteneurs.

![](assets/s_ncs_admin_survey_container_ex0.png)

Chaque conteneur s&#39;étend sur une colonne et chaque élément occupe une cellule :

![](assets/s_ncs_admin_survey_container_ex0a.png)

Le rendu est le suivant :

![](assets/s_ncs_admin_survey_container_ex0_rend.png)

Vous pouvez adapter les paramètres d&#39;affichage pour obtenir le rendu suivant :

![](assets/s_ncs_admin_survey_container_ex1_rend.png)

Dans l&#39;exemple de rendu ci-dessus, chaque zone de saisie, chaque titre et chaque image occupent une seule cellule dans les colonnes des conteneurs.

Vous pouvez modifier la mise en page au niveau de chaque conteneur. Dans notre exemple, vous pouvez passer le contenu du conteneur 4 sur deux colonnes et répartir les éléments.

![](assets/s_ncs_admin_survey_container_ex2_rend.png)

Le titre et la liste occupent une cellule chacune (et donc une ligne entière du conteneur) et la case à cocher s’étend sur deux cellules. Le nombre de cellules attribuées au champ de saisie est défini dans l’ **[!UICONTROL General]** onglet ou l’ **[!UICONTROL Advanced]** onglet, selon le type de champ :

![](assets/s_ncs_admin_survey_container_ex2.png)

## Définir la position des libellés {#defining-the-position-of-labels}

Vous pouvez définir l&#39;alignement des champs et des libellés du formulaire.

Par défaut, les paramètres d&#39;affichage des champs et autres contenus de la page sont hérités du paramétrage général du formulaire, le paramétrage de la page ou celui du conteneur parent, s&#39;il existe.

Les paramètres d’affichage globaux pour l’ensemble du formulaire sont spécifiés dans la zone Propriétés du formulaire. L’ **[!UICONTROL Rendering]** onglet permet de sélectionner la position des libellés.

![](assets/s_ncs_admin_survey_label_position.png)

This position can be overloaded for each page, each container, and each field, via the **[!UICONTROL Advanced]** tab.

Les alignements supportés sont les suivants :

* Hérité : l&#39;alignement est hérité de l&#39;élément parent (valeur par défaut), c&#39;est-à-dire le conteneur parent, ou, à défaut, la page.
* Gauche/Droite : le libellé est positionné à droite ou à gauche du champ,
* Au-dessus/En-dessous : le libellé est positionné au-dessus ou en-dessous du champ,
* Caché : le libellé n&#39;est pas affiché.

