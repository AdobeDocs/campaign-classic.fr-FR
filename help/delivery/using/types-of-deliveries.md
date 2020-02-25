---
title: Types de diffusions
seo-title: Types de diffusions
description: Types de diffusions
seo-description: null
page-status-flag: never-activated
uuid: a540efc7-105d-4c7f-a2ee-ade4d22b3445
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
discoiquuid: 0cbc4e92-482f-4dac-a1fb-b738e7127938
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 707352334144df86ae82aa51d595ae6bc751d1f2

---


# Types de diffusions{#types-of-deliveries}

Campaign contient trois types d&#39;objets de diffusion :

## Diffusion unique {#single-delivery}

Une **diffusion** est un objet de diffusion autonome exécuté une seule fois. Elle peut être dupliquée et préparée à nouveau. Toutefois, tant qu&#39;elle se trouve dans un état final (annulée, arrêtée, terminée), elle ne peut pas être réutilisée.

Les diffusions peuvent être créées à partir de la liste de diffusions ou au sein d&#39;un workflow via une activité [Diffusion](../../workflow/using/delivery.md).

Les processus fournissent également des activités de diffusion spécifiques en fonction du type de canal que vous souhaitez utiliser. For more on these activities, refer to [this section](../../workflow/using/cross-channel-deliveries.md).

## Diffusion récurrente {#recurring-delivery}

Une **diffusion récurrente** permet de créer une diffusion à chaque exécution de l&#39;activité. Ainsi, vous n&#39;avez pas à créer de diffusion pour les tâches récurrentes.

Par exemple, si vous exécutez ce type d&#39;activité une fois par mois, vous obtiendrez 12 diffusions au bout d&#39;un an.

Les diffusions récurrentes sont créées dans des workflows par le biais de l&#39;activité [](../../workflow/using/recurring-delivery.md)Diffusion récurrente. Un exemple d&#39;utilisation de cette activité est présenté dans la section suivante : [Créer une diffusion récurrente dans un workflow de ciblage](../../workflow/using/sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow).

## Diffusion (au fil de l&#39;eau){#continuous-delivery}

Une **diffusion au fil de l&#39;eau** permet d&#39;ajouter de nouveaux destinataires à une diffusion existante, ce qui évite d&#39;avoir à créer une diffusion à chaque exécution.

Si des informations liées à diffusion changent (contenu, nom, etc.), un nouvel objet de diffusion est créé lors de l&#39;exécution de la diffusion. Si aucune information n&#39;a été modifiée, le même objet de diffusion est réutilisé, et les logs de diffusion et de tracking sont ajoutés au même objet.

Par exemple, si vous exécutez ce type d&#39;activité une fois par mois, vous obtiendrez une seule diffusion au bout d&#39;un an (à condition que vous n&#39;ayez apporté aucune modification à la diffusion).

Continuous deliveries are created within workflows via the [Continuous delivery activity](../../workflow/using/continuous-delivery.md).
