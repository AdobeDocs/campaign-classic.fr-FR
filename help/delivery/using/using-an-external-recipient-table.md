---
title: Utiliser une table de destinataires externe
seo-title: Utiliser une table de destinataires externe
description: Utiliser une table de destinataires externe
seo-description: null
page-status-flag: never-activated
uuid: a6147425-14f0-41e8-a47f-3e7072deafa7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
discoiquuid: 92c32b2d-d8bf-41ab-9349-ef4a15f10521
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Utiliser une table de destinataires externe{#using-an-external-recipient-table}

Si la table des diffusions est une table externe, vous devez effectuer des paramétrages complémentaires. Le schéma **[!UICONTROL nms:seedmember]** doit alors être étendu. Un onglet supplémentaire est alors ajouté au niveau des adresses de contrôle afin de définir les champs adéquats, comme dans l&#39;exemple ci-dessous :

![](assets/s_ncs_user_seedlist_new_tab.png)

Dans ce cas, pour ajouter les adresses de contrôle dans la diffusion, renseignez directement les champs adéquats dans l&#39;onglet correspondant ou importez des modèles d&#39;adresses :

![](assets/s_ncs_user_seedlist_add_new_tab.png)

L&#39;extension du schéma **nms:seedMember** est présentée dans [cette section](../../configuration/using/seed-addresses.md).
