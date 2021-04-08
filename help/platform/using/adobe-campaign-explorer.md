---
solution: Campaign Classic
product: campaign
title: Utiliser Adobe Campaign Explorer
description: Découvrez comment utiliser Campaign Explorer
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 21656cc2-15a1-4156-8897-ea4fe3e9b97f,f91d69a4-b794-40f0-b450-de862d7333e2
translation-type: tm+mt
source-git-commit: 8405eefb2e79deeeca07e0c8231bdfa5200ec185
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 44%

---

# Utiliser l&#39;explorateur Adobe Campaign {#using-adobe-campaign-explorer}

L&#39;explorateur Adobe Campaign est accessible à partir de l&#39;icône de la barre d&#39;outils. Il permet d&#39;accéder à l&#39;ensemble des fonctions d&#39;Adobe Campaign, aux écrans de paramétrage et à une vue plus détaillée de certains éléments de la plate-forme.

L&#39;espace de travail **[!UICONTROL Explorateur]** est divisé en trois zones :

![](assets/s_ncs_user_navigation.png)

**1 - Arbre** : vous pouvez personnaliser le contenu de l’arborescence (ajouter, déplacer ou supprimer des noeuds). Cette procédure est destinée aux utilisateurs experts uniquement. Voir à ce propos [cette section](#about-navigation-hierarchy).).

**2 - Liste** : vous pouvez filtrer cette liste, lancer des recherches, ajouter des informations ou trier les données. [En savoir plus](adobe-campaign-ui-lists.md).

**3 - Détails** : vous pouvez afficher le détail de l&#39;élément sélectionné. L&#39;icône située dans la section supérieure droite permet d&#39;afficher ces informations en plein écran.

## Dossiers et arborescence de navigation{#about-navigation-hierarchy}

L&#39;arborescence de navigation fonctionne comme un navigateur de fichiers (par exemple, l&#39;Explorateur Windows). Les dossiers peuvent contenir des sous-dossiers. La sélection d’un noeud affiche la vue correspondante.

La vue affichée est une liste associée à un schéma et à un formulaire de saisie pour l&#39;édition de la ligne sélectionnée.

![](assets/d_ncs_integration_navigation.png)

Pour ajouter un nouveau dossier dans l&#39;arborescence, cliquez avec le bouton droit sur le dossier dans la branche duquel vous souhaitez insérer un dossier et choisissez **[!UICONTROL Ajouter un dossier]**. Dans le menu contextuel, sélectionnez le type de dossier à créer.

![](assets/d_ncs_integration_navigation_create.png)

Découvrez comment configurer l&#39;arborescence de navigation de Campaign [dans cette section](../../configuration/using/configuration.md).

Découvrez comment définir des autorisations sur les dossiers [dans cette section](access-management-folders.md).

## Meilleures pratiques de configuration des dossiers

* **Utiliser des dossiers intégrés**

   L’utilisation des dossiers intégrés facilite l’utilisation, la maintenance et le dépannage de l’application pour les personnes qui ne sont pas impliquées dans le projet. Vous ne devez pas créer de structures de dossiers personnalisées pour les destinataires, les listes, les diffusions, etc., mais utiliser les dossiers standard tels que Administration, Profils et Cibles, Gestion de campagne.

* **Création de sous-dossiers**

   Placez les workflows techniques sous le dossier standard : Administration / Production / Workflows techniques, et créer des sous-répertoires par type de processus.

* **Définir une convention d’affectation de nom**

   Par exemple, vous pouvez nommer les workflows par ordre alphabétique, de sorte qu’ils s’affichent dans l’ordre d’exécution.

   Par exemple :

   * A1 - destinataires d&#39;importation, débuts à 10 h ;
   * A2 - billets d&#39;importation, débuts à 11h00.

* **Créer des modèles pour les utilisateurs avec lesquels début**

   Créez des modèles de diffusion, des modèles de processus, des modèles de campagne spécifiques aux utilisateurs. Cette structure permet de gagner du temps et de s’assurer que le mappage et les typologies de diffusion appropriés sont utilisés pour chaque utilisateur.

## Résolution d&#39;écran {#screen-resolution}

Pour une navigation et une convivialité optimales, Adobe recommande l&#39;utilisation d&#39;une résolution d&#39;écran minimale de 1 600x900 pixels.

>[!CAUTION]
>
>Les résolutions inférieures à 1 600 x 900 pixels sont prises en charge par Adobe Campaign.

Dans l&#39;espace de travail de l&#39;**[!UICONTROL Explorateur]**, si certaines parties de la zone **[!UICONTROL Détails]** semblent tronquées, développez-la à l&#39;aide de la flèche située en haut de la zone ou cliquez sur le bouton **[!UICONTROL Agrandir]**.

![](assets/s_ncs_user_resolution.png)

## Parcourir et personnaliser des listes {#browsing-lists}

Découvrez comment parcourir, gérer et personnaliser les listes [dans cette section](adobe-campaign-ui-lists.md).
