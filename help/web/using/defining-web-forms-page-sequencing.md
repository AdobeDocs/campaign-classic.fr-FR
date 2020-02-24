---
title: Définir l'enchaînement des pages des formulaires web
seo-title: Définir l'enchaînement des pages des formulaires web
description: Définir l'enchaînement des pages des formulaires web
seo-description: null
page-status-flag: never-activated
uuid: 297fad62-d806-4bd8-9b8c-313c20344ab0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-forms
discoiquuid: 85bf3244-6896-43e7-96b8-84c45c282fec
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c9c9d5f96856ce9e19571bad032d2bf04eaa60bd

---


# Définir l&#39;enchaînement des pages des formulaires web{#defining-web-forms-page-sequencing}

Le formulaire peut contenir une ou plusieurs pages. Il est construit au travers d&#39;un diagramme qui permet d&#39;enchaîner les pages et les étapes de test, d&#39;exécution de script, d&#39;enregistrement et les sauts. Le mode de construction du diagramme est le même que pour un workflow.

## A propos des pages précédente et suivante {#about-previous-page-and-next-page}

Pour chaque page, il est possible de supprimer les boutons **[!UICONTROL Suivant]** ou **[!UICONTROL Précédent]**. Pour cela, sélectionnez la page concernée et cochez l&#39;option **[!UICONTROL Ne pas autoriser le passage à la page suivante]** ou **[!UICONTROL Ne pas autoriser le retour à la page précédente]** .

![](assets/s_ncs_admin_survey_no_next_page.png)

Vous pouvez remplacer ces boutons par des liens. Voir [Insertion de contenu](../../web/using/static-elements-in-a-web-form.md#inserting-html-content)HTML.

## Insérer un saut {#inserting-a-jump}

L&#39;objet **[!UICONTROL Saut]** permet d&#39;accéder à une autre page ou un autre formulaire lorsque l&#39;utilisateur clique sur le bouton **[!UICONTROL Suivant]**.

La destination peut être :

* Une autre page du formulaire. Pour cela, sélectionnez l&#39;option **[!UICONTROL Activité interne]** puis indiquez la page visée, comme ci-dessous :

   ![](assets/s_ncs_admin_jump_param1.png)

* Un autre formulaire. Pour cela, sélectionnez l&#39;option **[!UICONTROL Explicite]** et indiquez le formulaire de destination.

   ![](assets/s_ncs_admin_jump_param2.png)

* La destination peut être stockée dans une variable. Dans ce cas, il suffit de la sélectionner dans la liste déroulante, comme dans l&#39;exemple suivant :

   ![](assets/s_ncs_admin_jump_param3.png)

* L&#39;onglet **[!UICONTROL Commentaire]** permet de saisir des informations qui seront visibles par l&#39;opérateur lorsqu&#39;il clique sur l&#39;objet dans le diagramme.

   ![](assets/s_ncs_admin_survey_jump_comment.png)

## Example: accessing another form according to a parameter of the URL {#example--accessing-another-form-according-to-a-parameter-of-the-url}

Dans cet exemple nous allons paramétrer un formulaire Web qui permet, à la validation, d&#39;afficher un autre formulaire, désigné par un paramètre de l&#39;URL. Les étapes sont les suivantes :

1. Insérez un saut à la fin d&#39;un formulaire : le saut remplace alors la boîte de **[!UICONTROL Fin]**.

   ![](assets/s_ncs_admin_survey_jump_sample1.png)

1. Dans les propriétés du formulaire, ajoutez un paramètre (**next**) stocké dans une variable locale (**next**). Les variables locales sont détaillées dans la section [Stockage des données dans une variable](../../web/using/web-forms-answers.md#storing-data-in-a-local-variable)locale.

   ![](assets/s_ncs_admin_survey_jump_sample2.png)

1. Editez l&#39;objet **[!UICONTROL Saut]**, choisissez l&#39;option **[!UICONTROL Stockée dans une variable]** et sélectionnez la variable **next** dans la liste déroulante.

   ![](assets/s_ncs_admin_survey_jump_sample3.png)

1. L&#39;URL de diffusion doit contenir le nom interne du formulaire de destination, par exemple :

   ```
   https://[myserver]/webForm/APP62?&next=APP22
   ```

   Ainsi, lorsque l&#39;utilisateur clique sur le bouton **[!UICONTROL Valider]**, le formulaire **APP22** est affiché.

## Insérer un lien vers une autre page du formulaire {#inserting-a-link-to-another-page-of-the-form}

You can insert links to other pages of the form. To do this, add a **[!UICONTROL Link]** type static element to the page. Pour plus d&#39;informations, reportez-vous à la section [Insertion d&#39;un lien](../../web/using/static-elements-in-a-web-form.md#inserting-a-link).

## Conditionner l&#39;affichage des pages {#conditional-page-display}

### Affichage en fonction des réponses {#display-based-on-responses}

La boîte de **[!UICONTROL Test]** permet de conditionner l&#39;enchaînement des pages dans un formulaire. Elle permet de définir différents embranchements en fonction du résultat d&#39;un test. Vous pouvez ainsi afficher des pages différentes en fonction des réponses fournies par l&#39;utilisateur.

Par exemple, vous pouvez afficher une page différente pour les clients ayant déjà commandé sur internet, et une autre pour ceux ayant effectué plus de dix commandes. Pour cela, dans la première page du formulaire, insérez une zone de saisie de type **[!UICONTROL Nombre]** pour que l&#39;utilisateur indique le nombre de commandes passées.

![](assets/s_ncs_admin_survey_test_ex0.png)

Vous pouvez stocker cette information dans un champ de la base de données ou utiliser une variable locale, selon vos besoins.

>[!NOTE]
>
>Les modes de stockage sont détaillés dans les champs [de stockage](../../web/using/web-forms-answers.md#response-storage-fields)Réponse.

Dans notre exemple, nous allons utiliser une variable :

![](assets/s_ncs_admin_survey_test_ex1.png)

Dans le diagramme du formulaire, insérez ensuite une boîte de test afin de définir les conditions. Pour chaque condition, un nouveau branchement sera ajouté en sortie de la boîte de test.

![](assets/s_ncs_admin_survey_test_ex2.png)

Cochez l&#39;option **[!UICONTROL Activer le branchement par défaut]** pour ajouter une transition pour les cas où aucune des conditions n&#39;est vraie. Cette option n&#39;est pas utile si tous les cas possibles sont couverts par les conditions définies.

Définissez ensuite l&#39;enchaînement des pages lorsque l&#39;une ou l&#39;autre des conditions est vérifiée, par exemple :

![](assets/s_ncs_admin_survey_test_ex3.png)

### Affichage en fonction des paramètres {#display-based-on-parameters}

Vous pouvez également personnaliser le séquencement des pages en fonction des paramètres d’initialisation du formulaire Web ou des valeurs stockées dans la base de données. Voir Paramètres [d’URL de](../../web/using/defining-web-forms-properties.md#form-url-parameters)formulaire.

## Ajouter des scripts {#adding-scripts}

L&#39;objet **[!UICONTROL Script]** vous permet de saisir directement un script Javascript par exemple pour modifier la valeur d&#39;un champ, récupérer des données dans la base ou appeler une API Adobe Campaign.

## Personnaliser la page de fin {#personalizing-the-end-page}

Vous devez positionner une page de fin à la fin du diagramme. La page de fin est affichée lorsque l&#39;utilisateur clique sur le bouton **[!UICONTROL Valider]** du formulaire Web.

Pour personnaliser cette page, double-cliquez sur l&#39;objet **[!UICONTROL Fin]** et saisissez le contenu de la page dans l&#39;éditeur central.

![](assets/s_ncs_admin_survey_end_page_edit.png)

* Vous pouvez copier et coller un contenu HTML existant. Pour cela, cliquez sur le bouton **[!UICONTROL Afficher le code source]** et insérez le code HTML.
* Vous pouvez utiliser une URL externe : pour cela, cochez l&#39;option correspondante et saisissez l&#39;URL de la page à afficher.

