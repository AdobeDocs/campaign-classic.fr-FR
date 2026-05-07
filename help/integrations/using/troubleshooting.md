---
product: campaign
title: Résolution des problèmes
description: Résolution des problèmes
feature: Audiences, People Core Service Integration, Troubleshooting
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
audience: integrations
content-type: reference
topic-tags: audience-sharing
hide: true
exl-id: 61bb184e-affa-430c-8571-56e911cd5a3d
source-git-commit: 720a5f4edf534788f7fd143a476c25e58a6f1586
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 78%

---

# Résolution des problèmes{#troubleshooting}



En cas d&#39;erreur, vérifiez que les éléments suivants sont correctement configurés :

* **Comptes externes**

  Dans **[!UICONTROL Administration > Plateforme > Comptes externes]**, vérifiez que les comptes SFTP externes suivants sont correctement configurés. Les serveurs SFTP mentionnés doivent avoir été configurés dans Adobe Experience Cloud par votre consultant.

   * **[!UICONTROL importSharedAudience : compte SFTP dédié à l&#39;import d&#39;audiences.]**
   * **[!UICONTROL exportSharedAudience : compte SFTP dédié à l&#39;export d&#39;audiences.]**

* **AMC Data source**

  Dans **[!UICONTROL Administration > Plateforme > AMC Data sources]**, vérifiez que l&#39;AMC Data source est correctement définie.

Il est possible que certaines données soient manquantes lors du partage d’une audience via Experience Cloud Audience ou lors de l’import d’une audience. Seuls les enregistrements dont l’identifiant (&#39;Visitor ID&#39; ou &#39;Declared ID&#39;) a pu être réconcilié avec la dimension des profils sont transférés. Les identifiants provenant de segments non reconnus par Adobe Campaign ne sont pas importés.
