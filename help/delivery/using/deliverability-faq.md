---
product: campaign
title: Points clés de la gestion de la délivrabilité dans Adobe Campaign Classic
description: Découvrez les points clés à vérifier lors de la gestion de la délivrabilité dans Adobe Campaign.
feature: Deliverability, Troubleshooting
role: User
exl-id: f94897c1-b44c-4100-ac50-a89b13fa6f2f
TQID: https://experienceleague.adobe.com/ZRai7Bd-IRaWUQQmkuUYwXhNXp2BI-B4k-4cGq1k6uk
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 674
ht-degree: 83%

---

# Résolution des problèmes de délivrabilité{#deliverability-faq}

Vous rencontrez un problème de délivrabilité ? La solution se trouve peut-être ici.

## Erreur de règle MX {#mx-rule-error}

**A quoi correspond le message d&#39;erreur &quot;Quota atteint&quot; ?**

Ce message signifie que vous avez atteint le seuil limite pour un MX spécifique et que vous devez attendre pour pouvoir envoyer un autre email au FAI.

Dans Adobe Campaign, il existe une configuration concernant le nombre d’e-mails par heure qui peuvent être envoyés. Ce paramétrage doit être utilisé avec précaution car le nombre défini dans l&#39;instance concerne le nombre de connexions réalisées avec le FAI et non le nombre d&#39;emails réellement envoyés.

Cela signifie qu’une connexion peut utiliser une règle MX sans envoyer d’e-mail. Dans ce cas, une configuration avec une adresse IP ou un domaine à faible réputation devra essayer plusieurs connexions avant d&#39;envoyer un e-mail. Pour chaque tentative, un crédit de messages par heure sera utilisé. Par conséquent, les performances de la campagne marketing seront affectées de manière significative.

Le message &quot;quotas atteints&quot; n’indique donc pas seulement un problème de configuration, mais peut aussi être lié à la réputation. Il est important d’analyser les messages d’erreur dans le [log SMTP](../../production/using/monitoring-processes.md#smtp-errors-per-domain).

Pour en savoir plus à propos de la configuration des MX, voir [cette section](../../installation/using/email-deliverability.md#mx-configuration).

## Même message d’erreur pour un FAI {#same-error-for-an-isp}

**Pourquoi ai-je toujours le même message d&#39;erreur pour un FAI particulier ?**

Si vous recevez toujours le même message d&#39;erreur pour un FAI, il se peut que vous rencontriez des problèmes de réputation liés à votre adresse IP ou votre adresse d&#39;expéditeur. Appliquez les recommandations suivantes :
* Vérifiez si vous recevez un fort pourcentage d’échecs liés à des adresses email inexistantes (échecs de type **Utilisateur inconnu**)
* Mettez à jour vos formulaires d’abonnement pour détecter d’éventuelles erreurs sur la saisie des noms de domaine (par exemple, gmaul.com ou yaho.com)
* Si vous constatez des erreurs indiquant que vos messages sont déclarés en spam, ou que vos messages sont constamment bloqués, essayez d’exclure de la cible les destinataires qui n’ont pas ouvert ou cliqué dans l’un de vos messages dans les 12 mois précédents.

Si le problème persiste, contactez les services commerciaux, les services chargés de la délivrabilité ou l&#39;[Assistance clientèle d’Adobe Campaign](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Liste bloquée et quarantaine {#denylist-versus-quarantine}

* **Quelle est la différence entre une adresse email en liste bloquée et une adresse email en quarantaine ?**

   * Le statut **[!UICONTROL Placé sur la liste bloquée]** signifie qu’une personne a déclaré un message comme étant un spam.

   * L’application du statut **[!UICONTROL Quarantaine]** est le résultat d’un rebond temporaire ou définitif.

  Voir à ce propos [cette section](delivery-failures-quarantine.md#quarantine-vs-denylist).

* **À quoi correspondent les différentes raisons de mise en quarantaine ?**

  Il existe dix raisons de mise en quarantaine : non définie, utilisateur inconnu, domaine invalide, sur liste bloquée, refusé, erreur ignorée, inatteignable, compte désactivé, boîte pleine, non connecté.

  Pour plus d’informations, voir [Comprendre la gestion des quarantaines](delivery-failures-quarantine.md).

## Retrait de la liste bloquée {#remove-from-denylist}

* **Un de mes destinataires a été ajouté par erreur à la liste bloquée. Comment puis-je le retirer de la liste bloquée pour pouvoir lui envoyer à nouveau des messages ?**

   * Sélectionnez **[!UICONTROL Administration > Gestion de campagne > Gestion des NP@I > NP@I et Adresses]**.
   * Dans l’écran de détails de l’enregistrement correspondant, changez la valeur du champ **[!UICONTROL Statut]** à **[!UICONTROL Valide]**.
   * Sauvegardez l’enregistrement.

* **Comment puis-je savoir si l&#39;une de mes adresses IP est sur une liste bloquée ? Comment supprimer mes adresses IP d’une liste bloquée ?**

  Pour vérifier si votre adresse IP se trouve sur une liste bloquée, vous pouvez utiliser différents sites web, tels que :
   * [MX Toolbox](https://mxtoolbox.com/)
   * [Quelle est mon adresse IP ?](https://whatismyipaddress.com)

  En général, la vérification d&#39;une adresse IP renvoie une liste contenant les détails de la liste bloquée et le nom du site web qui a bloqué l&#39;adresse IP.

  En cliquant sur le lien correspondant, vous pouvez accéder aux détails du site web. Vous pouvez ensuite demander que votre adresse IP soit supprimée du site web qui l’a mise en liste bloquée.

  >[!NOTE]
  >
  >Le processus peut varier selon le site web. Certains sites requièrent la création d&#39;un compte alors que d&#39;autres demandent uniquement que vous fournissiez l&#39;adresse IP.
