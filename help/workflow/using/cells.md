---
product: campaign
title: Cellules
description: Cellules
feature: Workflows, Targeting Activity
hide: true
exl-id: 7b562dba-7e4b-40a7-91db-7b9379de44ca
TQID: https://experienceleague.adobe.com/hYy1-NOxnpCxVNYLV4QfiLJPec0IAQ4NlNy6RM6pYjA
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
topic_v2: id: e0eb8757-182f-49f3-94a4-1587d16f5094id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 135
ht-degree: 79%

---

# Cellules{#cells}



L&#39;activité **[!UICONTROL Cellules]** fournit une vue des différents sous-ensembles sous la forme de colonnes de données. Il facilite la manipulation des sous-ensembles et est également conçu pour encourager les possibilités de personnalisation.

![](assets/wf_split_cells.png)

Cette activité peut être configurée dans le but de renseigner des paramètres spécifiques en fonction des besoins de l&#39;utilisateur. Par défaut, le détail de chaque sous-ensemble est décrit dans une fenêtre dédiée au travers des onglets **[!UICONTROL Sélection]** et **[!UICONTROL Avancé]**. Dans l&#39;exemple ci-dessous, le formulaire a été modifié : un onglet **[!UICONTROL Données]** a été ajouté afin de permettre l&#39;association d&#39;une offre et d&#39;un niveau de priorité à chaque sous-ensemble.

![](assets/wf_split_cells_with_customization.png)

Pour réaliser ce paramétrage, les informations suivantes ont été ajoutées dans le formulaire des workflows (sous le noeud **[!UICONTROL Administration > Paramétrages > Formulaires de saisie]** de l&#39;arborescence Adobe Campaign) :

```
<container img="nms:miniatures/mini-enrich.png" label="Data">
                <input xpath="@code"/>
                <container xpath="select/node[@alias='@numTest']">
                  <input alwaysActive="true" expr="'long'" type="expr" xpath="@type"/>
                  <input alwaysActive="true" expr="'Priority'" type="expr" xpath="@label"/>
                  <input label="Priority" maxValue="12" minValue="0" type="number"
                         xpath="@value" xpathEditFromType="@type"/>
                </container>
                <container xpath="select/node[@alias='@test']">
                  <input alwaysActive="true" expr="'string'" type="expr" xpath="@type"/>
                  <input alwaysActive="true" expr="'Identifier'" type="expr" xpath="@label"/>
                  <input label="Cell identifier" xpath="@value"/>
                </container>
                <container xpath="select/node[@alias='linkTest']">
                  <input alwaysActive="true" expr="'link'" type="expr" xpath="@type"/>
                  <input alwaysActive="true" expr="'nms:offer'" type="expr" xpath="@dataType"/>
                  <input alwaysActive="true" expr="'Offre'" type="expr" xpath="@label"/>
                  <input computeStringAlias="@valueLabel" label="Offers" notifyPathList="@_cs|@valueLabel"
                         schema="nms:offer" type="linkEdit" xpath="@value"/>
                </container>
```

La personnalisation des formulaires de saisie sous Adobe Campaign est réservée à des utilisateurs experts. Pour plus d’informations à ce sujet, consultez cette [section](../../configuration/using/identifying-a-form.md).
