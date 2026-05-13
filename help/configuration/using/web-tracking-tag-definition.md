---
product: campaign
title: Définition de la balise de tracking web
description: Définition de la balise de tracking web
feature: Application Settings
role: Developer
exl-id: 0b5575be-57e7-4eee-9c0a-e9ef4b0931bf
TQID: https://experienceleague.adobe.com/UkA0XyCzaDt2qlxpODQ-zoyC0YdKs3K5qg4UacvT8ck
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 362
ht-degree: 66%

---

# Balise de tracking web : définition{#web-tracking-tag-definition}



Une balise de tracking Web n&#39;est autre qu&#39;une URL construite avec les paramètres adéquats, transmise au serveur de redirection via une requête HTTP.

## Format des données à transmettre {#format-of-the-data-to-be-sent}

Le format d&#39;une URL de tracking Web est le suivant : **https://`<name_of_redirection_server>`:`<port>`/r/`<random_number>`?`<parameters>`**

>[!NOTE]
>
>Le nombre aléatoire ajouté à l&#39;URL sert à contourner les problèmes de mise en cache des pages Web par les navigateurs.

Le tableau ci-dessous donne la liste des paramètres spéciaux supportés par le serveur de redirection.

<table>
                     <thead>
                        <tr>
                           <th>Nom</th>
                           <th>Type</th>
                           <th>Description</th> 
                        </tr> 
                     </thead>
                     <tbody>
                        <tr>
                           <td>
                              <p>ID</p> 
                           </td>
                           <td>
                              <p>cookie de session</p> 
                           </td>
                           <td>
                              <p>Identifiant de diffusion et identifiant de destinataire.</p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>uuid230</p> 
                           </td>
                           <td>
                              <p>cookie permanent</p> 
                           </td>
                           <td>
                              <p>Identifiant de destinataire (utile si le cookie de session est absent).</p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>tagid</p> 
                           </td>
                           <td>
                              <p>paramètre d'URL</p> 
                           </td>
                           <td>
                              <p>Identifiant de la page Web trackée : c'est le seul paramètre obligatoire.</p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>jobid</p> 
                           </td>
                           <td>
                              <p>paramètre d'URL</p> 
                           </td>
                           <td>
                              <p>Identifiant de la diffusion à utiliser en l'absence de cookie de session. Cette valeur doit être
                                 exprimé en hexadécimal.
                              </p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>rcpid</p> 
                           </td>
                           <td>
                              <p>paramètre d'URL</p> 
                           </td>
                           <td>
                              <p>Paramètre utilisé pour identifier l'internaute. Le format de ce paramètre est « name=value »,
                                 où le nom est un champ du schéma des destinataires. Ce paramètre a la priorité sur
                                 identifiant contenu dans le cookie de session.
                              </p> 
                           </td> 
                        </tr> 
                     </tbody>  
                  </table>

**Quelques URL de webtracking**

* Passage sur une page d&#39;identifiant &#39;accueil&#39;

  **https://myserver.adobe.com/r/9862?tagid=home**

* Collecte des informations relatives au chiffre d&#39;affaires

  **https://myserver.adobe.com/r/4567?tagid=command&amount=100&article=2l**

* Spécification d&#39;un champ pour retrouver le destinataire

  **https://myserver.adobe.com/r/2353?tagid=home&rcpid=saccount%3D10**

  Un destinataire dont le numéro de compte est 10 est passé sur la page d&#39;accueil.

* Utilisation d&#39;une diffusion par défaut

  **https://myserver.adobe.com/r/2456?tagid=home&jobid=e6**

  Un destinataire est envoyé à la page d’accueil. Ces informations seront stockées dans la diffusion d&#39;identifiant 230 (e6 dans la base de données 16) sauf si un cookie de session contenant un identifiant de diffusion est envoyé avec cette requête.

>[!NOTE]
>
>Toutes les valeurs envoyées au serveur de redirection via les paramètres d&#39;URL doivent être encodées en URL. Dans les exemples donnés, notez que les caractères &#39;=&#39; et &#39;|&#39; sont codés respectivement en &#39;%3D&#39; et &#39;%7C&#39;.

## Méthodes de transmission des données {#data-transmission-methods}

Les méthodes possibles sont les suivantes :

* Insertion de l&#39;URL dans l&#39;attribut **&quot;src&quot;** d&#39;une balise HTML **`<img>`** intégrée à la page Web que l&#39;on souhaite tracker.
* Appel direct au serveur de redirection au moment de la génération de la page Web que l&#39;on souhaite tracker.
