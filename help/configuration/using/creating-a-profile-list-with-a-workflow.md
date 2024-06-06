---
product: campaign
title: Création d'une liste de profils avec un workflow
description: Découvrez comment créer une liste de profils dans un workflow
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
feature: Workflows, Profiles
role: User
exl-id: 6b308299-4d07-4c9e-bd2f-a0860c41cf02
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: ht
source-wordcount: '212'
ht-degree: 100%

---

# Création d&#39;une liste de profils avec un workflow{#creating-a-profile-list-with-a-workflow}


Pour créer une liste de type **[!UICONTROL Liste]** basée sur la nouvelle table des destinataires, vous devez créer un workflow de ciblage qui va générer la liste.

Pour plus d&#39;informations sur les listes dans Campaign, consultez [cette section](../../platform/using/creating-and-managing-lists.md#about-lists-in-adobe-campaign).

![](assets/do-not-localize/how-to-video.png) [Découvrez cette fonctionnalité en vidéo](../../platform/using/creating-and-managing-lists.md#create-list-in-a-wf-video)

Pour créer un workflow de ciblage et mettre à jour des destinataires dans une table de destinataires personnalisée, procédez comme suit :

1. Ouvrez le nœud **[!UICONTROL Profils et cibles > Traitements > Workflows de ciblage]** dans l&#39;explorateur.
1. Créez un nouveau workflow de ciblage.
1. Placez une activité **Requête** puis une activité **Mise à jour de liste**.

   ![](assets/mapping_create_list_workflow01.png)

1. Double cliquez sur l&#39;activité **Requête** puis cliquez sur **[!UICONTROL Editer la requête]** afin de choisir une dimension de ciblage basée sur le schéma de la nouvelle table de destinataires (dans le cas de l&#39;exemple : **Individual**). Cliquez sur **[!UICONTROL Terminer]** pour valider.

   ![](assets/mapping_create_list_workflow03.png)

1. Double cliquez sur l&#39;activité **Mise à jour de la liste** puis sélectionnez le bouton radio **[!UICONTROL Créer la liste si besoin (Nom calculé)]**.

   ![](assets/mapping_create_list_workflow02.png)

1. Sélectionner le dossier de création de la nouvelle liste.
1. Exécuter le workflow pour créer la liste.
1. Visualiser le résultat dans le noeud de l&#39;arborescence que vous avez choisi lors de l&#39;activité **[!UICONTROL Mise à jour de la liste]**.

   Le tableau de bord précise le schéma sur lequel est basée la liste, comme le montre l&#39;écran ci-dessous :

   ![](assets/mapping_list_view.png)
