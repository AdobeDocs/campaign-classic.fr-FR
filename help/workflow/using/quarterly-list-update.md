---
title: Mise à jour de la liste trimestrielle à l’aide d’une requête incrémentielle
description: Dans ce cas d’utilisation, une requête incrémentielle est utilisée pour mettre automatiquement à jour une liste destinataire.
page-status-flag: never-activated
uuid: 24d322e8-172c-4faa-8a1f-59085b390a76
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 31071cd2-7d97-4a4f-a6cc-5ac5b6178be5
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: aa192d975a08246ba684940fff3d33853d7d9345
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 80%

---


# Mise à jour de la liste trimestrielle à l’aide d’une requête incrémentielle {#quarterly-list-update}

In the following example, an [incremental query](../../workflow/using/incremental-query.md) is used to automatically update a recipient list. These recipients are targeted as part of seasonal marketing campaigns.

Ces campagnes étant lancées à chaque début de saison afin de proposer des activités sportives pertinentes, les listes sont mises à jour une fois par trimestre. Cependant, un destinataire ne doit ici être ciblé qu&#39;une fois tous les 9 mois par cette campagne. Cela permet d&#39;espacer la fréquence d&#39;éligibilité d&#39;un destinataire et de lui proposer des activités pour différentes saisons au fil des ans.

![](assets/incremental_query_example.png)

1. Placez une activité de requête incrémentale ainsi qu&#39;une activité de mise à jour de liste dans un nouveau workflow.
1. Paramétrez l’onglet **[!UICONTROL Requête incrémentale]** de l’activité comme indiqué à la section [Créer une requête](../../workflow/using/query.md#creating-a-query).
1. Sélectionnez l&#39;onglet **[!UICONTROL Planification &amp; Historique]** et indiquez un historique de 270 jours. Un destinataire déjà ciblé ne sera plus ciblé pour une période de 270 jours, soit environ 9 mois.

   Cliquez ensuite sur le bouton **[!UICONTROL Changer...]**.

1. Le but étant de mettre à jour la liste avant chaque début de saison, sélectionnez le type de périodicité **[!UICONTROL Mensuel]**.
1. À l&#39;écran suivant, sélectionnez les mois de mars, juin, septembre et décembre. Indiquez comme jour le 20 du mois et choisissez l&#39;heure à laquelle lancer l&#39;exécution du workflow.
1. Sélectionnez ensuite la période de validité de la requête. Par exemple, si vous souhaitez que cette dernière soit active en permanence, sélectionnez **[!UICONTROL Validité permanente]**.

   ![](assets/incremental_query_example_2.png)

1. Après avoir validé le paramétrage de la requête incrémentale, paramétrez l&#39;activité de mise à jour de liste comme décrit à la section [Mise à jour de liste](../../workflow/using/list-update.md).

Le workflow sera ainsi lancé automatiquement juste avant chaque début de saison. La liste sera mise à jour avec les nouveaux destinataires éligibles pour recevoir les offres.
