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

Pour accéder aux fonctionnalités avancées de gestion des destinataires, vous devez modifier l’arborescence d’Adobe Campaign. Pour ce faire, cliquez sur le **[!UICONTROL Explorer]** bouton dans la barre d’outils.

Par défaut, les destinataires sont stockés dans le **[!UICONTROL Profiles and targets]** noeud de l’arborescence Adobe Campaign. A partir du même noeud, vous pouvez créer un ou plusieurs dossiers et sous-dossiers pour stocker les profils de destinataires.

Chaque noeud correspond à un dossier. Les données de chaque dossier doivent être considérées comme cloisonnées les unes des autres. Ainsi, dans le cas de dossiers de destinataires multiples, la gestion des doublons sera plus délicate.

>[!NOTE]
>
>Pour afficher la liste de tous les destinataires dans la base de données, vous devez créer une vue. Reportez-vous à [Dossiers et vues](../../platform/using/access-management.md#folders-and-views).

## Déplacer un destinataire {#moving-recipients}

Vous pouvez sélectionner un ou plusieurs destinataires et le(s) déplacer d&#39;un dossier vers une autre par un glisser-déposer depuis la liste des destinataires vers le dossier visé. Un message d&#39;avertissement vous permet de confirmer l&#39;opération.

## Dupliquer un destinataire {#copying-a-recipient}

You can copy a recipient in the same folder by right-clicking the desired recipient and selecting **[!UICONTROL Copy]**.

## Supprimer des destinataires {#deleting-recipients}

Pour supprimer des destinataires, déplacez-les dans un dossier spécifique, puis purgez le contenu de ce dossier. Il est **vivement recommandé de ne pas utiliser** l’ **[!UICONTROL Delete]** option dans ce cas.

To purge a folder, use the **[!UICONTROL Actions > Purge folder]** menu, accessed by right-clicking the desired folder.

![](assets/s_ncs_user_purge_folder.png)

Cliquez sur **[!UICONTROL Start]** pour lancer l’opération. La section centrale de la fenêtre affiche l’état de progression, comme illustré ci-dessous :

![](assets/s_ncs_user_purge_folder_start.png)

