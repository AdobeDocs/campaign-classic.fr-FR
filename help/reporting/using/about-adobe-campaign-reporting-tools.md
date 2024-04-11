---
product: campaign
title: À propos des outils de reporting d'Adobe Campaign
description: Analysez la réussite de vos campagnes dans des rapports natifs ou personnalisés.
feature: Reporting, Monitoring
badge-v8: label="S’applique également à la version 8" type="Positive" tooltip="S’applique également à Campaign v8"
exl-id: 1ef30004-e1b0-4dde-8104-0ee9e8aa9d8b
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 93%

---

# Prise en main des rapports {#about-adobe-campaign-reporting-tools}



En complément des [rapports natifs](../../reporting/using/about-campaign-built-in-reports.md), Adobe Campaign permet de générer des rapports dans différents contextes et de répondre à des besoins variés. Les principes d&#39;utilisation et leur mode de mise en œuvre sont présentés dans ce document.

Adobe Campaign n&#39;est pas un outil spécialisé dans le reporting : les rapports créés dans Adobe Campaign permettent principalement de visualiser des données agrégées. Dédiés à l&#39;analyse et à la représentation des données, les rapports d&#39;Adobe Campaign ne sont pas conçus pour réaliser des exports de données de la base.

Pour exporter des données de la base Adobe Campaign, vous devez créer un workflow et utiliser une activité d&#39;export de données. Pour plus d’informations, consultez [cette section](../../workflow/using/about-action-activities.md).

Adobe Campaign propose plusieurs outils de reporting :

1. **Rapports natifs** : Adobe Campaign propose un ensemble de rapports sur les diffusions, les opérations, les activités de la plateforme, les fonctionnalités optionnelles, etc. Ces rapports sont disponibles à partir des différentes fonctionnalités auxquelles ils se rapportent. Ils peuvent être adaptés pour mieux répondre à vos besoins.

   Pour plus d’informations, consultez [cette section](../../reporting/using/about-campaign-built-in-reports.md).

1. **L&#39;analyse descriptive des données** : Adobe Campaign propose un outil visuel afin de produire des statistiques métier sur les données de la base. Vous pouvez créer des rapports d&#39;analyse descriptive à travers un assistant dédié et définir leur contenu et leur mise en page en fonction de vos besoins.

   Pour plus d’informations, consultez [cette section](../../reporting/using/about-descriptive-analysis.md).

1. **Les rapports personnalisés** : Adobe Campaign vous permet de créer des rapports sur les données de la base. Une fois créés, ces rapports sont ensuite rendus accessibles dans les contextes appropriés.

   Selon la complexité des requêtes, des calculs et les volumes manipulés, les données analysées dans ces rapports peuvent être collectées via une requête et pré-agrégées dans une liste (workflow de type &#39;data management&#39;) ou dans un Cube (via l&#39;utilisation de Marketing Analytics). Elles seront affichées sous la forme d&#39;un tableau croisé dynamique ou d&#39;une liste avec regroupement.

   Pour plus d’informations, consultez [cette section](../../reporting/using/about-reports-creation-in-campaign.md).

1. **Les rapports d&#39;analyse** : Marketing Analytics permet une exploration intuitive des données.

   Pour plus d’informations, consultez [cette section](../../reporting/using/ac-cubes.md).

>[!CAUTION]
>
>Pour permettre son affichage et sa manipulation, ainsi que le bon fonctionnement des fonctionnalités d&#39;export, un rapport ne doit pas contenir plus de 1000 lignes.
