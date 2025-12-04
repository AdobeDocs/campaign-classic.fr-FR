---
product: campaign
title: Bonnes pratiques des performances de diffusion
description: En savoir plus sur les performances et les bonnes pratiques de diffusion
feature: Deliverability
role: User, Developer
exl-id: cc793d7b-0a26-4a75-97ed-d79c87d9b3b8
source-git-commit: eac670cd4e7371ca386cee5f1735dc201bf5410a
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 6%

---

# Bonnes pratiques des performances de diffusion {#delivery-performances}

>[!NOTE]
>
>Des conseils complets sur les performances et les bonnes pratiques de diffusion sont documentés à la page [Bonnes pratiques de diffusion de Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices). Ce contenu s’applique aux utilisateurs de Campaign Classic v7 et de Campaign v8.
>
>Cette page documente les configurations de performances spécifiques à Campaign Classic v7 **pour les déploiements hybrides et on-premise.**

Pour obtenir des bonnes pratiques complètes sur les performances des diffusions, l&#39;optimisation de la plateforme, la gestion des quarantaines, la maintenance de la base de données et les recommandations de planification, reportez-vous à la documentation [&#x200B; Bonnes pratiques de diffusion de Campaign v8 &#x200B;](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}.

## Réglage des performances {#best-practices-performance}

Pour les déploiements hybrides/on-premise **Campaign Classic v7**, les optimisations suivantes de la base de données et de l&#39;infrastructure peuvent améliorer les performances de diffusion :

### Optimisation de la base de données

**Adresses d’index** pour optimiser les performances des requêtes SQL utilisées dans l’application. Un index peut être déclaré à partir de l&#39;élément principal du schéma de données. Cette optimisation nécessite un accès direct à la base de données et une personnalisation des schémas disponibles dans les déploiements On-Premise.

### Réglage de l’infrastructure

**Configuration des diffusions volumineuses** : les diffusions vers plus d’un million de destinataires ont besoin d’espace dans les files d’attente d’envoi. Pour les installations on-premise, les enfants MTA peuvent être configurés pour gérer les tailles de lot personnalisées. Contactez votre administrateur système pour ajuster ces paramètres en fonction de la capacité de votre infrastructure.

>[!NOTE]
>
>Pour les utilisateurs de Campaign v8 Managed Cloud Services, l’optimisation de l’infrastructure et la configuration du MTA sont gérées par Adobe. Pour obtenir des recommandations de performances applicables à votre déploiement[&#x200B; consultez les bonnes pratiques de diffusion &#x200B;](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}Campaign v8) .

## Maintenance de la base de données {#performance-issues}

Pour les déploiements hybrides/on-premise **Campaign Classic v7**, la maintenance de la plateforme et de la base de données affecte directement les performances d&#39;envoi des diffusions.

Les tâches de maintenance régulières incluent :

**Nettoyage de la base de données** : utilisez le workflow de nettoyage de la base de données pour supprimer les anciens logs de diffusion, les données de tracking et les tables temporaires. Une mauvaise maintenance de la base de données peut ralentir la préparation et l’envoi des diffusions.

**Surveillance des performances de la base de données** : surveillez les performances des requêtes, la fragmentation des index et les statistiques des tables. Pour obtenir des conseils détaillés, consultez [cette page](../../production/using/database-performances.md).

**Surveillance des workflows techniques** : assurez-vous que tous les workflows techniques (en particulier les workflows de nettoyage, de tracking et de mise à jour de délivrabilité) s’exécutent correctement, sans erreur.

>[!NOTE]
>
>Pour les utilisateurs de Campaign v8 Managed Cloud Services, la maintenance de la base de données et les workflows techniques sont surveillés et gérés par Adobe. Concentrez-vous sur la surveillance spécifique aux diffusions, comme décrit dans la documentation [Surveiller les diffusions de Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitoring-deliverability){target="_blank"}.

## Rubriques connexes

* [&#x200B; Bonnes pratiques de diffusion &#x200B;](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} (documentation de Campaign v8)
* [Surveiller votre délivrabilité](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitoring-deliverability){target="_blank"} (documentation de Campaign v8)
* [Résolution des problèmes liés aux diffusions](delivery-troubleshooting.md)
* [Performances de la base de données](../../production/using/database-performances.md) (v7 hybride/on-premise)
