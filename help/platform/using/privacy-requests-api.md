---
product: campaign
title: Processus automatique de demande d'accès à des informations personnelles
description: Découvrez comment configurer un processus automatique de demande d’accès à des informations personnelles.
feature: Privacy, Privacy Tools
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: a93bac61-f615-4178-bc12-0f056e48687d
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '667'
ht-degree: 100%

---

# Processus automatique de demande d&#39;accès à des informations personnelles {#automatic-privacy-request-api}



Adobe Campaign fournit une **API** qui permet de configurer un processus automatique de demande d&#39;accès à des informations personnelles.

Avec l&#39;API, le processus général d&#39;accès à des informations personnelles est identique à [celui de l&#39;interface](privacy-requests-ui.md). La seule différence est la création de la demande d&#39;accès à des informations personnelles. Au lieu de créer la demande dans Adobe Campaign, une instruction POST contenant les informations de la demande est envoyée à Campaign. Pour chaque demande, une nouvelle entrée est ajoutée dans l&#39;écran **[!UICONTROL Demandes d&#39;accès à des informations personnelles]**. Les workflows techniques d&#39;accès à des informations personnelles traitent ensuite la demande, de la même manière que pour une demande ajoutée à l&#39;aide de l&#39;interface.

Si vous utilisez l&#39;API pour soumettre des demandes d&#39;accès à des informations personnelles, il est recommandé de conserver l&#39;option **Processus en 2 étapes** activée pour les premières demandes de suppression, afin de tester les données renvoyées. Une fois vos tests terminés, vous pouvez désactiver le processus en 2 étapes de façon à ce que le processus de demande de suppression puisse s&#39;exécuter automatiquement.

L&#39;API JS **[!UICONTROL CreateRequestByName]** est définie comme suit.

>[!NOTE]
>
>Si vous utilisiez l&#39;API **gdprRequest**, vous pouvez la conserver, mais il est recommandé d&#39;utiliser la nouvelle API **privacyRequest**.

>[!IMPORTANT]
>
>Le droit nommé **[!UICONTROL Droit relatif aux données personnelles]** est nécessaire pour utiliser l&#39;API.

```
<method library="nms:gdpr.js" name="CreateRequestByName" static="true">
 <help>Create a new GDPR Request using namespace internal name</help>
 <parameters>
  <param name="namespaceName" type="string" desc="Namespace internal name"/>
  <param name="reconciliationValue" type="string" desc="Reconciliation value"/>
  <param name="type" type="long" desc="Reconciliation value"/>
  <param name="confirmDeletePending" type="boolean" desc="Request confirm before deleting data"/>
  <param name="regulation" type="long" desc="regulation of newly created request"/>
  <param name="id" type="long" inout="out" desc="ID of newly created request"/>
 </parameters>
</method>
```

>[!NOTE]
>
>Le champ &quot;règlement&quot; n&#39;est disponible que si vous utilisez Campaign Classic 20.2 (build 9178+).
>
>Si vous effectuez une migration vers la version 20.2 et que vous utilisiez déjà l&#39;API, vous devez ajouter ce champ comme illustré ci-dessus. Si vous avez recours à un build précédent, vous pouvez continuer à utiliser l&#39;API sans le champ «règlement».

## Appel de l&#39;API en externe {#invoking-api-externally}

Voici un exemple d&#39;appel externe de l&#39;API (authentification via l&#39;API et détails spécifiques sur l&#39;API de protection des données). Pour en savoir plus sur l&#39;API de protection des données, consultez la [documentation de l&#39;API](https://experienceleague.adobe.com/developer/campaign-api/api/s-nms-privacyRequest.html?lang=fr). Vous pouvez également consulter la [documentation sur les appels Web Service](../../configuration/using/web-service-calls.md).

Tout d&#39;abord, vous devez effectuer l&#39;authentification par le biais de l&#39;API :

1. Téléchargez le WSDL **xtk:session** depuis cette URL : **`<server url>`/nl/jsp/schemawsdl.jsp?schema=xtk:session**.

1. Utilisez la méthode &quot;Logon&quot; et transmettez un nom d&#39;utilisateur et un mot de passe en tant que paramètres dans la demande. Vous obtiendrez une réponse contenant un jeton de session. Voici un exemple utilisant SoapUI.

   ![](assets/do-not-localize/privacy-api.png)

1. Utilisez le jeton de session retourné comme authentification pour tous les appels d&#39;API suivants. Il arrive à expiration au bout de 24 heures.

Vous pouvez ensuite appeler l&#39;API de protection des données :

1. Téléchargez le WSDL depuis cette URL : **`<server url>`/nl/jsp/schemawsdl.jsp?schema=nms:privacyRequest**.

1. Utilisez **[!UICONTROL CreateRequestByName]** pour créer une demande d&#39;accès à des informations personnelles spécifique.

   Voici un exemple utilisant **[!UICONTROL CreateRequestByName]**. Remarquez comment nous utilisons le jeton de session fourni ci-dessus pour l&#39;authentification. La réponse est l&#39;identifiant de la demande créée.

   ![](assets/do-not-localize/privacy-api-2.png)

   Pour vous aider à effectuer les étapes ci-dessus, tenez compte des points suivants :

   * Vous pouvez utiliser une **queryDef** sur le schéma **nms:gdprRequest** pour vérifier le statut de la demande d&#39;accès.
   * Vous pouvez utiliser une **queryDef** sur le schéma **nms:gdprRequestData** pour obtenir le résultat de la demande d&#39;accès.
   * Pour pouvoir télécharger le fichier XML à partir de **&quot;$(serverUrl)&#39;/nms/gdpr.jssp?id=&#39;@id&quot;**, vous devez être connecté et y accéder à partir d’une adresse IP placée sur la liste autorisée. Pour ce faire, créez une application web vous permettant d&#39;accéder au fichier généré par le JSSP.

## Appel de l&#39;API depuis un script JS {#invoking-api-from-js}

Vous trouverez ci-dessous un exemple d&#39;appel de l&#39;API depuis un script JS dans Campaign Classic.

>[!NOTE]
>
>Le champ &quot;règlement&quot; n&#39;est disponible que si vous utilisez Campaign Classic 20.2 (build 9178+).
>
>Si vous effectuez une migration vers la version 20.2 et que vous utilisiez déjà l&#39;API, vous devez ajouter ce champ. Si vous avez recours à un build précédent, vous pouvez continuer à utiliser l&#39;API sans le champ «règlement».

* Si **vous utilisez une version précédente (avec le package RGPD)**, vous pouvez continuer à utiliser l&#39;API sans le champ &#39;regulation&#39; comme illustré ci-dessous :

  ```
  loadLibrary("nms:gdpr.js");
  /**************************** 
  This code calls an API to create new Privacy request on the DB.
  It requires 4 parameters below.
  Feel free to change parameter values.
  ****************************/
  // 1. Namespace internal name
  var namespaceName = "defaultNamespace1";
  // 2. Reconciliation value for privacy request
  var reconciliationValue = "example@adobe.com";
  // 3. Privacy request type
  // GDPR_REQUEST_TYPE_ACCESS = 1;
  // GDPR_REQUEST_TYPE_DELETE = 2;
  var requestType = GDPR_REQUEST_TYPE_ACCESS;
  // 4. Confirm deleting data required.
  // value : true or false
  var ConfirmDeletePending = true;
  // BEGIN
  var requestId = nms.privacyRequest.CreateRequestByName(namespaceName, reconciliationValue, requestType, ConfirmDeletePending);
  // User can use a simple queryDef with requestID as a parameter to check request status.
  ```

* Si vous effectuez une **migration vers la version 20.2** et que vous utilisiez déjà l&#39;API, vous devez ajouter ce champ comme illustré ci-dessous :

  ```
  loadLibrary("nms:gdpr.js");
  /**************************** 
  This code calls an API to create new Privacy request on the DB.
  It requires 5 parameters below.
  Feel free to change parameter values.
  ****************************/
  // 1. Namespace internal name
  var namespaceName = "defaultNamespace1";
  // 2. Reconciliation value for privacy request
  var reconciliationValue = "example@adobe.com";
  // 3. Privacy request type
  // PRIVACY_REQUEST_TYPE_ACCESS = 1;
  // PRIVACY_REQUEST_TYPE_DELETE = 2;
  var requestType = PRIVACY_REQUEST_TYPE_ACCESS;
  // 4. Confirm deleting data required.
  // value : true or false
  var ConfirmDeletePending = true;
  // 5. Specify which regulation applies to newly created request. This is mandatory parameter.
  // GDPR = 1
  // CCPA = 2
  // PDPA = 3
  // LGPD = 4
  var regulation = 1;
  // BEGIN
  var requestId = nms.privacyRequest.CreateRequestByName(namespaceName, reconciliationValue, requestType, ConfirmDeletePending, regulation);
  // User can use a simple queryDef with requestID as a parameter to check request status.
  ```

* Si **vous utilisez Campaign Classic 20.2 (version 9178+) ou une version ultérieure**, le champ &#39;regulation&#39; est facultatif, comme illustré ci-dessous :

  ```
  loadLibrary("nms:gdpr.js");
  /**************************** 
  This code calls an API to create new Privacy request on the DB.
  It requires 5 parameters below.
  Feel free to change parameter values 
  ****************************/
  // 1. Namespace internal name
  var namespaceName = "defaultNamespace1";
  // 2. Reconciliation value for privacy request
  var reconciliationValue = "example@adobe.com";
  // 3. Privacy request type
  // PRIVACY_REQUEST_TYPE_ACCESS = 1;
  // PRIVACY_REQUEST_TYPE_DELETE = 2;
  var requestType = PRIVACY_REQUEST_TYPE_ACCESS;
  // 4. Confirm deleting data required.
  // value : true or false
  var ConfirmDeletePending = true;
  // 5. Specify which regulation applies to newly created request. This is optional parameter.
  // GDPR = 1
  // CCPA = 2
  // PDPA = 3
  // LGPD = 4
  var regulation = 1;
  // BEGIN
  var requestId = nms.privacyRequest.CreateRequestByName(namespaceName, reconciliationValue, requestType, ConfirmDeletePending, regulation);
  // User can use a simple queryDef with requestID as a parameter to check request status.
  ```
