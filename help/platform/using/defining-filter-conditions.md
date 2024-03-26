---
product: campaign
title: Définir les conditions de filtrage
description: Définir les conditions de filtrage
feature: Query Editor
badge-v7: label="v7" type="Informative" tooltip="S’applique à Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="S’applique également à Campaign v8"
audience: platform
content-type: reference
topic-tags: creating-queries
exl-id: b62e23e5-f1b7-44c4-82d9-95c6b3240352
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '3475'
ht-degree: 82%

---

# Définition des conditions de filtre{#defining-filter-conditions}



## Sélectionner l’opérateur {#choosing-the-operator}

Dans une condition de filtrage, il faut lier deux valeurs grâce à un opérateur.

![](assets/query_editor_nveau_96.png)

Voici une liste descriptive des opérateurs disponibles :

<table> 
 <thead> 
  <tr> 
   <th> Opérateur<br /> </th> 
   <th> Intérêt<br /> </th> 
   <th> Exemple<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">Egal à</span> <br /> </td> 
   <td> Retrouver un résultat rigoureusement identique à ce qui est entré dans la seconde colonne Valeur.<br /> </td> 
   <td> <strong>Nom (@lastName) égal à 'Martin'</strong>. Ici ne seront retournés que les destinataires dont le nom est 'Martin', avec les seuls caractères indiqués.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Supérieur à</span> <br /> </td> 
   <td> Obtenir un résultat supérieur à la valeur indiquée.<br /> </td> 
   <td> <strong>Age (@age) supérieur à '50'</strong> pour retourner toutes les valeurs supérieures à '50', donc '51', '52', etc.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Inférieur à</span> <br /> </td> 
   <td> Obtenir un résultat inférieur à la valeur indiquée.<br /> </td> 
   <td> <strong>Date de création (@created) strictement plus tôt que 'DaysAgo(100)'</strong> afin de retrouver tous les destinataires créés dans la base il y a moins de 100 jours.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Supérieur ou égal à</span> <br /> </td> 
   <td> Obtenir un résultat rigoureusement égal ou supérieur à la valeur renseignée.<br /> </td> 
   <td> <strong>Age (@age) supérieur ou égal à '30'</strong>, afin de retrouver les destinataires dont l'âge est de 30 ans, 31 ans, etc.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Inférieur ou égal à</span> <br /> </td> 
   <td> Obtenir un résultat rigoureusement égal ou inférieur à la valeur renseignée.<br /> </td> 
   <td> <strong>Age (@age) inférieur ou égal à '60'</strong> pour retrouver les destinataires dont l'âge est de 60 ans ou moins.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Différent de</span> <br /> </td> 
   <td> Le résultat retourné ne doit pas être identique à la valeur renseignée.<br /> </td> 
   <td> <strong>Langue (@language) différent de 'Anglais'</strong>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Commence par</span> <br /> </td> 
   <td> Obtenir des résultats commençant par la valeur indiquée.<br /> </td> 
   <td> <strong>N° de compte (@account) commence par '32010'.</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Ne commence pas par</span> <br /> </td> 
   <td> Obtenir des résultats qui ne commencent pas par la valeur renseignée<br /> </td> 
   <td> <strong>N° de compte (@account) ne commence pas par '20'</strong>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Contient</span> <br /> </td> 
   <td> Obtenir un résultat comportant au moins la valeur qui est renseignée.<br /> </td> 
   <td> <strong>Domaine de l'email (@domain) contient 'mail'</strong>, renverra tous les noms de domaine contenant "mail". Le domaine 'gmail.com' sera donc également retourné.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Ne contient pas</span> <br /> </td> 
   <td> Ne pas obtenir de résultats contenant au moins la valeur renseignée.<br /> </td> 
   <td> <strong>Domaine de l'email (@domain) ne contient pas 'vo'</strong>. Dans ce cas, les noms de domaine contenant "vo" ne seront pas renvoyés. Le nom de domaine 'voila.fr' n'apparaîtra pas dans les résultats.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Comme</span> <br /> </td> 
   <td> <span class="uicontrol">Comme</span> est quasiment identique à l'opérateur <span class="uicontrol">Contient. </span> Il vous permet d’insérer un caractère joker <span class="uicontrol">%</span> dans la valeur.<br /> </td> 
   <td> <strong>Nom (@lastName) comme 'Jon%s'</strong>. Ici, le caractère joker est utilisé comme "joker" pour trouver le nom "Jones", si l'opérateur a oublié la lettre manquante entre le 'n' et le 's'.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Pas comme</span> <br /> </td> 
   <td> Est similaire à <span class="uicontrol">Comme</span> . Permet de ne pas récupérer la valeur saisie. La valeur renseignée doit ici aussi comporter le caractère de substitution <span class="uicontrol">%</span>.<br /> </td> 
   <td> <strong>Nom (@lastName) différent de 'Smi%h'</strong>. Ici, les destinataires dont le nom est 'Smi%h' ne seront pas retournés.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Est vide</span> <br /> </td> 
   <td> Dans ce cas, le résultat recherché correspond à une valeur vide dans la seconde colonne Valeur.<br /> </td> 
   <td> <strong>Portable (@mobilePhone) est vide</strong> afin de retrouver tous les destinataires ne disposant pas d'un numéro de téléphone mobile.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">N'est pas vide</span> <br /> </td> 
   <td> Fonctionne en sens inverse de la fonction <span class="uicontrol">Est vide</span> de l’opérateur. Il n'est pas nécessaire de saisir des données dans la seconde colonne Valeur.<br /> </td> 
   <td> <strong>Email (@email) n'est pas vide</strong>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Est compris dans</span> <br /> </td> 
   <td> Renvoie les résultats compris dans les valeurs indiquées. Ces valeurs doivent être séparées par une virgule.<br /> </td> 
   <td> <strong>Code Postal (location/@zipCode) est compris dans '75014, 75015'</strong>. Si des destinataires sont recherchés, la requête retrouvera ceux dont le code postal égal à 75014 et 75015. <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">N'est pas compris dans</span> <br /> </td> 
   <td> Fonctionne comme le <span class="uicontrol">Est inclus dans</span> de l’opérateur. Ici, nous allons exclure les destinataires en fonction des valeurs renseignées.<br /> </td> 
   <td> <strong>La date de naissance (@birthDate) n’est pas incluse dans "12/10/1979,12/10/1984"</strong>. Contrairement à l’exemple précédent, les destinataires nés à cette date ne seront pas renvoyés.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Utiliser ET, OU, SAUF {#using-and--or--except}

Dans les requêtes utilisant plus d&#39;un critère de filtrage, vous devez définir les liens entre conditions. Il y a trois liens possibles :

* **[!UICONTROL Et]** permet de cumuler deux conditions de filtrage,
* **[!UICONTROL Ou]** sert à proposer une alternative,
* **[!UICONTROL Sauf]** sert à définir une exception.

Cliquez sur le **[!UICONTROL Et]** (proposé par défaut) et faites votre choix dans la liste déroulante.

![](assets/query_condition_modif_01.png)

* **[!UICONTROL Et]** : ajoute une condition en plus de la précédente et permet de surfiltrer.
* **[!UICONTROL Ou]** : permet de prendre en compte au moins un résultat par rapport aux conditions définies.

  L&#39;exemple ci-dessous permet de retrouver des destinataires dont le domaine d&#39;email contient &quot;voila.fr&quot; OU dont le code postal commence par le chiffre &quot;49&quot;.

  ![](assets/query_condition_modif_02.png)

* **[!UICONTROL Sauf]** : si vous avez deux filtres et que le premier permet de ne pas obtenir de valeur, une relation de ce type crée une exception.

  Dans l&#39;exemple ci-dessous, on recherche des destinataires dont le domaine d&#39;email contient &quot;voila.fr&quot; SAUF si le nom de famille des destinataires correspond à la valeur &quot;Smith&quot;.

  ![](assets/query_condition_modif_03.png)

Cet autre exemple montre un filtre permettant d&#39;afficher : les destinataires de langue espagnole OU les femmes dont le numéro de téléphone mobile est renseigné OU les destinataires qui n&#39;ont pas renseigné leur numéro de compte et dont le nom de société commence &quot;N&quot;.

![](assets/query_editor_nveau_31.png)

## Hiérarchiser les conditions {#prioritizing-conditions}

Cette section explique comment hiérarchiser les conditions. Ceci est possible grâce aux flèches bleues situées dans la barre d&#39;outils.

* La flèche pointant vers la droite permet d&#39;ajouter un niveau de parenthèses au filtrage.
* La flèche pointant vers la gauche permet de supprimer un niveau de parenthèses.

  ![](assets/query_condition_modif_04.png)

* Les flèches pointant vers le haut et vers le bas permettent de déplacer une condition. Cela modifie l&#39;ordre d&#39;exécution des filtres.

Cet exemple montre comment utiliser la flèche pour supprimer un niveau de parenthèses. Commencez par la condition de filtrage suivante : **[!UICONTROL Ville égale à Londres OU genre égal à masculin et mobile non indiqué OU numéro de compte commence par &quot;95&quot; et le nom de la société commence par &quot;A&quot;]**.

Pointez votre curseur sur la condition de filtrage **[!UICONTROL Gender (@gender) égal à Masculin]** puis cliquez sur la flèche **[!UICONTROL Supprimer un niveau de parenthèses]**.

![](assets/query_editor_nveau_32.png)

La variable **[!UICONTROL Genre (@gender) égal à Masculin]** a été extraite de sa parenthèse. Il est passé au même niveau que la condition &quot;Ville égale à Londres&quot;. Ces conditions sont liées (**[!UICONTROL Et]**).

## Sélectionner les données à extraire {#selecting-data-to-extract}

Les champs disponibles varient d’une table à l’autre. Tous les champs sont stockés dans un noeud principal appelé **[!UICONTROL Elément principal]**. Dans l&#39;exemple suivant, les champs disponibles se trouvent dans la table des destinataires. Les champs sont toujours affichés par ordre alphabétique.

Le détail du champ sélectionné est visible en bas de la fenêtre. Par exemple, la variable **[!UICONTROL Domaine de l&#39;email]** est un **[!UICONTROL Champ SQL calculé]** et son extension est **[!UICONTROL (@domain)]**.

![](assets/query_editor_nveau_59.png)

>[!NOTE]
>
>Utilisez la section **[!UICONTROL Rechercher]** pour retrouver un champ disponible.

Double-cliquez sur un champ disponible pour l&#39;ajouter aux colonnes de sortie. A la fin de la requête, chaque champ sélectionné crée une colonne dans le champ **[!UICONTROL Aperçu des données]** fenêtre.

![](assets/query_editor_nveau_01.png)

Les champs avancés ne sont pas affichés par défaut. Cliquez sur **[!UICONTROL Afficher les champs avancés]** dans le coin inférieur droit des champs disponibles pour tout afficher. Cliquez de nouveau pour revenir à la vue précédente.

Par exemple, dans la table des destinataires, les champs avancés sont **Booléen 1**, **[!UICONTROL Booléen 2]**, **[!UICONTROL Booléen 3]**, **[!UICONTROL Clé étrangère du lien &quot;Dossier&quot;]**, etc.

L&#39;exemple ci-dessous montre les champs avancés de la table des destinataires.

![](assets/query_editor_nveau_53.png)

Les différentes catégories de champs :

<table> 
 <thead> 
  <tr> 
   <th> Icône<br /> </th> 
   <th> Description<br /> </th> 
   <th> Exemples<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_47.png" /> </td> 
   <td> Champ simple<br /> </td> 
   <td> Civilité, email, genre, etc.<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_48.png" /> </td> 
   <td> Clé primaire. Ce champ SQL sert à identifier de manière unique un enregistrement dans une table.<br /> </td> 
   <td> L'identifiant d'un destinataire est une clé primaire et un identifiant est unique par définition.<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_02.png" /> </td> 
   <td> Clé étrangère. Sert de lien vers une autre table.<br /> </td> 
   <td> Clé étrangère du destinataire, clé étrangère du service, etc.<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_46.png" /> </td> 
   <td> Champ calculé. Ce type de champ est calculé à la demande, à partir de valeurs stockées en base.<br /> </td> 
   <td> Âge, domaine d'email, etc.<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_49.png" /> </td> 
   <td> Champ contenant des textes longs.<br /> </td> 
   <td> Commentaire, Adresse complète, etc.<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_50.png" /> </td> 
   <td> Champ SQL indexé. <br /> </td> 
   <td> Nom complet, Code ISO, etc. <br /> </td> 
  </tr> 
 </tbody> 
</table>

Liens vers une table et éléments de collection :

<table> 
 <thead> 
  <tr> 
   <th> Icône<br /> </th> 
   <th> Description<br /> </th> 
   <th> Exemple<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_51.png" /> </td> 
   <td> Liens vers une table en particulier. Elles correspondent à des associations de type 1-1. Une occurrence de la table source ne peut correspondre qu’à une seule occurrence de la table cible. Par exemple, un seul destinataire peut être lié à un pays.<br /> </td> 
   <td> Dossier, Etat, Pays, etc. <br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_52.png" /> </td> 
   <td> Elément de collection sur une table spécifique. Elles correspondent à des associations de type 1-N. Une occurrence de la table source peut correspondre à plusieurs occurrences de la table cible, mais une occurrence de la table cible peut correspondre à une seule occurrence de la table source. Par exemple, un destinataire peut s'abonner à "n" lettres d'abonnement.<br /> </td> 
   <td> Abonnements, listes, logs d'exclusion, etc.<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>* Utilisez le bouton **[!UICONTROL Ajouter]** (au-dessus de la barre d’icônes latérale) pour ajouter une colonne de sortie dans laquelle vous souhaitez modifier l’expression. Pour plus d’informations sur la modification d’une expression, voir [cette section](#building-expressions).
>* Supprimez une colonne de sortie en cliquant sur la croix rouge **Supprimer**.
>* Modifiez l&#39;ordre des colonnes de sortie grâce aux flèches.
>* L’icône **[!UICONTROL Répartition des valeurs]** sert à visualiser la répartition des valeurs du champ sélectionné (par exemple, les répartitions liées aux villes des destinataires, à la langue des destinataires, etc.).

## Créer des champs calculés {#creating-calculated-fields}

Au besoin, ajoutez une colonne lors du formatage des données. Un champ calculé ajoute une colonne à la section d’aperçu des données. Cliquez sur **[!UICONTROL Ajouter un champ calculé]**.

![](assets/query_editor_nveau_43.png)

Quatre types de champ calculé sont proposés :

* **[!UICONTROL Chaîne fixe]** : pour ajouter une chaîne de caractères.

  ![](assets/query_editor_nveau_60.png)

* **[!UICONTROL Chaîne avec fusion JavaScript]** : la valeur du champ calculé combine une chaîne de caractères à des directives JavaScript.

  ![](assets/query_editor_nveau_61.png)

* **[!UICONTROL Expression JavaScript]** : la valeur du champ calculé est le résultat de l&#39;évaluation d&#39;une fonction JavaScript. La valeur retournée peut être typée (nombre, date, etc.).

  ![](assets/query_editor_nveau_62.png)

* **[!UICONTROL Enumérations]**. Ce type de champ permet d&#39;utiliser/transformer le contenu d&#39;une des colonnes de sortie dans une nouvelle colonne.

  On peut utiliser la valeur source d&#39;une colonne et lui donner une valeur de destination. Cette valeur de destination sera affichée dans la nouvelle colonne de sortie.

  Un exemple d&#39;ajout de champ calculé de type **[!UICONTROL Enumérations]** est disponible. Reportez-vous à [cette section](../../workflow/using/adding-enumeration-type-calculated-field.md).

  ![](assets/query_editor_nveau_63.png)

  Le champ calculé de type **[!UICONTROL Enumérations]** peut comporter quatre conditions :

   * **[!UICONTROL Conserver la valeur source]** restitue la valeur de la source, sans transformation dans la cible.
   * **[!UICONTROL Utiliser la valeur suivante]** sert à saisir une valeur de destination par défaut, pour les valeurs sources non définies.
   * **[!UICONTROL Générer un avertissement et continuer]** avertit l&#39;utilisateur que la valeur source ne peut être transformée.
   * **[!UICONTROL Générer une erreur et rejeter la ligne]** empêche le calcul de la ligne et son export.

Cliquez sur la loupe **[!UICONTROL Détail du champ calculé]** pour visualiser le champ inséré en détail.

Pour retirer le champ, cliquez sur la croix rouge **[!UICONTROL Enlever le champ calculé]**.

![](assets/query_editor_nveau_58.png)

## Créer des expressions {#building-expressions}

L&#39;outil d&#39;édition d&#39;une expression sert à calculer des agrégats, générer une fonction ou éditer une formule à partir d&#39;une expression.

L&#39;exemple ci-dessous présente comment faire un comptage sur une clé primaire.

Les étapes sont les suivantes :

1. Cliquez sur **[!UICONTROL Ajouter]** dans le **[!UICONTROL Données à extraire]** fenêtre. Dans le **[!UICONTROL Type de formule]** sélectionnez un type de formule pour renseigner l&#39;expression.

   Plusieurs types de formules sont disponibles : **[!UICONTROL Champ simple]**, **[!UICONTROL Agrégat]**, **[!UICONTROL Expression]**.

   Sélectionner **[!UICONTROL Traitement sur une fonction d&#39;agrégat]**, et **[!UICONTROL Count]**. Cliquez sur **[!UICONTROL Suivant]**.

   ![](assets/query_editor_nveau_54.png)

1. Le calcul de la clé primaire est effectué.

   ![](assets/query_editor_nveau_88.png)

Voici le détail des choix de la fenêtre **[!UICONTROL Types de formules]** :

![](assets/query_editor_nveau_05.png)

1. **[!UICONTROL Champ simple]** permet de revenir à la fenêtre **[!UICONTROL Champ à sélectionner]**.
1. **[!UICONTROL Agrégat (Traitement sur une fonction d&#39;agrégat)]**. Voici des exemples d&#39;utilisation des agrégats :

   * **[!UICONTROL Comptage]** permet d&#39;effectuer un comptage de clé primaire.
   * **[!UICONTROL Somme]** sert à totaliser tous les achats d&#39;un prospect sur une année.
   * **[!UICONTROL Valeur maximum]** pour retrouver des clients qui ont acheté un maximum de &quot;n&quot; produits.
   * **[!UICONTROL Valeur minimum]** permet d&#39;obtenir parmi des clients, ceux qui ont souscrit à une offre le plus récemment.
   * **[!UICONTROL Moyenne]**. Cette fonction permet de calculer l&#39;âge moyen des destinataires.

     La case **[!UICONTROL Distinct]** permet de récupérer les valeurs uniques et non nulles d&#39;une colonne. On peut ainsi récupérer les logs de tracking d&#39;un destinataire qui seront ramenés à la valeur 1 car il s&#39;agit d&#39;un seul destinataire.

1. **[!UICONTROL Expression]** ouvre la fenêtre **[!UICONTROL Edition de l&#39;expression]**. Par exemple, une expression pourra détecter les numéros de téléphone de plus de 10 chiffres, synonymes de possibles erreurs de saisie.

   ![](assets/query_editor_nveau_71.png)

   Pour une liste complète des fonctions disponibles, voir la section [Liste des fonctions](#list-of-functions).

## Liste des fonctions {#list-of-functions}

Si **[!UICONTROL Expression]** type de formule choisie, vous serez alors dirigé vers la fenêtre &quot;éditer l&#39;expression&quot;. Différentes catégories de fonctions peuvent être associées aux champs disponibles : **[!UICONTROL Agrégats]**, **[!UICONTROL Chaîne]**, **[!UICONTROL Date]**, **[!UICONTROL Numérique]**, **[!UICONTROL Devise]**, **[!UICONTROL Geomarketing]**, **[!UICONTROL Fonction Windows]** et **[!UICONTROL Autres]**.

L&#39;éditeur d&#39;expression se présente comme suit :

![](assets/s_ncs_user_filter_define_expression.png)

Il permet de sélectionner des champs dans les tables de la base de données et de leur adjoindre des fonctions avancées. Les fonctions disponibles sont les suivantes :

**Agrégats**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Nom</strong><br /> </td> 
   <td> <strong>Description</strong><br /> </td> 
   <td> <strong>Syntaxe</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Avg</strong><br /> </td> 
   <td> Renvoie la moyenne d'une colonne de type numérique<br /> </td> 
   <td> Avg(&lt;valeur&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Count</strong><br /> </td> 
   <td> Compte les valeurs non nulles d'une colonne<br /> </td> 
   <td> Count(&lt;valeur&gt;)<br /></td>  
  </tr> 
  <tr> 
   <td> <strong>CountAll</strong><br /> </td> 
   <td> Compte les valeurs retournées (tous champs confondus)<br /> </td> 
   <td> CountAll()<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Countdistinct</strong><br /> </td> 
   <td> Compte les valeurs distinctes non nulles d'une colonne<br /> </td> 
   <td> Countdistinct(&lt;valeur&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Max</strong><br /> </td> 
   <td> Renvoie la valeur maximum d'une colonne de type nombre, chaîne ou date<br /> </td> 
   <td> Max(&lt;valeur&gt;)<br /></td>  
  </tr> 
  <tr> 
   <td> <strong>Min</strong><br /> </td> 
   <td> Renvoie la valeur minimum d'une colonne de type nombre, chaîne ou date<br /> </td> 
   <td> Min(&lt;valeur&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>StdDev</strong><br /> </td> 
   <td> Renvoie l'écart type d'une colonne de type nombre<br /> </td> 
   <td> StdDev(&lt;valeur&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Sum</strong><br /> </td> 
   <td> Renvoie la somme des valeurs d'une colonne de type nombre, chaîne ou date<br /> </td> 
   <td> Sum(&lt;valeur&gt;)<br /></td> 
  </tr> 
 </tbody> 
</table>

**Chaîne**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Nom</strong><br /> </td> 
   <td> <strong>Description</strong><br /> </td> 
   <td> <strong>Syntaxe</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AllNonNull2</strong><br /> </td> 
   <td> Indique si tous les paramètres sont non nuls et non vides<br /> </td> 
   <td> AllNonNull2(&lt;chaîne&gt;, &lt;chaîne&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>AllNonNull3</strong><br /> </td> 
   <td> Indique si tous les paramètres sont non nuls et non vides<br /> </td> 
   <td> AllNonNull3(&lt;chaîne&gt;, &lt;chaîne&gt;, &lt;chaîne&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Ascii</strong><br /> </td> 
   <td> Renvoie la valeur ascii du premier caractère de la chaîne.<br /> </td> 
   <td> Ascii(&lt;chaîne&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Char</strong><br /> </td> 
   <td> Renvoie le caractère de code ascii n<br /> </td> 
   <td> Char(&lt;nombre&gt;)<br /></td>  
  </tr> 
  <tr> 
   <td> <strong>Charindex</strong><br /> </td> 
   <td> Retourne la position de la chaîne 2 dans la chaîne 1.<br /> </td> 
   <td> Charindex(&lt;chaîne&gt;, &lt;chaîne&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>GetLine</strong><br /> </td> 
   <td> Renvoie la nième (de 1 à n) ligne de la chaîne<br /> </td> 
   <td> GetLine(&lt;chaîne&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>IfEquals</strong><br /> </td> 
   <td> Renvoie le troisième paramètre si les deux premiers paramètres sont égaux. Sinon, renvoie le dernier paramètre.<br /> </td> 
   <td> IfEquals(&lt;chaîne&gt;, &lt;chaîne&gt;, &lt;chaîne&gt;, &lt;chaîne&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>IsMemoNull</strong><br /> </td> 
   <td> Indique si le memo passé en paramètre est nul<br /> </td> 
   <td> IsMemoNull(&lt;memo&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>JuxtWords</strong><br /> </td> 
   <td> Concatène les chaînes passées en paramètres. Ajoute des espaces entre les chaînes si nécessaire.<br /> </td> 
   <td> JuxtWords(&lt;chaîne&gt;, &lt;chaîne&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>JuxtWords3</strong><br /> </td> 
   <td> Concatène les chaînes passées en paramètres. Ajoute des espaces entre les chaînes si nécessaire.<br /> </td> 
   <td> JuxtWords3(&lt;string&gt;, &lt;string&gt;, &lt;string&gt;)<br /></td>  
  </tr> 
  <tr> 
   <td> <strong>LPad</strong><br /> </td> 
   <td> Renvoie la chaîne complétée à gauche<br /> </td> 
   <td> LPad(&lt;chaîne&gt;, &lt;nombre&gt;, &lt;caractère&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Left</strong><br /> </td> 
   <td> Renvoie les n premiers caractères de la chaîne<br /> </td> 
   <td> Left(&lt;chaîne&gt;, &lt;nombre&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Length</strong><br /> </td> 
   <td> Renvoie la longueur de la chaîne<br /> </td> 
   <td> Length(&lt;chaîne&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Lower</strong><br /> </td> 
   <td> Renvoie la chaîne en minuscules<br /> </td> 
   <td> Lower(&lt;chaîne&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Ltrim</strong><br /> </td> 
   <td> Ote les espaces à gauche de la chaîne<br /> </td> 
   <td> Ltrim(&lt;chaîne&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Md5Digest</strong><br /> </td> 
   <td> Renvoie une représentation hexadécimale de la clé MD5 d'une chaîne<br /> </td> 
   <td> Md5Digest(&lt;chaîne&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>MemoContains</strong><br /> </td> 
   <td> Indique si le mémo contient la chaîne passée en paramètre<br /> </td> 
   <td> MemoContains(&lt;memo&gt;, &lt;chaîne&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>RPad</strong><br /> </td> 
   <td> Renvoie la chaîne complétée à droite<br /> </td> 
   <td> RPad(&lt;chaîne&gt;, &lt;nombre&gt;, &lt;caractère&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Right</strong><br /> </td> 
   <td> Renvoie les n derniers caractères de la chaîne<br /> </td> 
   <td> Right(&lt;chaîne&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Rtrim</strong><br /> </td> 
   <td> Ote les espaces à droite de la chaîne<br /> </td> 
   <td> Rtrim(&lt;chaîne&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Smart</strong><br /> </td> 
   <td> Renvoie la chaîne avec la première lettre de chaque mot en majuscule<br /> </td> 
   <td> Smart(&lt;chaîne&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Substring</strong><br /> </td> 
   <td> Extrait la sous-chaîne débutant au caractère n1 de la chaîne et de longueur n2<br /> </td> 
   <td> Substring(&lt;chaîne&gt;, &lt;départ&gt;, &lt;longueur&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToString</strong><br /> </td> 
   <td> Convertit le nombre en chaîne<br /> </td> 
   <td> ToString(&lt;nombre&gt;, &lt;nombre&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Upper</strong><br /> </td> 
   <td> Renvoie la chaîne en majuscules<br /> </td> 
   <td> Upper(&lt;chaîne&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>VirtualLink</strong><br /> </td> 
   <td> Renvoie la clé étrangère d'un lien passée en premier paramètre, si les deux autres paramètres sont égaux<br /> </td> 
   <td> VirtualLink(&lt;nombre&gt;, &lt;nombre&gt;, &lt;nombre&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>VirtualLinkStr</strong><br /> </td> 
   <td> Renvoie la clé étrangère (texte) d'un lien passée en premier paramètre, si les deux autres paramètres sont égaux<br /> </td> 
   <td> VirtualLinkStr(&lt;chaîne&gt;, &lt;nombre&gt;, &lt;nombre&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>dataLength</strong><br /> </td> 
   <td> Renvoie la taille de la chaîne<br /> </td> 
   <td> dataLength(&lt;chaîne&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

**Date**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Nom</strong><br /> </td> 
   <td> <strong>Description</strong><br /> </td> 
   <td> <strong>Syntaxe</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AddDays</strong><br /> </td> 
   <td> Ajoute un nombre de jours à une date<br /> </td> 
   <td> AddDays(&lt;date&gt;, &lt;nombre&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddHours</strong><br /> </td> 
   <td> Ajoute un nombre d'heures à une date<br /> </td> 
   <td> AddHours(&lt;date&gt;, &lt;nombre&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddMinutes</strong><br /> </td> 
   <td> Ajoute un nombre de minutes à une date<br /> </td> 
   <td> AddMinutes(&lt;date&gt;, &lt;nombre&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddMonths</strong><br /> </td> 
   <td> Ajoute un nombre de mois à une date<br /> </td> 
   <td> AddMonths(&lt;date&gt;, &lt;nombre&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddSeconds</strong><br /> </td> 
   <td> Ajoute un nombre de secondes à une date<br /> </td> 
   <td> AddSeconds(&lt;date&gt;, &lt;nombre&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddYears</strong><br /> </td> 
   <td> Ajoute un nombre d'années à une date<br /> </td> 
   <td> AddYears(&lt;date&gt;, &lt;nombre&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DateOnly</strong><br /> </td> 
   <td> Renvoie la date uniquement (avec heure à zéro)*<br /> </td> 
   <td> DateOnly(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Jour</strong><br /> </td> 
   <td> Renvoie le nombre représentant le jour de la date<br /> </td> 
   <td> Day(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DayOfYear</strong><br /> </td> 
   <td> Renvoie le numéro du jour dans l'année de la date<br /> </td> 
   <td> DayOfYear(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DaysAgo</strong><br /> </td> 
   <td> Renvoie la date correspondant à la date courante moins n jours<br /> </td> 
   <td> DaysAgo(&lt;nombre&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DaysAgoInt</strong><br /> </td> 
   <td> Renvoie la date (entier aaaammjj) correspondant à la date courante moins n jours<br /> </td> 
   <td> DaysAgoInt(&lt;nombre&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DaysDiff</strong><br /> </td> 
   <td> Nombre de jours entre deux dates<br /> </td> 
   <td> DaysDiff(&lt;date de fin&gt;, &lt;date de début&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DaysOld</strong><br /> </td> 
   <td> Renvoie l'ancienneté en jours d'une date<br /> </td> 
   <td> DaysOld(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>GetDate</strong><br /> </td> 
   <td> Renvoie la date système courante du serveur<br /> </td> 
   <td> GetDate()<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Hour</strong><br /> </td> 
   <td> Renvoie l'heure de la date<br /> </td> 
   <td> Hour(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>HoursDiff</strong><br /> </td> 
   <td> Renvoie le nombre d'heures entre deux dates<br /> </td> 
   <td> HoursDiff(&lt;date de fin&gt;, &lt;date de début&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Minute</strong><br /> </td> 
   <td> Renvoie les minutes de la date<br /> </td> 
   <td> Minute(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>MinutesDiff</strong><br /> </td> 
   <td> Renvoie le nombre de minutes entre deux dates<br /> </td> 
   <td> MinutesDiff(&lt;date de fin&gt;, &lt;date de début&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Month</strong><br /> </td> 
   <td> Renvoie le nombre représentant le mois de la date<br /> </td> 
   <td> Month(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>MonthsAgo</strong><br /> </td> 
   <td> Renvoie la date correspondant à la date courante moins n mois<br /> </td> 
   <td> MonthsAgo(&lt;nombre&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>MonthsDiff</strong><br /> </td> 
   <td> Renvoie le nombre de mois entre deux dates<br /> </td> 
   <td> MonthsDiff(&lt;date de fin&gt;, &lt;date de début&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>MonthsOld</strong><br /> </td> 
   <td> Renvoie l'ancienneté en mois d'une date<br /> </td> 
   <td> MonthsOld(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Second</strong><br /> </td> 
   <td> Renvoie les secondes de la date<br /> </td> 
   <td> Second(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SecondsDiff</strong><br /> </td> 
   <td> Renvoie le nombre de secondes entre deux dates<br /> </td> 
   <td> SecondsDiff(&lt;date de fin&gt;, &lt;date de début&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubDays</strong><br /> </td> 
   <td> Enlève un nombre de jours à une date<br /> </td> 
   <td> SubDays(&lt;date&gt;, &lt;nombre&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubHours</strong><br /> </td> 
   <td> Enlève un nombre d'heures à une date<br /> </td> 
   <td> SubHours(&lt;date&gt;, &lt;nombre&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubMinutes</strong><br /> </td> 
   <td> Enlève un nombre de minutes à une date<br /> </td> 
   <td> SubMinutes(&lt;date&gt;, &lt;nombre&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubMonths</strong><br /> </td> 
   <td> Enlève un nombre de mois à une date<br /> </td> 
   <td> SubMonths(&lt;date&gt;, &lt;nombre&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubSeconds</strong><br /> </td> 
   <td> Enlève un nombre de secondes à une date<br /> </td> 
   <td> SubSeconds(&lt;date&gt;, &lt;nombre&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubYears</strong><br /> </td> 
   <td> Enlève un nombre d'années à une date<br /> </td> 
   <td> SubYears(&lt;date&gt;, &lt;nombre&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToDate</strong><br /> </td> 
   <td> Convertit une date + heure en date seule<br /> </td> 
   <td> ToDate(&lt;date + heure&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToDateTime</strong><br /> </td> 
   <td> Convertit une chaîne en date + heure<br /> </td> 
   <td> ToDateTime(&lt;chaîne&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncDate</strong><br /> </td> 
   <td> Arrondit une date + heure à la seconde<br /> </td> 
   <td> TruncDate(@lastModified, &lt;nombre de secondes&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>TruncDateTZ</strong><br /> </td> 
   <td> Arrondit une date + heure à la seconde près<br /> </td> 
   <td> TruncDateTZ(&lt;date&gt;, &lt;nombre de secondes&gt;, &lt;fuseau horaire&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>TruncQuarter</strong><br /> </td> 
   <td> Arrondit une date au trimestre<br /> </td> 
   <td> TruncQuarter(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncTime</strong><br /> </td> 
   <td> Arrondit la partie heure à la seconde<br /> </td> 
   <td> TruncTim(e&lt;date&gt;, &lt;nombre de secondes&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncWeek</strong><br /> </td> 
   <td> Arrondit une date à la semaine<br /> </td> 
   <td> TruncWeek(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncYear</strong><br /> </td> 
   <td> Arrondit une date + heure au premier janvier de l'année<br /> </td> 
   <td> TruncYear(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncWeek</strong><br /> </td> 
   <td> Renvoie le numéro du jour dans la semaine de la date<br /> </td> 
   <td> WeekDay(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Year</strong><br /> </td> 
   <td> Renvoie le nombre représentant l'année de la date<br /> </td> 
   <td> Year(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>YearAnd Month</strong><br /> </td> 
   <td> Renvoie le nombre représentant l'année et le mois de la date<br /> </td> 
   <td> YearAndMonth(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>YearsDiff</strong><br /> </td> 
   <td> Renvoie le nombre d'années entre deux dates<br /> </td> 
   <td> YearsDiff(&lt;date de fin&gt;, &lt;date de début&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>YearsOld</strong><br /> </td> 
   <td> Renvoie l'ancienneté en années d'une date<br /> </td> 
   <td> YearsOld(&lt;date&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Notez que la fonction **Dateonly** prend uniquement le fuseau horaire du serveur, et non celui de l&#39;opérateur.

**Numériques**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Nom</strong><br /> </td> 
   <td> <strong>Description</strong><br /> </td> 
   <td> <strong>Syntaxe</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Abs</strong><br /> </td> 
   <td> Renvoie la valeur absolue d'un nombre<br /> </td> 
   <td> Abs(&lt;nombre&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Ceil</strong><br /> </td> 
   <td> Renvoie le plus petit entier supérieur ou égal à un nombre<br /> </td> 
   <td> Ceil(&lt;nombre&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Floor</strong><br /> </td> 
   <td> Renvoie le plus grand entier supérieur ou égal à un nombre<br /> </td> 
   <td> Floor(&lt;nombre&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Greatest</strong><br /> </td> 
   <td> Renvoie le plus grand de deux nombres<br /> </td> 
   <td> Greatest(&lt;nombre 1&gt;, &lt;nombre 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Least</strong><br /> </td> 
   <td> Renvoie le plus petit de deux nombres<br /> </td> 
   <td> Least(&lt;nombre 1&gt;, &lt;nombre 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Mod</strong><br /> </td> 
   <td> Renvoie le reste de la division entiers de n1 par n2<br /> </td> 
   <td> Mod(&lt;nombre 1&gt;, &lt;nombre 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Percent</strong><br /> </td> 
   <td> Renvoie la proportion en pourcentage entre deux nombres<br /> </td> 
   <td> Percent(&lt;nombre 1&gt;, &lt;nombre 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Random</strong><br /> </td> 
   <td> Renvoie une valeur aléatoire<br /> </td> 
   <td> Random()<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Round</strong><br /> </td> 
   <td> Arrondit un nombre à n décimales près<br /> </td> 
   <td> Round(&lt;nombre&gt;, &lt;nombre de décimales&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Sign</strong><br /> </td> 
   <td> Renvoie le signe du nombre<br /> </td> 
   <td> Sign(&lt;nombre&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToDouble</strong><br /> </td> 
   <td> Convertit un entier en réel<br /> </td> 
   <td> ToDouble(&lt;nombre&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToInt64</strong><br /> </td> 
   <td> Convertit un réel en entier 64 bits<br /> </td> 
   <td> ToInt64(&lt;nombre&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToInteger</strong><br /> </td> 
   <td> Convertit un réel en entier<br /> </td> 
   <td> ToInteger(&lt;nombre&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Trunc</strong><br /> </td> 
   <td> Tronque n1 à n2 décimales<br /> </td> 
   <td> Trunc(&lt;n1&gt;, &lt;n2&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

1. Monétaire

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Nom</strong><br /> </td> 
   <td> <strong>Description</strong><br /> </td> 
   <td> <strong>Syntaxe</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>ConvertCurrency</strong><br /> </td> 
   <td> Convertit un montant d'une monnaie source en un montant d'une monnaie cible<br /> </td> 
   <td> ConvertCurrency(&lt;montant&gt;, &lt;monnaie source&gt;, &lt;monnaie cible&gt;, &lt;date de conversion&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>FormatCurrency</strong><br /> </td> 
   <td> Formate l'affichage d'un montant en fonction des paramètres de la monnaie choisie<br /> </td> 
   <td> FormatCurrency(&lt;montant&gt;, &lt;monnaie&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

**Géomarketing**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Nom</strong><br /> </td> 
   <td> <strong>Description</strong><br /> </td> 
   <td> <strong>Syntaxe</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Distance</strong><br /> </td> 
   <td> Renvoie la distance entre deux points donnés par leur longitude et leur latitude, exprimées en degrés.<br /> </td> 
   <td> Distance(&lt;Longitude A&gt;, &lt;Latitude A&gt;, &lt;Longitude B&gt;, &lt;Latitude B&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

**Autres**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Nom</strong><br /> </td> 
   <td> <strong>Description</strong><br /> </td> 
   <td> <strong>Syntaxe</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Case</strong><br /> </td> 
   <td> Renvoie la valeur 1 si la condition est vérifiée. Sinon, renvoie la valeur 2.<br /> </td> 
   <td> Case(When(&lt;condition&gt;, &lt;valeur 1&gt;), Else(&lt;valeur 2&gt;))<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>ClearBit</strong><br /> </td> 
   <td> Efface le Flag dans la valeur<br /> </td> 
   <td> ClearBit(&lt;identifiant&gt;, &lt;flag&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Coalesce</strong><br /> </td> 
   <td> Renvoie la valeur 2 si la valeur 1 est nulle ou vide (null), sinon renvoie la valeur 1<br /> </td> 
   <td> Coalesce(&lt;valeur 1&gt;, &lt;valeur 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Decode</strong><br /> </td> 
   <td> Renvoie la valeur 3 si la valeur 1 = la valeur 2. Sinon, renvoie la valeur 4.<br /> </td> 
   <td> Decode(&lt;valeur 1&gt;, &lt;valeur 2&gt;, &lt;valeur 3&gt;, &lt;valeur 4&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Else</strong><br /> </td> 
   <td> Renvoie la valeur 1 (ne peut être utilisée qu'en paramètre de la fonction Case)<br /> </td> 
   <td> Else(&lt;valeur 1&gt;, &lt;valeur 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>GetEmailDomain</strong><br /> </td> 
   <td> Extrait le domaine d'une adresse e-mail<br /> </td> 
   <td> GetEmailDomain(&lt;valeur&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>GetMirrorURL</strong><br /> </td> 
   <td> Récupère l'URL du serveur de page miroir<br /> </td> 
   <td> GetMirrorURL(&lt;valeur&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Iif</strong><br /> </td> 
   <td> Renvoie la valeur 1 si l’expression est vraie. Sinon, renvoie la valeur 2.<br /> </td> 
   <td> Iif(&lt;condition&gt;, &lt;valeur 1&gt;, &lt;valeur 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>IsBitSet</strong><br /> </td> 
   <td> Indique si le Flag est présent dans la valeur<br /> </td> 
   <td> IsBitSet(&lt;identifiant&gt;, &lt;flag&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>IsEmptyString</strong><br /> </td> 
   <td> Renvoie la valeur 2 si la chaîne 1 est vide, sinon renvoie la valeur 3<br /> </td> 
   <td> IsEmptyString(&lt;valeur 1&gt;, &lt;valeur 2&gt;, &lt;valeur 3&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>NoNull</strong><br /> </td> 
   <td> Renvoie la chaîne vide si l'argument n'a pas de valeur (null)<br /> </td> 
   <td> NoNull(&lt;valeur&gt;)<br /> </td>   
  </tr> 
  <tr> 
   <td> <strong>RowId</strong><br /> </td> 
   <td> Renvoie le numéro de la ligne<br /> </td> 
   <td> RowId<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>SetBit</strong><br /> </td> 
   <td> Force le Flag dans la valeur<br /> </td> 
   <td> SetBit(&lt;identifiant&gt;, &lt;flag&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToBoolean</strong><br /> </td> 
   <td> Convertit un nombre en booléen<br /> </td> 
   <td> ToBoolean(&lt;nombre&gt;)<br /> </td>   
  </tr> 
  <tr> 
   <td> <strong>When</strong><br /> </td> 
   <td> Renvoie la valeur 1 si l’expression est vraie. Sinon, renvoie la valeur 2 (ne peut être utilisée qu’en paramètre de la fonction Case).<br /> </td> 
   <td> When(&lt;condition&gt;, &lt;valeur 1&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

**Fonctions de fenêtrage**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Nom</strong><br /> </td> 
   <td> <strong>Description</strong><br /> </td> 
   <td> <strong>Syntaxe</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Desc</strong><br /> </td> 
   <td> Applique un tri descendant<br /> </td> 
   <td> Desc(&lt;valeur 1&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>OrderBy</strong><br /> </td> 
   <td> Trie le résultat au sein de la partition<br /> </td> 
   <td> OrderBy(&lt;valeur 1&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>PartitionBy</strong><br /> </td> 
   <td> Partitionne le résultat d'une requête sur une table<br /> </td> 
   <td> PartitionBy(&lt;valeur 1&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>RowNum</strong><br /> </td> 
   <td> Génère un numéro de ligne en fonction de la partition de la table et d'un ordre de tri.<br /> </td> 
   <td> RowNum(PartitionBy(&lt;valeur 1&gt;), OrderBy(&lt;valeur 1&gt;))<br /> </td> 
  </tr> 
 </tbody> 
</table>
