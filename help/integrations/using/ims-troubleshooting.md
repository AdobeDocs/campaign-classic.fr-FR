---
title: Dépanner IMS
seo-title: Dépanner IMS
description: Dépanner IMS
seo-description: null
page-status-flag: never-activated
uuid: 5db95afc-8cbf-4ec3-b58f-504486fe4a40
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
discoiquuid: e31db11a-ad8e-4fd0-bab7-0df1079231c9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# Dépanner IMS{#ims-troubleshooting}

Les conseils de dépannage suivants aideront les clients **on-premise** à résoudre les problèmes les plus fréquents lors de l&#39;utilisation de l&#39;intégration IMS. Si vous êtes un client **hébergé**, veuillez contacter Adobe.

**Compte externe**

Il ne doit y avoir qu&#39;**un** compte externe avec les paramètres suivants :

* **Nom interne** : Adobe_Marketing_Cloud
* **Type **: Adobe Marketing Cloud

Supprimez tout compte externe en double avec les mêmes paramètres.

**Product Context**

Si le compte externe possède un champ **Product Context**, vérifiez que sa valeur est définie sur : **dma_campaign_classic**

Vérifiez que votre Product Context est identique pour Campaign et Experience Cloud.

Par exemple, si le **Product Context** n&#39;apparaît pas, le Product Context par défaut doit être **dma_campaign** à la fois dans Campaign et Experience Cloud. Si le champ **Product Context** apparaît, le Product Context par défaut doit être **dma_campaign_classic** à la fois dans Campaign et Experience Cloud.

**[!UICONTROL IMS Server URL]**

Dans le compte externe Campaign **Adobe Marketing Cloud** , vérifiez que le **[!UICONTROL IMS Server URL]** paramètre est [adobeid-na1.services.adobe.com](https://adobeid-na1.services.adobe.com/) ou [ims-na1.adobelogin.com](http://ims-na1.adobelogin.com/). Assurez-vous que les instances d’étape et de production pointent vers le même point final de production IMS.

**Masque de correspondance**

* Vérifiez que l&#39;utilisateur tentant de se connecter fait partie d&#39;un groupe d&#39;opérateurs dans Enterprise Dashboard.
* Check that the **[!UICONTROL Association Mask]** is a prefix of the user&#39;s operator group name in the Enterprise Dashboard.
* Assurez-vous qu&#39;il n&#39;y a aucun espace blanc ni faute d&#39;orthographe.
* Vérifiez que les noms des groupes d’opérateurs dans Campaign n’ont pas été modifiés et respectez la syntaxe suivante :

```
<Association Mask> + <Operator Group Name in Campaign> = Complete name of the operator group in Enterprise Dashboard
```

**Périmètre**

Les périmètres définis dans le compte externe Campaign doivent être un sous-ensemble de ceux provisionnés par IMS.

**URL de callback**

L&#39;**URL de callback** doit figurer en whiteliste et commencer par &quot;https://&quot;. Vérifiez que l&#39;**URL de callback** est liée à l&#39;instance correspondante. Par exemple, l&#39;instance de production doit rediriger vers l&#39;URL de production.

**Identifiant du client et secret**

L&#39;identifiant du client du compte externe Campaign correspond à celui provisionné par IMS.

Vérifiez que le secret de client saisi est correct.

**Redémarrer le serveur**

Redémarrez le serveur si des modifications ont été apportées aux paramètres ci-dessus dans le compte externe Campaign.

**Types d&#39;erreurs fréquents et solutions possibles**

* L&#39;utilisateur est redirigé vers la page adobe.com :

   Il y a un problème avec le **[!UICONTROL Callback URL]**. Refer to the previous steps to check the **[!UICONTROL Callback URL]** configuration.

* Affichage du message &quot;Le login ne possède aucun droit correspondant à l&#39;expression&quot; :

   Refer to the previous steps to check the **[!UICONTROL Association Mask]** and operator groups configuration.

* L&#39;utilisateur ne parvient pas à accéder à la page de login Adobe ID :

   Reportez-vous aux étapes précédentes pour vérifier le paramétrage du périmètre.

