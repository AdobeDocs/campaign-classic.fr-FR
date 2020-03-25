---
title: Insérer une image dynamique
seo-title: Insérer une image dynamique
description: Insérer une image dynamique
seo-description: null
page-status-flag: never-activated
uuid: 4acc905e-625c-45aa-bb70-7dde22911aa0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-target
discoiquuid: f6e4d22b-4ad3-4a1e-8a6f-3bdfc1da0535
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f4d5d8474099776f770e88fcaf3bf15256da1be2

---


# Inserting Target dynamic content {#inserting-a-dynamic-image}

Dans ce guide, nous allons décrire comment intégrer une offre dynamique provenant de Target dans un email créé préalablement dans Adobe Campaign.

Nous souhaitons créer une diffusion contenant un bloc d&#39;image qui change dynamiquement en fonction du pays du destinataire. Les données sont envoyées avec chaque requête de mbox et dépendent de l&#39;adresse IP du visiteur.

Dans cet email, nous souhaitons que les images changent dynamiquement en fonction des expériences utilisateur suivantes :

* L&#39;email est ouvert en France.
* L&#39;email est ouvert aux Etats-Unis.
* Si aucune de ces conditions n&#39;est remplie, une image par défaut s&#39;affiche.

![](assets/target_4.png)

Pour ce faire, nous devons suivre les étapes suivantes dans Adobe Campaign et Target:

1. [Insérer l&#39;offre dynamique dans un email](../../integrations/using/inserting-a-dynamic-image.md#inserting-dynamic-offer)
1. [Créer les offres de redirection](../../integrations/using/inserting-a-dynamic-image.md#create-redirect-offers)
1. [Création d&#39;une audience](../../integrations/using/inserting-a-dynamic-image.md#audiences-target)
1. [Créer une activité de ciblage d&#39;expérience](../../integrations/using/inserting-a-dynamic-image.md#creating-targeting-activity)
1. [Prévisualiser et envoyer l&#39;email](../../integrations/using/inserting-a-dynamic-image.md#preview-send-email)

## Insérer l&#39;offre dynamique dans un email {#inserting-dynamic-offer}

Dans Adobe Campaign, une fois que vous avez défini la cible et le contenu de votre email, vous pouvez insérer une image dynamique provenant de Target.

Pour ce faire, spécifiez l&#39;URL de l&#39;image par défaut, le nom de l&#39;emplacement et les champs que vous souhaitez transférer à Target.

Dans Adobe Campaign, vous pouvez insérer une image dynamique de Target dans un email de deux manières différentes :

* Si vous utilisez l’éditeur de contenu numérique, choisissez une image existante et sélectionnez **[!UICONTROL Insert]** > **[!UICONTROL Dynamic image served by Adobe Target]** dans la barre d’outils.

   ![](assets/target_5.png)

* If you are using the standard editor, place the cursor where you want to insert the image and select **[!UICONTROL Include]** > **[!UICONTROL Dynamic image served by Adobe Target...]** from the personalization drop-down menu.

   ![](assets/target_12.png)

### Définir les paramètres de l&#39;image {#defining-image-parameters}

* The **[!UICONTROL Default image]**&#39;s URL: The image that will be displayed when none of the conditions are fulfilled. Vous pouvez également sélectionner une image dans votre bibliothèque Assets.
* The **[!UICONTROL Target location]**: Enter a name for your dynamic offer&#39;s location. Vous devrez sélectionner cet emplacement dans votre activité Target.
* Le **[!UICONTROL Landing Page]**: Si vous souhaitez que l’image par défaut redirige vers un  par défaut. Cette URL s’applique uniquement aux cas où l’image par défaut est affichée dans le courrier électronique final et est facultative.
* The **[!UICONTROL Additional decision parameters]**: Specify the mapping between the fields defined in the Adobe Target segments and the Adobe Campaign fields. Les champs d&#39;Adobe Campaign utilisés doivent avoir été spécifiés au niveau du &quot;rawbox&quot;. Dans notre exemple, nous avons ajouté le champ Pays.

Si vous utilisez les autorisations d’entreprise dans vos paramètres dans  Adobe, ajoutez la propriété correspondante dans ce champ. Pour en savoir plus sur les autorisations d’ d’entreprise dans [cette page](https://marketing.adobe.com/resources/help/en_US/target/target/properties-overview.html).

![](assets/target_13.png)

## Créer les offres de redirection {#create-redirect-offers}

Dans le , vous pouvez créer différentes versions de votre  de. Selon chaque expérience utilisateur, vous pouvez créer une offre de redirection et spécifier l&#39;image qui sera affichée.

Dans notre cas, nous avons besoin de deux offres de redirection, la troisième (celle par défaut) étant définie dans Adobe Campaign.

1. Pour créer une nouvelle  de redirection  dans  Standard, cliquez sur **[!UICONTROL Content]** dans l’ **[!UICONTROL Code offers]** onglet.

1. Cliquez **[!UICONTROL Create]** alors **[!UICONTROL Redirect Offer]**.

   ![](assets/target_9.png)

1. Saisissez le nom de votre offre et l&#39;URL de votre image.

   ![](assets/target_6.png)

1. Suivez la même procédure pour l&#39;offre de redirection restante. Pour plus d’informations à ce propos, consultez [cette page](https://docs.adobe.com/help/en/target/using/experiences/offers/offer-redirect.html).

## Création d&#39;une audience {#audiences-target}

Dans le , vous devez créer les deux  de dans lesquels les personnes qui visitent votreseront classées pour les différents contenus à diffuser. Pour chaque audience, ajoutez une règle pour définir qui pourra visualiser l&#39;offre.

1. Pour créer un nouveau   en, cliquez sur **[!UICONTROL Audiences]** dans l’ **[!UICONTROL Create Audience]** onglet.

   ![](assets/audiences_1.png)

1. Ajouter un nom à votre .

   ![](assets/audiences_2.png)

1. Cliquez sur **[!UICONTROL Add a rule]** puis sélectionnez un . La règle utilise des critères spécifiques pour cibler les visiteurs. Vous pouvez affiner les règles en ajoutant des conditions ou en créant des règles dans d&#39;autres catégories.

1. Suivez la même procédure pour les audiences restantes.

## Créer une activité de ciblage d&#39;expérience {#creating-targeting-activity}

Dans , nous devons créer un  ciblage d’expérience, définir les différentes expériences et les associer aucorrespondant.

### Définir l&#39;audience {#defining-the-audience}

1. Pour créer un  de ciblage d’expérience, cliquez sur **[!UICONTROL Activities]** puis **[!UICONTROL Create Activity]** dans l’ **[!UICONTROL Experience Targeting]** onglet.

   ![](assets/target_10.png)

1. Sélectionnez **[!UICONTROL Form]** comme **[!UICONTROL Experience Composer]**.

1. Choisissez un   en cliquant sur le **[!UICONTROL Change audience]** bouton.

   ![](assets/target_10_2.png)

1. Sélectionnez le   qui a été créé lors des étapes précédentes.

   ![](assets/target_10_3.png)

1. Créez une autre expérience en cliquant sur **[!UICONTROL Add Experience Targeting]**.

### Définir l&#39;emplacement et le contenu {#defining-location-content}

Ajoutez un contenu pour chaque audience :

1. Sélectionnez le nom de l’emplacement choisi lors de l’insertion du   dans le  de Adobe Campaign.

   ![](assets/target_15.png)

1. Cliquez sur le bouton déroulant et sélectionnez **[!UICONTROL Change Redirect Offer]**.

   ![](assets/target_content.png)

1. Sélectionnez l&#39;offre de redirection précédemment créée.

   ![](assets/target_content_2.png)

1. Suivez les mêmes étapes pour la deuxième expérience.

### Définir l&#39;activité {#defining-activity}

The **[!UICONTROL Target]** window summarizes your activity. Au besoin, vous pouvez ajouter d&#39;autres expériences.

![](assets/target_experience.png)

The **[!UICONTROL Goal & Settings]** window allows you to personalize your activity by setting a priority, an objective, or a duration.

The **[!UICONTROL Reporting Settings]** section lets you select an action and edit the parameters that will determine when your goal is achieved.

![](assets/target_experience_2.png)

## Prévisualisation et envoi du courrier électronique dans Campaign Classic {#preview-send-email}

Dans Adobe Campaign, vous pouvez à présent prévisualiser l&#39;email et tester le rendu pour différents destinataires. Vous pouvez constater que l&#39;image change selon les différentes expériences créées. To learn more on email creation, refer to this [page](../../delivery/using/defining-the-email-content.md).

Votre email comprenant une offre dynamique provenant de Target peut maintenant être envoyé.

![](assets/target_20.png)
