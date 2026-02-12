---
product: campaign
title: Conception et exécution de campagnes marketing
description: Définir, optimiser, exécuter et analyser des campagnes marketing
role: User
feature: Campaigns
hide: true
hidefromtoc: true
exl-id: 4e0df18f-3623-4dfb-a2f8-ad293dbc4dd5
source-git-commit: df014d3f3029a61176e5117e27f3d2e8228fc407
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 80%

---


# Conception et exécution de campagnes marketing{#designing-marketing-campaigns}

[!DNL Adobe Campaign] vous permet de définir, d’optimiser, d’exécuter et d’analyser des campagnes marketing et de communication. [!DNL Adobe Campaign] agit comme un centre de commande et d’exécution unifié pour les stratégies marketing. Pour plus d’informations à ce sujet, reportez-vous aux sections [Accès aux campagnes](../../distributed/using/accessing-campaigns.md) et [Création de campagnes marketing](../../campaign/using/setting-up-marketing-campaigns.md).

De plus, le module **Marketing Resource Management (MRM)** vous permet de contrôler les actions marketing de manière collaborative en assurant une gestion complète et le tracking en temps réel des tâches, budgets et ressources marketing impliquées. Marketing Resource Management vous permet d’optimiser et de réguler la gestion des processus, ressources et campagnes marketing internes et externes. Il prend également en charge les relations avec des tiers (agences, imprimeurs, etc.). Pour plus d’informations, consultez [cette section](../../mrm/using/about-marketing-resource-management.md).

>[!NOTE]
>
>Pour plus d’informations sur les [!DNL Adobe Campaign] fonctionnalités de base, consultez [cette section](../../platform/using/about-adobe-campaign-classic.md).
>
>Les fonctionnalités relatives au ciblage des populations, à la personnalisation et à la diffusion de messages sur les différents canaux sont présentées dans la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html?lang=fr){target="_blank"}.


![Miniature vidéo pratique](assets/do-not-localize/how-to-video.png) [Découvrez en vidéo les concepts clés des campagnes marketing](#video)

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

D’autres vidéos pratiques [!DNL Campaign Classic] sont disponibles [ici](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=fr).
