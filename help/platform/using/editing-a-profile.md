---
title: Editer un profil
seo-title: Editer un profil
description: Editer un profil
seo-description: null
page-status-flag: never-activated
uuid: ad3cd54e-b22f-4fae-8d2a-3e0d3e45fffb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: profile-management
discoiquuid: 93dd29e8-cf0a-4010-a3cc-f68c52c0d9ef
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 51e4d72abf3a1f48700ca38566dbf06dd24594b8

---


# Editer un profil{#editing-a-profile}

Pour consulter les informations relatives à un profil, cliquez sur son nom dans la liste des profils.

Le détail du profil est alors affiché dans un nouvel onglet.

![](assets/s_user_recipient_edit.png)

Les données relatives à un profil sont regroupées dans des onglets.

Les onglets et leur contenu dépendent de votre configuration et des packages installés.

>[!CAUTION]
>
>Le schéma XML et le formulaire qui concernent les champs du tableau des profils sont accessibles via le **[!UICONTROL Administration > Configuration > Data schemas]** noeud de l’arborescence Adobe Campaign. Seuls les utilisateurs experts peuvent apporter des modifications à ces schémas.
>
>Voir à ce propos [cette page](../../configuration/using/about-schema-edition.md).

## Onglet Général {#general-tab}

Cet écran contient toutes les informations générales relatives au profil sélectionné. Il contient notamment son nom, son prénom, son adresse email, le format de réception de ses emails, etc. Il se présente comme suit :

![](assets/s_ncs_user_profile_general_tab.png)

>[!NOTE]
>
>Lorsque l’ **[!UICONTROL No longer contact (by any channel)]** option est sélectionnée, cela signifie que le profil est placé sur liste noire, c’est-à-dire qu’il a exprimé le souhait de ne pas être contacté (par exemple, en cliquant sur un lien de désabonnement dans un bulletin d’information). Ils ne seront plus ciblés par les livraisons sur n&#39;importe quel canal (courriel, courrier électronique, etc.). Voir à ce propos [cette page](../../delivery/using/understanding-quarantine-management.md).

## Onglet Coordonnées {#contact-information-tab}

Cet écran contient les coordonnées postales du profil sélectionné. Il se présente comme suit :

![](assets/s_ncs_user_profile_details_tab.png)

L&#39;indice de qualité de cette adresse est reporté dans cet écran, ainsi que le nombre d&#39;erreurs sur l&#39;adresse. Ces informations sont directement implémentées par le prestataire de courrier en fonction du nombre d&#39;erreur rencontrées lors des précédentes diffusions. Elles ne peuvent pas être modifiées manuellement.

## Onglet Autres {#other-tab}

Cet écran contient des champs définis par l’utilisateur qui peuvent être personnalisés en fonction des besoins. Vous pouvez également modifier les noms des champs et définir leur format, via **[!UICONTROL Field properties...]**, comme illustré ci-dessous :

![](assets/s_ncs_user_profile_others_tab.png)

>[!NOTE]
>
>Pour plus d&#39;informations sur les propriétés des champs et l&#39;ajout de champs, consultez [cette page](../../configuration/using/new-field-wizard.md).

## Onglet Listes {#lists-tab}

Cet écran affiche le ou les groupes auxquels appartient le profil sélectionné. Cliquez sur **[!UICONTROL Add]** pour abonner le profil à une liste. Cliquez sur **[!UICONTROL Detail]** pour afficher la description et la liste des profils dans la liste sélectionnée.

![](assets/s_ncs_user_profile_groups_tab_details.png)

Pour plus d’informations, reportez-vous à la section [Création et gestion des listes](../../platform/using/creating-and-managing-lists.md).

## Onglet Abonnements {#subscriptions-tab}

Cet écran contient les services d&#39;information auxquels s&#39;est abonné le profil.

![](assets/s_ncs_user_profile_subscript_tab_details.png)

Le **[!UICONTROL Detail]** bouton affiche les propriétés de l’abonnement sélectionné. Le **[!UICONTROL Add]** bouton permet d’ajouter manuellement un nouvel abonnement.

Voir à ce propos [cette page](../../delivery/using/managing-subscriptions.md).

## Onglet Diffusions {#deliveries-tab}

Cet écran permet de visualiser les logs de diffusion du profil sélectionné. Vous pouvez ainsi visualiser les libellés, dates et statuts des actions de diffusion adressées au profil, tous canaux confondus.

![](assets/s_ncs_user_profile_delivery_tab.png)

## Onglet Tracking {#tracking-tab}

Cet écran est utilisé pour consulter les logs de tracking du profil sélectionné. Ces informations permettent de suivre le comportement du profil suite aux diffusions.

![](assets/s_ncs_user_profile_tracking_tab.png)

Cet onglet présente le cumul de toutes les URL trackées dans les diffusions.

La liste est paramétrable et contient typiquement : l&#39;URL cliquée, la date et l&#39;heure du clic, le document dans lequel l&#39;URL figurait.

>[!NOTE]
>
>Pour plus d&#39;informations sur les fonctionnalités de mise en œuvre du tracking, consultez [cette page](../../delivery/using/monitoring-a-delivery.md).

