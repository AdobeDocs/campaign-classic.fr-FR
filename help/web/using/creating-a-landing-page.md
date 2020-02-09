---
title: Créer une Landing Page
seo-title: Créer une Landing Page
description: Créer une Landing Page
seo-description: null
page-status-flag: never-activated
uuid: fc0e9749-f44e-4aa0-bdfa-6f44ba570bea
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: editing-html-content
discoiquuid: 5f1e5886-628f-4c9e-80c1-d82feec23e8c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 36beb1eca48c698634c7548e0f931ab3fe17c021

---


# Créer une Landing Page{#creating-a-landing-page}

## A propos de la création des landing pages {#about-landing-pages-creation}

Ce cas d&#39;utilisation présente l&#39;utilisation du Digital Editor dans le cadre de la création d&#39;une Landing Page à partir de la console Adobe Campaign.

Avant de commencer le paramétrage de la Landing Page dans Adobe Campaign, vous devez avoir **à disposition un ou plusieurs modèles** représentant la ou les pages HTML.

L&#39;objectif principal de ce cas d&#39;utilisation est de faire correspondre les champs des formulaires de la Landing Page avec des champs métiers dans Adobe Campaign en utilisant les fonctionnalités du DCE.

## Création de la Landing Page {#creating-the-landing-page}

Pour créer une nouvelle Application Web de type Landing Page, respectez les étapes suivantes :

1. Accédez à l’ **[!UICONTROL Campaigns]** onglet et cliquez sur le **[!UICONTROL Web application]** lien, puis cliquez sur le **[!UICONTROL Create]** bouton.
1. Sélectionnez le **[!UICONTROL New landing page]** modèle et saisissez une étiquette, puis cliquez sur **[!UICONTROL Save]**.

   ![](assets/dce_uc1_newlandingpage.png)

1.  Cliquez sur l’ **[!UICONTROL Edit]** onglet.
1. Supprimez l&#39;activité **Fin**.
1. Add a **[!UICONTROL Page]** activity after the **[!UICONTROL Storage]** activity.
1. Modifiez l’activité **Page 2** , puis désélectionnez l’ **[!UICONTROL Activate outbound transitions]** option dans l’ **[!UICONTROL Properties]** onglet.

   ![](assets/dce_uc1_transition.png)

1. Enregistrez les modifications.

Vous obtiendrez ensuite le séquencement suivant :

![](assets/dce_uc1_edition_activity.png)

>[!NOTE]
>
>La création d&#39;une application web est présentée dans [cette section](../../web/using/creating-a-new-web-application.md).

## Etape 1 - Sélection et chargement de modèles {#step-1---selecting-and-loading-templates}

Dans cette section nous allons voir comment **importer un contenu HTML** pour chaque page de l&#39;application Web.

Un modèle doit contenir :

* un fichier **HTML** (obligatoire)
* un ou plusieurs fichiers **CSS** (facultatif)
* un ou plusieurs fichiers **image** (facultatif)

Pour charger le modèle dans la première page, respectez les étapes suivantes :

1. Ouvrez la première activité **[!UICONTROL Page]** de l&#39;application Web.
1. Sélectionnez **[!UICONTROL From a file]** pour récupérer votre modèle de contenu.

   ![](assets/dce_uc1_selectmodel.png)

1. Sélectionnez le fichier HTML à utiliser.
1. Cliquez sur **Ouvrir** afin de démarrer l&#39;import.

   Lors du chargement, la liste des fichiers chargés apparait. Le système d&#39;import vérifie que tous les fichiers liés au HTML sélectionné sont présents (CSS, images, etc.).

   Click the **[!UICONTROL Close]** button once the import has finished.

   ![](assets/dce_uc1_import.png)

   >[!CAUTION]
   >
   >Vous devez attendre d’avoir reçu le message suivant avant de fermer : **[!UICONTROL The external resources have been successfully published]** .

1.  Cliquez sur l’ **[!UICONTROL Properties]** onglet.
1. Enter a **label** for each page (for example: Page 1= Collect, Page 2=Thank you).

   ![](assets/dce_uc1_pagelabel.png)

Vous devez effectuer ces étapes pour chacune des pages insérées dans l&#39;application Web.

>[!CAUTION]
>
>**Le DCE exécute le code JavaScript de la page HTML chargée.** Il se peut que des erreurs JavaScript propres au modèle HTML soient remontées dans l&#39;interface Adobe Campaign. Ces erreurs ne concernent pas l&#39;éditeur. Pour vérifier qu&#39;il n&#39;y a aucune erreur dans les fichiers importés, il est conseillé de les tester dans un navigateur (Internet Explorer / FireFox / Chrome) avant d&#39;importer les fichiers dans le DCE.

## Etape 2 - Paramétrage du contenu {#step-2---configuring-the-content}

Dans cette section, nous allons ajuster le contenu importé puis associer les champs de la base de données avec le formulaire de la page web. L&#39;application Web créée précédemment est la suivante :

![](assets/dce_uc1_lp_enchainement.png)

### Modification du contenu {#modifying-content}

Nous allons d&#39;abord modifier les couleurs de la page. Pour cela :

1. Ouvrez la **[!UICONTROL Collection]** page.
1. Cliquez sur la zone d&#39;arrière-plan.
1. Cliquez sur la zone **Couleur de fond** dans la zone droite.
1. Sélectionnez une nouvelle couleur de fond dans le nuancier.
1. Validez le changement en cliquant sur **OK**

   ![](assets/dce_uc1_changecolor.png)

1. Reproduisez les mêmes étapes pour modifier la couleur du bouton

   ![](assets/dce_uc1_finalcolor.png)

### Association des champs du formulaire {#linking-form-fields}

Nous allons associer les champs proposés dans la page à des champs de la base de données, afin de stocker les informations renseignées.

1. Sélectionnez un champ du formulaire.
1. Edit the **[!UICONTROL Field]** section on right-hand side of the editor.
1. Sélectionnez le champ de la base de données que vous souhaitez associer au champ sélectionné.

   ![](assets/dce_uc1_mapping.png)

1. Reproduisez cette association pour chaque champ de la page.

Il est possible de rendre un champ obligatoire : par exemple, cliquez sur le champ **[!UICONTROL Email]** puis activez l&#39;option **Obligatoire**.

![](assets/dce_uc1_fieldmandatory.png)

### Création d&#39;un lien vers la page suivante {#creating-a-link-to-the-next-page}

This step is mandatory because it will allow the Web application to determine the sequence of the next steps: Saving the collected data in the database then displaying the next page (**Thank you** page).

1. Select the **[!UICONTROL Send it!]** button of the **[!UICONTROL Collection]** page.
1. Click the **[!UICONTROL Action]** drop-down menu.
1. Sélectionnez l’ **[!UICONTROL Next page]** action.

   ![](assets/dce_uc1_actionbouton.png)

### Insertion d&#39;un champ de personnalisation {#inserting-a-personalization-field}

Cette étape permet de personnaliser le contenu de la page de remerciements. Pour cela :

1. Ouvrez la **[!UICONTROL Thank you]** page.
1. Positionnez le curseur dans une zone de texte, là où vous souhaitez insérer le prénom du destinataire.
1. Sélectionnez **[!UICONTROL Personalization field]** dans le **[!UICONTROL Insert]** menu de la barre d’outils.
1. Sélectionnez le prénom.

   ![](assets/dce_uc1_persochamp.png)

Le champ de personnalisation s&#39;affiche sur fond jaune dans l&#39;éditeur.

![](assets/dce_uc1_edit_champperso.png)

## Etape 3 - Publication du contenu {#step-3---publishing-content}

Le contenu est publié à partir du tableau de bord de l&#39;application Web. Cliquez sur le **[!UICONTROL Publish]** bouton pour l’exécuter.

![](assets/dce_uc1_pub_dashboard.png)

Lors de la publication, un journal est affiché. Le système de mise en ligne analyse l&#39;intégralité des contenus présents dans l&#39;application Web.

![](assets/dce_uc1_pub_dashboard_journal.png)

>[!NOTE]
>
>Dans le journal de publication, les avertissements ou erreurs potentiels sont triés par activité.

Le formulaire est maintenant disponible : son URL est accessible dans le tableau de bord de l&#39;application et peut être proposée aux destinataires.
