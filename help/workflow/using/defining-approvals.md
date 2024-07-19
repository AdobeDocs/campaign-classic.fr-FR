---
product: campaign
title: Définition des validations
description: Les validations permettent à des opérateurs de prendre des décisions à certaines étapes dʼun workflow ou de confirmer la poursuite dʼun traitement.
feature: Approvals
exl-id: 4d413d51-ae5d-4e5e-bfaf-4160a6075281
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '872'
ht-degree: 100%

---

# Définition des validations {#defining-approvals}



Les validations permettent à des opérateurs de prendre des décisions à certaines étapes d&#39;un workflow ou de confirmer la poursuite d&#39;un traitement.

Un message est envoyé à un groupe d&#39;opérateurs et le workflow attend une réponse pour poursuivre le traitement qui suit la validation. Le workflow n&#39;est pas bloqué et peut effectuer d&#39;autres opérations en l&#39;attente d&#39;une réponse. Il peut donc, par exemple, y avoir plusieurs validations simultanées en attente.

Une validation peut proposer plusieurs choix : l&#39;opérateur devra sélectionner une option parmi les choix possibles. Cependant, il est possible de n&#39;autoriser qu&#39;un seul choix dans le but de soumettre une tâche à réaliser à un opérateur, par exemple effectuer un ciblage : l&#39;opérateur répond lorsque la tâche est réalisée (puis le processus se poursuit). L&#39;exemple ci-dessous illustre les deux types de validations :

![](assets/validation-1.png)

Dans les opérations, toutes les étapes qui nécessitent une validation fonctionnent sur le même principe.

![](assets/validation-1-in-op.png)

Consultez des exemples de validations dans [cette section](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries).

Pour répondre, l&#39;opérateur dispose de deux modes : valider via la page web dont l&#39;URL est fournie dans l&#39;email envoyé, ou valider directement depuis la console.

>[!NOTE]
>
>Une fois la réponse enregistrée, elle ne peut plus être modifiée.

## Validations par e-mail {#sending-emails}

Il est possible de recevoir un message de validation qui contient un lien vers une page web permettant de répondre. Pour le recevoir l&#39;opérateur ciblé doit renseigner son adresse e-mail dans son profil. Dans le cas contraire, il devra passer par la console pour répondre.

La gestion des opérateurs est présentée dans cette [section](../../platform/using/access-management.md).

Les e-mails de validation sont envoyés en continu. Le modèle de diffusion par défaut est **[!UICONTROL notifyAssignee]** : il est enregistré dans le dossier **[!UICONTROL Administration > Gestion de campagne > Modèles des diffusions techniques]**. Ce scénario peut être personnalisé. Il est également recommandé de faire une copie et de modifier les modèles pour chaque activité.

Les diffusions créées depuis ce modèle sont stockées dans le dossier **[!UICONTROL Administration > Exploitation > Objets créés automatiquement > Diffusions techniques > Notifications de workflow]**.

## Validation depuis la console {#approval-via-the-console}

Dans les opérations, les éléments à valider sont affichés dans le tableau de bord de l&#39;opération.

Pour les workflows techniques, les tâches que l&#39;utilisateur peut valider sont accessibles depuis l&#39;arborescence en sélectionnant le dossier **[!UICONTROL Administration > Exploitation > Objets créés automatiquement > Validations en attente]**.

![](assets/validation-node.png)

## Groupes {#groups}

Une validation est assignée à un groupe d&#39;opérateurs, un opérateur unique ou un ensemble d&#39;opérateurs sélectionnés au travers d&#39;une condition de filtrage.

1. Pour une validation simple, la tâche est terminée dès qu&#39;un opérateur a répondu. Tout autre opérateur qui essayera de répondre recevra alors un message lui signalant que quelqu&#39;un d&#39;autre a déjà répondu.
1. Pour les validations multiples, voir la section [Validation multiple](#multiple-approval).

Les groupes d&#39;opérateurs destinés aux validations doivent être conçus comme des rôles ou des fonctions plutôt que des personnes nommées. Par exemple, un groupe &quot;Responsable budget campagne&quot; est plus pertinent que &quot;Equipe Martine&quot;. Il est conseillé d&#39;avoir toujours au moins deux personnes dans un groupe pour valider une tâche, afin qu&#39;en cas d&#39;absence, une personne puisse toujours répondre.

## Expirations {#expirations}

Les expirations sont des transitions spécifiques utilisées dans différents types d&#39;activité, et en particulier dans les validations. Vous pouvez utiliser une expiration pour déclencher une action après un certain temps sans réponse. Les expirations peuvent également être utilisées, par exemple, pour continuer le workflow et affecter une validation à un autre groupe.

Le deuxième onglet des propriétés de l&#39;activité de validation permet de définir une ou plusieurs expirations. En effet, vous pouvez définir plusieurs types d&#39;expiration.

![](assets/expiration.png)

Pour ajouter une nouvelle expiration, cliquez sur le bouton **[!UICONTROL Ajouter]**. Une transition est ajoutée pour chacune des expirations créées. Vous pouvez :

* soit modifier les paramètres usuels directement depuis la liste en cliquant sur une cellule (ou en appuyant sur la touche F2),
* soit éditer l&#39;expiration en cliquant sur le bouton **[!UICONTROL Détail...]**.

>[!NOTE]
>
>Il n&#39;est pas nécessaire d&#39;ordonner les expirations, elles seront traitées par ordre chronologique.

L&#39;option **[!UICONTROL Ne pas terminer la tâche]** laisse la validation active une fois le délai expiré. Ce mode de fonctionnement permet de gérer des relances tout en laissant la validation active : les opérateurs ont toujours la possibilité de répondre. Cette option est désactivée par défaut : lorsque le délai est expiré la tâche est terminée et les opérateurs ne peuvent plus répondre.

Vous pouvez créer quatre types d&#39;expirations :

* **Délai après le début de la tâche**: l&#39;expiration est calculée en ajoutant une durée que vous spécifiez à la date d&#39;activation de la validation.
* **Délai après une date donnée** : l&#39;expiration est calculée en ajoutant une durée à une date que vous spécifiez.
* **Délai avant une date donnée** : l&#39;expiration est calculée en soustrayant une durée à une date que vous spécifiez.
* **Expiration calculée par script** : l&#39;expiration est calculée à partir d&#39;un script JavaScript.

  L&#39;exemple suivant calcule une expiration 24 heures avant la date de démarrage d&#39;une diffusion (identifiée par **vars.deliveryId**) :

  ```
  var delivery = nms.delivery.get(vars.deliveryId)
  var expiration = delivery.scheduling.contactDate
  var oneDay = 1000*60*60*24
  expiration.setTime(expiration.getTime() - oneDay)
  return expiration
  ```

## Validation multiple {#multiple-approval}

La validation multiple permet à tous les opérateurs validants de répondre. Une transition est activée pour chaque réponse.

La validation multiple est utile pour des mécanismes de votes ou de sondages. Il est possible de compter les réponses, puis de traiter le résultat du vote après un délai donné en ajoutant une expiration.

## Droits requis {#required-rights}

Les opérateurs d&#39;un groupe doivent avoir au minimum les droits suivants pour répondre à une demande de validation :

* Droit en lecture sur le workflow.
* Droit en lecture et en écriture sur le dossier des tâches à valider.

Le groupe &#39;Exécution des workflows&#39; possède ces droits. Pour qu&#39;un opérateur puisse répondre à une demande de validation, il suffit donc de l&#39;ajouter à ce groupe.
