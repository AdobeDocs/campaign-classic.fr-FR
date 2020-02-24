---
title: Comprendre la gestion des quarantaines
seo-title: Comprendre la gestion des quarantaines
description: Comprendre la gestion des quarantaines
seo-description: null
page-status-flag: never-activated
uuid: 9421e26c-bdcc-4588-8e44-fa6f31051081
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
discoiquuid: 56cbf48a-eb32-4617-8f80-efbfd05976ea
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 16e7266a101b4abea3271c32fcc403e7d7fbaa2d

---


# Comprendre la gestion des quarantaines{#understanding-quarantine-management}

## A propos des quarantaines {#about-quarantines}

Adobe Campaign gère une liste d&#39;adresses en quarantaine. Les destinataires dont l&#39;adresse est en quarantaine sont par défaut exclus lors de l&#39;analyse d&#39;une diffusion : ils ne seront pas ciblés. Une adresse email peut être mise en quarantaine par exemple lorsque la boîte de messagerie est pleine ou si l&#39;adresse n&#39;existe pas. Dans tous les cas, la mise en quarantaine répond à des règles précises qui sont décrites ci-après.

>[!NOTE]
>
>Cette section s&#39;applique aux canaux on-line : email, SMS et notification push.

### Optimiser votre diffusion par le biais des mises en quarantaine {#optimizing-your-delivery-through-quarantines}

Les profils dont l&#39;adresse email ou le numéro de téléphone est en quarantaine sont exclus automatiquement lors de la préparation des messages (voir [Identifier les adresses en quarantaine pour une diffusion](#identifying-quarantined-addresses-for-a-delivery)). Le taux d&#39;erreur ayant une incidence importante sur la vitesse de diffusion, les envois sont ainsi accélérés.

Certains fournisseurs d&#39;accès Internet considèrent automatiquement les emails comme du spam si le taux d&#39;adresses invalides est trop élevé. Les mises en quarantaine permettent donc d&#39;éviter des blacklistages de la part de ces fournisseurs.

De plus, elles réduisent les coûts d&#39;envoi des SMS en excluant les numéros de téléphone erronés des diffusions. Pour plus d&#39;informations sur les bonnes pratiques en matière de sécurisation et d&#39;optimisation de vos diffusions, consultez [cette page](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliveryBestPractices.html).

### Mise en quarantaine et blacklistage {#quarantine-vs-blacklisting}

La **mise en quarantaine** concerne uniquement une adresse, pas le profil lui-même. Cela signifie que si deux profils utilisent la même adresse email, en cas de mise en quarantaine de l&#39;adresse, les deux profils seront impactés.

De même, un profil, dont l&#39;adresse email est en quarantaine qui met à jour son profil et enregistre une nouvelle adresse pourra de nouveau être ciblé par des actions de diffusions.

En revanche, en cas de **blacklistage**, c&#39;est le profil qui ne sera plus ciblé par aucune diffusion, par exemple après une désinscription (opt-out).

>[!NOTE]
>
>Lorsqu&#39;un utilisateur répond à un SMS avec un mot-clé tel que &quot;STOP&quot; pour se désinscrire des diffusions SMS, son profil n&#39;est pas blacklisté comme c&#39;est le cas pour la désinscription des emails. Le numéro de téléphone du profil est mis en quarantaine, de sorte que l&#39;utilisateur puisse continuer à recevoir des emails.

## Identifier les adresses en quarantaine {#identifying-quarantined-addresses}

Les adresses en quarantaine peuvent être répertoriées pour une diffusion spécifique ou l&#39;ensemble de la plateforme.

### Identifier les adresses en quarantaine pour une diffusion {#identifying-quarantined-addresses-for-a-delivery}

Quarantined addresses for a specific delivery are listed during the delivery preparation phase, in the delivery logs of the delivery dashboard (see [Delivery logs and history](../../delivery/using/monitoring-a-delivery.md#delivery-logs-and-history)).

### Identifier les adresses en quarantaine pour l&#39;ensemble de la plateforme {#identifying-quarantined-addresses-for-the-entire-platform}

Les administrateurs peuvent répertorier les adresses en quarantaine pour l&#39;ensemble de la plateforme depuis le nœud **[!UICONTROL Administration > Gestion de campagne > Gestion des NP@I > NP@I et adresses]**.

>[!NOTE]
>
>Ce menu répertorie les éléments en quarantaine pour les canaux **email**, **SMS** et **notification push**.

Les informations disponibles pour chacune des adresses sont les suivantes :

![](assets/tech_quarant_npai.png)

>[!NOTE]
>
>L&#39;augmentation du nombre de quarantaines est un phénomène normal, lié à &quot;l&#39;usure&quot; de la base. Par exemple, si l&#39;on considère que la durée de vie d&#39;une adresse email est de trois ans et que la table des destinataires augmente de 50% tous les ans, l&#39;augmentation des quarantaines peut être calculée comme suit :
>
>Fin de l&#39;année 1 : (1*0,33)/(1+0,5)=22%.
Fin de l&#39;année 2 : ((1,22*0,33)+0,33)/(1,5+0,75)=32,5 %.

### Identifier les adresses en quarantaine dans les rapports de diffusion {#identifying-quarantined-addresses-in-delivery-reports}

Les rapports suivants fournissent des informations relatives aux adresses en quarantaine :

* Pour chaque diffusion, le rapport **[!UICONTROL Synthèse de la diffusion]** permet de consulter le nombre d&#39;adresses en quarantaine dans la cible de la diffusion. Il affiche :

   * le nombre d&#39;adresses mises en quarantaine lors de l&#39;analyse de la diffusion,

   * le nombre d&#39;adresses passées en quarantaine suite à l&#39;action de diffusion.

* Le rapport **[!UICONTROL Echecs et retours]** affiche des informations relatives aux adresses en quarantaine, aux types d&#39;erreurs rencontrées, etc., et une répartition des échecs par domaines.

Vous pouvez consulter ces informations pour l&#39;ensemble des diffusions de la plateforme (**Page d&#39;accueil > Rapports**) ou pour une diffusion particulière. Vous pouvez également créer des rapports personnalisés et sélectionner les informations à afficher.

### Identifier les adresses en quarantaine pour un destinataire {#identifying-quarantined-addresses-for-a-recipient}

Pour chaque destinataire, vous pouvez consulter l&#39;état de son adresse email. Pour cela, sélectionnez le profil du destinataire et cliquez sur l&#39;onglet **[!UICONTROL Diffusions]**. Vous pouvez voir pour l&#39;ensemble des diffusions vers ce destinataire si l&#39;adresse a été en échec, mise en quarantaine lors de l&#39;analyse, etc. Pour chaque dossier, vous ne pouvez afficher que les destinataires dont l&#39;adresse email est en quarantaine. Pour cela, utilisez le filtre applicatif **[!UICONTROL Email en quarantaine]**.

![](assets/tech_quarant_recipients_filter.png)

### Sortir une adresse de quarantaine {#removing-a-quarantined-address}

Si vous avez besoin de sortir une adresse de quarantaine, modifiez manuellement son statut et choisissez **[!UICONTROL Valide]**.

![](assets/tech_quarant_error_status.png)

Si vous choisissez le statut **[!UICONTROL En whiteliste]**, l&#39;adresse sera ciblée systématiquement à chaque diffusion même en cas d&#39;erreur.

>[!CAUTION]
Les adresses en blackliste ne sont pas soumises au système des quarantaines et ne sont pas ciblées, même si vous modifiez le statut de l&#39;adresse.

Vous pouvez également modifier le nombre d&#39;erreurs prévues au compteur et la durée entre deux erreurs. Pour cela, modifiez les paramètres de l&#39;assistant de déploiement (Canal emails/Paramètres avancés). Reportez-vous à [cette section](../../installation/using/deploying-an-instance.md) pour la présentation de l&#39;assistant de déploiement.

## Conditions de mise en quarantaine d&#39;une adresse {#conditions-for-sending-an-address-to-quarantine}

Adobe Campaign gère la mise en quarantaine en fonction du type d’échec de remise et de la raison attribuée lors de la qualification des messages d’erreur (voir qualification [du courrier](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification)Rebond) et des types et motifs d’échec de [remise](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons).

* **Erreur de type Ignoré** : les erreurs de type Ignoré ne mettent pas une adresse en quarantaine.
* **Erreur de type Hard** : l&#39;adresse email correspondante est mise immédiatement en quarantaine.
* **Erreur de type Soft** : les erreurs de type Soft ne provoquent pas de mise en quarantaine immédiate mais incrémentent un compteur d&#39;erreurs. For more on this, see [Soft error management](#soft-error-management).

Si un utilisateur qualifie un email comme du spam (**système de gestion des plaintes (feedback loop)**), le message est automatiquement redirigé vers une boîte email technique gérée par Adobe. L&#39;adresse email de l&#39;utilisateur est alors automatiquement mise en quarantaine.

Dans la liste des adresses en quarantaine, le champ **[!UICONTROL Raison de l&#39;erreur]** indique pourquoi l&#39;adresse sélectionnée a été mise en quarantaine. La quarantaine dans Adobe Campaign respecte la casse. Veillez à importer les adresses email en minuscules, de telle sorte qu&#39;elles ne soient pas reciblées ultérieurement.

![](assets/tech_quarant_error_reasons.png)

### Gestion des erreurs douces {#soft-error-management}

Contrairement aux erreurs matérielles, les erreurs logicielles n’envoient pas immédiatement une adresse à la quarantaine, mais incrémentent plutôt un compteur d’erreurs.

* Lorsque le compteur d’erreurs atteint le seuil limite, l’adresse est placée en quarantaine.
* Dans les paramétrages par défaut, le seuil est de cinq erreurs : deux erreurs sont significatives si elles sont séparées d&#39;au moins 24h. L&#39;adresse est mise en quarantaine à la sixième erreur.
* Le seuil du compteur d&#39;erreurs peut être modifié. For more on this, refer to [Retries after a delivery temporary failure](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure).

Le compteur d’erreurs est réinitialisé si la dernière erreur significative s’est produite il y a plus de 10 jours. The address status then changes to **Valid** and it is deleted from the list of quarantines by the **Database cleanup** workflow.

## Quarantaines des notifications push {#push-notification-quarantines}

Le mécanisme de quarantaine des notifications Push est globalement identique au processus général. Voir [A propos des quarantaines](#about-quarantines). Toutefois, certaines erreurs sont gérées différemment pour les notifications Push. Par exemple, pour certaines erreurs logicielles, aucune nouvelle tentative n’est effectuée au cours de la même remise. Les spécificités de la notification Push sont énumérées ci-dessous. Le mécanisme de nouvelle tentative (nombre de tentatives, fréquence) est le même que pour les courriers électroniques.

Les éléments mis en quarantaine sont les jetons d&#39;appareil.

### Quarantaine iOS {#ios-quarantine}

**Pour iOS - connecteur binaire**

Pour chaque notification, Adobe Campaign reçoit les erreurs synchrones et asynchrones du serveur APNS. Adobe Campaign génère des erreurs soft pour les erreurs synchrones suivantes :

* Problèmes liés à la longueur de la payload : aucune reprise, la raison de l&#39;échec est **[!UICONTROL Inatteignable]**.
* Problèmes liés à l&#39;expiration du certificat : aucune reprise, la raison de l&#39;échec est **[!UICONTROL Inatteignable]**.
* Perte de la connexion pendant la diffusion : reprise effectuée, la raison de l&#39;échec est **[!UICONTROL Inatteignable]**.
* Problème lié à la configuration du service (certificat non valide, mot de passe du certificat incorrect, aucun certificat) : aucune reprise, la raison de l&#39;échec est **[!UICONTROL Inatteignable]**.

Le serveur APNS informe de manière asynchrone Adobe Campaign de la désinscription d&#39;un jeton d&#39;appareil (lors de la désinstallation de l&#39;application mobile par l&#39;utilisateur). Le workflow **[!UICONTROL mobileAppOptOutMgt]** s&#39;exécute toutes les 6 heures pour contacter les services de feedback APNS afin de mettre à jour la table **AppSubscriptionRcp**. Pour tous les jetons désactivés, le champ **Désactivé** est défini sur **True** et l&#39;inscription associée à ce jeton d&#39;appareil est automatiquement exclue des prochaines diffusions.

**Pour iOS - connecteur HTTP/2**

Le protocole HTTP/2 permet d&#39;obtenir un feedback direct et le statut de chaque notification push. Si le connecteur HTTP/2 est utilisé, le service de feedback n&#39;est plus appelé par le workflow **[!UICONTROL mobileAppOptOutMgt]**. Les jetons désinscrits sont gérés différemment par le connecteur binaire iOS et le connecteur HTTP/2 iOS. Un jeton est considéré comme désinscrit lorsqu&#39;une application mobile est désinstallée ou réinstallée.

Si l&#39;APNS renvoie de manière synchrone un statut &quot;désinscrit&quot; pour un message, le jeton cible est immédiatement mis en quarantaine.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Scénario</strong><br /> </td> 
   <td> <strong>Status</strong><br /> </td> 
   <td> <strong>Message de l'erreur</strong><br /> </td> 
   <td> <strong>Type de l'échec</strong><br /> </td> 
   <td> <strong>Raison de l'échec</strong><br /> </td> 
   <td> <strong>Réessayer</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Appareil ciblé sous tension<br /> </td> 
   <td> Ok<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Appareil ciblé hors tension<br /> </td> 
   <td> Ok<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> L'utilisateur désactive les notifications de l'application<br /> </td> 
   <td> Ok<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Création du message/phase d'analyse - payload trop volumineuse<br /> </td> 
   <td> Echec<br /> </td> 
   <td> Payload trop longue<br /> </td> 
   <td> Soft<br /> </td> 
   <td> Refusés<br /> </td> 
   <td> Non<br /> </td> 
  </tr> 
  <tr> 
   <td> Création du message/phase d'analyse - problème lié à un format de contenu inattendu<br /> </td> 
   <td> Echec<br /> </td> 
   <td> Messages d'erreur différents selon l'erreur<br /> </td> 
   <td> Soft<br /> </td> 
   <td> Indéfinie<br /> </td> 
   <td> Non<br /> </td> 
  </tr> 
  <tr> 
   <td> Problème de certificat (mot de passe, endommagement, etc.) et problème de test de connexion à l'APNS<br /> </td> 
   <td> Echec<br /> </td> 
   <td> Messages d'erreur différents selon l'erreur<br /> </td> 
   <td> Soft<br /> </td> 
   <td> Refusés<br /> </td> 
   <td> Non<br /> </td> 
  </tr> 
  <tr> 
   <td> Perte de la connexion réseau pendant l'envoi<br /> </td> 
   <td> Echec<br /> </td> 
   <td> Erreur de connexion<br /> </td> 
   <td> Indéfinie<br /> </td> 
   <td> Inatteignable<br /> </td> 
   <td> Oui<br /> </td> 
  </tr> 
  <tr> 
   <td> Rejet du message APNS : Désinscription<br /> de l’utilisateur a supprimé l’application ou le jeton a expiré<br /> </td> 
   <td> Echec<br /> </td> 
   <td> Désinscrit<br /> </td> 
   <td> Hard<br /> </td> 
   <td> Utilisateur inconnu<br /> </td> 
   <td> Non<br /> </td> 
  </tr> 
  <tr> 
   <td> Rejet du message par l'APNS : toutes les autres erreurs<br /> </td> 
   <td> Echec<br /> </td> 
   <td> La raison de l'erreur de rejet est indiquée dans le message d'erreur<br /> </td> 
   <td> Soft<br /> </td> 
   <td> Refusés<br /> </td> 
   <td> Non<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Quarantaine Android {#android-quarantine}

**Pour Android V1**

Pour chaque notification, Adobe Campaign reçoit les erreurs synchrones directement du serveur FCM. Adobe Campaign les gère à la volée et génère des erreurs hard ou soft selon la gravité des erreurs. Des reprises peuvent être effectuées :

* Dépassement de la longueur de la payload, problème de connexion, problème lié à la disponibilité du service : reprise effectuée, erreur soft, raison de l&#39;échec : **[!UICONTROL Refusés]**.
* Dépassement du quota d&#39;appareils : aucune reprise, erreur soft, raison de l&#39;échec : **[!UICONTROL Refusés]**.
* Jeton non valide ou désinscrit, erreur inattendue, problème lié au compte de l&#39;expéditeur : aucune reprise, erreur hard, raison de l&#39;erreur : **[!UICONTROL Refusés]**.

Le workflow **[!UICONTROL mobileAppOptOutMgt]** s&#39;exécute toutes les 6 heures pour mettre à jour la table **AppSubscriptionRcp**. Pour les jetons déclarés comme désinscrits ou qui ne sont plus valides, le champ **Désactivé** est défini sur **True** et l&#39;inscription associée à ce jeton d&#39;appareil est automatiquement exclue des prochaines diffusions.

Pendant l&#39;analyse de la diffusion, tous les appareils qui sont exclus de la cible sont automatiquement ajoutés à la table **excludeLogAppSubRcp**.

>[!NOTE]
Pour les utilisateurs qui ont recours au connecteur Baidu, voici les différents types d&#39;erreur :
* Problème de connexion au début de la diffusion : type d&#39;échec **[!UICONTROL Indéfini]**, raison d&#39;échec **[!UICONTROL Inatteignable]**, reprise effectuée.
* Perte de connexion pendant une diffusion : erreur soft, raison d&#39;échec **[!UICONTROL Refusés]**, reprise effectuée.
* Erreur synchrone renvoyée par Baidu pendant l&#39;envoi : erreur hard, raison d&#39;échec **[!UICONTROL Refusés]**, aucune reprise.

Adobe Campaign contacte le serveur Baidu toutes les 10 minutes pour récupérer le statut du message envoyé et met à jour les broadlogs. Si un message est déclaré comme envoyé, le statut du message dans les broadlogs est défini sur **[!UICONTROL Reçu]**. Si Baidu déclare une erreur, le statut est défini sur **[!UICONTROL Echoué]**.

**Pour Android V2**

Le mécanisme de mise en quarantaine Android V2 utilise le même processus qu&#39;Android V1. Il en va de même pour les mises à jour d&#39;inscriptions et d&#39;exclusions. Pour plus d&#39;informations, voir la section [Android V1](#android-quarantine).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Scénario</strong><br /> </td> 
   <td> <strong>Status</strong><br /> </td> 
   <td> <strong>Message de l'erreur</strong><br /> </td> 
   <td> <strong>Type de l'échec</strong><br /> </td> 
   <td> <strong>Raison de l'échec</strong><br /> </td> 
   <td> <strong>Réessayer</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Création du message/phase d'analyse : mots-clés illégaux utilisés dans les champs personnalisés<br /> </td> 
   <td> Echec<br /> </td> 
   <td> Les mots-clés suivants ne peuvent être utilisés : {1}<br /> </td> 
   <td> Soft<br /> </td> 
   <td> </td> 
   <td> Non<br /> </td> 
  </tr> 
  <tr> 
   <td> Création du message/phase d'analyse : payload trop volumineuse<br /> </td> 
   <td> Echec<br /> </td> 
   <td> La notification est trop lourde : {1} bits contre {2} autorisés<br /> </td> 
   <td> Soft<br /> </td> 
   <td> Refusés<br /> </td> 
   <td> Non<br /> </td> 
  </tr> 
  <tr> 
   <td> Perte de la connexion réseau pendant l'envoi<br /> </td> 
   <td> Echec<br /> </td> 
   <td> Aucune réponse du service Firebase Cloud Messaging pour cette adresse : {1}<br /> </td> 
   <td> Soft<br /> </td> 
   <td> Inatteignable<br /> </td> 
   <td> Oui<br /> </td> 
  </tr> 
  <tr> 
   <td> Rejet du message par le FCM : le serveur FCM est temporairement hors service (par exemple avec des délais). <br /> </td> 
   <td> Echec<br /> </td> 
   <td> Le service Firebase Cloud Messaging est temporairement hors service<br /> </td> 
   <td> Soft<br /> </td> 
   <td> Inatteignable<br /> </td> 
   <td> Oui<br /> </td> 
  </tr> 
  <tr> 
   <td> Rejet du message par le FCM : erreur lors de l'authentification du compte de l'expéditeur<br /> </td> 
   <td> Echec<br /> </td> 
   <td> Echec de l'identification du compte développeur, vérifiez votre identifiant et mot de passe<br /> </td> 
   <td> Soft<br /> </td> 
   <td> Refusés<br /> </td> 
   <td> Non<br /> </td> 
  </tr> 
  <tr> 
   <td> Rejet du message par le FCM : dépassement du quota d'appareils<br /> </td> 
   <td> Echec<br /> </td> 
   <td> </td> 
   <td> Soft<br /> </td> 
   <td> Refusés<br /> </td> 
   <td> Oui<br /> </td> 
  </tr> 
  <tr> 
   <td> Rejet du message par le FCM : inscription invalide / non inscrit<br /> </td> 
   <td> Echec<br /> </td> 
   <td> </td> 
   <td> Hard<br /> </td> 
   <td> Utilisateur inconnu<br /> </td> 
   <td> Non<br /> </td> 
  </tr> 
  <tr> 
   <td> Rejet du message par le FCM : toutes les autres erreurs<br /> </td> 
   <td> Echec<br /> </td> 
   <td> Le serveur Firebase Cloud Messaging a retourné un code d'erreur non attendu : {1} </td> 
   <td> </td> 
   <td> Refusés<br /> </td> 
   <td> Non<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Quarantaines des SMS {#sms-quarantines}

**Pour les connecteurs standards**

Le mécanisme de quarantaine des messages SMS est globalement identique au processus général. Voir [A propos des quarantaines](#about-quarantines). Les spécificités du SGS sont énumérées ci-dessous.

>[!NOTE]
Le tableau **[!UICONTROL Qualification des logs de diffusion]** ne s&#39;applique pas au connecteur **SMPP Générique étendu**.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Scénario</strong><br /> </td> 
   <td> <strong>Status</strong><br /> </td> 
   <td> <strong>Message de l'erreur</strong><br /> </td> 
   <td> <strong>Type de l'échec</strong><br /> </td> 
   <td> <strong>Raison de l'échec</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Transmis au prestataire<br /> </td> 
   <td> Envoyés<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Reçu sur le mobile<br /> </td> 
   <td> Reçu<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Erreur retournée par le prestataire<br /> </td> 
   <td> Echec<br /> </td> 
   <td> Erreur lors de la récupération de données (SR ou MO).<br /> </td> 
   <td> Soft<br /> </td> 
   <td> Inatteignable<br /> </td> 
  </tr> 
  <tr> 
   <td> Accusé de réception du MT non valide<br /> </td> 
   <td> Echec<br /> </td> 
   <td> Erreur '{1}' lors du traitement de la trame d'accusé réception d'une requête d'envoi.<br /> </td> 
   <td> Soft<br /> </td> 
   <td> Inatteignable<br /> </td> 
  </tr> 
  <tr> 
   <td> Erreur lors de l'envoi du MT<br /> </td> 
   <td> Echec<br /> </td> 
   <td> Erreur lors de l'envoi des messages.<br /> </td> 
   <td> Soft<br /> </td> 
   <td> Inatteignable<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Pour le connecteur SMPP générique étendu**

Lors de l&#39;utilisation du protocole SMPP pour envoyer des SMS, la gestion des erreurs est traitée différemment. Pour plus d&#39;informations sur le connecteur SMPP générique étendu, consultez [cette page](../../delivery/using/sms-channel.md#creating-an-smpp-external-account).

Le connecteur SMPP récupère les données du message du SR (rapport d&#39;état) qui est renvoyé à l&#39;aide d&#39;expressions régulières (regex) pour filtrer son contenu. Ces données sont alors mises en correspondance avec les informations figurant dans la table **[!UICONTROL Qualification des logs de diffusion]** (disponible via le menu **[!UICONTROL Administration]** > **[!UICONTROL Gestion de campagnes]** > **[!UICONTROL Gestion des NP@I]**).

Avant qu&#39;un nouveau type d&#39;erreur ne soit qualifié, la raison de l&#39;échec est toujours défini sur **Refusé** par défaut.

>[!NOTE]
Les types d’échec et les raisons de l’échec sont les mêmes que pour les courriers électroniques. See [Delivery failure types and reasons](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons).
Demandez à votre prestataire la liste des codes d&#39;erreur et des états pour définir les types et les raisons corrects des erreurs dans la table Qualification des logs de diffusion.

Exemple de message généré :

```
SR Generic DELIVRD 000|#MESSAGE#
```

* Tous les messages d&#39;erreur commencent par **SR** pour faire la distinction entre les codes d&#39;erreur SMS et les codes d&#39;erreur email.
* La seconde partie (**Generic**, dans cet exemple) du message d&#39;erreur fait référence au nom de l&#39;implémentation du SMSC comme défini dans le champ **[!UICONTROL Nom de l&#39;implémentation du SMSC]** du compte externe SMS. Voir [cette page](../../delivery/using/sms-channel.md#creating-an-smpp-external-account).

   Comme un même code d&#39;erreur peut avoir une signification différente pour chaque prestataire, ce champ vous permet de déterminer quel prestataire a généré le code d&#39;erreur. Vous pouvez alors rechercher l&#39;erreur dans la documentation du prestataire adéquat.

* La troisième partie (**DELIVRD**, dans cet exemple) du message d&#39;erreur correspond au code d&#39;état extrait du SR à l&#39;aide de la regex d&#39;extraction de code d&#39;état définie dans le compte externe SMS.

   Cette regex est spécifiée dans l&#39;onglet **[!UICONTROL Spécificités du SMSC]** du compte externe. Voir [cette page](../../delivery/using/sms-channel.md#creating-an-smpp-external-account).

   ![](assets/tech_quarant_error_regex.png)

   Par défaut, la regex extrait le champ **stat:** comme défini dans la section **Appendix B** de la **spécification SMPP 3.4**.

* La quatrième partie (**000**, dans cet exemple) du message d&#39;erreur correspond au code d&#39;erreur extrait du SR à l&#39;aide de la regex d&#39;extraction de code d&#39;erreur définie dans le compte externe SMS.

   Cette regex est spécifiée dans l&#39;onglet **[!UICONTROL Spécificités du SMSC]** du compte externe. Voir [cette page](../../delivery/using/sms-channel.md#creating-an-smpp-external-account).

   Par défaut, la regex extrait le champ **err:** comme défini dans la section **Appendix B** de la **spécification SMPP 3.4**.

* Everything that comes after the pipe symbol (|) is only displayed in the **[!UICONTROL First text]** column of the **[!UICONTROL Delivery log qualification]** table. This content is always replaced by **#MESSAGE#** after the message is normalized. This process avoids having multiple entries for similar errors and is the same as for emails. Pour plus d&#39;informations, reportez-vous à la section Qualification [de courrier](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification)Rebond.

Le connecteur SMPP générique étendu applique une méthode heuristique pour rechercher des valeurs par défaut sensibles : si l&#39;état commence par **DELIV**, il est considéré comme une réussite, car il correspond aux états **DELIVRD** ou **DELIVERED** courants, utilisés par la plupart des prestataires. Tout autre état correspond à un échec hard.
