---
solution: Campaign Classic
product: campaign
title: Utiliser une table de destinataires externe
description: Utiliser une table de destinataires externe
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 100%

---


# Utiliser une table de destinataires externe{#using-an-external-recipient-table}

Si la table des diffusions est une table externe, vous devez effectuer des paramétrages complémentaires. Le schéma **[!UICONTROL nms:seedmember]** doit alors être étendu. Un onglet supplémentaire est alors ajouté au niveau des adresses de contrôle afin de définir les champs adéquats, comme dans l&#39;exemple ci-dessous :

![](assets/s_ncs_user_seedlist_new_tab.png)

Dans ce cas, pour ajouter les adresses de contrôle dans la diffusion, renseignez directement les champs adéquats dans l&#39;onglet correspondant ou importez des modèles d&#39;adresses :

![](assets/s_ncs_user_seedlist_add_new_tab.png)

L&#39;extension du schéma **nms:seedMember** est présentée dans [cette section](../../configuration/using/seed-addresses.md).
