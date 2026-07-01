---
product: campaign
title: Bonnes pratiques en matière de reporting
description: Bonnes pratiques en matière de reporting Campaign
feature: Reporting, Monitoring
badge: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
exl-id: 0c7f00f3-b16d-41c5-a7b1-f5a59201bf8c
TQID: https://experienceleague.adobe.com/0NZ2bS4K-X1okyD-snv-pBDekzNqmFV5soF-qUOOVKo
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: c309ee4e-82e4-4f7e-b608-ef345678c34e
subfeature_v2: id: b3a4149f-2b3a-44d1-894e-e3ac4c77fb47id: cfda811a-e413-43a4-adf0-7370888f5cfcid: afe938ea-bc18-44a4-a3fb-03e1031466cb
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: c2be0313-b3ae-45e0-b454-d20bf54b23f2id: d095671a-1355-40aa-8b5f-06c33c68080bid: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 857
ht-degree: 100%

---

# Bonnes pratiques en matière de reporting{#best-practices-reporting}



## Analyse des besoins{#analyzing-needs}

L&#39;utilisation d&#39;un outil de reporting dépend du volume des données à manipuler, de leur complexité et du type de reporting à mettre en place.

Afin d’optimiser la création, l’utilisation et la pérennité d’un rapport, vous devez étudier précisément les besoins auxquels vous souhaitez répondre.Cette première analyse vous permettra d’identifier le type de rapport à créer et le mode de création à privilégier.Pour créer le rapport, effectuez les étapes suivantes :

1. Identifier le besoin

   La première étape consiste à identifier clairement le besoin : ce que vous souhaitez afficher dans votre rapport et quel est son objectif (suivi, analyse, export de données, etc.).

   Adobe Campaign offre un large éventail de capacités de reporting.Il est essentiel d’analyser clairement votre besoin pour identifier la fonctionnalité la mieux adaptée pour y répondre.

   Vous pouvez par exemple :

   * Explorer les données de la base et définir des mesures. En savoir plus dans [cette section](../../reporting/using/ac-cubes.md)
   * Ajouter des indicateurs à un rapport existant. En savoir plus dans [cette section](../../reporting/using/about-reports-creation-in-campaign.md)
   * Visualiser des données dans la base de données. En savoir plus dans [cette section](../../reporting/using/about-descriptive-analysis.md)
   * Créer un rapport de diffusion. En savoir plus dans [cette section](../../reporting/using/about-reports-creation-in-campaign.md)),
   * Exporter les données de la base Adobe Campaign (via un workflow, voir [cette section](../../workflow/using/about-workflows.md)
   * Créer un tableau croisé dynamique. En savoir plus dans [cette section](../../reporting/using/creating-a-table.md#creating-a-breakdown-or-pivot-table)
   * Explorer les données agrégées. En savoir plus dans [cette section](../../reporting/using/ac-cubes.md)
   * Utiliser un assistant pour analyser les données. En savoir plus dans [cette section](../../reporting/using/about-descriptive-analysis.md)
   * Analyser de grands volumes de données. En savoir plus dans [cette section](../../reporting/using/about-reports-creation-in-campaign.md)

1. Identifier la population cible

   Vous devez ensuite savoir à quelle cible le rapport que vous souhaitez créer s’adresse, connaître le ou les publics qui seront amenés à le consulter et connaître le mode d’affichage du rapport (dans un navigateur, dans Adobe Campaign, pour un objet précis, pour toute la plateforme, etc.).

   Vous pouvez ainsi créer des rapports pour :

   * Tous les opérateurs Adobe Campaign,
   * Seulement les opérateurs ayant des droits sur une opération marketing,
   * Un seul opérateur, pour une consultation ponctuelle,
   * Tous les opérateurs en accès Web, etc.

   Ces considérations doivent également prendre en compte les problématiques liées aux droits d&#39;accès et à la sécurité.

1. Définir le contenu

   Vous devez ensuite savoir quel type de données vous souhaitez afficher : indicateurs de diffusion, rapport sur les profils de la base de données, etc.

   Vous devez également connaître la nature de ces données (simples, issues d&#39;un calcul, volumineuses, etc.), leur localisation (dans Adobe Campaign, dans un système tiers), leur fréquence de mise à jour, afin de définir la périodicité du calcul (quotidien, hebdomadaire, à la volée), ainsi que leur volume.

   Les problèmes liés aux volumes et aux mises à jour des données doivent être étudiés attentivement afin d’éviter les problèmes d’affichage des rapports, notamment en termes de temps.Nous vous recommandons donc de créer des agrégats pour pré-calculer certaines données en dehors du rapport.Les tables contenant les logs de tracking et de diffusion peuvent contenir des millions d’enregistrements : les données doivent donc être agrégées via un workflow pour pouvoir les utiliser dans un rapport.

## Optimisation de la conception des rapports{#optimizing-report-creation}

### Volume des données {#data-volume}

Afin de garantir des performances optimales, le volumes des données manipulées ne doit pas être trop élevé.

Ainsi :

* Le temps de calcul d&#39;un rapport ne doit jamais excéder 5 minutes.

  De même, lors de sa phase de conception, avec un faible volume de données, si le calcul du rapport excède 60 secondes, alors la méthode employée doit être ré-étudiée.

* Lors de l&#39;utilisation de Marketing Analytics, les données de reporting ne doivent pas excéder 10 millions de lignes.

Nous recommandons également de calculer des agrégats la nuit et d’utiliser ces données agrégées directement dans les rapports.Ces agrégats doivent être créés via des workflows de gestion des données (Data Management) dédiés (requêtes SQL).

Vous pouvez également calculer les rapports pendant la nuit et créer automatiquement un historique qui pourra être consulté à tout moment, sans surcharger la base de données.

### Requêtes {#queries}

Nous recommandons d’utiliser des requêtes SQL chaque fois que possible et d’éviter le post-traitement JavaScript.Si nécessaire, utilisez une activité Script dans un workflow et supprimez les données utilisées pour le calcul.Vous pouvez également utiliser les données archivées pour accélérer le temps de traitement.

Dans ce cas, la syntaxe à utiliser sera du type :

```
if(string(ctx@_historyId)!==""))
```

Les requêtes qui permettent de collecter les données affichées dans les rapports ne doivent pas être trop complexes, surtout si elles sont réalisées sur la totalité des données de la base de données.Pour améliorer les performances, il peut être utile de filtrer les données avant d’exécuter ces requêtes : ainsi, les calculs ne porteront que sur une partie des données.

### Performances {#performances}

Les recommandations ci-dessus permettent d&#39;optimiser au maximum le calcul des rapports.

Adobe Campaign vous recommande, en complément, les axes d&#39;optimisation suivants :

* Travailler sur votre modèle de données : les champs indexés doivent être utilisés en priorité afin d’améliorer les performances de calcul.

  Pour repérer rapidement un champ indexé, observez le nom de la colonne dans l&#39;interface d&#39;Adobe Campaign : la flèche de tri est soulignée en rouge lorsque le champ est indexé.

  Pour plus d&#39;informations sur les index, consultez [cette section](../../configuration/using/data-model-best-practices.md#indexes).

* Assurez-vous que le rapport est évolutif : le volume de données peut augmenter considérablement au fil du temps.

  De même, le volume des données manipulées dans les phases de test peut être différent du volume des données réelles en production.Les phases de test ne doivent donc pas être négligées.

  Enfin, les délais de purge des données doivent être connus, et au besoin adaptés pour faciliter la manipulation des informations.

  Pour en savoir plus sur le nettoyage et la conservation des données, consultez [cette section](../../configuration/using/data-model-best-practices.md#data-retention).

### Exportation des rapports {#exporting-reports}

Les recommandations spécifiques liées à lʼexportation des rapports sont présentées dans [cette section](../../reporting/using/actions-on-reports.md#exporting-a-report).
