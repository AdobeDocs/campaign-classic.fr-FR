---
product: campaign
title: Bonnes pratiques relatives aux cubes
description: Bonnes pratiques relatives aux cubes
feature: Reporting, Monitoring
badge: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
hide: true
hidefromtoc: true
exl-id: 5f22fa2c-b648-4126-9a24-1798adfa8f34
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '1574'
ht-degree: 100%

---

# Bonnes pratiques relatives aux cubes{#concepts-and-methodology}



## Mise en classe des données {#data-binning}

La mise en classe permet de simplifier l&#39;affichage des données en regroupant les valeurs sur critères. Selon les informations dont vous disposez, vous pouvez ainsi définir des tranches d&#39;âges, grouper des domaines d&#39;email, restreindre à une énumération de valeurs, restreindre explicitement les données à afficher et regrouper toutes les autres dans une colonne ou une ligne dédiée, etc.

Globalement, trois types de mise en classe sont possibles :

1. Utilisation de plages de valeurs définies manuellement. Par exemple, âge, panier d’achat moyen, nombre de diffusions ouvertes, etc.). Voir à ce sujet la section [Définir chaque classe](#defining-each-bin).
1. Dynamiquement, selon les valeurs d&#39;une énumération : on n&#39;affiche que les valeurs contenues dans l’énumération et toutes les valeurs différentes sont regroupées dans « Autres ». Pour plus d&#39;informations, consultez la section [Gérer dynamiquement les classes](#dynamically-managing-bins).
1. En utilisant des plages de valeurs, toutes les autres étant regroupées. Par exemple, les 18 à 25 ans, les 26 à 59 ans, et les autres. Pour plus d&#39;informations, consultez la section [Créer des plages de valeurs](#creating-value-ranges).

Pour activer la mise en classe, cochez l&#39;option correspondante lors de la création de la dimension.

![](assets/s_advuser_cube_class_00.png)

Vous pouvez créer chaque classe manuellement ou les lier à une énumération existante.

Pour générer automatiquement les classes, Adobe Campaign propose également un assistant : les valeurs peuvent être réparties en N groupes, ou regroupées selon les plus représentées dans la base.

### Définition de chaque classe {#defining-each-bin}

Pour créer unitairement chaque classe, sélectionnez l&#39;option **[!UICONTROL Définir chaque classe]** et utilisez le tableau pour créer les différentes classes.

![](assets/s_advuser_cube_class_01.png)

Cliquez sur le bouton **[!UICONTROL Ajouter]** pour créer une nouvelle classe et listez les valeurs qui seront regroupées dans la classe.

![](assets/s_advuser_cube_class_02.png)

Dans l&#39;exemple ci-dessous, les langues seront réparties dans trois groupes : Anglais-Allemand-Néerlandais, Français-Italien-Espagnol et Autres.

![](assets/s_advuser_cube_class_03.png)

Vous pouvez utiliser un masque SQL pour regrouper plusieurs valeurs selon un filtre. Pour cela, cochez l&#39;option **[!UICONTROL Oui]** dans la colonne **[!UICONTROL Utiliser un masque SQL]** et saisissez le filtre SQL à appliquer dans la colonne **[!UICONTROL Valeur ou expression]**.

Dans l&#39;exemple ci-dessous, tous les domaines d&#39;email commençant par **yahoo** (yahoo.fr, yahoo.com, yahoo.be, etc.), ou par **ymail** (ymail.com, ymail.eu, etc.) seront regoupés sous le libellé **YAHOO!**, ainsi que les adresses du domaine **rocketmail.com**.

![](assets/s_advuser_cube_class_03b.png)

### Gérer dynamiquement les classes {#dynamically-managing-bins}

Les valeurs peuvent être gérées dynamiquement via les énumérations. Ainsi, seules les valeurs contenues dans l&#39;énumération seront affichées. Lorsque les valeurs de l&#39;énumération sont modifiées, le contenu du cube est adapté automatiquement.

Pour créer ce type de mise en classe des valeurs, les étapes sont les suivantes :

1. Créez une nouvelle dimension et activez la mise en classe.
1. Sélectionnez l&#39;option **[!UICONTROL Lier dynamiquement les valeurs à une énumération]** et sélectionnez l&#39;énumération correspondante.

   ![](assets/s_advuser_cube_class_04.png)

   Lorsque les valeurs de l&#39;énumération sont mises à jour, les classes sont automatiquement adaptées, sans aucune action côté utilisateur.

### Création de plages de valeurs {#creating-value-ranges}

Vous pouvez regrouper les valeurs dans des plages selon l&#39;intervalle souhaité.

Pour définir manuellement les intervalles, cliquez sur le bouton **[!UICONTROL Ajouter]** et choisissez l&#39;option **[!UICONTROL Définir un intervalle]** :

![](assets/s_advuser_cube_class_05.png)

Indiquez ensuite les bornes inférieures et supérieures et cliquez sur **[!UICONTROL Ok]** pour valider.

### Génération automatique de classes {#generating-bins-automatically}

Vous pouvez également générer automatiquement les classes. Pour cela, cliquez sur le lien **[!UICONTROL Générer les classes...]**.

![](assets/s_advuser_cube_class_06.png)

Vous pouvez, au choix :

* Récupérer les valeurs les plus représentées

  Dans l&#39;exemple ci-dessus, les 4 valeurs les plus représentées seront affichées, les autres seront comptabilisées et regroupées sous le libellé &#39;Autres&#39;.

* Générer les classes sous forme de plages

  Dans l&#39;exemple ci-dessus, Adobe Campaign crée automatiquement 4 plages de valeurs de même taille pour afficher les valeurs de la base.

Dans ce cas, le filtre sélectionné au niveau du schéma des faits est ignoré.

### Énumérations {#enumerations}

Afin d&#39;augmenter la lisibilité et la pertinence des rapports, Adobe Campaign vous permet de créer des énumérations spécifiques pour regrouper différentes valeurs dans une même classe. Ces énumérations, réservées à la mise en classe, sont référencés dans les cubes puis affichées dans les rapports.

Adobe Campaign propose ainsi une énumération sur les domaines qui permet d&#39;afficher la liste des domaines des emails de tous les contacts en base, regroupés par FAI, comme dans l&#39;exemple ci-dessous :

![](assets/nmx_report_sample.png)

Elle est construite selon le modèle suivant :

![](assets/nmx_enum_domain.png)

Pour créer un rapport utilisant cette énumération, créez un Cube utilisant la dimension **[!UICONTROL Domaine de l&#39;email]**. Choisissez l&#39;option **[!UICONTROL Activer la mise en classe]** puis **[!UICONTROL Lier dynamiquement les valeurs à une énumération]**. Choisissez alors l&#39;énumération **Domaines(domain)** présentée ci-dessus. Toutes les valeurs pour lesquelles aucun alias n&#39;a été défini seront regroupées sous le libellé **Autres**.

![](assets/nmx_add_dimension.png)

Créez ensuite un rapport basé sur ce Cube pour afficher les valeurs.

Il suffira de modifier l&#39;énumération pour mettre à jour le rapport associé. Par exemple, créez la valeur **Adobe** et ajoutez l&#39;alias **adobe.com**, au niveau de l&#39;énumération : le rapport est automatiquement mis à jour avec la valeur Adobe.

![](assets/nmx_add_alias.png)

L&#39;énumération **[!UICONTROL Domaines]** est utilisée pour générer les rapports natifs affichant la liste des domaines. Pour adapter le contenu de ces rapports, vous pouvez modifier cette liste.

Vous pouvez créer d&#39;autres énumérations réservées à la mise en classe et les utiliser dans d&#39;autres Cubes : toutes les valeurs d&#39;alias seront regroupées dans les classes définies dans le premier onglet de l&#39;énumération.

## Calcul et utilisation dʼagrégats {#calculating-and-using-aggregates}

Vous pouvez précalculer les données les plus volumineuses dans des agrégats.

Les agrégats sont pertinents lorsque vous manipulez un gros volume de données. Ils sont mis à jour automatiquement selon les paramètres définis dans la boîte de workflow dédiée, afin d&#39;intégrer les dernières données collectées dans les indicateurs.

Les agrégats sont définis au niveau du cube, dans l&#39;onglet correspondant.

>[!NOTE]
>
>Le workflow de mise à jour des calculs de l&#39;agrégat peut être paramétré dans l&#39;agrégat lui-même, mais l&#39;agrégat peut également être mis à jour au travers d&#39;un workflow externe dans lequel est référencé le cube correspondant.

Pour créer un nouvel agrégat, les étapes sont les suivantes :

1. Cliquez sur l&#39;onglet **[!UICONTROL Agrégats]** du cube puis sur le bouton **[!UICONTROL Ajouter]**.

   ![](assets/s_advuser_cube_agregate_02.png)

1. Saisissez le libellé de l&#39;agrégat, puis ajoutez les dimensions à calculer.

   ![](assets/s_advuser_cube_agregate_03.png)

1. Sélectionnez la dimension et le niveau. Recommencez l&#39;opération pour chaque dimension et chaque niveau à calculer.
1. Cliquez sur l&#39;onglet **[!UICONTROL Workflow]** pour créer le workflow d&#39;agrégation.

   ![](assets/s_advuser_cube_agregate_04.png)

   * L&#39;activité **[!UICONTROL Planificateur]** permet de définir la fréquence de mise à jour des calculs. Le planificateur est présenté dans [cette section](../../workflow/using/scheduler.md).
   * L&#39;activité **[!UICONTROL Mise à jour d&#39;agrégat]** permet de choisir le mode de mise à jour à appliquer : complète ou partielle.

     Par défaut, une mise à jour complète est réalisée à chaque calcul. Pour permettre une mise à jour partielle des données, sélectionnez l&#39;option correspondante puis définissez les conditions de mise à jour.

     ![](assets/s_advuser_cube_agregate_05.png)

## Définition des mesures {#defining-measures}

Les types de mesures à réaliser sont définis dans l&#39;onglet **[!UICONTROL Mesures]** du cube. Vous pouvez calculer des sommes, des moyennes, des écarts, etc.

Il est possible de créer autant de mesures que nécessaire : vous choisirez ensuite celle que vous souhaitez afficher ou masquer dans le tableau. Voir à ce propos [Affichage des mesures](#displaying-measures).

Pour définir une nouvelle mesure, les étapes sont les suivantes :

1. Cliquez sur le bouton **[!UICONTROL Ajouter]** situé au-dessus de la liste des mesures et sélectionnez le type de mesure et la formule à calculer.

   ![](assets/s_advuser_cube_create_a_measure.png)

1. Au besoin, selon l&#39;opérateur sélectionné, choisissez l&#39;expression sur laquelle porte l&#39;opération.

   Le bouton **[!UICONTROL Sélection avancée]** permet de créer des formules de calcul complexes. Voir à ce sujet [cette section](../../platform/using/about-queries-in-campaign.md).

   ![](assets/s_advuser_cube_create_a_measure_01.png)

1. Le lien **[!UICONTROL Filtrer les données de la mesure...]** permet de restreindre le champ du calcul et de ne l&#39;appliquer qu&#39;à certaines données de la base.

   ![](assets/s_advuser_cube_create_a_measure_02.png)

1. Saisissez le libellé de la mesure et ajoutez une description, puis cliquez sur **[!UICONTROL Terminer]** pour créer la mesure.

## Affichage des mesures {#displaying-measures}

Vous pouvez paramétrer l&#39;affichage des mesures dans le tableau selon vos besoins. Vous pouvez ainsi choisir :

* l’ordre d’affichage des mesures (voir la section [Ordre d’affichage](#display-sequence)),
* les informations à afficher/masquer dans le rapport (consultez la section [Configuration de l’affichage](#configuring-the-display)).
* les mesures à afficher : pourcentage, total, nombre de décimales, etc. (consultez la section [Modification du type de mesure affichée](#changing-the-type-of-measure-displayed)).

### Ordre d&#39;affichage {#display-sequence}

Les mesures calculées dans le cube sont configurées à partir du bouton **[!UICONTROL Mesures]**.

Vous pouvez changer l&#39;ordre d&#39;affichage en déplaçant les lignes. Dans l&#39;exemple suivant, les données de la France sont déplacées en bas de la liste : elles seront alors affichées dans la dernière colonne.

![](assets/s_advuser_cube_in_report_config_04.png)

### Configuration de l’affichage {#configuring-the-display}

Le paramétrage des mesures, lignes et colonnes affichées peut être réalisé unitairement pour chaque mesure ou au niveau général. Une icône spécifique permet d&#39;accéder à la fenêtre de sélection des modes d&#39;affichage.

* Cliquez sur l’icône **[!UICONTROL Modifier la configuration du tableau croisé dynamique]** pour accéder à la fenêtre de configuration.

  Vous pouvez choisir d&#39;afficher ou non les libellés des mesures ainsi que leur disposition (en ligne ou en colonne).

![](assets/s_advuser_cube_in_report_config_05.png)

Les options de coloration permet d&#39;identifier visuellement les valeurs les plus importantes afin d&#39;optimiser la lisibilité des informations.

![](assets/s_advuser_cube_in_report_config_06.png)

### Modification du type de mesure affichée {#changing-the-type-of-measure-displayed}

Au niveau de chaque mesure, vous pouvez définir lʼunité et le formatage à appliquer.

![](assets/s_advuser_cube_in_report_config_07.png)

## Partage du rapport {#sharing-a-report}

Une fois le rapport paramétré, vous pouvez choisir de le conserver et de le partager avec d&#39;autres opérateurs.

Pour cela, cliquez sur l&#39;icône **[!UICONTROL Afficher les propriétés du rapport]** et activez l&#39;option **[!UICONTROL Partager ce rapport]**.

![](assets/cube_share_option.png)

Indiquez la catégorie à laquelle ce rapport appartient et sa pertinence. Voir à ce propos les sections **Ordre d&#39;affichage** et **Définir les options de filtrage** de [cette page](../../reporting/using/configuring-access-to-the-report.md#report-display-context).

Pour valider ces modifications, vous devez enregistrer le rapport.

![](assets/cube_share_confirm.png)

## Création de filtres {#creating-filters}

Vous pouvez créer des filtres afin de n&#39;afficher qu&#39;une partie des données.

Pour cela :

1. Cliquez sur l&#39;icône **[!UICONTROL Ajouter un filtre]**.

   ![](assets/neolap_add_filter.png)

1. Sélectionnez la dimension sur laquelle porte le filtrage.

   ![](assets/neolap_define_filter.png)

1. Sélectionnez le type de filtre à appliquer et indiquez sa précision.

   ![](assets/neolap_ceate_filter.png)

1. Une fois créé, le filtre apparaît au-dessus du rapport.

   ![](assets/neolap_filter_zone.png)

   Cliquez sur le filtre pour l&#39;éditer.

   Cliquez sur la croix pour supprimer le filtre.

   Vous pouvez combiner autant de filtres que nécessaire : ils seront tous affichés dans cette zone.

   ![](assets/neolap_multiple_filters.png)

A chaque modification (ajout, modification, suppression de filtres), cliquez sur la flèche pour relancer le calcul du rapport.

Un filtre peut également être créé à partir d&#39;une sélection. Pour cela, choisissez la ou les cellules, lignes et colonnes sources et cliquez sur l&#39;icône **[!UICONTROL Ajouter un filtre]**.

Pour sélectionner une ligne, une colonne ou une cellule, cliquez dessus avec le bouton gauche de la souris. Pour la dé-sélectionner, cliquez une seconde fois.

![](assets/neolap_create_filter_from_selection.png)

Le filtre est automatiquement appliqué et ajouté dans la zone des filtres, au-dessus du rapport.

![](assets/neolap_create_filter_display.png)
