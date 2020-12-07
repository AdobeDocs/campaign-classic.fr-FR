---
solution: Campaign Classic
product: campaign
title: Résolution des problèmes
description: Résolution des problèmes
audience: integrations
content-type: reference
topic-tags: audience-sharing
translation-type: ht
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: ht
source-wordcount: '141'
ht-degree: 100%

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
