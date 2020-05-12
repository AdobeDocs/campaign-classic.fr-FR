---
title: A propos de la délivrabilité dans Adobe Campaign Classic
description: En savoir plus sur la gestion de la délivrabilité dans Adobe Campaign Classic.
page-status-flag: never-activated
uuid: 2681042b-3018-42ae-b252-2367b56616bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 6a394eeb-fbe1-4712-bb13-db5d7965fb73
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e6617614ae22b73c6783f9775f441e5e25ae19e3
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 100%

---


# A propos de la délivrabilité{#about-deliverability}

**La délivrabilité consiste à mesurer le succès de vos campagnes atteignant la boîte de réception de vos destinataires sans rebonds ou sans être marqués comme spam.**

Adobe Campaign propose un certain nombre d&#39;outils pour suivre les performances de délivrabilité de votre plateforme. Cette section met également en évidence les principes essentiels que vous devez garder à l&#39;esprit pour la gestion et de l&#39;optimisation de la délivrabilité.

## Configuration {#configuration}

Cette fonctionnalité est disponible via un package dédié d&#39;Adobe Campaign. Pour l’utiliser, ce package doit être installé. Une fois l&#39;installation terminée, redémarrez le serveur pour que le package soit pris en compte.
* Pour les clients hébergés et hybrides, la **supervision de la délivrabilité** est configurée sur votre instance par l&#39;assistance technique et les consultants d&#39;Adobe. Pour plus d&#39;informations, contactez votre chargé de compte Adobe.

* Pour les installations on-premise, vous devez installer le package **[!UICONTROL Supervision de la délivrabilité (Email Deliverability)]** via le menu **[!UICONTROL Outils]** > **[!UICONTROL Avancé]** > **[!UICONTROL Import de package]**. Pour plus d&#39;informations, voir la section [Installer des packages standard Campaign Classic](../../installation/using/installing-campaign-standard-packages.md).

Dans Adobe Campaign Classic, la **supervision de la délivrabilité** est gérée par le workflow **[!UICONTROL Mise à jour pour la délivrabilité]**. Il est installé par défaut sur toutes les instances et permet d&#39;initialiser la liste des règles de qualification des emails bounce, la liste des domaines et la liste des MX. Une fois le package **[!UICONTROL Supervision de la délivrabilité (Email Deliverability)]** installé, ce workflow s&#39;exécute de nuit pour mettre à jour régulièrement la liste des règles et vous permettre de gérer activement la délivrabilité des plateformes.

## Informations générales {#background}

La délivrabilité des emails présente un défi majeur pour les responsables marketing, qu’ils envoient un millier de messages ou plusieurs milliards. Un message sur cinq n’arrive jamais dans la boîte de réception ou n’atteint jamais le destinataire visé.

Autrefois considéré comme un « problème technique » pour le service informatique, la délivrabilité des emails est aujourd&#39;hui au cœur des préoccupations des marketeurs, car bien que nombre de ses éléments soient de nature technique, il s&#39;agit d&#39;un problème commercial avec une influence importante sur le chiffre d&#39;affaires.

Prenez l&#39;entonnoir du marketing email. La délivrabilité détermine le nombre de messages reçus, ce qui, à son tour, a un impact sur chaque étape suivante de l&#39;entonnoir. Un nombre inférieur d&#39;emails reçus a pour résultat un nombre inférieur d&#39;ouvertures, moins de clics et moins de conversions. **Pour les entreprises dont la base de données est volumineuse, la différence entre une délivrabilité moyenne et une forte délivrabilité peut se traduire par un chiffre d&#39;affaires de plusieurs centaines à quelques milliers de dollars.**

![](assets/deliverability_overview_1.png)

En se contentant d&#39;une délivrabilité moyenne (80 %), les marketeurs passent à côté d&#39;un nombre important de conversions et d&#39;une hausse de leur chiffre d&#39;affaires.

Qu&#39;est-ce exactement la délivrabilité des emails ? Comment les marketeurs peuvent-ils améliorer les taux de délivrabilité pour élargir l&#39;embouchure de l&#39;entonnoir et y obtenir plus de résultats de leurs campagnes email ?

La délivrabilité des emails désigne l&#39;ensemble des caractéristiques qui déterminent la capacité d&#39;un message à atteindre sa destination, via une adresse email personnelle, en peu de temps, et avec la qualité attendue en termes de contenu et de format. Ces caractéristiques se divisent en quatre catégories principales : qualité des données, message et contenu, infrastructure d&#39;envoi et réputation. Ensemble, elles forment la base d&#39;un programme performant de délivrabilité des emails. Cette vue d&#39;ensemble présente les quatre principes fondamentaux d&#39;une délivrabilité des emails performante et décrit les bonnes pratiques pour que les messages atteignent la boîte de réception et que le chiffre d&#39;affaires généré à partir des programmes de marketing email soit plus élevé.

<!--![](assets/deliverability_overview_2.png)-->
