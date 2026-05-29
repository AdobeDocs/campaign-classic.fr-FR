---
product: campaign
title: À propos de la délivrabilité dans Adobe Campaign Classic
description: En savoir plus sur la gestion de la délivrabilité dans Adobe Campaign
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
feature: Deliverability
role: User
exl-id: dcd3a9f9-5fe9-4c28-a4a5-5aed67b036ab
TQID: https://experienceleague.adobe.com/5O5mdQrj0-Ts1C-lZRDHqDYwit4dSUOZHzG5SVDVitA
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 854
ht-degree: 88%

---

# Contrôle du contenu de votre message{#control-message-content}

Pour que vos emails atteignent vos destinataires et améliorer ainsi leur taux de délivrabilité, assurez-vous qu’ils respectent un certain nombre de règles. Dans le cas contraire, le contenu de certains messages peut être détecté comme du spam. Adobe Campaign fournit plusieurs outils vous permettant de vérifier que votre contenu respecte ces règles.

Suivez les principes ci-dessous lors de la conception du contenu de votre message :

* [Adresse expéditeur](#sender-address) : l’adresse doit identifier explicitement l’expéditeur. Le domaine doit appartenir à l’expéditeur et être enregistré auprès de lui. Le registre des domaines ne doit pas être privatisé.
* [Personnalisation](#personalization) : la personnalisation du contenu et la définition d’une heure d’envoi par destinataire augmentent les chances d’ouverture de votre message.
* Images et texte : respectez un ratio texte/images correct (par exemple, 60 % de texte et 40 % d’images).
* [Lien de désinscription](#opt-out) et page de destination correspondante : le lien de désinscription est indispensable. Il doit être visible et valide, et le formulaire doit être fonctionnel.
* Prévisualisation : utilisez les outils fournis par Adobe Campaign pour vérifier et optimiser le contenu de votre email ([Inbox Rendering](#message-responsiveness), [&#x200B; SpamAssassin emails](#spamassassin)).

Pour obtenir des conseils supplémentaires sur l’optimisation de la délivrabilité lors de la conception du contenu, consultez le [Guide des bonnes pratiques relatives à la délivrabilité d’Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/content-best-practices-for-optimal-delivery.html?lang=fr).

>[!NOTE]
>
>Pour plus d’informations sur la modification du contenu de l’e-mail, consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/defining-the-email-content.html?lang=fr){target="_blank"}.

## Adresse d’expéditeur {#sender-address}

Certains FAI vérifient la validité de l’adresse d’expédition (**[!UICONTROL De]**) avant d’accepter les messages. Une adresse erronée peut causer un refus de la part du serveur receveur.

Vous devez vous assurer qu&#39;une adresse correcte est donnée au niveau de l&#39;instance (menu **[!UICONTROL Outils > Avancé > assistant de déploiement...]**) ou dans les scénarios les plus fréquemment utilisés.

Pour en savoir plus, consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/defining-the-email-content.html?lang=fr){target="_blank"}.

## Personnalisation {#personalization}

Pour améliorer l’expérience de vos destinataires et les inciter à ouvrir votre e-mail, Adobe Campaign vous permet de personnaliser vos messages.

Pour plus d’informations sur l’utilisation des champs de personnalisation dans Adobe Campaign, consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/send/personalize/personalization-fields){target="_blank"}.

## Lien et formulaire d’opt-out {#opt-out}

Par défaut, une règle de typologie vérifie au moment de l’analyse du message qu’un lien d’opt-out est bien présent dans le contenu d’une diffusion et génère un avertissement en cas d’absence. Vous pouvez modifier le niveau d’alerte de cette règle afin qu’elle génère une erreur, de façon à ce qu’en aucun cas une diffusion ne puisse être démarrée sans ce lien. Consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/validate/delivery-analysis.html?lang=fr){target="_blank"}.

Vous devez vérifier le bon fonctionnement du lien d&#39;opt-out avant chaque envoi. Par exemple, lors de l’envoi du BAT, vérifiez que le lien est valide, que le formulaire est en ligne et que sa validation change bien la valeur de **[!UICONTROL Ne plus contacter cette personne]** à **[!UICONTROL Oui]**. Cette vérification doit être systématique car on ne peut pas exclure une erreur humaine dans la saisie du lien ou dans la modification du formulaire.

Découvrez comment insérer une option d’opt-out dans la [documentation de Campaign v8](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/send/personalize/personalization-blocks.html?lang=fr){target="_blank"}.

Au cas où un problème empêchant l’exclusion ne serait détecté qu’après le démarrage de la diffusion, il sera toutefois possible d’exclure manuellement (à l’aide d’une mise à jour en masse, par exemple) les destinataires qui ont cliqué sur le lien d’opt-out, même s’ils n’ont pas pu confirmer ce choix.

En règle générale, n’essayez pas d’empêcher les destinataires qui souhaitent se désinscrire de le faire en les obligeant à remplir des champs tels que leur adresse e-mail ou leur nom, par exemple. Le formulaire ne doit comporter qu&#39;un seul bouton de validation et la réconciliation ne doit être effectuée que sur l&#39;identifiant chiffré.

Demander une confirmation supplémentaire n’est pas fiable, car un utilisateur peut disposer de deux adresses email redirigées vers la même boîte (par exemple : prénom.nom@club.com et prénom.nom@internet-club.com). Si le destinataire est capable de se souvenir uniquement de la première adresse et souhaite s’exclure via un message envoyé à l’autre, le formulaire refusera cette adresse, car l’identifiant chiffré et l’adresse e-mail saisie ne correspondront pas.

## Rendu de la boîte de réception {#message-responsiveness}

Avant d’envoyer votre message, vous pouvez tester sa réactivité en vérifiant son apparence sur différents appareils. Vous vous assurez ainsi que son affichage sera optimal sur divers clients web, webmails et appareils.

Pour permettre cette opération, Adobe Campaign capture le rendu et le rend disponible dans un rapport dédié. Vous pouvez ainsi prévisualiser le message envoyé dans les différents contextes de réception.

Pour plus d&#39;informations, consultez la section [Inbox rendering](inbox-rendering.md).

## SpamAssassin {#spamassassin}

Adobe Campaign peut être configuré pour fonctionner avec SpamAssassin. Cela permet d&#39;attribuer un score aux emails afin de déterminer si un message risque d&#39;être considéré comme indésirable par les outils anti-spams utilisés à sa réception.

Avant de démarrer une diffusion, l&#39;onglet **[!UICONTROL Aperçu]** permet d&#39;évaluer les risques. Un message d&#39;avertissement donne le résultat du test.

En savoir plus dans cette [section](spamassassin.md).
