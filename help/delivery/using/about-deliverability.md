---
title: À propos de la délivrabilité dans Adobe Campaign Classic
description: En savoir plus sur la gestion de la délivrabilité dans Adobe Campaign Classic.
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
source-git-commit: 68756f920fbc8658cff552615adbf023b4c5e3aa

---


# A propos de la délivrabilité{#about-deliverability}

Adobe Campaign propose un certain nombre d’outils pour suivre les performances de délivrabilité de votre plateforme. Cette section met également en évidence les principes principaux que vous devez garder à l&#39;esprit lors de la gestion et de l&#39;optimisation de la délivrabilité.

## Configuration {#configuration}

Cette fonctionnalité est disponible via un pack dédié dans Adobe Campaign. Pour l&#39;utiliser, ce package doit être installé. Une fois terminé, redémarrez le serveur pour que le package soit pris en compte.
* Pour les clients hébergés et hybrides, la surveillance **de la** délivrabilité est configurée sur votre instance par l’assistance technique et les consultants d’Adobe. Pour plus d’informations, contactez votre gestionnaire de compte Adobe.

* Pour les installations sur site, vous devez installer le package de surveillance de la **[!UICONTROL délivrabilité (délivrabilité du courrier électronique)]** via le menu **[!UICONTROL Outils]** > **[!UICONTROL Avancé]** > **[!UICONTROL Importer le package.]** Pour plus d’informations, voir [Installation des packs](../../installation/using/installing-campaign-standard-packages.md)standard Campaign Classic.

Dans Adobe Campaign Classic, la surveillance **de la** délivrabilité est gérée par le processus **[!UICONTROL Actualiser pour la délivrabilité]** . Il est installé par défaut sur toutes les instances et vous permet d’initialiser la liste des règles de qualification du courrier de retour, la liste des domaines et la liste des MX. Une fois le package de surveillance de la **[!UICONTROL délivrabilité (délivrabilité des e-mails)]** installé, ce flux de travail s’exécute de nuit pour mettre à jour régulièrement la liste des règles et vous permet de gérer activement la délivrabilité des plateformes.

## Informations générales {#background}

La délivrabilité des emails présente un défi majeur pour les responsables marketing, qu’ils envoient un millier de messages ou plusieurs milliards. Un message sur cinq n’arrive jamais dans la boîte de réception ou n’atteint jamais le destinataire visé.

Autrefois considéré comme un « problème technique » pour le service informatique, la délivrabilité des emails est aujourd&#39;hui au cœur des préoccupations des marketeurs, car bien que nombre de ses éléments soient de nature technique, il s&#39;agit d&#39;un problème commercial avec une influence importante sur le chiffre d&#39;affaires.

Prenez l&#39;entonnoir du marketing email. La délivrabilité détermine le nombre de messages reçus, ce qui, à son tour, a un impact sur chaque étape suivante de l&#39;entonnoir. Un nombre inférieur d&#39;emails reçus a pour résultat un nombre inférieur d&#39;ouvertures, moins de clics et moins de conversions. **Pour les entreprises dont la base de données est volumineuse, la différence entre une délivrabilité moyenne et une forte délivrabilité peut se traduire par un chiffre d&#39;affaires de plusieurs centaines à quelques milliers de dollars.**

![](assets/deliverability_overview_1.png)

En se contentant d&#39;une délivrabilité moyenne (80 %), les marketeurs passent à côté d&#39;un nombre important de conversions et d&#39;une hausse de leur chiffre d&#39;affaires.

Qu&#39;est-ce exactement la délivrabilité des emails ? Comment les marketeurs peuvent-ils améliorer les taux de délivrabilité pour élargir l&#39;embouchure de l&#39;entonnoir et y obtenir plus de résultats de leurs campagnes email ?

La délivrabilité des emails désigne l&#39;ensemble des caractéristiques qui déterminent la capacité d&#39;un message à atteindre sa destination, via une adresse email personnelle, en peu de temps, et avec la qualité attendue en termes de contenu et de format. Ces caractéristiques se divisent en quatre catégories principales : qualité des données, message et contenu, infrastructure d&#39;envoi et réputation. Ensemble, elles forment la base d&#39;un programme performant de délivrabilité des emails. Cette vue d&#39;ensemble présente les quatre principes fondamentaux d&#39;une délivrabilité des emails performante et décrit les bonnes pratiques pour que les messages atteignent la boîte de réception et que le chiffre d&#39;affaires généré à partir des programmes de marketing email soit plus élevé.

![](assets/deliverability_overview_2.png)
