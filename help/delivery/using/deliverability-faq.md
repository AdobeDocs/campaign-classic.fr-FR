---
title: Points clés de la gestion de la délivrabilité dans Adobe Campaign Classic
description: Quels sont les points clés à vérifier lors de la gestion de la délivrabilité dans Adobe Campaign Classic ?
page-status-flag: never-activated
uuid: 2681042b-3018-42ae-b252-2367b56616bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 6a394eeb-fbe1-4712-bb13-db5d7965fb73
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 15581517df8d2f397285bbadebd83b7f4539dfd7
workflow-type: tm+mt
source-wordcount: '1338'
ht-degree: 43%

---


# Dépannage de la délivrabilité{#deliverability-faq}

Vous rencontrez un problème de délivrabilité ? La solution se trouve peut-être ici.

## Erreur de règle MX {#mx-rule-error}

**A quoi correspond le message d&#39;erreur &quot;Quota atteint&quot; ?**

Ce message signifie que vous avez atteint le seuil limite pour un MX spécifique et que vous devez attendre pour pouvoir envoyer un autre email au FAI.

Dans Adobe Campaign, il existe une configuration à propos du nombre d&#39;emails pouvant être envoyé par heure. Ce quota doit être utilisé avec précaution car le nombre défini dans l&#39;instance se rapporte au nombre de connexions réalisées avec le FAI et non le nombre de messages réellement envoyés.

Une connexion peut donc utiliser une règle MX sans réussir l&#39;envoi d&#39;un email. Dans ce cas, une configuration avec une IP ou un nom de domaine à faible réputation devra tenter plusieurs connexions avant de réussir l&#39;envoi d&#39;un email. Pour chaque tentative un crédit Messages par heure sera utilisé. La performance de la campagne marketing sera fortement réduite.

Par conséquent, les &quot;quotas satisfaits&quot; ne sont pas seulement une question de configuration, mais peuvent aussi être liés à la réputation. It is important to analyze error messages in the [SMTP log](../../production/using/monitoring-processes.md#smtp-errors-per-domain).

For more on MX configuration, see [this section](../../installation/using/email-deliverability.md#mx-configuration).

## Même message d&#39;erreur pour un fournisseur de services Internet {#same-error-for-an-isp}

**Pourquoi ai-je toujours le même message d&#39;erreur pour un FAI particulier ?**

Si vous recevez toujours le même message d&#39;erreur pour un FAI, il se peut que vous rencontriez des problèmes de réputation liés à votre adresse IP ou votre adresse d&#39;expéditeur. Appliquez les recommandations suivantes :
* Vérifiez si vous recevez un fort pourcentage d&#39;échecs liés à des adresses email inexistantes (échecs de type **Utilisateur inconnu**)
* Mettez à jour vos formulaires d&#39;abonnement pour détecter d&#39;éventuelles erreurs sur la saisie des noms de domaine (par exemple, gmaul.com ou yaho.com)
* Si vous constatez des erreurs indiquant que vos messages sont déclarés en spam, ou que vos messages sont constamment bloqués, essayez d&#39;exclure de la cible les destinataires qui n&#39;ont pas ouvert ou cliqué dans l&#39;un de vos messages dans les 12 mois précédents.

Si le problème persiste, contactez les services commerciaux ou de délivrabilité, le service à la clientèle Adobe Campaign ou le service d’assistance Adobe Campaign.

## Liste noire ou quarantaine {#blacklisting-versus-quarantine}

* **Quelle est la différence entre une adresse email blacklistée et en quarantaine ?**

   * Le statut **[!UICONTROL En blackliste]** signifie que l&#39;un de vos destinataires a déclaré un message comme étant un spam.

   * L&#39;application du statut **[!UICONTROL Quarantaine]** est entraînée par un échec soft ou hard.
   Voir à ce propos [cette section](../../delivery/using/understanding-quarantine-management.md#quarantine-vs-blacklisting).

* **A quoi correspondent les différentes raisons de mise en quarantaine ?**

   Il existent dix raisons de mise en quarantaine : non définie, utilisateur inconnu, domaine invalide, adresse en blackliste, refusé, erreur ignorée, inatteignable, compte désactivé, boîte pleine, non connecté.

   Pour plus d’informations, voir [Comprendre la gestion des quarantaines](../../delivery/using/understanding-quarantine-management.md).

## Annulation de la liste noire {#unblacklisting}

* **Un de mes destinataires est passé par erreur en statut &quot;En blackliste&quot;. Que puis-je faire lui envoyer à nouveau des emails ?**

   * Sélectionnez **[!UICONTROL Administration > Gestion de campagne > Gestion des NP@I > NP@I et Adresses]**.
   * Dans l&#39;écran de détails de l&#39;enregistrement correspondant, changez la valeur du champ **[!UICONTROL Statut]** à **[!UICONTROL Valide]**.
   * Sauvegardez l&#39;enregistrement.

* **Comment puis-je savoir si l&#39;une de mes IP est backlistée ? Comment débloquer mon ou mes IP ?**

   Pour vérifier si votre adresse IP est blacklistée, vous pouvez consulter l&#39;un des sites web ci-dessous :
   * [https://mxtoolbox.com/](https://mxtoolbox.com/)
   * [https://whatismyipaddress.com/blacklist-check](https://whatismyipaddress.com/blacklist-check)
   * [https://www.blacklistalert.org/](https://www.blacklistalert.org/)
   En général, la vérification d&#39;adresse IP renvoie une liste contenant les détails du blacklistage et le nom du site web qui a blacklisté l&#39;adresse IP.

   En cliquant sur le lien correspondant, vous pouvez accéder aux détails du site Web. Vous pouvez ensuite demander que votre adresse IP soit supprimée du site web qui l&#39;a blacklistée.

   >[!NOTE]
   >
   >Le processus peut varier selon le site web. Certains sites requièrent la création d&#39;un compte alors que d&#39;autres demandent uniquement que vous fournissiez l&#39;adresse IP.

## Bonnes pratiques {#best-practices}

Vous trouverez ci-dessous quelques bonnes pratiques qui peuvent aider à cerner et à résoudre les problèmes de délivrabilité.

### Identifier un problème de délivrabilité {#identify-deliverability-issue}

Les éléments suivants peuvent attirer votre attention :

* Mesures de publipostage ou de campagne : les taux de désabonnement, de plaintes pour abus et/ou de rebonds sont plus élevés que d&#39;habitude.
* activité d&#39;abonné : s’ouvre, les clics et/ou les transactions sont inférieurs à la normale.
* Les comptes de démarrage indiquent des envois filtrés ou non livrés.

### Hypothèses des causes potentielles {#potential-causes}

Posez-vous les questions suivantes pour identifier les causes possibles de votre problème de délivrabilité :

* Y a-t-il eu récemment un changement dans la segmentation des listes ?
* Ai-je acquis de nouvelles sources de données ?
* Ai-je envoyé par inadvertance un fichier de quarantaine ?
* Le problème pourrait-il être dû au contenu de mon message ?
* Est-ce que je envoie un courrier assez souvent pour conserver les adresses IP chaudes ?
* Suis-je en train de segmenter mes envois par activité/engagement, ou d&#39;envoyer des fichiers complets ?
* Quel est le segment &quot;sûr&quot; de mon dossier en termes de récence ?
* Des stratégies de réactivation et de reconfirmation sont-elles en place pour les segments qui ne sont pas définis comme sûrs ?

### Résoudre le problème {#address-issue}

**Plaintes (Complaints)**

Les plaintes sont définies par les abonnés qui **signalent un courriel comme indésirable** en appuyant sur le bouton correspondant de leur boîte de réception.

Si votre problème de diffusion est dû à des plaintes :
* Vous devez essayer de déterminer pourquoi les destinataires se plaignent.
* Vous pouvez également envisager de déplacer votre lien de désabonnement en haut de votre courriel. Cela encouragera les abonnés à se désabonner au lieu de se plaindre avec le bouton spam.

Les expéditeurs peuvent recueillir une mine d&#39;informations à partir de leurs plaintes en boucle [de](../../delivery/using/technical-recommendations.md#feedback-loop) rétroaction :
* Il est important de regrouper les données et de rechercher des schémas dans des choses comme la source d&#39;inclusion, la durée d&#39;inscription de l&#39;adresse, ou même certains comportements démographiques.
* Les plaintes peuvent souvent identifier une source ou un segment de données à risque dans le dossier. Le risque est défini comme le plus susceptible de se plaindre, ce qui peut nuire à la réputation, et en retour, les taux de boîte de réception.

Les plaintes proviennent aussi des abonnés qui ne veulent tout simplement plus recevoir de courrier électronique :
* Cela peut souvent être dû à des messages excessifs, à la perception qu&#39;ont vos abonnés du message, au fait qu&#39;ils n&#39;attendaient pas le message ou qu&#39;ils ne se souviennent pas avoir choisi.
* Il est également important d’exécuter une vérification pour s’assurer que tous les points de collecte sont clairs et qu’il n’y a pas de cases pré-cochées dans vos points d’acquisition.
* Vous devez également envoyer un courriel de bienvenue aux abonnés qui s&#39;abonnent pour donner le ton et expliquer à quelle fréquence ils peuvent s&#39;attendre à recevoir des courriels de votre part.

**Validité des données**

**Des rebonds** durs se produisent lorsque vous envoyez à une adresse **** non livrable à un fournisseur de services Internet. Une adresse peut être non livrable pour de nombreuses raisons, telles que :
* Adresse mal orthographiée. Il est possible de résoudre ce problème avec un service de validation des données en temps réel ou en exigeant une inclusion confirmée avant d’envoyer des courriers électroniques marketing à cette adresse.
* liste ou source de données incorrecte. S&#39;il provient d&#39;une nouvelle source, vérifiez comment les adresses ont été collectées et assurez-vous qu&#39;il y a eu autorisation.
* Envoi par courrier à une adresse qui était à un moment active, mais qui a été fermée ou arrêtée après une période d&#39;inactivité.

**Engagement**

Outre les plaintes et la validité des données, les FSI se concentrent plus que jamais sur un engagement **** positif pour prendre des décisions diffusions. Ils cherchent à savoir si vos abonnés ouvrent vos courriels ou les effacent sans les lire. Etant donné qu’ils ne partagent pas ces données avec les expéditeurs, nous devons utiliser les informations disponibles et traduire les ouvertures/clics/transactions en tant qu’engagement.

Dans le cadre du maintien permanent de la réputation, il est important de comprendre comment les abonnés engagés se trouvent sur votre liste et d&#39;établir une hiérarchie **des risques de** récence pour les abonnés de chaque dossier. La récence est définie comme la dernière date d&#39;ouverture/de clic/de transaction ou d&#39;inscription. Cette période peut différer selon la verticale. Pour cela :

1. Déterminez les segments actifs (&quot;sûrs&quot;) pour chaque verticale. Il s’agit généralement des abonnés qui ont été actifs au cours des 3 à 6 derniers mois.
1. Réduisez la fréquence en inactifs.
1. Créez une série de [réengagements](../../delivery/using/re-engagement-best-practices.md) pour les actifs à risque modéré. Il s&#39;agit généralement de 6 à 9 mois sans engagement.
1. Développer une campagne de reconfirmation pour les actifs à risque élevé. Il s’agit généralement d’abonnés qui n’ont pas utilisé de courriel depuis 9 à 12 mois.
1. Enfin, définissez une règle d’abandon et supprimez les abonnés qui n’ont pas ouvert vos courriels depuis les mois x. Nous recommandons généralement plus de 12 mois, mais cela peut varier en fonction des ventes et du cycle d&#39;achat.
