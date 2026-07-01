---
product: campaign
title: Utilisation d’Adobe Campaign et Adobe Target
description: Découvrez comment intégrer Adobe Campaign à Adobe Target
feature: Target Integration
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: 2e29d090-b87b-4cff-a703-58e1da082f04
TQID: https://experienceleague.adobe.com/f58vs0ePAH-7bcfJ8u1GKLzcz0-fHnrwFyOVUWOFW-o
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2:
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
  - id: df0d6518-6f49-46e2-b46e-3bcc513f553f
  - id: eb007b6d-6e57-46ab-9485-3f24d6102304
  - id: b1fd1501-3105-4d6b-b4d4-9af53126df75
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 209
ht-degree: 100%

---

# Utilisation de Campaign et Target{#integrating-with-adobe-target}



Utilisez Adobe Campaign avec Adobe Target pour optimiser le contenu des e-mails.

Pour optimiser le contenu de vos e-mails, vous pouvez créer une offre de redirection dans Adobe Target, puis utiliser Adobe Campaign pour gérer les offres par e-mail. Par exemple, vous pouvez afficher différentes offres pour les destinataires masculins et féminins.

L’intégration a lieu à l’ouverture de l’e-mail. Lorsque le client ouvre l’e-mail, un appel est effectué vers Target. Une version dynamique du contenu s’affiche alors. Le contenu se compose d’une image statique prise en charge par tous les navigateurs. Target effectue le suivi de la réaction à l’offre au niveau de l’audience ou de la session. Ces données sont disponibles dans les rapports Target. [En savoir plus dans la documentation relative à Adobe Target](https://experienceleague.adobe.com/docs/target/using/integrate/campaign-and-target.html?lang=fr).


>[!NOTE]
>
>L&#39;intégration prend uniquement en charge les images statiques. Le reste du contenu n’est pas personnalisable.

Plusieurs types de données peuvent être exploités par Adobe Target :

* données provenant du datamart Adobe Campaign ;
* segments associés à l&#39;identifiant visiteur dans Adobe Target, si les données utilisées ne sont pas soumises à des limitations légales ;
* Données Adobe Target : agent utilisateur, adresse IP, données de géolocalisation
