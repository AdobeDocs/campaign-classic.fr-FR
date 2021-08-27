---
product: campaign
title: Dépanner IMS
description: Dépanner IMS
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: 1ce89c3a-1fe6-4ed6-9547-2eb9713a0ec3
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 100%

---

# Dépanner IMS{#ims-troubleshooting}

![](../../assets/common.svg)

Les conseils de dépannage suivants aideront les clients **on-premise** à résoudre les problèmes les plus fréquents lors de l&#39;utilisation de l&#39;intégration IMS. Si vous êtes un client **hébergé**, veuillez contacter Adobe.

**Compte externe**

Il ne doit y avoir qu&#39;**un** compte externe avec les paramètres suivants :

* **Nom interne** : Adobe_Marketing_Cloud
* **Type** : Adobe Marketing Cloud

Supprimez tout compte externe en double avec les mêmes paramètres.

**Product Context**

Si le compte externe possède un champ **Product Context**, vérifiez que sa valeur est définie sur : **dma_campaign_classic**

Vérifiez que votre Product Context est identique pour Campaign et Experience Cloud.

Par exemple, si le **Product Context** n&#39;apparaît pas, le Product Context par défaut doit être **dma_campaign** à la fois dans Campaign et Experience Cloud. Si le champ **Product Context** apparaît, le Product Context par défaut doit être **dma_campaign_classic** à la fois dans Campaign et Experience Cloud.

**[!UICONTROL URL du serveur IMS]**

Dans le compte externe **Adobe Marketing Cloud** Campaign, vérifiez que l&#39;**[!UICONTROL URL du serveur IMS]** est [adobeid-na1.services.adobe.com](https://adobeid-na1.services.adobe.com/) ou [ims-na1.adobelogin.com](http://ims-na1.adobelogin.com/). Assurez-vous que les instances d&#39;étape et de production pointent sur le même point de terminaison de production IMS.

**Masque de correspondance**

* Vérifiez que l&#39;utilisateur tentant de se connecter fait partie d&#39;un groupe d&#39;opérateurs dans Enterprise Dashboard.
* Vérifiez que le **[!UICONTROL masque de correspondance]** est un préfixe du nom de groupe d&#39;opérateurs de l&#39;utilisateur dans Enterprise Dashboard.
* Assurez-vous qu&#39;il n&#39;y a aucun espace blanc ni faute d&#39;orthographe.
* Vérifiez que les noms des groupes d&#39;opérateurs dans Campaign n&#39;ont pas été modifiés et qu&#39;ils respectent la syntaxe suivante :

```
<Association Mask> + <Operator Group Name in Campaign> = Complete name of the operator group in Enterprise Dashboard
```

**Périmètre**

Les périmètres définis dans le compte externe Campaign doivent être un sous-ensemble de ceux provisionnés par IMS.

**URL de callback**

L&#39;**URL de callback** doit être ajoutée à la liste autorisée et commencer par &quot;https://&quot;. Vérifiez que l’**URL de callback** est liée à l’instance correspondante. Par exemple, l’instance de production doit rediriger vers l’URL de production.

**Identifiant du client et secret**

L&#39;identifiant du client du compte externe Campaign correspond à celui provisionné par IMS.

Vérifiez que le secret de client saisi est correct.

**Redémarrer le serveur**

Redémarrez le serveur si des modifications ont été apportées aux paramètres ci-dessus dans le compte externe Campaign.

**Types d&#39;erreurs fréquents et solutions possibles**

* L&#39;utilisateur est redirigé vers la page adobe.com :

   Il y a un problème avec l&#39;**[!UICONTROL URL de callback]**. Reportez-vous aux étapes précédentes pour vérifier le paramétrage de l&#39;**[!UICONTROL URL de callback]**.

* Affichage du message &quot;Le login ne possède aucun droit correspondant à l&#39;expression&quot; :

   Reportez-vous aux étapes précédentes pour vérifier le paramétrage du **[!UICONTROL masque de correspondance]** et des groupes d&#39;opérateurs.

* L&#39;utilisateur ne parvient pas à accéder à la page de login Adobe ID :

   Reportez-vous aux étapes précédentes pour vérifier le paramétrage du périmètre.
