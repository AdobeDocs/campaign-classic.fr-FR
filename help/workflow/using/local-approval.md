---
product: campaign
title: Validation en local
description: Validation en local
feature: Workflows
hide: true
hidefromtoc: true
exl-id: 2d9cbfc8-1f99-4b38-8460-77c7c986e9ca
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '700'
ht-degree: 100%

---

# Validation en local{#local-approval}



Intégrée à un workflow de ciblage, l&#39;activité **[!UICONTROL Validation en local]** permet de mettre en place un processus de validation des destinataires avant l&#39;envoi d&#39;une diffusion.

![](assets/local_validation_0.png)

>[!CAUTION]
>
>Pour utiliser cette activité, vous devez acquérir le module Distributed Marketing, qui est une option de Campaign. Vérifiez votre contrat de licence.

Pour un exemple de l’activité **[!UICONTROL Validation en local]** avec un modèle de distribution, consultez la section [Utiliser l’activité Validation en local](using-the-local-approval-activity.md).

Renseignez tout d&#39;abord libellé de l&#39;activité et le champ **[!UICONTROL Action à effectuer]** :

![](assets/local_validation_1.png)

* Sélectionnez l&#39;option **[!UICONTROL Notification pour la validation de la cible]** pour envoyer un email de notification aux responsables locaux, avant la diffusion, afin qu&#39;ils valident les destinataires qui leur sont assignés.

  ![](assets/local_validation_intro_2.png)

* **Requête incrémentale** : vous permet d’effectuer une requête et d’en planifier l’exécution. Pour plus d&#39;informations, consultez la section [Requête incrémentale](incremental-query.md).

  ![](assets/local_validation_intro_3.png)

## Notification pour la validation de la cible {#target-approval-notification}

Dans ce cas, l&#39;activité **[!UICONTROL Validation en local]** se place entre le ciblage en amont et la diffusion :

![](assets/local_validation_2.png)

Les champs à renseigner dans le cas d&#39;une notification pour la validation de la cible sont les suivants :

![](assets/local_validation_3.png)

* **[!UICONTROL Contexte de distribution]** : sélectionnez l’option **[!UICONTROL Spécifié dans la transition]** si vous utilisez une activité de type **[!UICONTROL Partage]** pour limiter la population ciblée. Dans ce cas, le modèle de répartition est renseigné dans l’activité de partage. Si vous ne limitez pas la population ciblée, sélectionnez ici l’option **[!UICONTROL Explicite]** et renseignez le modèle de répartition dans le champ **[!UICONTROL Répartition des données]**.

  Pour plus d’informations sur la création d’un modèle de distribution de données, voir [Limiter le nombre d&#39;enregistrements des sous-ensembles par répartition de données](split.md#limiting-the-number-of-subset-records-per-data-distribution).

* **[!UICONTROL Gestion de la validation :]**

   * Sélectionnez le modèle de diffusion et l’objet qui seront utilisés pour l’e-mail de notification. Un modèle par défaut est disponible : **[!UICONTROL Notification de validation locale]**. Vous pouvez également ajouter une description qui apparaîtra au-dessus des listes de personnes destinataires dans les notifications d’approbation et de commentaires.
   * Définissez le **[!UICONTROL Type de validation]**, qui correspond à la date limite de validation (date ou délai à partir du début de la validation). A cette date, le workflow reprend et les destinataires qui n&#39;ont pas été validés ne sont pas pris en compte dans le ciblage. Lorsque les notifications sont envoyées, l&#39;activité est mise en attente afin que les responsables locaux puissent valider leurs contacts.

     >[!NOTE]
     >
     >Par défaut, lorsque la validation débute, l&#39;activité est mise en attente pendant trois jours.

     Vous pouvez également ajouter un ou plusieurs rappels pour informer les personnes responsables locales que l’échéance approche. Pour ce faire, cliquez sur le lien **[!UICONTROL Ajouter un rappel]**.

* **[!UICONTROL Complémentaire]** : L&#39;option **[!UICONTROL Générer le complémentaire]** permet de générer un second ensemble contenant toutes les cibles non validées.

  >[!NOTE]
  >
  >Par défaut, cette option est désactivée.

## Rapport de retour de diffusion {#delivery-feedback-report}

Dans ce cas, l&#39;activité **[!UICONTROL Validation en local]** se place après la diffusion :

![](assets/local_validation_4.png)

Les champs à renseigner dans le cas d&#39;un rapport de retour de diffusion sont les suivants :

![](assets/local_validation_workflow_4.png)

* Sélectionnez l’option **[!UICONTROL Spécifié dans la transition]** si la diffusion a été saisie au cours d’une activité précédente. Sélectionnez **[!UICONTROL Explicite]** pour définir la diffusion dans l’activité d’approbation locale.
* Sélectionnez le modèle de diffusion et l’objet de l’e-mail de notification. Il existe un modèle par défaut : **[!UICONTROL Notification de validation locale]**.

## Exemple : validation de la diffusion d&#39;un workflow {#example--approving-a-workflow-delivery}

Cet exemple montre comment configurer un processus de validation pour une diffusion de workflow. Pour plus d’informations sur la création de workflows de diffusion, voir la section [Exemple : workflow de diffusion](delivery.md#example--delivery-workflow).

Pour valider un envoi, un opérateur dispose de deux modes : il peut utiliser la page web dont l’URL est fournie dans l’e-mail envoyé, ou valider directement depuis la console.

* Validation Web

  L&#39;email adressé aux opérateurs du groupe Administrateur permet de valider la cible de l&#39;envoi. Le message reprend le texte défini en remplaçant l&#39;expression JavaScript par la valeur calculée (ici &#39;574&#39;).

  Pour valider l&#39;envoi, cliquez sur le lien correspondant et connectez-vous à la console Adobe Campaign.

  ![](assets/new-workflow-valid-webaccess.png)

  Sélectionnez votre choix et cliquez sur le bouton **[!UICONTROL Soumettre]**.

  ![](assets/new-workflow-valid-webaccess-confirm.png)

* Validation depuis la console

  Dans l&#39;arborescence, le noeud **[!UICONTROL Administration > Exploitation > Objets créés automatiquement > Validations en attente]** contient la liste des tâches à valider par l&#39;opérateur actuellement connecté. La liste doit afficher une ligne. Double-cliquez sur la ligne pour répondre. La fenêtre suivante s&#39;affiche :

![](assets/new-workflow-7.png)

Sélectionnez l&#39;option **Oui**, puis cliquez sur le bouton **[!UICONTROL Valider]**. Un message vous informe que la réponse est enregistrée.

Revenez sur l&#39;écran des workflows : au bout de quelques dizaines de secondes, le diagramme se présente comme suit:

![](assets/new-workflow-8.png)

Le workflow a exécuté la tâche **[!UICONTROL Agir sur une diffusion]**, qui consiste ici à démarrer la diffusion précédemment créée, puis est arrivé jusqu&#39;à la fin. Le workflow s&#39;est terminé avec succès.
