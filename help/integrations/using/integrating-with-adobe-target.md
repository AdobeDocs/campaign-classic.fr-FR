---
product: campaign
title: Intégration avec Adobe Target
description: Intégration avec Adobe Target
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: 2e29d090-b87b-4cff-a703-58e1da082f04
source-git-commit: b6e24c63ece12f25b7dafe3fede9e38b3aab2427
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 40%

---

# Intégration avec Adobe Target{#integrating-with-adobe-target}

![](../../assets/common.svg)

Utilisez Adobe Campaign avec Adobe Target pour optimiser le contenu des emails.

Pour optimiser le contenu de vos emails, vous pouvez créer une offre de redirection dans Adobe Target, puis utiliser Adobe Campaign pour gérer les offres par email. Par exemple, vous pouvez afficher différentes offres pour les destinataires masculins et féminins.

L’intégration a lieu à l’ouverture de l’email. Lorsque le client ouvre l’e-mail, un appel est lancé vers Target et une version dynamique du contenu s’affiche. Le contenu se compose d’une image statique prise en charge par tous les navigateurs. Target effectue le suivi de la réaction à l’offre au niveau de l’audience ou de la session et ces données sont disponibles dans les rapports Target. [En savoir plus dans la documentation Adobe Target](https://experienceleague.adobe.com/docs/target/using/integrate/campaign-and-target.html?lang=fr).


>[!NOTE]
>
>L&#39;intégration supporte uniquement les images statiques. Le reste du contenu n&#39;est pas personnalisable.

Plusieurs types de données peuvent être exploités par Adobe Target :

* données provenant du datamart Adobe Campaign ;
* segments associés à l&#39;identifiant visiteur dans Adobe Target, si les données utilisées ne sont pas soumises à des limitations légales ;
* Données Adobe Target : agent utilisateur, adresse IP, données de géolocalisation
