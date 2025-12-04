---
product: campaign
title: Comprendre la gestion des quarantaines
description: Comprendre la gestion des quarantaines
feature: Monitoring, Deliverability
role: User
exl-id: cfd8f5c9-f368-4a31-a1e2-1d77ceae5ced
source-git-commit: eac670cd4e7371ca386cee5f1735dc201bf5410a
workflow-type: tm+mt
source-wordcount: '609'
ht-degree: 2%

---

# Comprendre la gestion des quarantaines{#understanding-quarantine-management}

>[!NOTE]
>
>Des conseils complets sur la gestion des quarantaines sont documentés dans la page [Gestion des quarantaines de Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines). Ce contenu s’applique aux utilisateurs de Campaign Classic v7 et de Campaign v8 et couvre les sujets suivants :
>
>* Concepts de mise en quarantaine et de place sur la liste bloquée
>* Pourquoi les adresses sont-elles envoyées en quarantaine (erreurs hard/soft) ?
>* Gestion des erreurs de type Soft et seuils des compteurs d&#39;erreurs
>* Accès et identification des adresses en quarantaine
>* Comment supprimer des adresses de la quarantaine (automatique, manuelle, en bloc)
>* Rapports de gestion des quarantaines
>
>Cette page présente la configuration spécifique à **Campaign Classic v7** pour la gestion des quarantaines dans les déploiements hybrides et on-premise.

Pour obtenir des conseils complets sur la gestion des quarantaines, consultez la documentation [Gestion des quarantaines de Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"}.

## Configuration de la quarantaine {#v7-quarantine-config}

Les options de configuration suivantes sont disponibles pour les déploiements hybrides/on-premise de **Campaign Classic v7** afin de personnaliser le comportement de la quarantaine.

### Configuration du seuil d’erreur soft {#soft-error-threshold}

Pour les installations on-premise utilisant l&#39;ancien MTA de Campaign, vous pouvez modifier le nombre d&#39;erreurs et la période entre deux erreurs avant qu&#39;une adresse ne soit mise en quarantaine.

Pour configurer ces paramètres :

1. Accédez à l’assistant de déploiement depuis **[!UICONTROL Outils]** > **[!UICONTROL Avancé]** > **[!UICONTROL Assistant de déploiement]**
2. Accédez à **[!UICONTROL Canal e-mail]** > **[!UICONTROL Paramètres avancés]**
3. Configurer :
   * **Nombre d&#39;erreurs** : nombre maximal d&#39;erreurs soft avant la mise en quarantaine d&#39;une adresse (par défaut : 5)
   * **Période entre deux erreurs significatives** : fenêtre temporelle (en secondes) pour le comptage des erreurs (par défaut : 86 400 secondes = 1 jour)

Lorsque le compteur d&#39;erreurs atteint le seuil, l&#39;adresse est mise en quarantaine. Si la dernière erreur significative s’est produite il y a plus de 10 jours, le compteur d’erreurs est réinitialisé.

Pour plus d’informations, consultez [cette page](communication-channels.md) sous **Envoi de diffusion** > **Configurer les reprises**.

>[!NOTE]
>
>Pour les utilisateurs de Campaign v8 Managed Cloud Services, les paramètres de reprise et les seuils d’erreur sont gérés par Adobe en fonction des performances IP et de la réputation du domaine. Aucune configuration n’est requise.

### Workflow de nettoyage de la base de données {#database-cleanup-workflow}

Pour les installations on-premise, le workflow technique **[!UICONTROL Nettoyage de la base de données]** supprime automatiquement les adresses en quarantaine qui correspondent à des conditions spécifiques.

Accédez à ce workflow à partir de **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Workflows techniques]** > **[!UICONTROL Nettoyage de la base de données]**.

Le workflow supprime les adresses de la quarantaine dans les cas suivants :

* Adresses à l’état **[!UICONTROL En erreur]** après une diffusion réussie
* Adresses avec le statut **[!UICONTROL En erreur]** si le dernier soft bounce s&#39;est produit il y a plus de 10 jours
* Adresses dans l’erreur **[!UICONTROL Avec erreurs]** statut avec **[!UICONTROL Boîte pleine]** après 30 jours

Assurez-vous que ce workflow s’exécute régulièrement (recommandé : tous les jours) pour maintenir l’hygiène des listes de quarantaine.

Pour plus d&#39;informations sur le nettoyage de la base de données, consultez [cette section](../../production/using/database-cleanup-workflow.md).

>[!NOTE]
>
>Pour les utilisateurs et utilisatrices de Campaign v8 Managed Cloud Services, le workflow de nettoyage de la base de données est surveillé et géré par Adobe.

### Spécificités de la quarantaine des notifications push {#push-quarantine-specifics}

Pour Campaign Classic v7, les quarantaines des notifications push suivent le mécanisme général de mise en quarantaine avec certains comportements spécifiques aux canaux.

Pour les notifications push **iOS** et **Android**, le mécanisme de quarantaine utilise des jetons d’appareil plutôt que des adresses e-mail. Lorsqu&#39;une application mobile est désinstallée ou réinstallée, le jeton associé est mis en quarantaine.

Pour plus d&#39;informations sur les scénarios de quarantaine des notifications push (types d&#39;erreur iOS et Android, comportement des reprises, etc.), reportez-vous à la documentation [Comprendre les échecs de diffusion](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} qui comprend des tableaux complets sur les types d&#39;erreur des notifications push.

### Spécifications de la quarantaine SMS {#sms-quarantine-specifics}

Pour Campaign Classic v7, les quarantaines des SMS suivent le mécanisme général de mise en quarantaine avec certains comportements spécifiques aux canaux liés aux numéros de téléphone plutôt qu’aux adresses e-mail.

Le mécanisme de mise en quarantaine des SMS varie en fonction du connecteur utilisé :

* **Connecteurs SMPP standard** : les règles de qualification des erreurs définies dans **[!UICONTROL Administration > Gestion de campagne > Gestion des échecs > Qualification des logs de diffusion]** s’appliquent aux diffusions SMS.

* **Connecteur SMPP générique étendu** : la gestion des erreurs est traitée différemment à l&#39;aide d&#39;expressions régulières (regexes) pour analyser les messages de rapport de statut (SR) renvoyés par le fournisseur SMSC.

Pour plus d’informations sur les scénarios de mise en quarantaine des SMS et les types d’erreur, reportez-vous à la documentation [Comprendre les échecs de diffusion](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} qui comprend des tables complètes de types d’erreur SMS.

## Rubriques connexes

* [Gestion des quarantaines](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"} (documentation de Campaign v8)
* [Présentation des diffusions en échec](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} (documentation de Campaign v8)
* [&#x200B; Bonnes pratiques de diffusion &#x200B;](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} (documentation de Campaign v8)
* [Workflow de nettoyage de la base de données](../../production/using/database-cleanup-workflow.md) (v7 hybride/on-premise)
* [Configuration des reprises de diffusion](communication-channels.md) (v7 hybride/on-premise)
