---
product: campaign
title: Étapes de mise en place
description: Étapes de mise en place
feature: Configuration
role: Developer
exl-id: a5ae0b61-3377-46d9-a327-6c897eeda770
TQID: https://experienceleague.adobe.com/1Euw5OREQLbcjZLR0g-QKzU3tOI9041En4Z7Uf-NTy8
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
feature_v2: []
subfeature_v2: []
source-git-commit: bb41e9407ab5853b0194bb325bbf3f17bc3ea232
workflow-type: tm+mt
source-wordcount: 244
ht-degree: 84%

---

# Etapes de mise en place{#setup-stages}

Le principe de base repose sur l&#39;ajout des balises de tracking Web dans certaines pages de votre site.

Il existe deux types de balises :

* **WEB** : cette balise permet de savoir si la page a été visitée,
* **TRANSACTION** : fonctionne comme une balise web, mais avec la possibilité d’ajouter des informations relatives, par exemple, au chiffre d’affaires généré (montant de la transaction, nombre d’articles achetés, etc.).

Les étapes pour mettre en place ces balises sont les suivantes:

1. Identifier les pages que vous souhaitez tracker et déterminer leur type (WEB ou TRANSACTION).
1. Déterminer quelles informations supplémentaires vous souhaitez collecter et étendre le schéma **nms:webTrackingLog** avec la description de ces informations. Par défaut, ce schéma propose de stocker le montant des transactions et le nombre d’articles par transaction.
1. Création des balises de tracking Web. Vous avez le choix entre les deux méthodes suivantes :

   * Insérer les URL correspondant à ces pages dans votre plateforme Adobe Campaign, puis générer et extraire les différentes balises de tracking Web associées (à partir du noeud **[!UICONTROL Ressources>On-line>Balises de tracking Web]** de la console cliente).
   * Créer vous-même les balises de tracking Web en mode &quot;création à la volée&quot; : les URL correspondant à ces pages seront insérées automatiquement dans votre plateforme Adobe Campaign.

1. Ajouter ces balises, de façon dynamique ou statique, dans les pages que vous souhaitez tracker.

   >[!NOTE]
   >
   >Toutes les balises de type WEB peuvent être ajoutées telles quelles aux pages de votre site. Les balises TRANSACTION doivent être modifiées ou ajoutées dynamiquement afin de contenir les informations supplémentaires (montant, éléments, etc.).

**Exemple**:

```
<script type="text/javascript">
var _f = "nmsWebTracking"
var _t = window.location.href.match(/.*://[^/]*(/[^?#&]*)/)[1] + "|w|" + _f
document.write("<img height='0' width='0' alt='' src='" +
window.location.protocol + "//tsupport/r/" +
Math.random().toString() + "?tagid=" + escape(_t) + "'/>")
</script>
```
