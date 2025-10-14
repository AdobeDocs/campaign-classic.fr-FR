---
product: campaign
title: Conception et exécution de campagnes marketing
description: Définissez, optimisez, exécutez et analysez des campagnes marketing.
role: User
feature: Campaigns
hide: true
hidefromtoc: true
exl-id: 4e0df18f-3623-4dfb-a2f8-ad293dbc4dd5
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 95%

---

# Conception et exécution de campagnes marketing{#designing-marketing-campaigns}


Adobe Campaign vous permet de définir, d’optimiser, d’exécuter et d’analyser des campagnes marketing et de communication. Adobe Campaign agit comme un centre de commande et d’exécution unifié pour les stratégies marketing. Pour plus d’informations à ce sujet, reportez-vous aux sections [Accès aux campagnes](../../distributed/using/accessing-campaigns.md) et [Création de campagnes marketing](../../campaign/using/setting-up-marketing-campaigns.md).

De plus, le module **Gestion des ressources marketing (MRM)** vous permet de contrôler les actions marketing de façon collaborative à travers la gestion complète et le tracking en temps réel des tâches, budgets et ressources marketing impliqués. La gestion des ressources marketing permet d’optimiser et de réguler la gestion des processus internes et externes, des ressources et des campagnes marketing, ainsi que des relations tierces (agences, imprimeurs, etc.). Pour plus d’informations, consultez [cette section](../../mrm/using/about-marketing-resource-management.md).

>[!NOTE]
>
>Pour plus d’informations sur les fonctionnalités de base d’Adobe Campaign, reportez-vous à [cette section](../../platform/using/about-adobe-campaign-classic.md).\
>Les fonctionnalités relatives au ciblage de la population, à la personnalisation des messages et à la diffusion des messages sur les différents canaux sont présentées dans la documentation de [Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html){target="_blank"}.

![](assets/do-not-localize/how-to-video.png) [Découvrir les concepts clés des campagnes marketing dans une vidéo](#video)

## Concepts de base {#core-concepts}

Dans le contexte de Campaign, les concepts listés ci-dessous doivent être connus :

* **Opération**

  Une opération centralise tous les éléments relatifs à une campagne marketing : diffusions, règles de ciblage, coûts, fichiers d&#39;exports, documents associés, etc. Chaque opération est rattachée à un programme.

  Voir à ce sujet la section [Ajouter une opération](../../campaign/using/setting-up-marketing-campaigns.md#adding-a-campaign).

* **Programme**

  Un programme permet de définir des actions marketing pour une période calendaire : programme de lancement, de prospection, de fidélisation, etc. Chaque programme regroupe des opérations : elles sont centralisées dans le calendrier du programme auquel elles sont attachées, afin d’en avoir une vue d’ensemble.

* **Plan**

  Le plan marketing est composé d&#39;un ensemble de programmes unitaires. Il s&#39;inscrit dans une période calendaire, avec un budget alloué, et peut se voir rattacher des documents et objectifs à remplir.

  Voir à ce sujet la section [Calendrier des campagnes](../../campaign/using/accessing-marketing-campaigns.md#campaign-calendar).

* **Workflow**

  Un workflow d&#39;opération contient les mêmes activités que tous les workflows, mais il est propre à l&#39;opération. Il permet de créer et configurer des diffusions sur tous les canaux disponibles.

  Pour plus d’informations, consultez [cette section](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow).

* **Objectifs**

  Au niveau de l&#39;opération, du programme ou du plan, vous pouvez indiquer une liste d&#39;objectifs. Il s&#39;agit de valeurs quantifiées à atteindre. Au terme de l&#39;opération, du programme ou du plan, le module MRM permet de comparer les objectifs et les résultats dans des rapports dédiés.

* **Composition de diffusion**

  Une composition est une description structurée d&#39;une diffusion. Chaque diffusion peut référencer une composition qui contient, par exemple, les offres associées, des documents à joindre ou un lien vers des magasins. En fonction de la composition sélectionnée, telle ou telle offre sera référencée dans la diffusion.

  Pour plus d’informations, consultez [cette section](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

## Tutoriel {#video}

Cette vidéo présente les concepts clés des campagnes marketing.

>[!VIDEO](https://video.tv.adobe.com/v/35131?quality=12)

D’autres vidéos pratiques sur Campaign Classic sont disponibles [ici](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=fr).
