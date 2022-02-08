---
product: campaign
title: API orientées métier
description: API orientées métier
feature: API
exl-id: e6638870-3141-4f12-b904-db436127c0d1
source-git-commit: 8fa50d17a9ff36ccc310860ac93771590cfd76fd
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 100%

---

# API orientées métier{#business-oriented-apis}

![](../../assets/v7-only.svg)

Les API métier sont spécifiques à chaque type d&#39;objet. Elles agissent sur :

* Diffusions :

   * créer une action de diffusion, voir la section [SubmitDelivery (nms:delivery)](#submitdelivery--nms-delivery-),
   * envoyer une campagne (démarrer, mettre en pause, arrêter, envoyer un BAT),
   * récupérer les logs de diffusion.

* Workflows :

   * démarrer un workflow,
   * contrôler les process, etc.

      Pour plus d&#39;informations, consultez la section [Méthodes SOAP en JavaScript](../../configuration/using/soap-methods-in-javascript.md).

* Gestion de contenu
* Gestion des abonnements, voir les sections [Subscribe (nms:subscription)](#subscribe--nms-subscription-) et [Unsubscribe (nms:subscription)](#unsubscribe--nms-subscription-).
* Les traitements sur les données : imports, exports.

Cette section montre comment utiliser les services &quot;Subscribe&quot;, &quot;Unsubscribe&quot; et &quot;SubmitDelivery&quot;.

>[!IMPORTANT]
>
>La [documentation JSAPI Campaign](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=fr) contient des informations supplémentaires sur les appels SOAP et l’utilisation de Javascript dans Adobe Campaign ainsi qu’une référence complète de toutes les méthodes et fonctions utilisées dans l’application.

## Subscribe (nms:subscription) {#subscribe--nms-subscription-}

Ce service permet d&#39;inscrire un destinataire à un service d&#39;information et de mettre à jour son profil.

L&#39;invocation du service nécessite les paramètres suivants :

* une authentification,
* le nom interne du service d&#39;abonnement,
* un document XML contenant les informations du destinataire (de schéma &quot;nms:recipient&quot;).
* un booléen pour la création du destinataire s&#39;il n&#39;existe déjà pas.

Description de la méthode &quot;subscribe&quot; dans le schéma &quot;nms:subscription&quot; :

```
<method name="Subscribe" static="true">
  <parameters>
     <param name="serviceName" type="string"  desc="List of information service names (comma separated)"/>
     <param name="recipient" type="DOMElement" desc="Recipient"/>
     <param name="create" type="Boolean" desc="Create recipient if it does not exist"/>
   </parameters>
</method>
```

La définition de la clé de réconciliation doit être renseignée via l’attribut _**key** sur l’élément `<recipient>` du document XML. Le contenu de cet attribut est une liste XPath séparée par des virgules.

Cet appel ne retourne pas de données, hormis les erreurs.

### Exemples      {#examples}

Abonnement avec clé de réconciliation du destinataire sur l’adresse e-mail : le document XML en entrée doit référencer l’adresse e-mail et la définition de la clé sur ce champ.

```
<recipient _key="email" email= "john.doe@adobe.com"/>
```

Mise à jour du destinataire en plus de son abonnement.

```
<recipient _key="email, [folder-id]" email= "john.doe@adobe.com" folder-id="1305" firstName="John" lastName="Doe"/>
```

### Exemple de messages SOAP {#example-of-soap-messages}

* Requête:

   ```
   <?xml version='1.0' encoding='ISO-8859-1'?>
   <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
     <SOAP-ENV:Body>
       <m:Subscribe xmlns:m='urn:nms:subscription' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
         <sessiontoken xsi:type='xsd:string'/>
         <service xsi:type='xsd:string'>SVC1</service>
         <content xsi:type='' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
           <recipient _key="@email" email= "john.doe@adobe.com/>
         </content>
         <create xsi:type='xsd:boolean'>true</create>
       </m:Subscribe>
     </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

* Réponse :

   ```
   <?xml version='1.0' encoding='ISO-8859-1'?>
   <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
     <SOAP-ENV:Body>
       <m:SubscribeResponse xmlns:m='urn:nms:subscription' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
       </m:SubscribeResponse>
     </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

## Unsubscribe (nms:subscription) {#unsubscribe--nms-subscription-}

Ce service permet de désinscrire un destinataire à un service d&#39;information et de mettre à jour son profil.

L&#39;invocation du service nécessite les paramètres suivants :

* une authentification,
* le nom interne du service à désabonner,
* un document XML contenant les informations du destinataire (de schéma &quot;nms:recipient&quot;).

Description de la méthode &quot;Unsubscribe&quot; dans le schéma &quot;nms:subscription&quot; :

```
<method name="Unsubscribe" static="true">
  <parameters>
    <param name="serviceName" type="string" desc="List of information service names (comma separated)"/>
    <param name="recipient" type="DOMElement"  desc="Recipient"/>
  </parameters>
</method>
```

La définition de la clé de réconciliation doit être renseignée via l’attribut _key sur l’élément `<recipient>` du document XML. Le contenu de cet attribut est une liste XPath séparée par des virgules.

Si le destinataire n&#39;est pas présent dans la base de données, ou bien s&#39;il n&#39;est pas inscrit au service d&#39;information concerné, le service n&#39;effectue aucune action et ne génère pas d&#39;erreur.

>[!NOTE]
>
>Si le nom du service n&#39;est pas précisé en paramètre, alors le destinataire est automatiquement placé sur la liste bloquée (@blackList=&quot;1&quot;).

Cet appel ne retourne pas de données, hormis les erreurs.

### Exemple de messages SOAP {#example-of-soap-messages-1}

Requête:

```
<?xml version='1.0' encoding='ISO-8859-1'?>
<SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
  <SOAP-ENV:Body>
    <m:Unsubscribe xmlns:m='urn:nms:subscription' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
    <sessiontoken xsi:type='xsd:string'/>
    <service xsi:type='xsd:string'>SVC1</service>
    <content xsi:type='' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
      <recipient _key="@email" email= "john.doe@adobe.com/>
    </content>
  </m:Unsubscribe>
</SOAP-ENV:Body>
```

Réponse :

```
<?xml version='1.0' encoding='ISO-8859-1'?>
<SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
  <SOAP-ENV:Body>
    <m:UnsubscribeResponse xmlns:m='urn:nms:subscription' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
    </m:UnsubscribeResponse>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

## SubmitDelivery (nms:delivery) {#submitdelivery--nms-delivery-}

Ce service permet de créer et soumettre une action de diffusion.

L&#39;invocation du service nécessite les paramètres suivants :

* une authentification,
* le nom interne du modèle de diffusion,
* un document XML optionnel contenant les données complémentaires de la diffusion.

Cette API ne doit pas être appelée en volume, car vous pouvez rencontrer des problèmes de performance.

Description de la méthode dans son schéma :

```
<method name="SubmitDelivery" static="true">
  <parameters>
    <param name="scenarioName" type="string" inout="in" desc="Internal name of the delivery template"/>
    <param name="content" type="DOMElement"  inout="in" desc="XML content of the delivery template" />
  </parameters>
</method>
```

Un modèle de diffusion doit être créé à partir de la console cliente Adobe Campaign, il contient les paramètres communs à tous les envois (adresse de l&#39;expéditeur ou la durée de validité du message).

Le document XML en entrée est un fragment de modèle de diffusion respectant la structure du schéma &quot;nms:delivery&quot;. Celui-ci va contenir toutes les données complémentaires qui n&#39;ont pas pu être définies de façon statique dans le modèle de diffusion (par exemple la liste des destinataires à cibler).

Cet appel ne retourne pas de données, hormis les erreurs.

### Exemple de document XML {#xml-document-example}

Cet exemple est basé sur un modèle de diffusion personnalisée à partir d’une source de données externe (un fichier dans ce cas). La configuration est entièrement décrite dans le modèle de diffusion. Lorsque l’appel est effectué, il ne reste donc plus qu’à envoyer le contenu du fichier à partir de l’élément `<externalsource>`.

```
<delivery>
  <targets fromExternalSource="true">
    <externalSource>
      MsgId|ClientId|Title|Name|FirstName| Mobile|Email| Market_segment|Product_affinity1 |Product_affinity2|Product_affinity3| Product_affinity4| Support_Number|Amount|Threshold1|000001234|M.| Doe|John|0650201020| john.doe@adobe.com
|1| A1|A2|A3|A4|E12|120000|100000
    </externalSource>
  </target>
</delivery>
```

Si vous ne disposez pas d&#39;un modèle de diffusion, vous pouvez utiliser l&#39;exemple suivant :

```
<delivery>
<targets fromExternalSource="true" targetMode="1" noReconciliation="true" addressField="Email" >  
    <fileFormat active="true">  
      <source format="text" type="text">  
        <dataSourceConfig >  
          <dataSourceColumn label="Email" name="Email" type="string"/>  
        </dataSourceConfig>  
      </source>  
      <destination type="xtkDataStore"/>  
    </fileFormat>  
    <externalSource><![CDATA[not-a-repicipient@domain.com]]></externalSource>  
  </targets> 
</delivery> 
```
