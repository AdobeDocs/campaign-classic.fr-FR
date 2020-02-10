---
title: Cellules
seo-title: Cellules
description: Cellules
seo-description: null
page-status-flag: never-activated
uuid: 1b18928f-04e1-4268-ab8e-ff74d78599de
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: f7187d42-56e9-4681-b172-22abd43ecd29
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Cellules{#cells}

L’ **[!UICONTROL Cells]** activité fournit une vue des différents sous-ensembles sous la forme de colonnes de données. Il facilite la manipulation des sous-ensembles et est également conçu pour encourager les possibilités de personnalisation.

![](assets/wf_split_cells.png)

Cette activité peut être configurée pour entrer des paramètres spécifiques en fonction des besoins de l’utilisateur. Par défaut, les détails de chaque sous-ensemble sont détaillés dans une fenêtre dédiée via les **[!UICONTROL Selection]** onglets et les **[!UICONTROL Advanced]** . Dans l’exemple ci-dessous, le formulaire a été modifié : un **[!UICONTROL Data]** onglet a été ajouté pour activer l’association d’une offre et un niveau de priorité pour chaque sous-ensemble.

![](assets/wf_split_cells_with_customization.png)

For this configuration, the following information was added to the workflow form (in the **[!UICONTROL Administration > Configurations > Input forms]** node of the Adobe Campaign tree):

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

La personnalisation des formulaires de saisie sous Adobe Campaign est réservée à des utilisateurs experts. Reportez-vous à ce sujet à cette [section](../../configuration/using/identifying-a-form.md).
