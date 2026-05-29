---
product: campaign
title: À propos du tracking web
feature: Configuration, Instance Settings
description: À propos du tracking web
role: User, Developer
exl-id: 91c31703-75e6-47a4-a877-35682dd687a9
TQID: https://experienceleague.adobe.com/FfA6FEH5WP2JJGVR4BhpjO19Yj4mt8irvyJLwuzCThs
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: d3cdead0-685a-4489-9250-4bb709942f66
feature_v2: []
subfeature_v2: []
source-git-commit: bb41e9407ab5853b0194bb325bbf3f17bc3ea232
workflow-type: tm+mt
source-wordcount: 192
ht-degree: 58%

---

# À propos du tracking web{#about-web-tracking}

Outre le suivi standard qui montre le comportement d’un internaute qui clique sur un lien dans un e-mail, la plateforme Adobe Campaign permet de collecter des informations sur la manière dont les internautes naviguent sur votre site web. Cette collecte de données est effectuée par le module de tracking Web.

Lorsqu’un internaute clique sur un lien suivi dans un e-mail d’une diffusion donnée, le serveur de redirection contacté dépose un cookie de session contenant l’identifiant broadlog (broadlogId) ainsi que l’identifiant de la diffusion (deliveryId).

Le client web envoie ensuite ce cookie au serveur chaque fois que l&#39;utilisateur visite une page contenant une balise de tracking web. Cela se poursuit tout au long de la session, c’est-à-dire jusqu’à la fermeture du client web.

Le serveur de redirection collecte donc les informations suivantes :

* l&#39;URL de la page web visitée, via un identifiant transmis en paramètre,
* la diffusion à partir de laquelle la page web est visitée, via le cookie de session,
* l&#39;identifiant de l&#39;internaute ayant cliqué, via le cookie de session,
* des informations supplémentaires, telles que le chiffre d&#39;affaires généré.

Le schéma suivant présente les étapes de la conversation entre le client et les différents serveurs.

![](assets/d_ncs_integration_webtracking_structure1.png)
