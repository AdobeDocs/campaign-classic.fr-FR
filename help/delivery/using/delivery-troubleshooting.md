---
product: campaign
title: Résolution des problèmes liés à lʼenvoi de diffusions
description: En savoir plus sur les performances des diffusions et comment résoudre les problèmes liés à la surveillance des diffusions
badge-v7: label="v7" type="Informative" tooltip="S’applique à Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="S’applique également à Campaign v8"
feature: Monitoring, Deliverability, Troubleshooting
role: User
exl-id: 37b1d7fb-7ceb-4647-9aac-c8a80495c5bf
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '812'
ht-degree: 79%

---

# Résolution des problèmes liés à l&#39;envoi de diffusions {#delivery-troubleshooting}

Cette section répertorie les problèmes courants que vous pouvez rencontrer lors de l’envoi de diffusions et comment les résoudre.

De plus, veillez à suivre les bonnes pratiques et la liste de contrôle détaillée sur [cette page](delivery-performances.md) pour vous assurer que vos diffusions fonctionnent bien.

**Rubriques connexes :**

* [Statuts de diffusion](delivery-statuses.md)
* [Tableau de bord de la diffusion](delivery-dashboard.md)
* [Comprendre les échecs de diffusion](understanding-delivery-failures.md)

## Diffusions lentes {#slow-deliveries}

Après avoir cliqué sur le bouton **[!UICONTROL Envoyer]**, votre diffusion semble prendre plus de temps que d&#39;habitude. Cela peut être dû à différents éléments :

* Certains fournisseurs de messagerie ont peut-être ajouté vos adresses IP à une liste bloquée. Dans ce cas, vérifiez vos broadlogs et consultez [cette section](about-deliverability.md).

* Votre diffusion peut être trop volumineuse pour être traitée rapidement. Cela peut être le cas avec une personnalisation JavaScript élevée ou si votre diffusion pèse plus de 60 Ko. Reportez-vous à Adobe Campaign [Bonnes pratiques de diffusion](delivery-best-practices.md) pour en savoir plus sur les directives relatives au contenu.

* Le MTA Adobe Campaign a peut-être été soumis à une limitation. Celle-ci est due aux éléments suivants :

   * Messages mis en attente (**[!UICONTROL Quota atteint]** message) : les quotas déclarés par les règles MX déclaratives définies dans Campaign ont été atteints. Pour plus d’informations sur ce message, voir [cette page](deliverability-faq.md). Pour en savoir plus sur les règles MX, consultez [cette section](../../installation/using/email-deliverability.md#about-mx-rules).

   * Messages mis en attente (message **[!UICONTROL Contrôle de flux dynamique]**) : le MTA de Campaign a rencontré des erreurs lors de la diffusion des messages pour un FAI donné, ce qui a entraîné un ralentissement afin d’éviter une densité d’erreurs trop importante et une mise sur liste bloquée éventuelle.

* Un problème lié au système peut empêcher les serveurs d’interagir ensemble : l’ensemble du processus d’envoi peut être ainsi ralenti. Vérifiez que les serveurs ne présentent aucun problème de mémoire ou de ressource qui peut impacter Campaign dans le processus de récupération des données de personnalisation par exemple.

## Diffusions planifiées {#scheduled-deliveries-}

Si des diffusions ne s’exécutent pas exactement à la date planifiée, c’est peut-être en raison d’une différence de fuseau horaire entre les serveurs. L’instance de mid-sourcing et celle de production peuvent se trouver dans des fuseaux horaires différents.

Par exemple, si l’instance de mid-sourcing se trouve dans le fuseau horaire de Brisbane et que l’instance de production figure dans le fuseau horaire de Darwin, les deux fuseaux horaires sont espacés d’une demi-heure. Dans le journal d’audit, vous verrez clairement que si la diffusion est planifiée pour la production à 11h56, la même diffusion sera planifiée pour le mid-sourcing à 12h26, ce qui représente une différence d’une demi-heure.

## Statut En échec {#failed-status}

Si l’état d’une diffusion par email est **[!UICONTROL En échec]**, la raison peut être un problème lié aux blocs de personnalisation. Dans une diffusion, les blocs de personnalisation peuvent générer des erreurs lorsque les schémas ne correspondent pas au mapping de diffusion, par exemple.

Les logs de diffusion sont la clé pour apprendre pourquoi une diffusion a échoué. Voici les erreurs possibles que vous pouvez détecter dans les logs de diffusion :

* Les messages des destinataires échouent avec une erreur &quot;Inatteignable&quot; indiquant :

  ```
  Error while compiling script 'content htmlContent' line X: `[table]` is not defined. JavaScript: error while evaluating script 'content htmlContent
  ```

  Le problème est presque toujours dû à une personnalisation du code HTML qui tente d’appeler une table ou un champ non défini ou mappé dans le ciblage amont ou dans le mapping de ciblage de la diffusion.

  Pour corriger ce problème, le workflow et le contenu de la diffusion doivent être examinés afin de déterminer précisément quelle personnalisation tente d’appeler la table en question et si la table peut être mappée ou non. À partir de là, supprimer l’appel à cette table dans le code HTML ou résoudre le mapping sur la diffusion peut permettre de résoudre le problème.

* Dans le modèle de déploiement Mid-sourcing, le message suivant peut apparaître dans les logs de diffusion :

  ```
  Error during the call of method 'AppendDeliveryPart' on the mid sourcing server: 'Communication error with the server: please check this one is correctly configured. Code HTTP 408 'Service temporarily unavailable'.
  ```

  La cause de cette erreur est liée à des problèmes de performance. Elle indique que l’instance marketing a passé trop de temps à créer des données avant de les envoyer au serveur de mid-sourcing.

  Pour résoudre ce problème, il est recommandé d&#39;effectuer un nettoyage et une réindexation de la base de données. Pour plus d&#39;informations sur la maintenance de la base, reportez-vous à la section [cette section](../../production/using/recommendations.md).

  Vous devez également redémarrer tous les workflows avec une activité planifiée et tous ceux dont l’état est en échec. Consultez [cette section](../../workflow/using/scheduler.md).

* En cas d’échec d’une diffusion, l’erreur suivante peut s’afficher dans les logs de diffusion :

  ```
  DLV-XXXX The count of message prepared (123) is greater than the number of messages to send (111). Please contact support.
  ```

  En règle générale, cette erreur signifie qu’un champ ou un bloc de personnalisation dans l’email possède plusieurs valeurs pour le destinataire. Un bloc de personnalisation est utilisé et il récupère plusieurs enregistrements pour un destinataire spécifique.

  Pour résoudre ce problème, vérifiez les données de personnalisation utilisées, puis vérifiez la cible des destinataires ayant plusieurs entrées pour l&#39;un de ces champs. Vous pouvez également utiliser une **[!UICONTROL Déduplication]** activité dans le workflow de ciblage avant l&#39;activité de diffusion pour vérifier qu&#39;il n&#39;y a qu&#39;un seul champ de personnalisation à la fois. Pour plus d’informations sur la déduplication, reportez-vous à la section [cette page](../../workflow/using/deduplication.md).

* Certaines diffusions peuvent échouer avec une erreur &quot;Inatteignable&quot; indiquant :

  ```
  Inbound email bounce (rule 'Auto_replies' has matched this bounce).
  ```

  Cela signifie que la diffusion a réussi mais qu’Adobe Campaign a reçu une réponse automatique du destinataire (par exemple une réponse &quot;Absent du bureau&quot;) qui correspondait aux règles d’email entrant &quot;Réponses_automatiques&quot;.

  L’email de réponse automatique est ignoré par Adobe Campaign et l’adresse du destinataire n’est pas envoyée en quarantaine.
