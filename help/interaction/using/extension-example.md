---
product: campaign
title: Exemple d'extension
description: Exemple d'extension
feature: Interaction, Offers
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: d4acf99b-cef4-48f7-b4cd-c032ec12592f
TQID: 'https://experienceleague.adobe.com/TQZaYrJop03HAw47XPFqgmoxb073iC-xztTp-f-5dEk'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b6fcaf36-3bc4-4604-94f3-81b5d3f41ecf
    internal-label: Offer Management
  - id: 65702805-0026-5ca1-843a-144fa79f0883
    internal-label: Interaction
  - id: ea08db70-4682-59a2-9408-9aedd9548e07
    internal-label: Offers
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: e739ee2b-6228-412e-878f-45de0791417d
    internal-label: Use cases
source-git-commit: 323ff901668895588a6e9587fa2a8b7804cf2fb4
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 85%
---
# Exemple d&#39;extension{#extension-example}



Dans le cas d&#39;un contact entrant (centre d&#39;appel ou site web), les offres les plus pertinentes sont proposées à un contact donné grâce à un ensemble de règles d&#39;éligibilité. Pour enrichir les critères d’éligibilité de vos offres, étendez le schéma **nms:interaction**.

* Pour ajouter un nouveau contexte d’interaction, étendez le schéma **nms:interaction** et créez autant d’éléments **attribute** que nécessaire dans le schéma.

  Dans l&#39;exemple suivant, les critères ajoutés sont le code du pays et la dernière page visitée.

  ![](assets/s_ncs_configuration_offer_schemas.png)

* Vous pourrez ensuite utiliser les attributs précédemment créés lors de la définition des critères d&#39;éligibilité.

  Dans l&#39;exemple suivant, il est possible de créer des critères d&#39;éligibilité pour afficher une offre en fonction du pays de l&#39;internaute ou de la dernière page sur laquelle il se sera rendu lors de sa navigation sur le site web concerné.

  ![](assets/s_ncs_configuration_offer_context.png)

* Lors du paramétrage des appels SOAP, insérez l&#39;élément XML **context** pour référencer les informations contextuelles ajoutées dans le schéma d&#39;interaction. Pour plus d’informations, consultez la section [Intégration via SOAP (côté serveur)](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/offers/inbound/interaction-integration){target="_blank"} (documentation de Campaign v8).
