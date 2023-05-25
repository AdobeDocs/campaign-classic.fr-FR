---
product: campaign
title: Types de maintenance
description: Types de maintenance
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: 08e179aa-fd83-4c0a-879e-ab7aec168d92
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: ht
source-wordcount: '494'
ht-degree: 100%

---

# Types de maintenance{#types-of-maintenance}



## Maintenance au niveau applicatif {#application-maintenance}

Adobe Campaign met à votre disposition un workflow intégré qui permet de planifier certaines tâches de maintenance. Il s&#39;agit du **workflow de nettoyage de la base** qui effectue les tâches suivantes :

* suppression des enregistrements expirés,
* suppression des enregistrements orphelins et réinitialisation du statut des objets qui ont expirés,
* mise à jour des statistiques de la base de données.

>[!IMPORTANT]
>
>Le workflow de nettoyage assure la maintenance au niveau applicatif et non celle du SGDB (à l&#39;exception de la mise à jour des statistiques). Il est cependant nécessaire d&#39;effectuer des opérations de maintenance sur la base. En effet, le fait que la tâche de nettoyage se déroule sans erreur ne signifie pas que la base de données soit totalement optimisée.

## Maintenance technique {#technical-maintenance}

Le workflow de nettoyage de la base ne comprend aucun système pour planifier la maintenance de la base. C&#39;est à vous que revient la responsabilité de planifier la maintenance. Pour cela, vous pouvez, au choix :

* collaborer avec l&#39;administrateur de la base de données pour configurer la maintenance de la base avec des outils tiers,
* utiliser le moteur de workflow disponible dans Adobe Campaign pour planifier et suivre les activités de maintenance.

Ces procédures de maintenance doivent être effectuées régulièrement. Il s&#39;agit, par exemple, des procédures suivantes :

* regénérer l&#39;index des tables fréquemment mises à jour,
* compacter ou reconstruire les tables pour leur éviter d&#39;être fragmentées.

### Planifier la maintenance {#maintenance-schedule}

Vous devez trouver le moment approprié pour effectuer les opérations de maintenance. Celles-ci peuvent avoir un impact important sur les performances de la base de données ou bloquer l&#39;application (du fait du verrouillage).

Il est courant de lancer les tâches de maintenance une fois par semaine, pendant une période de faible activité et en dehors des périodes de sauvegarde, de rechargement de données ou de calcul des agrégats. Sur certains systèmes très sollicités il peut être nécessaire de le faire plus souvent.

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
   <td> Requiert deux fois plus d'espace-disque.<br /> Tous les processus qui doivent accéder à la table en écriture doivent être arrêtés. Ils ne seront pas affectés par les opérations de duplication/renommage/suppression car les différentes versions de la table sont échangées au dernier moment lorsque la défragmentation est terminée. <br /> </td> 
  </tr> 
 </tbody> 
</table>
