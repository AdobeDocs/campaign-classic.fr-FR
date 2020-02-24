---
title: Créer des adresses de contrôle
seo-title: Créer des adresses de contrôle
description: Créer des adresses de contrôle
seo-description: null
page-status-flag: never-activated
uuid: 0dae107a-7b53-4096-93c3-9517b402cbc9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
discoiquuid: 6dad49af-4818-471b-9df1-057cc6b9a68a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Créer des adresses de contrôle{#creating-seed-addresses}

Les adresses de contrôle ne sont pas gérées via les profils et cibles standards, mais dans un nœud dédié de l&#39;arborescence Adobe Campaign, sous **[!UICONTROL Ressources > Gestion de campagne > Adresses de contrôle]**.

You can create sub-folders in order to organize the seed addresses. To do this, right-click the **[!UICONTROL Seed addresses]** node and select **[!UICONTROL Create a new &#39;Seed addresses&#39; folder]**. Name the sub-folder and then press **[!UICONTROL Enter]** to validate. You can now create or copy seed addresses to this sub-folder. For more on this, refer to [Defining addresses](#defining-addresses).

Adobe Campaign vous permet également de créer des modèles d’adresse de départ importés dans des remises ou des campagnes et adaptés en fonction des besoins spécifiques des livraisons et campagnes concernées. Reportez-vous à [Création de modèles](#creating-seed-address-templates)d’adresse de départ.

## Définir des adresses {#defining-addresses}

Pour créer des adresses de contrôle, procédez comme suit :

1. Cliquez sur le bouton **[!UICONTROL Nouveau]** situé au-dessus de la liste des adresses de contrôle.
1. Saisissez les données associées à l&#39;adresse dans les champs correspondants de l&#39;onglet **[!UICONTROL Destinataire]**. Les champs disponibles correspondent aux champs standards dans les profils des destinataires de la diffusion (nms:recipient table) : nom, prénom, email, etc.

   >[!NOTE]
   >
   >Le libellé de l&#39;adresse reprend automatiquement le nom et le prénom saisis.
   >
   >Pour chaque adresse de contrôle, il n&#39;est pas nécessaire de renseigner tous les champs des différents onglets. Les éléments de personnalisation manquants sont renseignés aléatoirement lors de l&#39;envoi.

   ![](assets/s_ncs_user_seedlist_new_address.png)

1. Indiquez dans l&#39;onglet **[!UICONTROL Champs de l&#39;adresse]** les valeurs qui seront insérées dans les logs de la diffusion lors de la phase d&#39;analyse (dans la table **[!UICONTROL nms:broadLog]**).
1. Indiquez dans l&#39;onglet **[!UICONTROL Données additionnelles]** les données de personnalisation utilisées dans les diffusions créées dans les workflows avec Datamanagement et que vous souhaitez voir renseignées par une valeur spécifique.

## Créer des modèles d&#39;adresses de contrôle {#creating-seed-address-templates}

Pour créer des modèles d&#39;adresses, qui seront importées et pourront être modifiées pour chaque diffusion, la procédure est la même que celle permettant de définir une nouvelle adresse de contrôle, mais les adresses des modèles doivent être stockées dans un dossier de type &#39;Modèle&#39;.

Pour définir un dossier de modèle, la procédure est la suivante :

1. Créez un dossier de type **[!UICONTROL Adresses de contrôle]**, cliquez avec le bouton droit dessus et sélectionnez **[!UICONTROL Propriétés...]**.

   ![](assets/s_ncs_user_seedlist_template_folder.png)

1. Click the **[!UICONTROL Restriction]** tab and add the following filtering condition: **@isModel = true**.

   ![](assets/s_ncs_user_seedlist_folder_is_model.png)

   Les adresses stockées dans ce dossier pourront ainsi être utilisées comme des modèles d&#39;adresses. Vous pouvez les importer dans des remises ou des campagnes et les adapter en fonction des besoins spécifiques des livraisons et campagnes concernées (voir [Ajout d’adresses](../../delivery/using/adding-seed-addresses.md)de base).
