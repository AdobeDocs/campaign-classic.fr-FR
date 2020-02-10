---
title: Exemples d'apps Facebook
seo-title: Exemples d'apps Facebook
description: Exemples d'apps Facebook
seo-description: null
page-status-flag: never-activated
uuid: 336f4006-3545-4b04-959d-61cd0446af27
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: social
content-type: reference
topic-tags: annexes
discoiquuid: 07be1d3c-b038-48ca-be37-a33adb8e0fc0
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7f03e1fbb94bbd5b00fa0094a0b5e9be45629ec7

---


# Exemples d&#39;apps Facebook{#examples-of-facebook-apps}

Lorsqu&#39;un utilisateur clique sur l&#39;onglet d&#39;une application Facebook, celle-ci s&#39;affiche dans un espace de 810 pixels de large. Par le biais d&#39;une application web de type Facebook, Adobe Campaign vous permet de définir et de personnaliser le contenu affiché dans l&#39;application Facebook, et facilite l&#39;acquisition de profils.

>[!NOTE]
>
>Il est également possible d’intégrer Adobe Campaign à une application Facebook développée par un partenaire. Dans ce cas, il n’est pas nécessaire d’utiliser l’application Web Adobe Campaign pour acquérir des profils Facebook. For more on this, refer to [Configuring external accounts](../../social/using/creating-a-facebook-application.md#configuring-external-accounts).

![](assets/social_webapp_fb_000.png)

>[!CAUTION]
>
>Suivez les étapes de configuration décrites dans [Création d&#39;une application](../../social/using/creating-a-facebook-application.md)Facebook.

>[!NOTE]
>
>Cette section présente les éléments spécifiques aux applications web de type Facebook. Tous les éléments communs avec les applications web standards sont présentés dans [cette section](../../web/using/about-web-applications.md).

Les exemples d&#39;applications web de type Facebook présentés dans cette section sont les suivants :

* Comment créer une application Facebook en 7 étapes. Refer to [Quick start: creating a Facebook application in 7 steps](#quick-start--creating-a-facebook-application-in-7-steps).
* Comment transférer des paramètres à une application Facebook. Refer to [How to forward settings to a Facebook application?](#how-to-forward-settings-to-a-facebook-application-).
* Comment acquérir des données de fan. Reportez-vous à [Comment acquérir des données de fan?](#how-to-acquire-fan-data-).

>[!CAUTION]
>
>Ces cas d&#39;utilisation simples ne sont donnés qu&#39;à titre d&#39;exemple afin d&#39;illustrer les fonctionnalités des applications web de type Facebook.

## Recommandations {#recommendations}

Les limitations suivantes sont des contraintes inhérentes à Facebook :

* Vous devez impérativement construire toutes vos applications web en HTTPS.
* Une application Facebook affichée à partir d&#39;un onglet a une largeur de 810 pixels.

## Quick Start : comment créer une application Facebook en 7 étapes {#quick-start--creating-a-facebook-application-in-7-steps}

Cet exemple décrit pas à pas toutes les étapes permettant d&#39;afficher, dans Facebook, une application construite avec Adobe Campaign. Dans cet exemple, nous allons créer une application permettant d&#39;afficher le message **Bienvenue** lorsque l&#39;utilisateur clique sur l&#39;onglet de l&#39;application (**App01**).

Pour créer cette application, suivez les étapes ci-dessous :

1. Créez une application sur Facebook ( [https://developers.facebook.com/apps](https://developers.facebook.com/apps)). Pour plus d’informations à ce sujet, voir : [Création d’une application](../../social/using/publishing-on-facebook-walls.md#creating-a-facebook-application)Facebook.

   ![](assets/social_create_facebook_app_002.png)

1. Créez un compte **[!UICONTROL Facebook Connect]** externe de type et saisissez les paramètres de l’application Facebook. For more on this, refer to: [Configuring external accounts](../../social/using/creating-a-facebook-application.md#configuring-external-accounts).

   ![](assets/social_quick_start_2.png)

1. Entrez les liens **[!UICONTROL Terms of service]** et **[!UICONTROL Privacy policy]** les liens à afficher sur l’écran de demande d’autorisation Facebook. Pour plus d’informations à ce sujet, voir : [Saisir les liens](../../social/using/creating-a-facebook-application.md#entering-the-terms-of-service-and-privacy-policy-links)des conditions de service et de la politique de confidentialité.

   ![](assets/social_quick_start_1.png)

1. Créez une application Web de type Facebook dans Adobe Campaign. Pour plus d’informations à ce sujet, voir : [Création d’une application](../../social/using/creating-a-facebook-application.md#creating-a-facebook-type-web-application)Web de type Facebook.

   ![](assets/social_webapp_005.png)

1. Modifiez votre application Web. In this example, we have added a **[!UICONTROL Page]** activity and defined a title for it.

   ![](assets/social_quick_start_4.png)

1. Publiez votre application.

   ![](assets/social_webapp_004.png)

1. Configurez votre application Facebook de sorte qu’elle s’affiche sous forme d’onglet sur votre page Facebook. For more on this, refer to: [Configuring Facebook tabs](../../social/using/creating-a-facebook-application.md#configuring-facebook-tabs).

   ![](assets/social_quick_start_5.png)

![](assets/social_quick_start_6.png)

Vérifiez que l&#39;onglet de l&#39;application **App01** apparaît bien sur votre page Facebook. Lorsque vous cliquez dessus, le message **Bienvenue** doit apparaître.

![](assets/social_webapp_042.png)

## How to forward settings to a Facebook application? {#how-to-forward-settings-to-a-facebook-application-}

>[!CAUTION]
>
>Suivez les étapes de configuration décrites dans [Création d’une application](../../social/using/creating-a-facebook-application.md)Facebook.

Dans l’exemple 1, nous avons personnalisé l’affichage de la page Facebook en fonction de la valeur du **[!UICONTROL Fan of the page]** champ. Il est également possible de traiter le **[!UICONTROL Application settings]** champ. Ce champ vous permet de récupérer les données contenues dans un lien généré par Adobe Campaign, via Facebook.

Prenons l&#39;exemple d&#39;une entreprise qui décide d&#39;envoyer une campagne par courriel. Dans la diffusion, un lien pointe vers l’application Facebook. Ce lien est personnalisé grâce au **[!UICONTROL app_data]** paramètre ajouté à la fin de l’URL. La valeur de ce paramètre peut être un indicateur qui reflète la signification du client. Dans notre exemple, les valeurs du **[!UICONTROL app_data]** paramètre sont **[!UICONTROL big]** (client important) et **[!UICONTROL small]** (client moins important).

Une fois personnalisée, l&#39;URL devient :

* `http://<path of the Facebook application>&app_data=big` (pour un client important)
* `http://<path of the Facebook application>&app_data=small` (pour un client moins important)

Among the anonymous data forwarded to Adobe Campaign by Facebook, the value of the **[!UICONTROL Application parameters]** field is collected, thus enabling Adobe Campaign to personalize application display based on this parameter.

Si l&#39;utilisateur est un client important (la valeur du paramètre **[!UICONTROL app_data]** est **[!UICONTROL big]**), l&#39;image suivante s&#39;affiche :

![](assets/social_webapp_017.png)

Si l&#39;utilisateur est un client moins important (la valeur du paramètre **[!UICONTROL app_data]** est **[!UICONTROL small]**), l&#39;image suivante apparaît :

![](assets/social_webapp_016.png)

Pour réaliser ce cas d&#39;utilisation, nous avons créé une application web composée des éléments suivants :

* Activité **[!UICONTROL Test]** basée sur le **[!UICONTROL Application parameter]** champ.
* two pages which contain the images to display according to the value of the **[!UICONTROL Application parameter]** field.

![](assets/social_webapp_018.png)

## How to acquire fan data? {#how-to-acquire-fan-data-}

>[!CAUTION]
>
>Suivez les étapes de configuration décrites dans [Création d’une application](../../social/using/creating-a-facebook-application.md)Facebook.

Cet exemple illustre comment entrer en contact avec les utilisateurs Facebook et leur proposer de partager leurs informations de profil. Prenons pour exemple une société qui souhaite acquérir un fichier de prospects. Elle organise un jeu concours, sur sa page Facebook, afin d&#39;attirer les prospects.

Lorsqu&#39;un utilisateur clique sur l&#39;onglet **[!UICONTROL App03]**, nous lui proposons de participer au jeu.

![](assets/social_webapp_fb_000.png)

S&#39;il choisit de participer au concours, nous lui proposons de partager ses informations de profil.

![](assets/social_webapp_021.png)

S&#39;il accepte de partager ses informations, l&#39;écran suivant apparaît.

![](assets/social_webapp_022.png)

Pour réaliser ce cas d&#39;utilisation, nous avons créé une application web composée des éléments suivants :

* une **[!UICONTROL Test]** activité
* trois pages
* une **[!UICONTROL Access control]** activité
* une **[!UICONTROL Pre-loading]** activité
* une **[!UICONTROL Save]** activité
* une **[!UICONTROL End]** activité

![](assets/social_webapp_019.png)

### Activité Test {#test-activity}

L’ **[!UICONTROL Test]** activité est basée sur le **[!UICONTROL ID]** champ et le champ **[!UICONTROL Application parameters]** .

![](assets/social_webapp_023.png)

Celle-ci comporte trois branches :

* **[!UICONTROL identifier (UID) is empty]** : l’identifiant n’est transmis par Facebook que si l’utilisateur a déjà accepté de partager ses informations. La première branche de l’ **[!UICONTROL Test]** activité vous permet de rendre le concours disponible uniquement pour les utilisateurs qui n’ont jamais participé, c’est-à-dire ceux qui ont un ID vide.
* **[!UICONTROL application parameter equals 'thanks']** : pour éviter une erreur d’affichage liée à Facebook, la page de fin de l’application Web pointe vers l’URL de l’application Facebook à laquelle le **[!UICONTROL app_data]** paramètre est ajouté à l’aide de la **[!UICONTROL thanks]** valeur (pour plus d’informations, reportez-vous à : Activité [de fin](#end-activity)). La deuxième branche vous permet de savoir si l’utilisateur provient de l’ **[!UICONTROL End]** activité de la première branche (et vient d’entrer dans le concours) pour afficher un message de remerciement. Pour plus d’informations sur l’utilisation de paramètres d’URL supplémentaires, voir : [Comment transférer des paramètres vers une application Facebook?](#how-to-forward-settings-to-a-facebook-application-).
* **[!UICONTROL Default branch]** : si l&#39;utilisateur a déjà participé au concours (ID déjà entré) à une date antérieure (paramètre d&#39;application différent de **[!UICONTROL thanks]**), nous afficherons une page indiquant qu&#39;il a déjà participé.

### Page du jeu {#competition-page}

Pour éviter l’erreur d’affichage liée à Facebook, vous devez également sélectionner **[!UICONTROL Parent window]** ou **[!UICONTROL In the top window]** dans le **[!UICONTROL Window]** champ de la page du concours.

![](assets/social_webapp_028.png)

### Activité Contrôle d&#39;accès {#access-control-activity}

L’ **[!UICONTROL Access control]** activité vous permet d’afficher la page de demande d’autorisation Facebook lorsque l’utilisateur entre dans le concours. S&#39;ils acceptent de partager leurs informations, elles sont récupérées pendant le préchargement. For more on this, refer to: [Pre-loading activity](#pre-loading-activity).

Si vous avez précédemment saisi le compte externe lors de la création de l’application Web (voir [Création d’une application](../../social/using/creating-a-facebook-application.md#creating-a-facebook-type-web-application)Web de type Facebook), vous n’avez pas besoin de modifier l’activité. Dans le cas contraire, accédez au **[!UICONTROL Application]** champ et sélectionnez le compte externe lié à l’application Facebook.

![](assets/social_webapp_024.png)

### Activité Pré-chargement {#pre-loading-activity}

Sélectionnez la source des données à utiliser pour le préchargement :

* **[!UICONTROL Marketing database]** : cette option vous permet de précharger des données via la base de données Adobe Campaign.
* **[!UICONTROL Facebook]** : cette option permet d&#39;effectuer le préchargement à partir des données Facebook.

![](assets/social_webapp_029.png)

**Base marketing**

Cette option vous permet de récupérer les données d’un profil existant dans le tableau des visiteurs. La vérification est effectuée en fonction de l’ID Facebook externe récupéré lorsque l’utilisateur clique sur l’onglet de l’application Facebook. Si vous ajoutez un formulaire après l’ **[!UICONTROL Pre-loading]** activité, les champs contenant des informations dans la base de données sont préchargés.

![](assets/social_webapp_030.png)

>[!NOTE]
>
>Reportez-vous à [cette section](../../web/using/publishing-a-web-form.md#pre-loading-the-form-data) pour plus d’informations sur le préchargement des données depuis la base de données Adobe Campaign.

**Facebook**

Cette option permet de définir les informations de profil Facebook à récupérer, parmi celles que l&#39;utilisateur a accepté de partager, dans le but de les enregistrer.

![](assets/social_webapp_025.png)

The **[!UICONTROL Database information]** option lets you collect the following data:

* **[!UICONTROL External ID]**: ID utilisateur
* **[!UICONTROL Gender]**: sexe de l’utilisateur
* **[!UICONTROL Verified]** : ce champ indique si l’utilisateur dispose d’un compte Facebook vérifié.
* **[!UICONTROL Full name]**: nom complet de l’utilisateur
* **[!UICONTROL First name]**: prénom de l’utilisateur
* **[!UICONTROL Last name]**: nom de famille de l’utilisateur
* **[!UICONTROL Language]**: langue de l’utilisateur

Vous pouvez également choisir de récupérer la photo de profil, la liste des amis, l&#39;adresse email, la date de naissance, les centres d&#39;intérêt et le lieu en cochant les cases correspondantes.

Avant de cliquer **[!UICONTROL Ok]**, cochez la **[!UICONTROL I agree to comply with Facebook conditions of use]** case.

>[!NOTE]
>
>If you check one or more boxes in the **[!UICONTROL Private information]** section, the Facebook permission request screen will automatically display the access request for this data.
>
>Pour récupérer les informations sélectionnées, l&#39;utilisateur doit avoir accepté de les partager.
>
>Si vous souhaitez effectuer les deux types de préchargement (depuis Adobe Campaign et Facebook), vous devez insérer deux boîtes de préchargement l&#39;une à la suite de l&#39;autre.

### Activité Enregistrement {#save-activity}

The **[!UICONTROL Save]** activity lets you store the information collected during the previous stages in the visitors&#39; table.

Si le profil existe déjà dans la table des visiteurs, ses données sont mises à jour avec les nouvelles données récupérées.

Si le profil n&#39;existe pas en base et que l&#39;adresse email de l&#39;utilisateur Facebook a été récupérée, un visiteur est créé dans la table des visiteurs.

![](assets/social_webapp_026.png)

1. Dans le **[!UICONTROL Visitor creation folder]** champ, sélectionnez le dossier dans lequel le profil sera créé. Dans le cas d’une application Web de type Facebook, le dossier de création par défaut est **[!UICONTROL Visitors]**.
1. In the **[!UICONTROL Reconciliation mode]** field, select the reconciliation mode you want to use:

   * **[!UICONTROL Automatic]** : La conciliation est effectuée sur la base du courriel, du nom, du prénom et de la date de naissance.
   * **[!UICONTROL Manual]** : Sélectionnez une ou plusieurs clés de réconciliation.
   * **[!UICONTROL None]** : Aucune réconciliation n&#39;aura lieu.

1. Dans le champ **[!UICONTROL Mapping]**, sélectionnez le schéma sur lequel vous souhaitez effectuer la réconciliation.

   >[!CAUTION]
   >
   >Assurez-vous que les champs de l’ **[!UICONTROL Social networks]** onglet sont correctement saisis dans le mappage de remise. Les mappages de remise sont accessibles via le **[!UICONTROL Administration > Campaign management > Target mappings]** noeud.

1. Vous pouvez sélectionner un dossier de recherche pour la réconciliation et un dossier de création pour les nouveaux profils. Si ces champs sont vides, les profils sont recherchés et créés dans le dossier par défaut correspondant au schéma du mapping.

### Activité Fin {#end-activity}

Pour éviter l’erreur d’affichage liée à Facebook, vous devez cocher la **[!UICONTROL Use an external URL]** case et saisir l’URL de l’application Facebook, suivie du **[!UICONTROL app_data]** paramètre et d’une valeur. Cette valeur sera utilisée dans l’ **[!UICONTROL Test]** activité pour détecter si l’utilisateur vient d’entrer dans le concours et pour afficher un message de remerciement, le cas échéant. For more on this, refer to: [Test activity](#test-activity).

Dans notre exemple, la valeur utilisée est **thanks**.

![](assets/social_webapp_027.png)

### Ecran de détails d&#39;un visiteur {#details-screen-of-a-visitor}

Comme pour les abonnés de Twitter (voir : Principe [d’exploitation](../../social/using/publishing-on-twitter.md#operating-principle)), les profils Facebook récupérés sont stockés dans le tableau des visiteurs. Pour afficher la liste des visiteurs, accédez au **[!UICONTROL Profiles and Targets > Visitors]** noeud.

Chaque prospect Facebook qui accepte de partager ses informations de profil est ajouté à la liste des visiteurs. Si la **[!UICONTROL Friends]** case est cochée dans l’ **[!UICONTROL Pre-load]** activité (voir : activité [de préchargement](#pre-loading-activity)), des amis sont également ajoutés.

![](assets/social_webapp_037.png)

In the **[!UICONTROL Summary]** section of the visitor detail window, there are two possible states for the **[!UICONTROL New Contact]** indicator:

![](assets/social_webapp_038.png)

Si une coche verte est affichée, cela signifie que le visiteur n&#39;a été réconcilié avec aucun destinataire. Dans ce cas, un nouveau profil est créé dans la liste des destinataires.

![](assets/social_webapp_039.png)

Une croix rouge signifie que le visiteur a été réconcilié avec un destinataire. Vous pouvez cliquer sur la loupe à droite du **[!UICONTROL Recipient]** champ pour afficher le destinataire correspondant.

![](assets/social_webapp_040.png)

Accédez à la fenêtre détaillée d’un destinataire pour afficher le visiteur correspondant, le cas échéant. Sélectionnez l’ **[!UICONTROL Others]** onglet, puis cliquez deux fois sur le nom du visiteur dans la **[!UICONTROL Web identities]** section.

![](assets/social_webapp_041.png)

The **[!UICONTROL Activities]** screen of a visitor&#39;s details page contains the following information:

* activités de type &quot;Open Graph&quot; du fan : musique écoutée, vidéos visionnées, articles lus et déduction des applications installées (Deezer, Spotify, Dailymotion, Yahoo News, etc.)

   ![](assets/social_facebook_activities.png)

* les mentions &quot;J&#39;aime&quot; et les commentaires que le fan a ajouté suite à des diffusions envoyées par Adobe Campaign
* les pages aimées par le fan
* les check-ins effectués par le fan

   ![](assets/social_facebook_checkins.png)

   >[!NOTE]
   >
   >Pour qu’Adobe Campaign puisse collecter les visites d’un fan, vous devez cliquer sur le **[!UICONTROL Subscribe]** bouton de l’écran de configuration du service. For more on this, refer to [Configuring external accounts](../../social/using/creating-a-facebook-application.md#configuring-external-accounts).

## Comment pré-remplir les champs d&#39;un formulaire avec les données de profil Facebook {#how-to-pre-load-the-fields-of-a-form-using-facebook-profile-data}

L’ **[!UICONTROL Social Marketing]** application vous permet également d’ajouter un bouton à un formulaire pour le préchargement de champs à l’aide des informations de profil Facebook. Cette option, disponible dans tous les modèles d’applications Web (activités de **[!UICONTROL Page]** type), est détaillée dans [cette section](../../web/using/static-elements-in-a-web-form.md#inserting-html-content).

![](assets/social_webapp_035.png)

>[!NOTE]
>
>Avant de commencer à utiliser cette fonction, vous devez créer une application Facebook et un compte externe de **[!UICONTROL Facebook Connect]** type. For more on this, refer to [Configuring external accounts](../../social/using/creating-a-facebook-application.md#configuring-external-accounts).

