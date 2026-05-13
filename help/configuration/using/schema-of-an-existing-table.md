---
product: campaign
title: Schéma d'une table existante
description: Schéma d'une table existante
feature: Custom Resources
role: Developer
exl-id: 964f1027-627c-4f12-91b5-f258e9ba458b
TQID: https://experienceleague.adobe.com/Vi1DhgY8tGIhq1TtMOGKeGMrqFgGecfJQHrKyFXTSgg
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
subfeature_v2: id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
role_v2: id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 232
ht-degree: 100%

---

# Schéma d&#39;une table existante{#schema-of-an-existing-table}

## Vue d&#39;ensemble {#overview}

Lorsque l&#39;application doit accéder aux données d&#39;une table déjà existante, ou d&#39;une vue SQL, ou de données provenant d&#39;une base distante, vous devez créer son schéma dans Adobe Campaign avec les données suivantes :

* le nom de la table : renseigner le nom de la table (avec son alias dans le cas d&#39;une utilisation d&#39;un dblink) avec l&#39;attribut &quot;sqltable&quot;,
* la clé du schéma : référencer le ou les champs de réconciliation,
* les index : utilisés pour la génération des requêtes,
* les champs et leur emplacement dans la structure XML : renseigner uniquement les champs utilisés dans l&#39;application,
* les liens : s&#39;il existe des jointures avec les autres tables de la base.

## Mise en œuvre {#implementation}

Pour créer le schéma correspondant, les étapes sont les suivantes :

1. Editez le nœud **[!UICONTROL Administration > Paramétrage > Schémas de données]** de l&#39;arborescence Adobe Campaign et cliquez sur l&#39;icône **[!UICONTROL Nouveau]** .
1. Sélectionnez l&#39;option **[!UICONTROL Accéder aux données d&#39;une table déjà existante ou d&#39;une vue SQL]** et cliquez sur **[!UICONTROL Suivant]** .

   ![](assets/s_ncs_configuration_extand_a_schema.png)

1. Sélectionnez la table ou la vue déjà existante :

   ![](assets/s_ncs_configuration_select_table.png)

1. Adaptez le contenu du schéma selon vos besoins.

   ![](assets/s_ncs_configuration_view_create_schema.png)

   Le schéma doit être renseigné avec l&#39;attribut view=&quot;true&quot; sur l&#39;élément racine `<srcSchema>` afin de ne pas générer de script SQL de création de la table.

**Exemple** :

```
<srcSchema name="recipient" namespace="cus" view="true">
  <element name="recipient" sqltable="dbsrv.recipient">
    <key name="email">
      <keyfield xpath="@email"/>
    </key>   
    <attribute name="email" type="string" length="80" sqlname="email"/>
  </element>
</srcSchema>
```

## Accès à une base de données externe {#accessing-an-external-database}

Grâce à l’option **Federated Data Access - FDA**, vous pouvez accéder aux données stockées dans une base externe.

Le paramétrage nécessaire au niveau des schémas pour accéder aux données d&#39;une base externe est détaillé dans [cette page](../../installation/using/creating-data-schema.md).
