---
product: campaign
title: À propos des outils de reporting d'Adobe Campaign
description: Analysez la réussite de vos campagnes dans des rapports natifs ou personnalisés.
feature: Reporting, Monitoring
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
exl-id: 1ef30004-e1b0-4dde-8104-0ee9e8aa9d8b
TQID: https://experienceleague.adobe.com/4D-bCeMQakNjr7OXhiZ1u0Sfp5MZWwzZzHtykBfFzZ8
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a075b2c1-7748-4328-b7f6-343aa314616aid: c309ee4e-82e4-4f7e-b608-ef345678c34e
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
subfeature_v2: id: b3a4149f-2b3a-44d1-894e-e3ac4c77fb47id: cfda811a-e413-43a4-adf0-7370888f5cfcid: afe938ea-bc18-44a4-a3fb-03e1031466cb
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 362
ht-degree: 100%

---

# Prise en main des rapports {#about-adobe-campaign-reporting-tools}



En complément des [rapports intégrés](../../reporting/using/about-campaign-built-in-reports.md), Adobe Campaign permet de générer des rapports dans différents contextes et de répondre à des besoins variés.Les principes d’utilisation et les modes d’implémentation sont présentés dans ce document.

Adobe Campaign n’est pas un outil spécialisé dans le reporting : les rapports créés dans Adobe Campaign permettent principalement de visualiser des données agrégées.Les rapports Adobe Campaign, qui sont dédiés à l’analyse et à la représentation des données, ne sont pas conçus pour les exports de base de données.

Si vous souhaitez exporter des données de la base Adobe Campaign, vous devez créer un workflow et utiliser une activité d&#39;export de données. Pour en savoir plus, consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/action-activities.html?lang=fr){target="_blank"}.

Adobe Campaign propose plusieurs outils de reporting :

1. **Rapports intégrés** : Adobe Campaign propose un ensemble de rapports sur les diffusions, les campagnes, les activités de la plateforme, les fonctionnalités optionnelles, etc. Ces rapports sont disponibles à partir des différentes fonctionnalités auxquelles ils se rapportent.Ils peuvent être adaptés à vos besoins spécifiques.

   Pour plus d’informations, consultez [cette section](../../reporting/using/about-campaign-built-in-reports.md).

1. **Analyse de données descriptives** : Adobe Campaign fournit un outil visuel permettant de produire des statistiques sur les données contenues dans la base de données. Vous pouvez créer des rapports d’analyse descriptive à l’aide d’un assistant dédié et adapter leur contenu ainsi que leur mise en page en fonction de vos besoins.

   Pour plus d’informations, consultez [cette section](../../reporting/using/about-descriptive-analysis.md).

1. **Rapports personnalisés** : utilisez Adobe Campaign pour créer des rapports sur les données de la base de données.Une fois créés, ils sont accessibles dans les contextes appropriés.

   Selon la complexité des requêtes, des calculs et des volumes, les données analysées dans ces rapports peuvent être collectées via une requête et pré-agrégées dans une liste (workflow de type « gestion des données ») ou dans un Cube (via l’utilisation de Marketing Analytics).Elles s’affichent sous la forme d’un tableau croisé dynamique ou d’une liste de groupes.

   Pour plus d’informations, consultez [cette section](../../reporting/using/about-reports-creation-in-campaign.md).

1. **Les rapports d&#39;analyse** : Marketing Analytics permet une exploration intuitive des données.

   Pour plus d’informations, consultez [cette section](../../reporting/using/ac-cubes.md).

>[!CAUTION]
>
>Pour permettre son affichage et sa manipulation, ainsi que le bon fonctionnement des fonctionnalités d&#39;export, un rapport ne doit pas contenir plus de 1000 lignes.
