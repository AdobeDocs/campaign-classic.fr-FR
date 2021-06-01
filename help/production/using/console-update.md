---
product: campaign
title: Mise à jour de la console
description: Mise à jour de la console
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3a127bbe-9abb-4b5b-bd7e-e1ea550929ba
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '67'
ht-degree: 100%

---

# Mise à jour de la console{#console-update}

Si vous avez coché l&#39;option **[!UICONTROL Ne pas demander la mise à jour de la console]** et que vous souhaitez réactiver la demande de mise à jour, la procédure est la suivante :

1. Ouvrez l’éditeur de la base de registre via la commande **regedit** depuis le menu **[!UICONTROL Démarrer > Exécuter]** de Windows.

   ![](assets/ncs_console_update_1.png)

1. Dans l’arborescence, affichez les options du nœud **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]**.
1. Supprimez l&#39;entrée **[!UICONTROL confAdvisedUpgrade]** et fermez l&#39;éditeur de base de registre.

   ![](assets/ncs_console_update_2.png)
