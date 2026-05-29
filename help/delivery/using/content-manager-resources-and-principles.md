---
product: campaign
title: Ressources et principes de la gestion de contenu
description: Ressources et principe de la gestion de contenu
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
feature: Templates
role: User, Developer
exl-id: ade3f1d1-2235-4148-9b6f-721d3f521a15
TQID: https://experienceleague.adobe.com/xWBOrnm4v7N3XOVvOcPNqngz0cDvvT39tI3xJVKdFZg
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: ce44533e-8ec8-4e11-a9e9-78b0fe561832
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 247
ht-degree: 79%

---

# Ressources et principes de la gestion de contenu{#content-manager-resources-and-principles}


Vous devez définir un modèle de publication contenant des modèles de transformation pour chaque contenu.

Un bloc de contenu est structuré dans un document XML pour le stockage des données. Une interface de modification est utilisée pour saisir le contenu à partir de la console cliente Adobe Campaign ou via un navigateur web. Le contenu peut également être automatiquement renseigné à partir de la capture de flux XML ou de données agrégées dans une base de données.

La combinaison du document XML et des feuilles de styles XSL ou un Template Javascript génère automatiquement la projection dans les différents formats (HTML, Texte) du modèle de publication.

![](assets/d_ncs_content_process.png)

Les différentes ressources nécessaires pour le paramétrage d&#39;un contenu sont les suivantes :

* Schémas de données : description de la structure des contenus XML. Voir à ce sujet la section [Schémas de données](data-schemas.md).
* Formulaires de saisie de données : construction d&#39;écrans de saisie de données. Pour plus d&#39;informations, consultez la section [Formulaires de saisie](input-forms.md).
* Images : images utilisées dans les formulaires de saisie de données. Pour plus d&#39;informations, consultez la section [Gestion des images](formatting.md#image-management).
* Feuilles de style : formatage des documents de sortie en langage XSLT. Pour plus d&#39;informations, consultez la section [Formatage](formatting.md).
* Modèles JavaScript : formatage des documents de sortie en langage JavaScript. Pour plus d&#39;informations, consultez la section [Modèles de publication](publication-templates.md).
* Codes JavaScript : codes JavaScript pour l&#39;agrégation des données. Pour plus d&#39;informations, consultez la section [Agrégateur](publication-templates.md#aggregator).
* Modèles de publication : définition des modèles de publication. Pour plus d&#39;informations, consultez la section [Modèles de publication](publication-templates.md).
* Contenu : instances de contenu à créer et à publier. Pour plus d&#39;informations à ce sujet, reportez-vous à la section [Utiliser un modèle de contenu](using-a-content-template.md).
