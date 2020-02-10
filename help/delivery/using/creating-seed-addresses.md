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

Seed addresses are not managed via standard profiles and targets, but in a dedicated node of the Adobe Campaign hierarchy **[!UICONTROL Resources > Campaign management > Seed addresses]**.

Vous pouvez créer des sous-dossiers afin d’organiser les adresses de départ. Pour ce faire, cliquez avec le bouton droit sur le **[!UICONTROL Seed addresses]** noeud et sélectionnez **[!UICONTROL Create a new 'Seed addresses' folder]**. Nommez le sous-dossier, puis appuyez sur **[!UICONTROL Enter]** pour valider. Vous pouvez désormais créer ou copier des adresses de base dans ce sous-dossier. For more on this, refer to [Defining addresses](#defining-addresses).

Adobe Campaign vous permet également de créer des modèles d’adresse de départ importés dans des remises ou des campagnes et adaptés en fonction des besoins spécifiques des livraisons et campagnes concernées. Reportez-vous à [Création de modèles](#creating-seed-address-templates)d’adresse de départ.

## Définir des adresses {#defining-addresses}

Pour créer des adresses de contrôle, procédez comme suit :

1. Click the **[!UICONTROL New]** button above the list of seed addresses.
1. Entrez les données liées à l&#39;adresse dans les champs correspondants de l&#39; **[!UICONTROL Recipient]** onglet. Les champs disponibles correspondent aux champs standard des profils des destinataires (tableau nms:destinataire) : nom, prénom, courriel, etc.

   >[!NOTE]
   >
   >Le libellé de l&#39;adresse reprend automatiquement le nom et le prénom saisis.
   >
   >Pour chaque adresse de contrôle, il n&#39;est pas nécessaire de renseigner tous les champs des différents onglets. Les éléments de personnalisation manquants sont renseignés aléatoirement lors de l&#39;envoi.

   ![](assets/s_ncs_user_seedlist_new_address.png)

1. In the **[!UICONTROL Seed fields]** tab, enter the values that will be inserted in the delivery logs during the analysis phase (in the **[!UICONTROL nms:broadLog]** table).
1. In the **[!UICONTROL Additional data]** tab, enter the personalization data used for the deliveries created in the Datamanagement workflows and which you want to assign a specific value to.

## Créer des modèles d&#39;adresses de contrôle {#creating-seed-address-templates}

Pour créer des modèles d&#39;adresses, qui seront importées et pourront être modifiées pour chaque diffusion, la procédure est la même que celle permettant de définir une nouvelle adresse de contrôle, mais les adresses des modèles doivent être stockées dans un dossier de type &#39;Modèle&#39;.

Pour définir un dossier de modèle, la procédure est la suivante :

1. Create a new **[!UICONTROL Seed addresses]** type folder, right-click the folder then select **[!UICONTROL Properties...]**.

   ![](assets/s_ncs_user_seedlist_template_folder.png)

1. Click the **[!UICONTROL Restriction]** tab and add the following filtering condition: **@isModel = true**.

   ![](assets/s_ncs_user_seedlist_folder_is_model.png)

   Les adresses stockées dans ce dossier pourront ainsi être utilisées comme des modèles d&#39;adresses. Vous pouvez les importer dans des remises ou des campagnes et les adapter en fonction des besoins spécifiques des livraisons et campagnes concernées (voir [Ajout d’adresses](../../delivery/using/adding-seed-addresses.md)de base).
