---
product: campaign
title: Espace de travail Adobe Campaign
description: Découvrez comment utiliser et personnaliser l’espace de travail Campaign
feature: Overview
role: Data Engineer
level: Beginner
exl-id: 5f689679-7148-4abd-a9bf-185854c64b13
source-git-commit: d78fe2e0fd85ba9c23e709a3f30a135cee411230
workflow-type: tm+mt
source-wordcount: '873'
ht-degree: 92%

---

# Espace de travail Adobe Campaign {#adobe-campaign-workspace}

## Exploration de l’interface Adobe Campaign {#about-adobe-campaign-interface}

Une fois connecté à la base de données, vous accédez à la page d&#39;accueil d&#39;Adobe Campaign. Celle-ci se présente sous la forme d&#39;un tableau de bord : il est composé de liens et de raccourcis qui vous permettent d&#39;accéder aux fonctions disponibles selon votre installation et aux paramétrages généraux de la plateforme.

Depuis la section centrale de la page d&#39;accueil, vous pouvez utiliser les liens pour accéder au portail de la documentation en ligne, au forum et au site web d&#39;assistance de Campaign.

![](assets/d_ncs_user_interface_home.png)

![](assets/do-not-localize/how-to-video.png) [&#x200B; Découvrir l’espace de travail Campaign en vidéo](#video)

>[!NOTE]
>
>Les fonctions Adobe Campaign disponibles sur votre instance dépendent des modules et composants additionnels installés. Selon vos autorisations et configurations spécifiques, certaines d&#39;entre elles peuvent ne pas être disponibles.
>
>Avant d’installer un module ou un composant additionnel, vous devez vérifier votre contrat de licence ou contacter votre chargé de compte Adobe.

### Accès console et accès web {#console-and-web-access}

La plateforme Adobe Campaign est accessible via une console ou par le biais d’un navigateur Internet. Consultez les navigateurs compatibles dans la section relative à la [matrice de compatibilité](../../rn/using/compatibility-matrix.md#Browsers).

L’interface d’accès web est similaire à l’interface de la console. Depuis un navigateur, vous pouvez utiliser les mêmes fonctionnalités de navigation et d’affichage que dans la console, mais vous ne pouvez exécuter qu’un ensemble réduit d’actions sur les campagnes. Par exemple, vous pouvez afficher et annuler des campagnes, mais vous ne pouvez pas les modifier. Pour un même opérateur, une campagne sera affichée dans la console avec les options suivantes :

![Depuis le tableau de bord d’une campagne, l’opérateur peut visualiser et annuler une campagne, mais aussi la modifier, et y ajouter des diffusions, des documents ainsi que des tâches.](assets/operation_from_console.png)

Dans le contexte d’un accès web, les options seront en revanche principalement consultatives :

![À partir d’un navigateur, le même opérateur ne peut que visualiser et annuler la campagne.](assets/operation_from_web.png)

En savoir plus sur l’[utilisation de l’interface web.](../../campaign/using/accessing-marketing-campaigns.md#using-the-web-interface-).

### Langues {#languages}

La langue est sélectionnée lors de l&#39;installation de votre instance Adobe Campaign Classic.

![](assets/language.png)

Cinq langues sont disponibles :

* Anglais (Royaume-Uni)
* Anglais (États-Unis)
* Français
* Allemand
* Japonais

La langue choisie pour votre instance Adobe Campaign Classic peut avoir une incidence sur les formats de date et d’heure. Pour en savoir plus à ce sujet, consultez la documentation [Campaign v8 (console)](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/new/campaign-ui){target=_blank}.

Pour plus d’informations sur la création d’une instance, consultez cette [page](../../installation/using/creating-an-instance-and-logging-on.md).

>[!CAUTION]
>
>La langue ne peut pas être modifiée après la création de l&#39;instance.

## Notions de base relatives à la navigation {#navigation-basics}

### Navigation sur les pages {#browsing-pages}

Les différentes fonctionnalités de la plateforme sont réparties dans les fonctions principales : utilisez les liens proposés dans le bandeau supérieur de l&#39;interface pour y accéder.

![](assets/overview_home.png)

La liste des fonctions principales auxquelles vous pouvez accéder dépend des packages et des composants additionnels installés, ainsi que de vos droits d&#39;accès.

Chaque fonction propose un ensemble de fonctionnalités, organisé selon les besoins métiers relatifs au contexte d&#39;utilisation. Ainsi, le lien **[!UICONTROL Profils et cibles]** vous permet d’accéder aux listes de destinataires, aux services d’abonnement, aux workflows de ciblage existants et aux raccourcis pour créer ces éléments.

Ainsi, les listes sont accessibles à partir du lien **[!UICONTROL Listes]** proposé dans la section gauche de l&#39;interface **[!UICONTROL Profils et cibles]**.

![](assets/recipient_list_overview.png)

### Utilisation des onglets {#using-tabs}

* Lorsque vous cliquez sur une fonction principale ou un lien, la page correspondante vient remplacer la page courante. Pour revenir à la page précédente, cliquez sur le bouton **[!UICONTROL Retour]** de la barre d’outils. Pour revenir à la page d&#39;accueil, cliquez sur le bouton **[!UICONTROL Accueil]**.

  ![](assets/d_ncs_user_interface_back_home_buttons.png)

* Dans le cas d&#39;un menu ou d&#39;un raccourci vers un écran terminal (tel qu&#39;une application web, un programme, une diffusion, un rapport, une tâche, etc.), la page correspondante est affichée sous un nouvel onglet. Ainsi, vous pouvez naviguer d&#39;une page à l&#39;autre en cliquant sur l&#39;onglet correspondant.

  ![](assets/d_ncs_user_interface_tabs.png)

### Création d’un élément {#creating-an-element}

Dans chaque section des fonctions principales, vous pouvez naviguer parmi les éléments disponibles. Pour cela, utilisez les raccourcis proposés dans la section **[!UICONTROL Navigation]**. Le lien **[!UICONTROL Autres choix]** permet d&#39;accéder à toutes les autres pages, indépendamment de celles de la fonction courante.

Vous pouvez créer un nouvel élément (diffusion, application web, workflow, etc.) à l’aide des raccourcis dans la section **[!UICONTROL Créer]** sur la gauche de l’écran. Utilisez le bouton **[!UICONTROL Créer]** situé au-dessus de la liste pour ajouter de nouveaux éléments à la liste.

Par exemple, au niveau de la page des diffusions, utilisez le bouton **[!UICONTROL Créer]** pour créer une nouvelle diffusion.

![](assets/d_ncs_user_interface_tab_add_del.png)


## Utilisation de l’explorateur Adobe Campaign {#using-adobe-campaign-explorer}

L’explorateur Adobe Campaign est accessible à partir de l’icône de la barre d’outils. Il permet d’accéder à l’ensemble des fonctions d’Adobe Campaign, aux écrans de paramétrage et à une vue plus détaillée de certains éléments de la plateforme.

Pour en savoir plus sur l’explorateur Adobe Campaign, consultez ces pages dans la documentation de Campaign v8 (console) :

* [Présentation de l’interface utilisateur de Campaign](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/new/campaign-ui){target=_blank}

* [Paramètres de l’interface utilisateur de Campaign](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/config/configuration/ui-settings){target=_blank}

* [Gérer les dossiers et les vues dans l’explorateur](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/config/configuration/folders-and-views){target=_blank}.


## Utiliser des listes {#manage-and-customize-lists}

Dans la console cliente Campaign, les données sont affichées dans des listes. Vous pouvez adapter ces listes à vos besoins. Vous pouvez par exemple ajouter des colonnes, filtrer les données, comptabiliser les enregistrements, enregistrer et partager vos paramètres.

>[!NOTE]
>
>Pour savoir comment gérer et personnaliser des listes dans Adobe Campaign, reportez-vous à la documentation de [Campaign v8 (console)](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/config/configuration/ui-settings#customize-lists){target=_blank}.

## Gérer les énumérations{#managing-enumerations}

Une énumération (également appelée liste détaillée) est une liste prédéfinie de valeurs que vous pouvez utiliser pour renseigner certains champs. Les énumérations permettent de normaliser les valeurs de champ, de rendre la saisie de données plus cohérente et de simplifier les requêtes.

Une fois définies, les valeurs sont affichées dans une liste déroulante. Une valeur peut être sélectionnée directement ou saisie à l’aide d’une entrée prédictive, qui suggère et complète les entrées correspondantes. Certains champs contiennent des énumérations prédéfinies. Des énumérations supplémentaires peuvent être créées si nécessaire.

Découvrez comment **utiliser les énumérations** dans la documentation d’[Adobe Campaign v8 (console)](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/config/settings/enumerations){target=_blank}.

## Tutoriel vidéo {#video}

Cette vidéo présente l‘espace de travail de Campaign Classic.

>[!VIDEO](https://video.tv.adobe.com/v/39530?quality=12&captions=fre_fr)
