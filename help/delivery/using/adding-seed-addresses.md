---
product: campaign
title: Ajouter des adresses de contrôle
description: Ajouter des adresses de contrôle
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
feature: Seed Address
role: User
exl-id: ae6eb4b0-b419-4661-9d63-e758f0242a0f
TQID: https://experienceleague.adobe.com/pVYaTG48-HiK0RwJXgBbIMWa-o-R7jlEpauXNXvGi5E
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
feature_v2: id: b631758a-142d-425f-b9aa-f756d85cb979id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2: id: e95a583b-fcfa-4524-8666-46a29c828119id: c8da4fdd-eb94-4751-a43c-f82733fb2d6eid: d5bbe3da-ba85-4242-817e-54f7c4b943e0id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 355
ht-degree: 100%

---

# Ajouter des adresses de contrôle{#adding-seed-addresses}

## Adresses de contrôle dans une diffusion {#seed-addresses-in-a-delivery}

Pour ajouter des adresses de contrôle spécifiques à une diffusion, cliquez sur le lien **[!UICONTROL Pour]**, puis sélectionnez l&#39;onglet **[!UICONTROL Adresses de contrôle]**.

![](assets/s_ncs_user_edit_del_addresses_tab.png)

Trois modes d&#39;insertion sont possibles :

1. Vous pouvez saisir les adresses de contrôle.

   Pour cela, cliquez sur le bouton **[!UICONTROL Ajouter]** et définissez le contenu des champs de l’adresse.Répétez l’opération pour chaque adresse.

1. Vous pouvez importer des modèles d&#39;adresses que vous pourrez adapter selon vos besoins.

   Pour cela, cliquez sur le lien **[!UICONTROL Importer des adresses de contrôle...]** et sélectionnez le dossier contenant les modèles d&#39;adresses. Pour plus d’informations à ce sujet, consultez [cette section](creating-seed-addresses.md#creating-seed-address-templates).

   Au besoin, une fois ajoutées, vous pouvez double-cliquer dessus ou cliquer sur le bouton **[!UICONTROL Détail...]** pour adapter le contenu des champs de chaque adresse.

1. Vous pouvez créer une condition pour sélectionner dynamiquement les adresses de contrôle à insérer.

   Pour cela, cliquez sur le lien **[!UICONTROL Modifier la condition dynamique…]**, puis renseignez les paramètres de sélection des adresses de contrôle.Vous pouvez par exemple inclure toutes les adresses de contrôle contenues dans un dossier spécifique ou les adresses de contrôle appartenant à un service particulier de votre société.

   Vous trouverez un exemple dans la section : [Cas pratique : sélectionner des adresses de contrôle selon des critères](use-case-selecting-seed-addresses-on-criteria.md).

>[!NOTE]
>
>Cette option est utilisée lorsque la table des destinataires utilisée n’est pas la table **nms:recipient** par défaut et que vous utilisez la fonctionnalité Rendu de la boîte de réception fournie par le module **[!UICONTROL Délivrabilité]** d’Adobe Campaign.
>
>Voir à ce sujet la section [Utiliser une table de destinataires externe](using-an-external-recipient-table.md) et la documentation sur la fonctionnalité [Inbox rendering](inbox-rendering.md).

Pour les diffusions, vous pouvez également personnaliser le mode d’insertion des adresses dans le fichier d’extraction.Par défaut, elles sont insérées dans l’ordre de tri du fichier de sortie, mais vous pouvez choisir de les insérer au début ou à la fin du fichier, ou de manière aléatoire parmi les destinataires de la cible principale.

![](assets/s_ncs_user_edit_del_addresses_sort.png)

## Adresses de contrôle dans une opération {#seed-addresses-in-a-campaign}

Pour ajouter des adresses de contrôle dans la cible au niveau d&#39;une opération, sélectionnez l&#39;opération visée et cliquez sur l&#39;onglet **[!UICONTROL Edition]**.

Cliquez sur le lien **[!UICONTROL Paramètres avancés de l&#39;opération...]** puis sur l&#39;onglet **[!UICONTROL Adresses de contrôle]**, comme ci-dessous :

![](assets/s_ncs_user_edit_op_addresses_tab.png)

Les adresses de contrôle insérées depuis l&#39;opération seront ajoutées à la cible de chacune des diffusions de cette opération.
