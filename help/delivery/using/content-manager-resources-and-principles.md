---
solution: Campaign Classic
product: campaign
title: Ressources et principes de la gestion de contenu
description: Ressources et principes de la gestion de contenu
audience: delivery
content-type: reference
topic-tags: content-management
translation-type: ht
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: ht
source-wordcount: '238'
ht-degree: 100%

---


# Ressources et principes de la gestion de contenu{#content-manager-resources-and-principles}

Vous devez définir un modèle de publication contenant des modèles de transformation pour chaque contenu.

Un contenu est structuré dans un document XML pour le stockage des données. Une interface de saisie éditoriale va permettre de renseigner ce contenu dans la console cliente Adobe Campaign ou à partir d&#39;un navigateur Web. Le contenu peut également être automatiquement renseigné à partir de capture de flux XML ou de données agrégées dans une base de données.

La combinaison du document XML et des feuilles de styles XSL ou un Template Javascript génère automatiquement la projection dans les différents formats (HTML, Texte) du modèle de publication.

![](assets/d_ncs_content_process.png)

Les différentes ressources nécessaires pour le paramétrage d&#39;un contenu sont les suivantes :

* Schémas de données : description de la structure des contenus XML. Voir à ce sujet la section [Schémas de données](../../delivery/using/data-schemas.md).
* Formulaires de saisie de données : construction d&#39;écrans de saisie de données. Voir à ce propos la section [Formulaires de saisie](../../delivery/using/input-forms.md).
* Images : images utilisées dans les formulaires de saisie de données. Voir à ce propos la section [Gestion des images](../../delivery/using/formatting.md#image-management).
* Feuilles de style : formatage des documents de sortie en langage XSLT. Voir à ce propos la section [Formatage](../../delivery/using/formatting.md).
* Modèles JavaScript : formatage des documents de sortie en langage JavaScript. Voir à ce propos la section [Modèles de publication](../../delivery/using/publication-templates.md).
* Codes JavaScript : codes JavaScript pour l&#39;agrégation des données. Voir à ce propos la section [Agrégateur](../../delivery/using/publication-templates.md#aggregator).
* Modèles de publication : définition des modèles de publication. Voir à ce propos la section [Modèles de publication](../../delivery/using/publication-templates.md).
* Contenu : instances de contenu à créer et à publier. Pour plus d&#39;informations à ce sujet, reportez-vous à la section [Utiliser un modèle de contenu](../../delivery/using/using-a-content-template.md).
