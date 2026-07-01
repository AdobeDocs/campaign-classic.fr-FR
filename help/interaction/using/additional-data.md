---
product: campaign
title: Données additionnelles
description: Additional data
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: 01adb584-5308-4d41-a6f1-223a97efa10f
TQID: https://experienceleague.adobe.com/OU8fQxcH3HXoSJbG-N-9DplMjkDVAT6tLXY-FWzPuwE
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9id: b6fcaf36-3bc4-4604-94f3-81b5d3f41ecf
subfeature_v2: id: a72a22e0-8c8d-4019-ba42-3f2644aa91a3id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: e0eb8757-182f-49f3-94a4-1587d16f5094
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 733
ht-degree: 100%

---

# Additional data{#additional-data}



Lors d’un appel au moteur Interaction, vous pouvez transférer des informations contextuelles supplémentaires.Ces données peuvent provenir des données de la cible stockées dans la table de travail d’un workflow (canal sortant) ou des données d’appel envoyées par le site web au moment de l’appel (canal entrant).Vous pouvez utiliser ces données supplémentaires dans les règles d’admissibilité et dans la personnalisation des offres. Vous pouvez également les stocker dans une table de propositions.

Pour le canal entrant, il peut être intéressant de récupérer, par exemple, la langue du navigateur de la personne qui a consulté l’offre ou le nom de l’agent ou de l’agente du centre d’appel.Vous pouvez ensuite utiliser ces données d’appel dans les règles d’admissibilité, afin de présenter une offre uniquement aux personnes qui consultent la page web en français ou en anglais.

Dans un workflow de ciblage (canal sortant), vous pouvez utiliser les données de la cible lors d’un appel au moteur.Vous pouvez, par exemple, enrichir la cible avec des données provenant d’une transaction associée à la personne destinataire, ou d’une base de données externe, via le FDA.

## Configuration des données additionnelles {#additional-data-configuration}

Vous devez étendre le schéma **nms:interaction** associé à l’environnement et déclarer la liste des champs supplémentaires qui seront utilisés lors d’un appel au moteur Interaction.Lors de la création de la règle d&#39;éligibilité ou de la personnalisation d&#39;une offre, ces champs deviennent accessibles depuis le nœud **Interaction** (voir la section [Utilisation des données additionnelles](#using-additional-data)).

Pour le canal entrant, vous devez ajouter les champs de données d&#39;appel dans le nœud **Interaction**.

```
<element label="Interactions" labelSingular="Interaction" name="interaction">
  <attribute label="Navigation language" name="navigationLanguage" type="string"/>
</element>
```

>[!NOTE]
>
>Les collections xml sont supportées pour le canal entrant, mais les liens vers d&#39;autres schémas ne le sont pas.

Pour le canal sortant, vous devez ajouter, dans le nœud **Interaction**, un élément **targetData** contenant les champs additionnels.

```
<element label="Interactions" labelSingular="Interaction" name="interaction">
  <element name="targetData">
    <attribute label="Date of last transaction" name="lastTransactionDate" type="datetime"/>
  </element>
</element>
```

>[!NOTE]
>
>Les collections ne sont pas prises en charge pour le canal sortant.Cependant, vous pouvez créer des liens vers d’autres schémas.

Si vous souhaitez stocker ces données dans la table des propositions, vous devez également étendre le schéma **nms:propositionRcp** et déclarer ces champs.

```
<element label="Recipient offer propositions" labelSingular="Recipient offer proposition" name="propositionRcp">
  <attribute label="Last transaction date" name="lastTransactionDate" type="datetime"/>
  <attribute label="Navigation language" name="navigationLanguage" type="string"/>
</element>
```

## Implémentation des données additionnelles {#additional-data-implementation}

### Canal entrant (page Web) {#input-channel--web-page-}

Pour passer des données additionnelles lors de l&#39;appel au moteur, vous devez ajouter la variable **interactionGlobalCtx** dans le code Javascript de la page web. Insérez, dans cette variable, le nœud **Interaction** contenant les données d&#39;appel. Vous devez respecter la même structure xml que celle du schéma **nms:interaction**.Voir à ce sujet la section [Configuration des données additionnelles](#additional-data-configuration).

```
interactionGlobalCtx = "<interaction navigationLanguage='"+myLanguage+"'/>";
```

### Canal sortant {#output-channel}

Ici, vous devez créer un workflow de ciblage chargeant des données supplémentaires dans la table de travail en respectant la même structure xml et les mêmes noms internes que dans le schéma **nms:interaction**.Voir à ce sujet la section [Configuration des données additionnelles](#additional-data-configuration).

## Utilisation des données additionnelles {#using-additional-data}

### Règles d’éligibilité {#eligibility-rules}

Il est possible d&#39;utiliser les données additionnelles dans les règles d&#39;éligibilité au niveau des offres, des catégories et des poids.

Par exemple, vous pouvez choisir de ne présenter l&#39;offre qu&#39;aux personnes visionnant la page en anglais.

![](assets/ita_calldata_query.png)

>[!NOTE]
>
>Vous devez limiter la règle aux canaux pour lesquels les données sont définies. Dans notre exemple, nous limitons la règle au canal web entrant (champ **[!UICONTROL Pris en compte si]**).

### Personnalisation {#personalization}

Vous pouvez également utiliser ces données supplémentaires lors de la personnalisation d’une offre.Vous pouvez par exemple ajouter une condition pour la langue de navigation.

![](assets/ita_calldata_perso.png)

>[!NOTE]
>
>Sachez que vous devez limiter la personnalisation aux canaux pour lesquels les données sont définies.Dans notre exemple, nous limitons la règle au canal web entrant.

Si vous avez personnalisé une offre sur des données additionnelles, celles-ci ne s&#39;afficheront pas par défaut dans la prévisualisation car elles ne sont pas disponibles en base. Sur l&#39;onglet **[!UICONTROL Exemple de données d&#39;appel]** de l&#39;environnement, vous devez ajouter les échantillons de valeurs à utiliser dans la prévisualisation. Respectez la même structure xml que celle de l’extension de schéma **nms:interaction**.Voir à ce sujet la section [Configuration des données additionnelles](#additional-data-configuration).

![](assets/ita_calldata_preview.png)

Lors de la prévisualisation, cliquez sur **[!UICONTROL Options de personnalisation du contenu pour l&#39;aperçu]** et sélectionnez une valeur dans le champ **[!UICONTROL Données d&#39;appel]**.

![](assets/ita_calldata_preview2.png)

### Stockage {#storage}

Au moment d’un appel au moteur, il est possible de stocker des données supplémentaires dans la table des propositions afin d’enrichir la base de données.Ces données peuvent être utilisées, par exemple dans des rapports, dans des calculs de retour sur investissement ou pour des processus ultérieurs.

>[!NOTE]
>
>Vous devez au préalable avoir étendu le schéma **nms:propositionRcp** et déclaré les champs qui contiendront les données à stocker.Voir à ce sujet la section [Configuration des données additionnelles](#additional-data-configuration).

Au niveau de l&#39;emplacement, positionnez-vous sur l&#39;onglet **[!UICONTROL Stockage]** et cliquez sur le bouton **[!UICONTROL Ajouter]**.

Dans la colonne **[!UICONTROL Chemin de stockage]**, sélectionnez le champ de stockage dans la table des propositions. Dans la colonne **[!UICONTROL Expression]**, sélectionnez le champ additionnel dans le noeud **[!UICONTROL Interaction]**.

Il est possible de récupérer les données d&#39;appel au moment de la génération de la proposition ou au moment de son acceptation (lorsque la personne clique sur l&#39;offre).

![](assets/ita_calldata_storage.png)
