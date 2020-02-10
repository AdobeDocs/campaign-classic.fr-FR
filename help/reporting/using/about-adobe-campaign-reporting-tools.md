---
title: A propos des outils de reporting d'Adobe Campaign
seo-title: A propos des outils de reporting d'Adobe Campaign
description: A propos des outils de reporting d'Adobe Campaign
seo-description: null
page-status-flag: never-activated
uuid: a8122c9e-60ba-4ef7-bc63-05d6cf16fad0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: reporting-in-adobe-campaign
discoiquuid: c5dad561-0708-4b7a-84a0-eb00beff58c6
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1719d6ac9643f0b3e9339037cf4d0f209d16340e

---


# Commencer à créer des rapports {#about-adobe-campaign-reporting-tools}

En complément des [rapports natifs](../../reporting/using/about-campaign-built-in-reports.md), Adobe Campaign permet de générer des rapports dans différents contextes et de répondre à des besoins variés. Les principes d&#39;utilisation et leur mode de mise en œuvre sont présentés dans ce document.

Adobe Campaign n&#39;est pas un outil spécialisé dans le reporting : les rapports créés dans Adobe Campaign permettent principalement de visualiser des données agrégées. Dédiés à l&#39;analyse et à la représentation des données, les rapports d&#39;Adobe Campaign ne sont pas conçus pour réaliser des exports de données de la base.

Si vous souhaitez exporter des données de la base Adobe Campaign, vous devez créer un workflow et utiliser une activité d&#39;export de données. Voir à ce propos [cette section](../../workflow/using/about-action-activities.md).

Adobe Campaign propose plusieurs outils de reporting :

1. **Rapports** intégrés : Adobe Campaign propose un ensemble de rapports sur les remises, les campagnes, les activités de plateforme, les fonctionnalités facultatives, etc. Ces rapports sont disponibles via les différentes fonctionnalités auxquelles ils se rapportent. Ils peuvent être adaptés à vos besoins spécifiques.

   Voir à ce propos [cette section](../../reporting/using/about-campaign-built-in-reports.md).

1. **L&#39;analyse descriptive des données** : Adobe Campaign propose un outil visuel afin de produire des statistiques métier sur les données de la base. Vous pouvez créer des rapports d&#39;analyse descriptive à travers un assistant dédié et définir leur contenu et leur présentation en fonction de vos besoins.

   Voir à ce propos [cette section](../../reporting/using/about-descriptive-analysis.md).

1. **Les rapports personnalisés** : Adobe Campaign vous permet de créer des rapports sur les données de la base. Une fois créés, ces rapports sont ensuite rendus accessibles dans les contextes appropriés.

   Selon la complexité des requêtes, des calculs et les volumes manipulés, les données analysées dans ces rapports peuvent être collectées via une requête et pré-agrégées dans une liste (workflow de type &#39;data management&#39;) ou dans un Cube (via l&#39;utilisation de Marketing Analytics). Elles seront affichées sous la forme d&#39;un tableau croisé dynamique ou d&#39;une liste avec regroupement.

   Voir à ce propos [cette section](../../reporting/using/about-reports-creation-in-campaign.md).

1. **Les rapports d&#39;analyse** : Marketing Analytics permet une exploration intuitive des données.

   Voir à ce propos [cette section](../../reporting/using/about-cubes.md).

>[!CAUTION]
>
>Pour permettre son affichage et sa manipulation, ainsi que le bon fonctionnement des fonctionnalités d&#39;export, un rapport ne doit pas contenir plus de 1000 lignes.