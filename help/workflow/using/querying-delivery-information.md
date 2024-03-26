---
product: campaign
title: Requête sur les informations de diffusion
description: Découvrez comment interroger les informations diffusion
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
feature: Query Editor, Workflows
exl-id: b699b064-1287-41c9-8d94-1c1aa2c145ab
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '1559'
ht-degree: 55%

---

# Informations sur la diffusion de requêtes {#querying-delivery-information}



## Nombre de clics pour une diffusion spécifique {#number-of-clicks-for-a-specific-delivery}

Dans cet exemple, vous allez rechercher le nombre de clics des destinataires, sur une diffusion spécifique. Ces clics sont rapportés grâce aux logs de tracking des destinataires, sur une période donnée. Le destinataire va être identifié au moyen de son adresse email. Cette requête utilise la table **[!UICONTROL Logs de tracking des destinataires]**.

* Quelle table doit-on sélectionner ?

  La table des logs de tracking des destinataires (**[!UICONTROL nms:trackingLogRcp]**).

* Quels sont les champs à sélectionner en colonne de sortie ?

  Clé primaire (avec comptage) et Email.

* En fonction de quels critères seront filtrées les informations ?

  En fonction d&#39;une période précise et en fonction d&#39;un élément du libellé de diffusion.

Pour réaliser cet exemple, les étapes sont les suivantes :

1. Ouvrez le **[!UICONTROL Requêteur générique]** et sélectionnez le schéma **[!UICONTROL Logs de tracking des destinataires]**.

   ![](assets/query_editor_tracklog_05.png)

1. Dans le **[!UICONTROL Données à extraire]** , nous voulons créer un agrégat pour collecter des informations. Pour cela, ajoutez la clé primaire (située au-dessus de la clé principale). **[!UICONTROL Logs de tracking des destinataires]** element) : Le nombre de logs de tracking est effectué sur cet élément **[!UICONTROL Clé Principal]** champ . L’expression modifiée sera **[!UICONTROL x=count(clé primaire)]**. Il relie la somme des différents logs de tracking à une seule adresse email.

   Pour cela :

   * Cliquez sur le bouton **[!UICONTROL Ajouter]** à droite de l’icône **[!UICONTROL Colonnes de sortie]** champ . Dans le **[!UICONTROL Type de formule]** , sélectionnez l’option **[!UICONTROL Editer la formule à partir d&#39;une expression]** et cliquez sur **[!UICONTROL Suivant]**. Dans le **[!UICONTROL Champ à sélectionner]** fenêtre, cliquez sur **[!UICONTROL Sélection avancée]**.

     ![](assets/query_editor_tracklog_06.png)

   * Dans la fenêtre **[!UICONTROL Type de formule]**, réalisez un traitement sur la fonction d&#39;agrégat. Ce traitement sera le comptage d&#39;une clé primaire.

     Sélectionnez **[!UICONTROL Traitement sur une fonction d&#39;agrégat]** dans le champ **[!UICONTROL Agrégat]**. Cliquez sur l&#39;option **[!UICONTROL Comptage]**.

     ![](assets/query_editor_nveau_18.png)

     Cliquez sur **[!UICONTROL Suivant]**.

   * Sélectionnez la variable **[!UICONTROL Clé Principal (@id)]** champ . La variable **[!UICONTROL count (clé primaire)]** La colonne output est configurée.

     ![](assets/query_editor_nveau_19.png)

1. Sélectionnez l&#39;autre champ à afficher en colonne de sortie. Dans le **[!UICONTROL Champs disponibles]** , ouvrez la colonne **[!UICONTROL Destinataire]** noeud et choisissez **[!UICONTROL Email]**. Vérifiez les **[!UICONTROL Groupe]** à **[!UICONTROL Oui]** pour regrouper les logs de tracking par adresse email : ce groupe relie chaque log à son destinataire.

   ![](assets/query_editor_nveau_20.png)

1. Paramétrez le tri des colonnes afin que les destinataires les plus actifs (avec le plus de logs de tracking) s&#39;affichent en premier. Vérifier **[!UICONTROL Oui]** dans le **[!UICONTROL Tri descendant]** colonne .

   ![](assets/query_editor_nveau_64.png)

1. Vous devez ensuite filtrer sur les logs qui vous intéressent, c&#39;est-à-dire ceux récents de moins de 15 jours et relatifs à des diffusions portant sur les Soldes.

   Pour cela :

   * Configurer le filtrage des données Pour ce faire, sélectionnez **[!UICONTROL Conditions de filtrage]** puis cliquez sur **[!UICONTROL Suivant]**.

     ![](assets/query_editor_nveau_22.png)

   * Récupérez les logs de tracking d&#39;une diffusion spécifique et sur une période donnée. Pour cela, utilisez trois conditions de filtrage : deux conditions de date pour situer la période recherchée entre 15 jours avant la date courante et la veille de la date courante, et une autre condition pour restreindre la recherche à une diffusion particulière.

     Dans le **[!UICONTROL Elément cible]** paramétrez la date de prise en compte des logs de tracking. Cliquez sur **[!UICONTROL Ajouter]**. Une ligne de condition s’affiche. Modifiez la variable **[!UICONTROL Expression]** en cliquant sur **[!UICONTROL Expression d’édition]** de la fonction Dans le **[!UICONTROL Champ à sélectionner]** fenêtre, choisissez **[!UICONTROL Date (@logDate)]**.

     ![](assets/query_editor_nveau_23.png)

     Sélectionnez la variable **[!UICONTROL supérieur à]** de l’opérateur. Dans le **[!UICONTROL Valeur]** colonne, cliquez sur **[!UICONTROL Expression d’édition]**, et dans la variable **[!UICONTROL Type de formule]** fenêtre, sélectionnez **[!UICONTROL Traitement des dates]**. Enfin, **[!UICONTROL Date courante moins n jours]**, saisissez &quot;15&quot;.

     Cliquez sur **[!UICONTROL Terminer]**.

     ![](assets/query_editor_nveau_24.png)

   * Pour sélectionner la date de fin de la recherche du log de tracking, créez une seconde condition en cliquant sur **[!UICONTROL Ajouter]**. Dans le **[!UICONTROL Expression]** colonne, choisissez **[!UICONTROL Date (@logDate)]** encore une fois.

     Sélectionnez la variable **[!UICONTROL inférieur à]** de l’opérateur. Dans le **[!UICONTROL Valeur]** colonne, cliquez sur **[!UICONTROL Expression d’édition]**. Pour le traitement des dates, accédez au **[!UICONTROL Type de formule]** , saisissez &quot;1&quot; dans **[!UICONTROL Date courante moins n jours]**.

     Cliquez sur **[!UICONTROL Terminer]**.

     ![](assets/query_editor_nveau_65.png)

     L&#39;intervalle de temps est configuré. La troisième condition de filtrage est à paramétrer : elle permettra d&#39;identifier la diffusion sur laquelle porte la recherche.

   * Cliquez sur le bouton **[!UICONTROL Ajouter]** pour créer une autre condition de filtrage. Dans le **[!UICONTROL Expression]** colonne, cliquez sur **[!UICONTROL Expression d’édition]**. Dans le **[!UICONTROL Champ à sélectionner]** fenêtre, choisissez **[!UICONTROL Libellé]** dans le **[!UICONTROL Diffusion]** noeud .

     Cliquez sur **[!UICONTROL Terminer]**.

     ![](assets/query_editor_nveau_66.png)

     Recherchez une diffusion contenant le mot &quot;soldes&quot;. Comme vous ne vous souvenez pas de son libellé exact, vous pouvez choisir la variable **[!UICONTROL contains]** et saisissez &quot;soldes&quot; dans la variable **[!UICONTROL Valeur]** colonne .

     ![](assets/query_editor_nveau_25.png)

1. Dans la fenêtre **[!UICONTROL Formatage des données]**, cliquez sur **[!UICONTROL Suivant]** : aucun formatage n&#39;est nécessaire dans notre exemple.
1. Dans la fenêtre **[!UICONTROL Prévisualisation des données]**, cliquez sur **[!UICONTROL Lancer la prévisualisation des données]** afin d&#39;obtenir le nombre de logs de tracking de chaque destinataire sur la diffusion.

   Le résultat des logs de tracking est présenté dans un ordre descendant.

   ![](assets/query_editor_tracklog_04.png)

   Le nombre de logs le plus élevé pour un utilisateur est de 11 sur cette diffusion. 6 utilisateurs différents ont ouvert l&#39;email de diffusion ou cliqué sur un lien de l&#39;email.

## Destinataires n&#39;ayant ouvert aucune diffusion {#recipients-who-did-not-open-any-delivery}

Dans cet exemple, nous voulons filtrer les destinataires n&#39;ayant pas ouvert d&#39;email au cours des 7 derniers jours.

Pour réaliser cet exemple, les étapes sont les suivantes :

1. Placez une activité **[!UICONTROL Requête]** dans un workflow, puis ouvrez-la.
1. Cliquez sur **[!UICONTROL Edition de la requête]** et définissez les dimensions de ciblage et de filtrage sur **[!UICONTROL Destinataires]**.

   ![](assets/query_recipients_1.png)

1. Sélectionnez **[!UICONTROL Critères de filtrage]**, puis cliquez sur **[!UICONTROL Suivant]**.
1. Cliquez sur le bouton **[!UICONTROL Ajouter]** et sélectionnez **[!UICONTROL Logs de tracking]**.
1. Définissez l&#39;**[!UICONTROL Opérateur]** de l&#39;expression **[!UICONTROL Logs de tracking]** sur **[!UICONTROL n&#39;existent pas tel que]**.

   ![](assets/query_open_1.png)

1. Ajoutez une autre expression. Sélectionner **[!UICONTROL Type]** dans le **[!UICONTROL URL]** catégorie.
1. Définissez ensuite son **[!UICONTROL Opérateur]** sur **[!UICONTROL égal à]** et sa **[!UICONTROL Valeur]** sur **[!UICONTROL Ouverte]**.

   ![](assets/query_open_2.png)

1. Ajoutez une autre expression et sélectionnez **[!UICONTROL Date]**. **[!UICONTROL Opérateur]** doit être défini sur **[!UICONTROL sur ou après]**.

   ![](assets/query_open_3.png)

1. Pour définir la valeur sur les 7 derniers jours, cliquez sur le bouton **[!UICONTROL Editer l&#39;expression]** dans le champ **[!UICONTROL Valeur]**.
1. Dans la catégorie **[!UICONTROL Fonction]**, sélectionnez **[!UICONTROL Date courante moins n jours]** et ajoutez le nombre de jours à cibler. Dans le cas présent, nous voulons cibler les 7 derniers jours.

   ![](assets/query_open_4.png)

Votre transition sortante contiendra les destinataires n&#39;ayant pas ouvert d&#39;email au cours des 7 derniers jours.

Si, au contraire, vous souhaitez filtrer les destinataires ayant ouvert au moins un email, votre requête doit être la suivante. Notez que, dans ce cas, la **[!UICONTROL Dimension de filtrage]** doit être définie sur **[!UICONTROL Logs de tracking (destinataires)]**.

![](assets/query_open_5.png)

## Destinataires ayant ouvert une diffusion {#recipients-who-have-opened-a-delivery}

L&#39;exemple suivant montre comment cibler les profils ayant ouvert une diffusion au cours des 2 dernières semaines :

1. Pour cibler les profils ayant ouvert une diffusion, vous devez utiliser les logs de tracking. ils sont stockés dans une table liée : vous devez d&#39;abord sélectionner cette table dans la liste déroulante du **[!UICONTROL Dimension de filtrage]** , comme illustré ci-dessous :

   ![](assets/s_advuser_query_sample1.0.png)

1. Au niveau des conditions de filtrage, cliquez sur le bouton **[!UICONTROL Expression d’édition]** icône des critères affichée dans la sous-arborescence des logs de tracking. Sélectionnez la variable **[!UICONTROL Date]** champ .

   ![](assets/s_advuser_query_sample1.1.png)

   Cliquez sur **[!UICONTROL Terminer]** pour valider la sélection.

   Afin de ne récupérer que les logs de tracking postérieurs aux 15 derniers jours, vous devez sélectionner l&#39;opérateur **[!UICONTROL Supérieur à]**.

   ![](assets/s_advuser_query_sample1.4.png)

   Cliquez ensuite sur le bouton **[!UICONTROL Expression d’édition]** dans le **[!UICONTROL Valeur]** pour définir la formule de calcul à appliquer. Sélectionnez la variable **[!UICONTROL Date courante moins n jours]** formule et saisissez 15 dans le champ correspondant.

   ![](assets/s_advuser_query_sample1.5.png)

   Cliquez sur le bouton **[!UICONTROL Terminer]** de la fenêtre de formule. Dans la fenêtre de filtrage, cliquez sur le bouton **[!UICONTROL Aperçu]** pour vérifier les critères de ciblage.

   ![](assets/s_advuser_query_sample1.6.png)

## Filtrage du comportement des destinataires après une diffusion {#filtering-recipients--behavior-folllowing-a-delivery}

Dans un workflow, la variable **[!UICONTROL Requête]** et **[!UICONTROL Partage]** permettent de sélectionner un comportement suite à une diffusion précédente. Cette sélection est réalisée à partir du **[!UICONTROL Destinataire de la diffusion]** filtre.

* But de l&#39;exemple

  Dans un workflow de diffusion, plusieurs méthodes permettent de suivre une première communication email. Ce type d’opération implique l’utilisation de la variable **[!UICONTROL Partage]** de la boîte.

* Contexte

  Une diffusion &quot;Offre sports d&#39;été&quot; est envoyée. Quatre jours après l&#39;envoi, deux autres diffusions sont renvoyées. L&#39;une est &quot;Offre sports nautiques&quot;, l&#39;autre est une relance de la première diffusion &quot;Offre sports d&#39;été&quot;.

  La diffusion &quot;Offre sports nautiques&quot; est envoyée aux destinataires qui ont cliqué sur la thématique &quot;sports nautiques&quot; dans la première diffusion. Ces clics montrent l&#39;intérêt des destinataires. Ils peuvent donc être orientés vers des offres similaires. En revanche, les destinataires qui n&#39;ont pas cliqué dans l&#39;email &quot;Offre sports d&#39;été&quot; sont relancés avec le même contenu.

Les étapes suivantes indiquent comment paramétrer la boîte **[!UICONTROL Partage]** en y intégrant deux comportements différents :

1. Insérez la boîte **[!UICONTROL Partage]** dans le workflow. Elle va répartir les destinataires de la première diffusion vers une des deux diffusions suivantes. Cette répartition est faite en fonction des critères de filtrage liés aux comportements des destinataires dans la première diffusion.

   ![](assets/query_editor_ex_09.png)

1. Ouvrez le **[!UICONTROL Partage]** de la boîte. Dans le **[!UICONTROL Général]** , saisissez un libellé : **Partage en fonction du comportement** par exemple.

   ![](assets/query_editor_ex_04.png)

1. Dans le **[!UICONTROL Sous-ensembles]** , définissez la première branche de partage. Par exemple, saisissez la variable **Cliqué** libellé de cette branche.
1. Sélectionnez la variable **[!UICONTROL Ajouter une condition de filtrage sur la population entrante]** . Cliquez sur **[!UICONTROL Modifier]**.
1. Dans la fenêtre **[!UICONTROL Dimension de ciblage et de filtrage]**, double-cliquez sur le filtre **[!UICONTROL Destinataires d&#39;une diffusion]**.

   ![](assets/query_editor_ex_05.png)

1. Dans la fenêtre **[!UICONTROL Elément de la cible]**, sélectionnez le comportement à appliquer sur cette branche : **[!UICONTROL Les destinataires ayant cliqué (email)]**.

   En dessous, sélectionnez l&#39;option **[!UICONTROL Diffusion spécifiée par la transition]**. Cette fonctionnalité va automatiquement récupérer les personnes ciblées lors de la première diffusion.

   Il s&#39;agira donc de la diffusion &quot;Offre sports nautiques&quot;.

   ![](assets/query_editor_ex_08.png)

1. Définissez la seconde branche. Cette branche va inclure l&#39;email de relance avec le même contenu que pour la première diffusion. Accédez au **[!UICONTROL Sous-ensembles]** et cliquez sur **[!UICONTROL Ajouter]** pour le créer.

   ![](assets/query_editor_ex_06.png)

1. Un autre sous-onglet s’affiche. Nommez-le &quot;**Ne pas cliquer**&quot;.
1. Cliquez sur **[!UICONTROL Ajouter une condition de filtrage sur la population entrante]**. Cliquez ensuite sur **[!UICONTROL Modifier...]**.

   ![](assets/query_editor_ex_07.png)

1. Cliquez sur **[!UICONTROL Destinataires d&#39;une diffusion]** dans la fenêtre **[!UICONTROL Dimension de ciblage et de filtrage]**.
1. Dans le **[!UICONTROL Elément cible]** , sélectionnez l’option **[!UICONTROL Destinataires n&#39;ayant pas cliqué (email)]** comportement. Sélectionnez la variable **[!UICONTROL Diffusion spécifiée par la transition]** comme pour la dernière branche.

   La boîte **[!UICONTROL Partage]** est maintenant paramétrée.

   ![](assets/query_editor_ex_03.png)

Voici la liste des différents comportements proposés par défaut :

* **[!UICONTROL Tous les destinataires,]**
* **[!UICONTROL Les destinataires des messages envoyés avec succès,]**
* **[!UICONTROL Les destinataires ayant ouvert ou cliqué (email),]**
* **[!UICONTROL Les destinataires ayant cliqué (email),]**
* **[!UICONTROL Les destinataires des messages en échec,]**
* **[!UICONTROL Les destinataires n&#39;ayant ni ouvert ni cliqué (email),]**
* **[!UICONTROL Les destinataires n&#39;ayant pas cliqué (email).]**

  ![](assets/query_editor_ex_02.png)
