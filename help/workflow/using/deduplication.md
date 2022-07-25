---
product: campaign
title: Déduplication
description: En savoir plus sur l’activité de workflow de déduplication
feature: Workflows, Targeting Activity
exl-id: 38add4fe-6238-45de-863e-895ebca189b7
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: ht
source-wordcount: '1146'
ht-degree: 100%

---

# Déduplication{#deduplication}

![](../../assets/v7-only.svg)

La déduplication supprime les doublons dans le ou les résultats des activités entrantes. La déduplication peut être effectuée en fonction de l&#39;adresse email, du numéro de téléphone ou d&#39;un autre champ.

L&#39;activité **[!UICONTROL Déduplication]** est utilisée pour supprimer des lignes dupliquées d&#39;un jeu de données. Par exemple, les enregistrements ci-dessous peuvent être considérés comme des duplicatas, car ils ont la même adresse email et le même téléphone portable et/ou de domicile.

| Date de la dernière modification | Prénom | Nom | Email | Téléphone mobile | Phone |
-----|------------|-----------|-------|--------------|------
| 02/03/2020 | Bob | Tisner | bob@mycompany.com | 444-444-4444 | 888-888-8888 |
| 05/19/2020 | Robert | Tisner | bob@mycompany.com | 444-444-4444 | 777-777-7777 |
| 07/22/2020 | Bobby | Tisner | bob@mycompany.com | 444-444-4444 | 777-777-7777 |

L&#39;activité **[!UICONTROL Déduplication]** peut conserver une ligne entière comme enregistrement unique après l&#39;identification des duplicatas. Par exemple, dans le cas pratique ci-dessus, si l’activité est configurée pour ne conserver que l’enregistrement avec la **[!UICONTROL Date]** la plus ancienne, le résultat est le suivant :

| Date | Prénom | Nom | Email | Téléphone mobile | Phone |
-----|----------|------------|-------|--------------|------
| 02/03/2020 | Bob | Tisner | bob@mycompany.com | 444-444-4444 | 888-888-8888 |

L’enregistrement principal sélectionné transfère les données sans fusionner les données de champ avec d’autres données pertinentes dans les lignes de duplicatas.

Complémentaire :

| Date | Prénom | Nom | Email | Téléphone mobile | Phone |
-----|------------|-----------|-------|--------------|------
| 05/19/2020 | Robert | Tisner | bob@mycompany.com | 444-444-4444 | 777-777-7777 |
| 07/22/2020 | Bobby | Tisner | bob@mycompany.com | 444-444-4444 | 777-777-7777 |

## Bonnes pratiques {#best-practices}

Lors d&#39;une déduplication, les flux entrants sont traités séparément. Si par exemple, un destinataire &#39;A&#39; est présent dans le résultat de la requête 1 et également dans le résultat de la requête 2, il ne sera pas dédupliqué.

Ce cas de figure doit s&#39;aborder de cette manière :

* Créer une activité **Union** pour unifier chaque flux entrant.
* Créer une activité **Déduplication** positionnée après l&#39;activité **Union**.

![](assets/dedup_bonnepratique.png)

## Configuration  {#configuration}

Pour paramétrer une déduplication, vous devez renseigner son libellé, la méthode et les critères de déduplication et les options relatives au résultat.

1. Cliquez sur le lien **[!UICONTROL Editer la configuration...]** pour définir le mode de déduplication.

   ![](assets/s_user_segmentation_dedup_param.png)

1. Sélectionnez le type de cible pour cette activité (par défaut, la déduplication est liée aux destinataires) et le critère à utiliser, c&#39;est-à-dire le champ pour lequel des valeurs identiques permettent d&#39;identifier les duplicatas.

   >[!NOTE]
   >
   >Si vous utilisez des données externes comme entrée, provenant par exemple d’un fichier externe, veillez à sélectionner l’option **[!UICONTROL Schéma temporaire]**.
   >
   >L&#39;option **[!UICONTROL Autre]** permet, à l&#39;étape suivante, de sélectionner le ou les critères à utiliser :

   ![](assets/s_user_segmentation_dedup_param2.png)

1. L&#39;option **[!UICONTROL Autre]** permet, à l&#39;étape suivante, de sélectionner le ou les critères à utiliser en cas de valeurs identiques :

   ![](assets/s_user_segmentation_dedup_param3.png)

1. Sélectionnez dans la liste déroulante la méthode de déduplication à utiliser et indiquez le nombre de doublons à conserver.

   ![](assets/s_user_segmentation_dedup_param4.png)

   Les méthodes disponibles sont les suivantes :

   * **[!UICONTROL Choisir pour moi]** : sélectionne au hasard parmi les doublons l&#39;enregistrement à conserver.
   * **[!UICONTROL Par ordonnancement de valeurs]** : permet de définir un ordre de priorité des valeurs pour un ou plusieurs champs. Pour définir les valeurs, sélectionnez un champ ou créez une expression puis ajoutez la ou les valeurs dans le tableau correspondant. Cliquez sur le bouton **[!UICONTROL Ajouter]** situé au-dessus de la liste des valeurs pour définir un nouveau champ.

      ![](assets/s_user_segmentation_dedup_param5.png)

   * **[!UICONTROL Valeur non vide]** : permet de conserver en priorité les enregistrements pour lesquels la valeur de l&#39;expression sélectionnée n&#39;est pas vide.

      ![](assets/s_user_segmentation_dedup_param6.png)

   * **[!UICONTROL A partir d&#39;une expression]** : permet de conserver les enregistrements dont la valeur de l&#39;expression renseignée est la plus petite (ou la plus grande).

      ![](assets/s_user_segmentation_dedup_param7.png)
   >[!NOTE]
   >
   >La fonctionnalité **[!UICONTROL Fusion]**, accessible via le lien **[!UICONTROL Paramètres avancés]**, vous permet de configurer un ensemble de règles afin de fusionner un champ ou un groupe de champs en un seul enregistrement de données obtenu. Pour plus d’informations à ce sujet, voir [Fusion de champs en un seul enregistrement](#merging-fields-into-single-record).

1. Cliquez sur **[!UICONTROL Terminer]** pour valider la méthode de déduplication sélectionnée.

   La section centrale de la fenêtre résume le paramétrage défini.

   Dans la section inférieure de la fenêtre d&#39;édition de l&#39;activité, vous pouvez modifier le libellé de la transition sortante de l&#39;objet graphique et saisir un code segment qui sera associé au résultat de l&#39;activité. Ce code pourra être utilisé ultérieurement comme critère de ciblage.

   ![](assets/s_user_segmentation_dedup_param8.png)

1. Cochez l&#39;option **[!UICONTROL Générer le complémentaire]** si vous souhaitez exploiter la population restante. Le complémentaire est constitué de tous les doublons. Une transition supplémentaire sera alors ajoutée à l&#39;activité, comme suit :

   ![](assets/s_user_segmentation_dedup_param9.png)

## Exemple : identifier des doublons avant une diffusion {#example--identify-the-duplicates-before-a-delivery}

Dans l&#39;exemple suivant, la déduplication porte sur l&#39;union de trois requêtes.

Le workflow a pour but de définir la cible d&#39;une diffusion en excluant les doublons afin d&#39;éviter d&#39;envoyer cette dernière plusieurs fois à un même destinataire.

Les doublons identifiés seront également intégrés à une liste constituée exclusivement de doublons qui pourra être réutilisée en cas de besoin ultérieur.

![](assets/deduplication_example.png)

1. Placez et reliez les différentes activités nécessaires au déroulement du workflow comme indiqué dans l&#39;illustration ci-dessus.

   L&#39;activité d&#39;union est ici utilisée pour « unifier » les trois requêtes en une seule transition. Ainsi, la déduplication ne s&#39;opérera pas individuellement sur chaque requête mais sur l&#39;ensemble. Pour plus d’informations, consultez la section [Meilleures pratiques](#best-practices).

1. Ouvrez l&#39;activité de déduplication puis cliquez sur le lien **[!UICONTROL Editer la configuration...]** afin de pouvoir définir le mode de déduplication.
1. Dans la fenêtre qui s&#39;ouvre, sélectionnez **[!UICONTROL Schéma de la base]**.
1. Sélectionnez **Destinataires** en tant que dimensions de ciblage et de filtrage.
1. Sélectionnez le champ d&#39;identification des doublons **[!UICONTROL Email]** afin de n&#39;envoyer la diffusion qu&#39;une seule fois par adresse mail, puis cliquez sur **[!UICONTROL Suivant]**.

   Si vous souhaitez baser l&#39;identification des doublons sur un champ précis, sélectionnez **[!UICONTROL Autre]** afin d&#39;accéder à la liste des champs disponibles.

1. Choisissez de ne conserver qu&#39;une seule entrée lorsque la même adresse e-mail est identifiée pour plusieurs destinataires.
1. Sélectionnez le mode de déduplication **[!UICONTROL Choisir pour moi]** afin que l&#39;enregistrement conservé en cas de doublons identifiés soit choisi au hasard, puis cliquez sur **[!UICONTROL Terminer]**.

Lors de l&#39;exécution du workflow, les destinataires identifiés comme étant des doublons seront exclus du résultat (et donc de la diffusion) et ajoutés à la liste des doublons. Cette liste pourra être réutilisée afin de ne pas avoir à identifier de nouveau les doublons.

## Fusion de champs en un seul enregistrement de données {#merging-fields-into-single-record}

La fonctionnalité **[!UICONTROL Fusion]** permet de configurer un ensemble de règles pour que la déduplication définisse un champ ou un groupe de champs à fusionner dans un seul enregistrement de données obtenu.

Par exemple, avec un ensemble d’enregistrements dupliqués, vous pouvez choisir de conserver le numéro de téléphone le plus ancien ou le nom le plus récent.

Un cas pratique exploitant cette fonctionnalité est disponible dans [cette section](deduplication-merge.md).

Pour ce faire, procédez comme suit :

1. Dans l’étape de sélection de la **[!UICONTROL méthode de déduplication]**, cliquez sur le lien **[!UICONTROL Paramètres avancés]**.

   ![](assets/dedup1.png)

1. Sélectionnez l&#39;option **[!UICONTROL Fusionner les enregistrements]** pour activer la fonctionnalité.

   Si vous souhaitez regrouper plusieurs champs de données dans chaque condition de fusion, activez l&#39;option **[!UICONTROL Utiliser plusieurs critères de fusion des enregistrements]**.

   ![](assets/dedup2.png)

1. Après avoir activé la fonctionnalité, un onglet **[!UICONTROL Fusion]** est ajouté à l&#39;activité **[!UICONTROL Déduplication]**. Il vous permet de définir des groupes de champs à fusionner et leurs règles associées.

   Pour plus d&#39;informations à ce sujet, reportez-vous au cas pratique disponible dans [cette section](deduplication-merge.md).

   ![](assets/dedup3.png)

## Paramètres d&#39;entrée {#input-parameters}

* tableName
* schema

Chacun des événements entrants doit spécifier une cible définie par ces paramètres.

## Paramètres de sortie {#output-parameters}

* tableName
* schema
* recCount

Ce triplet de valeurs identifie la cible résultant de la déduplication. **[!UICONTROL tableName]** est le nom de la table qui mémorise les identifiants de la cible, **[!UICONTROL schema]** est le schéma de la population (habituellement nms:recipient) et **[!UICONTROL recCount]** est le nombre d&#39;éléments dans la table.

La transition associée au complémentaire possède les mêmes paramètres.
