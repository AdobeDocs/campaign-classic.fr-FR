---
title: Meilleures pratiques en matière d’interaction Adobe Campaign Classic
description: Cette section présente la méthode recommandée pour gérer le module Interaction dans Adobe Campaign Classic.
page-status-flag: never-activated
uuid: 88bcc1d5-be8f-4a63-9b4a-3843b5751abe
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: interaction-overview
discoiquuid: 85e8348f-d240-4a36-b7bd-645807dbc227
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 91f80adf0b84d45a71e07079d4e72fd7628b41c1

---


# Bonnes pratiques relatives aux interactions{#interaction-best-practices}

## Recommandations générales {#general-recommendations}

Cette section présente les meilleures pratiques de gestion du module Interaction dans Adobe Campaign Classic, notamment les règles d’éligibilité, les filtres prédéfinis, les activités de flux de travail et les options de base de données.

Interaction dans Adobe Campaign requiert une gestion attentive pour fonctionner de manière efficace. Vous devez trouver un équilibre entre le nombre de contacts, de catégories d’offres et d’offres. Si ces facteurs ne sont pas gérés avec attention, votre instance Adobe Campaign peut rencontrer des problèmes.

### Mise en oeuvre {#implementation}

Vous trouverez ci-dessous les éléments importants à garder à l’esprit lors de la mise en œuvre et de la configuration des interactions.

* Dans le cas du moteur batch (généralement utilisé dans les communications sortantes, telles que les emails), le débit est la préoccupation centrale, car plusieurs contacts peuvent être gérés simultanément. Le goulot d’étranglement typique est la performance de la base de données.
* La principale contrainte du moteur unitaire (généralement utilisé dans les communications entrantes, telles qu’une bannière sur un site web) est la latence, car quelqu’un attend une réponse. Le goulot d’étranglement typique est la performance de l’unité centrale.
* La conception du catalogue d’offres a un impact énorme sur les performances d’Adobe Campaign Classic.
* S’il existe de nombreuses offres, divisez-les en plusieurs catalogues d’offres.

### Règles d’éligibilité {#eligibility-rules}

Vous trouverez ci-dessous certaines bonnes pratiques en matière de règles d’éligibilité.

* Simplifiez les règles. La complexité des règles a une incidence sur la performance, car elle prolonge la recherche. Une règle est complexe si elle comprend plus de cinq conditions.
* Afin d’accroître la performance, les règles peuvent être décomposées en différents filtres prédéfinis partagés entre des offres multiples.
* Placez les règles de catégorie d’offres les plus restrictives à la position la plus élevée possible dans l’arbre. De cette manière, elles excluront le plus grand nombre de contacts en premier, ce qui réduit le nombre de cibles et empêche leur traitement par d’autres règles.
* Placez les règles les plus coûteuses en termes de temps ou de traitement en bas de l’arbre. De cette façon, ces règles seront uniquement exécutées sur l’audience cible restante.
* Démarrez au niveau d’une catégorie spécifique afin d’éviter d’analyser l’ensemble de l’arbre.
* Pour économiser le temps de traitement, précalculez les agrégats au lieu de créer des règles complexes avec des jointures. Pour ce faire, essayez de stocker les données client dans une table de référence qui peut être consultée au sein des règles d’éligibilité.
* Utilisez un nombre minimum de poids pour limiter le nombre de requêtes.
* Il est recommandé de disposer d’un nombre limité d’offres par emplacement d’offre. Cela accélère la récupération des offres dans n’importe quel emplacement donné.
* Servez-vous d’index, en particulier pour les colonnes de recherche fréquemment utilisées.

### Table de propositions {#proposition-table}

Vous trouverez ci-dessous quelques bonnes pratiques concernant la table de propositions.

* Utilisez un nombre minimum de règles pour que le traitement soit le plus rapide possible.
* Limitez le nombre d’enregistrements dans la table de propositions : conservez uniquement les enregistrements requis pour contrôler la mise à jour de son statut et ce que requièrent les règles, puis archivez-les dans un autre système.
* Réalisez une maintenance de base de données intensive sur la table de propositions, par exemple, en reconstruisant les index ou en recréant la table.
* Limitez le nombre de propositions par cible. N’en définissez pas davantage par rapport à ce que vous allez utiliser.
* Dans la mesure du possible, évitez les jointures dans les critères des règles.

## Conseils et astuces sur la gestion des offres {#tips-managing-offers}

Cette section contient des conseils plus détaillés sur la gestion des offres et l’utilisation du module Interaction dans Adobe Campaign Classic.

### Utilisation de plusieurs espaces d’offre dans une remise par courrier électronique {#multiple-offer-spaces}

Lorsque vous incluez des offres dans des remises, les offres sont généralement sélectionnées en amont dans le flux de production de la campagne par le biais d’une activité d’enrichissement (ou d’une autre activité similaire).

Lorsque vous sélectionnez des offres dans une activité d’enrichissement, vous pouvez choisir l’espace d’offre à utiliser. Cependant, quel que soit l’espace d’offre sélectionné, le menu de personnalisation de la remise dépend de l’espace d’offre configuré dans la remise.

Dans l’exemple ci-dessous, l’espace d’offre sélectionné dans la remise est **[!UICONTROL Courriel (Environnement - Destinataire)]**:

![](assets/Interaction-best-practices-offer-space-selected.png)

Si l’espace d’offre que vous sélectionnez dans la remise ne comporte pas de fonction de rendu HTML configurée, vous ne l’afficherez pas dans le menu de remise et il ne sera pas disponible pour la sélection. Encore une fois, il est indépendant de l’espace d’offre sélectionné dans l’activité Enrichissement.

Dans l’exemple ci-dessous, la fonction de rendu HTML est disponible dans la liste déroulante, car l’espace d’offre sélectionné dans la remise comporte une fonction de rendu :

![](assets/Interaction-best-practices-HTML-rendering.png)

Cette fonction insère du code tel que : `<%@ include proposition="targetData.proposition" view="rendering/html" %>`.

Lorsque vous sélectionnez la proposition, la valeur de l’attribut **[!UICONTROL vue]** est la suivante :
* &quot;render/html&quot; : rendu HTML. Il utilise la fonction de rendu HTML.
* &quot;offer/view/html&quot; : contenu HTML. Il n’utilise pas la fonction de rendu HTML. Il inclut uniquement le champ HTML.

Lorsque vous incluez plusieurs espaces d’offre dans une remise de courrier électronique unique et que certains d’entre eux ont des fonctions de rendu et que d’autres ne l’ont pas, vous devez vous rappeler quelles offres utilisent les espaces d’offre et quels espaces d’offre ont des fonctions de rendu.

Par conséquent, pour éviter tout problème, il est recommandé de définir une fonction de rendu HTML pour tous les espaces d’offre, même si votre espace d’offre ne nécessite que du contenu HTML.

### Définition du rang dans le tableau du journal des propositions {#rank-proposition-log-table}

Les espaces d’offre permettent de stocker des données dans le tableau des propositions lorsque des propositions sont générées ou acceptées :

![](assets/Interaction-best-practices-offer-space-storage.png)

Toutefois, cela ne s’applique qu’aux interactions entrantes.

Il est également possible de stocker des données supplémentaires dans le tableau des propositions lors de l’utilisation d’interactions sortantes, ainsi que lors de l’utilisation d’offres sortantes sans le module Interaction.

Tout champ de la table temporaire de processus dont le nom correspond à un nom de champ dans la table proposition est copié dans le même champ de la table proposition.

Par exemple, lors de la sélection manuelle d’une offre (sans interaction) dans un enrichissement, les champs standard sont définis comme suit :

![](assets/Interaction-best-practices-manual-offer-std-fields.png)

D’autres champs peuvent être ajoutés, par exemple un champ @grade :

![](assets/Interaction-best-practices-manual-offer-add-fields.png)

Puisqu’il existe un champ dans la table proposition nommé @grade, la valeur dans la table temporaire du flux de travail sera copiée.

Pour plus d’informations sur le stockage de champs supplémentaires dans le tableau des propositions, voir [Intégration d’une offre via un flux de travail](../../interaction/using/integrating-an-offer-via-a-workflow.md#storing-offer-rankings-and-weights).

Pour les offres sortantes avec Interaction, cela s’avère utile lorsque plusieurs offres sont sélectionnées et que vous souhaitez enregistrer l’ordre dans lequel elles seront affichées dans un courrier électronique.

Vous pouvez également stocker des métadonnées supplémentaires directement dans le tableau des propositions, telles que le niveau de dépense actuel, afin de conserver des enregistrements historiques sur la dépense au moment de la génération des offres.

Lors de l’utilisation de l’interaction sortante, le champ @grade peut être ajouté, comme dans l’exemple ci-dessus, mais sa valeur est automatiquement définie en fonction de l’ordre renvoyé par l’interaction. Par exemple, si vous utilisez Interaction pour sélectionner trois offres, les valeurs 1, 2 et 3 sont renvoyées dans le champ @grade.

Lorsque vous utilisez Interaction et sélectionnez manuellement des offres, l’utilisateur peut combiner les deux approches. Par exemple, l’utilisateur peut définir manuellement le champ @grade sur 1 pour l’offre sélectionnée manuellement et utiliser une expression telle que &quot;1 + @grade&quot; pour les offres renvoyées par Interaction. En supposant que l’interaction sélectionne trois offres, les offres renvoyées par les deux approches seront classées 1 à 4 :

![](assets/Interaction-best-practices-manual-offer-combined.png)

### Extension du schéma nms:offer {#extending-nms-offer-schema}

Lors de l’extension du schéma nms:offer, veillez à suivre la structure prête à l’emploi déjà configurée :
* Définissez un nouveau champ pour le stockage de contenu sous `<element name="view">`.
* Chaque nouveau champ doit être défini deux fois. Une fois sous forme de champ XML normal, et une fois sous forme de champ XML CDATA avec &quot;_jst&quot; ajouté au nom. Par exemple :

   ```
   <element label="Price" name="price" type="long" xml="true"/>
   <element advanced="true" label="Script price" name="price_jst" type="CDATA" xml="true"/>
   ```

* Tout champ contenant des URL à suivre doit être placé sous `<element name="trackedUrls">` lequel se trouve sous `<element name="view" >`.