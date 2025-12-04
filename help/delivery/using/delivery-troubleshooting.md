---
product: campaign
title: Résolution des problèmes liés à lʼenvoi de diffusions
description: En savoir plus sur les performances des diffusions et comment résoudre les problèmes liés à la surveillance des diffusions
feature: Monitoring, Deliverability, Troubleshooting
role: User
exl-id: 37b1d7fb-7ceb-4647-9aac-c8a80495c5bf
source-git-commit: eac670cd4e7371ca386cee5f1735dc201bf5410a
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 16%

---

# Résolution des problèmes liés à lʼenvoi de diffusions {#delivery-troubleshooting}

>[!NOTE]
>
>Des conseils complets sur la résolution des problèmes de diffusion sont documentés dans la documentation de Campaign v8, applicable aux utilisateurs de Campaign Classic v7 et de Campaign v8 :
>
>* Échecs et solutions de diffusion courants : [Comprendre les échecs de diffusion](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}
>* Diagnostic de diffusion lente : [surveiller les diffusions dans l’interface utilisateur de Campaign](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"}
>* Bonnes pratiques de diffusion : [Bonnes pratiques de diffusion](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}
>
>Cette page présente la résolution des problèmes spécifique à Campaign Classic v7 **pour les déploiements hybrides et on-premise.**

## Résolution des problèmes {#v7-specific}

Pour les **déploiements hybrides/on-premise de Campaign Classic v7**, les étapes de dépannage suivantes sont spécifiques à l&#39;infrastructure que vous gérez :

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
>Pour les utilisateurs et utilisatrices de Campaign v8 Managed Cloud Services, la surveillance des workflows techniques et de l’infrastructure est gérée par Adobe. Concentrez-vous sur le contenu et le ciblage de la diffusion, comme décrit dans la [documentation de Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}.

## Rubriques connexes

* [Présentation des diffusions en échec](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} (documentation de Campaign v8)
* [&#x200B; Bonnes pratiques de diffusion &#x200B;](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} (documentation de Campaign v8)
* [Surveillance des diffusions dans l’interface utilisateur de Campaign](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"} (documentation de Campaign v8)
* [Maintenance de la base de données](../../production/using/recommendations.md) (v7 hybride/on-premise)
* [Délivrabilité des e-mails](../../installation/using/email-deliverability.md) (v7 hybride/on-premise)
