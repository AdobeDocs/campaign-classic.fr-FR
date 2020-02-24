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

Pour ajouter des adresses de contrôle spécifiques à une diffusion, cliquez sur le lien **[!UICONTROL Pour]**, puis sélectionnez l&#39;onglet **[!UICONTROL Adresses de contrôle]**.

![](assets/s_ncs_user_edit_del_addresses_tab.png)

Trois modes d&#39;insertion sont possibles :

1. Vous pouvez saisir les adresses de contrôle.

   Pour cela, cliquez sur le bouton **[!UICONTROL Ajouter]** et définissez le contenu des champs de l&#39;adresse. Répétez l&#39;opération pour chaque adresse à ajouter. Voir à ce propos [cette section](../../message-center/using/managing-seed-addresses-in-transactional-messages.md#creating-a-seed-address).

1. Vous pouvez importer des modèles d&#39;adresses que vous pourrez adapter selon vos besoins.

   **[!UICONTROL Pour ce faire, cliquez sur le bouton]** Importer les modèles de base... et sélectionnez le dossier contenant les modèles d’adresse. Pour plus d’informations, reportez-vous à la section [Création de modèles](../../delivery/using/creating-seed-addresses.md#creating-seed-address-templates)d’adresse de départ.

   **[!UICONTROL Si nécessaire, une fois ajoutés, vous pouvez double-cliquer dessus ou cliquer sur le]** détail... pour adapter le contenu de chaque adresse.

1. Vous pouvez créer une condition pour sélectionner dynamiquement les adresses de contrôle à insérer.

   Pour cela, cliquez sur le lien **[!UICONTROL Editer la condition dynamique...]**, puis indiquez les paramètres de sélection des adresses de contrôle. Vous pouvez par exemple inclure toutes les adresses de contrôle contenues dans un dossier spécifique ou les adresses de contrôle appartenant à un service particulier de votre société.

   Vous trouverez un exemple dans cette section : Cas [d’utilisation : sélection des adresses de départ sur des critères](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md).

>[!NOTE]
>
>Cette option est notamment utilisée lorsque la table des destinataires utilisée n&#39;est pas la table par défaut **nms:recipient** et que vous utilisez la fonctionnalité d&#39;Inbox Rendering fournie avec le module de **[!UICONTROL Délivrabilité]** d&#39;Adobe Campaign.
>
>Pour plus d’informations, reportez-vous à la section [Utilisation d’un tableau](../../delivery/using/using-an-external-recipient-table.md) de destinataire externe et à la documentation sur le rendu [de la](../../delivery/using/inbox-rendering.md)boîte de réception.

Pour les diffusions courrier, vous pouvez personnaliser le mode d&#39;insertion des adresses dans le fichier d&#39;extraction. Par défaut, elles sont insérées dans l&#39;ordre de tri du fichier de sortie, mais vous pouvez choisir de les insérer à la fin ou au début du fichier, ou aléatoirement parmi les destinataires de la cible principale.

![](assets/s_ncs_user_edit_del_addresses_sort.png)

## Adresses de contrôle dans une opération {#seed-addresses-in-a-campaign}

Pour ajouter des adresses de contrôle dans la cible au niveau d&#39;une opération, sélectionnez l&#39;opération visée et cliquez sur l&#39;onglet **[!UICONTROL Edition]**.

Cliquez sur le lien **[!UICONTROL Paramètres avancés de l&#39;opération...]** puis sur l&#39;onglet **[!UICONTROL Adresses de contrôle]**, comme ci-dessous :

![](assets/s_ncs_user_edit_op_addresses_tab.png)

Les adresses de contrôle insérées depuis l&#39;opération seront ajoutées à la cible de chacune des diffusions de cette opération.
