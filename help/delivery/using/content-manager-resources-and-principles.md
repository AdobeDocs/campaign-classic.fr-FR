---
title: Ressources et principes de la gestion de contenu
seo-title: Ressources et principes de la gestion de contenu
description: Ressources et principes de la gestion de contenu
seo-description: null
page-status-flag: never-activated
uuid: 3560e392-129a-471d-a211-05481cdda224
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: content-management
discoiquuid: b22b3abb-6fe5-4f4d-93fc-0d00d426edb6
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# Ressources et principes de la gestion de contenu{#content-manager-resources-and-principles}

Vous devez définir un modèle de publication contenant des modèles de transformation pour chaque contenu.

Un contenu est structuré dans un document XML pour le stockage des données. Une interface de saisie éditoriale va permettre de renseigner ce contenu dans la console cliente Adobe Campaign ou à partir d&#39;un navigateur Web. Le contenu peut également être automatiquement renseigné à partir de capture de flux XML ou de données agrégées dans une base de données.

La combinaison du document XML et des feuilles de styles XSL ou un Template Javascript génère automatiquement la projection dans les différents formats (HTML, Texte) du modèle de publication.

![](assets/d_ncs_content_process.png)

Les différentes ressources nécessaires pour le paramétrage d&#39;un contenu sont les suivantes :

* Schémas de données : description de la structure de contenu XML. For more on this, refer to [Data schemas](../../delivery/using/data-schemas.md).
* Formulaires de saisie de données : construction d’écrans d’entrée de données. For more on this, refer to [Input forms](../../delivery/using/input-forms.md).
* Images : images utilisées dans les formulaires de saisie de données. For more on this, refer to [Image management](../../delivery/using/formatting.md#image-management).
* Stylesheets : formatage des documents de sortie en langage XSLT. For more on this, refer to [Formatting](../../delivery/using/formatting.md).
* Modèles JavaScript : formatage des documents de sortie en utilisant le langage JavaScript. For more on this, refer to [Publication templates](../../delivery/using/publication-templates.md).
* Codes JavaScript : Codes JavaScript pour l’agrégation des données. For more on this, refer to [Aggregator](../../delivery/using/publication-templates.md#aggregator).
* Modèles de publication : définition des modèles de publication. For more on this, refer to [Publication templates](../../delivery/using/publication-templates.md).
* Contenu : instances de contenu à créer et à publier. Pour plus d’informations, reportez-vous à la section [Utilisation d’un modèle](../../delivery/using/using-a-content-template.md)de contenu.
