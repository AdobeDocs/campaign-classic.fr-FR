---
title: '"Cas pratique : création d''une diffusion email"'
seo-title: '"Cas pratique : création d''une diffusion email"'
description: '"Cas pratique : création d''une diffusion email"'
seo-description: null
page-status-flag: never-activated
uuid: 7cd6329c-63d5-4cf0-9451-f0b4c2eaf0dd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: editing-html-content
discoiquuid: 4ec34980-62a2-47b9-b103-de4290925624
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 36beb1eca48c698634c7548e0f931ab3fe17c021

---


# Cas pratique : création d&#39;une diffusion email{#use-case-creating-an-email-delivery}

Dans ce cas d’utilisation, vous apprendrez à concevoir une diffusion par courrier électronique à l’aide d’Adobe Campaign Digital Content Editor (DCE).

Notre objectif final est d&#39;obtenir une diffusion partant d&#39;un modèle personnalisé contenant :

* une adresse directe au destinataire (utilisant ses nom et prénom),
* deux types de liens vers une URL externe,
* une page miroir,
* un lien vers une application web.

>[!NOTE]
>
>Avant de commencer, vous devez avoir en votre possession au moins un **modèle HTML** prêt à accueillir le contenu de vos futures diffusions.
>
>Dans la remise **[!UICONTROL Properties]** , assurez-vous que le paramètre **[!UICONTROL Content editing mode]** (dans l’ **[!UICONTROL Advanced]** onglet) est défini sur **[!UICONTROL DCE]**. Pour garantir le fonctionnement optimal de l’éditeur, reportez-vous aux bonnes pratiques [en matière de modification du](../../web/using/content-editing-best-practices.md)contenu.

## Etape 1 - Créer une diffusion {#step-1---creating-a-delivery}

Pour créer une remise, placez le curseur dans l’onglet **Campagnes** et cliquez sur **Livraisons**. Cliquez ensuite sur le bouton **Créer** au-dessus de la liste des livraisons existantes. For more on creating deliveries, refer to [this page](../../delivery/using/about-email-channel.md).

![](assets/delivery_step_1.png)

## Etape 2 - Sélectionner un modèle {#step-2---selecting-a-template}

Select a delivery template, then name your delivery. This name will only be visible to users of the Adobe Campaign console and not by your recipients, however this heading will be displayed in your list of deliveries. Click **[!UICONTROL Continue]**.

![](assets/dce_delivery_model.png)

## Etape 3 - Sélectionner un contenu {#step-3---selecting-a-content}

Le Digital Content Editor est livré avec plusieurs modèles d&#39;usine aux structures variables (colonnes, zones de textes, etc.).

Select the content template that you want to use, then click the **[!UICONTROL Start with the selected content]** button to display the template in the created delivery.

![](assets/dce_select_model.png)

You can also import an HTML content created outside of Adobe Campaign by selecting **[!UICONTROL From a file]**.

![](assets/dce_select_from_file_template.png)

Vous pouvez enregistrer ce contenu en tant que modèle pour une utilisation ultérieure. Une fois un modèle de contenu personnalisé créé, vous pouvez le prévisualiser dans la liste des modèles. For more on this, refer to [Template management](../../web/using/template-management.md).

>[!CAUTION]
>
>Si vous utilisez l&#39;**interface web d&#39;Adobe Campaign**, vous devez importer un fichier .zip comportant le contenu HTML et les images associées.

## Etape 4 - Concevoir le message {#step-4---designing-the-message}

* Afficher les nom et prénom de vos destinataires

   To insert the first and second names of your recipients into a text field in your delivery, click your chosen text field, then place your cursor where you want to display them. Click the first icon in the pop-up toolbar, then click **[!UICONTROL Personalization block]**. Sélectionnez **[!UICONTROL Greetings]**, puis cliquez sur **[!UICONTROL OK]**.

   ![](assets/dce_personalizationblock_greetings.png)

* Insérer un lien sur une image

   Pour envoyer les destinataires à une adresse externe via une image, cliquez sur l’image appropriée pour afficher la barre d’outils contextuelle, placez le curseur sur la première icône, puis cliquez **[!UICONTROL Link to an external URL]**. Pour plus d’informations, voir [Ajout d’un lien](../../web/using/editing-content.md#adding-a-link).

   ![](assets/dce_externalpage.png)

   Saisissez l&#39;URL pour le lien dans le champ **URL** à l&#39;aide du format suivant **https://www.monURL.com**, puis confirmez.

   L&#39;adresse du lien est modifiable à tout moment dans la partie droite de la fenêtre.

* Insérer un lien sur du texte

   Pour intégrer un lien externe au texte dans votre diffusion, sélectionnez du texte ou un bloc de texte, puis cliquez sur la première icône de la barre d’outils contextuelle. Cliquez sur **[!UICONTROL Link to an external URL]**, entrez l’adresse du lien dans le **[!UICONTROL URL]** champ. Pour plus d’informations, voir [Ajout d’un lien](../../web/using/editing-content.md#adding-a-link).

   L&#39;adresse du lien est modifiable à tout moment dans la partie droite de la fenêtre.

   >[!CAUTION]
   >
   >The text entered in the **[!UICONTROL Label]** field replaces the original text.

* Ajouter une page miroir

   Pour permettre à vos destinataires d&#39;accéder au contenu de votre diffusion sur un navigateur Web, il vous est possible d&#39;intégrer à votre diffusion un lien vers une page Web miroir.

   Cliquez sur le champ de texte dans lequel vous souhaitez afficher le lien publié. Cliquez sur la première icône de la barre d’outils contextuelle, sélectionnez **[!UICONTROL Personalization block]**, puis **[!UICONTROL Link to Mirror Page (MirrorPage)]**. Cliquez sur **[!UICONTROL Save]** pour confirmer.

   ![](assets/dce_mirrorpage.png)

   >[!CAUTION]
   >
   >Le libellé du bloc de personnalisation remplace automatiquement le texte intial inscrit dans votre diffusion.

* Intégrer un lien vers une application Web

   Digital Content Editor vous permet d’intégrer des liens vers des applications Web à partir de votre console Adobe Campaign, comme une page d’entrée ou une page de formulaire. Pour plus d&#39;informations, reportez-vous à la section [Lien vers une application](../../web/using/editing-content.md#link-to-a-web-application)Web.

   Sélectionnez un champ de texte pour votre lien vers une application Web, puis cliquez sur la première icône. Choisissez **[!UICONTROL Link to a Web application]**, puis sélectionnez une application en cliquant sur l’icône à la fin du champ Application **** Web.

   ![](assets/dce_webapp.png)

   Cliquez sur **Enregistrer** pour valider.

   >[!NOTE]
   >
   >Cette étape nécessite l&#39;enregistrement préalable d&#39;au moins une application Web. Vous trouverez ces informations dans l&#39; **[!UICONTROL Campaigns > Web applications]** onglet de votre console.

## Etape 5 - Enregistrer la diffusion {#step-5---saving-the-delivery}

Une fois le contenu intégré, enregistrez la diffusion en cliquant sur **Enregistrer**. Il s’affiche désormais dans votre liste de livraisons, dans l’ **[!UICONTROL Campaigns > Deliveries]** onglet.
