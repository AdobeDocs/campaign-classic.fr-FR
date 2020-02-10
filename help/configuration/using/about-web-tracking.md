---
title: A propos du suivi Web
seo-title: A propos du suivi Web
description: A propos du suivi Web
seo-description: null
page-status-flag: never-activated
uuid: 59d18ffb-c26e-4571-8364-5e85ec587349
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 38ba9be9-dabc-41d4-878c-d772955301fe
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# A propos du suivi Web{#about-web-tracking}

En complément du tracking standard, assurant le suivi du comportement d&#39;un internaute lorsqu&#39;il clique sur un lien dans un email, la plateforme Adobe Campaign offre la possibilité de collecter des informations sur la navigation des internautes sur votre site web. Cette collecte est assurée par le module de webtracking.

Lorsqu&#39;un internaute clique sur un lien tracké dans un email d&#39;une diffusion donnée, le serveur de redirection contacté pose un cookie de session contenant l&#39;identifiant du broadlog (broadlogId) et l&#39;identifiant de la diffusion (deliveryId).

Le client Web transmettra alors ce cookie au serveur à chaque fois qu&#39;il visitera une page contenant une balise de tracking Web, ceci pendant toute la durée de la session, c&#39;est-à-dire jusqu&#39;à ce que le client Web soit fermé.

Le serveur de redirection collecte donc les informations suivantes :

* l&#39;URL de la page web visitée, via un identifiant transmis en paramètre,
* la diffusion à partir de laquelle la page web est visitée, via le cookie de session,
* l&#39;identifiant de l&#39;internaute ayant cliqué, via le cookie de session,
* des informations supplémentaires, telles que le chiffre d&#39;affaires généré.

Le schéma suivant présente les étapes de la conversation entre le client et les différents serveurs.

![](assets/d_ncs_integration_webtracking_structure1.png)

