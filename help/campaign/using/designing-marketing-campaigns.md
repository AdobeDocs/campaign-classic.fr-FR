---
title: Créer des campagnes marketing
seo-title: Créer des campagnes marketing
description: Créer des campagnes marketing
seo-description: null
page-status-flag: never-activated
uuid: e0fd5df6-7516-4ca6-bbdf-243a264d0283
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: about-marketing-campaigns
discoiquuid: a9eb6627-2e51-42d0-9b29-5b798bdf5b33
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 2a5711c4478f8378c079fec4792ecbb95266ad4b
workflow-type: ht
source-wordcount: '416'
ht-degree: 100%

---


# Créer des campagnes marketing{#designing-marketing-campaigns}

Adobe Campaign permet de définir, optimiser, exécuter et analyser des communications et des campagnes marketing. Adobe Campaign agit comme un véritable centre de commande et d&#39;exécution unifié de la stratégie marketing. Voir à ce propos les sections [Accéder aux opérations](../../campaign/using/accessing-campaigns.md) et [Créer des campagnes marketing](../../campaign/using/setting-up-marketing-campaigns.md).

De plus, le module **Marketing Resource Management (MRM)** complète cette application grâce à des fonctionnalités permettant la gestion complète et le tracking en temps réel des tâches, budgets et ressources marketing impliquées. Le Marketing Resource Management permet l&#39;optimisation et la régulation du management des processus internes et externes, des ressources et campagnes marketing, ainsi que des relations avec les tierces parties (agences, imprimeurs, etc.). Voir à ce sujet [cette section](../../campaign/using/about-marketing-resource-management.md).

>[!NOTE]
>
>Pour connaître les principales fonctionnalités relatives à la plate-forme Adobe Campaign, consultez la section [Prise en main](../../platform/using/about-adobe-campaign-classic.md).\
>Les fonctionnalités relatives au ciblage des populations, à la personnalisation et à la diffusion de messages personnalisés sur les différents canaux sont présentées dans [cette section](../../delivery/using/steps-about-delivery-creation-steps.md).

## Concepts de base {#core-concepts}

Dans le contexte de Campaign, les concepts listés ci-dessous doivent être connus :

* **Campagne**

   Une opération centralise tous les éléments relatifs à une campagne marketing : diffusions, règles de ciblage, coûts, fichiers d&#39;exports, documents associés, etc. Chaque opération est rattachée à un programme.

   Voir à ce sujet la section [Ajouter une opération](../../campaign/using/setting-up-marketing-campaigns.md#adding-a-campaign).

* **Programme**

   Un programme permet de définir des actions marketing pour une période calendaire : programme de lancement, de prospection, de fidélisation, etc. Chaque programme regroupe des opérations : elles sont centralisées dans le calendrier du programme auquel elles sont attachées, afin d&#39;en avoir une vue d&#39;ensemble.

* **Plan**

   Le plan marketing est composé d&#39;un ensemble de programmes unitaires. Il s&#39;inscrit dans une période calendaire, avec un budget alloué, et peut se voir rattacher des documents et objectifs à remplir.

   Voir à ce sujet la section [Calendrier des campagnes](../../campaign/using/accessing-marketing-campaigns.md#campaign-calendar).

* **Workflow**

   Un workflow d&#39;opération contient les mêmes activités que tous les workflows, mais il est propre à l&#39;opération. Il permet de créer et configurer des diffusions sur tous les canaux disponibles.

   Voir à ce propos [cette section](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow).

* **Objectifs**

   Au niveau de l&#39;opération, du programme ou du plan, vous pouvez indiquer une liste d&#39;objectifs. Il s&#39;agit de valeurs quantifiées à atteindre. Au terme de l&#39;opération, du programme ou du plan, le module MRM permet de comparer les objectifs et les résultats dans des rapports dédiés.

* **Composition de diffusion**

   Une composition est une description structurée d&#39;une diffusion. Chaque diffusion peut référencer une composition qui contient, par exemple, les offres associées, des documents à joindre ou un lien vers des magasins. En fonction de la composition sélectionnée, telle ou telle offre sera référencée dans la diffusion.

   Voir à ce sujet la section [Associer et structurer les ressources liées via une composition
de diffusion](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

