---
title: Meilleures pratiques de reporting
seo-title: Meilleures pratiques de reporting
description: Meilleures pratiques de reporting
seo-description: null
page-status-flag: never-activated
uuid: 09de6a17-b3a7-4543-b672-b0a21653aa75
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: reporting-in-adobe-campaign
discoiquuid: 904961e0-7dff-4350-8d5d-e4bdd368b3ff
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0c41cf2f35495a1514642e47f0b7146d8dd50946

---


# Meilleures pratiques de reporting{#best-practices-reporting}

## Analyse des besoins{#analyzing-needs}

L&#39;utilisation d&#39;un outil de reporting dépend du volume des données à manipuler, de leur complexité et du type de reporting à mettre en place.

Afin d&#39;optimiser la création, l&#39;utilisation et la pérennité d&#39;un rapport, vous devez étudier précisément les besoins auxquels vous souhaitez répondre. Cette première analyse vous permettra d&#39;identifier le type de rapport à créer et le mode de création à privilégier. Elle doit être menée en suivant les étapes ci-dessous :

1. Identifier le besoin

   La première étape consiste à identifier clairement le besoin : ce que vous souhaitez afficher dans votre rapport et quel est son objectif (suivi, analyse, export de données, etc.).

   De nombreuses capacités de reporting sont proposées dans Adobe Campaign, et il est essentiel d&#39;analyser clairement votre besoin pour identifier la fonctionnalité la mieux adaptée pour y répondre.

   Vous pouvez par exemple :

   * Explorer les données de la base et définir des mesures (via [cette section](../../reporting/using/about-cubes.md)),
   * Ajouter des indicateurs à un rapport existant (voir [cette section](../../reporting/using/about-reports-creation-in-campaign.md)),
   * Consulter les données de la base (via [cette section](../../reporting/using/about-descriptive-analysis.md)),
   * Créer un rapport de diffusion (voir [cette section](../../reporting/using/about-reports-creation-in-campaign.md)),
   * Exporter les données de la base Adobe Campaign (via un workflow, voir [cette section](../../workflow/using/about-workflows.md)),
   * Créer un tableau croisé dynamique (voir [cette section](../../reporting/using/creating-a-table.md#creating-a-breakdown-or-pivot-table)),
   * Explorer des données agrégées (via [cette section](../../reporting/using/about-cubes.md)),
   * Utiliser un assistant pour analyser les données (via [cette section](../../reporting/using/about-descriptive-analysis.md)),
   * Analyser un grand volume de données (voir [cette section](../../reporting/using/about-reports-creation-in-campaign.md)), etc.

1. Identifier le public auquel le rapport est destiné

   Vous devez ensuite savoir à qui le rapport que vous souhaitez créer s&#39;adresse, connaître le ou les publics qui seront amenés à le consulter et connaître le mode d&#39;affichage du rapport (dans un navigateur, dans Adobe Campaign, pour un objet précis, pour toute la plate-forme, etc.).

   Vous pouvez ainsi créer des rapports pour :

   * Tous les opérateurs Adobe Campaign,
   * Seulement les opérateurs ayant des droits sur une opération marketing,
   * Un seul opérateur, pour une consultation ponctuelle,
   * Tous les opérateurs en accès Web, etc.
   Ces considérations doivent également prendre en compte les problématiques liées aux droits d&#39;accès et à la sécurité.

1. Définir le contenu

   Vous devez ensuite savoir quel type de données vous souhaitez afficher : indicateurs d&#39;une diffusion, rapport sur les profils de la base de données, etc.

   Vous devez également connaître la nature de ces données (simples, issues d&#39;un calcul, volumineuses, etc.), leur localisation (dans Adobe Campaign, dans un système tiers), leur fréquence de mise à jour, afin de définir la périodicité du calcul (quotidien, hebdomadaire, à la volée), ainsi que leur volume.

   Les problématiques liées au volume et à la mise à jour des données doivent être étudiées avec attention afin d&#39;éviter les difficultés d&#39;affichage des rapports, notamment en terme de délais. Dans cette optique, il est recommandé de créer des agrégats afin de pré-calculer certaines données en dehors du rapport. Typiquement, les tables contenant les logs de tracking et les logs de diffusion peuvent atteindre des millions d&#39;enregistrements : les données doivent donc être agrégées, via un workflow, pour être exploitées dans un rapport.

## Optimiser la création des rapports{#optimizing-report-creation}

### Volume des données {#data-volume}

Afin de garantir des performances optimales, le volumes des données manipulées ne doit pas être trop élevé.

Ainsi :

* Le temps de calcul d&#39;un rapport ne doit jamais excéder 5 minutes.

   De même, lors de sa phase de conception, avec un faible volume de données, si le calcul du rapport excède 60 secondes, alors la méthode employée doit être ré-étudiée.

* Lors de l&#39;utilisation de Marketing Analytics, les données manipulées ne doivent pas excéder 10 millions de lignes.

Dans le cas contraire, il est recommandé de calculer des agrégats, par exemple la nuit, lorsque la base de données est la moins sollicitée, puis d&#39;utiliser ces données agrégées directement dans les rapports. Ces agrégats doivent être créés via des workflows de Data Management dédiés (requêtes SQL).

Vous pouvez également calculer les rapports pendant la nuit et créer automatiquement un historique qui pourra être consulté à tout moment, sans surcharger la base de données.

### Requêtes {#queries}

Il est recommandé de réaliser le maximum de requêtes en SQL et d&#39;éviter au maximum les post-traitements en Javascript. Au besoin, utilisez une activité Script dans un workflow et supprimez les données utilisées pour le calcul. Utilisez également les données historisées pour accélérer les temps de traitement.

Dans ce cas, la syntaxe à utiliser sera du type :

```
if(string(ctx@_historyId)!==""))
```

Les requêtes qui permettent de collecter les données affichées dans les rapports ne doivent pas être trop complexes, surtout si elles sont réalisées sur la totalité des données de la base. Il est souvent utile, pour améliorer les performances, de filtrer les données de la base avant d&#39;exécuter ces requêtes : ainsi les calculs ne porteront que sur une partie des données.

### Performances {#performances}

Les recommandations ci-dessus permettent d&#39;optimiser au maximum le calcul des rapports.

Adobe Campaign vous recommande, en complément, les axes d&#39;optimisation suivants :

* Etudier le modèle de données : les champs indexés doivent être utilisés prioritairement afin d&#39;améliorer les performances de calcul.

   Pour repérer rapidement un champ indexé, observez le nom de la colonne dans l&#39;interface d&#39;Adobe Campaign : la flèche de tri est soulignée en rouge lorsque le champ est indexé.

* Veiller à la perennité du rapport : le volume des données manipulées peut croître fortement dans le temps.

   De même, le volume des données manipulées dans les phases de test peut différer fortement du volume effectif des données en production. Les phases de test ne doivent donc pas être négligées.

   Enfin, les délais de purge des données doivent être connus, et au besoin adaptés pour faciliter la manipulation des informations.

### Export des rapports {#exporting-reports}

Les recommandations spécifiques liées à l&#39;export des rapports sont présentées dans [cette section](../../reporting/using/actions-on-reports.md#exporting-a-report).
