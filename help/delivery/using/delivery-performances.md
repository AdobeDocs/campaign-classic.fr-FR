---
product: campaign
title: Bonnes pratiques des performances de diffusion
description: En savoir plus sur les performances et les bonnes pratiques de diffusion
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
feature: Deliverability
role: User, Developer
exl-id: cc793d7b-0a26-4a75-97ed-d79c87d9b3b8
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 100%

---

# Bonnes pratiques des performances de diffusion {#delivery-performances}

Nous vous recommandons de suivre les instructions ci-dessous pour vous assurer que vos diffusions fonctionnent bien, ainsi que les vérifications effectuées si vous rencontrez des problèmes de diffusions.

**Rubriques connexes :**

* [Tableau de bord de la diffusion](delivery-dashboard.md)
* [Résolution des problèmes liés aux diffusions](delivery-troubleshooting.md)
* [À propos de la délivrabilité](about-deliverability.md)

## Bonnes pratiques relatives aux performances {#best-practices-performance}

* Ne gardez pas les diffusions en échec sur l&#39;instance, car cela conserve les tables temporaires et a un impact sur les performances.

* Supprimez les diffusions devenues inutiles.

* Les destinataires inactifs au cours des 12 derniers mois doivent être supprimés de la base de données pour maintenir la qualité des adresses.

* N&#39;essayez pas de planifier des diffusions volumineuses ensemble. 5 à 10 minutes sont nécessaires pour répartir la charge uniformément sur le système. Coordonnez la planification des diffusions avec les autres membres de votre équipe afin d&#39;optimiser les performances. Lorsque le serveur marketing gère simultanément trop de tâches différentes, cela peut diminuer les performances.

* Maintenez la taille des emails au plus petit volume possible. La taille maximale recommandée pour un email est d&#39;environ 35 Ko. La taille d&#39;un diffusion par email génère un certain volume dans les serveurs d&#39;envoi.

* Les diffusions volumineuses, notamment celles adressées à plus d&#39;un million de destinataires, ont besoin d&#39;espace dans les files d&#39;attente d&#39;envoi. Il ne s&#39;agit pas seulement d&#39;un problème de serveur. En effet, la combinaison de dizaines d&#39;autres diffusions volumineuses et simultanées peut introduire un délai d&#39;envoi.

* La personnalisation des emails extrait des informations de la base de données pour chaque destinataire. Si les éléments de personnalisation sont nombreux, la quantité de données nécessaire pour préparer la diffusion augmente.

* Indexez les adresses. Pour optimiser les performances des requêtes SQL utilisées dans l&#39;application, un index peut être déclaré à partir de l&#39;élément principal du schéma de données.

>[!NOTE]
>
>Les FAI peuvent désactiver les adresses suite à une période d&#39;inactivité. Les messages rebonds sont envoyés aux expéditeurs pour les informer de ce nouveau statut.

## Liste de contrôle des problèmes de performances {#performance-issues}

En cas de mauvaises performances des diffusions, vous pouvez vérifier les points suivants :

* **Taille de la diffusion** : l&#39;envoi de diffusions volumineuses peut prendre plus de temps. Les enfants du MTA sont configurés pour gérer une taille de batch par défaut, qui convient à la plupart des instances, mais qui doit être vérifiée lorsque les diffusions sont constamment lentes.
* **Cible de la diffusion** : les performances d’une diffusion peuvent être impactées par les rebonds temporaires, qui sont traités en fonction de la configuration des reprises. Plus le nombre des erreurs est élevé, plus les reprises sont nécessaires.
* **Charge globale de la plateforme** : il est possible que la plateforme soit affectée lorsque plusieurs diffusions volumineuses sont envoyées. Vous pouvez également vérifier la réputation IP et l’existence de problèmes de délivrabilité. Pour plus d’informations à ce sujet, consultez [cette section](about-deliverability.md) ainsi que le [Guide des bonnes pratiques relatives à la délivrabilité d’Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=fr).

La maintenance de la plateforme et de la base de données peut également impacter les performances d’envoi des diffusions. Pour plus d’informations, consultez [cette page](../../production/using/database-performances.md).
