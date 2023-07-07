---
product: campaign
title: Intégration via SOAP (côté serveur)
description: Intégration via SOAP (côté serveur)
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: interaction
content-type: reference
topic-tags: unitary-interactions
exl-id: 3eaef689-44fa-41b3-ade8-9fe447e165ec
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 100%

---

# Intégration via SOAP (côté serveur){#integration-via-soap-server-side}



Les services web SOAP fournis pour la gestion des offres sont différents de ceux habituellement utilisés dans Adobe Campaign. Ils sont accessibles via l&#39;URL d&#39;interaction décrite dans la section précédente et permettent de proposer ou mettre à jour des offres pour un contact donné.

## Proposition d&#39;offres {#offer-proposition}

Pour une proposition d&#39;offres via SOAP, vous devez ajouter la commande **nms:proposition#Propose**, suivie des paramètres suivants :

* **targetId** : clé primaire du destinataire (il peut s&#39;agir d&#39;une clé composite).
* **maxCount** : indique le nombre de propositions d&#39;offre pour le contact.
* **context** : vous permet d&#39;ajouter des informations contextuelles dans le schéma d&#39;espace. Si le schéma utilisé est **nms:interaction**, **`<empty>`** doit être ajouté.
* **categories** : indique la ou les catégories auxquelles doivent appartenir la ou les offres proposées.
* **themes** : indique la ou les thèmes auxquelles doivent appartenir la ou les offres proposées.
* **uuid** : valeur du cookie permanent Adobe Campaign (&quot;uuid230&quot;).
* **nlid** : valeur du cookie de session Adobe Campaign (&quot;nlid&quot;).
* **noProp** : utilisez la valeur &quot;true&quot; pour désactiver l&#39;insertion de propositions.

>[!NOTE]
>
>Les paramètres **targetId** et **maxCount** sont obligatoires. Les autres sont optionnels.

En réponse à la requête, le service SOAP renverra les paramètres suivants :

* **interactionId** : id de l&#39;interaction.
* **propositions** : élément XML, contient la liste des propositions, chacune ayant un id et une représentation HTML propre.

## Mise à jour d&#39;une offre {#offer-update}

Ajoutez la commande **nms:interaction#UpdateStatus** dans l&#39;URL, puis les paramètres suivants :

* **proposition** : chaîne de caractères, contient l&#39;identifiant de la proposition donnée en sortie lors d&#39;un appel au moteur. Voir [Proposition d&#39;offres](#offer-proposition).
* **status** : nombre, indique le nouveau statut de l&#39;offre. Les valeurs possibles sont listées dans l&#39;énumération **propositionStatus**, dans le schéma **nms:common**. Par exemple, d&#39;usine, le nombre 3 correspond au statut **Acceptée**.
* **Context** : élément XML, vous permet d&#39;ajouter des informations contextuelles dans le schéma d&#39;espace. Si le schéma utilisé est **nms:interaction**, **`<empty>`** doit être ajouté.

## Exemple d&#39;utilisation d&#39;un appel SOAP {#example-using-a-soap-call}

Voici un exemple de code pour un appel SOAP :

```
<%
  var space = request.parameters.sp
  var cnx = new HttpSoapConnection(
    "https://" + request.serverName + ":" + request.serverPort + "/interaction/" + env + "/" + space,
    "utf-8",
    HttpSoapConnection.SOAP_12)
  var session = new SoapService(cnx, "nms:interaction")
  var action = request.parameters.a
  if( action == undefined )
    action = 'propose'

  try
  {
    switch( action )
    {
    case "update":
      var proposition = request.parameters.p
      var status      = request.parameters.st
      session.addMethod("UpdateStatus", "nms:interaction#UpdateStatus",
       ["proposition", "string",
        "status",      "string",
        "context",     "NLElement"],
       [])
      session.UpdateStatus(proposition, status, <undef/>)
      var redirect = request.parameters.r
      if( redirect != undefined )
        response.sendRedirect(redirect)
      break;

    case "propose":
      var count = request.parameters.n
      var target = request.parameters.t
      var categorie = request.parameters.c
      var theme = request.parameters.th
      var layout = request.parameters.l
      if( count == undefined )
        count = 1
      session.addMethod("Propose", "nms:proposition#Propose",
       ["targetId",      "string",
        "maxCount",      "string",
         "categories",    "string",
         "themes",        "string",
        "context",       "NLElement"],
       ["interactionId", "string",
        "propositions",  "NLElement"])
      response.setContentType("text/html")
      var result = session.Propose(target, count, category, theme, <empty/>)
      var props = result[1]
  %><table><tr><%
      for each( var propHtml in props.proposition.*.mdSource )
      {
        %><td><%=propHtml%></td><%
      }
  %></tr></table><%
      break;
    }
  }
  catch( e )
  {
  }
  %>
```
