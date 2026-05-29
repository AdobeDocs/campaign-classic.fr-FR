---
product: campaign
title: Propriétés d’exécution
description: En savoir plus sur les propriétés des workflows de Campaign
feature: Workflows
hide: true
exl-id: c7bff902-4f5d-4783-aec4-13561fa7d242
TQID: https://experienceleague.adobe.com/H8Surh-owYlv-qVNN4efyqWctA53oD0GMexLgYaTxgo
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
subfeature_v2: id: ee25c34b-ea50-427b-9369-ba0a160f7d70id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22fid: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 624
ht-degree: 51%

---

# Propriétés d&#39;exécution{#workflow-properties}



## Onglet Exécution {#execution-tab}

L&#39;onglet **[!UICONTROL Exécution]** de la fenêtre **[!UICONTROL Propriétés]** d&#39;un workflow est organisée en 3 sections :

![](assets/wf_execution_tab.png)

### Planificateur {#scheduler}

Cette section n’apparaît que dans les workflows de campagne.

* **[!UICONTROL Priorité]**

  Le moteur de workflow traite les workflows à exécuter selon le critère de priorité défini dans ce champ. Par exemple, tous les workflows de priorité **[!UICONTROL moyenne]** sont exécutés avant ceux de priorité **[!UICONTROL faible]**.

* **[!UICONTROL Différer l’exécution vers une plage horaire de faible activité]**

  Cette option reporte le démarrage du workflow à une période moins chargée. Certains workflows peuvent être coûteux en termes de ressources pour le moteur de base de données. Nous vous recommandons de planifier l’exécution pendant une période de faible activité (la nuit, par exemple). Les plages horaires de faible activité sont définies dans le workflow technique **[!UICONTROL Traitements sur les campagnes]**.

### Exécution {#execution}

* **[!UICONTROL Affinité par défaut]**

  Si votre installation comprend plusieurs serveurs de workflow, utilisez ce champ pour choisir la machine sur laquelle le workflow sera exécuté. Si la valeur définie dans ce champ n’existe sur aucun serveur, le workflow reste en attente.

  Reportez-vous à ce [guide d’installation de Campaign Classic v7](../../installation/using/configuring-campaign-server.md#high-availability-workflows-and-affinities).

* **[!UICONTROL Jours d&#39;historique]**

  Les tables de travail de la base de données conservent un historique des exécutions (tâches, événements, journal). Vous pouvez définir ici le nombre de jours à archiver pour ce workflow : le processus de nettoyage supprimera les archives les plus anciennes une fois par jour. Si la valeur de ce champ est zéro, l’archive ne sera jamais supprimée.

* **[!UICONTROL Enregistrer les requêtes SQL dans le journal]**

  Cette fonctionnalité est réservée aux utilisateurs et utilisatrices avancés. Elle concerne les workflows qui contiennent des activités de ciblage (requête, union, intersection, etc.). Lorsque cette option est cochée, les requêtes SQL envoyées à la base de données lors de l&#39;exécution du workflow sont affichées dans Adobe Campaign : vous pouvez ainsi les analyser afin d&#39;optimiser les requêtes ou diagnostiquer d&#39;éventuels problèmes.

  Les requêtes sont affichées dans un onglet **[!UICONTROL Logs SQL]** ajouté au workflow (sauf pour les workflows de campagne) et à l’activité **[!UICONTROL Propriétés]** lorsque l’option est activée. L’onglet **[!UICONTROL Audit]** comprend également des requêtes SQL.

  ![](assets/wf_tab_log_sql.png)

* **[!UICONTROL Exécuter dans le moteur]**

  Cette option ne peut être utilisée qu’à des fins de débogage et jamais en production. Lorsqu’il est activé, le workflow en question devient prioritaire et tous les autres workflows sont arrêtés jusqu’à ce que celui-ci soit terminé.

### Gestion des erreurs {#error-management}

* **[!UICONTROL Résolution des problèmes]**

  Ce champ vous permet de définir les actions à effectuer si une tâche de workflow rencontre une erreur. Il existe deux options possibles :

   * **[!UICONTROL Arrêter le processus]** : le workflow est automatiquement mis en pause. Sinon, le statut du workflow devient **[!UICONTROL Échec]**. Une fois le problème résolu, redémarrez le workflow à l’aide des boutons **[!UICONTROL Démarrer]** ou **[!UICONTROL Redémarrer]**.
   * **[!UICONTROL Ignorer]** : le statut de la tâche qui a déclenché l’erreur passe à **[!UICONTROL Échec]**, mais le workflow conserve le statut **[!UICONTROL Démarré]**. Ce paramétrage est pertinent dans le cas de tâches récurrentes : si la branche comporte un planificateur, celui-ci se déclenchera normalement à sa prochaine date d&#39;exécution.

* **[!UICONTROL Erreurs consécutives]**

  Ce champ est disponible lorsque la valeur **[!UICONTROL Ignorer]** est sélectionnée dans le champ **[!UICONTROL En cas d’erreur]**. Vous pouvez spécifier le nombre d’erreurs qui peuvent être ignorées avant l’arrêt du processus. Une fois ce nombre atteint, le statut du workflow passe à **[!UICONTROL Échec]**. Si la valeur de ce champ est 0, le workflow ne sera jamais arrêté, quel que soit le nombre d’erreurs.

* **[!UICONTROL Template]**

  Dans ce champ, choisissez le modèle de notification à envoyer au groupe de supervision du workflow lorsque celui-ci passe sur **[!UICONTROL En échec]**.

  Les opérateurs et opératrices recevront un e-mail, à l’adresse indiquée dans leur profil, le cas échéant. Pour définir les responsable des workflows, accédez au champ **[!UICONTROL Personnes chargées de la supervision]** de l’onglet **[!UICONTROL Général]** des propriétés.

  ![](assets/wf-properties_select-supervisors.png)

  Le modèle par défaut **[!UICONTROL Notification du responsable d&#39;un workflow]** comprend un lien qui permet d&#39;accéder en Web à la console Adobe Campaign et, après connexion, d&#39;agir sur le workflow en erreur.

  Vous pouvez créer un modèle personnalisé dans **[!UICONTROL Administration > Gestion de campagne > Modèles des diffusions techniques]**.
