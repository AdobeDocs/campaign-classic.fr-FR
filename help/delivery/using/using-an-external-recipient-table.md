---
product: campaign
title: Utiliser une table de destinataires externe
description: Utiliser une table de destinataires externe
badge-v7: label="v7" type="Informative" tooltip="S’applique à Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="S’applique également à Campaign v8"
feature: Audiences
exl-id: b6aabc68-707d-4c6c-b008-277609166c6c
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 83%

---

# Utiliser une table de destinataires externe{#using-an-external-recipient-table}



Si le tableau des diffusions est un tableau externe, vous devrez effectuer des configurations supplémentaires. Le schéma **[!UICONTROL nms:seedmember]** doit être étendu. Un onglet est ajouté au niveau des adresses de contrôle afin de définir les champs adéquats, comme dans l&#39;exemple ci-dessous :

![](assets/s_ncs_user_seedlist_new_tab.png)

Dans ce cas, pour ajouter les adresses de contrôle dans la diffusion, renseignez directement les champs adéquats dans l&#39;onglet correspondant ou importez des modèles d&#39;adresses :

![](assets/s_ncs_user_seedlist_add_new_tab.png)

L&#39;extension du schéma **nms:seedMember** est présentée dans [cette section](../../configuration/using/seed-addresses.md).
