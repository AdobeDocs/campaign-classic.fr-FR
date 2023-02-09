---
product: campaign
title: Appels Web Service
description: Appels Web Service
feature: API
exl-id: ce94e7e7-b8f8-4c82-937f-e87d15e50c34
source-git-commit: f4513834cf721f6d962c7c02c6c64b2171059352
workflow-type: tm+mt
source-wordcount: '922'
ht-degree: 100%

---

# Appels Web Service{#web-service-calls}

![](../../assets/v7-only.svg)

## Informations générales {#general-information}

L&#39;ensemble des méthodes de l&#39;API sont exposées sous forme de service Web. Ainsi, il est possible de piloter l&#39;intégralité des fonctionnalités d&#39;Adobe Campaign au travers d&#39;appels SOAP qui sont le point d&#39;entrée natif du serveur d&#39;application Adobe Campaign. La console Adobe Campaign elle-même n&#39;utilise que des appels SOAP.

Les services Web permettent de créer, depuis un système tiers, de multiples applications :

* Alertes synchrones, notifications et exécution de modèles de diffusion en temps-réel depuis un back-office ou un système transactionnel,
* Développement d&#39;interfaces spécifiques avec des fonctionnalités simplifiées (interfaces Web, etc.),
* Alimentation et consultation des données de la base en respectant les règles métiers et en restant isolé du modèle physique sous-jacent.

## Définition des services Web {#definition-of-web-services}

La définition des services Web implémentés sur le serveur applicatif Adobe Campaign est disponible à partir des schémas de données.

Un service Web est décrit dans la grammaire des schémas de données et est disponible à partir de l&#39;élément **`<methods>`**.

```
<methods>
  <method name="GenerateForm" static="true">
    <help>Generates the form in Mail or Web mode</help>
    <parameters>
      <param name="formName" type="string" desc="Name of form"/>
      <param name="mailMode" type="boolean" desc="Generate a form of type Mail"/>
      <param name="result" type="string" inout="out" desc="Result "/>
    </parameters>
  </method>
</methods>
```

Nous avons ici un exemple de définition de la méthode de nom **GenerateForm**.

La description du service commence par l&#39;élément `<method>`. La liste des paramètres de la méthode est complétée à partir de l&#39;élément `<parameters>`. Chaque paramètre est spécifié par un nom, un type (booléen, chaîne, DOMElement, etc.) et une description. L&#39;attribut &quot;inout&quot; avec la valeur &quot;out&quot; permet de spécifier que le paramètre &quot;result&quot; est obtenu en sortie de l&#39;appel SOAP.

La présence de l&#39;attribut &quot;static&quot; (avec la valeur &quot;true&quot;) décrit cette méthode comme statique, ce qui signifie que tous les paramètres de la méthode doivent être déclarés.

Une méthode de type &quot;const&quot; possède implicitement en entrée un document XML au format de son schéma associé.

Une description complète de l&#39;élément `<method>` d&#39;un schéma Adobe Campaign figure dans la section [Méthode ](../../configuration/using/schema/method.md) du chapitre « Référence des schémas ».

Exemple de la méthode &quot;ExecuteQuery&quot; de type &quot;const&quot; à partir du schéma &quot;xtk:queryDef&quot; :

```
<method name="ExecuteQuery" const="true">
  <help>Retrieve data from a query</help>
  <parameters>
    <param desc="Output xml document" name="output" type="DOMDocument" inout="out"/>
  </parameters>
</method>
```

Le paramètre en entrée de cette méthode est un document XML au format du schéma &quot;xtk:queryDef&quot;.

## Description des services Web : WSDL {#web-service-description--wsdl}

Un fichier WSDL (Web Service Description Library) est disponible pour chaque service. Ce fichier écrit en XML décrit le service dans un méta-langage, il précise les méthodes disponibles, les paramètres et le serveur à contacter pour exécuter le service.

### Génération du fichier WSDL {#wsdl-file-generation}

Pour générer un fichier WSDL vous devez, à partir d&#39;un navigateur Web, saisir l&#39;URL suivante :

https://`<server>`/nl/jsp/schemawsdl.jsp?schema=`<schema>`

Avec :

* **`<server>`** : le serveur applicatif Adobe Campaign (nlserver web)
* **`<schema>`** : la clé d&#39;identification du schéma (namespace:nom_du_schéma)

### Exemple sur la méthode &#39;ExecuteQuery&#39; du schéma &#39;xtk:queryDef&#39; {#example-on-the--executequery--method-of-schema--xtk-querydef-}

On génère le fichier WSDL à partir de l’URL :

`https://localhost/nl/jsp/schemawsdl.jsp?schema=xtk:queryDef`

Une description WSDL définit d’abord les types utilisés pour former des messages, associés dans des « ports », reliés à un protocole par des « liaisons » formant des Services Web.

#### Types {#types}

Les définitions de type reposent sur des schémas XML. Dans notre exemple, la méthode &quot;ExecuteQuery&quot; utilise comme paramètres une chaîne &quot;s:string&quot; et un document XML (`<s:complextype>`). La valeur renvoyée par la méthode (&quot;ExecuteQueryResponse&quot;) est un document XML (  `<s:complextype>`).

```
<types>
<s:schema elementFormDefault="qualified" targetNamespace="urn:xtk:queryDef">
  <s:element name="ExecuteQuery">
    <s:complexType>
      <s:sequence>
        <s:element maxOccurs="1" minOccurs="1" name="sessiontoken" type="s:string"/>
        <s:element maxOccurs="1" minOccurs="1" name="entity">
          <s:complexType>
            <s:sequence>
              <s:any/>
            </s:sequence>
          </s:complexType>
        </s:element>
      </s:sequence>
    </s:complexType>
  </s:element>
  <s:element name="ExecuteQueryResponse">
    <s:complexType>
      <s:sequence>
        <s:element maxOccurs="1" minOccurs="1" name="pdomOutput">
          <s:complexType mixed="true">
            <s:sequence>
              <s:any/>
            </s:sequence>
          </s:complexType>
        </s:element>
      </s:sequence>
    </s:complexType>
  </s:element>
```

#### Messages {#messages}

Le `<message>` décrit les noms et les types d&#39;un ensemble de champs à envoyer. La méthode utilise deux messages à transmettre en tant que paramètre (&quot;ExecuteQueryIn&quot;) et la valeur renvoyée (&quot;ExecuteQueryOut&quot;).

```
<message name="ExecuteQueryIn">
  <part element="tns:ExecuteQuery" name="parameters"/>
</message>

<message name="ExecuteQueryOut">
  <part element="tns:ExecuteQueryResponse" name="parameters"/>
</message> 
```

#### PortType {#porttype}

La partie `<porttype>` associe les messages sur l&#39;opération &quot;ExecuteQuery&quot; déclenchée par la requête (&quot;input&quot;) générant une réponse (&quot;output&quot;).

```
<portType name="queryDefMethodsSoap">
  <operation name="ExecuteQuery">
    <input message="tns:ExecuteQueryIn"/>
    <output message="tns:ExecuteQueryOut"/>
  </operation>
</portType>
```

#### Binding {#binding}

La partie `<binding>` spécifie le protocole de communication SOAP ( `<soap:binding>` ), le transport de données en HTTP (valeur de l&#39;attribut &quot;transport&quot;) et le format de données pour l&#39;opération &quot;ExecuteQuery&quot;. Le corps de l&#39;enveloppe SOAP contient les segments de message, directement, sans transformation.

```
<binding name="queryDefMethodsSoap" type="tns:queryDefMethodsSoap">
  <soap:binding style="document" transport="http://schemas.xmlsoap.org/soap/http"/>
  <operation name="ExecuteQuery">
    <soap:operation soapAction="xtk:queryDef#ExecuteQuery" style="document"/>
    <input>
      <soap:body encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" namespace="urn:xtk:queryDef" use="literal"/>
    </input>
    <output>
      <soap:body encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" namespace="urn:xtk:queryDef" use="literal"/>
    </output>
  </operation>
</binding>
```

#### Service {#service}

La partie `<service>` décrit le service &quot;XtkQueryDef&quot; avec son URI sur l&#39;URL du serveur applicatif Adobe Campaign.

```
<service name="XtkQueryDef">
  <port binding="tns:queryDefMethodsSoap" name="queryDefMethodsSoap">
    <soap:address location="https://localhost/nl/jsp/soaprouter.jsp"/>
  </port>
</service>
```

## Connectivité {#connectivity}

Adobe Campaign a renforcé la sécurité des mécanismes d&#39;authentification en introduisant les [zones de sécurité](../../installation/using/security-zones.md) et paramètres de gestion des sessions.

Deux modes d&#39;authentification sont disponibles :

* **via un appel à la méthode logon()**. Ce mode génère un jeton de session et un jeton de sécurité. C&#39;est le mode le plus sécurisé et donc celui qui est conseillé.

ou

* **via login et mot de passe** Adobe Campaign qui crée un jeton de session. Le jeton de session expire automatiquement après un délai. Ce mode est déconseillé et il demande de réduire les paramètres de sécurité de l&#39;application dans la configuration des zones (allowUserPassword=&quot;true&quot; et sessionTokenOnly=&quot;true&quot;).

### Caractéristiques du jeton de session {#session-token-characteristics}

Le jeton de session possède les caractéristiques suivantes :

* une durée de vie de X heures (la durée de vie est paramétrable dans le fichier &#39;serverConf.xml&#39;, la durée par défaut est 24h)
* une construction aléatoire (il ne contient plus le login et le mot de passe de l&#39;utilisateur)
* lors d&#39;un accès Web :

   * le jeton de session devient un jeton permanent, il n&#39;est pas détruit lorsque le navigateur est fermé
   * il est placé dans un cookie HTTP-ONLY (activation des cookies obligatoire pour les opérateurs)

### Caractéristiques du jeton de sécurité {#security-token-characteristics}

Le jeton de sécurité possède les caractéristiques suivantes :

* il est généré à partir du jeton de session
* il a une durée de vie de 24h par défaut (configurable dans le fichier &#39;serverConf.xml&#39;)
* il est stocké dans la console Adobe Campaign
* lors d&#39;un accès Web :

   * il est stocké dans une propriété document.__securityToken
   * les URL de la page sont mises à jour pour actualiser le jeton de sécurité
   * les formulaires sont également mises à jour via un champ caché contenant le jeton

#### Circulation du jeton de sécurité {#security-token-movement}

Lors d&#39;un accès console, il est :

* transmis dans la réponse du logon (dans l&#39;en-tête HTTP)
* utilisé à chaque requête (dans l&#39;en-tête HTTP)

Lors d&#39;un POST et GET HTTP :

* le serveur complète les liens avec le jeton
* le serveur ajoute un champ caché aux formulaires

Lors d&#39;un appel SOAP :

* il est ajouté aux en-têtes de l&#39;appel

### Exemples d&#39;appels {#call-examples}

* En utilisant **HttpSoapConnection/SoapService** :

```
  
    var cnx = new HttpSoapConnection("https://serverURL/nl/jsp/soaprouter.jsp");
  var session = new SoapService(cnx, 'urn:xtk:session');
  session.addMethod("Logon", "xtk:session#Logon",
                      ["sessiontoken", "string", "Login", "string", "Password", "string", "Parameters", "NLElement"],
                      ["sessionToken", "string", "sessionInfo", "NLElement", "securityToken", "string"]);
  
  var res = session.Logon("", "admin", "pwd", <param/>);
  var sessionToken = res[0];
  var securityToken = res[2];
  
  cnx.addTokens(sessionToken, securityToken);
  var query = new SoapService(cnx, 'urn:xtk:queryDef');
  query.addMethod("ExecuteQuery", "xtk:queryDef#ExecuteQuery",
                      ["sessiontoken", "string", "entity", "NLElement"],
                      ["res", "NLElement"]);
  
  var queryRes = query.ExecuteQuery("", <queryDef operation="select" schema="nms:recipient">
            <select>
              <node expr="@email"/>
              <node expr="@lastName"/>
              <node expr="@firstName"/>
            </select>
            <where>
              <condition expr="@email = 'joe.doe@aol.com'"/>
            </where>
          </queryDef>);
  logInfo(queryRes[0].toXMLString())
```

* En utilisant **HttpServletRequest** :

>[!NOTE]
>
>Les URL utilisées dans les appels **HttpServletRequest** suivants doivent être placées dans la liste autorisée dans la section des autorisations d&#39;URL du fichier **serverConf.xml**. C&#39;est également vrai pour l&#39;URL du serveur lui-même.

Exécution du logon() :

```
var req = new HttpClientRequest("https://serverURL/nl/jsp/soaprouter.jsp");
req.header["Content-Type"] = "text/xml; charset=utf-8";
req.header["SOAPAction"] =   "xtk:session#Logon";
req.method = "POST";
req.body = '<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:xtk:session">' +
    '<soapenv:Header/>' +
    '<soapenv:Body>' +
        '<urn:Logon>' +
            '<urn:sessiontoken></urn:sessiontoken>' +
            '<urn:strLogin>LOGIN_HERE</urn:strLogin>' +
            '<urn:strPassword>PASSWORD_HERE</urn:strPassword>' +
            '<urn:elemParameters></urn:elemParameters>' +
        '</urn:Logon>' +
    '</soapenv:Body>' +
'</soapenv:Envelope>';
req.execute();
           
var resp = req.response;
var xmlRes = new XML(String(resp.body).replace("<?xml version='1.0'?>",""));
var sessionToken = String(xmlRes..*::pstrSessionToken);;
var securityToken = String(xmlRes..*::pstrSecurityToken);
```

Exécution de la requête :

```
var req2 = new HttpClientRequest("https://serverURL/nl/jsp/soaprouter.jsp");
req2.header["Content-Type"] = "text/xml; charset=utf-8";
req2.header["SOAPAction"] =   "xtk:queryDef#ExecuteQuery";req2.header["X-Security-Token"] = securityToken;
req2.header["cookie"]           = "__sessiontoken="+sessionToken;
req2.method = "POST";
req2.body = '<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:xtk:queryDef">' +
             '<soapenv:Header/><soapenv:Body><urn:ExecuteQuery><urn:sessiontoken/><urn:entity>' +
                '<queryDef operation="select" schema="nms:recipient">' +
                  '<select><node expr="@email"/><node expr="@lastName"/><node expr="@firstName"/></select>' +
                  '<where><condition expr="@email = \'john.doe@aol.com\'"/></where>' +
                '</queryDef>' +
           '</urn:entity></urn:ExecuteQuery></soapenv:Body></soapenv:Envelope>';
req2.execute();
var resp2 = req2.response;
logInfo(resp2.body)
```
