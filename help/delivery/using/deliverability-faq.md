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
translation-type: ht
source-git-commit: 56fed9fff445892366d3e0f1367029882077ae20
workflow-type: ht
source-wordcount: '1371'
ht-degree: 100%

---


# Résolution des problèmes de délivrabilité{#deliverability-faq}

Vous rencontrez un problème de délivrabilité ? La solution se trouve peut-être ici.

## Erreur de règle MX {#mx-rule-error}

**A quoi correspond le message d&#39;erreur &quot;Quota atteint&quot; ?**

Ce message signifie que vous avez atteint le seuil limite pour un MX spécifique et que vous devez attendre pour pouvoir envoyer un autre email au FAI.

Dans Adobe Campaign, il existe une configuration à propos du nombre d&#39;emails pouvant être envoyé par heure. Ce quota doit être utilisé avec précaution car le nombre défini dans l&#39;instance se rapporte au nombre de connexions réalisées avec le FAI et non le nombre de messages réellement envoyés.

Une connexion peut donc utiliser une règle MX sans réussir l&#39;envoi d&#39;un email. Dans ce cas, une configuration avec une IP ou un nom de domaine à faible réputation devra tenter plusieurs connexions avant de réussir l&#39;envoi d&#39;un email. Pour chaque tentative un crédit Messages par heure sera utilisé. La performance de la campagne marketing sera fortement réduite.

Le message &quot;quotas atteints&quot; n’indique donc pas seulement un problème de configuration, mais peut aussi être lié à la réputation. Il est important d’analyser les messages d’erreur dans le [log SMTP](../../production/using/monitoring-processes.md#smtp-errors-per-domain).

Pour en savoir plus à propos de la configuration des MX, voir [cette section](../../installation/using/email-deliverability.md#mx-configuration).

## Même message d’erreur pour un FAI {#same-error-for-an-isp}

**Pourquoi ai-je toujours le même message d&#39;erreur pour un FAI particulier ?**

Si vous recevez toujours le même message d&#39;erreur pour un FAI, il se peut que vous rencontriez des problèmes de réputation liés à votre adresse IP ou votre adresse d&#39;expéditeur. Appliquez les recommandations suivantes :
* Vérifiez si vous recevez un fort pourcentage d&#39;échecs liés à des adresses email inexistantes (échecs de type **Utilisateur inconnu**)
* Mettez à jour vos formulaires d&#39;abonnement pour détecter d&#39;éventuelles erreurs sur la saisie des noms de domaine (par exemple, gmaul.com ou yaho.com)
* Si vous constatez des erreurs indiquant que vos messages sont déclarés en spam, ou que vos messages sont constamment bloqués, essayez d&#39;exclure de la cible les destinataires qui n&#39;ont pas ouvert ou cliqué dans l&#39;un de vos messages dans les 12 mois précédents.

Si le problème persiste, contactez les services commerciaux, délivrabilité, assistance d’Adobe Campaign ou support technique d’Adobe Campaign.

## Différence entre liste bloquée et quarantaine {#block-list-versus-quarantine}

* **Quelle est la différence entre une adresse email sur liste bloquée et une adresse email en quarantaine ?**

   * Le statut **[!UICONTROL En liste bloquée]** signifie que l’un de vos destinataires a déclaré un message comme étant un spam.

   * L&#39;application du statut **[!UICONTROL Quarantaine]** est entraînée par un échec soft ou hard.
   Voir à ce propos [cette section](../../delivery/using/understanding-quarantine-management.md#quarantine-vs-block-list).

* **A quoi correspondent les différentes raisons de mise en quarantaine ?**

   Il existe dix raisons de mise en quarantaine : non définie, utilisateur inconnu, domaine invalide, adresse en liste bloquée, refusé, erreur ignorée, inatteignable, compte désactivé, boîte pleine, non connecté.

   Pour plus d’informations, voir [Comprendre la gestion des quarantaines](../../delivery/using/understanding-quarantine-management.md).

## Retrait d’une adresse email de la liste bloquée {#remove-from-block-list}

* **Un de mes destinataires a été ajouté par erreur à la liste bloquée. Comment puis-je le retirer de la liste bloquée pour pouvoir lui envoyer à nouveau des messages ?**

   * Sélectionnez **[!UICONTROL Administration > Gestion de campagne > Gestion des NP@I > NP@I et Adresses]**.
   * Dans l&#39;écran de détails de l&#39;enregistrement correspondant, changez la valeur du champ **[!UICONTROL Statut]** à **[!UICONTROL Valide]**.
   * Sauvegardez l&#39;enregistrement.

* **Comment savoir si une de mes adresses IP est en liste bloquée ? Comment supprimer mes adresses IP d’une liste bloquée ?**

   Pour vérifier si votre adresse IP se trouve dans une liste bloquée, vous pouvez utiliser différents sites web pour la vérifier, tels que :
   * [MX Toolbox](https://mxtoolbox.com/)
   * [Quelle est mon adresse IP ?](https://whatismyipaddress.com)

   En général, la vérification d’une adresse IP renvoie une liste contenant les détails de la liste bloquée et le nom du site web qui a bloqué l’adresse IP.

   En cliquant sur le lien correspondant, vous pouvez accéder aux détails du site web. Vous pouvez ensuite demander que votre adresse IP soit supprimée du site web qui l’a mise en liste bloquée.

   >[!NOTE]
   >
   >Le processus peut varier selon le site web. Certains sites requièrent la création d&#39;un compte alors que d&#39;autres demandent uniquement que vous fournissiez l&#39;adresse IP.

## Bonnes pratiques {#best-practices}

Vous trouverez ci-dessous quelques bonnes pratiques pour mieux identifier et résoudre les problèmes de délivrabilité.

### Identifier un problème de délivrabilité {#identify-deliverability-issue}

Il est possible que les éléments suivants attirent votre attention :

* Mesures de publipostage ou de campagne : les taux de désabonnement, de plaintes pour abus et/ou de rebonds sont plus élevés que d’habitude.
* Activité d’abonné : les ouvertures, les clics et/ou les transactions sont inférieurs à la normale.
* Les comptes d’adresse de contrôle indiquent des envois filtrés ou non diffusés.

### Formuler des hypothèses sur les causes potentielles {#potential-causes}

Posez-vous les questions suivantes pour identifier les causes possibles de votre problème de délivrabilité :

* Y a-t-il eu récemment un changement dans la segmentation des listes ?
* Ai-je acquis de nouvelles sources de données ?
* Ai-je envoyé par inadvertance un fichier de quarantaine ?
* Le problème peut-il être dû au contenu de mon message ?
* Est-ce que j’envoie des emails assez souvent pour maintenir le rodage des adresses IP ?
* Ai-je segmenté mes envois par activité/engagement ou ai-je envoyé des fichiers complets ?
* Quel est le segment « sûr » de mon dossier en termes de récence ?
* Des stratégies de réactivation et de reconfirmation sont-elles en place pour les segments qui ne sont pas définis comme sûrs ?

### Résoudre le problème {#address-issue}

**Plaintes (Complaints)**

Les plaintes sont définies par les abonnés qui **signalent un email comme indésirable** en appuyant sur le bouton correspondant de leur boîte de réception.

Si votre problème de diffusion est dû à des plaintes :
* Vous devez essayer de déterminer pourquoi les destinataires se plaignent.
* Vous pouvez également envisager de déplacer votre lien de désabonnement en haut de votre email. Ainsi, les abonnés pourront se désabonner au lieu de se plaindre en utilisant le bouton spam.

Les expéditeurs peuvent recueillir une mine d’informations à partir des plaintes issues d’une [feedback loop](../../delivery/using/technical-recommendations.md#feedback-loop) :
* Il est important de regrouper les données et de rechercher des schémas dans des éléments comme la source d’opt-in, la durée d’abonnement à l’adresse, ou même certains comportements liés aux données démographiques.
* Les plaintes permettent souvent d’identifier une source ou un segment de données à risque dans le fichier. Le risque se définit comme une probabilité maximale de plainte, ce qui peut nuire à la réputation, et en retour, aux taux de placement en boîte de réception.

Les plaintes proviennent aussi des abonnés qui ne veulent tout simplement plus recevoir d’emails :
* Souvent, cette situation découle d’un nombre excessif de messages, de leur perception par les abonnés, du caractère inattendu des messages ou de l’oubli par les abonnés de leur accord préalable.
* Par ailleurs, il est important de vérifier que tous les points de collecte sont clairs et qu’il n’y a pas de cases précochées dans vos points d’acquisition.
* Vous devez également envoyer un email de bienvenue aux abonnés qui donnent leur accord préalable pour leur expliquer à quelle fréquence ils peuvent s’attendre à recevoir des emails de votre part.

**Validité des données**

**Les erreurs hard** se produisent lorsque vous effectuez un envoi à une **adresse en échec** d’un FAI. Une adresse peut être en échec pour de nombreuses raisons, notamment :
* Adresse mal orthographiée. Il est possible de résoudre ce problème grâce à un service de validation des données en temps réel ou à l’obligation de confirmer l’accord préalable avant d’envoyer des emails marketing à cette adresse.
* Liste ou source de données incorrecte. Si les adresses proviennent d’une nouvelle source, vérifiez comment elles ont été collectées et assurez-vous que leur utilisation a été autorisée.
* Envoi à une adresse active à un moment donné, mais fermée ou supprimée suite à une période d’inactivité.

**Engagement**

Outre les plaintes et la validité des données, les FAI privilégient plus que jamais l’**engagement positif** pour prendre des décisions de diffusion. Ils cherchent à savoir si vos abonnés ouvrent vos emails ou les effacent sans les lire. Comme ils ne partagent pas ces données avec les expéditeurs, nous devons utiliser les informations disponibles et traduire les ouvertures/clics/transactions en engagements.

Dans le cadre de la gestion permanente de la réputation, il est important de comprendre le niveau d’engagement des abonnés de votre liste et d’établir une **hiérarchie des risques liés à la récence** pour les abonnés de chaque fichier. La récence est définie comme la date d’ouverture/de clic/de transaction ou d’abonnement la plus récente. Cette période peut différer selon la verticale. Pour cela :

1. Déterminez les segments actifs (« sûrs ») pour chaque verticale. Il s’agit généralement d’abonnés qui ont été actifs au cours des 3 à 6 derniers mois.
1. Réduisez la fréquence au niveau des inactifs.
1. Créez une série de [réengagements](../../delivery/using/re-engagement-best-practices.md) pour les inactifs à risque modéré. Il s’agit généralement d’abonnés qui ne se sont pas engagés depuis 6 à 9 mois.
1. Développez une campagne de reconfirmation pour les inactifs à risque élevé. Il s’agit généralement d’abonnés qui ne se sont pas engagés par email depuis 9 à 12 mois.
1. Enfin, définissez une règle d’abandon et supprimez les abonnés qui n’ont pas ouvert vos emails depuis « x » mois. Nous recommandons généralement une durée de 12 mois, mais cela peut varier en fonction des ventes et du cycle d’achat.
