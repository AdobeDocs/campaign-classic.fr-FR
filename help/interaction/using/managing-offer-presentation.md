---
title: Gérer la présentation des offres
seo-title: Gérer la présentation des offres
description: Gérer la présentation des offres
seo-description: null
page-status-flag: never-activated
uuid: cf4614b9-a322-4170-aa6d-4f138f8ca2d2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
discoiquuid: f6e44634-3a13-480e-ab44-f3c744054a96
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Gérer la présentation des offres{#managing-offer-presentation}

## Aperçu des règles de présentation {#presentation-rules-overview}

Interaction permet de contrôler le flux des propositions d&#39;offres à l&#39;aide de règles dites de présentation. Ces règles, propres à Interaction, sont des règles de typologie. Elles permettent d&#39;exclure certaines offres en fonction de l&#39;historique des propositions déjà faites à un destinataire. Elles sont référencées au niveau de l&#39;environnement.

## Créer et référencer une règle de présentation d&#39;offre {#creating-and-referencing-an-offer-presentation-rule}

1. Accédez au noeud **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Typology management]** > **[!UICONTROL Typology rules]** .
1. Create a typology rule and choose the **[!UICONTROL Offer presentation]** type.

   ![](assets/offer_typology_001.png)

1. Spécifiez éventuellement le canal sur lequel doit porter la règle.

   ![](assets/offer_typology_002.png)

1. Configurez les critères d’application de la règle. Pour plus d’informations, reportez-vous aux paramètres [des règles de](#presentation-rule-settings)présentation.
1. Accédez au noeud **[!UICONTROL Administration]** > **[!UICONTROL Campaign execution]** > **[!UICONTROL Typology management]** > **[!UICONTROL Typologies]** et créez une typologie qui regroupe toutes les **[!UICONTROL Offer presentation]** règles de type.

   ![](assets/offer_typology_003.png)

1. Une fois la typologie créée, positionnez-vous au niveau des règles de typologie et regroupez-les sous la typologie que vous venez de créer.

   ![](assets/offer_typology_004.png)

1. Au niveau de votre environnement d&#39;offres, référencez la typologie à l&#39;aide de la liste déroulante.

   ![](assets/offer_typology_005.png)

## Paramètres des règles de présentation {#presentation-rule-settings}

### Critères d&#39;application {#application-criteria-}

Les critères d’application disponibles dans l’ **[!UICONTROL General]** onglet vous permettent de spécifier les offres auxquelles la règle de présentation s’appliquera. Pour ce faire, vous devez créer une requête et choisir les offres concernées, comme décrit ci-dessous.

1. Dans la règle de typologie, cliquez sur le **[!UICONTROL Edit the rule application conditions...]** lien pour créer votre requête.

   ![](assets/offer_typology_006.png)

1. Dans la fenêtre de requête, vous pouvez appliquer un filtre sur les offres auxquelles vous souhaitez appliquer la règle de typologie.

   Vous pouvez par exemple sélectionner une catégorie d&#39;offres.

   ![](assets/offer_typology_008.png)

### Dimensions des offres {#offer-dimensions}

In the **[!UICONTROL Offer presentation]** tab, you must specify the same dimensions for the presentation rule as those configured in the environment.

Le **[!UICONTROL Targeting dimension]** rapport coïncide avec la table des destinataires (par défaut : nms:destinataires) qui recevra les propositions d’offre. Le **[!UICONTROL Storage dimension]** tableau coïncide avec le tableau qui contient l’historique des propositions liées à la dimension de ciblage (par défaut:nms:propositionRcp).

![](assets/offer_typology_009.png)

>[!NOTE]
>
>Vous pouvez également utiliser des tableaux non standard. Si vous souhaitez utiliser une dimension de ciblage spécifique, vous devez créer des tableaux ainsi qu’un environnement dédié à l’aide du mappage de cible. Pour plus d’informations, reportez-vous à la section [Création d’un environnement](../../interaction/using/live-design-environments.md#creating-an-offer-environment)d’offre.

### Période {#period}

Il s&#39;agit de la période glissante durant laquelle les propositions sont prises en compte dans la règle. Elle restreint dans le temps la prise en compte de l&#39;historique des propositions d&#39;offres. La règle ne s&#39;applique pas aux propositions d&#39;offres faites en dehors de cette période.

The period starts **n** days before the proposition date and ends **n** days afterwards, where **n** corresponds to the number entered in the **[!UICONTROL Period considered]** field:

* Pour un emplacement de type entrant, la date des propositions est la date de présentation de l&#39;offre.
* Pour un emplacement de type sortant, la date des propositions est la date de contact de la diffusion (par exemple la date d&#39;envoi saisie dans un workflow de ciblage).

Utilisez les flèches du champ pour modifier le nombre de jours ou saisissez directement la durée souhaitée (par exemple : &quot;2j 6h&quot;).

![](assets/offer_typology_010.png)

### Nombre de propositions {#number-of-propositions}

Vous pouvez fixer le nombre maximum de propositions à faire avant d&#39;exclure la ou les offres concernées.

Utilisez la flèche ascendante ou descendante pour modifier le nombre de propositions d&#39;offres.

![](assets/offer_typology_011.png)

## Définir les propositions et les destinataires {#defining-propositions-and-recipients}

The **[!UICONTROL Propositions to count]** section lets you specify both the recipients and the propositions which will lead to the exclusion of the offers defined in the **[!UICONTROL General]** tab if they appear a certain number of times in the propositions history.

### Filtrer les propositions {#filtering-propositions}

Vous pouvez sélectionner des critères de filtrage pour exclure des propositions selon le canal, les offres impactées ou l&#39;état des propositions déjà effectuées.

![](assets/offer_typology_014.png)

Ces critères représentent les applications les plus fréquentes des règles de présentation. Pour utiliser d’autres critères, vous pouvez créer une requête à l’aide du **[!UICONTROL Limit propositions...]** lien. For more on this, refer to the [Creating a query on propositions](#creating-a-query-on-propositions) section.

* **Filtre sur le canal**

   **[!UICONTROL On the same channel only]** : vous permet d’exclure les propositions d’offre sur le canal spécifié dans l’ **[!UICONTROL General]** onglet.

   Par exemple, le canal spécifié pour la règle dans l’ **[!UICONTROL General]** onglet est Courriel. Si les offres auxquelles s’applique la règle étaient jusqu’à présent uniquement proposées sur le canal Web, le moteur d’interaction peut les présenter dans une remise par courrier électronique. Cependant, une fois les offres présentées par courrier électronique, le moteur d’interaction choisit un canal différent pour présenter les offres.

   >[!NOTE]
   >
   >Il s&#39;agit bien du canal et non de l&#39;emplacement. Si la règle doit exclure une offre sur le canal web, l&#39;offre destinée à être proposée sur un site web à deux emplacements, (une bannière et le corps de texte de la page par exemple), n&#39;apparaîtra pas sur le site si elle a déjà été proposée auparavant.
   >
   >For a workflow involving offer presentation, the rules are only correctly taken into account if they are configured on **[!UICONTROL All channels]**.

* **Filtre sur l&#39;offre**

   Ce filtre permet de limiter à certains ensembles d&#39;offres les propositions d&#39;offres à comptabiliser.

   **[!UICONTROL All offers]** : valeur par défaut. Aucun filtre n’est appliqué aux offres.

   **[!UICONTROL Offer being presented]** : l’offre spécifiée dans l’ **[!UICONTROL General]** onglet est exclue si elle a déjà été présentée.

   **[!UICONTROL Offers from the same category]** : une offre est exclue si une offre de la même catégorie a déjà été présentée.

   **[!UICONTROL The offers which the rule applies to]** : lorsque plusieurs offres sont définies dans l’ **[!UICONTROL General]** onglet, chaque proposition d’offre de cet ensemble d’offres est prise en compte et se termine par l’exclusion de toutes les offres si le seuil de proposition est atteint.

   Par exemple, les offres 2, 3 et 5 sont définies dans l’ **[!UICONTROL General]** onglet. Le nombre maximal de propositions est fixé à 2. Si les offres 2 et 5 sont présentées une seule fois, le nombre de propositions comptées sera 2. Par conséquent, l’offre 3 ne sera jamais présentée.

* **Filtre sur l&#39;état de la proposition**

   Ce filtre permet de choisir directement les états les plus courants des propositions d&#39;offres à prendre en compte dans l&#39;historique des propositions.

   **[!UICONTROL Regardless of the proposition status]** : valeur par défaut. Aucun filtre n’est appliqué à l’état de proposition.

   **[!UICONTROL Accepted or rejected propositions]** : vous permet d’exclure les offres présentées précédemment qui ont été acceptées ou rejetées.

   **[!UICONTROL Accepted propositions]** : vous permet d’exclure les offres présentées précédemment qui ont été acceptées.

   **[!UICONTROL Rejected propositions]** : vous permet d’exclure les offres présentées précédemment qui ont été rejetées.

### Définir les destinataires {#defining-recipients}

Pour spécifier les destinataires, cliquez sur le **[!UICONTROL Edit the query from the targeting dimension...]** lien et sélectionnez les destinataires concernés par la règle.

![](assets/offer_typology_012.png)

### Créer une requête sur les propositions {#creating-a-query-on-propositions}

To specify the propositions to be counted via a query, click the **[!UICONTROL Limit propositions...]** link and specify the criteria to be taken into account.

Dans l&#39;exemple ci-dessous, les propositions à comptabiliser au bout de deux présentations sont celles de la catégorie **Offres spéciales**, pour l&#39;emplacement **Centre d&#39;appels**, dont le poids est inférieur à **20**.

![](assets/offer_typology_013.png)

