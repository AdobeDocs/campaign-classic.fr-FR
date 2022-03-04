---
product: campaign
title: Prise en main des formulaires web
description: Prise en main des formulaires web dans Campaign
feature: Landing Pages, Web Forms
exl-id: 63602bed-ace6-4632-a735-5d268a7d72d0
source-git-commit: b6f1556cf49492cefaf61c29a058584b0ccee16a
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 100%

---

# Prise en main des formulaires web{#about-web-forms}

![](../../assets/common.svg)

Adobe Campaign intègre un module graphique de définition et de publication de formulaires web afin de créer des pages proposant des champs de saisie et de sélection, et pouvant inclure des données de la base. Vous pouvez ainsi concevoir et mettre en ligne des pages web auxquelles les utilisateurs pourront accéder pour consulter ou renseigner des informations.

Ce chapitre présente le mode de création et de gestion d&#39;un formulaire Web, la gestion des champs et des pages, les modes de stockage et d&#39;enregistrement.

>[!CAUTION]
>
>Pour des raisons de confidentialité, nous vous recommandons d&#39;utiliser HTTPS pour toutes les ressources externes.

## Etapes de création d&#39;un formulaire web {#steps-for-creating-a-web-form}

Le chapitre suivant présente les étapes de conception d&#39;un formulaire de type **webForm** sous Adobe Campaign, ainsi que les options et paramétrages disponibles. Adobe Campaign permet de mettre ce formulaire Web à disposition des utilisateurs, et de collecter et archiver les réponses dans la base de données.

>[!CAUTION]
>
>Lors de la configuration d&#39;applications web et de formulaires web, vous devez disposer d&#39;une résolution verticale minimale de 900 pixels (ex : 1 600x900).

Les formulaires web sont accessibles via le menu Applications Web de l&#39;onglet **Campagnes**. Dans l’arborescence d’Adobe Campaign, ils sont regroupés sous le nœud **[!UICONTROL Ressources > En ligne > Applications Web]**.

Pour créer un formulaire Web, cliquez sur le bouton **[!UICONTROL Créer]** situé au-dessus de la liste des applications Web.

![](assets/webapp_create_new.png)

Choisissez le modèle de formulaire Web (par défaut **[!UICONTROL newWebForm]**).

![](assets/s_ncs_admin_survey_select_template.png)

Vous accédez alors au tableau de bord du formulaire.

![](assets/webapp_empty_dashboard.png)

L&#39;onglet **[!UICONTROL Edition]** permet d&#39;en créer le contenu.

![](assets/webapp_edit_tab.png)

Pour définir le paramétrage et le contenu du formulaire Web, les étapes sont les suivantes :

* Commencez par créer les pages et contrôles requis : champs de saisie, listes déroulantes, contenus HTML, etc.

   Cette étape est présentée ci-dessous.

* Définir de l&#39;enchaînement des pages et conditionner l&#39;affichage.

   Cette étape est présentée dans la section [Définir l&#39;enchaînement des pages des formulaires web](defining-web-forms-page-sequencing.md).

* Au besoin, traduire le contenu.

   Cette étape est présentée dans la section [Traduire un formulaire web](translating-a-web-form.md).

## À propos de la conception des formulaires web {#about-web-forms-designing}

Les pages du formulaire sont créées dans un éditeur spécifique qui permet de définir et de configurer des zones d&#39;entrée (texte), des champs de sélection (listes, cases à cocher, etc.) et des éléments statiques (images, contenus HTML, etc.). Ces éléments peuvent être regroupés en conteneurs et leur disposition modifiée en fonction de vos besoins (voir à ce sujet la section [Créer des conteneurs](defining-web-forms-layout.md#creating-containers)).

La définition du contenu et de la mise en page des écrans du formulaire sont présentés dans les sections suivantes :

* [Ajouter des champs à un formulaire web](adding-fields-to-a-web-form.md),
* [Insérer du contenu HTML](static-elements-in-a-web-form.md#inserting-html-content),
* [Eléments statiques dans un formulaire web](static-elements-in-a-web-form.md),
* [Définir la disposition des formulaires web](defining-web-forms-layout.md).

>[!NOTE]
>
>* Au cours de la conception des pages, vous pouvez visualiser le rendu final dans le sous-onglet **[!UICONTROL Aperçu]**. Pour visualiser les modifications, vous devez enregistrer le formulaire. Les erreurs éventuelles sont affichées dans l&#39;onglet **[!UICONTROL Journal]**.
>* Vous pouvez contrôler le bon enchaînement des pages et le stockage des informations en activant le mode debug au niveau du formulaire Web. Pour cela, à partir du sous-onglet **[!UICONTROL Aperçu]**, cochez l&#39;option **[!UICONTROL Activer le mode debug]** : les informations collectées et les éventuelles erreurs d&#39;exécution seront alors affichées en bas de chaque page.
>


### Utiliser les icônes de la barre d&#39;outils {#using-the-icons-in-the-toolbar}

Vous pouvez également utiliser les icônes de la barre d&#39;outils ou le bouton droit de la souris pour insérer une zone de saisie.

![](assets/s_ncs_admin_webform_add_selection.png)

Dans ce cas, vous devez d&#39;abord sélectionner le type de champ à ajouter puis le mode de stockage des réponses.

![](assets/s_ncs_admin_webform_select_storage.png)

Cliquez sur **[!UICONTROL Ok]** pour valider la sélection.

![](assets/s_ncs_admin_webform_confirm_storage.png)
