---
product: campaign
title: Configuration réseau
description: Découvrez les directives sur la communication du système
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: b86236ae-95e9-4406-b60f-6d90ad0d4a01
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 100%

---

# Configuration réseau{#network-configuration}



## Communication entre les processus {#communication-between-processes}

Certains processus de l&#39;application ont besoin de communiquer entre eux ou d&#39;accéder au réseau, à la fois au LAN et à Internet. En conséquence, certains ports TCP doivent être ouverts pour ces processus.

Vous devez privilégier l&#39;utilisation du port Apache Tomcat embarqué (8080 par défaut) pour toutes les communications internes entre les différents serveurs d&#39;application d&#39;une plateforme Adobe Campaign.

### Serveur de diffusion {#delivery-server}

Pour le serveur de diffusion (**nlserver mta**), les ports suivants doivent être ouverts :

<table> 
 <tbody> 
  <tr> 
   <td> Ports<br /> </td> 
   <td> Destination<br /> </td> 
   <td> Commentaires<br /> </td> 
  </tr> 
  <tr> 
   <td> 25/tcp (smtp)<br /> </td> 
   <td> N'importe où<br /> </td> 
   <td> Trafic SMTP pour la diffusion d’e-mails.<br /> </td> 
  </tr> 
  <tr> 
   <td> 53/udp (domain)<br /> </td> 
   <td> Serveurs DNS<br /> </td> 
   <td> Requêtes DNS.<br /> </td> 
  </tr> 
  <tr> 
   <td> 38000/tcp (port par défaut)<br /> </td> 
   <td> SMS gateway<br /> </td> 
   <td> Utilisé pour transmettre le trafic SMS à l'opérateur SMS NetSize [option].<br /> </td> 
  </tr> 
  <tr> 
   <td> 7777/udp<br /> </td> 
   <td> Serveur de statistiques<br /> </td> 
   <td> Accès au serveur de statistiques.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Mails entrants {#inbound-mail}

Pour le processus de récupération des mails entrants (**nlserver inMail**), les ports suivants doivent être ouverts :

<table> 
 <tbody> 
  <tr> 
   <td> Ports<br /> </td> 
   <td> Destination<br /> </td> 
   <td> Commentaires<br /> </td> 
  </tr> 
  <tr> 
   <td> 110/tcp (pop3)<br /> </td> 
   <td> Serveur de mails interne<br /> </td> 
   <td> Trafic POP3 pour relever les messages rebonds.<br /> </td> 
  </tr> 
  <tr> 
   <td> 25/tcp (smtp)<br /> </td> 
   <td> Serveur de mails interne<br /> </td> 
   <td> Trafic SMTP pour transmettre les messages rebonds résiduels qui ne sont pas automatiquement traités par les règles prédéfinies.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Serveur applicatif {#application-server}

Pour le serveur applicatif (**nlserver web**), les ports suivants doivent être ouverts :

<table> 
 <tbody> 
  <tr> 
   <td> Ports<br /> </td> 
   <td> Destination<br /> </td> 
   <td> Commentaires<br /> </td> 
  </tr> 
  <tr> 
   <td> 80/tcp (http)<br /> 443/tcp (https)<br /> </td> 
   <td> N'importe où<br /> </td> 
   <td> Trafic HTTP ou HTTPS (notamment pour l'offre de délivrabilité).<br /> </td> 
  </tr> 
 </tbody> 
</table>

Lorsque plusieurs serveurs applicatifs d&#39;une plateforme Adobe Campaign doivent communiquer entre eux, il est recommandé de privilégier l&#39;utilisation du port du serveur Apache Tomcat (par défaut : 8080) plutôt que celle du port HTTP du serveur Web avec lequel l&#39;intégration du module de redirection a été réalisée. Ce port doit donc être ouvert entre ces différents serveurs.

### Etat de diffusion des SMS {#sms-delivery-status}

Pour le tracking des diffusions SMS (**nlserver sms**), le port suivant doit être ouvert :

<table> 
 <tbody> 
  <tr> 
   <td> Ports<br /> </td> 
   <td> Destination<br /> </td> 
   <td> Commentaires<br /> </td> 
  </tr> 
  <tr> 
   <td> 38000/tcp (port par défaut)<br /> </td> 
   <td> SMS gateway<br /> </td> 
   <td> Interroge le statut des files d'attente de diffusion gérées par la passerelle SMS NetSize [option].<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Client riche {#rich-client}

Pour le client riche Adobe Campaign (**nlclient**), les ports suivants doivent être ouverts :

<table> 
 <tbody> 
  <tr> 
   <td> Ports<br /> </td> 
   <td> Destination<br /> </td> 
   <td> Commentaires<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp (http)</p><p>443/tcp (https)</p><br /> </td> 
   <td> Serveur applicatif<br /> </td> 
   <td> Trafic (HTTP) SOAP.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Accès à la base de données {#database-access}

Tous les composants qui dépendent de la base de données doivent pouvoir s&#39;y connecter. Cela concerne la plupart des composants, à l&#39;exception du serveur de redirection qui peut travailler seul, et du client léger Win32 qui utilise uniquement le protocole HTTP (ou HTTPS) pour communiquer avec le serveur applicatif.

Les ports par défaut sont les suivants :

<table> 
 <tbody> 
  <tr> 
   <td> Type de base de données<br /> </td> 
   <td> Port (défaut)<br /> </td> 
   <td> Destination<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Oracle</strong><br /> </td> 
   <td> 1521/tcp<br /> </td> 
   <td> Serveur de base de données<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>PostgreSQL</strong><br /> </td> 
   <td> 5432/tcp<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Microsoft SQL Server</strong><br /> </td> 
   <td> 1433/tcp<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>DB2</strong><br /> </td> 
   <td> 50000/tcp<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Accès depuis l&#39;extérieur {#external-access}

En outre, certains composants doivent être accessibles depuis l’Internet public afin que les campagnes e-mail exécutées directement depuis Adobe Campaign puissent être visualisées. Cela signifie que certains ports doivent être ouverts pour les composants.

### Serveur de redirection {#redirection-server}

<table> 
 <tbody> 
  <tr> 
   <td> Port d'écoute<br /> </td> 
   <td> Location<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp (http)</p><p> 443/tcp (https)</p><br /> </td> 
   <td> N'importe où. Chaque clic sur un lien tracké génère une requête HTTP sur ce serveur.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Serveur Web externe {#external-web-server}

Ce serveur héberge les formulaires Web, pages miroir, etc. Les ports suivants doivent être ouverts :

<table> 
 <tbody> 
  <tr> 
   <td> Port d'écoute<br /> </td> 
   <td> Location<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp (http)</p><p> 443/tcp (https)</p><br /> </td> 
   <td> N'importe où. Nécessaire quand les formulaires Web sont directement gérés par la plateforme Adobe Campaign, ou lorsque les pages miroir sont utilisées.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Serveur applicatif interne (web) {#internal-application-server--web-}

<table> 
 <tbody> 
  <tr> 
   <td> Port d'écoute<br /> </td> 
   <td> Location<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp (http)</p><p> 443/tcp (https)</p><br /> </td> 
   <td> Tous les ordinateurs exécutant le client léger ou le client riche.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Intégration avec Adobe Experience Manager {#integration-with-adobe-experience-manager}

L&#39;intégration entre Adobe Campaign et Adobe Experience Manager nécessite l&#39;ouverture de plusieurs ports dans le cas d&#39;une installation &quot;on-premise&quot;. Pour plus d&#39;informations sur la configuration de cette intégration, consultez la [documentation détaillée](../../integrations/using/about-adobe-experience-manager.md).

<table> 
 <tbody> 
  <tr> 
   <td> Port d'écoute<br /> </td> 
   <td> Description<br /> </td> 
  </tr> 
  <tr> 
   <td> 80<br /> </td> 
   <td> Connexion d'AEM vers Adobe Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 4502</p><p> 4503</p><br /> </td> 
   <td> Connexion d'Adobe Campaign vers les instances "author" et "publish" d'AEM. Les ports à ouvrir peuvent être différents des ports par défaut, selon votre configuration d'AEM.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Bande passante {#bandwidth}

Un autre paramètre clé de la configuration réseau à prendre en compte. Elle est presque toujours sortante et très sollicitée lors des diffusions e-mail. Voici quelques exemples de configurations basées sur notre expérience :

* 1 Mb/s pour 10 000 emails par heure (taille moyenne de 30 Ko)
* 8 à 10 Mb/s pour 100 000 emails par heure (taille moyenne de 30 Ko)

Si vous avez des contraintes de bande passante, il est toutefois possible de planifier l&#39;exécution des campagnes d&#39;e-mailing la nuit, lorsque celle-ci est moins utilisée.
