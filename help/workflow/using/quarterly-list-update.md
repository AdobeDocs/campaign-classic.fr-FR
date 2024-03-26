---
product: campaign
title: Mettre à jour la liste trimestrielle à l’aide d’une requête incrémentielle
description: Dans ce cas pratique, une requête incrémentielle est utilisée pour mettre automatiquement à jour une liste de destinataires.
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
feature: Workflows
exl-id: 0d3e7046-313a-42a6-9155-3365e8d60bac
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 92%

---

# Mise à jour de la liste trimestrielle à l’aide d’une requête incrémentielle {#quarterly-list-update}



Dans l’exemple ci-après, une [requête incrémentale](incremental-query.md) est utilisée afin de mettre à jour automatiquement une liste de destinataires. Ces derniers sont ciblés dans le cadre de campagnes marketing saisonnières.

Ces campagnes étant lancées à chaque début de saison afin de proposer des activités sportives pertinentes, les listes sont mises à jour une fois par trimestre. Cependant, un destinataire ne doit ici être ciblé qu&#39;une fois tous les 9 mois par cette campagne. Cela permet d&#39;espacer la fréquence d&#39;éligibilité d&#39;un destinataire et de lui proposer des activités pour différentes saisons au fil des ans.

![](assets/incremental_query_example.png)

1. Placez une activité de requête incrémentale ainsi qu&#39;une activité de mise à jour de liste dans un nouveau workflow.
1. Paramétrez l’onglet **[!UICONTROL Requête incrémentale]** de l’activité comme indiqué à la section [Création dʼune requête](query.md#creating-a-query).
1. Sélectionnez l&#39;onglet **[!UICONTROL Planification &amp; Historique]** et indiquez un historique de 270 jours. Un destinataire déjà ciblé ne sera plus ciblé pour une période de 270 jours, soit environ 9 mois.

   Cliquez ensuite sur le bouton **[!UICONTROL Changer...]**.

1. Le but étant de mettre à jour la liste avant chaque début de saison, sélectionnez le type de périodicité **[!UICONTROL Mensuel]**.
1. À l&#39;écran suivant, sélectionnez les mois de mars, juin, septembre et décembre. Indiquez comme jour le 20 du mois et choisissez l&#39;heure à laquelle lancer l&#39;exécution du workflow.
1. Sélectionnez ensuite la période de validité de la requête. Par exemple, si vous souhaitez que cette activité soit active de manière permanente, sélectionnez **[!UICONTROL Validité permanente]**.

   ![](assets/incremental_query_example_2.png)

1. Après avoir validé le paramétrage de la requête incrémentale, paramétrez l&#39;activité de mise à jour de liste comme décrit à la section [Mise à jour de liste](list-update.md).

Le workflow sera ainsi lancé automatiquement juste avant chaque début de saison. La liste sera mise à jour avec les nouveaux destinataires éligibles pour recevoir les offres.
