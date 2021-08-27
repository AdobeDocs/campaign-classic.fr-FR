---
product: campaign
title: Diffusions
description: En savoir plus sur les workflows de diffusions par défaut
audience: workflow
content-type: reference
topic-tags: technical-workflows
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 100%

---


# Diffusions{#deliveries}

![](../../assets/common.svg)

Les workflows présentés ci-dessous sont installés par défaut avec le module **Diffusions**.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Libellé</strong><br /> </td> 
   <td> <strong>Nom interne</strong><br /> </td> 
   <td> <strong>Description</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Agrégats du reporting</span> <br /> </td> 
   <td> <span class="uicontrol">reportingAggregates</span> <br /> </td> 
   <td> Ce workflow met à jour les agrégats utilisés dans les rapports. Par défaut, il se déclenche tous les jours à 2H00.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Facturation</span> <br /> </td> 
   <td> <span class="uicontrol">billing</span> <br /> </td> 
   <td> Ce workflow transmet par email le rapport d'activité du système à l'opérateur 'billing'. Par défaut, il se déclenche tous les 25 du mois.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Facturation (profils actifs)</span> <br /> </td> 
   <td> <span class="uicontrol">billingActiveContactCount</span> <br /> </td> 
   <td> <p>Ce workflow compte le nombre de profils actifs. Par défaut, il se déclenche toutes les nuits à 1h00 du matin.</p> <p>Un “<strong>profil</strong>” désigne un enregistrement d'informations (par exemple : un enregistrement dans la table nmsRecipient ou une table externe contenant un identifiant de cookie, un identifiant client, un identifiant mobile ou d'autres informations relatives à un canal particulier) représentant un client final ou un prospect. La facturation ne concerne que les profils “actifs”. Un profil est considéré comme actif s'il a été ciblé ou s'il a reçu des communications au cours des 12 derniers mois via n'importe quel canal.</p> <p>Les canaux Facebook et Twitter ne sont pas prises en compte.</p> <p>Vous pouvez obtenir un aperçu du <span class="uicontrol">Nombre de profils actifs</span> depuis le menu <span class="uicontrol">Administration</span> &gt; <span class="uicontrol">Gestion de campagne</span> &gt; <span class="uicontrol">Mesures des clients</span>.</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Gestion des alias</span> <br /> </td> 
   <td> <span class="uicontrol">aliasCleansing</span> <br /> </td> 
   <td> Ce workflow réalise l’uniformisation des valeurs des énumérations. Par défaut, il se déclenche tous les jours à 3h00.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Mise à jour pour la délivrabilité</span> <br /> </td> 
   <td> <span class="uicontrol">deliverabilityUpdate</span> <br /> </td> 
   <td> Ce workflow permet de créer la liste des règles de qualification des mails rebonds, ainsi que la liste des domaines et des MX dans la plateforme. Ce workflow ne fonctionne que si le port HTTPS est ouvert. Ces listes ne sont pas mises à jour tant que le module Délivrabilité n'est pas installé.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Nettoyage de la base</span> <br /> </td> 
   <td> <span class="uicontrol">cleanup</span> <br /> </td> 
   <td> <p>Ce workflow est le workflow d'entretien de la base : il procède aux différents calculs des statistiques et traitements, et supprime les données obsolètes de la base de données selon le paramétrage défini dans l'assistant de déploiement. Par défaut, il se déclenche tous les jours à 4H00.</p> <p>Pour plus d'informations, consultez cette <a href="../../production/using/database-cleanup-workflow.md">page</a>.</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Nettoyage des workflows en pause</span> <br /> </td> 
   <td> <span class="uicontrol">cleanupPausedWorkflows</span> <br /> </td> 
   <td> <p>Ce workflow analyse les workflows en pause dont le niveau de priorité est défini sur normal et déclenche des avertissements et des notifications lorsqu'ils sont en pause depuis trop longtemps. Après un mois, les workflows techniques en pause sont arrêtés de manière inconditionnelle. Par défaut, ce workflow est déclenché tous les lundis à 5h00.</p> <p>Pour plus d’informations, voir <a href="monitoring-workflow-execution.md#handling-of-paused-workflows" target="_blank">Gérer les workflows en pause</a>.</p></td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Notification des offres</span> <br /> </td> 
   <td> <span class="uicontrol">offerMgt</span> <br /> </td> 
   <td> Toutes les heures, ce workflow déploie les offres validées sur l'environnement en ligne, ainsi que toutes les catégories contenues dans le catalogue d'offres.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Prévisionnel</span> <br /> </td> 
   <td> <span class="uicontrol">forecasting</span> <br /> </td> 
   <td> Ce workflow effectue l’analyse des diffusions enregistrées dans le calendrier prévisionnel (création des logs prévisionnels). Par défaut, il se déclenche tous les jours à 1h00.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Tracking</span> <br /> </td> 
   <td> <span class="uicontrol">tracking</span> <br /> </td> 
   <td> Ce workflow réalise la récupération et la consolidation des informations de tracking. Il assure également le re-calcul des statistiques de tracking et de diffusions, notamment celles utilisées par les workflows d'archivage de Message Center. Par défaut, il se déclenche toutes les heures. <br /> </td> 
  </tr> 
 </tbody> 
</table>

