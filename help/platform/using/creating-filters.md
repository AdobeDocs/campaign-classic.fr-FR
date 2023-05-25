---
product: campaign
title: Création de filtres
description: Création de filtres
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: platform
content-type: reference
topic-tags: filtering-data
exl-id: 58e54f67-dc87-42f1-8426-6f801e8e4fb6
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: ht
source-wordcount: '2087'
ht-degree: 100%

---

# Création de filtres{#creating-filters}



Lorsque vous naviguez dans l’arborescence d’Adobe Campaign (à partir du menu **[!UICONTROL Explorateur]** de la page d’accueil), les informations contenues dans la base de données sont affichées sous forme de listes. Ces listes sont paramétrables afin de filtrer les données et de n’afficher que les éléments utiles à l’opérateur. Des actions peuvent ensuite être lancées sur les données issues du résultat du filtre. Le paramétrage des filtres permet de sélectionner les données d’une liste de façon **[!UICONTROL dynamique]**. En cas de modification des données, les données filtrées sont mises à jour.

>[!NOTE]
>
>Les paramètres de configuration de l’interface utilisateur sont définis localement pour le périphérique. Il peut parfois être nécessaire de nettoyer ces données, en particulier si des problèmes surviennent lors de leur actualisation. Pour ce faire, utilisez le menu **[!UICONTROL Fichier > Vider le cache local]**.

## Typologie des filtres disponibles {#typology-of-available-filters}

Adobe Campaign permet d&#39;appliquer des filtres sur les listes de données.

Ces filtres peuvent être utilisés ponctuellement ou enregistrés pour être réutilisés. Vous pouvez appliquer plusieurs filtres simultanément.

Les types de filtres disponibles dans Adobe Campaign sont les suivants :

* **Filtres par défaut**

   Le **filtre par défaut** est accessible depuis les champs situés au-dessus des listes. Il permet de filtrer sur des champs prédéfinis (par défaut, pour les profils de destinataires, le nom et l&#39;email). Les champs permettent de saisir les caractères sur lesquels porte le filtre ou de sélectionner les conditions de filtrage dans une liste déroulante.

   ![](assets/filters_recipient_default_filter.png)
<!--
  >[!NOTE]
  >
  >The **%** character replaces any character string. For example, the string `%@yahoo.com` lets you display all the profiles with an email address in the domain "yahoo.com".
-->
Vous pouvez modifier le filtre par défaut d’une liste. Pour plus d’informations, voir la section [Modifier le filtre par défaut](#altering-the-default-filter).

* **Filtres simples**

   Les **filtres simples** sont des filtres ponctuels sur les colonnes. Ils sont définis avec un ou plusieurs critères de recherche simple sur les colonnes affichées.

   Vous pouvez conjuguer plusieurs filtres simples sur une même liste de données pour affiner votre recherche. Les champs de filtrage s&#39;affichent les uns en-dessous des autres. Ils peuvent être supprimés indépendamment les uns des autres.

   ![](assets/filters_recipient_simple_filter.png)

   Les filtres simples sont détaillés dans la section [Créer un filtre simple](#creating-a-simple-filter).

* **Filtres avancés**

   Les **filtres avancés** sont créés à partir d’une requête ou d’une combinaison de requêtes sur les données.

   Pour plus d’informations sur la création d’un filtre avancé, voir la section [Créer un filtre avancé](#creating-an-advanced-filter).

   Vous pouvez utiliser des fonctions pour définir le contenu du filtre. Pour plus d’informations à ce sujet, consultez la section [Créer un filtre avancé avec fonctions](#creating-an-advanced-filter-with-functions).

   >[!NOTE]
   >
   >Pour plus d’informations sur la construction des requêtes dans Adobe Campaign, reportez-vous à [cette section](../../platform/using/about-queries-in-campaign.md).

* **Filtres utilisateurs**

   Un **filtre applicatif** est un filtre avancé qui a été enregistré afin d&#39;en conserver le paramétrage et le partager avec les autres opérateurs.

   Le bouton **[!UICONTROL Filtres]**, situé au-dessus des listes, propose un ensemble de filtres d’application pouvant être combinés pour affiner le filtrage. La méthode de création de ces filtres est présentée dans la section [Enregistrer un filtre](#saving-a-filter).

## Modifier le filtre par défaut {#altering-the-default-filter}

Pour modifier le filtre par défaut pour une liste de destinataires, cliquez sur le noeud **[!UICONTROL Profils et Cibles > Filtres prédéfinis]** de l&#39;arborescence.

Pour tout autre type de données, configurez le filtre par défaut à partir du noeud **[!UICONTROL Administration > Paramétrage > Filtres prédéfinis]**.

Les étapes sont les suivantes :

1. Dans la liste des filtres, sélectionnez le filtre que vous souhaitez voir proposé par défaut.
1. Cliquez sur l&#39;onglet **[!UICONTROL Paramètres]** et cochez l&#39;option **[!UICONTROL Filtre par défaut pour le type de document associé]**.

   ![](assets/s_ncs_user_default_filter.png)

   >[!CAUTION]
   >
   >Si un filtre est déjà appliqué par défaut à la liste visée, vous devez d&#39;abord le désactiver avant d&#39;appliquer un nouveau filtre. Pour cela, cliquez sur la croix rouge située à droite des champs de filtrage.

1. Cliquez sur le bouton **[!UICONTROL Enregistrer]** pour appliquer ce filtre.

   >[!NOTE]
   >
   >La fenêtre de définition des filtres est présentée dans les sections [Créer un filtre avancé](#creating-an-advanced-filter) et [Enregistrer un filtre](#saving-a-filter).

## Créer un filtre simple {#creating-a-simple-filter}

Pour créer un **filtre simple**, respectez les étapes suivantes :

1. Cliquez avec le bouton droit sur le champ sur lequel vous souhaitez filtrer les données et choisissez **[!UICONTROL Filtrer sur ce champ]**.

   ![](assets/s_ncs_user_sort_this_field.png)

   Les champs de filtrage par défaut s&#39;affichent au-dessus de la liste.

1. Sélectionnez dans la liste déroulante l&#39;option de filtrage ou saisissez les critères de filtrage à appliquer (le mode de sélection ou de saisie des critères dépend du type de champ : texte, énuméré, etc.).

   ![](assets/s_ncs_user_sort_fields.png)

1. Tapez sur la touche Entrée du clavier ou cliquez sur la flèche verte située à droite des champs de filtrage pour activer le filtre.

Si le champ sur lequel vous souhaitez filtrer les données n&#39;est pas affiché dans le formulaire du profil, vous pouvez l&#39;ajouter dans les colonnes affichées, puis filtrer sur cette colonne. Pour cela :

1. Cliquez sur l&#39;icône **[!UICONTROL Configurer la liste]**.

   ![](assets/s_ncs_user_configure_list.png)

1. Sélectionnez la colonne à afficher, par exemple l&#39;âge des destinataires.

   ![](assets/s_ncs_user_select_fields_to_display.png)

1. Puis cliquez avec le bouton droit dans la liste des destinataires, dans la colonne **Age**, et choisissez **[!UICONTROL Filtrer sur cette colonne]**.

   ![](assets/s_ncs_user_sort_this_column.png)

   Vous pouvez alors sélectionner les options de filtrage sur l&#39;âge.

   ![](assets/s_ncs_user_delete_filter.png)

## Créer un filtre avancé {#creating-an-advanced-filter}

Pour créer un **filtre avancé**, respectez les étapes suivantes :

1. Cliquez sur le bouton **[!UICONTROL Filtres]** et choisissez **[!UICONTROL Filtre avancé...]**.

   ![](assets/filters_recipient_create_adv_filter.png)

   Vous pouvez également cliquer avec le bouton droit dans la liste de données à filtrer et choisir **[!UICONTROL Filtre avancé...]**.

   La fenêtre de définition des conditions de filtrage s&#39;affiche à l&#39;écran.

1. Cliquez dans la colonne **[!UICONTROL Expression]** pour définir la valeur d&#39;entrée.
1. Cliquez sur l&#39;icône **[!UICONTROL Editer l&#39;expression]** pour sélectionner le champ sur lequel porte le filtre.

   ![](assets/s_user_filter_choose_field.png)

1. Sélectionnez dans la liste le champ sur lequel les données seront filtrées. Cliquez sur **[!UICONTROL Terminer]** pour valider.
1. Cliquez dans la colonne **[!UICONTROL Opérateur]** et sélectionnez dans la liste déroulante l&#39;opérateur à appliquer.
1. Sélectionnez une valeur attendue dans la colonne **[!UICONTROL Valeur]**. Vous pouvez combiner plusieurs filtres pour affiner votre requête. Pour ajouter un critère de filtrage, cliquez sur le bouton **[!UICONTROL Ajouter]**.

   ![](assets/s_ncs_user_filter_add_button_alone.png)

1. Vous pouvez hiérarchiser les expressions ou modifier l&#39;ordre des expressions de la requête en utilisant les flèches de la barre d&#39;outils.
1. L&#39;opérateur par défaut entre les expressions est le **Et**, mais vous pouvez le modifier en cliquant dans le champ. Vous pouvez choisir un opérateur **Ou**.

   ![](assets/s_ncs_user_filter_operator.png)

1. Cliquez sur **[!UICONTROL OK]** pour valider la création de ce filtre et l&#39;appliquer à la liste.

Le filtre appliqué est affiché au-dessus de la liste.

![](assets/s_ncs_user_filter_adv_edit.png)

Pour éditer ou modifier ce filtre, cliquez sur son libellé.

Pour annuler ce filtre, cliquez sur l&#39;icône **[!UICONTROL Supprimer ce filtre]** située à droite du filtre.

![](assets/s_ncs_user_filter_adv_remove.png)

Vous pouvez enregistrer un filtre avancé afin de le conserver pour une utilisation ultérieure. Pour plus d’informations sur ce type de filtre, voir la section [Enregistrer un filtre](#saving-a-filter).

### Créer un filtre avancé avec fonctions {#creating-an-advanced-filter-with-functions}

Les filtres avancés peuvent utiliser des fonctions : les **filtres avec fonctions** sont créés à partir d&#39;un éditeur d&#39;expressions qui permet de créer des formules qui utilisent les données de la base et des fonctions avancées. Pour créer un filtre avec fonctions, répétez les étapes 1, 2 et 3 de création d&#39;un filtre avancé puis procédez comme suit :

1. Dans la fenêtre de sélection du champ, cliquez sur le bouton **[!UICONTROL Sélection avancée]**.
1. Sélectionnez le type de formule à utiliser : agrégat, filtre utilisateur existant ou expression.

   ![](assets/s_ncs_user_filter_formula_select.png)

   Les options disponibles sont les suivantes :

   * **[!UICONTROL Champ simple]** pour sélectionner un champ. Il s&#39;agit du mode par défaut.
   * **[!UICONTROL Agrégat]** pour sélectionner la formule d&#39;agrégat à utiliser (comptage, somme, moyenne, maximum, minimum).
   * **[!UICONTROL Filtre utilisateur]** pour sélectionner l’un des filtres utilisateur existants. Les filtres utilisateur sont présentés dans la section [Enregistrer un filtre](#saving-a-filter).
   * **[!UICONTROL Expression]** pour accéder à l&#39;éditeur d&#39;expressions

      L&#39;éditeur d&#39;expression permet de définir un filtre avancé. Il se présente comme suit :

      ![](assets/s_ncs_user_create_exp_exple01.png)

      Il vous permet de sélectionner des champs dans les tables de base de données et de leur associer des fonctions avancées : sélectionnez la fonction à utiliser dans la **[!UICONTROL liste des fonctions]**. Les fonctions disponibles sont présentées dans la [liste des fonctions](../../platform/using/defining-filter-conditions.md#list-of-functions). Ensuite, sélectionnez les champs concernés par les fonctions et cliquez sur **[!UICONTROL OK]** pour valider l’expression.

      >[!NOTE]
      >
      >Un exemple de création de filtre à partir d’une expression est présenté dans [cette section](../../workflow/using/sending-a-birthday-email.md#identifying-recipients-whose-birthday-it-is).

## Enregistrer un filtre {#saving-a-filter}

Les filtres sont spécifiques à chaque opérateur et sont réinitialisés à chaque fois que l&#39;opérateur vide le cache de la console cliente.

Vous pouvez créer un **filtre applicatif** en enregistrant un filtre avancé : ainsi enregistré, le filtre pourra être réutilisé depuis le bouton droit de la souris dans n&#39;importe quelle liste ou à partir du bouton **[!UICONTROL Filtres]** situé au-dessus des listes.

Ces filtres sont également accessibles directement depuis l&#39;assistant de diffusion, dans l&#39;étape de sélection de la cible (consultez [cette section](../../delivery/using/creating-an-email-delivery.md) pour plus d&#39;informations sur la création de diffusions). Pour créer un filtre applicatif, vous pouvez :

* Transformer un filtre avancé en filtre applicatif : pour cela, vous devez cliquer sur **[!UICONTROL Enregistrer]** avant de fermer l&#39;éditeur de filtres avancés.

   ![](assets/s_ncs_user_filter_save.png)

* Créer ce filtre applicatif depuis le noeud **[!UICONTROL Administration > Paramétrage > Filtres prédéfinis]** (ou **[!UICONTROL Profils et Cibles > Filtres prédéfinis]** pour les destinataires). Pour cela, cliquez avec le bouton droit de la souris dans la liste des filtres et choisissez **[!UICONTROL Nouveau...]**. La procédure est la même que pour créer des filtres avancés.

   Le champ **[!UICONTROL Libellé]** vous permet de nommer ce filtre. Ce nom apparaîtra dans la liste déroulante du bouton **[!UICONTROL Filtres...]**.

   ![](assets/user_filter_apply.png)

Vous pouvez supprimer l&#39;ensemble des filtres sur la liste en cours à partir de l&#39;option **[!UICONTROL Pas de filtre]** accessible depuis le bouton droit de la souris ou l&#39;icône **[!UICONTROL Filtres]**, située au-dessus de la liste.

Vous pouvez combiner des filtres en utilisant le menu **[!UICONTROL Et...]** accessible à partir du bouton **[!UICONTROL Filtres]**.

![](assets/s_ncs_user_filter_combination.png)

## Filtrer les destinataires {#filtering-recipients}

Les filtres prédéfinis (voir la section [Enregistrer un filtre](#saving-a-filter)) vous permettent de filtrer les profils des destinataires contenus dans la base de données. Vous pouvez modifier des filtres à partir du nœud **[!UICONTROL Profils et Cibles > Filtres prédéfinis]** de l’arborescence. Les filtres sont répertoriés dans la section supérieure de l’espace de travail, via le bouton **[!UICONTROL Filtres]**.

Sélectionnez un filtre pour en afficher la définition et accéder à un aperçu des données filtrées.

![](assets/s_ncs_user_segment_edit.png)

>[!NOTE]
>
>Un exemple détaillé de création de filtre prédéfini est proposé dans la section [Cas pratique](../../platform/using/use-case.md).

Les filtres prédéfinis sont les suivants :

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Libellé</strong><br /> </td> 
   <td> <strong>Requête</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Ayant ouvert<br /> </td> 
   <td> Sélection des destinataires qui ont ouvert une diffusion.<br /> </td> 
  </tr> 
  <tr> 
   <td> Ayant ouvert mais pas cliqué<br /> </td> 
   <td> Sélection des destinataires qui ont ouvert une diffusion mais n'ont pas cliqué sur un lien.<br /> </td> 
  </tr> 
  <tr> 
   <td> Destinataires inactifs<br /> </td> 
   <td> Sélection des destinataires qui n'ont pas ouvert une diffusion depuis X mois.<br /> </td> 
  </tr> 
  <tr> 
   <td> Dernière activité par type d'appareil<br /> </td> 
   <td> Sélection des destinataires qui ont cliqué ou ouvert une diffusion Y depuis un appareil de type X dans les Z derniers jours.<br /> </td> 
  </tr> 
  <tr> 
   <td> Dernière activité par type d'appareil (Tracking)<br /> </td> 
   <td> Sélection des destinataires qui ont cliqué ou ouvert une diffusion Y depuis un appareil de type X dans les Z derniers jours.<br /> </td> 
  </tr> 
  <tr> 
   <td> Destinataires non ciblés<br /> </td> 
   <td> Sélection des destinataires qui n'ont jamais été ciblés sur un canal Y depuis X mois.<br /> </td> 
  </tr> 
  <tr> 
   <td> Destinataires très actifs<br /> </td> 
   <td> Sélection des destinataires qui ont cliqué dans une diffusion au moins X fois dans les Y derniers mois.<br /> </td> 
  </tr> 
  <tr> 
 <td> Adresse email sur liste bloquée<br /> </td> 
    <td> Sélectionne les destinataires dont l'adresse email se trouve sur la liste bloquée.<br/> </td>
  </tr> 
  <tr> 
   <td> Email en quarantaine<br /> </td> 
   <td> Sélection des destinataires dont l'email est en quarantaine.<br /> </td> 
  </tr> 
  <tr> 
   <td> Emails dupliqués dans le dossier<br /> </td> 
   <td> Sélection des destinataires dont l'email est dupliqué dans le dossier.<br /> </td> 
  </tr> 
  <tr> 
   <td> N'ayant ni ouvert ni cliqué<br /> </td> 
   <td> Sélection des destinataires qui n'ont ni ouvert une diffusion, ni cliqué dans une diffusion.<br /> </td> 
  </tr> 
  <tr> 
   <td> Nouveaux destinataires (jours)<br /> </td> 
   <td> Sélection des destinataires qui ont été créés dans les X derniers jours.<br /> </td> 
  </tr> 
  <tr> 
   <td> Nouveaux destinataires (minutes)<br /> </td> 
   <td> Sélection des destinataires qui ont été créés dans les X dernières minutes.<br /> </td> 
  </tr> 
  <tr> 
   <td> Nouveaux destinataires (mois)<br /> </td> 
   <td> Sélection des destinataires qui ont été créés dans les X derniers mois.<br /> </td> 
  </tr> 
  <tr> 
   <td> Par abonnement<br /> </td> 
   <td> Sélection des destinataires par abonnements.<br /> </td> 
  </tr> 
  <tr> 
   <td> Par clic sur une URL spécifique<br /> </td> 
   <td> Sélection des destinataires qui ont cliqué sur une URL particulière dans une diffusion.<br /> </td> 
  </tr> 
  <tr> 
   <td> Par comportement après une diffusion<br /> </td> 
   <td> Sélection des destinataires en fonction de leur comportement après la réception d'une diffusion.<br /> </td> 
  </tr> 
  <tr> 
   <td> Par date de création<br /> </td> 
   <td> Sélection des destinataires par date de création, sur une période entre X mois (date courante moins n mois) et Y mois (date courante moins n mois).<br /> </td> 
  </tr> 
  <tr> 
   <td> Par liste<br /> </td> 
   <td> Sélection des destinataires par liste.<br /> </td> 
  </tr> 
  <tr> 
   <td> Par nombre de clics<br /> </td> 
   <td> Sélection des destinataires qui ont cliqué dans une diffusion dans les X derniers mois.<br /> </td> 
  </tr> 
  <tr> 
   <td> Par nombre de messages reçus<br /> </td> 
   <td> Sélection des destinataires en fonction du nombre de messages qu'ils ont reçus.<br /> </td> 
  </tr> 
  <tr> 
   <td> Par nombre d'ouvertures<br /> </td> 
   <td> Sélection des destinataires qui ont ouvert entre X et Y diffusions dans une période de temps Z.<br /> </td> 
  </tr> 
  <tr> 
   <td> Par nom ou email<br /> </td> 
   <td> Sélection des destinataires en fonction de leur nom ou de leur email.<br /> </td> 
  </tr> 
  <tr> 
   <td> Par tranche d'âge<br /> </td> 
   <td> Sélection des destinataires en fonction de leur âge.<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Toutes les comparaisons de comptage et de période sont au sens large (les bornes sont incluses dans la comparaison).

Exemples de comptage :

* Sélection des destinataires de moins de 30 ans :

   ![](assets/predefined_filters_01.png)

* Sélection des destinataires de 18 ans et plus :

   ![](assets/predefined_filters_03.png)

* Sélection des destinataires qui ont entre 18 et 30 ans :

   ![](assets/predefined_filters_02.png)

## Paramètres avancés des filtres sur les données {#advanced-settings-for-data-filters}

Cliquez sur l&#39;onglet **[!UICONTROL Paramètres]** pour accéder aux options suivantes :

* **[!UICONTROL Filtre par défaut pour le type de document associé]** : cette option permet de proposer ce filtre par défaut dans l&#39;éditeur des listes concernées par le tri.

   Par exemple, le filtre **[!UICONTROL Par nom ou login]** est appliqué aux opérateurs. Cette option est sélectionnée donc le filtre est systématiquement proposé sur toutes les listes d&#39;opérateurs.

* **[!UICONTROL Filtre partagé avec les autres opérateurs]** : cette option permet de rendre ce filtre disponible pour tous les autres opérateurs sur la base courante.
* **[!UICONTROL Utilisation d&#39;un formulaire de saisie des paramètres]** : cette option permet de définir le ou les champs de filtrage qui s&#39;afficheront au-dessus de la liste lorsque ce filtre sera sélectionné. Ces champs permettent de définir les paramètres du filtre. Ce formulaire doit alors être saisi au format XML depuis le bouton **[!UICONTROL Formulaire]**. Par exemple, le filtre préconfiguré **[!UICONTROL Ayant ouvert]**, disponible dans la liste des destinataires, affiche un champ de filtrage permettant de sélectionner la diffusion visée par le filtre.

   Le bouton **[!UICONTROL Aperçu]** permet de visualiser le résultat du filtre choisi.

* Le lien **[!UICONTROL Paramètres avancés]** permet de définir des paramétrages complémentaires, et notamment d&#39;associer à ce filtre une table SQL afin de le rendre commun à tous les éditeurs qui partagent cette table.

   Cochez l&#39;option **[!UICONTROL Ne pas restreindre le filtre]** si vous souhaitez interdire à l&#39;utilisateur de surcharger ce filtre.

   Cette option est par exemple activée pour les filtres &quot;Destinataires d&#39;une diffusion&quot; et &quot;Destinataires des diffusions appartenant à un dossier&quot; proposés dans l&#39;assistant de diffusion et qui ne peuvent pas être surchargés.

   ![](assets/s_ncs_user_filter_advanced_param.png)
