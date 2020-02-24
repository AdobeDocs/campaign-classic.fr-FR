---
title: Résolution des problèmes
seo-title: Résolution des problèmes
description: Résolution des problèmes
seo-description: null
page-status-flag: never-activated
uuid: fb51ad18-221b-4058-b206-ca2ca045c507
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: audience-sharing
discoiquuid: f3ff8c8e-22b0-4d61-9f26-11f5ca3bc0be
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# Résolution des problèmes{#troubleshooting}

En cas d&#39;erreur, vérifiez que les éléments suivants sont correctement configurés :

* **Comptes externes**

   Dans **[!UICONTROL Administration > Plate-forme > Comptes externes]**, vérifiez que les comptes SFTP externes ci-dessous sont correctement configurés. Les serveurs SFTP indiqués doivent avoir été configurés par votre consultant dans Adobe Experience Cloud.

   * **[!UICONTROL importSharedAudience : compte SFTP dédié à l&#39;import d&#39;audiences.]**
   * **[!UICONTROL exportSharedAudience : compte SFTP dédié à l&#39;export d&#39;audiences.]**

* **AMC Data source**

   Dans **[!UICONTROL Administration > Plate-forme > AMC Data sources]**, vérifiez que l&#39;AMC Data source est correctement définie.

Il est possible que certaines données soient manquantes lors du partage d&#39;une audience via People core service ou lors de l&#39;import d&#39;une audience. Seuls les enregistrements dont l&#39;identifiant (&#39;Visitor ID&#39; ou &#39;Declared ID&#39;) a pu être réconcilié avec la dimension des profils sont transférés. Les identifiants provenant des segments de People core service non reconnus par Adobe Campaign ne sont pas importés.
