---
title: Gestion de profils
seo-title: Gestion de profils
description: Gestion de profils
seo-description: null
page-status-flag: never-activated
uuid: f045dd5e-e069-4293-8c44-49d71071b041
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: profile-management
discoiquuid: ef7aa3a0-249f-46eb-9300-5b97bce31c8c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 51e4d72abf3a1f48700ca38566dbf06dd24594b8

---


# Gestion de profils{#managing-profiles}

## Arborescence des destinataires {#recipient-tree}

Pour accéder aux fonctionnalités avancées de gestion des destinataires, vous devez éditer l&#39;arborescence d&#39;Adobe Campaign. Pour cela, cliquez sur le bouton **[!UICONTROL Explorateur]** de la barre d&#39;outils.

Le dossier des destinataires est positionné par défaut sous le noeud **[!UICONTROL Profils et cibles]** de l&#39;arborescence d&#39;Adobe Campaign. Vous pouvez créer, à partir du même noeud, un ou plusieurs dossiers et sous-dossiers afin d&#39;y stocker les profils des destinataires.

Chaque noeud correspond à un dossier. Les données de chaque dossier doivent être considérées comme cloisonnées les unes des autres. Ainsi, dans le cas de dossiers de destinataires multiples, la gestion des doublons sera plus délicate.

>[!NOTE]
>
>Pour afficher la liste de tous les destinataires dans la base de données, vous devez créer une vue. Reportez-vous à [Dossiers et vues](../../platform/using/access-management.md#folders-and-views).

## Déplacer un destinataire {#moving-recipients}

Vous pouvez sélectionner un ou plusieurs destinataires et le(s) déplacer d&#39;un dossier vers une autre par un glisser-déposer depuis la liste des destinataires vers le dossier visé. Un message d&#39;avertissement vous permet de confirmer l&#39;opération.

## Dupliquer un destinataire {#copying-a-recipient}

Vous pouvez dupliquer un destinataire dans le même dossier à partir du bouton droit de la souris sur le destinataire visé en choisissant **[!UICONTROL Dupliquer]**.

## Supprimer des destinataires {#deleting-recipients}

Pour supprimer des destinataires, vous devez au préalable les déplacer dans un dossier spécifique puis purger le contenu de ce dossier. Il est **vivement déconseillé** d&#39;utiliser l&#39;option **[!UICONTROL Supprimer]** dans ce cas de figure.

Pour purger un dossier, utilisez le menu **[!UICONTROL Actions > Purger le dossier]**, accessible à partir du bouton droit de la souris sur le dossier visé.

![](assets/s_ncs_user_purge_folder.png)

Cliquez sur **[!UICONTROL Démarrer]** pour lancer l&#39;opération. La section centrale de la fenêtre affiche l&#39;état d&#39;avancement, comme dans l&#39;exemple ci-dessous :

![](assets/s_ncs_user_purge_folder_start.png)

