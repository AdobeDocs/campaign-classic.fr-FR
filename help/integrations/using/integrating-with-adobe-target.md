---
title: Intégration avec Adobe Target
seo-title: Intégration avec Adobe Target
description: Intégration avec Adobe Target
seo-description: null
page-status-flag: never-activated
uuid: de482b31-0b7b-4669-8a00-28da48c6c5a9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-target
discoiquuid: 44c7acdd-6b7a-4e88-b2a7-3e9bf8a6eab5
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b0cd40d4616f7b55a1d655a1717b9c7ce8d8b6c6

---


# Intégration avec Adobe Target{#integrating-with-adobe-target}

L&#39;intégration entre Adobe Campaign et Adobe Target (Classic et Standard) au sein d&#39;Adobe Experience Cloud vous permet d&#39;inclure une offre d&#39;Adobe Target dans une diffusion email d&#39;Adobe Campaign.

Le principe de fonctionnement est le suivant : lorsqu&#39;un destinataire ouvre un email envoyé via Adobe Campaign, un appel vers Adobe Target permet d&#39;afficher une version dynamique du contenu. Cette version dynamique est calculée en fonction des règles définies en amont lors de la création de l&#39;email.

En savoir plus sur  Adobe Campaign et l’intégration d’Adobe  avec [ces quatre conseils et astuces](https://www.adobe.com/content/dam/www/us/en/marketing/campaign/pdfs/Adobe_Campaign_for_Target_Tips_and_Tricks.pdf).
>[!NOTE]
>
>L&#39;intégration supporte uniquement les images statiques. Le reste du contenu n&#39;est pas personnalisable.

Plusieurs types de données peuvent être exploités par Adobe Target :

* données provenant du datamart Adobe Campaign ;
* segments associés à l&#39;identifiant visiteur dans Adobe Target, si les données utilisées ne sont pas soumises à des limitations légales ;
* données d&#39;Adobe Target : user agent, adresse IP, données de géolocalisation.

>[!NOTE]
>
>Vous pouvez également trouver des informations relatives à l&#39;intégration entre Adobe Campaign et Adobe Target sur les [pages d&#39;aide d&#39;Adobe Target](https://marketing.adobe.com/resources/help/en_US/target/a4t/c_campaign_and_target.html).
