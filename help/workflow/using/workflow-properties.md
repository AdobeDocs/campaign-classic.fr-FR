---
product: campaign
title: Propriétés d’exécution
description: En savoir plus sur les propriétés des workflows de Campaign
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
feature: Workflows
exl-id: c7bff902-4f5d-4783-aec4-13561fa7d242
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 100%

---

# Propriétés d&#39;exécution        {#workflow-properties}



## Onglet Exécution {#execution-tab}

L&#39;onglet **[!UICONTROL Exécution]** de la fenêtre **[!UICONTROL Propriétés]** d&#39;un workflow est organisée en 3 sections :

![](assets/wf_execution_tab.png)

### Planificateur {#scheduler}

Cette section n&#39;apparaît que dans les workflows d&#39;opérations.

* **[!UICONTROL Priorité]**

  Le moteur de workflow traite les workflows à exécuter selon le critère de priorité défini dans ce champ. Par exemple, tous les workflows de priorité **[!UICONTROL moyenne]** sont exécutés avant ceux de priorité **[!UICONTROL faible]**.

* **[!UICONTROL Différer l’exécution vers une plage horaire de faible activité]**

  Cette option reporte le lancement du workflow vers une plage horaire moins chargée. Certains workflows peuvent être très coûteux en termes de ressources pour le moteur de base de données. Il peut donc être utile de décaler l’exécution des workflows moins urgents vers une plage de faible activité (la nuit par exemple). Les plages horaires de faible activité sont définies dans le workflow technique **[!UICONTROL Traitements sur les campagnes]**.

### Exécution {#execution}

* **[!UICONTROL Affinité par défaut]**

  Si votre installation comprend plusieurs serveurs de workflow, utilisez ce champ pour choisir sur quelle machine le workflow s&#39;exécutera. Si la valeur définie dans ce champ n&#39;existe au niveau d&#39;aucun serveur, le workflow restera en attente.

  Reportez-vous à ce [guide d’installation de Campaign Classic v7](../../installation/using/configuring-campaign-server.md#high-availability-workflows-and-affinities).

* **[!UICONTROL Jours d&#39;historique]**

  Les tables de travail de la base conservent un historique des exécutions (tâches, évènements, journal). Définissez ici le nombre de jours d&#39;historique que vous voulez conserver pour ce workflow : les processus de nettoyage de la base supprimeront chaque jour les historiques plus anciens. Si la valeur de ce champ est zéro, l&#39;historique ne sera jamais supprimé.

* **[!UICONTROL Enregistrer les requêtes SQL dans le journal]**

  Cette fonctionnalité est réservée aux utilisateurs experts. Elle concerne les workflows qui contiennent des activités de ciblage (requête, union, intersection, etc.). Lorsque cette option est cochée, les requêtes SQL envoyées vers la base lors de l&#39;exécution du workflow sont affichées dans Adobe Campaign : vous pouvez ainsi les analyser afin d&#39;optimiser les requêtes ou diagnostiquer d&#39;éventuels problèmes.

  Les requêtes sont affichées dans un onglet **[!UICONTROL Journaux SQL]** ajouté au workflow (sauf pour les workflows de campagne) et à l’activité **[!UICONTROL Propriétés]** lorsque l’option est activée. L’onglet **[!UICONTROL Audit]** comprend également des requêtes SQL.

  ![](assets/wf_tab_log_sql.png)

* **[!UICONTROL Exécuter dans le moteur]**

  Cette option ne doit être utilisée qu&#39;à des fins de débuggage et jamais en production. Lorsque cette option est activée, le workflow devient prioritaire, et tous les autres workflows sont stoppés par le moteur de workflow tant qu&#39;il n&#39;est pas terminé.

### Gestion des erreurs        {#error-management}

* **[!UICONTROL Résolution des problèmes]**

  Ce champ vous permet de définir l&#39;action à effectuer lorsqu&#39;une tâche du workflow est en erreur. Deux options sont disponibles :

   * **[!UICONTROL Arrêter le processus]** : le workflow est automatiquement mis en pause. Sinon, le statut du workflow devient **[!UICONTROL Échec]**. Une fois le problème résolu, redémarrez le workflow à l’aide des boutons **[!UICONTROL Démarrer]** ou **[!UICONTROL Redémarrer]**.
   * **[!UICONTROL Ignorer]** : la tâche ayant provoqué l&#39;erreur prend le statut **[!UICONTROL En échec]**, mais le workflow garde le statut **[!UICONTROL Démarré]**. Ce paramétrage est pertinent dans le cas de tâches récurrentes : si la branche comporte un planificateur, celui-ci se déclenchera normalement à sa prochaine date d&#39;exécution.

* **[!UICONTROL Erreurs consécutives]**

  Ce champ devient disponible lorsque la valeur **[!UICONTROL Ignorer]** est sélectionnée dans le champ **[!UICONTROL En cas d’erreur]**. Vous pouvez spécifier le nombre d’erreurs qui peuvent être ignorées avant l’arrêt du processus. Une fois ce nombre atteint, le statut du workflow passe à **[!UICONTROL Échec]**. Si la valeur de ce champ est 0, le workflow ne sera jamais arrêté, quel que soit le nombre d’erreurs.

* **[!UICONTROL Template]**

  Dans ce champ, choisissez le modèle de notification à envoyer au groupe de supervision du workflow lorsque celui-ci passe sur **[!UICONTROL En échec]**.

  Les opérateurs et opératrices recevront un e-mail, à l’adresse indiquée dans leur profil, le cas échéant. Pour définir les responsable des workflows, accédez au champ **[!UICONTROL Personnes chargées de la supervision]** de l’onglet **[!UICONTROL Général]** des propriétés.

  ![](assets/wf-properties_select-supervisors.png)

  Le modèle par défaut **[!UICONTROL Notification du responsable d&#39;un workflow]** comprend un lien qui permet d&#39;accéder en Web à la console Adobe Campaign et, après connexion, d&#39;agir sur le workflow en erreur.

  Vous pouvez créer un modèle personnalisé dans **[!UICONTROL Administration > Gestion de campagne > Modèles des diffusions techniques]**.
