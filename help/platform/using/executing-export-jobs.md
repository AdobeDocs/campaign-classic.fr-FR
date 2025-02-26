---
product: campaign
title: Configuration des traitements d'export
description: Découvrez comment configurer et exécuter des traitements d'export dans Campaign.
feature: Overview
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 94fc473a-dc49-41e8-b572-51c162b09996
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '1037'
ht-degree: 100%

---

# Configuration des traitements d’export {#executing-export-jobs}



Les traitements d&#39;export vous permettent d&#39;accéder à la base de données et d&#39;en extraire les données : contacts, clients, listes, segments, etc.

Il peut, par exemple, être utile d&#39;exploiter dans un tableur les données de suivi d&#39;une campagne (historique de tracking, etc.). Les données de sortie peuvent être au format txt, CSV, TAB ou XML.

L’assistant d’export vous permet de configurer un export, de définir ses options et de lancer son exécution. Il s’agit d’une série d’écrans dont le contenu dépend du type d’export (simple ou multiple) et des droits de l’opérateur ou de l’opératrice.

L’assistant d’export s’affiche après la création d’un traitement d’export (voir [Créer des traitements d’import et d’export](../../platform/using/creating-import-export-jobs.md)).

## Etape 1 - Choix du modèle d’export {#step-1---choosing-the-export-template}

Lorsque vous lancez l’assistant d’export, vous devez d’abord sélectionner un modèle. Par exemple, pour configurer l’export des personnes destinataires récemment enregistrées, procédez comme suit :

1. Sélectionnez le dossier **[!UICONTROL Profils et Cibles > Traitement > Imports et exports génériques]**.
1. Cliquez sur **Nouveau** puis sur **Export** pour créer le modèle d&#39;export.

   ![](assets/s_ncs_user_export_wizard01.png)

1. Cliquez sur la flèche située à droite du champ **[!UICONTROL Modèle d&#39;export]** pour sélectionner votre modèle, ou cliquez sur l&#39;icône **[!UICONTROL Choisir le lien]** pour parcourir l&#39;arborescence.

   Le modèle natif est **[!UICONTROL Nouvel export texte]**. Ce modèle ne doit pas être modifié, mais vous pouvez le dupliquer pour en configurer un nouveau. Par défaut, les modèles d&#39;export sont enregistrés dans le nœud **[!UICONTROL Ressources > Modèles > Modèles de traitement]**.

1. Saisissez un nom pour cet export dans le champ **[!UICONTROL Libellé]**. Vous pouvez ajouter une description.
1. Sélectionnez le type d&#39;export. Deux types d&#39;export sont possibles : **[!UICONTROL Export simple]** pour n&#39;exporter qu&#39;un seul fichier et **[!UICONTROL Export multiple]** pour exporter plusieurs fichiers en une seule exécution, depuis un ou plusieurs types de documents sources.

## Etape 2 - Type de fichier à exporter {#step-2---type-of-file-to-export}

Sélectionnez le type de document à exporter, c&#39;est-à-dire le schéma des données à exporter.

Par défaut, lorsque l&#39;export est lancé depuis le nœud **[!UICONTROL Traitements]**, il s&#39;agit des données de la table des destinataires. Si l&#39;export est lancé à partir d&#39;une liste de données (à partir du **[!UICONTROL menu contextuel > Exporter]**), la table à laquelle appartiennent les données est automatiquement renseignée dans le champ **[!UICONTROL Type de document]**.

![](assets/s_ncs_user_export_wizard02.png)

* Par défaut, la case **[!UICONTROL Rapatrier en local le fichier généré après l&#39;export]** est cochée. Dans le champ **[!UICONTROL Fichier local]**, renseignez le nom et le chemin du fichier à créer, ou parcourez votre disque local en cliquant sur le dossier situé à droite du champ. Vous pouvez désélectionner cette option pour saisir le chemin d&#39;accès et le nom du fichier de sortie sur le serveur.

  >[!NOTE]
  >
  >Les traitements automatiques d&#39;import et d&#39;export sont toujours effectués sur le serveur.
  >
  >Si vous souhaitez n&#39;exporter qu&#39;une partie des données, cliquez sur le lien **[!UICONTROL Paramètres avancés...]** et indiquez le nombre de lignes à exporter dans le champ correspondant.

* Vous pouvez créer un export différentiel afin de n&#39;exporter que les enregistrements modifiés depuis la dernière exécution. Pour cela, cliquez sur le lien **[!UICONTROL Paramètres avancés]**, cliquez sur l&#39;onglet **[!UICONTROL Export différentiel]**, puis cochez la case **[!UICONTROL Activer l&#39;export différentiel]**.

  ![](assets/s_ncs_user_export_wizard02_b.png)

  Vous devez indiquer la date de la dernière modification. Elle peut être récupérée dans un champ ou calculée.

## Etape 3 - Définition du format de sortie {#step-3---defining-the-output-format}

Sélectionnez le format de sortie du fichier exporté. Les formats possibles sont les suivants : Texte, Texte à colonnes fixes, CSV, XML.

![](assets/s_ncs_user_export_wizard03.png)

* Pour le format **[!UICONTROL Texte]**, choisissez les délimiteurs à utiliser pour séparer les colonnes (tabulations, virgules, points-virgules, ou personnalisé) et les chaînes (guillemets simples ou doubles, ou aucun).
* Pour les format **[!UICONTROL Texte]** et **[!UICONTROL CSV]**, vous pouvez cocher l&#39;option **[!UICONTROL Utiliser la première ligne comme titre des colonnes]**.
* Indiquez le format de date et le format des nombres. Pour cela, cliquez sur le bouton **[!UICONTROL Editer]** correspondant au champ et utilisez l&#39;éditeur.
* Pour les champs contenant des valeurs énumérées, vous pouvez sélectionner **[!UICONTROL Exporter les libellés plutôt que les valeurs internes des énumérations]**. Par exemple, le titre peut être stocké sous la forme **1=M.**, **2=Mademoiselle**, **3=Mme.**. Si cette option est sélectionnée, **M.**, **Melle** et **Mme** seront exportés.

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

Vous pouvez ajouter des conditions de filtrage afin de ne pas exporter toutes les données. La configuration de ce filtrage correspond à celle du ciblage des destinataires dans l’assistant de diffusion. Pour plus d’informations, consultez [cette page](../../delivery/using/steps-defining-the-target-population.md).

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

Cliquez sur **[!UICONTROL Lancer la prévisualisation des données]** pour un aperçu du résultat de l&#39;export. Par défaut, les 200 premières lignes sont affichées. Cliquez sur les flèches à droite du champ **[!UICONTROL Lignes à visualiser]** pour modifier cette valeur.

![](assets/s_ncs_user_export_wizard07.png)

Cliquez sur les onglets en bas de l’assistant pour basculer de la prévisualisation des résultats en colonnes aux résultats en XML. Vous pouvez également visualiser les requêtes SQL générées.

## Etape 9 - Lancement de l’export {#step-9---launching-the-export}

Cliquez sur **[!UICONTROL Démarrer]** pour lancer l’export des données.

![](assets/s_ncs_user_export_wizard08.png)

Vous pouvez ensuite surveiller l’exécution du traitement d’import (voir la section [Surveillance de l’exécution des traitements](../../platform/using/monitoring-jobs-execution.md).
