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
>Dans les **[!UICONTROL Propriétés]** de diffusion, vérifiez que le mode **[!UICONTROL d’édition de]** contenu (dans l’onglet **[!UICONTROL Avancé]** ) est défini sur **[!UICONTROL DCE.]** Pour garantir le fonctionnement optimal de l’éditeur, reportez-vous aux bonnes pratiques [en matière de modification du](../../web/using/content-editing-best-practices.md)contenu.

## Etape 1 - Créer une diffusion {#step-1---creating-a-delivery}

Pour créer une remise, placez le curseur dans l’onglet **Campagnes** et cliquez sur **Livraisons**. Cliquez ensuite sur le bouton **Créer** au-dessus de la liste des livraisons existantes. For more on creating deliveries, refer to [this page](../../delivery/using/about-email-channel.md).

![](assets/delivery_step_1.png)

## Etape 2 - Sélectionner un modèle {#step-2---selecting-a-template}

Sélectionnez un modèle de remise, puis nommez votre remise. Ce nom ne sera visible que par les utilisateurs de la console Adobe Campaign et non par vos destinataires. Toutefois, cet en-tête s’affichera dans votre liste de remises. Cliquez sur **[!UICONTROL Continuer]**.

![](assets/dce_delivery_model.png)

## Etape 3 - Sélectionner un contenu {#step-3---selecting-a-content}

Le Digital Content Editor est livré avec plusieurs modèles d&#39;usine aux structures variables (colonnes, zones de textes, etc.).

Sélectionnez le modèle de contenu qui vous convient, puis cliquez sur le bouton **[!UICONTROL Commencer avec le contenu sélectionné]** afin d’afficher le modèle dans la diffusion créée.

![](assets/dce_select_model.png)

Vous pouvez également importer du contenu HTML créé en dehors d&#39;Adobe Campaign en sélectionnant l&#39;option **[!UICONTROL A partir d&#39;un fichier]**.

![](assets/dce_select_from_file_template.png)

Vous pouvez enregistrer ce contenu en tant que modèle pour une utilisation ultérieure. Une fois un modèle de contenu personnalisé créé, vous pouvez le prévisualiser dans la liste des modèles. For more on this, refer to [Template management](../../web/using/template-management.md).

>[!CAUTION]
>
>Si vous utilisez l&#39;**interface web d&#39;Adobe Campaign**, vous devez importer un fichier .zip comportant le contenu HTML et les images associées.

## Etape 4 - Concevoir le message {#step-4---designing-the-message}

* Afficher les nom et prénom de vos destinataires

   To insert the first and second names of your recipients into a text field in your delivery, click your chosen text field, then place your cursor where you want to display them. Click the first icon in the pop-up toolbar, then click **[!UICONTROL Personalization block]**. Select **[!UICONTROL Greetings]**, then click **[!UICONTROL OK]**.

   ![](assets/dce_personalizationblock_greetings.png)

* Insérer un lien sur une image

   To take delivery recipients to an external address via an image, click on the relevant image to display the pop-up toolbar, place the cursor on the first icon then click **[!UICONTROL Link to an external URL]**. Pour plus d’informations, voir [Ajout d’un lien](../../web/using/editing-content.md#adding-a-link).

   ![](assets/dce_externalpage.png)

   Saisissez l&#39;URL pour le lien dans le champ **URL** à l&#39;aide du format suivant **https://www.monURL.com**, puis confirmez.

   L&#39;adresse du lien est modifiable à tout moment dans la partie droite de la fenêtre.

* Insérer un lien sur du texte

   To integrate an external link into the text in your delivery, select some text or a block of text then click on the first icon in the pop-up toolbar. Click **[!UICONTROL Link to an external URL]**, enter the link address into the **[!UICONTROL URL]** field. Pour plus d’informations, voir [Ajout d’un lien](../../web/using/editing-content.md#adding-a-link).

   L&#39;adresse du lien est modifiable à tout moment dans la partie droite de la fenêtre.

   >[!CAUTION]
   >
   >Le texte saisi dans le champ **[!UICONTROL Libellé]** remplace le texte initial.

* Ajouter une page miroir

   Pour permettre à vos destinataires d&#39;accéder au contenu de votre diffusion sur un navigateur Web, il vous est possible d&#39;intégrer à votre diffusion un lien vers une page Web miroir.

   Cliquez sur le champ texte dans lequel vous souhaitez voir figurer le lien vers la page miroir. Cliquez sur la première icône de la barre d&#39;outils contextuelle, sélectionnez **[!UICONTROL Bloc de personnalisation]**, puis **[!UICONTROL Lien vers la page miroir (MirrorPage)]**. Validez en cliquant sur **[!UICONTROL Enregistrer]**.

   ![](assets/dce_mirrorpage.png)

   >[!CAUTION]
   >
   >Le libellé du bloc de personnalisation remplace automatiquement le texte intial inscrit dans votre diffusion.

* Intégrer un lien vers une application Web

   Digital Content Editor vous permet d’intégrer des liens vers des applications Web à partir de votre console Adobe Campaign, comme une page d’entrée ou une page de formulaire. Pour plus d&#39;informations, reportez-vous à la section [Lien vers une application](../../web/using/editing-content.md#link-to-a-web-application)Web.

   Sélectionnez un champ texte dans lequel figurera votre lien vers l&#39;application Web, puis cliquez sur la première icône. Choisissez **[!UICONTROL Lien vers une application Web]**, puis sélectionnez l&#39;application souhaitée en cliquant sur l&#39;icône située à la fin du champ **Application Web**.

   ![](assets/dce_webapp.png)

   Cliquez sur **Enregistrer** pour valider.

   >[!NOTE]
   >
   >Cette étape nécessite l&#39;enregistrement préalable d&#39;au moins une application Web. Vous trouverez ces informations dans l’onglet **[!UICONTROL Campagnes > Applications]** Web de votre console.

## Etape 5 - Enregistrer la diffusion {#step-5---saving-the-delivery}

Une fois le contenu intégré, enregistrez la diffusion en cliquant sur **Enregistrer**. Elle s’affichera désormais dans votre liste de livraisons, sous l’onglet **[!UICONTROL Campagnes > Livraisons]** .
