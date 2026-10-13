---
product: campaign
title: Création d'une liste de profils avec un workflow
description: Découvrez comment créer une liste de profils dans un workflow
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Workflows, Profiles
role: User
exl-id: 6b308299-4d07-4c9e-bd2f-a0860c41cf02
TQID: 'https://experienceleague.adobe.com/km2D2qnUAdgDCauLUYcWSC-J567twPEyvaZBsLDAOKA'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
  - id: afa4204e-6d08-4e29-bc35-26aafb656d48
    internal-label: Profiles and audiences
subfeature_v2:
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
  - id: f529d0bd-1401-4c88-9833-43228cc1d40f
    internal-label: Profiles
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
source-git-commit: 59d78c785d8984861fd537c2f64f82a7d2d77fbf
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 77%
---
# Création d&#39;une liste de profils avec un workflow{#creating-a-profile-list-with-a-workflow}


Pour créer une liste de type **[!UICONTROL Liste]** basée sur la nouvelle table des destinataires, vous devez créer un workflow de ciblage qui va générer la liste.

Pour plus d’informations sur les listes dans Campaign, consultez [cette section](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/audience/create-audiences/create-audiences#create-a-list-of-contacts){target="_blank"} (documentation de Campaign v8).

![](assets/do-not-localize/how-to-video.png) [Découvrez cette fonctionnalité en vidéo](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/audience/create-audiences/create-audiences#create-a-list-wf){target="_blank"} (documentation de Campaign v8)

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
