---
title: Etapes de mise en place
seo-title: Etapes de mise en place
description: Etapes de mise en place
seo-description: null
page-status-flag: never-activated
uuid: 4111a805-95ab-4e26-be51-2db1e5c20f57
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 76174374-af73-4da0-b62b-6979bca0102b
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 100%

---


# Etapes de mise en place{#setup-stages}

Le principe de base repose sur l&#39;ajout des balises de tracking Web dans certaines pages de votre site.

Il existe deux types de balises :

* **WEB** : cette balise permet de savoir si la page a été visitée,
* **TRANSACTION** : fonctionne comme une balise WEB, mais avec la possibilité d&#39;ajouter des informations relatives, par exemple, au chiffre d&#39;affaires généré (montant de la transaction, nombre d&#39;articles achetés, etc.).

Les étapes pour mettre en place ces balises sont les suivantes:

1. Identifier les pages que vous souhaitez tracker et déterminer leur type (WEB ou TRANSACTION).
1. Déterminer quelles informations supplémentaires vous souhaitez collecter et étendre le schéma **nms:webTrackingLog** avec la description de ces informations. Par défaut, ce schéma propose de stocker le montant des transactions et le nombre d&#39;articles par transaction.
1. Créer les balises de tracking Web. Pour cela, deux méthodes sont possibles :

   * Insérer les URL correspondant à ces pages dans votre plateforme Adobe Campaign, puis générer et extraire les différentes balises de tracking Web associées (à partir du noeud **[!UICONTROL Ressources>On-line>Balises de tracking Web]** de la console cliente).
   * Créer vous-même les balises de tracking Web en mode &quot;création à la volée&quot; : les URL correspondant à ces pages seront insérées automatiquement dans votre plateforme Adobe Campaign.

1. Ajouter ces balises, de façon dynamique ou statique, dans les pages que vous souhaitez tracker.

   >[!NOTE]
   >
   >Toutes les balises de type WEB peuvent être ajoutées telles quelles dans les pages de votre site. Les balises de type TRANSACTION doivent être modifiées ou ajoutées dynamiquement afin de contenir les informations supplémentaires (montant, articles, etc.).

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

