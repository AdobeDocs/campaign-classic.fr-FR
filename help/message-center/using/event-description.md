---
product: campaign
title: Description des événements
description: Découvrez comment les événements de message transactionnel sont gérés dans Adobe Campaign Classic à l'aide des méthodes SOAP.
feature: Transactional Messaging, Message Center
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
audience: message-center
content-type: reference
topic-tags: introduction
exl-id: 9f7f4b6c-2ee8-4091-847d-f616d6abeb6b
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: ht
source-wordcount: '769'
ht-degree: 100%

---

# Description des événements {#event-description}



## Modèle de données de message transactionnel {#about-transactional-messaging-datamodel}

La messagerie transactionnelle repose sur le modèle de données d’Adobe Campaign et utilise deux tables supplémentaires distinctes. Ces [tables](../../configuration/using/data-model-description.md#message-center-module), **NmsRtEvent** et **NmsBatchEvent**, contiennent les mêmes champs et permettent de gérer les événements temps réel d’une part et les événements batch d’autre part.

## Méthodes SOAP {#soap-methods}

Cette section décrit les méthodes SOAP associées aux schémas du module des messages transactionnels.

Deux méthodes SOAP **PushEvent** ou **PushEvents** sont associées aux deux schémas de données **nms:rtEvent** et **nms:BatchEvent**. C&#39;est le système d&#39;information qui détermine si un événement est de type &quot;batch&quot; ou &quot;temps réel&quot;.

* **PushEvent** permet d&#39;insérer un seul événement dans le message,
* **PushEvents** permet d&#39;insérer une collection d&#39;événements dans le message.

Le chemin WSDL d&#39;accès aux deux méthodes est :

* **http://hostname/nl/jsp/schemawsdl.jsp?schema=nms:rtEvent** pour accéder au schéma de type temps réel.
* **http://hostname/nl/jsp/schemawsdl.jsp?schema=nms:batchEvent** pour accéder au schéma de type batch.

Pour plus d’informations sur la génération d’un fichier WSDL, voir [cette section](../../configuration/using/web-service-calls.md#web-service-description--wsdl).

Les deux méthodes contiennent un élément **`<urn:sessiontoken>`** permettant de se connecter au module de message transactionnel. Nous vous recommandons d&#39;utiliser une méthode d&#39;identification via des adresses IP approuvées. Pour récupérer le jeton de session, effectuez un appel SOAP de connexion, puis un jeton get suivi d’une fermeture de session. Utilisez le même jeton pour plusieurs appels RT. Les exemples inclus dans cette section utilisent la méthode du jeton de session qui est recommandée.

Si votre serveur présente une répartition de la charge, vous pouvez utiliser l’authentification par utilisateur/mot de passe (au niveau du message RT). Par exemple :

```
<PushEvent xmlns="urn:nms:rtEvent">
<sessiontoken>mc/PASSWORD</sessiontoken>
<domEvent>
<rtEvent wishedChannel="41" type="rt_MobileJourney_iOS_Push" registrationToken="c3ddc8aaecc24822df25d0f49865cca61ea3f86c61bfa53ae4d37294e37f4a1c" hashlpId="27EE7571EC14DBA23B9B5CC0EF79BB782DAECF4C03C88E5D92CC9B9DAC4E5DDA" correlationId="415b7593-4f6f-e911-811f-00505691247c" xmlns="">
<mobileApp uuid="236B24DC-C073-412F-8BCB-AC7207096258" _operation="none"/>
<ctx>...</ctx>
</rtEvent>
</domEvent>
</PushEvent>
```

La méthode **PushEvent** est constituée d’un paramètre **`<urn:domevent>`** qui contient l’événement.

La méthode **PushEvent** est constituée d’un paramètre **`<urn:domeventcollection>`** qui contient des événements.

Exemple avec PushEvent :

```
<urn:PushEvent>

 <sessiontoken>___921f9b38-72ac-49ad-b481-ab32973efc50</sessiontoken>
 
 <urn:domEvent>
 
   <rtEvent>
   
   ...
   
   </rtEvent>
 
 </urn:domEvent>

</urn:PushEvent>
```

>[!NOTE]
>
>En cas d’appel à la méthode **PushEvents**, nous devons ajouter un élément XML parent pour nous conformer au XML standard. Cet élément XML encadrera les différents éléments **`<rtevent>`** contenus dans l’événement.

Exemple avec PushEvents :

```
<urn:PushEvents>

 <sessiontoken>___921f9b38-72ac-49ad-b481-ab32973efc50</sessiontoken>
 
 <urn:domEventCollection>
 
   <Events>
   
     <rtEvent>... </rtEvent>
     
     <rtEvent>... </rtEvent>
     
     ...
   
   </Events>
 
 </urn:domEventCollection>

</urn:PushEvents>
```

Les éléments **`<rtevent>`** et **`<batchevent>`** possèdent un jeu d&#39;attributs ainsi qu&#39;un élément enfant indispensable : **`<ctx>`** permettant d’intégrer les données du message.

>[!NOTE]
>
>L’élément **`<batchevent>`** vous permet d’ajouter l’événement à la file d’attente &quot;batch&quot;. Le **`<rtevent>`** ajoute l’événement à la file d’attente &quot;temps réel&quot;.

Les attributs obligatoires des éléments **`<rtevent>`** et **`<batchevent>`** sont @type et @email. La valeur de @type doit être identique à la valeur de liste détaillée définie lors de la configuration de l’instance d’exécution. Cette valeur vous permet de définir le modèle à lier au contenu de l’événement pendant la diffusion.

`<rtevent> configuration example:`

```
<rtEvent type="order_confirmation" email="john.doe@domain.com" origin="eCommerce" wishedChannel="0" externalId="1242" mobilePhone="+33620202020"> 
```

Dans cet exemple, deux canaux sont renseignés : l&#39;adresse email et le numéro de téléphone portable. Le champ **wishedChannel** permet de définir le canal qui sera utilisé lors de la transformation de l&#39;évènement en message. La valeur &quot;0&quot; correspond au canal email, la valeur &quot;1&quot; au canal mobile, etc.

Si vous souhaitez différer le traitement d&#39;un évènement, ajoutez le champ **[!UICONTROL scheduled]** suivi de la date désirée. L&#39;évènement sera transformé en message à cette date.

Nous vous conseillons de remplir les attributs @wishedChannel et @emailFormat avec des valeurs numériques. La table de correspondance entre les valeurs numériques et les labels associés se trouve dans la description des schémas de données.

>[!NOTE]
>
>La description détaillée de tous les attributs autorisés et de leurs valeurs se trouve dans la description du schéma de données de **nms:rtEvent** et **nms:BatchEvent**.

L’élément **`<ctx>`** contient les données du message. Son contenu XML est ouvert, ce qui signifie qu’il peut être configuré selon le contenu à diffuser.

>[!NOTE]
>
>Il est important d&#39;optimiser le nombre et la taille des noeuds XML contenus dans le message afin de ne pas surcharger les serveurs lors de la diffusion.

Exemple de données :

```
   <ctx>
               <client>
                        <firstname>John</firstname>
                        <lastname>Doe</lastname>
               </client>
               <action>
                         <type>Order confirmation</type>
                          <number>CN23453</number>
               </action>
               <orderdetails>
                          <article num="1">
                                   <name>Generic USB key</name>
                                   <price>20</price>
                           </article>
               </orderdetails>
    </ctx>
```

## Informations retournées par l&#39;appel SOAP {#information-returned-by-the-soap-call}

Lors de la réception d&#39;un événement, Adobe Campaign génère un identifiant unique de retour. Il correspond à l&#39;identifiant de la version historisée de l&#39;événement.

>[!IMPORTANT]
>
>Lors de la réception d&#39;appels SOAP, Adobe Campaign vérifie le format des adresses email. Si une adresse email n&#39;est pas correctement mise en forme, une erreur est renvoyée.

* Exemple d&#39;identifiant renvoyé par la méthode lorsque le traitement d&#39;un événement a réussi :

  ```
  <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:ns="http://xml.apache.org/xml-soap" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
     <SOAP-ENV:Body>
        <urn:PushEventResponse SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:urn="urn:nms:rtEvent">
           <plId xsi:type="xsd:long">72057594037935966</plId>
        </urn:PushEventResponse>
     </SOAP-ENV:Body>
  </SOAP-ENV:Envelope>
  ```

Lorsque la valeur de l&#39;identifiant de retour est strictement supérieure à zéro, cela signifie que l&#39;événement est bien historisé dans Adobe Campaign.

En revanche, si le traitement de l&#39;événement échoue, la méthode renvoie un message d&#39;erreur ou une valeur égale à zéro.

* Exemple de traitement d&#39;un événement qui a échoué lorsque la requête ne contient pas de login ou que l&#39;opérateur spécifié n&#39;a pas les droits adéquats :

  ```
  <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
     <SOAP-ENV:Body>
        <SOAP-ENV:Fault>
           <faultcode>SOAP-ENV:Client</faultcode>
           <faultstring xsi:type="xsd:string">Error while reading parameters of method 'PushEvent' of service 'nms:rtEvent'.</faultstring>
           <detail xsi:type="xsd:string">Invalid login or password. Connection denied.</detail>
        </SOAP-ENV:Fault>
     </SOAP-ENV:Body>
  </SOAP-ENV:Envelope>
  ```

* Exemple de traitement d&#39;un événement qui a échoué du fait d&#39;une erreur dans la requête (la nomenclature XML n&#39;est pas respectée) :

  ```
  <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
     <SOAP-ENV:Body>
        <SOAP-ENV:Fault>
           <faultcode>SOAP-ENV:Client</faultcode>
           <faultstring xsi:type="xsd:string">The XML SOAP message is invalid (service 'PushEvent', method 'nms:rtEvent').</faultstring>
           <detail xsi:type="xsd:string"><![CDATA[(16:8) : Expected end of tag 'rtevent'
  Error while parsing XML string '<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:nms:rtEvent">
     <soapenv:Header/>
     <soapenv:Body>
        <urn:PushEvent>
           <urn:sessiontoken>mc/</urn:sessiontoken>
           <urn:domEvent>
  <rtevent type="create_account" email="esther.hall@adobe.com" origin="eCommerce" wishedChannel="email" 
        externalId="1596" language="english" country="EN" emailFormat="2"
        mobilePhone="+447700123123">
    <ctx>
     <website name="eCommerce" url="http://www.eCo']]></detail>
        </SOAP-ENV:Fault>
     </SOAP-ENV:Body>
  </SOAP-ENV:Envelope>
  ```

* Exemple de traitement d&#39;un événement qui a échoué et du renvoi d&#39;un identifiant à zéro (le nom de la méthode est erroné) :

  ```
  <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:ns="http://xml.apache.org/xml-soap" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
     <SOAP-ENV:Body>
        <urn:PushEventResponse SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:urn="urn:nms:rtEvent">
           <plId xsi:type="xsd:long">0</plId>
        </urn:PushEventResponse>
     </SOAP-ENV:Body>
  </SOAP-ENV:Envelope>
  ```
