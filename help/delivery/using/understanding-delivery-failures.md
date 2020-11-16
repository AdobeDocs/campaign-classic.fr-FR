---
title: Comprendre les diffusions en échec
description: Découvrez comment comprendre les échecs de diffusion
page-status-flag: never-activated
uuid: 03a91f84-77fe-40a9-8be9-a6a35a873ae1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
discoiquuid: 78b58a7a-b387-4d5d-80d5-01c06f83d759
translation-type: tm+mt
source-git-commit: cb2fb5a338220c54aba96b510a7371e520c2189e
workflow-type: tm+mt
source-wordcount: '2491'
ht-degree: 99%

---


# Comprendre les diffusions en échec{#understanding-delivery-failures}

## A propos des diffusions en échec {#about-delivery-failures}

Lorsqu&#39;un message (email, SMS, notification push) ne peut pas être envoyé à un profil, le serveur distant envoie automatiquement un message d&#39;erreur, qui est relevé par la plateforme Adobe Campaign et qualifié afin de déterminer si l&#39;adresse email ou le numéro de téléphone doit être mis ou non en quarantaine. Voir la section [Qualification des emails bounce](#bounce-mail-management).

>[!NOTE]
>
>Les messages d&#39;erreur de type Email (ou &quot;bounces&quot;) sont qualifiés par le processus inMail. Les messages d&#39;erreur de type SMS (ou &quot;SR&quot; pour &quot;Status Report&quot;) sont qualifiés par le processus MTA.

Une fois un message envoyé, les logs de diffusion permettent de consulter le statut de la diffusion pour chaque profil ainsi que le type d&#39;échec et la raison associés.

Les messages peuvent être également exclus pendant la préparation de la diffusion si une adresse est mise en quarantaine ou si un profil est placé sur liste bloquée. Les messages exclus sont répertoriés dans le tableau de bord de la diffusion.

**Rubriques connexes :**

* [Logs et historique de la diffusion](../../delivery/using/monitoring-a-delivery.md#delivery-logs-and-history)
* [Statut En échec](../../delivery/using/monitoring-a-delivery.md#failed-status)
* [Types de diffusion en échec et raisons](#delivery-failure-types-and-reasons)

## Types de diffusion en échec et raisons      {#delivery-failure-types-and-reasons}

Trois types d&#39;erreurs sont liés à un message en échec. Chaque type d&#39;erreur détermine si une adresse est mise en quarantaine. Voir à ce propos la section [Conditions de mise en quarantaine d&#39;une adresse](../../delivery/using/understanding-quarantine-management.md#conditions-for-sending-an-address-to-quarantine)

* **Hard** : une erreur de type &quot;hard&quot; indique une adresse invalide. Il s’agit d’un message d’erreur indiquant explicitement que l’adresse est invalide, par exemple : &quot;Utilisateur inconnu&quot;.
* **Soft** : il s’agit d’une erreur qui peut être temporaire, ou qui n’a pas pu être qualifiée, par exemple : &quot;Domaine invalide&quot; ou &quot;Boîte pleine&quot;.
* **Ignoré** : il s’agit d’une erreur que l’on sait temporaire, par exemple &quot;Out of office&quot;, ou d’une erreur technique, par exemple si l’expéditeur est de type &quot;postmaster&quot;.

Les motifs possibles d’une diffusion en échec sont les suivants :

<table> 
 <tbody> 
  <tr> 
   <td> Libellé de l'erreur </td> 
   <td> Type d'erreur </td> 
   <td> Valeur technique </td> 
   <td> Description </td> 
  </tr> 
  <tr> 
   <td> Compte désactivé </td> 
   <td> Soft/Hard </td> 
   <td> 4 </td> 
   <td> Le compte associé à l'adresse n'est plus actif. Lorsque le Fournisseur d'Accès Internet (FAI) détecte une inactivité prolongée, il peut fermer le compte de l'utilisateur, ce qui rend les diffusions vers son adresse impossibles. Si le compte est temporairement désactivé en raison d'une inactivité de 6 mois et qu’il peut toujours être activé, le statut En erreur sera affecté. Une tentative d'utilisation du compte est alors effectuée jusqu’à ce que le compteur d'erreurs atteigne 5. Si l'erreur signale que le compte est désactivé de manière permanente, il sera directement défini comme étant en quarantaine.<br /> </td> 
  </tr> 
  <tr> 
   <td> Adresse en quarantaine </td> 
   <td> Hard </td> 
   <td> 9 </td> 
   <td> L'adresse a été mise en quarantaine.<br /> </td> 
  </tr> 
  <tr> 
   <td> Adresse non renseignée </td> 
   <td> Hard </td> 
   <td> 7 </td> 
   <td> L'adresse du destinataire n'est pas renseignée.<br /> </td> 
  </tr> 
  <tr> 
   <td> Adresse de mauvaise qualité </td> 
   <td> Ignoré </td> 
   <td> 14 </td> 
   <td> L'indice de qualité de l'adresse postale est trop faible.<br /> </td> 
  </tr> 
  <tr> 
   <td> Adresse placée sur la liste bloquée </td> 
   <td> Hard </td> 
   <td> 8 </td> 
   <td> L'adresse a été ajoutée à la liste bloquée au moment de l'envoi. Cet état est utilisé pour importer des données à partir de listes externes et de systèmes externes dans la liste Quarantaine d’Adobe Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Adresse témoin </td> 
   <td> Ignoré </td> 
   <td> 127 </td> 
   <td> L'adresse de l'expéditeur fait partie de la population témoin.<br /> </td> 
  </tr> 
  <tr> 
   <td> Double </td> 
   <td> Ignoré </td> 
   <td> 10 </td> 
   <td> L'adresse du destinataire apparaissait déjà dans cette diffusion.<br /> </td> 
  </tr> 
  <tr> 
   <td> Erreur ignorée </td> 
   <td> Ignoré </td> 
   <td> 25 </td> 
   <td> L'adresse est sur la liste autorisée. L’erreur est donc ignorée et un email sera envoyé.<br /> </td> 
  </tr> 
  <tr> 
   <td> Exclu par un arbitrage </td> 
   <td> Ignoré </td> 
   <td> 12 </td> 
   <td> Le destinataire a été exclu par une règle de typologie de campagne de type 'arbitrage'.<br /> </td> 
  </tr> 
  <tr> 
   <td> Exclu par une règle SQL </td> 
   <td> Ignoré </td> 
   <td> 11 </td> 
   <td> Le destinataire a été exclu par une règle de typologie de campagne de type 'SQL'.<br /> </td> 
  </tr> 
  <tr> 
   <td> Domaine invalide </td> 
   <td> Soft </td> 
   <td> 2 </td> 
   <td> Le domaine de l'adresse email est erroné ou n'existe plus. Ce profil sera ciblé de nouveau jusqu'à ce que le nombre d'erreurs atteigne 5. Une fois ce chiffre atteint, l'enregistrement sera défini sur le statut Quarantaine et aucune autre reprise ne sera effectuée.<br /> </td> 
  </tr> 
  <tr> 
   <td> Boîte pleine </td> 
   <td> Soft </td> 
   <td> 5 </td> 
   <td> La boîte de messagerie de l'utilisateur est pleine et ne peut plus accepter d'autres messages. Ce profil sera ciblé de nouveau jusqu'à ce que le nombre d'erreurs atteigne 5. Une fois ce chiffre atteint, l'enregistrement sera défini sur le statut Quarantaine et aucune autre reprise ne sera effectuée.<br /> Ce type d'erreur est géré par un processus de nettoyage, l'adresse est défini sur un statut valide au bout de 30 jours.<br /> Attention : pour que l'adresse soit automatiquement retirée de la liste des adresses en quarantaine, le workflow technique Nettoyage de la base (cleanup) doit être démarré.<br /> </td> 
  </tr> 
  <tr> 
   <td> Non connecté </td> 
   <td> Ignoré </td> 
   <td> 6 </td> 
   <td> Le téléphone portable du destinataire est éteint ou n'est pas connecté au réseau au moment de l'envoi du message.<br /> </td> 
  </tr> 
  <tr> 
   <td> Non définie </td> 
   <td> Non définie </td> 
   <td> 0 </td> 
   <td> L'adresse est en cours de qualification, car les erreurs n'ont pas encore été incrémentées. Ce type d'erreur apparaît lorsqu'un nouveau message d'erreur est envoyé par le serveur : il peut s'agir d'une erreur isolée, mais si elle se répète, le compteur d'erreur augmente, ce qui permet d'alerter les équipes techniques. Celles-ci peuvent ensuite effectuer une analyse du message et qualifier cette erreur à partir du nœud <span class="uicontrol">Administration</span> / <span class="uicontrol">Gestion de campagne</span> / <span class="uicontrol">Gestion des NP@I</span> dans l'arborescence.<br /> </td> 
  </tr> 
  <tr> 
   <td> Non éligible aux offres </td> 
   <td> Ignoré </td> 
   <td> 16 </td> 
   <td> Le destinataire n'était pas éligible aux offres de la diffusion.<br /> </td> 
  </tr> 
  <tr> 
   <td> Refusés </td> 
   <td> Soft/Hard </td> 
   <td> 20 </td> 
   <td> L'adresse a été mise en quarantaine en raison d'un retour de sécurité signalant du spam. Selon l'erreur, l'adresse sera utilisée de nouveau jusqu'à ce que le compteur d'erreur atteigne 5 ou elle sera directement mise en quarantaine.<br /> </td> 
  </tr> 
  <tr> 
   <td> Cible limitée en taille </td> 
   <td> Ignoré </td> 
   <td> 17 </td> 
   <td> La taille de diffusion maximale a été atteinte pour le destinataire.<br /> </td> 
  </tr> 
  <tr> 
   <td> Adresse non qualifiée </td> 
   <td> Ignoré </td> 
   <td> 15 </td> 
   <td> L'adresse postale n'a pas été qualifiée.<br /> </td> 
  </tr> 
  <tr> 
   <td> Inatteignable </td> 
   <td> Soft/Hard </td> 
   <td> 3 </td> 
   <td> Une erreur s'est produite dans la chaîne de distribution du message. Il peut s'agir d'un incident sur le relais SMTP, d'un domaine temporairement inatteignable, etc. Selon l'erreur, l'adresse sera utilisée de nouveau jusqu'à ce que le compteur d'erreur atteigne 5 ou elle sera directement mise en quarantaine.<br /> </td> 
  </tr> 
  <tr> 
   <td> Utilisateur inconnu </td> 
   <td> Hard </td> 
   <td> 1 </td> 
   <td> L'adresse n'existe pas. Aucune autre diffusion ne sera envoyée pour ce profil.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Reprises après une diffusion temporairement en échec      {#retries-after-a-delivery-temporary-failure}

Si un message échoue en raison d&#39;une erreur Soft ou Ignoré qui est temporaire, les reprises seront effectuées pendant la durée de diffusion.********

>[!NOTE]
>
>Les messages temporairement non diffusés peuvent uniquement être associés à une erreur **Soft** ou **Ignoré**, mais pas à une erreur **Hard** (voir la section [Types de diffusion en échec et raisons](#delivery-failure-types-and-reasons)).

Pour modifier la durée d’une diffusion, accédez aux paramètres avancés de la diffusion ou du modèle de diffusion et indiquez la durée souhaitée dans le champ correspondant. Les propriétés avancées des diffusions sont présentées dans [cette section](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period).

La configuration par défaut permet cinq reprises à des intervalles d’une heure chacune, puis une reprise par jour pendant quatre jours. Le nombre de reprises peut être changé de manière globale (contactez l’administrateur technique Adobe) ou pour chaque diffusion ou modèle de diffusion (voir [cette section](../../delivery/using/steps-sending-the-delivery.md#configuring-retries)).

## Erreurs synchrones et asynchrones      {#synchronous-and-asynchronous-errors}

Un message peut échouer immédiatement (erreur synchrone) ou plus tard, après son envoi (erreur asynchrone).

* Erreur synchrone : le serveur de mail distant contacté par le serveur de diffusion Adobe Campaign a retourné immédiatement un message d&#39;erreur ; la diffusion ne peut être envoyée au serveur du profil. Adobe Campaign qualifie chaque échec afin de déterminer si les adresses email concernées doivent être mises en quarantaine ou non. Voir [Qualification des emails bounce](#bounce-mail-qualification).
* Erreur asynchrone : un mail rebond ou un SR a été renvoyé plus tard par le serveur de réception. Ce mail est récupéré dans une boîte email technique relevée par l&#39;application pour marquer les messages en erreur. Les erreurs asynchrones peuvent se produire jusqu&#39;à une semaine après l&#39;envoi d&#39;une diffusion.

   >[!NOTE]
   >
   >Le paramétrage de la boîte des mails rebonds est décrit dans [cette section](../../installation/using/deploying-an-instance.md#managing-bounced-emails).

   La [feedback loop](../../delivery/using/technical-recommendations.md#feedback-loop) fonctionne comme les emails de bounce. Lorsqu’un utilisateur qualifie un email de spam, vous pouvez configurer des règles d’email dans Adobe Campaign pour bloquer toutes les diffusions à cet utilisateur. Les messages envoyés à des utilisateurs qui ont qualifié un email comme spam sont automatiquement redirigés vers une boîte de réception spécialement créée à cet effet. Les adresses de ces utilisateurs figurent sur la liste bloquée même s&#39;ils n&#39;ont pas cliqué sur le lien de désinscription. Les adresses figurent sur la liste bloquée de la table des quarantaines (**NmsAddress**) et non de la table des destinataires (**NmsRecipient**).

   >[!NOTE]
   >
   >La gestion des plaintes est décrite dans la section [Gestion de la délivrabilité](../../delivery/using/about-deliverability.md).

## Gestion des emails bounce {#bounce-mail-management}

La plateforme Adobe Campaign permet de gérer les échecs d&#39;envoi d&#39;email via la fonctionnalité des mails rebonds. Lorsqu&#39;un email ne peut pas être délivré à son destinataire, le serveur de messagerie distant renvoie automatiquement un message d&#39;erreur (mail rebond) vers une boîte email technique réservée à cet usage. Les messages d&#39;erreur sont relevés par la plateforme Adobe Campaign et qualifiés par le processus inMail afin d&#39;enrichir la liste des règles de gestion des emails.

### Qualification des emails bounce      {#bounce-mail-qualification}

Lorsque l&#39;envoi d&#39;un email échoue, le serveur de diffusion Adobe Campaign reçoit un message d&#39;erreur de la part du serveur de messagerie ou du serveur DNS distant. La liste des erreurs est constituée à partir des chaînes contenues dans le message renvoyé par le serveur distant. A chaque message d&#39;erreur sont attribués un type et une raison d&#39;échec.

Cette liste est disponible depuis le nœud **[!UICONTROL Administration > Gestion de campagne > Gestion des NP@I > Qualification des logs de diffusion]**. Il contient toutes les règles utilisées par Adobe Campaign pour qualifier les erreurs de diffusion. Cette liste est non exhaustive et est régulièrement mise à jour par Adobe Campaign. Elle peut également être gérée par l&#39;utilisateur.

![](assets/tech_quarant_rules_qualif.png)

* Le message renvoyé par le serveur distant à la première occurrence de ce type d&#39;erreur est affiché dans la colonne **[!UICONTROL Premier texte]** de la table **[!UICONTROL Qualification des logs de diffusion]**. Si cette colonne n&#39;est pas visible, cliquez sur le bouton **[!UICONTROL Configurer la liste]** en bas à droite de la liste pour la sélectionner.

![](assets/tech_quarant_rules_qualif_text.png)

Adobe Campaign filtre ce message pour supprimer le contenu de la variable (identifiants, dates, adresses email, numéros de téléphone, etc.) et affiche le résultat filtré dans la colonne **[!UICONTROL Texte]**. Les variables sont remplacées par **`#xxx#`**, à l&#39;exception des adresses remplacées par **`*`**.

Ce processus permet de regrouper tous les échecs d&#39;un même type et d&#39;éviter plusieurs entrées pour des erreurs similaires dans la table Qualification des logs de diffusion.

>[!NOTE]
>
>Le champ **[!UICONTROL Nombre d&#39;occurrences]** affiche le nombre d&#39;occurrences du message dans la liste. Ce nombre est limité à 100 000 occurrences. Vous pouvez modifier le champ si vous le souhaitez, par exemple pour le réinitialiser.

Les statuts de qualification des mails rebonds sont les suivants :

* **[!UICONTROL A qualifier]** : le mail rebond n&#39;a pas pu être qualifié. La qualification doit être confiée à l&#39;équipe Délivrabilité afin de garantir le bon fonctionnement de la délivrabilité de la plateforme. Tant qu&#39;il n&#39;est pas qualifié, le mail rebond n&#39;est pas utilisé pour compléter la liste des règles de gestion des emails.
* **[!UICONTROL Conserver]** : le mail rebond a été qualifié et sera utilisé par le workflow **Mise à jour pour la délivrabilité** pour être comparé aux règles de gestion des emails existantes et en enrichir la liste.
* **[!UICONTROL Ignorer]** : le mail rebond est ignoré par le MTA de Campaign, ce qui signifie que ce rebond ne provoquera jamais la mise en quarantaine de l’adresse du destinataire. Il ne sera pas utilisé par le workflow **Mise à jour pour la délivrabilité** et il ne sera pas envoyé aux instances clientes.

![](assets/deliverability_qualif_status.png)

>[!IMPORTANT]
>
>Pour les installations hébergées ou hybrides, si vous avez effectué la mise à niveau vers le MTA amélioré :
>
>* Les qualifications de rebond dans la table **[!UICONTROL Qualification des logs de diffusion]** ne sont plus utilisées pour les messages d’erreur relatifs aux échecs des diffusions synchrones. Le MTA amélioré détermine le type et la qualification de rebond, puis renvoie ces informations à Campaign.
   >
   >
* Les rebonds asynchrones restent qualifiés par le processus inMail grâce aux règles de **[!UICONTROL mail entrant]**. Voir à ce propos la section [Règles de gestion des emails](#email-management-rules).
   >
   >
* Pour les instances qui utilisent le MTA amélioré sans **WebHooks/EFS**, les règles de **[!UICONTROL mail entrant]** sont également utilisées pour traiter les mails rebonds synchrones provenant du MTA amélioré, avec la même adresse email que pour les mails rebonds asynchrones.
>
>
Pour plus d’informations sur le MTA amélioré d’Adobe Campaign, consultez ce [document](https://helpx.adobe.com/fr/campaign/kb/acc-campaign-enhanced-mta.html).

### Règles de gestion des emails {#email-management-rules}

Les règles mail sont accessibles depuis le nœud **[!UICONTROL Administration > Gestion de campagne > Gestion des NP@I > Jeux de règles mail]**. Vous pouvez consulter les règles de gestion des emails dans la section inférieure de la fenêtre.

![](assets/tech_quarant_rules.png)

>[!NOTE]
>
>Les paramètres par défaut de la plateforme sont configurés dans l&#39;assistant de déploiement. Pour plus d&#39;information, reportez-vous à [cette section](../../installation/using/deploying-an-instance.md).

Les règles par défaut sont les suivantes.

>[!IMPORTANT]
>
>* Le serveur de diffusion (MTA) doit être relancé si les paramètres sont modifiés.
>* La modification ou la création de règles de gestion est réservée à des utilisateurs experts.


#### Mail entrant {#inbound-email}

Ces règles contiennent la liste des chaînes de caractères qui peuvent être renvoyées par les serveurs distants et qui permettent de qualifier l&#39;erreur en **Hard**, **Soft** ou **Ignoré**.

Lors de l’échec d’un envoi d’email, le serveur de messagerie distant renvoie un message d’erreur rebond à l’adresse spécifiée dans les paramètres de la plateforme. Adobe Campaign compare le contenu de chaque mail rebond aux chaînes disponibles dans la liste des règles puis attribue l’un des trois [types d’erreurs](#delivery-failure-types-and-reasons).

>[!NOTE]
>
>L’utilisateur peut créer ses propres règles. Lors d’un import de package et lors de la mise à jour des données par le workflow **Mise à jour pour la délivrabilité**, les règles mail créées par l’utilisateur sont écrasées.

Pour plus d’informations sur la qualification des mails rebonds, consultez [cette section](#bounce-mail-qualification).

>[!IMPORTANT]
>
>Pour les installations hébergées ou hybrides, si vous avez effectué la mise à niveau vers le MTA amélioré et si votre instance dispose de la fonctionnalité **Webhooks/EFS**, les règles de **[!UICONTROL mail entrant]** ne sont plus utilisées pour les messages d’erreur relatifs aux échecs des diffusions synchrones. Voir à ce propos [cette section](#bounce-mail-qualification).
>
>Pour plus d’informations sur le MTA amélioré d’Adobe Campaign, consultez ce [document](https://helpx.adobe.com/fr/campaign/kb/acc-campaign-enhanced-mta.html).

#### Gestion des domaines {#domain-management}

Le serveur de messagerie d’Adobe Campaign applique une règle unique de **gestion des domaines** à tous les domaines.

<!--![](assets/tech_quarant_domain_rules_02.png)-->

* Vous pouvez choisir d’activer ou non certaines normes d’identification et clés de cryptage pour vérifier le nom de domaine, comme **Sender ID**, **DomainKeys**, **DKIM**, **S/MIME**.
* Les paramètres de **Relais SMTP** permettent de configurer l’adresse IP et le port d’un serveur relais pour un domaine particulier. Voir à ce propos [cette section](../../installation/using/configuring-campaign-server.md#smtp-relay).

Si vos messages sont affichés dans Outlook avec la mention **[!UICONTROL Au nom de]** dans l’adresse de l’expéditeur, veillez à ne pas signer vos emails avec le **Sender ID** qui est la norme d’authentification de messagerie exclusive de Microsoft, devenue obsolète. Si l’option **[!UICONTROL Sender ID]** est activée, décochez la case correspondante et contactez l’assistance d’Adobe Campaign. Il n’y aura aucune incidence sur la délivrabilité.

>[!IMPORTANT]
>
>Pour les installations hébergées ou hybrides, si vous avez effectué la mise à niveau vers le MTA amélioré, les règles de **[!UICONTROL gestion des domaines]** ne sont plus utilisées. La signature d’authentification des emails **DKIM (DomainKeys Identified Mail)** est effectuée par le MTA amélioré pour tous les messages et tous les domaines. La signature n’utilise ni **Sender ID**, ni **DomainKeys** ou **S/MIME**, sauf indication contraire du MTA amélioré.
>
>Pour plus d’informations sur le MTA amélioré d’Adobe Campaign, consultez ce [document](https://helpx.adobe.com/fr/campaign/kb/acc-campaign-enhanced-mta.html).

#### Gestion des MX {#mx-management}

* Les règles de gestion MX permettent de réguler le flux des emails sortants pour un domaine spécifique. Elles consistent à faire un échantillonnage des messages qui reviennent en erreur et de bloquer les envois, le cas échéant.

* Le serveur de messagerie d’Adobe Campaign applique les règles spécifiques aux domaines, puis celles du cas général, symbolisé par un astérisque dans la liste des règles.

* Pour configurer des règles de gestion MX, il suffit de fixer un seuil et de sélectionner certains paramètres SMTP. Le **seuil** est une limite calculée en pourcentage d’erreur au-delà de laquelle tout message vers un domaine spécifique est bloqué. Par exemple, dans le cas général, pour un minimum de 300 messages, l’envoi des emails est bloqué pendant 3 heures si le taux d’erreur atteint 90 %.

Pour plus d&#39;informations sur la gestion des MX, consultez [cette section](../../installation/using/email-deliverability.md#mx-configuration).

>[!IMPORTANT]
>
>Pour les installations hébergées ou hybrides, si vous avez effectué la mise à niveau vers le MTA amélioré, les règles de débit de diffusion avec **[!UICONTROL Gestion des MX]** ne sont plus utilisées. Le MTA amélioré utilise ses propres règles MX. Il peut ainsi personnaliser le débit par domaine en fonction de votre réputation, basée sur l&#39;historique des emails et les commentaires en temps réel provenant des domaines auxquels vous adressez des emails.
>
>Pour plus d’informations sur le MTA amélioré d’Adobe Campaign, consultez ce [document](https://helpx.adobe.com/fr/campaign/kb/acc-campaign-enhanced-mta.html).
