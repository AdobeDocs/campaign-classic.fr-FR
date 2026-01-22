---
product: campaign
title: Dépanner IMS
description: Dépanner IMS
feature: Configuration
badge-v7-prem: label="On-Premise/hybride uniquement" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: 1ce89c3a-1fe6-4ed6-9547-2eb9713a0ec3
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: ht
source-wordcount: '427'
ht-degree: 100%

---

# Dépanner IMS{#ims-troubleshooting}


Les conseils de dépannage suivants aideront les clientes et clients **On-Premise** et **hybrides** à résoudre les problèmes les plus courants lors de l’utilisation de l’intégration IMS. Pour les clientes et clients **hébergés**, veuillez contacter Adobe.

**Compte externe**

Il ne doit y avoir qu&#39;**un** compte externe avec les paramètres suivants :

* **Nom interne** : Adobe_Marketing_Cloud
* **Type** : Adobe Marketing Cloud

Supprimez tout compte externe en double avec les mêmes paramètres.

**Product Context**

Si le compte externe possède un champ **Product Context**, vérifiez que sa valeur est définie sur : **dma_campaign_classic**

Vérifiez que votre Product Context est identique pour Campaign et Experience Cloud.

Par exemple, si **Product Context** n’apparaît pas, le contexte de produit par défaut doit être **dma_campaign** dans Campaign et Experience Cloud. Si **Product Context** apparaît, le contexte de produit par défaut doit être **dma_campaign_classic** dans Campaign et Experience Cloud.

**[!UICONTROL URL du serveur IMS]**

Dans le compte externe **Adobe Marketing Cloud** de Campaign, vérifiez que la variable **[!UICONTROL URL du serveur IMS]** est définie sur `adobeid-na1.services.adobe.com` ou `ims-na1.adobelogin.com`. Assurez-vous que les instances d’évaluation et de production pointent sur le même point d’entrée de production IMS.

**Masque de correspondance**

* Vérifiez que l’utilisateur tentant de se connecter fait partie d’un groupe d’opérateurs dans Enterprise Dashboard.
* Vérifiez que le **[!UICONTROL masque de correspondance]** est un préfixe du nom de groupe d’opérateurs de l’utilisateur dans Enterprise Dashboard.
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

  Il existe un problème avec l’**[!UICONTROL URL de callback]**. Reportez-vous aux étapes précédentes pour vérifier la configuration de l’**[!UICONTROL URL de callback]**.

* Affichage du message &quot;Le login ne possède aucun droit correspondant à l&#39;expression&quot; :

  Reportez-vous aux étapes précédentes pour vérifier le paramétrage du **[!UICONTROL masque de correspondance]** et des groupes d&#39;opérateurs.

* L&#39;utilisateur ne parvient pas à accéder à la page de login Adobe ID :

  Reportez-vous aux étapes précédentes pour vérifier le paramétrage du périmètre.
