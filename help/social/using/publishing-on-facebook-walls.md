---
product: campaign
title: Publication sur les murs Facebook
description: Publication sur les murs Facebook
audience: social
content-type: reference
topic-tags: configuration
exl-id: 2135a836-245f-406e-b351-c27d38e0f9fd
source-git-commit: b5334de18eca8fc1147ae0c42fe23a6932bf71d2
workflow-type: tm+mt
source-wordcount: '1029'
ht-degree: 100%

---

# Publication sur les murs Facebook{#publishing-on-facebook-walls}

![](../../assets/v7-only.svg)

Pour qu&#39;Adobe Campaign puisse envoyer des publications sur les murs de vos pages Facebook, vous devez déléguer, à Adobe Campaign, les droits d&#39;écriture sur ces pages. Les étapes de paramétrage sont les suivantes :

1. Créez un compte Facebook et une ou plusieurs pages.
1. Créez une page Facebook de test dédiée à l&#39;envoi de BAT.
1. Créez une application Facebook.
1. Renseignez les paramètres de l&#39;application Facebook dans Adobe Campaign, dans le compte externe **[!UICONTROL Routage Facebook]**.

## Conditions préalables requises {#prerequisites}

Vous devez tout d&#39;abord créer un compte Facebook ainsi qu&#39;une ou plusieurs pages, sur lesquelles vous enverrez vos publications.

* Pour créer un compte Facebook, suivez le lien : [https://www.facebook.com](https://www.facebook.com)
* Pour créer une page Facebook, suivez le lien : [ https://www.facebook.com/pages/create](https://www.facebook.com/pages/create).

   Il est conseillé d&#39;utiliser le même compte Facebook pour administrer toutes vos pages. Cela permettra de ne créer qu&#39;une seule application Facebook et de ne configurer qu&#39;un seul compte externe pour écrire sur n&#39;importe laquelle des pages du compte Facebook.

   ![](assets/social_diagram_fb_external_account.png)

## Création d’une page Facebook de test {#creating-a-test-facebook-page}

Il est recommandé de créer une page Facebook privée sur laquelle vous enverrez des BAT de vos publications (pour en savoir plus, consultez [cette section](../../social/using/publishing-on-facebook.md#sending-the-proof)).

1. Connectez-vous au compte Facebook à partir duquel vous administrez vos pages.
1. Créez une nouvelle page Facebook.
1. Cliquez sur le bouton **[!UICONTROL Paramètres]**, en haut à droite.
1. Dans l&#39;onglet **[!UICONTROL Général]**, modifiez les paramètres de visibilité de la page : cochez la case **[!UICONTROL Publication de la page annulée]**.
1. Cliquez sur le bouton **[!UICONTROL Enregistrer les modifications]**.

![](assets/social_facebook_test_page.png)

## Création d’une application Facebook {#creating-a-facebook-application}

Pour qu&#39;Adobe Campaign puisse publier sur les murs de vos pages, vous devez créer une application Facebook. Les étapes sont les suivantes :

1. Connectez-vous au compte Facebook à partir duquel vous administrez vos pages.
1. Dans la barre d&#39;adresse de votre navigateur Internet, saisissez l&#39;adresse [https://developers.facebook.com/apps](https://developers.facebook.com/apps).

   >[!CAUTION]
   >
   >En fonction du type de compte, une ou plusieurs autorisations peuvent vous être demandées.
   >
   >Pour créer une application Facebook, vous devez disposer d&#39;un compte Facebook **vérifié**.

1. Cliquez sur le bouton **[!UICONTROL Ajouter une app]** en haut à droite de la page. Saisissez le nom de l&#39;application et un email de contact. Effectuez ensuite le contrôle de sécurité.

   ![](assets/social_create_facebook_app_002.png)

1. Sous **[!UICONTROL Paramètres > Général]**, cliquez sur **[!UICONTROL Ajouter une plateforme]** et sélectionnez le type **[!UICONTROL Jeux Web Facebook]**.

   ![](assets/social_create_facebook_app_003.png)

1. Dans la section **[!UICONTROL Produits]**, dans le menu de gauche, vérifiez que le produit **[!UICONTROL Connexion Facebook]** s’affiche. Si ce n’est pas le cas, ajoutez un nouveau produit et sélectionnez **[!UICONTROL Connexion Facebook]**.

   ![](assets/social_create_facebook_app_003bis.png)

1. Une fois l&#39;application créée, sélectionnez l&#39;onglet **[!UICONTROL Examen des apps]** et publiez l&#39;application.

   ![](assets/social_create_facebook_app_004.png)

## Délégation des droits d’écriture à Adobe Campaign {#delegating-write-access-to-adobe-campaign}

Afin de déléguer à Adobe Campaign les droits d&#39;écriture sur les murs de vos pages, vous devez renseigner, dans Adobe Campaign, les paramètres de l&#39;application Facebook créée précédemment.

Cette étape requiert l&#39;accès simultané à votre console Adobe Campaign ainsi qu&#39;à un navigateur Internet connecté au compte Facebook administrateur de vos pages :

>[!CAUTION]
>
>L&#39;opérateur Adobe Campaign doit disposer des droits administrateur pour effectuer ce paramétrage.

* **Facebook** : sélectionnez l&#39;application créée précédemment ([https://developers.facebook.com/apps](https://developers.facebook.com/apps)), et sélectionnez l&#39;onglet **[!UICONTROL Paramètres > Général]** .

   ![](assets/social_facebook_external_account_002.png)

   >[!NOTE]
   >
   >Si la section **[!UICONTROL Jeux Web Facebook]** n&#39;apparaît pas, cliquez sur le bouton **[!UICONTROL Ajouter une plateforme]**, en bas de la page, et sélectionnez **[!UICONTROL Jeux Web Facebook]**.

* **Adobe Campaign** : dans l&#39;arborescence, positionnez-vous sur le noeud **[!UICONTROL Administration > Plateforme > Comptes externes]**, sélectionnez le compte externe **[!UICONTROL Routage Facebook]**, puis cliquez sur l&#39;onglet **[!UICONTROL Connecteur]**.

   ![](assets/social_facebook_external_account_001.png)

1. Dans la console Adobe Campaign, copiez l&#39;adresse contenue dans le champ **[!UICONTROL URL sécurisée du canevas]** et collez-la dans le champ **[!UICONTROL URL des jeux Web sécurisée (https)]** sur Facebook (dans la section **[!UICONTROL Jeux Web Facebook]**).

   ![](assets/social_facebook_external_account_006.png)

   >[!CAUTION]
   >
   >N&#39;utilisez en aucun cas l&#39;URL non sécurisée.

   Copiez et collez cette URL également sous **[!UICONTROL Produits]** > **[!UICONTROL Connexion Facebook]** > **[!UICONTROL Paramètres]** > **[!UICONTROL URI de redirection OAuth valides]**. Pour vérifier la validité de l’URL, enregistrez l’application, copiez et collez l’URL dans le champ **[!UICONTROL Rediriger l’URI pour vérification]** et cliquez sur **[!UICONTROL Vérifier l’URI]**.

   ![](assets/social_facebook_external_account_007bis.png)

1. Sur Facebook, copiez le contenu des champs **[!UICONTROL Identifiant de l&#39;app]** et **[!UICONTROL Clé secrète]** et collez-les dans les champs ID de l&#39;application et Clé secrète dans la console.

   ![](assets/social_facebook_external_account_007.png)

1. Sur Facebook, cliquez sur le bouton **[!UICONTROL Enregistrer les modifications]**, en bas de la page.
1. Dans la console Adobe Campaign, enregistrez le compte externe.

   >[!NOTE]
   >
   >Le champ **[!UICONTROL URL marketing]** est optionnel.

1. Dans la console Adobe Campaign, cliquez sur le lien **[!UICONTROL Demander l’autorisation auprès de l’application]**, en bas de l’onglet **[!UICONTROL Connecteur]**. Le workflow **[!UICONTROL Synchronisation des pages Facebook]** est automatiquement déclenché et récupère toutes les pages Facebook gérées par l’administrateur. [En savoir plus](#synchronizing-facebook-pages).

   ![](assets/social_facebook_external_account_004.png)

   >[!NOTE]
   >
   >Par défaut, les pages sont ajoutées à la racine du dossier de services **[!UICONTROL Facebook]**, disponible à partir du noeud **[!UICONTROL Profils et Cibles > Services et abonnements]**. Le champ **[!UICONTROL Dossier]** de l&#39;onglet **[!UICONTROL Connecteur]** permet de modifier le dossier de services dans lequel les pages Facebook sont créées après la synchronisation. Vous pouvez également choisir les pages Facebook que vous souhaitez synchroniser dans Adobe Campaign à l&#39;aide du champ **[!UICONTROL Filtre]**. Si vous laissez ce champ vide, toutes les pages Facebook gérées par l&#39;administrateur seront synchronisées.

1. Une boite de dialogue apparaît, avec les différents paramètres de demande d&#39;autorisation Facebook. Ces paramètres permettront à Adobe Campaign d&#39;envoyer des publications sur les murs des pages du compte Facebook.

   Acceptez les différentes demandes d’autorisations.

   ![](assets/social_facebook_external_account_003.png)

1. La délégation des droits d&#39;écriture d&#39;Adobe Campaign sur les murs des pages du compte Facebook est terminée.

   ![](assets/social_facebook_external_account_011.png)

>[!NOTE]
>
>Si le compte Facebook administre plusieurs pages, il suffit de ne configurer qu&#39;un seul compte externe pour écrire sur n&#39;importe laquelle des pages du compte Facebook. Pour chaque nouveau compte Facebook, vous devez créer un nouveau compte externe de type **[!UICONTROL Routage]**.

Le workflow **[!UICONTROL Synchronisation des pages Facebook]** synchronise ensuite toutes les pages administrées par le compte Facebook pour vous permettre de publier sur leur mur directement depuis Adobe Campaign. [En savoir plus](#synchronizing-facebook-pages).

## Synchronisation des pages Facebook {#synchronizing-facebook-pages}

Le workflow **[!UICONTROL Synchronisation des pages Facebook]**, accessible à partir du nœud **[!UICONTROL Administration > Exploitation > Workflows techniques > Gestion des réseaux sociaux]** permet de synchroniser, dans Adobe Campaign, les pages du compte Facebook configuré précédemment. Ce workflow est configuré par défaut pour se déclencher une fois par jour ou dès qu’un administrateur clique sur le lien **[!UICONTROL Demander l’autorisation auprès de l’application]**, dans l’écran de configuration du service. [En savoir plus](#delegating-write-access-to-adobe-campaign).

Une fois la synchronisation terminée, les pages collectées apparaissent dans le dossier de services renseigné dans le compte externe. [En savoir plus](#delegating-write-access-to-adobe-campaign).

Par défaut, les pages sont ajoutées à la racine du dossier du service **[!UICONTROL Facebook]**, disponible via le menu **[!UICONTROL Profils et Cibles > Services et abonnements]**.

![](assets/social_facebook_service_002.png)

Vous pouvez maintenant publier sur les murs de vos pages Facebook directement via Adobe Campaign. [En savoir plus](#publishing-on-facebook-walls).
