---
title: Publier sur Facebook
seo-title: Publier sur Facebook
description: Publier sur Facebook
seo-description: null
page-status-flag: never-activated
uuid: f15170fa-0e7d-4913-81d6-0072c1ece482
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: social
content-type: reference
topic-tags: publishing-on-facebook-twitter
discoiquuid: 335cf2de-1874-4e48-9538-f0937641cf96
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 963aaa81971a8883b944bfcf4d1a00d729627916

---


# Publier sur Facebook{#publishing-on-facebook}

Une fois le paramétrage effectué, Social Marketing permet d&#39;envoyer des publications sur les murs de vos pages Facebook.

## Limitations {#limitations}

Les limitations suivantes sont des contraintes inhérentes à Facebook.

* La longueur du message ne peut pas dépasser 1000 caractères.
* Le format HTML n&#39;est pas supporté.

## Créer la diffusion {#creating-the-delivery}

Créez une remise à l’aide du modèle de **[!UICONTROL Publish to a brand page]** remise.

![](assets/social_facebook_delivery_001.png)

## Choisir la cible principale {#selecting-the-main-target}

Vous devez sélectionner la ou les pages sur lesquelles vous souhaitez envoyer votre publication.

1. Cliquez sur le **[!UICONTROL To]** lien.

   ![](assets/social_facebook_delivery_010.png)

1. Cliquez sur le **[!UICONTROL Add]** bouton.

   ![](assets/social_facebook_delivery_011.png)

1. Sélectionner **[!UICONTROL A Facebook page]**.

   ![](assets/social_facebook_delivery_012.png)

1. Dans le **[!UICONTROL Folder]** champ, sélectionnez le dossier de service qui contient la page Facebook. Par défaut, les pages sont stockées à la racine du dossier du **[!UICONTROL Facebook]** service. Sélectionnez ensuite la page Facebook sur laquelle vous souhaitez publier du contenu.

   ![](assets/social_facebook_delivery_013.png)

## Choisir la cible du BAT {#selecting-the-proof-target}

L’ **[!UICONTROL Target of the proofs]** onglet vous permet de définir la page Facebook que vous souhaitez utiliser pour tester les remises avant de les envoyer.  Nous vous recommandons de créer une page Facebook privée dédiée à cet effet. Pour plus d’informations sur la création d’une page Facebook privée, voir [Création d’une page](../../social/using/publishing-on-facebook-walls.md#creating-a-test-facebook-page)Facebook de test. Pour sélectionner la cible d’épreuve, appliquez les mêmes étapes que pour la cible principale : [Sélection de la cible](#selecting-the-main-target)principale.

![](assets/social_facebook_delivery_004.png)

>[!NOTE]
>
>Si vous utilisez la même page de test Facebook pour toutes les remises, vous pouvez enregistrer la cible de validation dans le modèle de **[!UICONTROL Publish to a brand page]** remise, accessible via le **[!UICONTROL Resources > Templates > Delivery templates]** noeud. La cible d’épreuve sera saisie par défaut pour chaque nouvelle remise.

## Définir l&#39;audience {#defining-the-audience}

Si vous souhaitez utiliser des segments locaux afin d&#39;affiner le type de public qui sera autorisé à visualiser la publication, nous vous conseillons de créer une page Facebook par segment (par exemple : Adobe Campaign Paris, Adobe Campaign London, etc.).

Cependant, il est également possible d’utiliser les filtres d’audience utilisés par Facebook. L’ **[!UICONTROL Audience]** onglet de **[!UICONTROL Select target window]** propose quatre filtres :

* **[!UICONTROL Country]**
* **[!UICONTROL Regions]**
* **[!UICONTROL Cities]**
* **[!UICONTROL Languages]**

>[!IMPORTANT]
>
>Utilisez cette fonction avec soin. Dans les rapports de diffusion, l’ **[!UICONTROL Number of fans]** indicateur ne tient pas compte de ces filtres Facebook.
>
>Facebook peut être amené à modifier la liste des filtres d&#39;audience ainsi que leurs valeurs.

## Définir le contenu du message {#defining-message-content}

Select the type of publication using the **[!UICONTROL Content type]** drop-down menu.

![](assets/social_facebook_delivery_006.png)

Les types de diffusion suivants sont proposés :

* a **[!UICONTROL Status]**
* a **[!UICONTROL Status with a link]**
* a **[!UICONTROL Status with a YouTube link]**
* a **[!UICONTROL Photo album]**

### Publier un statut {#publishing-a-status}

Une diffusion de type statut contient uniquement du texte, comme dans l&#39;exemple ci-dessous :

![](assets/social_create_facebook_wall_post_004.png)

Saisissez le statut de la publication dans la zone de saisie.

![](assets/social_facebook_delivery_015.png)

### Publier un statut avec un lien {#publishing-a-status-with-a-link}

Une diffusion de type statut avec un lien peut contenir du texte, une image et un lien. Les correspondances entre les champs de l&#39;écran d&#39;édition de la diffusion et la publication finale sur Facebook sont présentées ci-dessous :

![](assets/social_facebook_delivery_007.png)

Renseignez les différents champs proposés :

>[!IMPORTANT]
>
>Toutes les URL doivent commencer par **&quot;http://&quot;** ou **&quot;https://&quot;**.

1. In the **[!UICONTROL Status]** field, enter the text which will be displayed under the name of the page.
1. In the **[!UICONTROL Name]** field, enter the publication title.
1. In the **[!UICONTROL Link]** field, enter the URL that the publication points to.

   >[!NOTE]
   >
   >If you want to add the **[!UICONTROL Link]** field to the URL of a Facebook application to promote it, we recommend that you adapt it to smartphone display criteria:
   >
   >1. Select the Facebook application [https://developers.facebook.com/apps](https://developers.facebook.com/apps), and select the **[!UICONTROL Settings > Basic]** tab.
   >1. Enter the **[!UICONTROL Namespace]** field.
   >1. Enter the **[!UICONTROL Mobile Site URL]** field: when a user clicks the publication link on their smartphone, they will automatically be redirected by Facebook to the URL defined in this field.
   >1. Construisez votre application web de manière à personnaliser l&#39;affichage de l&#39;application Facebook en fonction de l&#39;appareil utilisé (smartphone ou PC).
   >1. Go to the **[!UICONTROL Link]** field of the publication via the Adobe Campaign console, enter the URL of the **[!UICONTROL Canvas page]** field.


1. Dans le champ **[!UICONTROL Image]**, saisissez l&#39;URL de l&#39;image qui apparaîtra sur le côté gauche de la publication.

   >[!IMPORTANT]
   >
   >L&#39;image doit être hébergée sur un site Internet public pour que Facebook puisse la télécharger.

1. In the **[!UICONTROL Caption]** field, enter the text that will appear at the end of the publication.
1. Dans le champ **[!UICONTROL Description]**, saisissez le texte qui apparaîtra sous le titre.

![](assets/social_facebook_delivery_005.png)

### Publier un statut avec un lien YouTube {#publishing-a-status-with-a-youtube-link}

Ce type de contenu permet de publier un lien vers une vidéo YouTube. Comme pour un statut avec un lien classique, vous avez la possibilité de définir un statut, un nom, une légende, une description, et un lien additionnel. L&#39;image est automatiquement ajoutée par Facebook. Les correspondances entre les champs de l&#39;écran d&#39;édition de la diffusion et la publication finale sur Facebook sont présentées ci-dessous :

![](assets/social_facebook_delivery_youtube_1.png)

Renseignez les différents champs proposés :

>[!CAUTION]
>
>Toutes les URL doivent commencer par **&quot;http://&quot;** ou **&quot;https://&quot;**.

1. In the **[!UICONTROL Status]** field, enter the text which will be displayed under the name of the page.
1. In the **[!UICONTROL Name]** field, enter the publication title.
1. Dans le **[!UICONTROL Video code]** champ, saisissez le code de la vidéo YouTube. Par exemple, pour le lien &quot;https://www.youtube.com/watch?v=abc123456&#39;&quot;, le code vidéo sera &quot;abc123456&quot;.
1. In the **[!UICONTROL Caption]** field, enter the text that will appear at the end of the publication.
1. Dans le champ **[!UICONTROL Description]**, saisissez le texte qui apparaîtra sous le titre.

![](assets/social_facebook_delivery_youtube.png)

### Publier un album photo {#publishing-a-photo-album}

Ce type de contenu permet de publier un album photo. Vous avez la possibilité d&#39;ajouter un nom et une description pour l&#39;album ainsi qu&#39;une légende pour chaque photo. Les correspondances entre les champs de l&#39;écran d&#39;édition de la diffusion et la publication finale sur Facebook sont présentées ci-dessous :

![](assets/social_facebook_delivery_photos_1.png)

Renseignez les différents champs proposés :

1. Start by entering the **[!UICONTROL Album name]**.
1. Saisissez ensuite la **[!UICONTROL Description]** qui apparaîtra au-dessus des photos.
1. To add a photo, click the **[!UICONTROL Add]** button, select the photo and click **[!UICONTROL Open]**.
1. Pour chaque photo, vous avez la possibilité d&#39;ajouter une légende.

![](assets/social_facebook_delivery_photos.png)

## Visualiser l&#39;aperçu {#previewing}

The **[!UICONTROL Preview]** tab lets you view the rendering of the publication.

1.  Cliquez sur l’ **[!UICONTROL Preview]** onglet.
1. Cliquez sur le menu **[!UICONTROL Test personalization]** déroulant et sélectionnez **[!UICONTROL Service]**.
1. In the **[!UICONTROL Folder]** field, select the service folder which contains your Facebook pages. Par défaut, les pages sont stockées à la racine du dossier du **[!UICONTROL Facebook]** service.
1. Sélectionnez la page Facebook sur laquelle vous souhaitez tester l&#39;aperçu.

![](assets/social_facebook_delivery_008.png)

>[!NOTE]
>
>L’aperçu peut différer légèrement de la publication Facebook finale. Nous vous recommandons vivement d&#39;envoyer une preuve avant la livraison finale pour un rendu exact de la publication. Reportez-vous à [Envoi de la preuve](#sending-the-proof).

## Configurer le tracking {#configuring-tracking}

Tracking can be viewed in the delivery reports and in the **[!UICONTROL Edit > Tracking]** tab of the delivery and the service.

Les clics sur l’URL contenue dans la diffusion sont mesurés par Adobe Campaign. Le nombre de clics sur le **[!UICONTROL Like]** bouton, le nombre de commentaires et le nombre de fans sont mesurés par Facebook.

La configuration du tracking s’effectue de la même manière que pour une diffusion email. Voir à ce sujet [cette section](../../delivery/using/monitoring-a-delivery.md).

>[!NOTE]
>
>In the **[!UICONTROL Publish to a brand page]** delivery template, tracking is enabled by default.

## Envoyer le BAT {#sending-the-proof}

Nous vous recommandons vivement d&#39;envoyer une preuve de votre publication avant la livraison finale afin de voir le rendu exact de la publication sur une page de test Facebook privée. Pour plus d’informations sur la création d’une page de test Facebook privée, voir [Création d’une page](../../social/using/publishing-on-facebook-walls.md#creating-a-test-facebook-page)de test Facebook. Les étapes de sélection de l&#39;épreuve cible sont détaillées dans [Sélection de l&#39;épreuve cible](#selecting-the-proof-target).

L’envoi du BAT s’effectue de la même manière que pour une diffusion email. Reportez-vous à [cette section](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

## Envoyer le message {#sending-the-message}

1. Once the content is approved, click the **[!UICONTROL Send]** button.
1. Sélectionnez **[!UICONTROL Deliver as soon as possible]** puis cliquez sur le **[!UICONTROL Analyze]** bouton.

   >[!NOTE]
   >
   >The **[!UICONTROL Postpone the delivery]** option lets you postpone delivery to a later date.

   ![](assets/social_facebook_delivery_009.png)

1. Une fois l&#39;analyse terminée, vérifiez le résultat de l&#39;analyse.
1. Cliquez sur **[!UICONTROL Confirm delivery]**, puis sur **[!UICONTROL Yes]**.

   ![](assets/social_facebook_delivery_016.png)

