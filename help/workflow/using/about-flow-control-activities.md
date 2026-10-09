---
product: campaign
title: À propos des activités d’ordonnancement
description: À propos des activités d’ordonnancement
feature: Workflows
hide: true
exl-id: 3810cbd0-159c-4161-b568-1f61dcea0300
TQID: 'https://experienceleague.adobe.com/uL3u76ka1Z9QSSgnUDiY4w3ZoEy9mKu293PgxoCX-mE'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
    internal-label: HeatMap
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
    internal-label: Execution activities
  - id: d1110311-2ca4-442b-be37-088a6db845ee
    internal-label: Data Management activities
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
source-git-commit: 3e213ecc670d5a3cb8299c092ccbb5303858327d
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 100%
---
# Activités dʼordonnancement dans les workflows{#about-flow-control-activities}



Les activités suivantes sont les activités de base : leur tâche consiste principalement à coordonner les autres activités.

* **Début et Fin** : permettent respectivement de marquer les points de départ et de fin du workflow. Pour plus d&#39;informations, consultez la section [Début et Fin](start-and-end.md).
* **Branchement** : permet d’activer toutes les transitions sortantes. Pour plus d&#39;informations, consultez la section [Branchement](fork.md).
* **Rendez-vous** : permet d’attendre que plusieurs tâches lancées en parallèle soient terminées avant de continuer. Pour plus d&#39;informations, consultez la section [Branchement](fork.md).
* **Planificateur** : permet de définir un planning d’exécution du workflow. Pour plus d&#39;informations, consultez la section [Planificateur](scheduler.md).
* **Test** : active une transition en fonction du résultat d’un test. Pour plus d&#39;informations, consultez la section [Test](test.md).
* **Attente** : active la transition sortante après un délai donné. Pour plus d&#39;informations, consultez la section [Attente](wait.md).
* **Contrainte horaire** : permet de suspendre l’exécution d’une tâche pendant une période déterminée. Pour plus d&#39;informations, consultez la section [Contrainte horaire](time-constraint.md).
* **Sous-workflow** : permet de lancer l’exécution d’un autre workflow. Pour plus d&#39;informations, consultez la section [Sous-workflow](sub-workflow.md).
* **Sauts** : permettent de mettre en place des transitions sans lien. Pour plus d&#39;informations, consultez la section [Saut (départ et arrivée)](jump-start-point-and-end-point.md).
* **Signal externe** : permet d’activer la transition sortante sur réception d’un signal externe. Consultez la section [Signal externe](external-signal.md).
* **Validation** : permet d’envoyer un email à un opérateur ou à un groupe d’opérateurs et d’attendre la validation pour continuer l’exécution. Pour plus d&#39;informations, consultez la section [Validation](approval.md).
* **Alerte** : permet d’envoyer un email d’alerte à un opérateur ou à un groupe d’opérateurs. Pour plus d&#39;informations, consultez la section [Alerte](alert.md).
* **Tâche** : permet de configurer l’exécution de la tâche. Pour plus d&#39;informations, consultez la section [Tâche](task.md).
