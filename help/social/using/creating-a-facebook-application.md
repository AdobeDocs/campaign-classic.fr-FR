---
title: Créer une application Facebook
seo-title: Créer une application Facebook
description: Créer une application Facebook
seo-description: null
page-status-flag: never-activated
uuid: f02129b9-6f64-41ee-8b56-d85211a58f69
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: social
content-type: reference
topic-tags: configuration
discoiquuid: c1d880bb-256e-451c-8c52-198711907f8e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2e18121e4094bc4cb215e5471091810df56b3ef5

---


# Créer une application Facebook{#creating-a-facebook-application}

Grâce aux applications Web, le marketing social vous permet d’afficher du contenu personnalisé dans vos applications Facebook, ce qui facilite l’acquisition de prospects via ce réseau social. Pour plus d’exemples d’applications Web de type Facebook, voir [Exemples d’applications](../../social/using/examples-of-facebook-apps.md)Facebook.

>[!NOTE]
>
>Il est également possible d’intégrer Adobe Campaign à une application Facebook développée par un partenaire. Dans ce cas, il n’est pas nécessaire d’utiliser l’application Web Adobe Campaign pour acquérir des profils Facebook. For more on this, refer to [Configuring external accounts](#configuring-external-accounts).

![](assets/social_webapp_fb_000.png)

Les étapes de paramétrage sont les suivantes :

1. Créez une ou plusieurs applications Facebook. Pour plus d’informations à ce sujet, voir : [Création d’une application](../../social/using/publishing-on-facebook-walls.md#creating-a-facebook-application)Facebook.
1. Entrez les liens **[!UICONTROL terms of service]** et **[!UICONTROL Privacy policy]** les liens à afficher sur l’écran de demande d’autorisation Facebook. Pour plus d’informations à ce sujet, voir : [Saisir les liens](#entering-the-terms-of-service-and-privacy-policy-links)des conditions de service et de la politique de confidentialité.
1. Pour chaque application Facebook, créez un **[!UICONTROL Facebook Connect]** type de compte externe. For more on this, refer to: [Configuring external accounts](#configuring-external-accounts).
1. Pour chaque application Facebook, créez une application Web de type Facebook dans Adobe Campaign. Pour plus d’informations à ce sujet, voir : [Création d’une application](#creating-a-facebook-type-web-application)Web de type Facebook.
1. Configurez vos applications Facebook afin qu’elles s’affichent sous forme d’onglets sur votre page Facebook. For more on this, refer to: [Configuring Facebook tabs](#configuring-facebook-tabs).

## Paramétrer les comptes externes {#configuring-external-accounts}

Pour chaque application Facebook, vous devez créer un compte externe de type **[!UICONTROL Facebook Connect]**.

Cette étape requiert l&#39;accès simultané à votre console Adobe Campaign ainsi qu&#39;à un navigateur Internet connecté au compte Facebook administrateur de vos pages :

* **Facebook**: sélectionnez l’application créée précédemment ( [https://developers.facebook.com/apps](https://developers.facebook.com/apps)), puis sélectionnez l’onglet **[!UICONTROL Settings]** > **[!UICONTROL Basic]** .

   ![](assets/social_webapp_fb_008.png)

   >[!NOTE]
   >
   >Si la **[!UICONTROL Facebook Web Games]** section n’apparaît pas, cliquez sur le **[!UICONTROL Add Platform]** bouton, au bas de la page, puis sélectionnez **[!UICONTROL Facebook Web Games]**.

* **Adobe Campaign**: accédez au **[!UICONTROL Administration > Platform > External accounts]** noeud de l’arborescence et cliquez sur **[!UICONTROL New]**.

   ![](assets/social_webapp_fb_005.png)

1. Saisissez un libellé et un nom interne, et sélectionnez le type **[!UICONTROL Facebook Connect]**.

   ![](assets/social_webapp_fb_006.png)

1. Sélectionnez un mode d’hébergement pour l’application : **[!UICONTROL hosted by a partner]** ou **[!UICONTROL hosted by this instance]**.

   ![](assets/social_webapp_fb_012.png)

   **Application hébergée chez un partenaire**

   Il est possible d&#39;intégrer Adobe Campaign avec une application Facebook développée par un partenaire. Dans ce cas, il n&#39;est pas nécessaire d&#39;utiliser les applications web Adobe Campaign pour acquérir des profils Facebook. Lorsque l&#39;utilisateur Facebook installe l&#39;application, une clé (access token) est générée. Le partenaire transmet cette clé à Adobe Campaign en appelant un webservice. Adobe Campaign utilise cette clé pour se connecter à la base Facebook et récupérer les données que l&#39;utilisateur a partagé avec l&#39;application.

   >[!NOTE]
   >
   >Les paramètres du service Web sont détaillés dans le fichier WSDL disponible ici : **`https://<Instance name>/nl/jsp/schemawsdl.jsp?schema=nms:visitor`**

   To integrate the third-party application into Adobe Campaign, you need to copy the content of the **[!UICONTROL App ID]** and **[!UICONTROL App Secret]** Facebook fields and paste it into the **[!UICONTROL Application ID]** and **[!UICONTROL Application secret]** fields of the console.

   ![](assets/social_facebook_external_account_013.png)

   **Application hébergée sur cette instance**

   Si vous souhaitez héberger l’application sur cette instance (si vous n’avez pas d’application tierce), vous devez utiliser les applications Web Adobe Campaign pour acquérir des profils Facebook. Pour plus d’informations, reportez-vous à [Exemples d’applications](../../social/using/examples-of-facebook-apps.md)Facebook.

   Dans la console Adobe Campaign, copiez l’adresse contenue dans le **[!UICONTROL Secure Canvas URL]** champ et collez-la dans le **[!UICONTROL Facebook Web games (https)]** champ sur Facebook (dans la **[!UICONTROL Facebook Web Games]** section).

   ![](assets/social_facebook_external_account_009.png)

   >[!IMPORTANT]
   >
   >N&#39;utilisez en aucun cas l&#39;URL non sécurisée.

   Sur Facebook, copiez le contenu des champs **[!UICONTROL App ID]** et **[!UICONTROL App Secret]** et collez-le dans les **[!UICONTROL Application ID]** champs et **[!UICONTROL Application secret]** de la console.

   ![](assets/social_facebook_external_account_008.png)

1. On Facebook, click the **[!UICONTROL Save Changes]** button at the bottom of the page.
1. In the Adobe Campaign console, click the **[!UICONTROL Subscribe]** button to enable Adobe Campaign to recover the data in real time each time a fan checks in via this application. Pour plus d’informations à ce sujet, voir : [Exemples d’applications](../../social/using/examples-of-facebook-apps.md)Facebook.

   ![](assets/social_webapp_fb_013.png)

## Renseigner les liens Conditions d&#39;utilisation et Politique de confidentialité {#entering-the-terms-of-service-and-privacy-policy-links}

We strongly recommend adding the **[!UICONTROL Terms of service]** and **[!UICONTROL Privacy policy]** links, to be displayed on the Facebook permission request screen.

![](assets/social_fb_terms_of_services_001.png)

Les étapes de paramétrage sont les suivantes :

1. Saisissez l&#39;adresse [https://developers.facebook.com/apps](https://developers.facebook.com/apps), puis sélectionnez l&#39;application Facebook.
1. Sélectionnez l’ **[!UICONTROL Settings > Basic]** onglet et saisissez les **[!UICONTROL Privacy Policy URL]** champs et **[!UICONTROL Terms of Service URL]** .

   ![](assets/social_fb_terms_of_services.png)

## Créer une application web de type Facebook {#creating-a-facebook-type-web-application}

L&#39;application web Adobe Campaign de type Facebook permet d&#39;afficher du contenu personnalisé dans votre application Facebook. Pour chaque application Facebook, vous devez créer une application web dans Adobe Campaign. Les étapes de création d&#39;une application web de type Facebook sont les suivantes.

1. Allez dans l&#39; **[!UICONTROL Social networks]** univers, cliquez sur le **[!UICONTROL Applications]** lien, puis sur le **[!UICONTROL Create]** bouton.

   ![](assets/social_webapp_001.png)

1. Sélectionnez un modèle d&#39;application web Facebook dans la liste, et renseignez le libellé.

   ![](assets/social_webapp_002.png)

   >[!NOTE]
   >
   >Quatre modèles d&#39;applications web Facebook sont proposés par défaut :
   >
   >* **[!UICONTROL New Facebook application]**: sélectionnez ce modèle si vous souhaitez commencer à partir d’une application vide.
   >* **[!UICONTROL Pre-entered form]**: Application Facebook avec un formulaire et un bouton &quot;connexion Facebook&quot; qui permet aux utilisateurs de remplir automatiquement les champs du formulaire à l’aide des données de leur profil. Cela permet aux utilisateurs de remplir le formulaire plus rapidement et aux marques d’obtenir des informations de meilleure qualité.
   >* **[!UICONTROL "Canvas page" competition]**: application Facebook affichée à l’écran pour une meilleure expérience visuelle pour les utilisateurs.
   >* **[!UICONTROL "Page Tab" competition]**: Application Facebook entièrement intégrée aux onglets de la page de marque.


1. Dans le **[!UICONTROL Application]** champ, saisissez le compte externe lié à l’application Facebook. For more on this, refer to: [Configuring external accounts](#configuring-external-accounts).

   ![](assets/social_webapp_005.png)

1. Sélectionnez l’ **[!UICONTROL Edit]** onglet, puis modifiez l’application Web. Pour plus d’informations à ce sujet, voir : [Exemples d’applications](../../social/using/examples-of-facebook-apps.md)Facebook.

   ![](assets/social_webapp_003.png)

1. Once the web application is complete, select the **[!UICONTROL Dashboard]** tab, then click **[!UICONTROL Publish]** to publish online.

   ![](assets/social_webapp_004.png)

## Paramétrer les onglets Facebook {#configuring-facebook-tabs}

Vous pouvez paramétrer vos applications Facebook pour qu&#39;elles apparaissent sous la forme d&#39;onglets sur votre page Facebook. Les étapes de paramétrage sont les suivantes :

1. Select the Facebook application ([https://developers.facebook.com/apps](https://developers.facebook.com/apps)), and select the **[!UICONTROL Settings > Basic]** tab.

   ![](assets/social_webapp_fb_008.png)

1. Au bas de la page, cliquez sur le **[!UICONTROL Add Platform]** bouton, puis sélectionnez **[!UICONTROL Page Tab]**.

   ![](assets/social_webapp_fb_008bis.png)

1. In the **[!UICONTROL Page Tab Name]** field of the **[!UICONTROL Page Tab]** section, enter the label as you want it to appear on the Facebook page.

   ![](assets/social_webapp_fb_001.png)

1. Dans le **[!UICONTROL Secure Page Tab URL]** champ, saisissez l’URL publique de l’application Web, accessible via l’ **[!UICONTROL Dashboard]** onglet de l’application Web. Pour plus d’informations sur la création d’applications Web de type Facebook, voir [Création d’une application](#creating-a-facebook-type-web-application)Web de type Facebook.

   ![](assets/social_webapp_fb_002.png)

1. Sur la page **[!UICONTROL Dashboard]** de l’application Web, cliquez sur le **[!UICONTROL Add a page tab]** lien.

   ![](assets/social_webapp_fb_0010.png)

1. Select the Facebook page you want to add the tab to and click **[!UICONTROL Add Page Tab]**.

   ![](assets/social_webapp_fb_0011.png)

