---
title: Additional data
seo-title: Additional data
description: Additional data
seo-description: null
page-status-flag: never-activated
uuid: 81a889ce-b02d-4593-95fa-1de5601182e0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: advanced-parameters
discoiquuid: 29339aad-fd8e-4dae-8f6e-2db87221ad04
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# Additional data{#additional-data}

Il est possible, lors de l&#39;appel au moteur d&#39;Interaction, de passer des données additionnelles contextuelles. Ces données peuvent provenir des données de la cible stockées dans la table de travail d&#39;un workflow (canal sortant) ou des données d&#39;appel envoyées par le site web au moment de l&#39;appel (canal entrant). Vous avez la possibilité d&#39;utiliser ces données additionnelles dans les règles d&#39;éligibilité, dans la personnalisation des offres, et vous pouvez également les stocker dans la table des propositions.

En entrant, il peut être intéressant de récupérer, par exemple, la langue de navigation de la personne qui a consulté l&#39;offre ou le nom de l&#39;agent dans le centre d&#39;appel. Vous pouvez ensuite utiliser ces données d&#39;appel (call data), dans les règles d&#39;éligibilité, pour ne proposer une offre qu&#39;à une personne visionnant la page web en anglais ou en français.

Dans un workflow de ciblage (canal sortant), vous pouvez utiliser les données de la cible (target data) lors de l&#39;appel au moteur. Vous pouvez, par exemple, enrichir la cible avec des données provenant d&#39;une transaction associée au destinataire, ou d&#39;une base externe, via le FDA.

## Configuration des données additionnelles {#additional-data-configuration}

Vous devez étendre le schéma **nms:interaction** lié à l’environnement et déclarer la liste des champs supplémentaires qui seront utilisés lors d’un appel au moteur d’interaction. Lors de la création de la règle d’éligibilité ou de la personnalisation d’une offre, ces champs deviennent accessibles à partir du noeud **Interaction** (voir [Utilisation de données](#using-additional-data)supplémentaires).

Pour l&#39;entrant, vous devez ajouter les champs de données d&#39;appel dans le noeud **Interaction**.

```
<element label="Interactions" labelSingular="Interaction" name="interaction">
  <attribute label="Navigation language" name="navigationLanguage" type="string"/>
</element>
```

>[!NOTE]
>
>Les collections xml sont supportées pour le canal entrant, mais les liens vers d&#39;autres schémas ne le sont pas.

Pour le sortant, vous devez ajouter, dans le noeud **Interaction**, un élément **targetData** contenant les champs additionnels.

```
<element label="Interactions" labelSingular="Interaction" name="interaction">
  <element name="targetData">
    <attribute label="Date of last transaction" name="lastTransactionDate" type="datetime"/>
  </element>
</element>
```

>[!NOTE]
>
>Les collections ne sont pas supportées pour le canal sortant. Cependant, vous pouvez créer des liens vers d&#39;autres schémas.

Si vous souhaitez stocker ces données dans la table des propositions, vous devez également étendre le schéma **nms:propositionRcp** et déclarer ces champs.

```
<element label="Recipient offer propositions" labelSingular="Recipient offer proposition" name="propositionRcp">
  <attribute label="Last transaction date" name="lastTransactionDate" type="datetime"/>
  <attribute label="Navigation language" name="navigationLanguage" type="string"/>
</element>
```

## Implémentation des données additionnelles {#additional-data-implementation}

### Canal entrant (page Web) {#input-channel--web-page-}

To transfer additional data when calling the engine, you have to add the **interactionGlobalCtx** variable into the web page&#39;s JavaScript code. Insert the **Interaction** node containing the call data into this variable. You must respect the same xml structure that is in the **nms:interaction** schema. Reportez-vous à : Configuration [de données](#additional-data-configuration)supplémentaire.

```
interactionGlobalCtx = "<interaction navigationLanguage='"+myLanguage+"'/>";
```

### Canal sortant {#output-channel}

You must create a targeting workflow loading additional data in the work table by respecting the same xml structure and same internal names as in the **nms:interaction** schema. Reportez-vous à : Configuration [de données](#additional-data-configuration)supplémentaire.

## Utilisation des données additionnelles {#using-additional-data}

### Règles d’éligibilité {#eligibility-rules}

Il est possible d&#39;utiliser les données additionnelles dans les règles d&#39;éligibilité au niveau des offres, des catégories et des poids.

Par exemple, vous pouvez choisir de ne présenter l&#39;offre qu&#39;aux personnes visionnant la page en anglais.

![](assets/ita_calldata_query.png)

>[!NOTE]
>
>Vous devez limiter la règle aux canaux pour lesquels les données sont définies. Dans notre exemple, nous limitons la règle au canal web entrant (champ **[!UICONTROL Pris en compte si]**).

### Personnalisation  {#personalization}

Il est également possible d&#39;utiliser ces données additionnelles lors de la personnalisation d&#39;une offre. Vous pouvez, par exemple, ajouter une condition sur la langue de navigation.

![](assets/ita_calldata_perso.png)

>[!NOTE]
>
>Vous devez limiter la personnalisation aux canaux pour lesquels les données sont définies. Dans notre exemple, nous limitons la règle au canal web entrant.

If you have personalized an offer using additional data, this data will not appear in the preview by default because it is not available in the database. In the environment&#39;s **[!UICONTROL Example of call data]** tab, you must add value samples to use in the preview. Please respect the same xml structure that is in the **nms:interaction** schema extension. For more on this, refer to [Additional data configuration](#additional-data-configuration).

![](assets/ita_calldata_preview.png)

Lors de la prévisualisation, cliquez sur **[!UICONTROL Options de personnalisation du contenu pour l&#39;aperçu]** et sélectionnez une valeur dans le champ **[!UICONTROL Données d&#39;appel]**.

![](assets/ita_calldata_preview2.png)

### Stockage {#storage}

Au moment de l&#39;appel au moteur, il est possible de stocker les données additionnelles dans la table des propositions afin d&#39;enrichir la base. Ces données pourront, par exemple, être utilisée dans les rapports, dans le calcul du ROI, ou dans des processus ultérieurs.

>[!NOTE]
>
>You must have extended the **nms:propositionRcp** schema and declared the fields that will contain the data to be stored. Pour en savoir plus : Configuration [de données](#additional-data-configuration)supplémentaire.

Au niveau de l&#39;emplacement, positionnez-vous sur l&#39;onglet **[!UICONTROL Stockage]** et cliquez sur le bouton **[!UICONTROL Ajouter]**.

Dans la colonne **[!UICONTROL Chemin de stockage]**, sélectionnez le champ de stockage dans la table des propositions. Dans la colonne **[!UICONTROL Expression]**, sélectionnez le champ additionnel dans le noeud **[!UICONTROL Interaction]**.

Il est possible de récupérer les données d&#39;appel au moment de la génération de la proposition ou au moment de son acceptation (lorsque la personne clique sur l&#39;offre).

![](assets/ita_calldata_storage.png)

