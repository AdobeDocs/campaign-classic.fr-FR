---
title: A propos des workflows
seo-title: A propos des workflows
description: A propos des workflows
seo-description: null
page-status-flag: never-activated
uuid: 19adb0e5-042d-47a0-9f92-24e4b3045dbe
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: introduction
discoiquuid: 868940d1-f19d-4e9a-bffa-8654abb4441c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# A propos des workflows{#about-workflows}

Adobe Campaign intègre un module de workflow qui propose une interface de contrôle centralisée de l&#39;ensemble des opérations et processus. Le module de workflow permet d&#39;automatiser et de modéliser les différentes tâches des modules du serveur applicatif. Cet environnement graphique complet permet de construire des processus englobant segmentation, exécution de campagnes, manipulations de fichiers, validations, etc. Le moteur de workflow exécute et assure le suivi des processus.

Un workflow permet par exemple de télécharger un fichier depuis un serveur, de le décompresser et d&#39;importer ses enregistrements dans la base de données Adobe Campaign.

Un workflow peut également faire intervenir des opérateurs afin de notifier ou valider une opération ou faire un choix. Ainsi, il est possible de créer une action de diffusion, d&#39;assigner une tâche à un ou plusieurs opérateurs qui seront chargés de saisir son contenu ou spécifier sa cible, puis de faire valider le BAT avant de démarrer la diffusion.

Les workflows interviennent dans différents contextes et à différentes étapes du processus de gestion des campagnes.

Ainsi, Adobe Campaign utilise des workflows pour :

* Exécutez des campagnes de ciblage. For more on this, refer to [Implementation steps](../../workflow/using/building-a-workflow.md#implementation-steps-).
* Créez des campagnes : pour chaque campagne, l’onglet **[!UICONTROL Processus]** vous permet de créer la cible et les livraisons. For more on this, refer to [Campaign workflows](../../workflow/using/building-a-workflow.md#campaign-workflows).
* Exécuter des processus techniques : nettoyage, collecte des informations de suivi ou calculs provisoires. For more on this, refer to [Technical workflows](../../workflow/using/building-a-workflow.md#technical-workflows).

Un workflow peut désigner à la fois une définition de procédure (le modèle de workflow : une représentation de ce qui est censé se produire) et une instance de cette procédure (une instance de workflow : une représentation de ce qui est en train de se produire).

Le modèle de workflow décrit les différentes tâches à effectuer et la façon de les enchaîner. Les modèles de tâches sont appelés des activités et sont représentées par des icônes. Elles sont reliées entre elles par des transitions.

![](assets/example1.png)

Chaque workflow comprend :

* **[!UICONTROL Activités]**

   Une activité décrit un modèle de tâche. Il existe différents types d&#39;activités, représentés sur le diagramme par des icônes. Chaque type possède des propriétés communes et des propriétés spécifiques. Par exemple, si toutes les activités ont un nom et un libellé, seule l&#39;activité **[!UICONTROL Validation]** a une assignation.

   Dans un diagramme de workflow, une même activité peut engendrer plusieurs tâches, notamment en cas de boucle ou d&#39;actions récurrentes (périodiques).

   Toutes les activités de workflow sont répertoriées dans [cette section](../../workflow/using/about-activities.md), notamment les cas pratiques et les exemples.

* **[!UICONTROL Transitions]**

   Les transitions permettent de relier entres elles les activités et de définir leur ordre d&#39;enchaînement. Une transition relie une activité source à une activité destination. Il existe différents types de transitions, qui dépendent de l&#39;activité source. Certaines transitions possèdent des paramètres supplémentaires tels qu&#39;une durée, une condition ou un filtre.

   Une transition est flottante si elle n&#39;est pas rattachée à une activité destination. Les transitions flottantes apparaissent en orange et la pointe de leur flèche est remplacée par un losange.

   >[!NOTE]
   >
   >Un workflow contenant des transitions flottantes peut être exécuté : l&#39;exécution générera un avertissement et sera suspendue lors de l&#39;activation d&#39;une telle transition, mais aucune erreur ne sera générée. Il est ainsi possible de démarrer un workflow sans en avoir terminé la conception et de le compléter au fur et à mesure.

   Pour plus d&#39;informations sur la création d&#39;un workflow, consultez [cette section](../../workflow/using/building-a-workflow.md).

* **[!UICONTROL Tables de travail]**

   La table de travail contient l&#39;ensemble des informations portées par la transition. Ainsi, chaque workflow utilise plusieurs tables de travail. Les données véhiculées dans ces tables peuvent être accédées et utilisées tout au long du cycle de vie du workflow, sous réserve qu&#39;elles ne soient pas purgées. En effet, les tables inutiles sont purgées à chaque passivation du workflow, et potentiellement en cours d&#39;exécution pour les plus volumineuses afin de ne pas surcharger le serveur.

   Pour plus d&#39;informations sur les données de workflow et les tables, consultez [cette section](../../workflow/using/how-to-use-workflow-data.md).

