---
product: campaign
title: Performances des diffusions et résolution des problèmes
description: Découvrez comment optimiser les performances des diffusions et résoudre les problèmes dans Campaign Classic v7
feature: Monitoring, Deliverability, Troubleshooting
role: User, Developer
exl-id: cc793d7b-0a26-4a75-97ed-d79c87d9b3b8
source-git-commit: 2ebae2b84741bf26dd44c872702dbf3b0ebfc453
workflow-type: tm+mt
source-wordcount: '669'
ht-degree: 5%

---

# Performances des diffusions et résolution des problèmes {#delivery-performance-troubleshooting}

>[!NOTE]
>
>Des conseils complets sur les performances et les bonnes pratiques de diffusion sont documentés à la page [Bonnes pratiques de diffusion de Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices). Ce contenu s’applique aux utilisateurs de Campaign Classic v7 et de Campaign v8.
>
>Cette page présente les configurations spécifiques à **Campaign Classic v7** pour l’optimisation des performances et le dépannage dans les déploiements hybrides et on-premise.

Pour obtenir des bonnes pratiques complètes sur les performances des diffusions, l&#39;optimisation de la plateforme, la gestion des quarantaines, la maintenance de la base de données et les recommandations de planification, reportez-vous à la documentation [&#x200B; Bonnes pratiques de diffusion de Campaign v8 &#x200B;](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}.

## Optimisation des performances {#performance-optimization}

Pour les déploiements hybrides/on-premise **Campaign Classic v7**, les optimisations suivantes de la base de données et de l&#39;infrastructure peuvent améliorer les performances de diffusion.

### Optimisation de la base de données

**Adresses d’index** pour optimiser les performances des requêtes SQL utilisées dans l’application. Un index peut être déclaré à partir de l&#39;élément principal du schéma de données. Cette optimisation nécessite un accès direct à la base de données et une personnalisation des schémas disponibles dans les déploiements On-Premise.

### Réglage de l’infrastructure

**Configuration des diffusions volumineuses** : les diffusions vers plus d’un million de destinataires ont besoin d’espace dans les files d’attente d’envoi. Pour les installations on-premise, les enfants MTA peuvent être configurés pour gérer les tailles de lot personnalisées. Contactez votre administrateur système pour ajuster ces paramètres en fonction de la capacité de votre infrastructure.

>[!NOTE]
>
>Pour les utilisateurs de Campaign v8 Managed Cloud Services, l’optimisation de l’infrastructure et la configuration du MTA sont gérées par Adobe. Pour obtenir des recommandations de performances applicables à votre déploiement[&#x200B; consultez les bonnes pratiques de diffusion &#x200B;](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}Campaign v8) .

### Maintenance de la base de données {#database-maintenance}

Pour les déploiements hybrides/on-premise **Campaign Classic v7**, la maintenance de la plateforme et de la base de données affecte directement les performances d&#39;envoi des diffusions.

Les tâches de maintenance régulières incluent :

**Nettoyage de la base de données** : utilisez le workflow de nettoyage de la base de données pour supprimer les anciens logs de diffusion, les données de tracking et les tables temporaires. Une mauvaise maintenance de la base de données peut ralentir la préparation et l’envoi des diffusions.

**Surveillance des performances de la base de données** : surveillez les performances des requêtes, la fragmentation des index et les statistiques des tables. Pour obtenir des conseils détaillés, consultez [cette page](../../production/using/database-performances.md).

**Surveillance des workflows techniques** : assurez-vous que tous les workflows techniques (en particulier les workflows de nettoyage, de tracking et de mise à jour de délivrabilité) s’exécutent correctement, sans erreur.

>[!NOTE]
>
>Pour les utilisateurs de Campaign v8 Managed Cloud Services, la maintenance de la base de données et les workflows techniques sont surveillés et gérés par Adobe. Concentrez-vous sur la surveillance spécifique aux diffusions, comme décrit dans la documentation [Surveiller les diffusions de Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitoring-deliverability){target="_blank"}.

## Résolution des problèmes de diffusion {#troubleshooting}

>[!NOTE]
>
>Des conseils complets sur la résolution des problèmes de diffusion sont documentés dans la documentation de Campaign v8, applicable aux utilisateurs de Campaign Classic v7 et de Campaign v8 :
>
>* Échecs et solutions de diffusion courants : [Comprendre les échecs de diffusion](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}
>* Diagnostic de diffusion lente : [surveiller les diffusions dans l’interface utilisateur de Campaign](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"}
>* Bonnes pratiques de diffusion : [Bonnes pratiques de diffusion](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}
>
>Cette section présente la résolution des problèmes spécifique à **Campaign Classic v7** pour les déploiements hybrides et on-premise.

Pour les **déploiements hybrides/on-premise de Campaign Classic v7**, les étapes de dépannage suivantes sont spécifiques à l&#39;infrastructure que vous gérez.

### Configuration des règles MX

Si vous rencontrez des problèmes de limitation avec des FAI spécifiques, vous devrez peut-être vérifier et ajuster la configuration de vos règles MX. Pour plus d&#39;informations sur les règles MX et les quotas, consultez [cette section](../../installation/using/email-deliverability.md#about-mx-rules).

### Maintenance de la base de données pour les performances des diffusions

Si vous rencontrez l’erreur suivante dans les déploiements en midsourcing :

```
Error during the call of method 'AppendDeliveryPart' on the mid sourcing server: 'Communication error with the server: please check this one is correctly configured. Code HTTP 408 'Service temporarily unavailable'.
```

La cause de ce problème est liée à des problèmes de performances lorsque l’instance marketing passe trop de temps à créer des données avant de les envoyer au serveur de mid-sourcing.

**Pour les installations on-premise**, effectuez un nettoyage et une réindexation de la base de données. Pour plus d’informations sur la maintenance de la base de données, consultez [cette section](../../production/using/recommendations.md).

Vous devez également redémarrer tous les workflows avec une activité planifiée et tous ceux dans un état en échec. Consultez [cette section](../../workflow/using/scheduler.md).

### Surveillance des workflows techniques

Pour les installations on-premise, assurez-vous que tous les workflows techniques liés à la délivrabilité s&#39;exécutent sans erreur :

**Workflow de mise à jour de la délivrabilité** : met à jour les règles de qualification des emails rebonds et les indicateurs de délivrabilité.

**Workflow de tracking** : traite les données de tracking des diffusions envoyées.

**Workflow de nettoyage de la base de données** : purge régulièrement les anciens logs de diffusion et les tables temporaires pour maintenir les performances.

Vérifiez le statut des workflows dans **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Workflows techniques]**.

>[!NOTE]
>
>Pour les utilisateurs et utilisatrices de Campaign v8 Managed Cloud Services, la surveillance des workflows techniques et de l’infrastructure est gérée par Adobe. Concentrez-vous sur le contenu et le ciblage de la diffusion, comme décrit dans la [documentation de Campaign v8](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}.

## Rubriques connexes

* [Présentation des diffusions en échec](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} (documentation de Campaign v8)
* [&#x200B; Bonnes pratiques de diffusion &#x200B;](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} (documentation de Campaign v8)
* [Surveillance des diffusions dans l’interface utilisateur de Campaign](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"} (documentation de Campaign v8)
* [Maintenance de la base de données](../../production/using/recommendations.md) (v7 hybride/on-premise)
* [Délivrabilité des e-mails](../../installation/using/email-deliverability.md) (v7 hybride/on-premise)
* [Performances de la base de données](../../production/using/database-performances.md) (v7 hybride/on-premise)

