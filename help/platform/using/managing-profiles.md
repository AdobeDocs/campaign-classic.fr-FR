---
product: campaign
title: Gérer des profils
description: Gérer des profils
feature: Profiles
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
audience: platform
content-type: reference
topic-tags: profile-management
exl-id: e1d0556a-6f30-4863-9025-eb9c1b8b53d3
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 97%

---

# Gestion des profils{#managing-profiles}



## Arborescence des destinataires {#recipient-tree}

Pour accéder aux fonctionnalités avancées de gestion des destinataires, vous devez éditer l&#39;arborescence d&#39;Adobe Campaign. Pour cela, cliquez sur le bouton **[!UICONTROL Explorateur]** de la barre d&#39;outils.

Le dossier des destinataires est positionné par défaut sous le noeud **[!UICONTROL Profils et cibles]** de l&#39;arborescence d&#39;Adobe Campaign. Vous pouvez créer, à partir du même noeud, un ou plusieurs dossiers et sous-dossiers afin d&#39;y stocker les profils des destinataires.

Chaque noeud correspond à un dossier. Les données de chaque dossier doivent être considérées comme cloisonnées les unes des autres. Ainsi, dans le cas de dossiers de destinataires multiples, la gestion des doublons sera plus délicate.

>[!NOTE]
>
>Pour afficher la liste de tous les destinataires de la base, vous devez créer une vue. En savoir plus dans la section [Dossiers et vues](../../platform/using/access-management-folders.md).

## Déplacer des destinataires {#moving-recipients}

Vous pouvez sélectionner un ou plusieurs destinataires et le(s) déplacer en effectuant un glisser-déposer depuis la liste des destinataires vers le dossier visé. Un message d’avertissement vous permet de confirmer cette action.

## Copier un destinataire {#copying-a-recipient}

Vous pouvez copier un destinataire dans le même dossier en cliquant avec le bouton droit sur le destinataire visé et en sélectionnant **[!UICONTROL Copier]**.

## Supprimer des destinataires {#deleting-recipients}

Pour supprimer des destinataires, vous devez au préalable les déplacer dans un dossier spécifique puis purger le contenu de ce dossier. Il est **vivement déconseillé** d&#39;utiliser l&#39;option **[!UICONTROL Supprimer]** dans ce cas de figure.

Pour purger un dossier, utilisez le menu **[!UICONTROL Actions > Purger le dossier]**, accessible à partir du bouton droit de la souris sur le dossier visé.

![](assets/s_ncs_user_purge_folder.png)

Cliquez sur **[!UICONTROL Démarrer]** pour lancer l&#39;opération. La section centrale de la fenêtre affiche l&#39;état d&#39;avancement, comme dans l&#39;exemple ci-dessous :

![](assets/s_ncs_user_purge_folder_start.png)
