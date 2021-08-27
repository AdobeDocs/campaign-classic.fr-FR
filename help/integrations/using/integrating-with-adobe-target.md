---
product: campaign
title: Intégration avec Adobe Target
description: Intégration avec Adobe Target
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: 2e29d090-b87b-4cff-a703-58e1da082f04
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 100%

---

# Intégration avec Adobe Target{#integrating-with-adobe-target}

![](../../assets/common.svg)

L&#39;intégration entre Adobe Campaign et Adobe Target (Classic et Standard) au sein d&#39;Adobe Experience Cloud vous permet d&#39;inclure une offre d&#39;Adobe Target dans une diffusion email d&#39;Adobe Campaign.

Le principe de fonctionnement est le suivant : lorsqu&#39;un destinataire ouvre un email envoyé via Adobe Campaign, un appel vers Adobe Target permet d&#39;afficher une version dynamique du contenu. Cette version dynamique est calculée en fonction des règles définies en amont lors de la création de l&#39;email.

En savoir plus sur l’intégration d’Adobe Campaign et d’Adobe Target avec [ces quatre conseils et astuces](https://www.adobe.com/content/dam/www/us/en/marketing/campaign/pdfs/Adobe_Campaign_for_Target_Tips_and_Tricks.pdf).
>[!NOTE]
>
>L&#39;intégration supporte uniquement les images statiques. Le reste du contenu n&#39;est pas personnalisable.

Plusieurs types de données peuvent être exploités par Adobe Target :

* données provenant du datamart Adobe Campaign ;
* segments associés à l&#39;identifiant visiteur dans Adobe Target, si les données utilisées ne sont pas soumises à des limitations légales ;
* données d&#39;Adobe Target : user agent, adresse IP, données de géolocalisation.

>[!NOTE]
>
>Vous pouvez également trouver des informations relatives à l&#39;intégration entre Adobe Campaign et Adobe Target sur les [pages d&#39;aide d&#39;Adobe Target](https://experienceleague.adobe.com/docs/target/using/integrate/campaign-and-target.html?lang=fr).
