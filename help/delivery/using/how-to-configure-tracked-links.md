---
solution: Campaign Classic
product: campaign
title: Comment configurer des liens trackés
description: Comment configurer des liens trackés
audience: delivery
content-type: reference
topic-tags: tracking-messages
exl-id: ed88e1d6-c0d5-4a85-9f3e-be670f4bcc10
translation-type: ht
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: ht
source-wordcount: '497'
ht-degree: 100%

---

# Comment configurer des liens trackés{#how-to-configure-tracked-links}

La réception des messages ainsi que l’activation des liens insérés dans le contenu des messages peuvent être suivis pour chaque diffusion. Vous pouvez ainsi assurer un tracking du comportement des destinataires suite aux actions de diffusion dont ils ont été la cible.

Le tracking s’applique aux messages, tandis que le tracking web permet de suivre la navigation des destinataires sur un site Internet (pages visitées, achats). Le paramétrage du tracking web est présenté dans [cette section](../../configuration/using/about-web-tracking.md).

>[!NOTE]
>
>Les liens inclus dans le contenu des emails qui comportent des éléments de personnalisation ont besoin d&#39;une syntaxe spécifique pour être trackés. Pour plus d&#39;informations sur l&#39;ajout de liens dans des emails pouvant être personnalisés et prenant en charge le tracking, consultez [cette section](../../delivery/using/tracking-personalized-links.md).




Le tracking des messages est activé par défaut. Pour personnaliser le tracking des URL, procédez comme suit :

1. Sélectionnez l’option **[!UICONTROL Afficher les URL]**, située dans la section inférieure de l’assistant de diffusion, sous le contenu du message.

   ![](assets/s_ncs_user_email_del_display_urls.png)

   Lorsque vous sélectionnez une URL dans la liste des URL trackées, elle est mise en surbrillance dans le contenu de la diffusion, à l’exception du lien de la page miroir et du lien de désinscription qui sont fournis par défaut.

   ![](assets/s_ncs_user_email_del_show_urls.png)

1. Pour chaque URL du message, choisissez d’activer ou non le tracking.

   >[!IMPORTANT]
   >
   >Lorsque l’URL du lien est utilisée comme libellé, il est recommandé de désactiver le tracking afin de prévenir tout risque de rejet pour cause de phishing.
   >
   >Par exemple, si l’URL www.adobe.com est insérée dans le message et que l’URL est trackée, le contenu du lien hypertexte sera transformé en https://nlt.adobe.net/r/?id=xxxxxx. Il pourrait alors être considéré comme frauduleux par les clients de messagerie des destinataires.

1. Au besoin, modifiez le libellé du tracking, double-cliquez dessus et saisissez-en un nouveau.

   >[!NOTE]
   >
   >Les noms des URL trackées et des libellés être modifiés afin de simplifier la lecture des informations lors du suivi des diffusions. Deux URL ou deux libellés portant le même nom seront cumulés lors du calcul des clics.

1. Au besoin, modifiez le tracking, sélectionnez un nouveau mode dans la colonne **[!UICONTROL Tracking]** correspondant au lien visé, comme dans l’exemple ci-dessous :

   ![](assets/s_ncs_user_select_tracking_mode.png)

   Pour chaque URL, vous pouvez définir le mode de tracking sur l’une de ces valeurs :

   * **[!UICONTROL Activé]** : active le tracking de cette URL.
   * **[!UICONTROL Non activé]** : désactive le tracking de cette URL.
   * **[!UICONTROL Toujours activé]** : active toujours le tracking de cette URL. Cette information est enregistrée de sorte que si l’URL réapparaît dans le contenu d’un prochain message, son tracking est automatiquement activé.
   * **[!UICONTROL Jamais activé]** : n’active jamais le tracking de cette URL. Cette information est enregistrée de sorte que si l’URL réapparaît dans le contenu d’un prochain message, son tracking est automatiquement désactivé.
   * **[!UICONTROL Opt-out]** : considère cette URL comme une option d’opt-out ou une URL de désabonnement.
   * **[!UICONTROL Page miroir]** : considère cette URL comme une URL de page miroir.

1. De plus, vous pouvez sélectionner une catégorie pour chaque URL trackée dans la liste déroulante de la colonne **[!UICONTROL Catégorie]**. Ces catégories peuvent être affichées dans les rapports, comme par exemple **[!UICONTROL URL et flux de clics]** (voir [cette section](../../reporting/using/reports-on-deliveries.md#urls-and-click-streams)). Elles sont définies dans une énumération spécifique : **[!UICONTROL urlCategory]** (voir [Gestion des énumérations](../../platform/using/managing-enumerations.md)).
