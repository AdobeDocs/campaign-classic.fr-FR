---
product: campaign
title: 'Cas d’utilisation : créer une diffusion e-mail'
description: 'Cas d’utilisation : créer une diffusion e-mail'
badge-v7: label="v7" type="Informative" tooltip="S’applique à Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="S’applique également à Campaign v8"
feature: Web Apps, Web Forms, Landing Pages, Email Design
exl-id: e2679f12-459b-466d-9c82-60a28363b104
source-git-commit: 668cee663890fafe27f86f2afd3752f7e2ab347a
workflow-type: tm+mt
source-wordcount: '799'
ht-degree: 79%

---

# Cas d’utilisation : créer une diffusion e-mail{#use-case-creating-an-email-delivery}



Dans ce cas d’utilisation, vous apprendrez à concevoir une diffusion par email à l’aide du Digital Content Editor (DCE) d’Adobe Campaign.

Notre objectif final est d&#39;obtenir une diffusion partant d&#39;un modèle personnalisé contenant :

* une adresse directe au destinataire (utilisant ses nom et prénom),
* deux types de liens vers une URL externe,
* une page miroir,
* un lien vers une application web.

>[!NOTE]
>
>Avant de commencer, vous devez avoir en votre possession au moins un **modèle HTML** prêt à accueillir le contenu de vos futures diffusions.
>
>Dans les **[!UICONTROL Propriétés]** de diffusion, vérifiez que le **[!UICONTROL Mode d’édition du contenu]** (dans l’onglet **[!UICONTROL Avancé]**) est défini sur **[!UICONTROL DCE]**. Pour garantir le fonctionnement optimal de l’éditeur, consultez les [Bonnes pratiques relatives à l’édition de contenu](content-editing-best-practices.md).

## Etape 1 - Créer une diffusion {#step-1---creating-a-delivery}

Pour créer une diffusion, placez le curseur dans l’onglet **Campagnes** et cliquez sur **Diffusions**. Cliquez ensuite sur le bouton **Créer** au-dessus de la liste des diffusions existantes. Pour plus d’informations sur la création de diffusions, consultez [cette page](../../delivery/using/about-email-channel.md).

![](assets/delivery_step_1.png)

## Etape 2 - Sélectionner un modèle {#step-2---selecting-a-template}

Sélectionnez un modèle de diffusion, puis nommez votre diffusion. Ce nom sera visible uniquement par les utilisateurs de la console Adobe Campaign et non par vos destinataires mais cet intitulé s&#39;affichera dans la liste de vos diffusions. Cliquez sur **[!UICONTROL Continuer]**.

![](assets/dce_delivery_model.png)

## Etape 3 - Sélectionner un contenu {#step-3---selecting-a-content}

Le Digital Content Editor est livré avec plusieurs modèles d&#39;usine aux structures variables (colonnes, zones de textes, etc.).

Sélectionnez le modèle de contenu qui vous convient, puis cliquez sur le bouton **[!UICONTROL Commencer avec le contenu sélectionné]** afin d’afficher le modèle dans la diffusion créée.

![](assets/dce_select_model.png)

Vous pouvez également importer du contenu HTML créé en dehors d&#39;Adobe Campaign en sélectionnant l&#39;option **[!UICONTROL A partir d&#39;un fichier]**.

![](assets/dce_select_from_file_template.png)

Il est possible d&#39;enregistrer ce contenu en tant que modèle pour le réutiliser ultérieurement. Lorsqu&#39;un modèle de contenu personnalisé est créé, son aperçu figure dans la liste des modèles. Voir à ce sujet la section [Gestion des modèles](template-management.md).

>[!CAUTION]
>
>Si vous utilisez l&#39;**interface web d&#39;Adobe Campaign**, vous devez importer un fichier .zip comportant le contenu HTML et les images associées.

## Etape 4 - Concevoir le message {#step-4---designing-the-message}

* Afficher les nom et prénom de vos destinataires

  Pour insérer les noms et prénoms de vos destinataires dans un champ de texte de votre diffusion, cliquez sur le champ de texte de votre choix, puis placez le curseur à l&#39;endroit où vous souhaitez les afficher. Cliquez sur la première icône de la barre d’outils contextuelle, puis cliquez sur **[!UICONTROL Bloc de personnalisation]**. Sélectionner **[!UICONTROL Salutations]**, puis cliquez sur **[!UICONTROL OK]**.

  ![](assets/dce_personalizationblock_greetings.png)

* Insérer un lien sur une image

  Afin de permettre aux destinataires de vos diffusions de se rendre sur une adresse externe depuis une image, cliquez sur l’image concernée afin d’afficher la barre d’outils pop-up, positionnez le curseur sur la première icône, puis cliquez sur **[!UICONTROL Lien vers une URL externe]**. Voir à ce sujet la section [Ajouter un lien](editing-content.md#adding-a-link).

  ![](assets/dce_externalpage.png)

  Saisissez l&#39;URL pour le lien dans le champ **URL** à l&#39;aide du format suivant **https://www.monURL.com**, puis confirmez.

  L&#39;adresse du lien est modifiable à tout moment dans la partie droite de la fenêtre.

* Insérer un lien sur du texte

  Pour intégrer un lien externe dans le texte de votre diffusion, sélectionnez du texte ou un bloc de texte, puis cliquez sur la première icône de la barre d&#39;outils contextuelle. Cliquez sur **[!UICONTROL Lien vers une URL externe]**, saisissez l’adresse du lien dans la variable **[!UICONTROL URL]** champ . Pour plus d’informations, voir [Ajout d’un lien](editing-content.md#adding-a-link).

  L&#39;adresse du lien est modifiable à tout moment dans la partie droite de la fenêtre.

  >[!CAUTION]
  >
  >Le texte saisi dans le champ **[!UICONTROL Libellé]** remplace le texte initial.

* Ajouter une page miroir

  Pour permettre à vos destinataires d&#39;accéder au contenu de votre diffusion sur un navigateur Web, il vous est possible d&#39;intégrer à votre diffusion un lien vers une page Web miroir.

  Cliquez sur le champ de texte dans lequel vous souhaitez voir le lien publié. Cliquez sur la première icône de la barre d’outils contextuelle, puis sélectionnez **[!UICONTROL Bloc de personnalisation]**, puis **[!UICONTROL Lien vers la page miroir (MirrorPage)]**. Cliquez sur **[!UICONTROL Enregistrer]** pour confirmer.

  ![](assets/dce_mirrorpage.png)

  >[!CAUTION]
  >
  >Le libellé du bloc de personnalisation remplace automatiquement le texte intial inscrit dans votre diffusion.

* Intégrer un lien vers une application Web

  Le Digital Content Editor vous permet d&#39;intégrer des liens vers les applications Web de votre console Adobe Campaign, telles qu&#39;une landing page ou une page de formulaire. Voir à ce sujet la section [Lien vers une application web](editing-content.md#link-to-a-web-application).

  Sélectionnez un champ texte pour votre lien vers une application Web, puis cliquez sur la première icône. Choisir **[!UICONTROL Lien vers une application web]**, puis sélectionnez l’application souhaitée en cliquant sur l’icône située à la fin de la **Application web** champ .

  ![](assets/dce_webapp.png)

  Cliquez sur **Enregistrer** pour valider.

  >[!NOTE]
  >
  >Cette étape nécessite l&#39;enregistrement préalable d&#39;au moins une application web. Vous trouverez ces informations dans l’onglet **[!UICONTROL Campagnes > Applications web]** de votre console.

## Etape 5 - Enregistrer la diffusion {#step-5---saving-the-delivery}

Une fois le contenu intégré, enregistrez la diffusion en cliquant sur **Enregistrer**. Elle s’affichera désormais dans votre liste de diffusions, sous l’onglet **[!UICONTROL Campagnes > Diffusions]**.
