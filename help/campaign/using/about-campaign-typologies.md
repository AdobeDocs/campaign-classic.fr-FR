---
title: A propos des typologies de campagne
seo-title: A propos des typologies de campagne
description: A propos des typologies de campagne
seo-description: null
page-status-flag: never-activated
uuid: ec89fb14-7e2f-4e9f-b7ab-3c2caf93a697
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: campaign-optimization
discoiquuid: 72c5151c-ce1e-425a-9aee-beefe9f21a67
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# A propos des typologies de campagne{#about-campaign-typologies}

Campaign Optimization est le module d&#39;Adobe Campaign qui permet de contrôler, filtrer et suivre l&#39;envoi des diffusions. Afin d&#39;éviter les conflits entre les campagnes, Adobe Campaign peut tester différentes combinaisons en appliquant des règles de contraintes spécifiques. Vous pourrez ainsi vous assurer que les messages envoyés répondent le mieux possible aux attentes ou aux besoins du client, dans le respect de la cohérence de la communication de l&#39;entreprise.

>[!NOTE]
>
>Selon votre offre, Campaign Optimization peut être inclus ou proposé sous la forme d&#39;un composant additionnel. Vérifiez votre contrat de licence.

## Règles de typologie {#typology-rules}

Avec Adobe Campaign, vous pouvez concevoir et appliquer quatre types de règles de typologie :

1. **Règles de filtrage** qui vous permettent d’exclure une partie de la cible en fonction de critères. For more on this, refer to [Filtering rules](../../campaign/using/filtering-rules.md).
1. **Règles de pression** qui vous permettent de contrôler la fatigue du marketing. For more on this, refer to [Pressure rules](../../campaign/using/pressure-rules.md).
1. **Règles de capacité** qui vous permettent de limiter les charges pour garantir des conditions de traitement optimales. For more on this, refer to [Controlling capacity](../../campaign/using/consistency-rules.md#controlling-capacity).
1. **Règles de contrôle** qui vous permettent de vérifier la validité des messages avant leur envoi. For more on this, refer to [Control rules](../../campaign/using/control-rules.md).

Une fois créées, les règles de typologie sont regroupées dans des typologies de campagne, qui sont référencées dans les diffusions. Reportez-vous à la section [Appliquer les typologies](#applying-typologies).

## Typologies {#typologies}

Une typologie de campagne peut contenir plusieurs [règles de typologie](#typology-rules), mais une diffusion ne peut référencer qu&#39;une seule typologie.

L&#39;onglet **[!UICONTROL Règles]** permet d&#39;ajouter, supprimer ou visualiser les règles de typologie à appliquer.

![](assets/campaign_opt_rules_tab.png)

## Appliquer les typologies {#applying-typologies}

Vous trouverez ci-dessous les étapes nécessaires pour créer et appliquer une typologie à vos diffusions :

1. Créez des règles de typologie.

   Les règles de typologies sont regroupées sous le noeud **[!UICONTROL Administration > Gestion de campagne > Gestion des typologies > Règles de typologie]**.

   Les différents types de règles disponibles dans Campaign sont présentés dans les sections suivantes : [règles de pression commerciale](../../campaign/using/pressure-rules.md), [règles de capacité](../../campaign/using/consistency-rules.md#controlling-capacity), [règles de contrôle](../../campaign/using/control-rules.md) et [règles de filtrage](../../campaign/using/filtering-rules.md).

1. Créez une typologie et référencez les règles que vous avez créées dans celle-ci.

   Les typologies sont accessibles sous le nœud **[!UICONTROL Administration > Gestion de campagne > Gestion des typologies]** > **[!UICONTROL Typologies]**.

1. Configurez votre diffusion pour utiliser la typologie que vous avez créée. Pour plus d&#39;informations, consultez [cette section](../../campaign/using/applying-rules.md#applying-a-typology-to-a-delivery).
1. Testez et contrôlez le comportement par le biais de simulations de campagnes. Pour plus d&#39;informations sur les simulations de campagnes, consultez [cette section](../../campaign/using/campaign-simulations.md).

Pendant la préparation de la diffusion, les destinataires sont exclus lorsque le critère est satisfait. Vous pouvez consultez les logs pour suivre les exclusions. Des exemples d&#39;utilisation des règles de typologie de pression sont disponibles sur [cette page](../../campaign/using/pressure-rules.md#use-cases-on-pressure-rules).

**Rubrique connexe**

* [Appliquer des règles de fonctionnement automatiques aux livraisons sur n’importe quel canal](https://helpx.adobe.com/campaign/kb/simplifying-campaign-management-acc.html#Applyautomaticbusinessrulestodeliveriesonanychannel)