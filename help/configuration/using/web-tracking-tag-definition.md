---
product: campaign
title: Définition de la balise de tracking web
description: Définition de la balise de tracking web
feature: Application Settings
role: Data Engineer, Developer
exl-id: 0b5575be-57e7-4eee-9c0a-e9ef4b0931bf
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 100%

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
                              <p>Identifiant de diffusion à utiliser s'il n'y a pas de cookie de session. Cette valeur est à exprimer en base 16.
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
                              <p>Paramètre permettant d'identifier l'internaute. Le format de ce paramètre est "nom=valeur", nom étant un champ du schéma des destinataires. Ce paramètre est prioritaire sur l'identifiant contenu dans le cookie de session.
                              </p> 
                           </td> 
                        </tr> 
                     </tbody>  
                  </table>

**Quelques URL de webtracking**

* Passage sur une page d&#39;identifiant &#39;accueil&#39;

  **https://myserver.adobe.com/r/9862?tagid=home**

* Collecte des informations relatives au chiffre d&#39;affaires

  **https://myserver.adobe.com/r/4567?tagid=command&amp;amount=100&amp;article=2l**

* Spécification d&#39;un champ pour retrouver le destinataire

  **https://myserver.adobe.com/r/2353?tagid=home&amp;rcpid=saccount%3D10**

  Un destinataire dont le numéro de compte est 10 est passé sur la page d&#39;accueil.

* Utilisation d&#39;une diffusion par défaut

  **https://myserver.adobe.com/r/2456?tagid=home&amp;jobid=e6**

  Un destinataire est passé sur la page d&#39;accueil. Cette information sera stockée dans la diffusion dont l&#39;identifiant est 230 (soit e6 en base 16), si aucun cookie de session contenant un identifiant de diffusion n&#39;est envoyé avec cette requête.

>[!NOTE]
>
>Toutes les valeurs transmises au serveur de redirection via des paramètres d&#39;URL doivent être URL-encodées. Dans les exemples fournis, vous remarquerez que les caractères &#39;=&#39; et &#39;|&#39; sont respectivement encodés en &#39;%3D&#39; et &#39;%7C&#39;.

## Méthodes de transmission des données {#data-transmission-methods}

Les méthodes possibles sont les suivantes :

* Insertion de l&#39;URL dans l&#39;attribut **&quot;src&quot;** d&#39;une balise HTML **`<img>`** intégrée à la page Web que l&#39;on souhaite tracker.
* Appel direct au serveur de redirection au moment de la génération de la page Web que l&#39;on souhaite tracker.
