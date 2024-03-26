---
product: campaign
title: Utilisation d’Adobe Campaign et Adobe Target
description: Découvrez comment intégrer Adobe Campaign à Adobe Target
feature: Target Integration
badge-v7: label="v7" type="Informative" tooltip="S’applique à Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="S’applique également à Campaign v8"
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: 2e29d090-b87b-4cff-a703-58e1da082f04
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 100%

---

# Utilisation de Campaign et Target{#integrating-with-adobe-target}



Utilisez Adobe Campaign avec Adobe Target pour optimiser le contenu des e-mails.

Pour optimiser le contenu de vos e-mails, vous pouvez créer une offre de redirection dans Adobe Target, puis utiliser Adobe Campaign pour gérer les offres par e-mail. Par exemple, vous pouvez afficher différentes offres pour les destinataires masculins et féminins.

L’intégration a lieu à l’ouverture de l’e-mail. Lorsque le client ouvre l’e-mail, un appel est effectué vers Target. Une version dynamique du contenu s’affiche alors. Le contenu se compose d’une image statique prise en charge par tous les navigateurs. Target effectue le suivi de la réaction à l’offre au niveau de l’audience ou de la session. Ces données sont disponibles dans les rapports Target. [En savoir plus dans la documentation relative à Adobe Target](https://experienceleague.adobe.com/docs/target/using/integrate/campaign-and-target.html?lang=fr).


>[!NOTE]
>
>L&#39;intégration supporte uniquement les images statiques. Le reste du contenu n&#39;est pas personnalisable.

Plusieurs types de données peuvent être exploités par Adobe Target :

* données provenant du datamart Adobe Campaign ;
* segments associés à l&#39;identifiant visiteur dans Adobe Target, si les données utilisées ne sont pas soumises à des limitations légales ;
* Données Adobe Target : agent utilisateur, adresse IP, données de géolocalisation
