---
product: campaign
title: À propos des outils de reporting d'Adobe Campaign
description: Analysez la réussite de vos campagnes dans des rapports natifs ou personnalisés.
feature: Reporting, Monitoring
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
exl-id: 1ef30004-e1b0-4dde-8104-0ee9e8aa9d8b
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 50%

---

# Prise en main des rapports {#about-adobe-campaign-reporting-tools}



En complément des [rapports natifs](../../reporting/using/about-campaign-built-in-reports.md), Adobe Campaign permet de générer des rapports dans différents contextes et de répondre à des besoins variés. Les principes d’utilisation et les modes d’implémentation sont présentés dans ce document.

Adobe Campaign n&#39;est pas un outil spécialisé dans le reporting : les rapports créés dans Adobe Campaign permettent principalement de visualiser des données agrégées. Les rapports Adobe Campaign, qui sont dédiés à l’analyse et à la représentation des données, ne sont pas conçus pour les exportations de base de données.

Si vous souhaitez exporter des données de la base Adobe Campaign, vous devez créer un workflow et utiliser une activité d&#39;export de données. Pour en savoir plus, consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/action-activities.html?lang=fr){target="_blank"}.

Adobe Campaign propose plusieurs outils de reporting :

1. **Rapports natifs** : Adobe Campaign propose un ensemble de rapports sur les diffusions, les campagnes, les activités de la plateforme, les fonctionnalités optionnelles, etc. Ces rapports sont disponibles à partir des différentes fonctionnalités auxquelles ils se rapportent. Ils peuvent être adaptés à vos besoins spécifiques.

   Pour plus d’informations, consultez [cette section](../../reporting/using/about-campaign-built-in-reports.md).

1. **Analyse de données descriptives** : Adobe Campaign fournit un outil visuel permettant de produire des statistiques sur les données contenues dans la base de données. Vous pouvez créer des rapports d’analyse descriptive à l’aide d’un assistant dédié et adapter leur contenu ainsi que leur mise en page en fonction de vos besoins.

   Pour plus d’informations, consultez [cette section](../../reporting/using/about-descriptive-analysis.md).

1. **Rapports personnalisés** : Adobe Campaign permet de créer des rapports sur les données de la base. Une fois créés, ils sont rendus accessibles dans les contextes appropriés.

   Selon la complexité des requêtes, des calculs et des volumes manipulés, les données analysées dans ces rapports peuvent être collectées via une requête et pré-agrégées dans une liste (workflow de type &#39;data management&#39;) ou dans un cube (via l&#39;utilisation de Marketing Analytics). Elle s&#39;affiche sous la forme d&#39;un tableau croisé dynamique ou d&#39;une liste de groupes.

   Pour plus d’informations, consultez [cette section](../../reporting/using/about-reports-creation-in-campaign.md).

1. **Les rapports d&#39;analyse** : Marketing Analytics permet une exploration intuitive des données.

   Pour plus d’informations, consultez [cette section](../../reporting/using/ac-cubes.md).

>[!CAUTION]
>
>Pour permettre son affichage et sa manipulation, ainsi que le bon fonctionnement des fonctionnalités d&#39;export, un rapport ne doit pas contenir plus de 1000 lignes.
