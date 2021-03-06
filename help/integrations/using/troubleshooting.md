---
product: campaign
title: Résolution des problèmes
description: Résolution des problèmes
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: 61bb184e-affa-430c-8571-56e911cd5a3d
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 100%

---

# Résolution des problèmes{#troubleshooting}

![](../../assets/common.svg)

En cas d&#39;erreur, vérifiez que les éléments suivants sont correctement configurés :

* **Comptes externes**

   Dans **[!UICONTROL Administration > Plateforme > Comptes externes]**, vérifiez que les comptes SFTP externes ci-dessous sont correctement configurés. Les serveurs SFTP indiqués doivent avoir été configurés par votre consultant dans Adobe Experience Cloud.

   * **[!UICONTROL importSharedAudience : compte SFTP dédié à l&#39;import d&#39;audiences.]**
   * **[!UICONTROL exportSharedAudience : compte SFTP dédié à l&#39;export d&#39;audiences.]**

* **AMC Data source**

   Dans **[!UICONTROL Administration > Plateforme > AMC Data sources]**, vérifiez que l&#39;AMC Data source est correctement définie.

Il est possible que certaines données soient manquantes lors du partage d&#39;une audience via People core service ou lors de l&#39;import d&#39;une audience. Seuls les enregistrements dont l&#39;identifiant (&#39;Visitor ID&#39; ou &#39;Declared ID&#39;) a pu être réconcilié avec la dimension des profils sont transférés. Les identifiants provenant des segments de People core service non reconnus par Adobe Campaign ne sont pas importés.
