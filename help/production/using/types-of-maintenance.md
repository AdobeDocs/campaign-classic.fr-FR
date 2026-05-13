---
product: campaign
title: Types de maintenance
description: Types de maintenance
feature: Monitoring
badge-v7-prem: label="On-Premise/hybride uniquement" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: 08e179aa-fd83-4c0a-879e-ab7aec168d92
TQID: https://experienceleague.adobe.com/bnEjFRKyiM1Um7c1bjoQ6Irblxu9UnQdtXQeGxGvsZk
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 528
ht-degree: 65%

---

# Types de maintenance{#types-of-maintenance}



## Maintenance au niveau applicatif {#application-maintenance}

Adobe Campaign propose un workflow intégré qui permet de planifier certaines tâches de maintenance. Il s’agit du workflow **nettoyage de la base**. Ce workflow effectue les tâches suivantes :

* suppression des enregistrements expirés,
* suppression des enregistrements orphelins et réinitialisation du statut des objets qui ont expirés,
* mise à jour des statistiques de la base de données.

>[!IMPORTANT]
>
>Notez que la tâche de nettoyage concerne principalement la maintenance au niveau de l&#39;application, et non au niveau du SGBDR (à l&#39;exception de la mise à jour des statistiques). Toutefois, des opérations de maintenance seront nécessaires sur la base de données. Même si le workflow de nettoyage de la base de données s’exécute correctement, cela ne signifie pas que le réglage de la base de données est optimal.

## Maintenance technique {#technical-maintenance}

Le workflow de nettoyage de la base ne comprend aucun outil de maintenance de la base. C&#39;est à vous que revient la responsabilité d&#39;organiser la maintenance. Pour ce faire, vous pouvez effectuer l’une des opérations suivantes :

* collaborer avec l&#39;administrateur de la base de données pour configurer la maintenance de la base avec des outils tiers,
* utiliser le moteur de workflow disponible dans Adobe Campaign pour planifier et suivre les activités de maintenance.

Ces procédures de maintenance doivent être effectuées régulièrement. Il s&#39;agit, par exemple, des procédures suivantes :

* regénérer l&#39;index des tables fréquemment mises à jour,
* compacter ou reconstruire les tables pour leur éviter d&#39;être fragmentées.

### Planifier la maintenance {#maintenance-schedule}

Vous devez trouver les emplacements appropriés pour effectuer ces activités de maintenance. Ils peuvent avoir un impact important sur les performances de la base de données lors de l’exécution ou même bloquer l’application (en raison du verrouillage).

Ces tâches sont généralement exécutées une fois par semaine pendant une période de faible activité n’entrant pas en conflit avec les sauvegardes, le rechargement de données ou les calculs d’agrégats. Certains systèmes très sollicités nécessitent une maintenance plus fréquente.

Une opération de maintenance plus importante, comme la reconstruction de toutes les tables peut être faite une fois par mois, de préférence lorsque les applications sont totalement arrêtées, le système étant alors inutilisable.

### Reconstruire une table {#rebuilding-a-table}

Pour reconstruire une table, plusieurs stratégies sont envisageables :

<table> 
 <thead> 
  <tr> 
   <th> Opérations </th> 
   <th> Description </th> 
   <th> Avantages </th> 
   <th> Inconvénients </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Défragmentation à chaud<br /> </td> 
   <td> La plupart des moteurs de base de données mettent à disposition des méthodes de défragmentation.<br /> </td> 
   <td> Il suffit d'utiliser la méthode de défragmentation du moteur de base de données. Ces méthodes ont l'avantage de préserver l'intégrité des données, notamment en les verrouillant pendant la défragmentation.<br /> </td> 
   <td> Selon les bases, ces méthodes de défragmentation peuvent être fournies comme une option du SGBDR (Cf. Oracle) et ne sont pas toujours les plus efficaces sur les tables très volumineuses.<br /> </td> 
  </tr> 
  <tr> 
   <td> Sauvegarde puis restauration<br /> </td> 
   <td> Cette opération consiste à sauvegarder la table sous forme de fichier puis à la supprimer de la base de données et à la restaurer à partir du fichier de sauvegarde.<br /> </td> 
   <td> Il s'agit de la façon la plus simple de défragmenter une table. C'est également la seule envisageable lorsque la base occupe presque tout l'espace-disque.<br /> </td> 
   <td> La table étant supprimée puis recréée, il est impossible de garder l'application en état de fonctionnement, même en lecture seule car la table n'est pas accessible pendant la phase de restauration.<br /> </td> 
  </tr> 
  <tr> 
   <td> Duplication puis renommage et suppression<br /> </td> 
   <td> Cette opération consiste à créer une copie de la table et de ses index, à supprimer la table originelle puis à la remplacer par sa copie après l'avoir renommée.<br /> </td> 
   <td> Cette méthode est plus rapide que la première approche, car elle génère moins d'E/S (pas de copie en tant que fichier ni de lecture à partir de ce fichier).<br /> </td> 
   <td> Nécessite deux fois plus d’espace.<br /> Tous les processus actifs qui écrivent dans la table pendant le processus doivent être arrêtés. Toutefois, les processus de lecture ne sont pas affectés, car la table est échangée au dernier moment une fois la reconstruction effectuée. <br /> </td> 
  </tr> 
 </tbody> 
</table>
