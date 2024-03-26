---
product: campaign
title: Partage
description: En savoir plus sur l'activité de workflow de partage
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
feature: Workflows, Targeting Activity
exl-id: 4204350a-c2d2-4033-9bdf-87b49d8211b9
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '2151'
ht-degree: 80%

---

# Partage{#split}



Une activité de type **Partage** permet de partitionner une cible en plusieurs sous-ensembles. La cible est construite avec tous les résultats reçus : toutes les activités antérieures doivent donc être terminées pour que cette activité soit exécutée.

Cette activité ne déclenche pas d&#39;union des populations entrantes. Si plusieurs transitions arrivent sur une activité de partage, il est recommandé d&#39;insérer une **[!UICONTROL Union]** activité devant.

Pour obtenir un exemple de l&#39;activité de Partage utilisée, voir la section [Création de sous-ensembles à l&#39;aide de l&#39;activité Partage](targeting-data.md#creating-subsets-using-the-split-activity).

Un exemple d&#39;utilisation de l&#39;activité de Partage pour segmenter la cible en différentes populations à l&#39;aide des conditions de filtrage est présenté dans [cette section](cross-channel-delivery-workflow.md).

Un exemple d&#39;utilisation d&#39;une variable d&#39;instance dans une activité de Partage est présenté dans [cette section](javascript-scripts-and-templates.md).

Pour paramétrer cette activité, vous devez définir le contenu et le libellé des sous-ensembles souhaités dans l&#39;onglet **[!UICONTROL Sous-ensembles]**, puis choisir la dimension de ciblage dans l&#39;onglet **[!UICONTROL Général]**.

## Créer des sous-ensembles {#creating-subsets}

Pour créer un sous-ensemble :

1. Saisissez un libellé dans le champ correspondant et sélectionnez le mode de filtrage à appliquer.
1. Pour filtrer la population entrante, sélectionnez l&#39;option **[!UICONTROL Ajouter une condition de filtrage]** et cliquez sur le lien **[!UICONTROL Editer...]**.

   Sélectionnez le type de filtre à appliquer aux données pour qu&#39;elles soient incluses dans cet ensemble.

   Le mode de fonctionnement est le même que pour une activité de type **Requête**.

   >[!NOTE]
   >
   >Vous pouvez filtrer les données contenues dans deux bases externes (FDA) maximum.

1. Vous pouvez spécifier le nombre maximum d&#39;enregistrements à extraire de la cible pour créer le sous-ensemble. Pour ce faire, cochez la case **[!UICONTROL Limiter les enregistrements sélectionnés]** et cliquez sur l’option **[!UICONTROL Modifier...]** lien.

   Un assistant vous permet de choisir le mode de sélection des enregistrements de ce sous-ensemble. La procédure est décrite dans la section [Limiter le nombre d&#39;enregistrements des sous-ensembles](#limiting-the-number-of-subset-records).

   ![](assets/s_user_segmentation_partage4.png)

1. Si vous le souhaitez, **ajoutez d&#39;autres sous-ensembles** en utilisant le bouton **[!UICONTROL Ajouter]**.

   ![](assets/s_user_segmentation_partage_add.png)

   >[!NOTE]
   >
   >Si l&#39;option **[!UICONTROL Permettre le recouvrement des populations de sortie]** n&#39;est pas cochée, les sous-ensembles sont créés dans l&#39;ordre des onglets. Utilisez les flèches situées dans la section supérieure droite de cette fenêtre pour les déplacer. Ainsi, si le premier sous-ensemble récupère 70% de la population initiale, le sous-ensemble suivant n&#39;appliquera ses critères de sélection qu&#39;aux 30% restants, etc.

   Pour chaque sous-ensemble créé, une transition sortante sera ajoutée à l&#39;activité de partage.

   ![](assets/s_user_segmentation_partage_add2.png)

   Vous pouvez choisir de ne générer qu&#39;une seule transition sortante (et identifier les ensembles par exemple au travers du code segment) : pour cela, sélectionnez l&#39;option **[!UICONTROL Générer tous les sous-ensembles dans la même table]** dans l&#39;onglet **[!UICONTROL Général]**.

   S&#39;il est renseigné, le code segment de chaque sous-ensemble est automatiquement stocké dans une colonne additionnelle. Cette colonne sera accessible parmi les champs de personnalisation, au niveau des diffusions.

## Limiter le nombre d&#39;enregistrements des sous-ensembles {#limiting-the-number-of-subset-records}

Si vous ne souhaitez pas utiliser l&#39;ensemble de la population d&#39;un sous-ensemble, vous avez la possibilité d&#39;en limiter le nombre d&#39;enregistrements.

1. Dans la fenêtre d&#39;édition du sous-ensemble, cochez l&#39;option **[!UICONTROL Limiter les enregistrements sélectionnés]** et cliquez sur le lien **[!UICONTROL Editer...]**.
1. Sélectionnez le type de limitation de votre choix :

   * **[!UICONTROL Activer le tirage aléatoire]** : cette option applique un tirage aléatoire aux enregistrements. Le tirage aléatoire appliqué dépend du moteur de base de données.
   * **[!UICONTROL Conserver les premiers suite à un tri]**: cette option permet de définir une limitation en fonction d&#39;un ou plusieurs ordres de tri. Si vous sélectionnez l’option **[!UICONTROL Age]** champ comme critère de tri et 100 comme limite, seuls les 100 destinataires les plus jeunes seront conservés.
   * **[!UICONTROL Conserver les premiers suite à un tri (critères, aléatoire)]** : cette option regroupe les deux options précédentes. Elle permet de définir une limitation suivant un ou plusieurs ordres de tri puis d&#39;appliquer une sélection aléatoire sur les premiers enregistrements dans le cas où certains enregistrements ont des valeurs égales pour les critères choisis.

     Par exemple, si vous choisissez le champ **[!UICONTROL Age]** comme critère de tri, et que vous définissez ensuite une limite de 100, mais que les 2000 destinataires les plus jeunes en base ont tous 18 ans, alors 100 destinataires seront sélectionnés aléatoirement parmi ces 2000.

   ![](assets/s_user_segmentation_partage_wz1.png)

1. Si vous choisissez de définir des critères de tri, une étape supplémentaire vous permet de définir les colonnes et l&#39;ordre de tri.

   ![](assets/s_user_segmentation_partage_wz1.1.png)

1. Choisissez ensuite la méthode de limitation des données.

   ![](assets/s_user_segmentation_partage_wz2.png)

   Vous avez le choix entre les différentes méthodes suivantes :

   * **[!UICONTROL Taille (en %)]** : un pourcentage d&#39;enregistrements. Par exemple, le paramétrage ci-dessus extraira 10% de la population totale.

     Le pourcentage porte sur la population initiale, non sur le résultat de l&#39;activité.

   * **[!UICONTROL Taille (en % du segment)]** : un pourcentage d&#39;enregistrements portant uniquement sur le sous-ensemble et non sur la population initiale.
   * **[!UICONTROL Taille maximale]** : un nombre maximum d&#39;enregistrements.
   * **[!UICONTROL Par groupement de données]** : vous pouvez effectuer une limitation du nombre d&#39;enregistrements en fonction des valeurs d&#39;un champ précis de la population entrante. Voir à ce sujet la section [Limiter le nombre d’enregistrements des sous-ensembles par répartition de données](#limiting-the-number-of-subset-records-by-data-grouping).
   * **[!UICONTROL Par groupement de données (%)]** : vous pouvez effectuer une limitation du nombre d&#39;enregistrements en fonction des valeurs d&#39;un champ précis de la population entrante, sous la forme d&#39;un pourcentage. Voir à ce sujet la section [Limiter le nombre d’enregistrements des sous-ensembles par répartition de données](#limiting-the-number-of-subset-records-by-data-grouping).
   * **[!UICONTROL Par répartition de données]** : si vos champs de groupement comportent un trop grand nombre de valeurs ou que vous souhaitez éviter de ressaisir les valeurs à chaque nouvelle activité de partage, Adobe Campaign vous offre la possibilité d&#39;effectuer une limitation **[!UICONTROL Par répartition de données]** (module optionnel Distributed Marketing). Voir à ce sujet la section [Limiter le nombre d&#39;enregistrements des sous-ensembles par répartition de données](#limiting-the-number-of-subset-records-per-data-distribution).

1. Cliquez sur **[!UICONTROL Terminer]** pour valider les critères de sélection des enregistrements. Le paramétrage défini est alors affiché dans la fenêtre centrale de l&#39;éditeur.

## Limiter le nombre d&#39;enregistrements des sous-ensembles par groupement de données {#limiting-the-number-of-subset-records-by-data-grouping}

Vous pouvez effectuer une limitation du nombre d&#39;enregistrements par groupement de données. Cette limitation peut être effectuée à l&#39;aide d&#39;une valeur fixe ou d&#39;un pourcentage.

Par exemple, si vous choisissez le champ **[!UICONTROL Langue]** comme champ de groupement, vous pourrez définir une limite d&#39;enregistrements pour chaque langue.

1. Lors de la sélection des valeurs de limitation de données, sélectionnez **[!UICONTROL Par groupement de données]** ou **[!UICONTROL Par groupement de données (en %)]** et cliquez sur **[!UICONTROL Suivant]**.

   ![](assets/s_user_segmentation_partage_wz3.png)

1. Sélectionnez ensuite le ou les champs de groupement (par exemple, le champ **[!UICONTROL Langue]**) et cliquez sur le bouton **[!UICONTROL Suivant]**.

   ![](assets/s_user_segmentation_partage_wz4.png)

1. Indiquez enfin les seuils de groupement des données (avec les valeurs fixes ou les pourcentages selon la méthode de groupement sélectionnée précédemment). Pour définir le même seuil pour chaque valeur, par exemple si vous souhaitez définir le nombre d&#39;enregistrements pour chaque langue sur 10, sélectionnez l&#39;option **[!UICONTROL La taille de tous les groupes de données est identique.]** . Pour définir une limite différente pour chaque valeur, sélectionnez la variable **[!UICONTROL Limites par valeur de regroupement]** . Vous pourrez ainsi choisir une autre limitation pour l&#39;anglais, le français, etc.

   ![](assets/s_user_segmentation_partage_wz5.png)

1. Cliquez sur **[!UICONTROL Terminer]** pour valider la limitation et revenir à l&#39;édition de l&#39;activité de partage.

## Limiter le nombre d&#39;enregistrements des sous-ensembles par répartition de données {#limiting-the-number-of-subset-records-per-data-distribution}

Si vos champs de groupement contiennent un trop grand nombre de valeurs ou si vous souhaitez éviter de réinitialiser les valeurs pour chaque nouvelle activité de partage, Adobe Campaign vous permet de créer une limite par répartition de données. Lors de la sélection des valeurs de limitation des données (voir à ce sujet la section [Créer des sous-ensembles](#creating-subsets)), sélectionnez l’option **[!UICONTROL Par répartition de données]** et sélectionnez un modèle dans le menu déroulant. La création d&#39;un modèle de répartition de données est illustrée ci-dessous.

Un exemple de l&#39;activité **[!UICONTROL Validation en local]** avec un modèle de répartition est présenté dans la section [Utiliser l&#39;activité Validation en local](using-the-local-approval-activity.md).

![](assets/s_user_segmentation_partage_wz6.png)

>[!IMPORTANT]
>
>Pour utiliser cette fonction, vous devez acquérir le module Distributed Marketing, qui est une option de Campaign. Vérifiez votre contrat de licence.

Le modèle de répartition de données permet de limiter le nombre d&#39;enregistrements à partir d&#39;une liste de valeurs de groupement. Les étapes de création d&#39;un modèle de répartition de données sont les suivantes :

1. Pour créer le modèle de répartition de données, positionnez-vous sur le noeud **[!UICONTROL Ressources > Gestion de campagne > Répartition de données]**, et cliquez sur le bouton **[!UICONTROL Nouveau]**.

   ![](assets/local_validation_data_distribution_1.png)

1. L&#39;onglet **[!UICONTROL Général]** permet de renseigner le libellé ainsi que le contexte d&#39;exécution de la répartition (dimension de ciblage, champ de répartition).

   ![](assets/local_validation_data_distribution_2.png)

   Les champs à renseigner sont les suivants :

   * **[!UICONTROL Libellé]** : libellé du modèle de répartition.
   * **[!UICONTROL Dimension de ciblage]** : renseignez le schéma de ciblage sur lequel la répartition de données sera appliquée, par exemple **[!UICONTROL Destinataire]**. Ce schéma doit toujours être compatible avec les données utilisées dans le workflow de ciblage.
   * **[!UICONTROL Champ de répartition]**: sélectionnez un champ depuis la dimension de ciblage. Par exemple, si vous sélectionnez l’option **[!UICONTROL Domaine de l&#39;email]** , la liste des destinataires sera répartie par domaine.
   * **[!UICONTROL Type de répartition]** : sélectionnez la manière dont sera exprimée la valeur de limitation de la cible dans l&#39;onglet **[!UICONTROL Distribution]** : **[!UICONTROL Pourcentage]** ou **[!UICONTROL Fixe]**.
   * **[!UICONTROL Type d&#39;affectation]**: sélectionnez le type d’affectation de répartition de données. Vous pouvez choisir entre une affectation par groupe ou opérateur ou une affectation par entité locale. L’affectation par entité locale est utilisée dans **Marketing distribué**. Pour plus d&#39;informations, consultez cette [section](../../distributed/using/about-distributed-marketing.md).
   * **[!UICONTROL Stockage des validations]** : si vous utilisez une activité **[!UICONTROL Validation en local]** dans votre workflow de ciblage (voir la section [Validation en local](local-approval.md)), indiquez le schéma dans lequel seront stockés les résultats de validation. Vous devez spécifier un schéma de stockage pour chaque schéma de ciblage. Si vous utilisez le schéma de ciblage **[!UICONTROL Destinataires]**, saisissez le schéma de stockage par défaut **[!UICONTROL Validation en local d&#39;un destinataire]**.

     Il n&#39;est pas nécessaire de renseigner le champ **[!UICONTROL Stockage des validations]** dans le cas d&#39;une simple limitation par groupement de données, sans validation en local.

1. Si vous utilisez une activité **[!UICONTROL Validation en local]** (voir la section [Validation en local](local-approval.md)), renseignez ensuite les **[!UICONTROL Paramètres avancés]** du modèle de répartition :

   ![](assets/local_validation_data_distribution_3.png)

   Les champs à renseigner sont les suivants :

   * **[!UICONTROL Valider les messages ciblés]** : cochez cette option si vous souhaitez que tous les destinataires soient pré-sélectionnés dans la liste de destinataires à valider. Si cette option est décochée, aucun destinataire ne sera pré-sélectionné.

     >[!NOTE]
     >
     >Cette option est cochée par défaut.

     ![](assets/local_validation_notification.png)

   * **[!UICONTROL Libellé de la diffusion]** : permet de définir une expression pour afficher le libellé de la diffusion dans la notification de retour. L&#39;expression par défaut renseigne le libellé standard de la diffusion (compute string). Vous avez la possibilité de modifier cette expression.

     ![](assets/local_validation_notification_3.png)

   * **[!UICONTROL Champ de groupement]** : ce champ permet de définir le groupement utilisé pour l&#39;affichage des destinataires dans les notifications de validation et de retour.

     ![](assets/local_validation_notification_4.png)

   * **[!UICONTROL Interface Web]**: permet de lier une application web à la liste des destinataires. Dans la notification de validation et de retour, chaque destinataire sera cliquable et sera associé à l&#39;application web sélectionnée. La variable **[!UICONTROL Paramètres]** champ (par exemple, **[!UICONTROL recipientId]**) permet de paramétrer le paramètre supplémentaire à utiliser dans l&#39;URL et l&#39;application web.

     ![](assets/local_validation_notification_5.png)

1. L&#39;onglet **[!UICONTROL Répartition]** permet de définir la liste des valeurs de répartition.

   ![](assets/local_validation_data_distribution_4.png)

   * **[!UICONTROL Valeur]** : saisissez les valeurs de répartition.
   * **[!UICONTROL Pourcentage/Fixe]** : renseignez la limite d&#39;enregistrements (fixe ou en pourcentage) associée à chaque valeur.

     Cette colonne est définie par le champ **[!UICONTROL Type de répartition]** de l&#39;onglet **[!UICONTROL Général]**.

   * **[!UICONTROL Libellé]** : saisissez le libellé associé à chaque valeur.
   * **[!UICONTROL Groupe ou opérateur]** : si vous utilisez une activité **[!UICONTROL Validation en local]** (voir la section [Validation en local](local-approval.md)), sélectionnez l&#39;opérateur ou le groupe d&#39;opérateurs affecté à chaque valeur de répartition.

     Il n&#39;est pas nécessaire de renseigner le champ **[!UICONTROL Groupe ou opérateur]** dans le cas d&#39;une simple limitation par groupement de données, sans validation en local.

     >[!IMPORTANT]
     >
     >Vérifiez que les opérateurs disposent des droits adéquats.

   * **[!UICONTROL Entité locale]**: sélectionnez l&#39;entité locale affectée à chaque valeur de répartition. Les entités locales sont utilisées dans **Marketing distribué**. Pour plus d&#39;informations, consultez cette [section](../../distributed/using/about-distributed-marketing.md).

## Paramètres de filtrage {#filtering-parameters}

Cliquez sur l&#39;onglet **[!UICONTROL Général]** pour saisir le libellé de l&#39;activité. Sélectionnez les dimensions de ciblage et de filtrage de ce partage. Au besoin, vous pouvez modifier ces dimensions pour tel ou tel sous-ensemble.

![](assets/s_user_segmentation_partage_general.png)

Cochez l&#39;option **[!UICONTROL Générer le complémentaire]** si vous souhaitez exploiter la population restante. Le complémentaire est la cible entrante, moins l&#39;union des sous-ensembles. Une transition sortante supplémentaire sera alors ajoutée à l&#39;activité, comme suit :

![](assets/s_user_segmentation_partage_compl.png)

Pour que cette option fonctionne correctement, les données en entrée doivent posséder une clé primaire.

Par exemple si les données sont lues directement depuis une base de données externe telle que Netezza (qui ne supporte pas la notion d&#39;index) via une activité de **[!UICONTROL Chargement (SGBD)]**, le complémentaire généré par l&#39;activité de **[!UICONTROL Partage]** sera incorrect.

Pour éviter cela, vous pouvez faire glisser et déposer un **[!UICONTROL Enrichissement]** activité juste avant la **[!UICONTROL Partage]** activité. Dans le **[!UICONTROL Enrichissement]** , vérifiez les **[!UICONTROL Conserver toutes les données additionnelles de l’ensemble principal]** et spécifier dans les données additionnelles les colonnes que vous souhaitez utiliser pour configurer les filtres du **[!UICONTROL Partage]** activité. Les données de la transition entrante de la **[!UICONTROL Partage]** Les activités sont ensuite stockées localement dans une table temporaire sur le serveur Adobe Campaign et le complémentaire peut être généré correctement.

L&#39;option **[!UICONTROL Permettre le recouvrement des populations de sortie]** permet de gérer les populations appartenant à plusieurs sous-ensembles :

* Lorsque la case est décochée, l&#39;activité de partage assure qu&#39;un destinataire ne sera pas présent dans plusieurs transitions en sortie, même s&#39;il vérifie les critères de plusieurs sous-ensembles. Il sera dans la cible du premier onglet dont les critères sont vérifiés.
* Lorsque la case est cochée, les destinataires peuvent être présents dans plusieurs sous-ensembles s&#39;ils vérifient leurs critères de filtrage. Adobe Campaign vous recommande d&#39;utiliser des critères exclusifs.

## Paramètres d&#39;entrée {#input-parameters}

* tableName
* schema

Chacun des événements entrants doit spécifier une cible définie par ces paramètres.

## Paramètres de sortie {#output-parameters}

* tableName
* schema
* recCount

Ce triplet de valeurs identifie la cible résultant de l’exclusion. **[!UICONTROL tableName]** est le nom de la table qui mémorise les identifiants de la cible, **[!UICONTROL schema]** est le schéma de la population (habituellement nms:recipient) et **[!UICONTROL recCount]** est le nombre d’éléments dans la table.

La transition associée au complémentaire possède les mêmes paramètres.
