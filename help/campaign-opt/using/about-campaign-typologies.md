---
product: campaign
title: À propos des typologies de campagne
description: À propos des typologies de campagne
role: User, Data Engineer
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
feature: Typology Rules, Campaigns
exl-id: 6d5b8584-4aa1-4d9a-89d9-d41da75dd323
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 90%

---

# À propos des typologies de campagne{#about-campaign-typologies}

Le module d’optimisation des campagnes d’Adobe Campaign permet de contrôler, de filtrer et de surveiller l’envoi des diffusions. Pour éviter les conflits entre les campagnes, Adobe Campaign peut tester différentes combinaisons en appliquant des règles de contrainte spécifiques. Elles permettent de s’assurer que les messages envoyés répondent aux attentes et aux besoins des clients et des politiques de communication de l’entreprise.

![](assets/do-not-localize/how-to-video.png) [Découvrez cette fonctionnalité en vidéo](#typologies-video)

>[!NOTE]
>
>Selon votre offre, Campaign Optimization peut être inclus ou proposé sous la forme d&#39;un composant additionnel. Vérifiez votre contrat de licence.

## Règles de typologie {#typology-rules}

Avec Adobe Campaign, vous pouvez concevoir et appliquer quatre types de règles de typologie :

* Les règles de **filtrage** qui vous permettent d’exclure une partie de la cible en fonction de critères. Voir à ce sujet la section [Règles de filtrage](filtering-rules.md).
* Les règles de **pression** qui vous permettent de contrôler la lassitude marketing. Voir à ce sujet la section [Règles de pression](pressure-rules.md).
* Les règles de **capacité** qui vous permettent de limiter les charges pour garantir des conditions de traitement optimales. Voir à ce sujet la section [Contrôler la capacité](consistency-rules.md#controlling-capacity).
* Les règles de **contrôle** qui vous permettent de vérifier la validité des messages avant leur envoi. Voir à ce sujet la section [Règles de contrôle](control-rules.md).

Une fois créées, les règles de typologie sont regroupées dans des typologies de campagne qui sont référencées dans les diffusions. Voir [Appliquer les typologies](#applying-typologies).

## Typologies {#typologies}

Une typologie de campagne peut contenir plusieurs [règles de typologie](#typology-rules), mais une diffusion ne peut référencer qu&#39;une seule typologie.

L&#39;onglet **[!UICONTROL Règles]** permet d&#39;ajouter, supprimer ou visualiser les règles de typologie à appliquer.

![](assets/campaign_opt_rules_tab.png)

## Appliquer les typologies {#applying-typologies}

Vous trouverez ci-dessous les étapes nécessaires pour créer et appliquer une typologie à vos diffusions :

1. Créez des règles de typologie.

   Les règles de typologies sont regroupées sous le noeud **[!UICONTROL Administration > Gestion de campagne > Gestion des typologies > Règles de typologie]**.

   Les différents types de règles disponibles dans Campaign sont présentés dans les sections suivantes : [règles de pression commerciale](pressure-rules.md), [règles de capacité](consistency-rules.md#controlling-capacity), [règles de contrôle](control-rules.md) et [règles de filtrage](filtering-rules.md).

1. Créez une typologie et référencez les règles que vous avez créées dans celle-ci.

   Les typologies sont accessibles sous le nœud **[!UICONTROL Administration > Gestion de campagne > Gestion des typologies]** > **[!UICONTROL Typologies]**.

1. Configurez votre diffusion pour utiliser la typologie que vous avez créée. Pour plus d’informations, consultez [cette section](applying-rules.md#applying-a-typology-to-a-delivery).
1. Testez et contrôlez le comportement par le biais de simulations de campagne. Pour plus d&#39;informations sur les simulations d&#39;opérations, reportez-vous à la section [cette section](campaign-simulations.md).

Lors de la préparation de la diffusion, les destinataires sont exclus lorsque le critère est satisfait. Vous pouvez consulter les journaux pour surveiller les exclusions. Des exemples de cas d’utilisation des règles de typologie de pression sont disponibles dans [cette page](pressure-rules.md#use-cases-on-pressure-rules).

## Tutoriels vidéo {#typologies-video}

### Comment configurer la gestion de la fatigue à l’aide de règles de typologie

Cette vidéo explique comment implémenter la gestion de la fatigue dans Adobe Campaign en utilisant les règles de typologie.

>[!VIDEO](https://video.tv.adobe.com/v/25090?quality=12)

### Comment configurer la gestion de la fatigue à l&#39;aide de filtres prédéfinis

La gestion de la fatigue contrôle la fréquence et le nombre des messages afin d&#39;éviter une sollicitation excessive des destinataires. Si votre instance ne contient pas le module d&#39;optimisation de campagne, vous pouvez configurer un filtre prédéfini qui filtrera la population cible en fonction du nombre de messages reçus. Cette vidéo explique comment implémenter la gestion de la fatigue dans Adobe Campaign Classic à l&#39;aide de filtres.

>[!VIDEO](https://video.tv.adobe.com/v/25091?quality=12)

D’autres vidéos pratiques sur Campaign sont disponibles [ici](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=fr).

**Rubrique connexe**

* [Prise en main des typologies et de la gestion de la fatigue](pressure-rules.md)

