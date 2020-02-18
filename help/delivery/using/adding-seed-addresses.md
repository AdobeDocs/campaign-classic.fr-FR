---
title: Ajouter des adresses de contrôle
seo-title: Ajouter des adresses de contrôle
description: Ajouter des adresses de contrôle
seo-description: null
page-status-flag: never-activated
uuid: e94ddd46-bed6-4505-91b7-7e17abb0e9c8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
discoiquuid: 0b9b53bf-4dd2-416c-894e-393aded489f8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 4ac96bf0e54268832b84b17c3cc577af038cc712

---


# Ajouter des adresses de contrôle{#adding-seed-addresses}

## Adresses de contrôle dans une diffusion {#seed-addresses-in-a-delivery}

To add specific seed addresses for a delivery, click the **[!UICONTROL To]** link, then select the **[!UICONTROL Seed addresses]** tab.

![](assets/s_ncs_user_edit_del_addresses_tab.png)

Trois modes d&#39;insertion sont possibles :

1. Vous pouvez saisir les adresses de contrôle.

   Pour ce faire, cliquez sur le **[!UICONTROL Add]** bouton et définissez le contenu des champs d’adresse. Répétez cette opération pour chaque adresse. Voir à ce propos [cette section](../../message-center/using/managing-seed-addresses-in-transactional-messages.md#creating-a-seed-address).

1. Vous pouvez importer des modèles d&#39;adresses que vous pourrez adapter selon vos besoins.

   Pour ce faire, cliquez sur le **[!UICONTROL Import seed templates...]** lien et sélectionnez le dossier contenant les modèles d’adresse. Pour plus d’informations, reportez-vous à la section [Création de modèles](../../delivery/using/creating-seed-addresses.md#creating-seed-address-templates)d’adresse de départ.

   If necessary, once they are added, you can double-click them or click the **[!UICONTROL Detail...]** button to adapt the content of each address.

1. Vous pouvez créer une condition pour sélectionner dynamiquement les adresses de contrôle à insérer.

   Pour ce faire, cliquez sur le **[!UICONTROL Edit the dynamic condition...]** lien, puis entrez les paramètres de sélection de l’adresse de départ. Par exemple, vous pouvez inclure toutes les adresses de base contenues dans un dossier spécifique ou les adresses de base appartenant à un service spécifique de votre organisation.

   Vous trouverez un exemple dans cette section : Cas [d’utilisation : sélection des adresses de départ sur des critères](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md).

>[!NOTE]
>
>This option is used when the recipient table used is not the default **nms:recipient** table and you are using the Inbox Rendering functionality provided with Adobe Campaign&#39;s **[!UICONTROL Deliverability]** module.
>
>Pour plus d’informations, reportez-vous à la section [Utilisation d’un tableau](../../delivery/using/using-an-external-recipient-table.md) de destinataire externe et à la documentation sur le rendu [de la](../../delivery/using/inbox-rendering.md)boîte de réception.

Pour les diffusions courrier, vous pouvez personnaliser le mode d&#39;insertion des adresses dans le fichier d&#39;extraction. Par défaut, elles sont insérées dans l&#39;ordre de tri du fichier de sortie, mais vous pouvez choisir de les insérer à la fin ou au début du fichier, ou aléatoirement parmi les destinataires de la cible principale.

![](assets/s_ncs_user_edit_del_addresses_sort.png)

## Adresses de contrôle dans une opération {#seed-addresses-in-a-campaign}

To add seed addresses to a target for a campaign, select the operation and click the **[!UICONTROL Edit]** tab.

Cliquez sur le **[!UICONTROL Advanced campaign settings...]** lien, puis sur l’ **[!UICONTROL Seed addresses]** onglet, comme illustré ci-dessous :

![](assets/s_ncs_user_edit_op_addresses_tab.png)

Les adresses de contrôle insérées depuis l&#39;opération seront ajoutées à la cible de chacune des diffusions de cette opération.
