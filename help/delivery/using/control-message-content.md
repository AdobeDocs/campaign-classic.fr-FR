---
solution: Campaign Classic
product: campaign
title: A propos de la délivrabilité dans Adobe Campaign Classic
description: En savoir plus sur la gestion de la délivrabilité dans Adobe Campaign Classic.
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: d6a581ae86e50c17ac20fe54baf305b864e11790
workflow-type: tm+mt
source-wordcount: '774'
ht-degree: 36%

---


# Contrôler le contenu de votre message{#control-message-content}

Pour que vos courriels atteignent vos destinataires et améliorent le taux de livraison de vos courriels, ils doivent respecter un certain nombre de règles. Sinon, le contenu de certains messages peut être détecté comme indésirable. Adobe Campaign fournit plusieurs outils pour que votre contenu respecte ces règles.

Suivez les principes ci-dessous lors de la conception du contenu de votre message :

* [Adresse](#sender-address) de l&#39;expéditeur : l&#39;adresse doit identifier explicitement l&#39;expéditeur. Le domaine doit être détenu par l&#39;expéditeur et enregistré auprès de celui-ci. Le registre des domaines ne doit pas être privatisé.
* [Personnalisation](#personalization) : la personnalisation du contenu et la définition d’une heure d’envoi par destinataire augmentent les chances d’ouverture de votre message.
* Images et texte : respectez un rapport texte/image correct (par exemple, 60 % de texte et 40 % d’images).
* [Désinscription ](#opt-out) linkand landing page : le lien désinscription est essentiel. Il doit être visible et valide et le formulaire doit être fonctionnel.
* Prévisualisation : utilisez les outils proposés par Adobe Campaign pour vérifier et optimiser le contenu de votre courrier électronique ([rendu de boîte de réception](#message-responsiveness), [SpamAssassin](#spamassassin)).

Pour obtenir des conseils supplémentaires sur l&#39;optimisation de la délivrabilité lors de la conception de contenu, consultez le [Guide des meilleures pratiques en matière de délivrabilité des Adobes](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/content-best-practices-for-optimal-delivery.html).

>[!NOTE]
>
>Pour plus d’informations sur la modification du contenu des courriels, voir [Définition du contenu des courriels](../../delivery/using/defining-the-email-content.md) et [Création de contenu personnalisé](../../delivery/using/design-and-personalize.md).

## Adresse d&#39;expéditeur {#sender-address}

Certains FAI vérifient la validité de l&#39;adresse de l&#39;expéditeur (**[!UICONTROL From]**) avant d&#39;accepter les messages. Une adresse mal formée peut entraîner son rejet par le serveur de réception.

Il faut s&#39;assurer qu&#39;une adresse correcte est bien renseignée au niveau de l&#39;instance (menu **[!UICONTROL Outils > Avancé > Assistant de déploiement...)]** ou dans les scénarios les plus couramment utilisés.

Pour plus d&#39;informations à ce sujet, voir [Définition de l&#39;expéditeur](../../delivery/using/defining-the-email-content.md).

## Personnalisation      {#personalization}

Pour améliorer l’expérience de vos destinataires et les faire ouvrir, Adobe Campaign vous permet de personnaliser vos messages.

Pour plus d’informations sur l’utilisation des champs de personnalisation en Adobe Campaign, voir [cette section](../../delivery/using/personalization-fields.md).

Vous trouverez dans [cette section](../../delivery/using/design-and-personalize.md#optimize-personalization) quelques conseils pour optimiser la personnalisation lors de la création de votre contenu.

## Lien et formulaire de désinscription {#opt-out}

Par défaut, lorsque le message est analysé, une [règle de typologie](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies) vérifie si un lien d’exclusion a été inclus et génère un avertissement s’il est absent. Vous pouvez modifier cette règle afin qu’une erreur soit déclenchée plutôt qu’un simple avertissement et empêcher une diffusion de sortir sans ce lien.

Il faut vérifier du début à la fin le bon fonctionnement du lien de désinscription avant chaque envoi. Par exemple, lors de l&#39;envoi du BAT, vérifiez que le lien est valide, que le formulaire est en ligne et que sa validation change bien la valeur de **[!UICONTROL Ne plus contacter cette personne]** à **[!UICONTROL Oui]**. Cette vérification doit être systématique car on ne peut pas exclure une erreur humaine dans la saisie du lien ou dans la modification du formulaire.

Découvrez comment insérer un lien d’exclusion [dans cette section](../../delivery/using/personalization-blocks.md#personalization-blocks-example).

Au cas où un problème empêchant la désinscription ne serait détecté qu&#39;après le démarrage de la diffusion, il sera toutefois possible de désinscrire manuellement (à l&#39;aide d&#39;une mise à jour en masse, par exemple) les destinataires qui ont cliqué sur le lien de désinscription, même s&#39;ils n&#39;ont pas pu ou voulu confirmer ce choix.

En règle générale, n’essayez pas d’empêcher les destinataires qui souhaitent s’exclure en les obligeant à remplir des champs tels que leur adresse électronique ou leur nom, par exemple. Le formulaire ne doit comporter qu’un seul bouton de validation et la réconciliation ne doit être effectuée que sur l’identifiant chiffré.

La demande de confirmation supplémentaire n&#39;est pas fiable : un utilisateur peut voir deux adresses électroniques redirigées vers la même zone (par exemple : firstname.lastname@club.com et firstname.lastname@internet-club.com). Si le destinataire est capable de se souvenir de la première adresse seulement et souhaite se désabonner via un message envoyé à l&#39;autre, le formulaire refusera cette adresse car l&#39;identifiant chiffré et l&#39;adresse électronique saisie ne correspondent pas.

## Inbox rendering {#message-responsiveness}

Avant d&#39;envoyer votre message, vous pouvez tester la réactivité de votre message en vérifiant à quoi ressemblera votre message sur différents périphériques. Vous vous assurez ainsi que son affichage sera optimal sur divers clients web, webmails et appareils.

Pour vous aider, Adobe Campaign capture le rendu et le rend disponible dans un rapport dédié. Vous pouvez visualiser l&#39;affichage du message envoyé dans les différents contextes de réception.

Voir à ce propos la section [Inbox rendering](../../delivery/using/inbox-rendering.md).

## SpamAssassin {#spamassassin}

Adobe Campaign peut être configuré pour fonctionner avec SpamAssassin. Cela permet d&#39;attribuer un score aux emails afin de déterminer si un message risque d&#39;être considéré comme indésirable par les outils anti-spams utilisés à sa réception.

Avant de démarrer une diffusion, l&#39;onglet **[!UICONTROL Prévisualisation]** vous permet d&#39;évaluer les risques. Un message d’avertissement indique le résultat du test.

En savoir plus dans cette [section](../../delivery/using/spamassassin.md).