---
title: Optimiser la diffusion des messages
seo-title: Optimiser la diffusion des messages
page-status-flag: never-activated
uuid: a540efc7-105d-4c7f-a2ee-ade4d22b3445
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
discoiquuid: 0cbc4e92-482f-4dac-a1fb-b738e7127938
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 5e6ecd636ee0b2199808c03b2fd898a194f0c1ea
workflow-type: tm+mt
source-wordcount: '749'
ht-degree: 63%

---


# Optimisez votre diffusion {#optimize-delivery}

Avant même de commencer à créer des diffusions, vous pouvez prendre des mesures pour sécuriser et optimiser le processus d&#39;envoi en amont.

La section suivante présente les bonnes pratiques et les procédures recommandées pour optimiser la configuration d&#39;Adobe Campaign. L&#39;application de ces pratiques permettra de limiter les problèmes que vous risquez de rencontrer en aval.

## Performances de la plate-forme

Plusieurs facteurs peuvent avoir une incidence directe sur les performances du serveur et ralentir la plate-forme :

* Nombre et type d’éléments de personnalisation : la personnalisation dans les courriers électroniques extrait les données de la base de données pour chaque destinataire. Si les éléments de personnalisation sont nombreux, la quantité de données nécessaire pour préparer la diffusion augmente.  Learn more about personalization in [this section](../../delivery/using/about-personalization.md)

* Chargement du serveur : lorsque le serveur marketing gère plusieurs tâches différentes en même temps, il peut ralentir les performances. Le serveur marketing doit coordonner toutes les données entrantes et sortantes pour toutes les diffusions afin de s’assurer que les données sont correctes et à temps.

   **CONSEIL** - Pour éviter cela, coordonnez la planification des diffusions avec les autres membres de votre équipe afin d’assurer les meilleures performances.

* Exécution du flux de travaux : la surveillance de vos workflows est essentielle pour éviter les problèmes de performances de la plate-forme. Suivez les directives énumérées [dans ce document](../../workflow/using/workflow-best-practices.md#execution-and-performance).

* En tant que client hébergé, vous pouvez tirer parti des fonctionnalités [du panneau de contrôle](https://docs.adobe.com/content/help/fr-FR/control-panel/using/discover-control-panel/key-features.html) Campaign pour surveiller votre plateforme à l’aide des fonctionnalités de surveillance [des](https://docs.adobe.com/content/help/en/control-panel/using/performance-monitoring/about-performance-monitoring.html) performances.

## Vérifier la configuration du réseau {#network-config}

Pour optimiser une diffusion lors d&#39;un envoi en masse et éviter d&#39;être pris pour un spammeur, vérifiez que vous disposez d&#39;une configuration réseau correcte qui ne cherche pas à cacher des informations.

**Conseil**:  Utilisez une adresse d’expéditeur transparente correspondant au site Web de votre marque. Par exemple, la société TravelAgency gère la chaîne d&#39;hôtels Valentino. Elle possède le domaine valentino.com pour son site web. Pour promouvoir l’hôtel Valentino à Paris, elle utilise le sous-domaine paris.valentino.com. Une adresse d’expéditeur pertinente peut donc être hotel@paris.valentino.com.

## Gestion de la délivrabilité {#deliverability-management}

Pour que vos messages arrivent dans la boîte de réception de vos destinataires sans rebond et sans être marqués comme spam, vous devez en améliorer la délivrabilité.

* Qu’est-ce que la délivrabilité ?

   * La délivrabilité désigne les facteurs qui déterminent la capacité d’un email à être accepté par le serveur d’un destinataire. Les fournisseurs d’accès à Internet (FAI) filtrent les emails qu’ils identifient comme spam ou bloquent le téléchargement des images. S’ils déterminent qu’un domaine donné envoie un trop grand nombre d’emails, ils fixent une limite au nombre d’emails qu’ils acceptent de cet expéditeur.

   * Lorsque vous vérifiez la délivrabilité de votre email, vous devez vous concentrer sur quatre catégories principales : qualité des données, message et contenu, infrastructure d’envoi et réputation. Pour une plongée plus approfondie sur ce sujet, consultez [cette section](../../delivery/using/about-deliverability.md).

* Appliquez les recommandations détaillées [dans ce document](../../delivery/using/deliverability-key-points.md).

* Contactez votre représentant d&#39;Adobe pour obtenir de l&#39;aide.

## Gestion des quarantaines {#quarantine-management}

Vous avez tout intérêt à mettre en place et à conserver de bons processus de gestion des quarantaines.

Lorsque vous commencez à envoyer des emails sur une nouvelle plate-forme, vous pouvez utiliser une liste d’adresses qui ne sont pas entièrement qualifiées. Or l’envoi à des adresses non valides ou à des adresses pièges (boîtes mails créées dans le but de piéger les spammeurs) contribue à abaisser la réputation de la plate-forme. De bons processus de gestion des quarantaines aident à : maintenez la qualité de l&#39;adresse, évitez la liste bloquée des fournisseurs d&#39;accès internet et réduisez votre taux d&#39;erreur, en accélérant les diffusions et le débit.

**Conseils**

* If you have a list of invalid addresses, Adobe recommends importing it to the quarantine table, through **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Non deliverables and addresses]**.

* Les destinataires dont l’adresse est en quarantaine sont par défaut exclus lors de l’analyse d’une diffusion : ils ne seront pas ciblés. Le taux d’erreur ayant une incidence importante sur la vitesse de diffusion, les envois sont ainsi accélérés. Une adresse email peut être mise en quarantaine par exemple lorsque la boîte de messagerie est pleine ou si l’adresse n’existe pas. [En savoir plus](#identifying-quarantined-addresses-for-a-delivery)

* Le mode de gestion des adresses en erreur par Adobe Campaign dépend du type d’erreur retourné. Voir à ce propos [cette section](../../delivery/using/understanding-quarantine-management.md).


* Certains fournisseurs d&#39;accès Internet considèrent automatiquement les emails comme du spam si le taux d&#39;adresses invalides est trop élevé. La quarantaine permet donc d’éviter d’être ajouté à une liste bloquée par ces fournisseurs.

* La gestion des quarantaines aidera également à réduire les coûts d&#39;envoi de SMS en excluant les numéros de téléphone erronés des diffusions.

## Mécanisme de double opt-in {#double-opt-in}

Pour éviter d&#39;envoyer des messages à des adresses invalides, limiter les communications abusives et améliorer la réputation de l&#39;expéditeur, Adobe recommande de mettre en place un mécanisme de double opt-in pour une confirmation après inscription. Cela vous permet de vous assurer que le destinataire est bien à l&#39;origine de l&#39;abonnement.

Les détails de la mise en oeuvre de ce mécanisme sont décrits dans [cette section](../../web/using/use-cases--web-forms.md).
