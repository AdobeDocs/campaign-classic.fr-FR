---
title: Déploiement d'une instance
seo-title: Déploiement d'une instance
description: Déploiement d'une instance
seo-description: null
page-status-flag: never-activated
uuid: 5694b07a-6c1c-45a3-8a22-fd9da163c28c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: initial-configuration
discoiquuid: 71fc8bfc-40e0-4592-a540-bd6807ded3a0
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Déploiement d&#39;une instance{#deploying-an-instance}

>[!NOTE]
>
>Les paramétrages côté serveur ne peuvent être réalisés que par Adobe pour les déploiements hébergés par Adobe. Pour plus d&#39;informations sur les différents déploiements, reportez-vous à la section [Modèles d&#39;hébergement](../../installation/using/hosting-models.md) ou à [cet article](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html).

## L&#39;assistant de déploiement {#deployment-wizard}

Un assistant graphique accessible à partir de la console cliente Adobe Campaign permet de renseigner les paramètres de l&#39;instance sur laquelle vous allez vous connecter.

Pour démarrer l&#39;assistant de déploiement, sélectionnez **Outils > Avancé > Assistant de déploiement**.

![](assets/s_ncs_install_deployment_wiz_01.png)

Les étapes de paramétrage sont les suivantes :

1. [Paramètres généraux](#general-parameters)
1. [Paramètres du canal email](#email-channel-parameters)
1. [Gestion des mails rebonds](#managing-bounced-emails)
1. [Paramétrage du tracking](#tracking-configuration)
1. [Paramètres du canal mobile](#mobile-channel-parameters)
1. [Options régionales](#regional-settings)
1. [Accès depuis Internet](#access-from-the-internet)
1. [Gestion des ressources publiques](#managing-public-resources)
1. [Purge des données](#purging-data)

## Paramètres généraux {#general-parameters}

La première étape de l&#39;assistant de déploiement permet de renseigner les informations générales relatives à l&#39;instance.

![](assets/s_ncs_install_deployment_wiz_02.png)

### Informations générales {#general-information}

La section inférieure de la fenêtre permet de sélectionner les options à activer.

* **[!UICONTROL Identifiant client pour la facturation]** : il peut s&#39;agir par exemple du nom de l&#39;instance et du numéro de version.
* **[!UICONTROL Nom usuel du client]** : saisissez le nom de votre société. Cette information est notamment utilisée notamment dans les liens de désabonnement.
* **[!UICONTROL Espace de nommage]** : saisissez ici un identifiant court, en minuscules. L&#39;objectif consiste à distinguer votre configuration spécifique de la configuration d&#39;usine en cas de mise à jour. L&#39;espace de nommage par défaut est **cus** - pour customer (client).

### Options techniques {#technical-options}

La section inférieure de la fenêtre permet de sélectionner les options à activer.

Les options disponibles sont les suivantes :

* **[!UICONTROL Canal]** de courriel : pour activer la remise des e-mails. Reportez-vous aux paramètres [de canal de](#email-channel-parameters)courriel.
* **[!UICONTROL Suivi]** : Pour activer le suivi de la population cible (ouvre et clique). Reportez-vous à la configuration [du](#tracking-configuration)suivi.
* **[!UICONTROL Gestion des courriels]** rebondés : Pour définir le compte POP utilisé pour récupérer le courrier électronique entrant. Reportez-vous à [Gestion des courriers électroniques](#managing-bounced-emails)rebondis.
* **[!UICONTROL Intégration]** LDAP : Pour configurer l’authentification des utilisateurs via un annuaire LDAP. Reportez-vous à [Connexion via LDAP](../../installation/using/connecting-through-ldap.md).

## Paramètres du canal email {#email-channel-parameters}

L&#39;étape suivante permet de définir les informations qui seront affichées dans l&#39;en-tête des emails.

Ces paramètres peuvent être surchargés dans les modèles de diffusion et, unitairement au niveau de chaque diffusion (sous réserve que les utilisateurs possèdent les droits appropriés).

### Paramètres des emails envoyés {#parameters-for-delivered-emails}

![](assets/s_ncs_install_deployment_wiz_04.png)

Indiquez les paramètres suivants :

* **[!UICONTROL Nom expéditeur]** : le nom de l&#39;expéditeur,
* **[!UICONTROL Adresse expéditeur]** : l&#39;adresse email de l&#39;expéditeur,
* **[!UICONTROL Nom de l&#39;adresse de réponse]** : le nom, personnalisable, qui sera utilisé lorsque le destinataire clique sur le bouton **[!UICONTROL Répondre]** de son logiciel de messagerie,
* **[!UICONTROL Adresse de réponse]** : l&#39;adresse email à utiliser lorsque le destinataire clique sur le bouton **[!UICONTROL Répondre]** de son logiciel de messagerie,
* **[!UICONTROL Adresse d&#39;erreur]** : l&#39;adresse email des messages en erreur. Il s&#39;agit d&#39;une adresse technique utilisée pour gérer les rebonds, notamment les emails reçus par le serveur Adobe Campaign si les adresses ciblés n&#39;existent pas.

En complément, vous pouvez indiquer les **masques** autorisés pour l&#39;adresse expéditeur et l&#39;adresse d&#39;erreur. Au besoin, ces masques doivent être séparés les uns des autres par une virgule. Ce paramétrage est facultatif. Lorsque ces champs sont renseignés, Adobe Campaign contrôle, au moment de l&#39;envoi (ou au moment de l&#39;analyse, lorsque l&#39;adresse ne contient pas d&#39;éléments variables), que les adresses renseignées dans la diffusion sont valables. Ce fonctionnement permet d&#39;éviter l&#39;utilisation d&#39;adresses qui pourraient poser des problème de délivrabilité. Les adresses d&#39;expédition doivent être configurées sur le serveur d&#39;envoi.

### Caractères autorisés dans les adresses {#characters-authorized-in-addresses}

<!--This window enables you to define, for all email campaigns, the delivery and address-quality management options.-->

Dans la base Adobe Campaign, toute adresse email doit être composée comme suit : `x@y.z`. Les caractères **x**, **y** et **z** ne doivent pas être vides, ni contenir des caractères non autorisés.

Vous pouvez ici définir la liste des caractères autorisés (&#39;data policy&#39;) dans le champ email de la base de données. Les caractères absents de la liste seront interdits, et donc refusés lors d&#39;une saisie dans la base, mais aussi lors d&#39;un import ou à la validation d&#39;un formulaire Web.

Deux listes sont proposées : **Européens uniquement** ou **US uniquement**. Elles peuvent être complétées par d&#39;autres caractères, au besoin.

### Paramètres de la diffusion {#delivery-parameters}

Le lien **Paramètres avancés...** permet d&#39;accéder aux options de diffusion, aux paramètres liés aux reprises et aux mises en quarantaines.

![](assets/s_ncs_install_deployment_wiz_05.png)

Cette fenêtre permet de définir, pour toutes les campagnes email, les options de diffusion et de gestion de la qualité des adresses.

Les options disponibles sont les suivantes :

* **[!UICONTROL Durée de diffusion des messages]** : durée maximum au-delà de laquelle la diffusion des messages est arrêtée (par défaut, 5 jours),
* **[!UICONTROL Durée de validité des ressources en ligne]** : durée pendant laquelle seront conservées toutes les informations relatives au profil du destinataire afin de générer les pages miroir,
* **[!UICONTROL Exclure les destinataires qui ne souhaitent plus être contactés]** : lorsque cette option est sélectionnée, la diffusion ne sera pas effectuée sur les destinataires en blackliste,
* **[!UICONTROL Supprimer automatiquement les doublons]** : lorsque cette option est sélectionnée, la diffusion ne sera pas effectuée sur les adresses emails en doublon.

### Paramètres de reprise {#retry-parameters}

Les informations relatives aux reprises sont indiquées dans les champs **Période des reprises** et **Nombre de reprises** : lorsqu&#39;un destinataire est inatteignable, par exemple si sa boîte mail est pleine, le programme réessayera par défaut de le contacter 5 fois, espacées d&#39;au moins une heure (pendant la durée maximum de diffusion des messages). Ces valeurs peuvent être adaptées selon vos besoins.

### Paramètres de mise en quarantaine {#quarantine-parameters}

Les options de configuration pour les mises en quarantaines sont les suivantes :

* **[!UICONTROL Durée entre deux erreurs significatives]** : saisissez une valeur (par défaut &quot;1j&quot; : 1 jour) pour définir le temps d&#39;attente de l&#39;application avant d&#39;incrémenter le compteur d&#39;erreurs lors d&#39;un échec,
* **[!UICONTROL Nombre maximum d&#39;erreurs avant mise en quarantaine]** : une fois atteinte la valeur renseignée ici, l&#39;email est passé en quarantaine (par défaut &quot;5&quot; : l&#39;adresse sera mise en quarantaine à la sixième erreur). Cela signifie que ce contact sera automatiquement exclu des prochaines diffusions.

## Gestion des mails rebonds {#managing-bounced-emails}

Les mails rebonds sont essentiels pour qualifier les erreurs suite à une diffusion. Ces erreurs seront réparties dans les NP@I une fois que les règles auront déterminé la cause de non aboutissement du message.

This step is only available if the **Email channel** and **Bounce mail** management options are selected in the first stage of the deployment wizard. Reportez-vous aux paramètres [](#general-parameters)généraux.

Dans cette étape, vous pouvez définir les paramètres de gestion des mails rebonds.

![](assets/s_ncs_install_deployment_wiz_06.png)

### Compte POP de relevé des mails entrants {#pop-account-used-to-retrieve-incoming-mails}

Indiquez les paramètres de connexion au compte de relevé des mails entrants.

* **[!UICONTROL Libellé]** : nom regroupant les paramètres ci-dessous,
* **[!UICONTROL Serveur]** : serveur utilisé pour relever les mails rebonds (emails entrants),
* **[!UICONTROL Sécurité]** : au besoin, sélectionnez la valeur **[!UICONTROL SSL]** dans la liste déroulante,
* **[!UICONTROL Port]** : port du serveur (en général 110),
* **[!UICONTROL Compte]** : nom du compte dédié aux rebonds,
* **[!UICONTROL Mot de passe]** : mot de passe associé au compte.

Une fois les paramètres POP renseignés, cliquez sur **Test** afin de vérifier que ces paramètres sont corrects.

### Mails rebonds non traités {#unprocessed-bounce-mails}

Les mails rebonds sont traités de façon automatique par Adobe Campaign, en appliquant les règles répertoriées dans le nœud **Administration > Gestion de campagne > Gestion des NP@I > Qualification des logs de diffusion**. Voir à ce sujet [Gestion des mails rebonds](../../delivery/using/understanding-delivery-failures.md#bounce-mail-management).

Les mails rebonds non traités ne sont pas affichés dans l’interface Adobe Campaign. Ils sont supprimés automatiquement à moins qu’ils ne soient transférés à une boîte de tierce partie au moyen des champs suivants :

* **[!UICONTROL Adresse de transfert]** : remplissez ce champ pour transférer vers une adresse tierce tous les messages d’erreurs (traitées ou non) collectés par la plate-forme Adobe Campaign.
* **[!UICONTROL Adresse pour les erreurs]** : remplissez ce champ pour transférer vers une adresse tierce uniquement les messages d’erreurs que le processus inMail n’a pas été en mesure de qualifier.
* **[!UICONTROL Serveur SMTP]** : serveur utilisé pour envoyer les mails rebonds non traités.

>[!CAUTION]
>
>Pour transférer les mails rebonds non traités, Adobe vous recommande de remplir seulement le champ **[!UICONTROL Adresse pour les erreurs]**. Veillez cependant à ce que l’adresse utilisée soit vérifiée régulièrement, car cela pourrait induire une charge importante sur votre serveur de messagerie. Contactez votre chargé de compte pour plus d’informations.

## Paramétrage du tracking {#tracking-configuration}

Dans l&#39;étape suivante, procédez à la configuration du tracking pour l&#39;instance. L&#39;instance doit être déclarée et enregistrée auprès du ou des serveurs de tracking.

This step is only offered when the **Email channel** and **Tracking** options are selected in the first page of the deployment wizard. Reportez-vous aux paramètres [](#general-parameters)généraux.

La configuration du tracking web (mode de tracking, création et insertion des balises...) est détaillée dans [ce document](../../configuration/using/about-web-tracking.md).

### Principe de fonctionnement {#operating-principle}

Lorsque vous activez le tracking sur une instance, les URL présentes dans les diffusions sont transformées lors de l&#39;envoi afin de permettre d&#39;en assurer le suivi.

* Les informations concernant les URL externes (sécurisées ou non) saisies dans cette étape de l&#39;assistant de déploiement sont utilisées pour construire la nouvelle URL. En plus de ces informations, le lien ainsi transformé contient : l&#39;identifiant de la diffusion, l&#39;identifiant du destinataire et l&#39;identifiant de l&#39;URL.

   Les informations de tracking sont collectées par Adobe Campaign sur le ou les serveurs de tracking afin d&#39;alimenter le profil des destinataires ainsi que les données liées à la diffusion (onglets **[!UICONTROL Tracking]**).

   Les informations concernant les URL internes ne sont utilisées que par le serveur applicatif Adobe Campaign afin de contacter le ou les serveurs de tracking.

   For more on this, refer to [Tracking server](#tracking-server).

* Une fois les URL configurées, il est nécessaire d&#39;activer le tracking. Pour cela, l&#39;instance doit être enregistrée auprès du ou des serveurs de tracking.

   For more on this, refer to [Saving tracking](#saving-tracking).

### Serveur de tracking {#tracking-server}

![](assets/s_ncs_install_deployment_wiz_08.png)

Pour permettre le bon fonctionnement du tracking sur cette instance, les informations suivantes doivent être paramétrées :
<!--With Mid-sourcing architecture, you can externalize tracking management. To do this:-->

* **[!UICONTROL URL externe]** et/ou **[!UICONTROL URL externe sécurisée]** : saisir l&#39;URL de redirection à utiliser dans les emails à envoyer.
* **[!UICONTROL URL interne(s)]** : URL utilisée(s) uniquement par le serveur Adobe Campaign afin de contacter le(s) serveur(s) de tracking pour la collecte des logs et le téléchargement des URL. Il n&#39;est pas nécessaire de l&#39;associer à l&#39;instance.

   Si vous ne renseignez pas d&#39;URL, par défaut l&#39;URL de tracking sera utilisée.

Dans le cadre d&#39;une architecture en Mid-Sourcing, vous pouvez externaliser la gestion du tracking. Pour cela :

1. Sélectionnez l&#39;option **[!UICONTROL Externaliser la gestion du tracking]** : vous pourrez ainsi utiliser un serveur de mid-sourcing comme serveur de tracking.
1. Renseignez les champs **[!UICONTROL Compte externe]** et **[!UICONTROL Nom de l&#39;instance]** pour pouvoir vous connecter au serveur de mid-sourcing.

   Pour plus d’informations, reportez-vous à la section Serveur [de sources](../../installation/using/mid-sourcing-server.md)intermédiaires.

1. Cliquez sur le bouton **[!UICONTROL Activer l&#39;instance de tracking]** pour valider la connexion au serveur.

   ![](assets/s_ncs_install_deployment_wiz_18.png)

### Enregistrement du tracking {#saving-tracking}

Une fois les URL renseignées, vous devez procéder à l&#39;enregistrement du serveur de tracking.

Cliquez sur le lien **Enregistrement auprès du ou des serveurs de tracking** et sélectionnez une des options proposées.

![](assets/s_ncs_install_deployment_wiz_09.png)

Trois types d&#39;architecture sont possibles pour la mise en place du tracking :

1. **Ajouter le tracking à une instance déjà existante**

   Ce choix s&#39;applique dans le cas où une instance a déjà été créée pour d&#39;autres besoins (serveur de diffusion, etc.) sur le ou les serveurs qui serviront de serveurs de tracking.

   ![](assets/s_ncs_install_deployment_wiz_11.png)

   Saisissez le mot de passe du compte **internal** du ou des serveurs de redirection, afin de pouvoir configurer l&#39;instance de tracking.

   >[!NOTE]
   >
   >Si plusieurs serveurs de tracking sont paramétrés, leurs nom et mot de passe doivent être les mêmes.

   Renseigner le nom de l&#39;instance et son mot de passe.

1. **Créer une nouvelle instance dédiée au tracking**

   Cette option est adaptée dans le cas où les instances de tracking sont réservées au tracking et ne comportent aucun autre module applicatif.

   ![](assets/s_ncs_install_deployment_wiz_10.png)

   Saisissez le mot de passe du compte **internal** du ou des serveurs de redirection, afin de pouvoir configurer l&#39;instance de tracking.

   >[!NOTE]
   >
   >Si plusieurs serveurs de tracking sont paramétrés, ils doivent tous utiliser le même mot de passe.

   Renseignez le nom de l&#39;instance et son mot de passe ainsi que les masques DNS qui lui sont associés, par exemple **[!UICONTROL Campaign*]**.

1. **Valider une instance de tracking préconfigurée pour vous**

   Cette option est utilisée lorsque vous ne disposez pas du mot de passe du compte **internal** ; dans ce cas, un compte de tracking a été préconfiguré pour vous sur le ou les serveurs de redirection. Entrez le mot de passe du compte de tracking du ou des serveurs de redirection, afin de pouvoir valider l&#39;instance de tracking.

   ![](assets/s_ncs_install_deployment_wiz_17.png)

   Renseignez le nom de l&#39;instance à valider et son mot de passe.

Cliquez sur **Valider** pour lancer la procédure d&#39;enregistrement auprès des serveurs de tracking.

De retour à la fenêtre précédente, un message confirme l&#39;enregistrement auprès du serveur de tracking :

![](assets/s_ncs_install_deployment_wiz_tracking_ok.png)

Dans un contexte standard d&#39;installation, les paramètres relatifs à la recherche des URL **ne doivent pas être modifiés**. Pour tout autre cas, contactez Adobe.

## Paramètres du canal mobile {#mobile-channel-parameters}

L&#39;étape suivante permet de définir les paramètres par défaut lors des diffusions vers les mobiles (SMS et WAP Push).

>[!NOTE]
>
>Le canal mobile est une option : l&#39;étape suivante n&#39;apparaît que si elle a été acquise. Consultez votre contrat de licence.

![](assets/s_ncs_install_deployment_wiz_12.png)

### Compte par défaut pour le routage des SMS {#default-account-for-sms-delivery}

Renseignez les informations suivantes :

* **[!UICONTROL Libellé]** : indiquez un nom pour ce compte SMS/ Wap Push. Il peut contenir par exemple le nom de votre prestataire.
* Pour les champs **[!UICONTROL Serveur]**, **[!UICONTROL Port]**, **[!UICONTROL Compte]**, **[!UICONTROL Mot de passe]**, **[!UICONTROL Connecteur]**, **[!UICONTROL Endpoint envoi]**, **[!UICONTROL Endpoint rcp]**, **[!UICONTROL Endpoint notif]**, contactez votre prestataire afin d&#39;obtenir les paramètres nécessaires.

### Paramètres des SMS envoyés {#parameters-of-sms-sent}

Dans la liste déroulante **Priorité**, sélectionnez la valeur &quot;normale&quot;, &quot;haute&quot; ou &quot;urgente&quot; afin de l&#39;appliquer aux messages qui seront diffusés.

### Paramètres avancés {#advanced-parameters}

Le lien **Paramètres avancés...** permet d&#39;accéder aux options de reprise et de mise en quarantaines.

![](assets/s_ncs_install_deployment_wiz_13.png)

Les informations relatives aux reprises sont indiquées dans les champs **Période des reprises** et **Nombre de reprises** : lorsqu&#39;un mobile est inatteignable, le programme réessayera par défaut de le contacter 5 fois, espacées d&#39;au moins 15 minutes (pendant la durée maximum de diffusion des messages). Ces valeurs peuvent être adaptées selon vos besoins.

Les options de configuration pour les mises en quarantaines sont les suivantes :

* **[!UICONTROL Durée entre deux erreurs significatives]** : saisissez une valeur (par défaut &quot;1j&quot; : 1 jour) pour définir le temps d&#39;attente de l&#39;application avant d&#39;incrémenter le compteur d&#39;erreurs lors d&#39;un échec.
* **[!UICONTROL Nombre maximum d&#39;erreurs avant mise en quarantaine]** : une fois atteinte la valeur renseignée ici, le numéro de mobile est passé en quarantaine (par défaut &quot;5&quot; : le numéro sera mis en quarantaine à la sixième erreur). Cela signifie que ce contact sera automatiquement exclu des prochaines diffusions.

## Options régionales {#regional-settings}

Cette étape permet d&#39;indiquer des préférences relatives aux contraintes sur les données (data policy).

![](assets/s_ncs_install_deployment_wiz_14.png)

* **[!UICONTROL Interpréter les numéros comme internationaux]** : si cette option est sélectionnée, l&#39;application appliquera le format international aux numéros de téléphone (le préfixe du pays est alors obligatoire car le nombre de chiffres ne sera pas vérifié avant d&#39;appliquer le formatage). Si cette case n&#39;est pas cochée, vous devez préfixer vous-même le numéro de téléphone international avec &quot;+&quot; ou &quot;00&quot;.
* **[!UICONTROL Stocker tous les numéros au format international]** : cette option ne concerne que les numéros de téléphone **français** importés ou édités. On définit ici si l&#39;on préfère utiliser un format de numéro à 10 chiffres (ex : 01 41 98 35 35) ou un format international (ex : +33 1 41 98 35 35)

## Accès depuis Internet {#access-from-the-internet}

>[!CAUTION]
>
>Pour des raisons de confidentialité, nous vous recommandons d&#39;utiliser HTTPS pour toutes les ressources externes.

Cette étape permet de définir les URL d&#39;accès aux pages Adobe Campaign exposées sur Internet.

Vous devez également y indiquer les options de publication liées aux formulaires Web.

![](assets/s_ncs_install_deployment_wiz_15.png)

### Serveurs exposés sur le Web {#servers-exposed-on-the-web}

Renseignez dans cette page les URL des serveurs pour :

1. Accéder au serveur applicatif exposé sur Internet : formulaires d&#39;inscription / de désinscription, extranet, etc.
1. Accéder au serveur applicatif pour les ressources non exposées sur le Web : formulaires, intranet, pages de validation.
1. Accéder aux pages miroir renseignées des diffusions.

   Une page miroir est une page dynamique qui affiche le contenu de l&#39;email. Elle est accessible via un lien inséré dans le message adressé au destinataire et peut contenir des éléments de personnalisation, s&#39;ils ont été définis. La page miroir permet au destinataire de lire correctement l&#39;email dans son navigateur Internet plutôt que dans son outil de messagerie, quel que soit son format de réception (texte ou HTML). Toutefois, pour chaque action de diffusion, les pages miroir ne sont générées que si un contenu HTML a été défini.

Adobe Campaign offre la possibilité de différencier ces trois URL afin de mieux répartir la charge sur plusieurs plateformes.

## Gestion des ressources publiques {#managing-public-resources}

>[!CAUTION]
>
>Pour des raisons de confidentialité, nous vous recommandons d&#39;utiliser HTTPS pour toutes les ressources externes.

Pour être visibles depuis l&#39;extérieur, les images utilisées dans les emails et les ressources publiques associées aux opérations doivent être présentes sur un serveur accessible de l&#39;extérieur. Elles pourront ainsi être disponibles pour les destinataires ou les opérateurs externes.

![](assets/s_ncs_install_deployment_wiz_img_uploading.png)

Dans cette étape, vous devez renseigner :

1. Nouvelle URL de ressource publique. Pour plus d’informations, consultez la section URL [des ressources](#public-resources-url) publiques.
1. Mode de détection des images dans une diffusion. Pour plus d’informations, reportez-vous à la section Détection [des images de](#delivery-image-detection) diffusion.
1. Options de publication. For more information, refer to the [Publication modes](#publication-modes) section.

Les ressources publiques sont accessibles à partir du noeud **Administration > Ressources > On-line > Ressources publiques** de l&#39;arborescence Adobe Campaign. Elles sont regroupées dans une bibliothèque et peuvent être incluses dans les emails mais aussi utilisées au niveau des opérations ou des tâches, ainsi que pour la gestion de contenu.

![](assets/install_pub_resources_view.png)

### URL des ressources publiques {#public-resources-url}

Le premier champ permet de saisir le début de l&#39;URL des ressources lorsqu&#39;elles sont mises en ligne. Les ressources sont alors accessibles via cette nouvelle URL.

Dans une diffusion, vous pouvez utiliser des images stockées dans la bibliothèque de ressources publiques ou toute autre image locale ou stockée sur un serveur.

* Pour les images des emails, l&#39;URL **https://** serveur **/res/img**.

   Cette valeur peut être surchargée au niveau de chaque diffusion.

* Pour les ressources publiques, l’URL **https://** serveur **/res/** instance ****où&#x200B;**instance**est le nom de l’instance de tracking.

### Détection des images d&#39;une diffusion {#delivery-image-detection}

Dans une diffusion, vous pouvez utiliser des images stockées dans la bibliothèque de ressources publiques ou toute autre image locale ou stockée sur un serveur.

Le champ **Masques des URL** permet d&#39;indiquer la liste des masques des URL qui seront ignorées lors de la mise en ligne automatique des images. Par exemple, si vous utilisez des images qui sont stockées sur un site accessible depuis l&#39;extérieur, notamment sur votre site internet, vous pouvez saisir dans ce champ l&#39;URL d&#39;accès au site.

![](assets/s_ncs_install_deployment_wiz_img_mask.png)

Vous pouvez saisir plusieurs masques, séparés les uns des autres par une virgule.

* Le mode d&#39;utilisation et la gestion des images dans les emails sont présentés dans [cette section](../../delivery/using/defining-the-email-content.md#adding-images).
* Dans l&#39;assistant de diffusion, les images appelées depuis ces URL auront le statut &quot;Ignoré&quot;.

### Modes de publication {#publication-modes}

La section inférieure de l&#39;assistant permet de sélectionner les options de publication des ressources publiques et des images. Ces options sont également disponibles pour les formulaires web et les questionnaires.

Les modes de publication suivants sont disponibles :

* Serveur(s) de tracking

   Les ressources seront automatiquement copiées sur les différents serveurs de suivi. Ils sont configurés dans l’étape Configuration [du](#tracking-configuration)suivi.

* Autre(s) serveur(s) Adobe Campaign

   Vous pouvez utiliser un ou plusieurs autres serveurs Adobe Campaign où seront copiées les ressources.

   Côté serveur, pour utiliser un serveur Adobe Campaign dédié, vous devez créer une nouvelle instance avec la commande suivante :

   ```
   nlserver config -addtrackinginstance:<trackingA>/<trackingA*>
   ```

   Puis saisissez le mot de passe.

   Les paramètres du ou des serveurs dédiés sont indiqués dans les champs **[!UICONTROL URL médias]**, **[!UICONTROL Nom de l&#39;instance]** et **[!UICONTROL Mot de passe]**.

   ![](assets/s_ncs_install_images_upload_b.png)

* Script de publication manuelle (seulement pour les ressources publiques)

   ![](assets/s_ncs_install_images_upload_c.png)

   Vous pouvez publier les ressources via un script :

   * Vous devez créer ce script : son contenu dépend de votre configuration.
   * Le script sera appelé via la commande suivante :

      ```
      [INSTALL]/copyToFrontal.vbs "$(XTK_INSTALL_DIR)\var\<instance>\upload\" "img1,img2,img3"
      ```

      where `[INSTALL]` is the access path to the Adobe Campaign installation folder.

   * Sous Unix, assurez-vous que ce script soit exécutable.

Pour les images, il doit les copier depuis le dossier &quot;images&quot; renseigné via l&#39;option **NmsDelivery_ImageSubDirectory** vers un ou plusieurs serveurs frontaux. Ces serveurs vont stocker les images afin de les rendre accessibles via la nouvelle URL configurée.

In the event of publication on an Adobe Campaign server without a manual publication script, by default, the images of a delivery are stored in the `$(XTK_INSTALL_DIR)/var/res/img/ directory`. The corresponding URL is the following: **`https://server/res/img`**.

`XTK_INSTALL_DIR)/var/res/$(INSTANCE_NAME)`. The corresponding URL is as follows: **`https://server/res/instance`** where instance is the name of the tracking instance.

>[!NOTE]
>
>Il est possible de modifier le répertoire de stockage des ressources publiques. Pour plus d’informations à ce sujet, reportez-vous à [Gestion des ressources](#managing-public-resources)publiques.

### Synchronisation des ressources publiques {#synchronizing-public-resources}

Cette fonctionnalité permet de **synchroniser des ressources publiques** sur plusieurs spare-serveurs.

Si une ressource publique n&#39;est pas présente sur le serveur de tracking ou si la ressource renvoie une erreur 404, le serveur de tracking va essayer de trouver la ressource sur un des spare-serveurs.

Vous devez déclarer et configurer les spare-serveurs dans le fichier **serverConf.xml** du serveur Marketing. Tous les paramètres disponibles dans **serverConf.xml** sont répertoriés dans cette [section](../../installation/using/the-server-configuration-file.md).

**Déclaration**

```
<redirection>
<spareServer enabledIf="" id="" url=""/>
</redirection>
```

**Configuration**

For each public resource that has to be synchronized, you have to add a status attribute to the `<url>` element in the `<relay>` part:

L&#39;attribut status peut prendre trois valeurs :

* spare : la ressource publique est synchronisée

* normal : comportement existant (sans synchronisation)

* blacklist : l&#39;url est blacklistée si elle renvoie une erreur 404. La durée (en secondes) du blacklistage est définie par un attribut **timeout** dont la valeur par défaut est de 60s.

La configuration d&#39;usine de la synchronisation est :

```
(extracted from the serverConf.xml file)

<redirection P3PCompactPolicy="CAO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV"
databaseId="" defLogCount="30" expirationURL="" maxJobsInCache="100"
startRedirection="true" startRedirectionInModule="true" trackWebVisitors="false" trackingPassword="">
<spareServer enabledIf="" id="1" url=""/>
</redirection>

....


<relay debugRelay="false" forbiddenCharsInAuthority="?#.@/:" forbiddenCharsInPath="?#/"
           modDir="index.html" startRelay="false" startRelayInModule="true" timeout="60">
   <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="normal" targetUrl="https://localhost:8080" timeout="" urlPath="/view/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="*.jsp"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="*.jssp"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="/webApp/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="/report/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="/jssp/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="normal" targetUrl="https://localhost:8080" timeout="" urlPath="/strings/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="normal" targetUrl="https://localhost:8080" timeout="" urlPath="/interaction/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="normal" targetUrl="https://localhost:8080" timeout="" urlPath="/barcode/*"/>

      <url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" status="spare" targetUrl="" timeout="" urlPath="/favicon.*"/>
      <url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" status="spare" targetUrl="" timeout="" urlPath="/*.html"/>
      <url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" status="spare" targetUrl="" timeout="" urlPath="/*.png"/>
      <url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" status="spare" targetUrl="" timeout="" urlPath="/*.jpg"/>

 </relay>
```

## Purge des données {#purging-data}

La dernière étape de l&#39;assistant de déploiement permet de paramétrer la purge automatique des données obsolètes de la base. Les valeurs sont exprimées en jours.

![](assets/s_ncs_install_deployment_wiz_16.png)

Data is deleted automatically via the Database cleanup workflow. For more on how to configure and operate this workflow and details on the deleted items, refer to this [document](../../production/using/database-cleanup-workflow.md).
