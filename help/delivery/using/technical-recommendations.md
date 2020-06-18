---
title: Recommandations techniques pour améliorer la délivrabilité avec Adobe Campaign Classic
description: Découvrez les techniques, les configurations et les outils que vous pouvez utiliser pour améliorer votre taux de délivrabilité avec Adobe Campaign Classic.
page-status-flag: never-activated
uuid: 71be1087-e5ff-4a7a-85ca-36803839e72f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: fc95538b-b54d-44ec-81aa-f51b62982699
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 537cbdec1ec88da1c759f6ca8eafe383c55a61d3
workflow-type: tm+mt
source-wordcount: '2467'
ht-degree: 91%

---


# Recommandations techniques{#technical-recommendations}

Un certain nombre de techniques, paramétrages et outils pour améliorer votre taux de délivrabilité sont présentés ci-dessous.

## Configuration {#configuration}

### Reverse DNS {#reverse-dns}

Adobe Campaign vérifie qu’un reverse DNS est bien renseigné pour une adresse IP et que celui-ci reboucle bien sur l’IP.

Un point indispensable de la configuration réseau est d&#39;avoir établi un reverse DNS correct pour chacune des adresses IP d&#39;envoi. Cela signifie que pour une adresse IP donnée, il existe un enregistrement reverse DNS (enregistrement PTR) dont la correspondance DNS (enregistrement A) reboucle sur l&#39;adresse IP initiale.

Le choix du domaine pour un reverse DNS a une incidence lorsque vous traitez avec certains FAI. AOL, en particulier, n’accepte que les feedback loops dont l’adresse appartient au même domaine que le reverse DNS (voir la section [Feedback loop](#feedback-loop)).

Un outil est proposé pour vérifier la configuration d’un domaine : [https://mxtoolbox.com/SuperTool.aspx](https://mxtoolbox.com/SuperTool.aspx).

### Règles MX {#mx-rules}

Les règles MX (Mail eXchanger) correspondent aux règles de gestion de communication entre un serveur expéditeur et un serveur destinataire.

Plus précisément, elles servent à contrôler la vitesse d’envoi des emails par le MTA (Message Transfer Agent) de Campaign à chaque domaine d’email ou de FAI (par exemple, hotmail.com, comcast.net). Ces règles sont généralement basées sur les limites publiées par les FAI (par exemple, ne pas inclure plus de 20 messages par connexion SMTP).

Pour plus d&#39;informations sur la gestion des MX, consultez [cette section](../../installation/using/email-deliverability.md#mx-configuration).

### TLS {#tls}


(Transport Layer Security) est un protocole de cryptage qui peut être utilisé pour sécuriser la connexion entre deux serveurs de messagerie et empêcher la lecture du contenu d’un email par une autre personne que le destinataire prévu.

## Authentification {#authentication}

### SPF {#spf}

SPF (Sender Policy Framework) est une norme d’authentification d’email qui permet au propriétaire d’un domaine de spécifier les serveurs de messagerie autorisés à envoyer des emails pour le compte de ce domaine. Cette norme utilise le domaine indiqué dans l’en-tête « Return-Path » de l’email (également appelé adresse « Envelope From »).

Un outil est proposé pour vérifier la configuration d’un enregistrement SPF : [https://www.kitterman.com/spf/validate.html](https://www.kitterman.com/spf/validate.html)

La technique SPF permet, dans une certaine mesure, de vous assurer que le nom de domaine utilisé dans un email n’est pas usurpé. Lorsqu’un message provient d’un domaine, le serveur DNS du domaine est interrogé. Il répond par un enregistrement court (enregistrement SPF) détaillant les serveurs autorisés à envoyer des emails depuis ce domaine. Si nous supposons que seul le propriétaire du domaine a les moyens de modifier cet enregistrement, nous pouvons considérer que cette technique ne permet pas de falsifier l’adresse de l’expéditeur, du moins pas la partie située à droite du « @ ».

Dans la [spécification RFC 4408](https://www.rfc-editor.org/info/rfc4408) finale, deux éléments du message sont utilisés pour déterminer le domaine considéré comme l’expéditeur : le domaine spécifié par la commande SMTP &quot;HELO&quot; (ou &quot;EHLO&quot;) et le domaine spécifié par l’adresse de l’en-tête &quot;Return-Path&quot; (ou &quot;MAIL FROM&quot;), qui est également l’adresse des rebonds. Différentes considérations permettent de ne prendre en compte que l’une de ces valeurs ; nous vous recommandons de vous assurer que les deux sources spécifient le même domaine.

La vérification SPF produit une évaluation de la validité du domaine expéditeur :

* **None** : aucune évaluation n’a pu être faite,
* **Neutral** : le domaine interrogé ne permet pas l’évaluation,
* **Pass** : le domaine est considéré comme authentique,
* **Fail** : le domaine est certainement usurpé, le message devrait être rejeté,
* **SoftFail** : le domaine est probablement usurpé, mais le message ne doit pas être rejeté pour autant,
* **TempError** : une erreur temporaire a interrompu l’évaluation. Le message peut être rejeté,
* **PermError** : les enregistrements SPF du domaine sont incorrects.

Il faut bien noter que les modifications des enregistrements au niveau des serveurs DNS peuvent mettre jusqu&#39;à 48 heures pour être prises en compte. Ce délai est en fonction de la fréquence de rafraîchissement des caches DNS des serveurs de réception.

### DKIM {#dkim}

L’authentification DKIM (DomainKeys Identified Mail) est un successeur de SPF. Elle utilise la cryptographie à clé publique qui permet au serveur de messagerie de réception de vérifier qu’un message a bien été envoyé par la personne ou l’entité revendiquant l’envoi et si le contenu du message a été modifié ou non entre le moment où il a été envoyé (et « signé » par DKIM) et celui où il a été reçu. Cette norme utilise généralement le domaine dans l’en-tête « From » ou « Sender ». Pour assurer le niveau de sécurité du DKIM, la valeur 1024b est la taille de cryptage recommandée selon les bonnes pratiques. Les clés DKIM inférieures ne seront pas considérées comme valides par la majorité des fournisseurs d’accès.

DKIM est né de l&#39;union des principes d&#39;authentification DomainKeys, de Yahoo! et Identified Internet Mail, de Cisco et va permettre de vérifier l&#39;authenticité du domaine expéditeur et garantir l&#39;intégrité du message.

DKIM a remplacé l&#39;authentification **DomainKeys**.

L&#39;utilisation de DKIM nécessite quelques prérequis :

* **Sécurité** : le cryptage est un élément clé de DKIM. La taille minimum de cryptage recommandée est 1024b. Des tailles inférieures ne seront pas considérées comme valides pour la plupart des fournisseurs d&#39;accès.
* **Réputation** : la réputation est basée sur l&#39;IP et/ou le domaine mais le sélecteur DKIM est aussi un élément à prendre en compte. Le choix d&#39;un sélecteur est important : évitez de garder celui par défaut car il peut être utilisé par n&#39;importe qui. Sa réputation est donc très faible. Vous devez implémenter un sélecteur différent pour les communications **retention vs acquisition** et pour l&#39;authentification.
* **Déclaration d&#39;option dans Adobe Campaign** : dans Adobe Campaign, la clé privée DKIM est basée sur un sélecteur DKIM et un domaine. Actuellement il n&#39;est pas possible de créer de multiples clés privées pour le même domaine ou sous-domaine, avec des sélecteurs différents. Dans l&#39;instance ou dans l&#39;email, il n&#39;est pas possible de définir quel sélecteur doit être utilisé pour l&#39;authentification. L&#39;instance choisit alternativement une des clés privées : le risque d&#39;échec lors de l&#39;authentification est élevé.

>[!NOTE]
>
>* Si vous avez configuré DomainKeys pour votre instance Adobe Campaign, vous devez simplement sélectionner **dkim** dans les [règles de gestion des domaines](../../delivery/using/understanding-delivery-failures.md#domain-management). Dans le cas contraire, suivez les mêmes étapes de configuration (clé privée/clé publique) que pour DomainKeys.
>* Il est inutile d&#39;activer DomainKeys et DKIM pour un même domaine, DKIM étant une version améliorée de DomainKeys.
>* Les domaines validant actuellement DKIM sont les suivants : AOL, Gmail.


>[!IMPORTANT]
>
>Pour les installations hébergées ou hybrides, si vous avez effectué une mise à niveau vers le [MTA amélioré](https://helpx.adobe.com/campaign/kb/acc-campaign-enhanced-mta.html), la signature de l’authentification des emails DKIM est effectuée par celui-ci pour tous les messages et domaines.

### DMARC {#dmarc}

DMARC (Domain-based Message Authentication, Reporting and Conformance) est la forme la plus récente d’authentification des emails. Le processus s’appuie simultanément sur l’authentification SPF et DKIM pour déterminer si un email sera diffusé avec succès ou non. DMARC est sans équivalent et puissant pour deux raisons très importantes :

* Conformité : il permet à l’expéditeur de donner aux FAI des instructions sur les actions à exécuter sur les messages qui ne parviennent pas à s’authentifier (par exemple, ne pas l’accepter).
* Reporting : il fournit à l’expéditeur un rapport détaillé indiquant tous les messages ayant échoué lors de l’authentification DMARC, ainsi que le domaine &quot;From&quot; et l’adresse IP utilisée pour chacun. Une entreprise peut ainsi identifier un email légitime qui ne réussit pas l’authentification et qui a besoin d’une correction (par exemple, ajouter des adresses IP à son enregistrement SPF), ainsi que les sources et la prévalence des tentatives de phishing sur ses domaines de messagerie.

DMARC peut utiliser les rapports générés par [250ok](https://250ok.com/).

<!--#### Configuring the application {#configuring-the-application}

To define the domain used for the HELO command, edit the instance's configuration file (conf/config-instance.xml) and define a "localDomain" attribute as follows:

```
<serverConf>
  <shared>
    <dnsConfig localDomain="mydomain.net"/>
  </shared>
</serverConf>
```

The MAIL FROM domain is the domain used in technical bounce messages. This address is defined in the deployment wizard or via the NmsEmail_DefaultErrorAddr option.

#### DNS configuration {#dns-configuration}

An SPF record can currently be defined on a DNS server as a TXT type record (code 16) or an SPF type record (code 99). An SPF record takes the form of a character string. For example:

```
v=spf1 ip4:12.34.56.78/32 ip4:12.34.56.79/32 ~all
```

defines the 2 IP addresses 12.34.56.78 and 12.34.56.79 as authorized to send emails for the domain. **~all** means that any other address should be interpreted as a SoftFail.

Recommendations for defining an SPF record:

* Add **~all** (SoftFail) or **-all** (Fail) at the end to reject all servers other than those defined. Without this, servers will be able to forge this domain (with a Neutral evaluation).
* Do not add **ptr** (openspf.org recommends against this as costly and unreliable).-->

## Feedback loop {#feedback-loop}

Une boucle de rétroaction fonctionne en déclarant au niveau du fournisseur de services Internet une adresse électronique donnée pour une plage d’adresses IP utilisées pour l’envoi de messages. Le FAI enverra à cette boîte aux lettres, de la même manière que pour les messages de rebond, ces messages qui sont signalés par les destinataires comme étant du spam. La plateforme doit être configurée pour bloquer les futures diffusions aux utilisateurs qui se sont plaints. Il est important de ne plus les contacter même s’ils n’ont pas utilisé le lien d’exclusion approprié. C&#39;est sur la base de ces plaintes qu&#39;un FAI ajoutera une adresse IP à sa liste bloquée. Selon le fournisseur de services Internet, un taux de plainte d&#39;environ 1 % entraînera le blocage d&#39;une adresse IP.

Un standard est en cours d’établissement pour définir le format des messages de feedback loop : l’[ARF (Abuse Feedback Reporting Format)](https://tools.ietf.org/html/rfc6650).

La mise en place d&#39;une feedback loop pour une instance suppose d&#39;avoir :

* une boîte mail dédiée à l&#39;instance, qui peut éventuellement être la boîte de mails rebonds,
* des adresses IP d&#39;envoi dédiées à l&#39;instance.

La mise en œuvre d’une feedback loop simple dans Adobe Campaign fait appel à la fonctionnalité de messages rebonds. La boîte email de feedback loop est utilisée comme boîte de rebond et une règle est définie pour détecter ces messages. Les adresses email des destinataires qui ont signalé le message comme indésirable seront ajoutées à la liste des adresses en quarantaine.

* Créez ou adaptez une règle de mails rebonds **Feedback_loop** dans **[!UICONTROL Administration>Gestion de campagne>Gestion des NP@I>Jeux de règles mail]** avec la raison **Refusé** et le type **Hard**.
* Si une boîte a été définie spécialement pour la feedback loop, définissez les paramètres pour relever son contenu en créant un nouveau compte externe de type Mails rebonds dans **[!UICONTROL Administration>Plate-forme>Comptes externes]**.

Le mécanisme est immédiatement opérationnel pour traiter les notifications de plaintes. Pour vérifier le bon fonctionnement de la règle, vous pouvez temporairement désactiver les comptes afin qu&#39;ils ne relèvent pas ces messages, puis vérifier le contenu de la boîte de feedback loop manuellement. Sur le serveur, exécutez les commandes suivantes :

```
nlserver stop inMail@instance,
nlserver inMail -instance:instance -verbose.
```

Si vous êtes contraint d&#39;utiliser une seule adresse de feedback loop pour plusieurs instances, il faudra :

* répliquer les messages reçus sur autant de boîtes qu&#39;il existe d&#39;instances,
* faire relever chaque boîte par une seule instance,
* Configurez les instances pour qu’elles ne traitent que les messages qui les concernent : les informations d’instance se trouvent dans l’en-tête Message-ID des messages envoyés par Adobe Campaign et figurent donc également dans les messages de feedback loop. Il vous suffit de spécifier le paramètre **checkInstanceName** dans le fichier de configuration de l’instance (par défaut, l’instance n’est pas vérifiée, ce qui peut entraîner une mise en quarantaine abusive de certaines adresses) :

   ```
   <serverConf>
     <inMail checkInstanceName="true"/>
   </serverConf>
   ```

Le service Délivrabilité d&#39;Adobe Campaign gère votre inscription aux services de feedback loop pour les FAI suivants : AOL, BlueTie, Comcast, Cox, EarthLink, FastMail, Gmail, Hotmail, HostedEmail, Libero, Mail.ru, MailTrust, OpenSRS, QQ, RoadRunner, Synacor, Telenor, Terra, UnitedOnline, USA, XS4ALL, Yahoo, Yandex, Zoho.

## List-Unsubscribe {#list-unsubscribe}

### A propos de List-Unsubscribe {#about-list-unsubscribe}

L&#39;ajout d&#39;un en-tête SMTP appelé **List-Unsubscribe** est obligatoire pour une gestion optimale de la délivrabilité.

Cet en-tête pourra être utilisé comme une alternative à l&#39;icône &quot;Signaler comme SPAM&quot;. Il s&#39;affichera comme un lien de désinscription dans l&#39;interface mail.

L&#39;utilisation de cette fonctionnalité protège votre réputation et le feedback sera exécuté comme une désinscription.

>[!NOTE]
>
>Cette fonctionnalité est disponible à partir du build 6831.

Pour utiliser List-Unsubscribe, vous devez entrer une ligne de commande similaire à celle-ci :

```
List-Unsubscribe: mailto: client@newsletter.example.com?subject=unsubscribe?body=unsubscribe
```

>[!IMPORTANT]
>
>L&#39;exemple ci-dessus est basé sur la table des destinataires. Si l&#39;implémentation de la base de données est faite à partir d&#39;une autre table, pensez à reformuler la ligne de commande avec l&#39;information correcte.

La ligne de commande suivante peut-être utilisée pour créer un **List-Unsubscribe** dynamique :

```
List-Unsubscribe: mailto: %=errorAddress%?subject=unsubscribe%=message.mimeMessageId%
```

Gmail, Outlook.com et Microsoft Outlook supportent cette méthode. Ils afficheront un lien de désinscription directement dans leur interface. Cette technique favorise la diminution du taux de plaintes.

![](assets/s_tn_del_msn_unsubscribe_list.png)

![](assets/s_tn_del_gmail_unsubscribe_list.png)

Vous pouvez implémenter le **List-Unsubscribe** en :

* ajoutant directement la ligne de commande dans le modèle de diffusion - voir [cette section](#adding-a-command-line-in-a-delivery-template), ou
* créant une règle de typologie - voir [cette section](#creating-a-typology-rule).

### Ajouter la ligne de commande dans le modèle de diffusion {#adding-a-command-line-in-a-delivery-template}

La ligne de commande doit être ajoutée dans la section additionnelle de l&#39;en-tête SMTP de l&#39;email.

Cet ajout peut se faire dans chaque email, ou dans les modèles de diffusion existants. Vous pouvez aussi créer un nouveau modèle de diffusion qui inclue cette fonctionnalité.

### Créer une règle de typologie {#creating-a-typology-rule}

La règle de typologie doit contenir le script qui génère la ligne de commande et être inclue dans l&#39;en-tête de l&#39;email.

>[!NOTE]
>
>La création d&#39;une règle de typologie est recommandée : la fonctionnalité List-Unsubscribe sera automatiquement ajoutée à chaque email.

1. List-Unsubscribe: &lt;mailto:unsubscribe@domain.com>

   Un clic sur le lien **unsubscribe** ouvre le client messagerie par défaut de l&#39;utilisateur. Cette règle de typologie doit être ajoutée dans une typologie utilisée pour la création d&#39;email.

1. List-Unsubscribe: `<https://domain.com/unsubscribe.jsp>`

   Un clic sur le lien **unsubscribe** redirige l&#39;utilisateur vers votre formulaire de désinscription.

   Exemple:

   ![](assets/s_tn_del_unsubscribe_param.png)

## Optimisation des emails {#email-optimization}

### SMTP {#smtp}

SMTP (Simple mail transfer protocol) est une norme Internet pour la transmission des emails.

Les erreurs SMTP qui ne sont vérifiées par aucune règle sont recensées dans le dossier **[!UICONTROL Administration]** > **[!UICONTROL Gestion de campagne]** > **[!UICONTROL Gestion des NP@I]** > **[!UICONTROL Qualification des logs de diffusion]**. Ces messages d’erreurs sont interprétés par défaut comme des erreurs soft inatteignables. Les erreurs les plus nombreuses doivent être identifiées et une règle leur correspondant doit être ajoutée dans **[!UICONTROL Administration]** > **[!UICONTROL Gestion de campagne]** > **[!UICONTROL Gestion des NP@I]** > **[!UICONTROL Jeux de règles mail]** si on souhaite qualifier correctement les retours de serveurs SMTP. Sans cela, la plateforme serait amenée à faire des essais d’envoi inutiles (cas d’utilisateurs inconnus) ou de mettre abusivement en quarantaine certains destinataires après le nombre d’essais prévus.

### Adresses IP dédiées {#dedicated-ips}

Adobe fournit une stratégie IP dédiée pour chaque client avec une adresse IP en phase de montée (ramp-up) afin d&#39;établir une réputation et optimiser les performances de diffusion.

## Certification IP {#ip-certification}

La certification IP est un programme de bonnes pratiques d&#39;envoi qui permet de s&#39;assurer que les courriels sont reçus sans être bloqués par des filtres antispam ou d&#39;autres systèmes de blocage des courriels.

Actuellement, deux fournisseurs proposent une certification IP : Return Path et Certified Senders Alliance.

Les expéditeurs certifiés sont ajoutés aux listes autorisées de messagerie électronique utilisées par les fournisseurs de boîtes aux lettres globaux et les sociétés de sécurité des courriels. Ces listes autorisées commerciales sont basées sur un système qui permet à l&#39;expéditeur de contourner complètement les filtres antispam ou de se voir attribuer des points incrémentiels lorsqu&#39;ils entrent dans le système.

Le programme [Return Path Certification](https://www.validity.com/products/returnpath/certification/) offre un certain nombre d’avantages, notamment :

* une augmentation mesurable du placement en boîte de réception pour les principaux fournisseurs de messagerie tels que Microsoft, AOL, Yahoo, Gmail, Comcast, Orange, Mail.ru, etc. ;
* une réputation et un traitement favorables des filtres critiques tels que Cloudmark, SpamAssassin et Cisco Ironport ;
* une équipe de conformité dédiée à la surveillance 24h/24 et 7j/7, qui émet des alertes de sécurité et collabore avec vous pour résoudre tout problème éventuel ;
* des données relatives aux fournisseurs de messagerie donnant des informations détaillées sur les indicateurs de performances clés (IPC), le placement en boîte de réception et les performances de certification ;
* un processus de rodage des adresses IP simplifié et plus rapide, notamment une meilleure réputation et une reconnaissance plus performante en cas de migration ou d’obtention d’une nouvelle adresse IP.

La certification [Certified Senders Alliance](https://certified-senders.org/certification-process/) offre entre autres avantages :

* la certification des expéditeurs d’emails commerciaux pouvant se conformer à des normes de qualité élevée ;
* l’amélioration de la diffusion et de la délivrabilité des emails commerciaux pour augmenter le taux de placement en boîte de réception et réduire le filtrage anti-spam ;
* une protection contre les risques juridiques et financiers en respectant entièrement les normes juridiques ;
* la protection de la réputation grâce à des avertissements précoces émis par le Bureau des réclamations de la Certified Senders Alliance et des rapports quotidiens relatifs aux pièges anti-spam.

Les FAI sont libres d&#39;utiliser ces services et le nombre de FAI peut varier selon la liste autorisée.

Toutefois, étant donné que les FAI sont de plus en plus nombreux à créer leurs filtres anti-spam en fonction du comportement de chaque titulaire de boîte de réception plutôt que du contenu des messages, l’utilisation de la certification IP ne garantit pas nécessairement le placement en boîte de réception, ni même la diffusion.
