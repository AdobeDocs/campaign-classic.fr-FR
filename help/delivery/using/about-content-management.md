---
product: campaign
title: À propos de la gestion de contenu
description: Prise en main du module de gestion de contenu de Campaign
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
feature: Landing Pages, Email Design
role: User
exl-id: 87434cc2-1636-4558-ab60-255b7f873c0c
TQID: https://experienceleague.adobe.com/o8iygj4G7Hph45AwYChP9CEeXP0lmrp7n7GSbOrVC2w
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 273
ht-degree: 78%

---

# À propos de la gestion de contenu{#about-content-management}

Le module Adobe Campaign Content Manager est un [package natif](../../installation/using/installing-campaign-standard-packages.md) spécifique à Campaign Classic. Vous pouvez l’installer pour créer des newsletters récurrentes ou des sites web. Il permet de vous assister dans la création, la validation et la publication de vos messages.

>[!NOTE]
>
>Cette section fait référence au module de gestion de contenu. Pour plus d’informations sur la conception du contenu des diffusions par e-mail, consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/defining-the-email-content.html?lang=fr){target="_blank"}.

Le module de gestion de contenu intègre des fonctionnalités de groupe de travail, de workflow et d’agrégation de contenu. Il permet de mettre automatiquement en forme un message : email, courrier, SMS, web, etc.

L&#39;utilisation d&#39;un gestionnaire de contenu dans une diffusion permet de proposer des champs de saisie ou de sélection aux opérateurs en charge de la création de contenu. La mise en page et l’affichage de ce contenu, ainsi que les modifications apportées, sont gérés automatiquement à l’aide de la feuille de style.

![](assets/s_ncs_content_create_content_sample.png)

>[!CAUTION]
>
>Toute modification de la feuille de style est répercutée au niveau des diffusions créées à partir des modèles de contenus l&#39;utilisant.

La gestion de contenu offre les avantages suivants :

* Rédaction structurée des messages via des interfaces de saisie,
* Séparation des données et de leur présentation (génération au format XML),
* Génération de documents dans plusieurs formats (html, txt, XML, etc.) en se basant sur des feuilles de style pour garantir la conformité aux chartes graphiques,
* Récupération et agrégation automatique de flux de contenus externes,
* Collaboration avec workflow de validation et contrôle des données.

Ce mode de création du contenu entraîne toutefois quelques contraintes, et notamment les suivantes :

* Moins de libertés vis-à-vis du design des documents finaux,
* L&#39;analyse des besoins doit être rigoureuse afin ne pas bloquer les utilisateurs finaux par l&#39;omission d&#39;une fonctionnalité.
