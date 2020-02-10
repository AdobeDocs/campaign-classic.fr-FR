---
title: A propos des formulaires web
seo-title: A propos des formulaires web
description: A propos des formulaires web
seo-description: null
page-status-flag: never-activated
uuid: 1d129af4-008b-4f6a-9094-b2edd6c1eee1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-forms
discoiquuid: 3b8e4691-fcbc-48ef-b529-11c9a9a9d788
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# A propos des formulaires web{#about-web-forms}

Adobe Campaign intègre un module graphique de définition et de publication de formulaires web afin de créer des pages proposant des champs de saisie et de sélection, et pouvant inclure des données de la base. Vous pouvez ainsi concevoir et mettre en ligne des pages web auxquelles les utilisateurs pourront accéder pour consulter ou renseigner des informations.

Ce chapitre présente le mode de création et de gestion d&#39;un formulaire Web, la gestion des champs et des pages, les modes de stockage et d&#39;enregistrement.

>[!CAUTION]
>
>Pour des raisons de confidentialité, nous vous recommandons d&#39;utiliser HTTPS pour toutes les ressources externes.

## Etapes de création d&#39;un formulaire web {#steps-for-creating-a-web-form}

Le chapitre suivant présente les étapes de conception d&#39;un formulaire de type **webForm** sous Adobe Campaign, ainsi que les options et paramétrages disponibles. Adobe Campaign permet de mettre ce formulaire Web à disposition des utilisateurs, et de collecter et archiver les réponses dans la base de données.

>[!CAUTION]
>
>Lors de la configuration d&#39;applications web et de formulaires web, vous devez disposer d&#39;une résolution verticale minimale de 900 pixels (ex : 1 600x900).

Les formulaires Web sont accessibles via le menu Applications Web de l’onglet **Campagnes** . Dans l’arborescence d’Adobe Campaign, ils sont regroupés sous le **[!UICONTROL Resources > Online > Web Applications]** noeud.

To create a Web form, click the **[!UICONTROL Create]** button above the list of Web applications.

![](assets/webapp_create_new.png)

Choisissez le modèle de formulaire Web (par défaut **[!UICONTROL newWebForm]**).

![](assets/s_ncs_admin_survey_select_template.png)

Vous accédez alors au tableau de bord du formulaire.

![](assets/webapp_empty_dashboard.png)

The **[!UICONTROL Edit]** tab lets you create your content.

![](assets/webapp_edit_tab.png)

Pour définir le paramétrage et le contenu du formulaire Web, les étapes sont les suivantes :

* Créer la ou les pages et les contrôles qui les composent : champs de saisie, listes déroulantes, contenus HTML, etc.

   Cette étape est présentée ci-dessous.

* Définir de l&#39;enchaînement des pages et conditionner l&#39;affichage.

   Cette étape est détaillée dans [Définition du séquencement](../../web/using/defining-web-forms-page-sequencing.md)des pages de formulaires Web.

* Au besoin, traduire le contenu.

   Cette étape est détaillée dans [Traduction d’un formulaire](../../web/using/translating-a-web-form.md)Web.

## A propos de la conception des formulaires web {#about-web-forms-designing}

Les pages du formulaire sont créées via un éditeur spécifique qui vous permet de définir et de configurer des zones d’entrée (texte), des champs de sélection (listes, cases à cocher, etc.) et des éléments statiques (images, contenus HTML, etc.). Ils peuvent être regroupés en conteneurs et leur disposition modifiée en fonction de vos besoins (pour plus d’informations, reportez-vous à la section [Création de conteneurs](../../web/using/defining-web-forms-layout.md#creating-containers)).

La définition du contenu et de la mise en page des écrans du formulaire sont présentés dans les sections suivantes :

* [Ajouter des champs à un formulaire web](../../web/using/adding-fields-to-a-web-form.md),
* [Insérer du contenu HTML](../../web/using/static-elements-in-a-web-form.md#inserting-html-content),
* [Eléments statiques dans un formulaire web](../../web/using/static-elements-in-a-web-form.md),
* [Définir la disposition des formulaires web](../../web/using/defining-web-forms-layout.md).

>[!NOTE]
>
>* Lors de la conception de la page, vous pouvez afficher le rendu final dans l’ **[!UICONTROL Preview]** onglet. Pour afficher les modifications, enregistrez d’abord le formulaire. Toutes les erreurs s’affichent dans l’ **[!UICONTROL Log]** onglet.
>* Pour vous assurer que l’affichage des pages et le stockage des informations se produisent dans la séquence appropriée, activez le mode de débogage dans le formulaire Web. Pour ce faire, accédez au **[!UICONTROL Preview]** sous-onglet et cochez la **[!UICONTROL Enable debug mode]** case : toutes les informations collectées et les erreurs d&#39;exécution possibles s&#39;afficheront au bas de chaque page.
>



### Utiliser les icônes de la barre d&#39;outils {#using-the-icons-in-the-toolbar}

Vous pouvez également utiliser les icônes de la barre d&#39;outils ou le bouton droit de la souris pour insérer une zone de saisie.

![](assets/s_ncs_admin_webform_add_selection.png)

Dans ce cas, vous devez d&#39;abord sélectionner le type de champ à ajouter puis le mode de stockage des réponses.

![](assets/s_ncs_admin_webform_select_storage.png)

Cliquez sur **[!UICONTROL Ok]** pour valider la sélection.

![](assets/s_ncs_admin_webform_confirm_storage.png)

