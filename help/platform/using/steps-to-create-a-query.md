---
product: campaign
title: Étapes pour créer une requête
description: Étapes pour créer une requête
feature: Query Editor
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
audience: platform
content-type: reference
topic-tags: creating-queries
exl-id: cf914366-8bac-4d68-a0cc-2a43d102eef2
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: ht
source-wordcount: '952'
ht-degree: 100%

---

# Étapes pour créer une requête{#steps-to-create-a-query}



Les étapes de construction d&#39;une requête dans Adobe Campaign sont les suivantes :

1. Sélectionner la table de travail. Pour plus d&#39;informations, consultez la section [Etape 1 - Sélection de la table](#step-1---choose-a-table).
1. Sélectionner les données à extraire. Pour plus d&#39;informations, consultez la section [Etape 2 - Sélection des données à extraire](#step-2---choose-data-to-extract).
1. Définir la séquence de tri des données. Pour plus d&#39;informations, consultez la section [Etape 3 - Tri des données](#step-3---sort-data).
1. Filtrer les données. Pour plus d&#39;informations, consultez la section [Etape 4 - Filtrage des données](#step-4---filter-data).
1. Mettre en forme les données. Pour plus d&#39;informations, consultez la section [Etape 5 - Formatage des données](#step-5---format-data).
1. Afficher le résultat. Pour plus d&#39;informations, consultez la section [Etape 6 - Prévisualisation des données](#step-6---preview-data).

>[!NOTE]
>
>Dans le requêteur générique, toutes ces étapes sont proposées. Lorsqu&#39;une requête est créée dans un autre contexte, certaines étapes peuvent être omises.\
>L&#39;activité Requête est présentée dans [cette section](../../workflow/using/query.md).

## Etape 1 - Sélection de la table {#step-1---choose-a-table}

Sélectionnez la table contenant les données sur lesquelles vous souhaitez effectuer une requête dans la fenêtre **[!UICONTROL Type de document]**. Au besoin, filtrez les données en utilisant le champ de filtrage ou le bouton **[!UICONTROL Filtres]**.

![](assets/query_editor_nveau_21.png)

## Etape 2 - Sélection des données à extraire {#step-2---choose-data-to-extract}

Dans la fenêtre **[!UICONTROL Données à extraire]**, sélectionnez les données à afficher : ces champs constitueront les colonnes de sortie.

Sélectionnez par exemple **[!UICONTROL Age]**, **[!UICONTROL Clé primaire]**, **[!UICONTROL Domaine de l&#39;email]** et **[!UICONTROL Ville]**. Les résultats seront organisés en fonction de cette sélection. Réordonnez les colonnes de sortie avec les flèches bleues situées à droite de la fenêtre.

![](assets/query_editor_nveau_01.png)

Vous pouvez éditer une expression en y insérant une formule ou réaliser un traitement sur une fonction d&#39;agrégat. Pour cela, cliquez dans le champ de la colonne **[!UICONTROL Expression]** puis choisissez **[!UICONTROL Editer l&#39;expression]**.

![](assets/query_editor_nveau_97.png)

Vous pouvez regrouper les données des colonnes de sortie : pour cela, cochez la case **[!UICONTROL Oui]** dans la colonne **[!UICONTROL Grouper]** de la fenêtre **[!UICONTROL Données à extraire]**. Cette fonction génère un résultat autour de l&#39;axe de groupement coché. Un exemple de requête avec regroupement est proposé dans [cette section](../../workflow/using/querying-delivery-information.md).

![](assets/query_editor_nveau_56.png)

* La fonction de groupement **[!UICONTROL Gérer les groupements (GROUP BY + HAVING)]** permet un groupement (&quot;group by&quot;) et une sélection de ce qui a été groupé (&quot;having&quot;). Elle s&#39;applique aux champs inscrits en colonne de sortie. Par exemple, cette option regroupe les choix d&#39;une colonne de sortie et récupère un type d&#39;information particulier : les destinataires âgés de 35 à 50 ans.

  Voir à ce propos [cette section](../../workflow/using/querying-using-grouping-management.md).

* La fonction **[!UICONTROL Supprimer les doublons (DISTINCT)]** permet de dédoublonner des résultats identiques obtenus en colonne de sortie. Si l&#39;on recense les destinataires en sélectionnant les champs Nom, Prénom et Email en colonne de sortie, ceux qui ont un prénom, un nom et une adresse email identiques sont éliminés. En effet, il s&#39;agit du même contact renseigné plus d&#39;une fois dans la base. Ainsi, un seul résultat sera pris en compte.

## Etape 3 - Tri des données {#step-3---sort-data}

La fenêtre **[!UICONTROL Tris]** permet de trier le contenu des colonnes. Utilisez les flèches pour modifier l&#39;ordre de tri des colonnes :

* Avec **[!UICONTROL Tri]**, le contenu de chaque colonne est ordonné de A à Z. Le contenu est ordonné par ordre croissant s&#39;il est chiffré.
* Avec **[!UICONTROL Tri descendant]**, le contenu de la colonne est ordonné de Z à A ou dans un ordre décroissant si le contenu est chiffré. Un tri descendant est utile par exemple pour visualiser les ventes de disques, avec les meilleurs scores affichés en haut de la liste.

Dans cet exemple, les données seront triées en fonction de l&#39;âge des destinataires, du plus jeune au plus âgé.

![](assets/query_editor_nveau_57.png)

## Etape 4 - Filtrage des données {#step-4---filter-data}

Le requêteur permet de filtrer les données pour affiner la recherche.

Les filtres proposés dépendent de la table sur laquelle porte la requête.

![](assets/query_editor_nveau_09.png)

Après la sélection de **[!UICONTROL Critères de filtrage]**, vous accédez à la section **[!UICONTROL Eléments de la cible]** : vous pouvez y définir comment filtrer les données à collecter.

* Pour créer un nouveau filtre, sélectionnez les champs, opérateurs et valeurs nécessaires à la création de la formule. Elle devra être vérifiée pour permettre la sélection des données. Il est possible de combiner plusieurs conditions (voir à ce sujet la section [Définir les conditions de filtrage](../../platform/using/defining-filter-conditions.md)).
* Pour utiliser des filtres enregistrés au préalable, déroulez la liste du bouton **[!UICONTROL Ajouter]**, cliquez sur **[!UICONTROL Filtre prédéfini]** puis sélectionnez un filtre pré-enregistré.

  ![](assets/query_editor_15.png)

* Les filtres créés dans le **[!UICONTROL Requêteur générique]** peuvent être utilisés dans d&#39;autres applications de requêtage (et inversement). Pour enregistrer un filtre, cliquez sur l&#39;icône **[!UICONTROL Enregistrer]**.

  >[!NOTE]
  >
  >La création et l&#39;utilisation des filtres sont présentées dans la section [Options de filtrage](../../platform/using/filtering-options.md).

Dans l&#39;exemple ci-dessous, pour ne récupérer que les destinataires de langue française, choisissez : &quot;langue des destinataires **égal à** FR&quot;.

![](assets/query_editor_nveau_89.png)

>[!NOTE]
>
>Vous pouvez accéder directement à une option en inscrivant la formule suivante dans le champ **Valeur** : **$(options:OPTION_NAME)**.

Cliquez sur l&#39;onglet **[!UICONTROL Aperçu]** afin de visualiser le résultat de la condition de filtrage. Dans ce cas, chaque destinataire de langue française est affiché avec son nom, prénom et adresse email.

![](assets/query_editor_nveau_98.png)

Les utilisateurs maîtrisant le langage SQL peuvent cliquer sur **[!UICONTROL Requête SQL correspondante]** pour visualiser la requête en SQL.

![](assets/query_editor_nveau_99.png)

## Etape 5 - Formatage des données {#step-5---format-data}

Après le paramétrage de filtres de restriction, vous accédez à la fenêtre **[!UICONTROL Formatage des données]**. Elle permet de réordonner l&#39;affichage des colonnes de sortie, de transformer les données et de modifier la casse des libellés de colonnes. Elle permet également d&#39;appliquer une formule sur le résultat final, grâce à un champ calculé.

>[!NOTE]
>
>Au sujet des types de champs calculés, voir la section [Création de champs calculés](../../platform/using/defining-filter-conditions.md#creating-calculated-fields).

Une colonne qui n&#39;est pas cochée ne s&#39;affichera pas dans la fenêtre de prévisualisation des données.

![](assets/query_editor_nveau_10.png)

La colonne **[!UICONTROL Transformation]** permet de modifier la casse du libellé d&#39;une colonne. Sélectionnez une colonne puis cliquez dans la colonne **[!UICONTROL Transformation]**. Les modifications possibles sont :

* **[!UICONTROL Passer en minuscules]**,
* **[!UICONTROL Passer en majuscules]**,
* **[!UICONTROL Première lettre en majuscule]**.

![](assets/query_editor_nveau_42.png)

## Etape 6 - Prévisualisation des données {#step-6---preview-data}

La fenêtre **[!UICONTROL Prévisualisation des données]** est la dernière étape. Cliquez sur **[!UICONTROL Lancer la prévisualisation des données]** pour obtenir le résultat de la requête. Il est disponible soit en colonnes, soit au format XML. Cliquez sur l&#39;onglet **[!UICONTROL Requêtes SQL générées]** pour visualiser la requête en langage SQL.

Dans cet exemple, les données sont triées selon l&#39;âge des destinataires ciblés et dans un ordre croissant.

![](assets/query_editor_nveau_11.png)

>[!NOTE]
>
>Dans la fenêtre **[!UICONTROL Prévisualisation des données]**, les 200 premières lignes de résultat s&#39;affichent par défaut. Pour modifier cette quantité, saisissez un chiffre dans la case **[!UICONTROL Lignes à visualiser]**, validez puis cliquez sur **[!UICONTROL Lancer la prévisualisation des données]**.
