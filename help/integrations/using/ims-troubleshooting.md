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
TQID: https://experienceleague.adobe.com/cUoMAlp8ExhammApiilFqRyrOkyyqxk1om0AifZVxb0
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
subfeature_v2:
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
  - id: df0d6518-6f49-46e2-b46e-3bcc513f553f
  - id: eb007b6d-6e57-46ab-9485-3f24d6102304
  - id: b1fd1501-3105-4d6b-b4d4-9af53126df75
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 521
ht-degree: 86%

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

**Problèmes de cache de WebView2**

Si vous rencontrez des problèmes lors de la connexion à la **[!UICONTROL console cliente]** avec votre Adobe ID, essayez d’effacer le cache WebView2 local. Dans la plupart des cas, cela résout le problème. Suivez les étapes ci-dessous :

1. Fermez la **[!UICONTROL console cliente]** et arrêtez tout processus `nlclient` en cours d’exécution.

1. Supprimez tous les dossiers `webview2` et `webview2Cache` des emplacements suivants :

   * `C:\ProgramData\Neolane\NL_5\nlclient\`
   * `C:\Users\<username>\AppData\Roaming\Neolane\NL_5\nlclient\`

1. Redémarrez la **[!UICONTROL console cliente]** et connectez-vous avec votre Adobe ID. Les dossiers de cache seront automatiquement recréés lors du prochain lancement.
