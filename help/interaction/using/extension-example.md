---
title: Exemple d'extension
seo-title: Exemple d'extension
description: Exemple d'extension
seo-description: null
page-status-flag: never-activated
uuid: 6703b6e8-4eac-4a94-a80a-a7cd71b25cdf
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: advanced-parameters
discoiquuid: 990b6cbc-9b7b-4278-a635-653d5abafe87
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Exemple d&#39;extension{#extension-example}

Dans le cas d&#39;un contact entrant (centre d&#39;appel ou site web), les offres les plus pertinentes sont proposées à un contact donné grâce à un ensemble de règles d&#39;éligibilité. Pour enrichir les critères d&#39;éligibilité de vos offres, il est nécessaire d&#39;étendre le schéma **nms:interaction**.

* Pour ajouter un nouveau contexte d&#39;interaction, étendez le schéma **nms:interaction** et créez autant d&#39;éléments **attribute** que nécessaire dans le schéma.

   Dans l&#39;exemple suivant, les critères ajoutés sont le code du pays et la dernière page visitée.

   ![](assets/s_ncs_configuration_offer_schemas.png)

* Vous pourrez ensuite utiliser les attributs précédemment créés lors de la définition des critères d&#39;éligibilité.

   Dans l&#39;exemple suivant, il est possible de créer des critères d&#39;éligibilité pour afficher une offre en fonction du pays de l&#39;internaute ou de la dernière page sur laquelle il se sera rendu lors de sa navigation sur le site web concerné.

   ![](assets/s_ncs_configuration_offer_context.png)

* When configuring SOAP calls, insert the **context** XML element to reference context information added in the interaction schema. Pour plus d’informations, voir [Intégration via SOAP (côté serveur)](../../interaction/using/integration-via-soap--server-side-.md).

