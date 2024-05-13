---
product: campaign
title: Insertion d’une image dynamique
description: Insertion d’une image dynamique
feature: Target Integration
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: 6177f57b-534c-4d86-8f73-d96980c48a77
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: ht
source-wordcount: '875'
ht-degree: 100%

---

# Insertion de contenu dynamique Target {#inserting-a-dynamic-image}



Cette page vous explique comment intégrer une offre dynamique provenant d’Adobe Target dans un e-mail créé dans Adobe Campaign.

L’objectif est de créer une diffusion avec un bloc d’images qui change de façon dynamique en fonction du pays du destinataire : les données sont envoyées avec chaque requête mbox et dépendent de l’adresse IP du destinataire.

Dans ce message, les images peuvent varier de façon dynamique en fonction des expériences utilisateur suivantes :

* L&#39;e-mail est ouvert en France.
* L&#39;e-mail est ouvert aux États-Unis.
* Si aucune de ces conditions n&#39;est remplie, une image par défaut s&#39;affiche.

![](assets/target_4.png)

Pour cela, les étapes sont les suivantes :

1. [Insertion de l&#39;offre dynamique dans un e-mail](../../integrations/using/inserting-a-dynamic-image.md#inserting-dynamic-offer)
1. [Créer des offres de redirection](../../integrations/using/inserting-a-dynamic-image.md#create-redirect-offers)
1. [Création d’audiences](../../integrations/using/inserting-a-dynamic-image.md#audiences-target)
1. [Création d&#39;une activité de ciblage d&#39;expérience](../../integrations/using/inserting-a-dynamic-image.md#creating-targeting-activity)
1. [Prévisualisation et envoi de l’e-mail](../../integrations/using/inserting-a-dynamic-image.md#preview-send-email)

## Insertion de l’offre dynamique dans un e-mail {#inserting-dynamic-offer}

Dans Adobe Campaign, une fois que vous avez défini la cible et le contenu de votre email, vous pouvez insérer une image dynamique provenant de Target.

Pour ce faire, spécifiez l’URL de l’image par défaut, le nom de l’emplacement et les champs que vous souhaitez transférer à Target.

Dans Adobe Campaign, vous pouvez insérer une image dynamique de Target dans un email de deux manières différentes :

* Si vous utilisez l&#39;éditeur Digital Content Editor, choisissez une image existante, puis sélectionnez **[!UICONTROL Insérer]** > **[!UICONTROL Image dynamique servie par Adobe Target]** depuis la barre d&#39;outils.

  ![](assets/target_5.png)

* Si vous utilisez l&#39;éditeur standard, placez le curseur à l&#39;endroit où vous souhaitez insérer l&#39;image et sélectionnez **[!UICONTROL Inclure]** > **[!UICONTROL Image dynamique servie par Adobe Target...]** dans le menu déroulant de personnalisation.

  ![](assets/target_12.png)

### Définition des paramètres de l’image {#defining-image-parameters}

* L’**[!UICONTROL URL de l’image par défaut]** : il s’agit de l’image affichée si aucune des conditions n’est remplie. Vous pouvez également sélectionner une image dans votre bibliothèque Assets.
* L’**[!UICONTROL Emplacement Target]** : saisissez le nom de l’emplacement de votre offre dynamique. Vous devrez sélectionner cet emplacement dans votre activité Target.
* La **[!UICONTROL Landing Page]** : si vous souhaitez que l’image par défaut soit redirigée vers une landing page par défaut. Cette adresse URL ne s’applique qu’aux cas où l’image par défaut est affichée dans l’email final et est facultative.
* Les **[!UICONTROL Paramètres de décision additionnels]** : associez les champs définis dans les segments d’Adobe Target et les champs d’Adobe Campaign. Les champs d’Adobe Campaign utilisés doivent avoir été spécifiés au niveau du « rawbox ». Dans notre exemple, nous avons ajouté le champ Pays.

Dans Adobe Target, si vous utilisez les autorisations Enterprise, ajoutez la propriété correspondante dans ce champ. Pour plus d’informations sur les autorisations Target Enterprise, consultez [cette page](https://experienceleague.adobe.com/docs/target/using/administer/manage-users/enterprise/properties-overview.html?lang=fr).

![](assets/target_13.png)

## Créer des offres de redirection {#create-redirect-offers}

Avec Target, vous pouvez créer différentes versions de votre offre. Selon chaque expérience utilisateur, vous pouvez créer une offre de redirection et spécifier l&#39;image qui sera affichée.

Dans notre cas, nous avons besoin de deux offres de redirection, la troisième (celle par défaut) étant définie dans Adobe Campaign.

1. Pour créer une offre de redirection dans Target Standard, cliquez sur **[!UICONTROL Offres (code)]** dans l&#39;onglet **[!UICONTROL Contenu]**.

1. Cliquez sur **[!UICONTROL Créer]**, puis sur **[!UICONTROL Offre de redirection]**.

   ![](assets/target_9.png)

1. Saisissez le nom de votre offre et l&#39;URL de votre image.

   ![](assets/target_6.png)

1. Suivez la même procédure pour l&#39;offre de redirection restante. Voir à ce propos [cette page](https://experienceleague.adobe.com/docs/target/using/experiences/offers/offer-redirect.html?lang=fr).

## Création d’audiences {#audiences-target}

Avec Target, vous devez créer les deux audiences dans lesquelles les visiteurs de votre offre seront classés selon les différents contenus à diffuser. Pour chaque audience, ajoutez une règle pour définir qui pourra visualiser l’offre.

1. Pour créer une audience avec Target, dans l&#39;onglet **[!UICONTROL Audiences]**, cliquez sur **[!UICONTROL Créer une audience]**.

   ![](assets/audiences_1.png)

1. Ajoutez un nom à l&#39;audience.

   ![](assets/audiences_2.png)

1. Cliquez sur **[!UICONTROL Ajouter une règle]** et sélectionnez une catégorie. La règle utilise des critères spécifiques pour cibler les visiteurs. Vous pouvez affiner les règles en ajoutant des conditions ou en créant des règles dans d&#39;autres catégories.

1. Suivez la même procédure pour les audiences restantes.

## Création d&#39;une activité de ciblage d&#39;expérience {#creating-targeting-activity}

Dans Target, nous devons créer une activité de ciblage d’expérience, définir les différentes expériences et les associer aux offres correspondantes.

### Définition de l’audience {#defining-the-audience}

1. Pour créer une activité de ciblage d&#39;expérience, dans l&#39;onglet **[!UICONTROL Activités]**, cliquez sur **[!UICONTROL Créer une activité]**, puis sur **[!UICONTROL Ciblage d&#39;expérience]**.

   ![](assets/target_10.png)

1. Sélectionnez **[!UICONTROL Formulaire]** comme **[!UICONTROL compositeur d&#39;expérience]**.

1. Choisissez une audience en cliquant sur le bouton **[!UICONTROL Changer l&#39;audience]**.

   ![](assets/target_10_2.png)

1. Sélectionnez l&#39;audience créée aux étapes précédentes.

   ![](assets/target_10_3.png)

1. Créez une autre expérience en cliquant sur **[!UICONTROL Ajouter le ciblage d&#39;expérience]**.

### Définition de l’emplacement et du contenu {#defining-location-content}

Ajoutez un contenu pour chaque audience :

1. Sélectionnez le nom de l’emplacement choisi lors de l’insertion de l’offre dynamique dans Adobe Campaign.

   ![](assets/target_15.png)

1. Cliquez sur le bouton de liste déroulante et sélectionnez **[!UICONTROL Modifier l&#39;offre de redirection]**.

   ![](assets/target_content.png)

1. Sélectionnez l&#39;offre de redirection précédemment créée.

   ![](assets/target_content_2.png)

1. Suivez la même procédure pour la deuxième expérience.

### Définition de l’activité {#defining-activity}

La fenêtre **[!UICONTROL Target]** résume votre activité. Au besoin, vous pouvez ajouter d&#39;autres expériences.

![](assets/target_experience.png)

La fenêtre **[!UICONTROL Objectif et paramètres]** permet de personnaliser votre activité en définissant une priorité, un objectif ou une durée.

La section **[!UICONTROL Paramètres de création de rapports]** permet de sélectionner une action et d&#39;éditer les paramètres qui déterminent à quel moment votre objectif est atteint.

![](assets/target_experience_2.png)

## Prévisualisation et envoi de l’e-mail {#preview-send-email}

Dans Adobe Campaign, vous pouvez désormais prévisualiser votre e-mail et en tester le rendu pour différents destinataires. Vous pouvez constater que l&#39;image change selon les différentes expériences créées. Pour en savoir plus sur la création d’un email, consultez cette [page](../../delivery/using/defining-the-email-content.md).

Votre email comprenant une offre dynamique provenant de Target peut maintenant être envoyé.

![](assets/target_20.png)
