---
product: campaign
title: Simulation de campagnes
description: Prise en main des simulations de campagnes
role: User, Developer
feature: Campaigns
hide: true
exl-id: 709c64a8-34bf-43fa-a820-238295fb26b8
TQID: https://experienceleague.adobe.com/RRjCa2LDMEuCoh-u4xGb4lZZpNOxPk4IjTMa-iSPUlg
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
subfeature_v2:
  - id: e5fb657f-3c0a-4fcc-9980-3589a23ab4de
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 1393
ht-degree: 78%

---

# Simulation de campagnes{#campaign-simulations}

## À propos des simulations {#about-simulations}

Campaign Optimization permet de tester l&#39;efficacité d&#39;un plan de campagne à l&#39;aide de simulations. Vous pouvez ainsi mesurer le succès potentiel d’une campagne : le chiffre d’affaires généré, le volume de la cible en fonction des règles de typologie appliquées, etc.

La simulation permet de suivre et de comparer l&#39;impact des diffusions les unes par rapport aux autres.

>[!NOTE]
>
>Les diffusions préparées en mode Test n&#39;ont pas d&#39;impact les unes sur les autres, par exemple lors de l&#39;évaluation d&#39;une opération dans le cadre du marketing distribué, ou tant que l&#39;inscription des diffusions au calendrier prévisionnel n&#39;est pas validée.\
>Cela signifie que les règles de pression et de capacité ne s&#39;appliquent qu&#39;aux diffusions dans le mode **[!UICONTROL Estimation de la cible et personnalisation des messages]**. Les diffusions des modes **[!UICONTROL Estimation et validation de la cible prévisionnelle]** et **[!UICONTROL Évaluation de la cible]** ne sont pas prises en compte.\
>Le mode de diffusion est sélectionné dans les propriétés de la diffusion, sous l&#39;onglet **[!UICONTROL Typologie]**.

![](assets/simu_campaign_select_delivery_mode.png)

## Configuration dʼune simulation {#setting-up-a-simulation}

### Création dʼune simulation {#creating-a-simulation}

Pour créer une simulation, les étapes sont les suivantes :

1. Ouvrez l’onglet **[!UICONTROL Campagnes]**, cliquez sur le lien **[!UICONTROL Autres choix]** de la section **[!UICONTROL Créer]** et choisissez l’option **[!UICONTROL Simulation]**.

   ![](assets/simu_campaign_opti_01.png)

1. Indiquez le modèle et le nom de la simulation. Cliquez sur le bouton **[!UICONTROL Enregistrer]** pour créer la simulation.

   ![](assets/simu_campaign_opti_02.png)

1. Cliquez sur l&#39;onglet **[!UICONTROL Edition]** pour la paramétrer.

   ![](assets/simu_campaign_opti_edit.png)

1. Dans l&#39;onglet **[!UICONTROL Périmètre]**, indiquez les diffusions à considérer dans cette simulation. Pour cela, cliquez sur le bouton **[!UICONTROL Ajouter]** et indiquez le mode de sélection des diffusions à prendre en compte.

   ![](assets/simu_campaign_opti_edit_scope.png)

   Vous pouvez sélectionner unitairement chaque diffusion ou considérer celles appartenant à une ou plusieurs opérations, programmes ou plans.

   >[!NOTE]
   >
   >Si vous sélectionnez les diffusions d&#39;un plan, d&#39;un programme ou d&#39;une opération, Adobe Campaign peut réactualiser automatiquement la liste des diffusions à prendre en compte à chaque lancement de la simulation. Pour cela, cochez l&#39;option **[!UICONTROL Réactualiser la sélection des diffusions à chaque démarrage de la simulation]**.
   >  
   >Dans le cas contraire, seules les diffusions présentes dans le plan, le programme et la ou les opérations au moment de la création de la simulation seront prises en comptes : les diffusions ajoutées ultérieurement seront ignorées.

   ![](assets/simu_campaign_opti_edit_scope_update.png)

1. Sélectionnez les éléments à inclure dans la portée de la simulation. Si nécessaire, sélectionnez plusieurs éléments à l’aide des touches MAJ et CTRL.

   ![](assets/simu_campaign_opti_edit_scope_select.png)

   Cliquez sur le bouton **[!UICONTROL Terminer]** pour valider la sélection.

   Il est possible de combiner des diffusions sélectionnées manuellement avec celles appartenant à un ou plusieurs plans, programmes ou opérations.

   ![](assets/simu_campaign_opti_edit_scope_save.png)

   Au besoin, vous pouvez utiliser une condition dynamique à partir du lien **[!UICONTROL Modifier la condition dynamique…]**

   Cliquez sur le bouton **[!UICONTROL Enregistrer]** pour valider ce paramétrage.

   >[!NOTE]
   >
   >Seules les diffusions dont la cible a été calculée sont prises en compte dans les calculs des simulations (états : **Cible prête** ou **Prête à être diffusée**).

1. Dans l&#39;onglet **[!UICONTROL Calculs]**, sélectionnez une dimension d&#39;analyse comme, par exemple, le schéma des destinataires.

   ![](assets/simu_campaign_opti_dimension.png)

1. Vous pouvez ensuite ajouter des expressions.

   ![](assets/simu_campaign_opti_dimension_02.png)

### Paramètres d&#39;exécution {#execution-settings}

Dans l&#39;onglet **[!UICONTROL Général]** de la simulation, vous pouvez indiquer ses paramètres d&#39;exécution :

* L&#39;option **[!UICONTROL Planifier l&#39;exécution pour les temps d&#39;arrêt]** permet de différer le lancement de la simulation à une période moins chargée, en fonction du niveau de priorité choisi. Les simulations utilisent d&#39;importantes ressources de base de données, c&#39;est pourquoi les simulations non urgentes doivent être planifiées pour fonctionner la nuit, par exemple.
* La **[!UICONTROL Priorité]** est le niveau appliqué à la simulation pour en différer le déclenchement.
* **[!UICONTROL Enregistrer les requêtes SQL dans le journal]**. Les logs SQL permettent de diagnostiquer une simulation si elle se termine par une erreur. Ils peuvent également vous aider à comprendre pourquoi une simulation est trop lente. Ces messages seront visibles après la simulation dans le sous-onglet **[!UICONTROL Logs SQL]** de l&#39;onglet **[!UICONTROL Suivi]**.

## Exécution dʼune simulation {#executing-a-simulation}

### Démarrage dʼune simulation {#starting-a-simulation}

Une fois le périmètre de la simulation défini, vous pouvez l&#39;exécuter.

Pour cela, ouvrez le tableau de bord de la simulation et cliquez sur le bouton **[!UICONTROL Démarrer la simulation]**.

![](assets/simu_campaign_opti_start.png)

Une fois l&#39;exécution terminée, ouvrez la simulation et cliquez sur l&#39;onglet **[!UICONTROL Résultats]** pour visualiser les cibles calculées pour chacune des diffusions considérées.

![](assets/simu_campaign_opti_results.png)

1. Le sous-onglet **[!UICONTROL Diffusions]** liste les diffusions prises en compte par la simulation. Il présente deux comptages :

   * Le **[!UICONTROL Comptage initial]** correspond à la cible telle qu&#39;elle a été calculée lors de son estimation, au niveau de la diffusion.
   * Le **[!UICONTROL Comptage final]** affiche le nombre de destinataires comptabilisés après l&#39;exécution de la simulation.

     Le delta entre comptage initial et final reflète l&#39;application des différentes règles ou filtrages paramétrés en amont de la simulation.

     Pour comprendre ce calcul, éditez le sous-onglet **[!UICONTROL Exclusions]**.

1. Le sous-onglet **[!UICONTROL Exclusions]** permet de visualiser la répartition des exclusions par diffusions.

   ![](assets/simu_campaign_opti_14.png)

1. Le sous-onglet **[!UICONTROL Alertes]** regroupe tous les messages d&#39;alerte générés lors de la simulation. Des messages d&#39;alerte peuvent être envoyés en cas de surcharge de capacité (par exemple si le nombre de destinataires ciblés dépasse la capacité fixée).
1. Le sous-onglet **[!UICONTROL Exploration des exclusions]** permet de créer un tableau d&#39;analyse des résultats. L’utilisateur doit indiquer des variables sur les axes des abscisses/ordonnées.

   Pour un exemple de création de tableau d&#39;analyse, reportez-vous à la fin de la section [Explorer les résultats](#exploring-results).

### Affichage des résultats {#viewing-results}

#### Journal {#audit}

L&#39;onglet **[!UICONTROL Journal]** sert à suivre l&#39;exécution de la simulation. Le sous-onglet **[!UICONTROL Logs SQL]** est utile aux utilisateurs experts. Il répertorie les logs d&#39;exécution, en langage SQL. Ces logs ne s&#39;affichent que si l&#39;option **[!UICONTROL Enregistrer les requêtes SQL dans le log]** a été sélectionnée dans l&#39;onglet **[!UICONTROL Général]** avant l&#39;exécution de la simulation.

![](assets/simu_campaign_opti_11.png)

#### Exploration des résultats {#exploring-results}

Le sous-onglet **[!UICONTROL Exploration des exclusions]** permet d&#39;analyser les données issues de la simulation.

L&#39;analyse descriptive est présentée dans cette [section](../../reporting/using/about-adobe-campaign-reporting-tools.md).

## Résultats d’une simulation {#results-of-a-simulation}

Les indicateurs présentés dans l&#39;onglet **[!UICONTROL Résultats]** donnent un premier aperçu du résultat de la simulation. **&#x200B;**&#x200B;Pour obtenir une vue plus détaillée des résultats, ouvrez l&#39;onglet **[!UICONTROL Rapports]**.

### Rapports {#reports}

Pour analyser le résultat d&#39;une simulation, éditez les rapports qui lui sont associés: ils présentent les exclusions de la simulation et leurs causes.

Par défaut, les rapports suivants sont proposés :

* **[!UICONTROL Détail des exclusions de la simulation]** : ce rapport propose un tableau détaillé de toutes les causes d&#39;exclusion, pour toutes les diffusions concernées par cette simulation.
* **[!UICONTROL Résumé de la simulation]** : ce rapport résume les volumes de populations exclues par la simulation, dans les différentes diffusions concernées.
* **[!UICONTROL Synthèse des exclusions dues à la simulation]** : ce rapport affiche un tableau des exclusions dues à la simulation, avec la règle de typologie appliquée, et un graphique représentant la proportion d&#39;exclusion par règle.

>[!NOTE]
>
>Vous pouvez créer des rapports et les ajouter aux rapports proposés. Pour plus d’informations, consultez [cette section](../../reporting/using/about-adobe-campaign-reporting-tools.md).

Pour accéder aux rapports, cliquez sur le lien **[!UICONTROL Rapports]** de la simulation visée à partir de son tableau de bord.

![](assets/campaign_opt_reporting_edit_from_board.png)

Vous pouvez également éditer les rapports à partir du lien **[!UICONTROL Rapports]** accessible depuis le tableau de bord de la simulation.

### Comparaison des simulations {#comparing-simulations-}

A nouvelle exécution d&#39;une simulation, le résultat calculé remplace le résultat antérieur : vous ne pouvez pas afficher et comparer les résultats d&#39;une exécution à l&#39;autre.

Pour comparer les résultats, vous devez utiliser des rapports. En effet, Adobe Campaign permet d&#39;enregistrer un historique de rapport pour le ré-afficher ultérieurement. Cet historique est conservé tout au long du cycle de vie des simulations.

**Exemple:**

1. Créez une simulation sur une diffusion à laquelle la typologie **A** est appliquée.
1. Dans l&#39;onglet **[!UICONTROL Rapports]**, éditez un des rapports disponibles, par exemple **[!UICONTROL Détail des exclusions de la simulation]**.
1. Dans la section supérieure droite du rapport, cliquez sur l&#39;icône de création d&#39;un nouvel historique.

   ![](assets/campaign_opt_reporting_create_hist.png)

1. Fermez cette simulation et modifiez le paramétrage de la typologie **A**.
1. Exécutez à nouveau la simulation et comparez le résultat obtenu à celui affiché dans le rapport dont vous avez créé l&#39;historique.

   ![](assets/campaign_opt_reporting_edit_hist.png)

   Vous pouvez enregistrer autant d&#39;historiques de rapports que nécessaire.

### Axes de reporting {#reporting-axes}

L&#39;onglet **[!UICONTROL Calculs]** vous permet de définir des axes de reporting sur la cible. Ces axes seront utilisés lors de l’analyse des résultats (voir [Explorer les résultats](#exploring-results)).

>[!NOTE]
>
>Il est recommandé de définir des axes de calculs dans un modèle de simulation plutôt que dans chaque simulation.\
>Les modèles de simulation sont enregistrés dans le noeud **[!UICONTROL Ressources > Modèles > Modèles de simulation]** de l&#39;arborescence Adobe Campaign.

**Exemple:**

Dans l&#39;exemple suivant, nous allons créer un axe de reporting supplémentaire portant sur le statut du destinataire (&quot;Client&quot;, &quot;Prospect&quot; ou aucun).

1. Pour définir un axe de reporting, sélectionnez la table contenant les informations à traiter dans le champ **[!UICONTROL Dimension d&#39;analyse]**. Cette information est obligatoire.
1. Ici, nous allons sélectionner le champ Segment de la table des destinataires.

   ![](assets/simu_campaign_opti_09.png)

1. Les options disponibles sont les suivantes :

   * **[!UICONTROL Générer les statistiques de recouvrement de la cible]** permet de récupérer toutes les statistiques de recouvrement dans le rapport de simulation. Les chevauchements sont des destinataires ciblés dans au moins deux diffusions au sein d’une simulation.

     >[!IMPORTANT]
     >
     >Le choix de cette option augmente considérablement le temps d&#39;exécution de la simulation.

   * **[!UICONTROL Conserver la table de travail de la simulation]** afin de garder des traces de la simulation.

     >[!IMPORTANT]
     >
     >La conservation systématique de ces tables requiert une capacité de stockage élevée : assurez-vous que la taille de la base de données le permet.

A l&#39;affichage des résultats de la simulation, les informations relatives à l&#39;expression sélectionnée seront affichées dans le sous-onglet **[!UICONTROL Recouvrements]**.

Les recouvrements des cibles de diffusions indiquent les destinataires ciblés dans au moins deux des diffusions d&#39;une simulation.

![](assets/simu_campaign_opti_13.png)

>[!NOTE]
>
>Ce sous-onglet n&#39;est affiché que si l&#39;option **[!UICONTROL Générer les statistiques de recouvrement des cibles]** a été activée.

Les informations relatives aux axes de reporting peuvent être exploitées dans les rapports d&#39;analyse des exclusions, créés sous le sous-onglet **[!UICONTROL Exploration des exclusions]**. Voir à ce sujet la section [Explorer les résultats](#exploring-results).
