---
product: campaign
title: Créer une landing page
description: Créer une landing page
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
feature: Landing Pages
exl-id: 71c737c2-b0d6-4ae8-a5df-28a08dff82d7
TQID: https://experienceleague.adobe.com/-IwRJsJKykm7pbLwdlXjLa1YP3TuJX2zvbrJGd2zLto
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
topic_v2:
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
subfeature_v2:
  - id: f391046b-0cf3-4e76-bd3b-97fe06654506
  - id: ed29abcd-b6a8-4d4b-ab8b-b7e746973281
  - id: d7be2b01-dc9c-40f7-aace-a151707504ed
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 782
ht-degree: 83%

---

# Créer une landing page{#creating-a-landing-page}



## À propos de la création des landing pages {#about-landing-pages-creation}

Ce cas d&#39;utilisation présente l&#39;utilisation du Digital Editor dans le cadre de la création d&#39;une Landing Page à partir de la console Adobe Campaign.

Avant de commencer le paramétrage de la Landing Page dans Adobe Campaign, vous devez avoir **à disposition un ou plusieurs modèles** représentant la ou les pages HTML.

L&#39;objectif principal de ce cas d&#39;utilisation est de faire correspondre les champs des formulaires de la Landing Page avec des champs métiers dans Adobe Campaign en utilisant les fonctionnalités du DCE.

## Création de la Landing Page {#creating-the-landing-page}

Pour créer une nouvelle Application Web de type Landing Page, respectez les étapes suivantes :

1. Dans l’onglet **[!UICONTROL Campagnes]**, cliquez sur le lien **[!UICONTROL Application Web]**, puis sur le bouton **[!UICONTROL Créer]**.
1. Sélectionnez le modèle **[!UICONTROL Nouvelle landing page]**, saisissez un libellé, puis cliquez sur **[!UICONTROL Enregistrer]**.

   ![](assets/dce_uc1_newlandingpage.png)

1. Cliquez sur l&#39;onglet **[!UICONTROL Edition]**.
1. Supprimez l&#39;activité **Fin**.
1. Ajoutez une activité **[!UICONTROL Page]** à la suite de l’activité **[!UICONTROL Enregistrement]**.
1. Editez l&#39;activité **Page 2**, puis décochez l&#39;option **[!UICONTROL Activer les transitions sortantes]** dans l&#39;onglet **[!UICONTROL Propriétés]**.

   ![](assets/dce_uc1_transition.png)

1. Enregistrez les modifications.

Vous obtenez alors le séquencement suivant :

![](assets/dce_uc1_edition_activity.png)

>[!NOTE]
>
>La création d&#39;une application web est présentée dans [cette section](creating-a-new-web-application.md).

## Etape 1 - Sélection et chargement de modèles {#step-1---selecting-and-loading-templates}

Dans cette section nous allons voir comment **importer un contenu HTML** pour chaque page de l&#39;application Web.

Un modèle doit contenir :

* un fichier **HTML** (obligatoire)
* un ou plusieurs fichiers **CSS** (facultatif)
* un ou plusieurs fichiers **image** (facultatif)

Pour charger le modèle dans la première page, respectez les étapes suivantes :

1. Ouvrez la première activité **[!UICONTROL Page]** de l&#39;application Web.
1. Sélectionnez **[!UICONTROL A Partir d&#39;un fichier]** comme choix de modèles de contenus disponibles.

   ![](assets/dce_uc1_selectmodel.png)

1. Sélectionnez le fichier HTML à utiliser.
1. Cliquez sur **Ouvrir** afin de démarrer l&#39;import.

   Lors du chargement, la liste des fichiers partagés s&#39;affiche. Le système d’importation vérifie que tous les fichiers liés à l’HTML sélectionnée sont bien présents (CSS, images, etc.).

   Cliquez sur le bouton **[!UICONTROL Fermer]** lorsque l&#39;import est terminé.

   ![](assets/dce_uc1_import.png)

   >[!CAUTION]
   >
   >Vous devez attendre d’avoir reçu le message suivant avant de procéder à la fermeture : **[!UICONTROL La mise en ligne des ressources externes est terminée]**.

1. Cliquez sur l&#39;onglet **[!UICONTROL Propriétés]**.
1. Saisissez un **libellé** pour chaque page (par exemple : Page 1 = Collecte, Page 2 = Remerciements).

   ![](assets/dce_uc1_pagelabel.png)

Vous devez effectuer ces étapes pour chacune des pages insérées dans l&#39;application Web.

>[!CAUTION]
>
>**Le DCE exécute le code JavaScript pour la page HTML chargée.** Erreurs JavaScript du modèle HTML pouvant apparaître dans l’interface d’Adobe Campaign. Ces erreurs ne sont pas liées à l’éditeur. Pour vérifier qu’il n’y a aucune erreur dans les fichiers importés, il est recommandé de les tester dans un navigateur web avant d’importer les fichiers dans le DCE.

## Etape 2 - Paramétrage du contenu {#step-2---configuring-the-content}

Dans cette section, nous allons ajuster le contenu importé et associer les champs de la base de données au formulaire de la page web. L&#39;application Web créée précédemment est la suivante :

![](assets/dce_uc1_lp_enchainement.png)

### Modification du contenu {#modifying-content}

Commençons par modifier les couleurs de la page. Pour cela :

1. Ouvrez la page **[!UICONTROL Collecte]**.
1. Cliquez sur la zone d&#39;arrière-plan.
1. Cliquez sur la zone **Couleur d’arrière-plan** dans la zone droite.
1. Sélectionnez une nouvelle couleur d’arrière-plan dans le nuancier.
1. Validez le changement en cliquant sur **OK**

   ![](assets/dce_uc1_changecolor.png)

1. Reproduisez les mêmes étapes pour modifier la couleur du bouton

   ![](assets/dce_uc1_finalcolor.png)

### Association des champs du formulaire {#linking-form-fields}

Nous allons associer les champs proposés dans la page à des champs de la base de données, afin de stocker les informations renseignées.

1. Sélectionnez un champ du formulaire.
1. Editez la section **[!UICONTROL Champ]** dans la zone droite de l&#39;éditeur.
1. Sélectionnez le champ de la base de données que vous souhaitez associer au champ sélectionné.

   ![](assets/dce_uc1_mapping.png)

1. Reproduisez cette association pour chaque champ de la page.

Il est possible de rendre un champ obligatoire : par exemple, cliquez sur le champ **[!UICONTROL Email]** puis activez l&#39;option **Obligatoire**.

![](assets/dce_uc1_fieldmandatory.png)

### Création d&#39;un lien vers la page suivante {#creating-a-link-to-the-next-page}

Cette étape est obligatoire car elle va permettre à l’application Web de déterminer le déroulement des étapes : enregistrer les données collectées dans la base puis afficher la page suivante (page **Remerciements**).

1. Sélectionnez l’option **[!UICONTROL Envoyer !]** de la page **[!UICONTROL Collection]**.
1. Cliquez dans le menu déroulant **[!UICONTROL Action]**.
1. Sélectionnez l&#39;action **[!UICONTROL Page Suivante]**.

   ![](assets/dce_uc1_actionbouton.png)

### Insertion d&#39;un champ de personnalisation {#inserting-a-personalization-field}

Cette étape permet de personnaliser la page de remerciement. Pour cela :

1. Ouvrez la page **[!UICONTROL Remerciements]**.
1. Positionnez le curseur dans une zone de texte, là où vous souhaitez insérer le prénom du destinataire.
1. Sélectionnez **[!UICONTROL Champ de personnalisation]** dans le menu **[!UICONTROL Insérer]** de la barre d&#39;outils.
1. Sélectionnez le prénom.

   ![](assets/dce_uc1_persochamp.png)

Le champ de personnalisation s’affiche sur un arrière-plan jaune dans l’éditeur.

![](assets/dce_uc1_edit_champperso.png)

## Etape 3 - Publication du contenu {#step-3---publishing-content}

Le contenu est publié à partir du tableau de bord de l’application web. Cliquez sur le bouton **[!UICONTROL Publier]** pour effectuer la publication.

![](assets/dce_uc1_pub_dashboard.png)

Lors de la publication, un journal s’affiche. Le système de publication analyse l&#39;ensemble du contenu présent dans l&#39;application Web

![](assets/dce_uc1_pub_dashboard_journal.png)

>[!NOTE]
>
>Dans le log de publication, les avertissements ou erreurs potentiels sont triés par activité.

Le formulaire est maintenant disponible : son URL est accessible dans le tableau de bord de l&#39;application et peut être proposée aux destinataires.
