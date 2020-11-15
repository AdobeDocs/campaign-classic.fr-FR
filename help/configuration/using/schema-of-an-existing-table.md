---
title: Schéma d'une table existante
seo-title: Schéma d'une table existante
description: Schéma d'une table existante
seo-description: null
page-status-flag: never-activated
uuid: cb766259-8ed7-40a1-8df7-75a8a3f9986d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 6877d94d-d6e5-4080-a537-ef1bb6e6f8cf
translation-type: tm+mt
source-git-commit: 9bbde65aea6735e30e95e75c2b6ae5445d4a2bdd
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 100%

---


# Schéma d&#39;une table existante{#schema-of-an-existing-table}

## Présentation {#overview}

Lorsque l&#39;application doit accéder aux données d&#39;une table déjà existante, ou d&#39;une vue SQL, ou de données provenant d&#39;une base distante, vous devez créer son schéma dans Adobe Campaign avec les données suivantes :

* le nom de la table : renseigner le nom de la table (avec son alias dans le cas d&#39;une utilisation d&#39;un dblink) avec l&#39;attribut &quot;sqltable&quot;,
* la clé du schéma : référencer le ou les champs de réconciliation,
* les index : utilisés pour la génération des requêtes,
* les champs et leur emplacement dans la structure XML : renseigner uniquement les champs utilisés dans l&#39;application,
* les liens : s&#39;il existe des jointures avec les autres tables de la base.

## Mise en oeuvre {#implementation}

Pour créer le schéma correspondant, les étapes sont les suivantes :

1. Editez le nœud **[!UICONTROL Administration > Paramétrage > Schémas de données]** de l&#39;arborescence Adobe Campaign et cliquez sur l&#39;icône **[!UICONTROL Nouveau]** .
1. Sélectionnez l&#39;option **[!UICONTROL Accéder aux données d&#39;une table déjà existante ou d&#39;une vue SQL]** et cliquez sur **[!UICONTROL Suivant]** .

   ![](assets/s_ncs_configuration_extand_a_schema.png)

1. Sélectionnez la table ou la vue déjà existante :

   ![](assets/s_ncs_configuration_select_table.png)

1. Adaptez le contenu du schéma selon vos besoins.

   ![](assets/s_ncs_configuration_view_create_schema.png)

   Le schéma doit être renseigné avec l&#39;attribut view=&quot;true&quot; sur l&#39;élément racine `<srcSchema>` afin de ne pas générer de script SQL de création de la table.

**Exemple** :

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
