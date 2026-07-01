---
product: campaign
title: Mettre à jour la liste trimestrielle à l’aide d’une requête incrémentielle
description: Dans ce cas pratique, une requête incrémentielle est utilisée pour mettre automatiquement à jour une liste de destinataires.
feature: Workflows
hide: true
exl-id: 0d3e7046-313a-42a6-9155-3365e8d60bac
TQID: https://experienceleague.adobe.com/BH9Rd9DTl5ZnTIo17AS6FKEYio-DjbXiOf0Nn1GLXWI
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: id: ee25c34b-ea50-427b-9369-ba0a160f7d70id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22fid: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 286
ht-degree: 100%

---

# Mise à jour de la liste trimestrielle à l’aide d’une requête incrémentielle {#quarterly-list-update}



Dans l’exemple suivant, une [requête incrémentale](incremental-query.md) est utilisée pour mettre automatiquement à jour une liste de personnes destinataires.Ces personnes destinataires sont ciblées dans le cadre des campagnes marketing saisonnières.

Comme ces campagnes sont lancées au début de chaque saison afin de proposer des activités sportives pertinentes, ces listes sont mises à jour tous les trimestres.Cependant, une personne destinataire ne doit être ciblée ici qu’une fois tous les 9 mois par cette campagne.Vous pouvez ainsi espacer la fréquence d’éligibilité de la personne destinataire et proposer des activités selon les saisons au fil des ans.

![](assets/incremental_query_example.png)

1. Placez une activité de requête incrémentale ainsi qu&#39;une activité de mise à jour de liste dans un nouveau workflow.
1. Paramétrez l’onglet **[!UICONTROL Requête incrémentale]** de l’activité comme indiqué à la section [Création dʼune requête](query.md#creating-a-query).
1. Sélectionnez l’onglet **[!UICONTROL Planification et historique]** et indiquez un historique de 270 jours.Une personne destinataire déjà ciblée ne sera plus ciblée pendant une période de 270 jours, soit environ 9 mois.

   Cliquez ensuite sur le bouton **[!UICONTROL Changer...]**.

1. Le but étant de mettre à jour la liste avant chaque début de saison, sélectionnez le type de périodicité **[!UICONTROL Mensuel]**.
1. Dans l’écran suivant, sélectionnez Mars, Juin, Septembre et Décembre.Indiquez comme jour le 20 du mois et choisissez l’heure à laquelle lancer l’exécution du workflow.
1. Sélectionnez ensuite la période de validité de la requête. Par exemple, si vous souhaitez que cette dernière soit active en permanence, sélectionnez **[!UICONTROL Validité permanente]**.

   ![](assets/incremental_query_example_2.png)

1. Après avoir validé le paramétrage de la requête incrémentale, paramétrez l&#39;activité de mise à jour de liste comme décrit à la section [Mise à jour de liste](list-update.md).

Le workflow sera ainsi lancé automatiquement juste avant chaque début de saison.La liste sera mise à jour avec les nouvelles personnes destinataires éligibles pour recevoir les offres.
