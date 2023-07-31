---
product: campaign
title: Configuration des traitements d'export
description: Découvrez comment configurer et exécuter des traitements d'export dans Campaign.
fearture: Overview
badge-v7: label="v7" type="Informative" tooltip="S’applique à Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="S’applique également à Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 94fc473a-dc49-41e8-b572-51c162b09996
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: ht
source-wordcount: '1027'
ht-degree: 100%

---

# Configuration des traitements d’export {#executing-export-jobs}



Les traitements d&#39;export vous permettent d&#39;accéder à la base de données et d&#39;en extraire les données : contacts, clients, listes, segments, etc.

Par exemple, il peut s&#39;avérer utile d&#39;utiliser les données de tracking des campagnes (historique de tracking, etc.) dans une feuille de calcul. Les données de sortie peuvent être au format txt, CSV, TAB ou XML.

L&#39;assistant d&#39;export vous permet de paramétrer un export, de définir ses options et de lancer son exécution. Il s&#39;agit d&#39;une série d&#39;écrans dont le contenu dépend du type d&#39;export (simple ou multiple) et des droits de l&#39;opérateur.

L’assistant d’export s’affiche après la création d’un nouveau traitement d’export (voir la section [Création de traitements d’import et d’export](../../platform/using/creating-import-export-jobs.md)).

## Etape 1 - Choix du modèle d’export {#step-1---choosing-the-export-template}

Lorsque vous lancez l&#39;assistant d&#39;export, vous devez d&#39;abord sélectionner un modèle. A titre d&#39;exemple, pour configurer l&#39;export des destinataires qui se sont récemment inscrits, procédez comme suit :

1. Sélectionnez le dossier **[!UICONTROL Profils et Cibles > Traitement > Imports et exports génériques]**.
1. Cliquez sur **Nouveau** puis sur **Export** pour créer le modèle d&#39;export.

   ![](assets/s_ncs_user_export_wizard01.png)

1. Cliquez sur la flèche située à droite du champ **[!UICONTROL Modèle d&#39;export]** pour sélectionner votre modèle, ou cliquez sur l&#39;icône **[!UICONTROL Choisir le lien]** pour parcourir l&#39;arborescence.

   Le modèle natif est **[!UICONTROL Nouvel export texte]**. Ce modèle ne doit pas être modifié, mais vous pouvez le dupliquer pour paramétrer un nouveau modèle. Par défaut, les modèles d&#39;export sont enregistrés dans le nœud **[!UICONTROL Ressources > Modèles > Modèles de traitement]**.

1. Saisissez un nom pour cet export dans le champ **[!UICONTROL Libellé]**. Vous pouvez ajouter une description.
1. Sélectionnez le type d&#39;export. Deux types d&#39;export sont possibles : **[!UICONTROL Export simple]** pour n&#39;exporter qu&#39;un seul fichier et **[!UICONTROL Export multiple]** pour exporter plusieurs fichiers en une seule exécution, depuis un ou plusieurs types de documents sources.

## Etape 2 - Type de fichier à exporter {#step-2---type-of-file-to-export}

Sélectionnez le type de document à exporter, c&#39;est-à-dire le schéma des données à exporter.

Par défaut, lorsque l&#39;export est lancé depuis le nœud **[!UICONTROL Traitements]**, il s&#39;agit des données de la table des destinataires. Si l&#39;export est lancé à partir d&#39;une liste de données (à partir du **[!UICONTROL menu contextuel > Exporter]**), la table à laquelle appartiennent les données est automatiquement renseignée dans le champ **[!UICONTROL Type de document]**.

![](assets/s_ncs_user_export_wizard02.png)

* Par défaut, l&#39;option **[!UICONTROL Rapatrier en local le fichier généré après l&#39;export]** est cochée : dans le champ **[!UICONTROL Fichier local]**, renseignez le chemin et le nom du fichier à créer, ou parcourez votre disque local en cliquant sur le dossier situé à droite du champ. Vous pouvez décocher cette option pour saisir le chemin d&#39;accès et le nom du fichier de sortie sur le serveur.

  >[!NOTE]
  >
  >Les traitements automatiques d&#39;import et d&#39;export sont toujours effectués sur le serveur.
  >
  >Si vous souhaitez n&#39;exporter qu&#39;une partie des données, cliquez sur le lien **[!UICONTROL Paramètres avancés...]** et indiquez le nombre de lignes à exporter dans le champ correspondant.

* Vous pouvez créer un export différentiel afin de n&#39;exporter que les enregistrements modifiés depuis la dernière exécution. Pour cela, cliquez sur le lien **[!UICONTROL Paramètres avancés...]**, cliquez sur l&#39;onglet **[!UICONTROL Export différentiel]** et cochez l&#39;option **[!UICONTROL Activer l&#39;export différentiel]**.

  ![](assets/s_ncs_user_export_wizard02_b.png)

  Vous devez indiquer la date de la dernière modification. Elle peut être récupérée dans un champ ou calculée.

## Etape 3 - Définition du format de sortie {#step-3---defining-the-output-format}

Sélectionnez le format de sortie du fichier exporté. Les formats possibles sont les suivants : Texte, Texte à colonnes fixes, CSV, XML.

![](assets/s_ncs_user_export_wizard03.png)

* Pour le format **[!UICONTROL Texte]**, choisissez les délimiteurs à utiliser pour séparer les colonnes (tabulations, virgules, points-virgules, ou personnalisé) et les chaînes (guillemets simples ou doubles, ou aucun).
* Pour les format **[!UICONTROL Texte]** et **[!UICONTROL CSV]**, vous pouvez cocher l&#39;option **[!UICONTROL Utiliser la première ligne comme titre des colonnes]**.
* Indiquez les formats des dates et des nombres. Pour cela, cliquez sur le bouton **[!UICONTROL Editer...]** relatif au champ à paramétrer et renseignez l&#39;éditeur.
* Pour les champs contenant des valeurs énumérées, vous pouvez sélectionner **[!UICONTROL Exporter les libellés plutôt que les valeurs internes des énumérations]**. Par exemple, le titre peut être enregistré sous la forme **1=M.**, **2=Melle**, **3=Mme.**. Si cette option est sélectionnée, **M.**, **Melle** et **Mme** seront exportés.

## Etape 4 - Sélection des données {#step-4---data-selection}

Sélectionnez les champs à exporter. Pour cela :

1. Double-cliquez sur les champs de votre choix dans la liste **[!UICONTROL Champs disponibles]** afin de les ajouter à la section **[!UICONTROL Colonnes de sortie]**.
1. Utilisez les flèches à droite de la liste pour définir l&#39;ordre des champs dans le fichier de sortie.

   ![](assets/s_ncs_user_export_wizard04.png)

1. Cliquez sur le bouton **[!UICONTROL Ajouter]** pour faire appel à des fonctions. Pour plus d&#39;informations, consultez la section [Liste des fonctions](../../platform/using/defining-filter-conditions.md#list-of-functions).

## Etape 5 - Tri des colonnes {#step-5---sorting-columns}

Sélectionnez l&#39;ordre de tri des colonnes.

![](assets/s_ncs_user_export_wizard05.png)

## Etape 6 - Conditions de filtrage {#step-6---filter-conditions-}

Vous pouvez ajouter des conditions de filtrage afin de ne pas exporter toutes les données. Le paramétrage de ce filtrage correspond à celui du ciblage des destinataires dans l&#39;assistant de diffusion. Voir à ce sujet [cette page](../../delivery/using/steps-defining-the-target-population.md).

![](assets/s_ncs_user_export_wizard05_b.png)

## Etape 7 - Formatage des données {#step-7---data-formatting}

Vous pouvez modifier l&#39;ordre et le libellé des champs pour le fichier de sortie. Vous pouvez également appliquer des transformations aux données sources.

* Pour changer l&#39;ordre des colonnes à exporter, sélectionnez la colonne concernée et utilisez les flèches bleues situées à droite du tableau.
* Pour changer le libellé d&#39;un champ, cliquez dans la cellule de la colonne **[!UICONTROL Libellé]** correspondant au champ à modifier et saisissez le nouveau libellé. Appuyez sur la touche Entrée du clavier pour valider la saisie.
* Pour appliquer une transformation de casse au contenu d&#39;un champ, sélectionnez-la depuis la colonne **[!UICONTROL Transformation]**. Vous pouvez choisir :

   * Passer en majuscules
   * Passer en minuscules
   * Première lettre en majuscule

  ![](assets/s_ncs_user_export_wizard06.png)

* Cliquez sur l&#39;icône **[!UICONTROL Ajouter un champ calculé]** si vous voulez créer un champ calculé (par exemple, une colonne contenant le nom+le prénom). Voir à ce sujet la section [Champs calculés](../../platform/using/executing-import-jobs.md#calculated-fields).

Si vous exportez une collection d&#39;éléments (par exemple les abonnements des destinataires, les listes auxquelles ils appartiennent, etc.), vous devez indiquer le nombre d&#39;éléments de la collection que vous voulez exporter.

![](assets/s_ncs_user_export_wizard06_c.png)

## Etape 8 - Prévisualisation des données {#step-8---data-preview}

Cliquez sur **[!UICONTROL Lancer la prévisualisation des données]** pour avoir un aperçu du résultat de l&#39;export. Par défaut, les 200 premières lignes sont affichées. Cliquez sur les flèches à droite du champ **[!UICONTROL Lignes à visualiser]** pour modifier cette valeur.

![](assets/s_ncs_user_export_wizard07.png)

Cliquez sur les onglets en bas de l&#39;assistant pour basculer de l&#39;aperçu du résultat en colonnes, au résultat en XML. Vous pouvez également visualiser les requêtes SQL générées.

## Etape 9 - Lancement de l’export {#step-9---launching-the-export}

Cliquez sur **[!UICONTROL Démarrer]** pour lancer l’export des données.

![](assets/s_ncs_user_export_wizard08.png)

Vous pouvez ensuite surveiller l’exécution du traitement d’import (voir la section [Surveillance de l’exécution des traitements](../../platform/using/monitoring-jobs-execution.md).
