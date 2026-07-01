---
product: campaign
title: Power Booster et Power Cluster
description: Power Booster et Power Cluster
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 59364cfc-9917-4057-ad5f-fbca7e261b07
TQID: https://experienceleague.adobe.com/lcr5Xfipd9cDuglWBqBsiVXJUUZqQxLEmzzZPrAEhHU
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a7760dfc-5c44-4d77-bb68-c50b1e265c93
subfeature_v2: id: ac9c0a9c-8a76-4419-bd64-9c34c5782666id: fb2a841f-c522-491f-9901-a1b939d252df
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080bid: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: bb41e9407ab5853b0194bb325bbf3f17bc3ea232
workflow-type: ht
source-wordcount: 416
ht-degree: 100%

---

# Power Booster et Power Cluster{#power-booster-and-power-cluster}



## Vue d&#39;ensemble {#overview}

Adobe Campaign fournit deux séries d&#39;options architecturales pré-packagées permettant de dimensionner votre déploiement :

* **Power Booster**

  Cette option permet la prise en charge d’une instance d’exécution supplémentaire découplée de l’instance d’application Adobe Campaign principale.Les instances d’exécution dédiées peuvent être hébergées à distance ou par un tiers.Lorsqu’elle est implémentée, l’exécution des e-mails, le tracking, les pages miroir et les messages de rebond sont gérés indépendamment des fonctions de l’application centrale.

* **Power Cluster**

  Cette option permet la prise en charge de 2 à N instances d’exécution en cluster découplées de l’instance d’application Adobe Campaign principale par rapport à une application donnée.Les clusters peuvent être hébergés à distance, dans des déploiements distribués et par des tiers.Outre les avantages de l’isolation des processus, l’option Adobe Campaign Power Cluster permet des stratégies de redondance et d’évolutivité à l’aide de matériel standard pour une évolution simplifiée du SLA ou des performances.

![](assets/architectural_options_diagram.png)

## Applications éligibles {#eligible-applications}

Les options Power Booster et Power Cluster peuvent être exploitées par les applications suivantes :

* Campagne
* Diffusion
* Message Center

## Matrice de recommandations architecturales {#matrix-of-architectural-recommendations}

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>Architecture standard</strong><br /> </td> 
   <td> <strong>Power Booster</strong><br /> </td> 
   <td> <strong>Power Cluster</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Campagnes e-mail et interactions sortantes<br /> </td> 
   <td> Jusqu'à environ 30 millions d'emails par mois<br /> </td> 
   <td> 30-100 millions d'emails par mois<br /> </td> 
   <td> Au-delà de 100 millions d'emails par mois<br /> </td> 
  </tr> 
  <tr> 
   <td> Messages transactionnels<br /> </td> 
   <td> 50 000 par heure par serveur d’exécution<br /> </td> 
   <td> 50 000 par heure par serveur d’exécution<br /> </td> 
   <td> 50 000 par heure par serveur d’exécution<br /> </td> 
  </tr> 
  <tr> 
   <td> Disponibilité<br /> </td> 
   <td> Celle de la base principale<br /> </td> 
   <td> 24/7 sauf pour maintenance et
arrêts de l'instance d'exécution<br /> </td> 
   <td> Service 24/7/365 possible<br /> </td> 
  </tr> 
  <tr> 
   <td> Sécurité<br /> </td> 
   <td> Datamart est potentiellement accessible depuis l'internet public<br /> </td> 
   <td> Datamart isolé des composants frontaux
exposés sur l'internet public<br /> </td> 
   <td> Datamart isolé des composants frontaux
exposés sur l'internet public<br /> </td> 
  </tr> 
  <tr> 
   <td> Modèle de déploiement<br /> </td> 
   <td> Tout sur site (peut être on premise ou bien dans le cloud)<br /> </td> 
   <td> Fonctions marketing on premise avec une exécution dans le cloud possible<br /> </td> 
   <td> Fonctions marketing on premise avec une exécution dans le cloud possible ; exécution dans de multiples géographies possible<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Recommandations {#recommendations}

* Une instance d’exécution doit être dédiée à un service.Vous ne pouvez pas installer un package pour un service auquel vous n’avez pas souscrit d’abonnement.Par exemple, si vous avez souscrit à l&#39;option **Power Booster** pour le service **Message Center**, vous ne pouvez installer que le package **[!UICONTROL Exécution des messages transactionnels]** sur l&#39;instance d&#39;exécution dédiée. Veuillez vérifier votre contrat de licence.
* Dans la mesure où les instances dédiées (ou clusters) sont des instances Adobe Campaign, les recommandations sont les mêmes que pour une instance principale. Voir à ce sujet [ce document](../../production/using/foreword.md).
* Pour dimensionner correctement l&#39;instance d&#39;un point de vue base de données/composants matériels, nous vous invitons à vous rapprocher des services professionnels d&#39;Adobe Campaign.
