---
title: Requête
seo-title: Requête
description: Requête
seo-description: null
page-status-flag: never-activated
uuid: 32f4f467-5083-414f-8616-1aa4bf2b5867
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: b53d9810-f61f-4257-b410-e4d30f78429d
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f8cf2f72dcf2ab48a42faf7931ca831b6431548d

---


# Requête{#query}

## Créer une requête {#creating-a-query}

Une requête permet de sélectionner une cible selon des critères. Vous pouvez associer un code segment au résultat de la requête et y insérer des données additionnelles.
Pour plus d&#39;informations sur les exemples de requêtes, consultez cette [section](../../workflow/using/querying-recipient-table.md).

>[!NOTE]
>
>Les activités de requête ne sont pas compatibles avec les champs CLOB lors de l’utilisation d’Oracle.

![](assets/s_user_segmentation_wizard_9.png)

For more on using and managing additional data, refer to [Adding data](#adding-data).

The **[!UICONTROL Edit query...]** link lets you define the targeting type, the restrictions, and the selection criteria for the population in the following way:

1. Sélectionnez la dimension de ciblage et de filtrage. Par défaut, la cible est sélectionnée parmi les destinataires. La liste des filtres de restriction est la même que celle utilisée lors du ciblage d&#39;une diffusion.

   La dimension de ciblage correspond au type d&#39;élément sur lequel on va travailler, par exemple la population ciblée par l&#39;opération.

   La dimension de filtrage permet d&#39;aller chercher ces éléments, par exemple les informations liées à la personne ciblée (les contrats, les soldes de comptes, etc.).

   For more on this, refer to [Targeting and filtering dimensions](../../workflow/using/building-a-workflow.md#targeting-and-filtering-dimensions).

   ![](assets/s_user_segmentation_query_edit.png)

   A query can be based on data from the inbound transition, if necessary, by selecting **[!UICONTROL Temporary schema]** when choosing targeting and filtering dimensions.

   ![](assets/query_temporary_table.png)

1. Définissez les populations à l’aide de l’assistant. Les champs à saisir peuvent différer selon le type de cible. Vous pouvez prévisualiser la population ciblée avec vos critères actuels à l’aide de l’ **[!UICONTROL Preview]** onglet.

   La création et l&#39;utilisation des filtres et des requêtes sont présentées dans cette [section](../../platform/using/filtering-options.md).

   ![](assets/s_user_segmentation_wizard.png)

1. If you have selected **[!UICONTROL Filtering conditions]** at step 1 or using the **[!UICONTROL Filters]** > **[!UICONTROL Advanced filter...]** option, then you will have to manually add filtering criteria later on.

   Vous pouvez également ajouter des conditions de groupement de données en cochant la case correspondante. Pour cela, la dimension de filtrage doit impérativement être différente de la dimension de ciblage de la requête. Pour plus d&#39;informations concernant le groupement, consultez cette [section](../../workflow/using/querying-using-grouping-management.md).

   Vous pouvez également ajouter d’autres critères à l’aide du générateur d’expression et le combiner avec les options logiques ET, OU et EXCEPT. Vous pouvez ensuite afficher un aperçu de la combinaison **[!UICONTROL Corresponding SQL query...]** de critères. Voir à ce propos cette [section](../../platform/using/defining-filter-conditions.md#building-expressions).

   Enregistrez votre filtre si vous souhaitez pouvoir le réutiliser ultérieurement.

   ![](assets/s_user_segmentation_query_advanced.png)

## Ajouter des données {#adding-data}

Les colonnes additionnelles permettent de collecter des informations supplémentaires sur la population ciblée, par exemple ses numéros de contrats, ses abonnements à des newsletters ou son origine. Ces données peuvent être stockées dans la base de données Adobe Campaign ou dans une base externe.

The **[!UICONTROL Add data...]** link lets you select the additional data to collect.

![](assets/wf_add_data_link.png)

Sélectionnez d&#39;abord le type de données à ajouter :

![](assets/wf_add_data_1st_option.png)

* Sélectionnez **[!UICONTROL Data linked to the filtering dimension]** les données dans la base de données Adobe Campaign.
* Sélectionnez **[!UICONTROL External data]** pour ajouter des données à partir d’une base de données externe. Cette option n’est disponible que si vous avez acheté l’option Accès **aux données** fédérées. For more on this, refer to [Accessing an external database (FDA)](../../workflow/using/accessing-an-external-database--fda-.md).
* Sélectionnez l’ **[!UICONTROL An offer proposition]** option pour ajouter un ensemble de colonnes qui vous permet de stocker la meilleure proposition générée par le moteur d’offre. This option is only available if you have purchased the **Interaction** module.

Si aucun module optionnel n&#39;est installé sur la plate-forme, cette étape n&#39;est pas affichée. Vous accédez directement à l&#39;étape suivante.

Pour ajouter des données de la base Adobe Campaign :

1. Sélectionnez le type de données que vous souhaitez ajouter. Il peut s&#39;agir de données appartenant à la dimension de filtrage ou de données stockées dans des tables liées.

   ![](assets/query_add_columns.png)

1. Lorsque les données appartiennent à la dimension de filtrage de la requête, il suffit de les sélectionner dans la liste des champs disponibles afin de les faire apparaître parmi les colonnes de sortie.

   ![](assets/wf_add_data_field_selection.png)

   Vous pouvez ajouter :

   * Champ calculé sur la base de données provenant de la population ciblée ou d’un total (nombre d’achats en attente au cours du dernier mois, montant moyen d’un reçu, etc.). Par exemple, accédez à [Sélection de données](../../workflow/using/targeting-data.md#selecting-data).
   * A new field, created using the **[!UICONTROL Add]** button to the right of the list of output columns.

      Vous pouvez également ajouter une collection d’informations, par exemple une liste de contrats, les 5 dernières livraisons, etc. Les collections coïncident avec des champs pouvant avoir plusieurs valeurs pour le même profil (relation 1-N). Pour plus d’informations, reportez-vous à la section [Modification de données](../../workflow/using/targeting-data.md#editing-additional-data)supplémentaires.

Pour ajouter une collection d&#39;informations liées à une population ciblée :

1. À la première étape de l’assistant, sélectionnez l’ **[!UICONTROL Data linked to the filtering dimension]** option :
1. Select the table which contains the information you want to collect and click **[!UICONTROL Next]**.

   ![](assets/wf_add_data_linked_table.png)

1. Si nécessaire, indiquez le nombre d’éléments de la collection que vous souhaitez conserver en sélectionnant l’une des valeurs du **[!UICONTROL Data collected]** champ. Par défaut, toutes les lignes de la collection sont récupérées, puis filtrées selon les conditions spécifiées à l’étape suivante.

   * If a single element of the collection coincides with the filtering conditions for this collection, select **[!UICONTROL Single row]** in the **[!UICONTROL Data collected]** field.

      >[!IMPORTANT]
      >
      >Ce mode optimise la requête SQL générée grâce à une jointure directe sur les éléments de la collection.
      >
      >Si la condition initiale n&#39;est pas respectée, le résultat peut être erroné (lignes manquantes ou doublons).

   * If you choose to recover several lines (**[!UICONTROL Limit the line count]**) you can specify the number of lines to collect.
   * Si les colonnes collectées contiennent des agrégats, par exemple le nombre d&#39;échecs déclarés, la dépense moyenne sur un site, etc. vous pouvez utiliser la **[!UICONTROL Aggregates]** valeur.
   ![](assets/query_add_collection_param.png)

1. Définissez la sous-sélection des éléments de la collection. Par exemple : les achats des 15 derniers jours seulement.

   ![](assets/query_add_columns_collection_filter.png)

1. Si vous avez sélectionné l’ **[!UICONTROL Limit the line count]** option, définissez l’ordre dans lequel les données collectées doivent être filtrées. Une fois que le nombre de lignes collectées est supérieur au nombre de lignes que vous avez indiqué de conserver, l’ordre de filtrage vous permet de spécifier les lignes à conserver.

## Exemple : ciblage sur des attributs destinataires simples {#example--targeting-on-simple-recipient-attributes}

Dans l&#39;exemple suivant, la requête cherchera à identifier les hommes de 18 à 30 ans et vivant en France. Cette requête pourra par exemple être utilisée dans un workflow visant à leur faire parvenir une offre qui leur est spécialement réservée.

>[!NOTE]
>
>D&#39;autres exemples de requête sont présentés dans [cette section](../../workflow/using/querying-recipient-table.md).

1. Name your query then select the **[!UICONTROL Edit query...]** link.
1. Select **[!UICONTROL Filtering conditions]** in the list of types of filter available.
1. Renseignez les différents critères correspondant à la cible souhaitée. Ici, les critères sont combinés à l’aide de l’opérateur ET. Pour faire partie de la sélection, ils devront donc réunir les quatre conditions suivantes :

   * Les destinataires dont la civilité est &quot;M.&quot; (également possible en utilisant le champ **Genre** et la valeur **Masculin**).
   * Les destinataires ayant moins de 30 ans.
   * Les destinataires ayant plus de 18 ans.
   * Les destinataires dont le pays de résidence est la France.
   ![](assets/query_example.png)

   Vous pouvez visualiser le code SQL correspondant à votre combinaison de critères :

   ![](assets/query_example_sql.png)

1. Affichez un aperçu des destinataires correspondant à votre requête via l&#39;onglet correspondant afin de vérifier que vos critères sont correctement renseignés :

   ![](assets/query_example_preview.png)

1. Save your filters so that you can use them again at a later date by clicking **[!UICONTROL Finish]** > **[!UICONTROL OK]**.
1. Continue editing your workflow by adding other activities to it. Once it has been launched and the previous query step finished, the number of recipients found will be displayed. You can display further details using the mouse pop-up menu (right click the transition > **[!UICONTROL Display the target...]**).

   ![](assets/query_example_result.png)

## Paramètres de sortie {#output-parameters}

* tableName
* schema
* recCount

Cet ensemble de trois valeurs identifie la population ciblée par la requête. **[!UICONTROL tableName]** est le nom de la table qui enregistre les identificateurs cible, **[!UICONTROL schema]** est le schéma de la population (généralement nms:destinataire) et **[!UICONTROL recCount]** est le nombre d’éléments de la table.

Cette valeur correspond au schéma de la table de travail. Ce paramètre est valide pour toutes les transitions avec **[!UICONTROL tableName]** et **[!UICONTROL schema]**.

## Optimisation de vos requêtes {#optimizing-queries}

La section ci-dessous présente les meilleures pratiques pour optimiser les requêtes exécutées sur Adobe Campaign afin de limiter la charge de travail sur la base de données et d’améliorer l’expérience utilisateur.

### Jointures et index {#joins-and-indexes}

* Les requêtes efficaces reposent sur des index.
* Utilisez un index pour toutes les jointures.
* La définition de liens sur le schéma détermine les conditions de jointure. La table liée doit avoir un index unique sur la clé primaire et la jointure doit se trouver sur ce champ.
* Effectuez des jointures en définissant des clés sur des champs numériques au lieu de champs de chaîne.
* Evitez d’exécuter des jointures externes. Dans la mesure du possible, utilisez l’enregistrement d’ID zéro pour obtenir la fonctionnalité de jointure externe.
* Utilisez le type de données approprié pour les jointures.

   Assurez-vous que la `where` clause est du même type que le champ.

   Une erreur courante est : `iBlacklist='3'` où `iBlacklist` est un champ numérique et `3` signifie une valeur de texte.

   Assurez-vous de connaître le plan d&#39;exécution de votre requête. Evitez les analyses de table complètes, en particulier pour les requêtes en temps réel ou quasi en temps réel qui s’exécutent toutes les minutes.

Pour plus d’informations, reportez-vous aux[bonnes pratiques](https://helpx.adobe.com/campaign/kb/acc-data-model-best-practices.html) du modèle de données et aux sections de mappage [de](../../configuration/using/database-mapping.md) base de données.

### Fonctions {#functions}

* Attention aux fonctions comme `Lower(...)`. Lorsque la fonction Lower est utilisée, l’index n’est pas utilisé.
* Vérifiez soigneusement les requêtes à l’aide de l’instruction &quot;J’aime&quot; ou des instructions &quot;supérieur&quot; ou &quot;inférieur&quot;. Appliquez &quot;Upper&quot; sur la saisie de l’utilisateur et non sur le champ de base de données.

   For more on functions, refer to [this section](../../platform/using/defining-filter-conditions.md#list-of-functions).

### Filtrage des dimensions {#filtering-dimensions}

Utilisez la dimension de filtrage de la requête au lieu d’utiliser l’opérateur &quot;existe tel que&quot;.

![](assets/optimize-queries-filtering.png)

Dans les requêtes, les conditions &quot;existe tel que&quot; dans les filtres ne sont pas efficaces. Ils sont l’équivalent d’une sous-requête dans SQL :

`select iRecipientId from nmsRecipient where iRecipientId IN (select iRecipientId from nmsBroadLog where (...))`

Il est recommandé d’utiliser plutôt la dimension de filtrage de la requête :

![](assets/optimize-queries-filtering2.png)

L’équivalent de la dimension de filtrage dans SQL est la jointure interne :

`select iRecipientId from nmsRecipient INNER JOIN nmsBroadLog ON (...)`

For more on filtering dimensions, refer to [this section](../../workflow/using/building-a-workflow.md#targeting-and-filtering-dimensions).

### Architecture {#architecture}

* Créez une plateforme de développement avec des volumes, des paramètres et une architecture similaires à ceux de la plate-forme de production.
* Utilisez les mêmes valeurs pour les environnements de développement et de production. Dans la mesure du possible, utilisez la même méthode :

   * Système d&#39;exploitation,
   * Version,
   * Données,
   * Application,
   * Volumes.
   >[!NOTE]
   >
   >Une fonctionnalité qui fonctionne dans un environnement de développement peut ne pas fonctionner dans un environnement de production où les données peuvent être différentes. Essayer d&#39;identifier les principales différences afin d&#39;anticiper les risques et de préparer des solutions.

* Effectuez des configurations qui correspondent aux volumes cible. Les gros volumes nécessitent des configurations spécifiques. Une configuration qui fonctionnait pour 100 000 destinataires peut ne pas fonctionner pour 10 000 000 destinataires.

   Pensez à la façon dont le système va évoluer lorsqu&#39;il sera en service. Le simple fait que quelque chose fonctionne à petite échelle ne signifie pas qu&#39;il sera adapté à de plus grands volumes. Les essais doivent être effectués avec des volumes similaires au volume en production. Vous devez également évaluer l’effet des modifications des volumes (nombre d’appels, taille de la base de données) aux heures de pointe, aux jours de pointe et pendant toute la durée du projet.
