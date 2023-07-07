---
product: campaign
title: À propos de la délivrabilité dans Adobe Campaign Classic
description: En savoir plus sur la gestion de la délivrabilité dans Adobe Campaign
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Deliverability
exl-id: dcd3a9f9-5fe9-4c28-a4a5-5aed67b036ab
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 100%

---

# Contrôle du contenu de votre message{#control-message-content}



Pour que vos emails atteignent vos destinataires et améliorer ainsi leur taux de délivrabilité, assurez-vous qu’ils respectent un certain nombre de règles. Dans le cas contraire, le contenu de certains messages peut être détecté comme du spam. Adobe Campaign fournit plusieurs outils vous permettant de vérifier que votre contenu respecte ces règles.

Suivez les principes ci-dessous lors de la conception du contenu de votre message :

* [Adresse expéditeur](#sender-address) : l’adresse doit identifier explicitement l’expéditeur. Le domaine doit appartenir à l’expéditeur et être enregistré auprès de lui. Le registre des domaines ne doit pas être privatisé.
* [Personnalisation](#personalization) : la personnalisation du contenu et la définition d’une heure d’envoi par destinataire augmentent les chances d’ouverture de votre message.
* Images et texte : respectez un ratio texte/images correct (par exemple, 60 % de texte et 40 % d’images).
* [Lien de désinscription](#opt-out) et landing page correspondante : le lien de désinscription est indispensable. Il doit être visible et valide. En outre, le formulaire doit être fonctionnel.
* Prévisualisation : utilisez les outils fournis par Adobe Campaign pour vérifier et optimiser le contenu de votre email ([Inbox Rendering](#message-responsiveness), [ SpamAssassin emails](#spamassassin)).

Pour obtenir des conseils supplémentaires sur l’optimisation de la délivrabilité lors de la conception du contenu, consultez le [Guide des bonnes pratiques relatives à la délivrabilité d’Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/content-best-practices-for-optimal-delivery.html?lang=fr).

>[!NOTE]
>
>Pour plus d’informations sur la modification du contenu des e-mails, consultez les sections [Définition du contenu de l’e-mail](defining-the-email-content.md) et [Création de contenu personnalisé](design-and-personalize.md).

## Adresse d’expéditeur {#sender-address}

Certains FAI vérifient la validité de l’adresse de l’expéditeur (**[!UICONTROL De]**) avant d’accepter les messages. Une adresse mal formée peut entraîner son rejet par le serveur de réception.

Il faut s’assurer qu’une adresse correcte est bien renseignée au niveau de l’instance (menu **[!UICONTROL Outils > Avancé > Assistant de déploiement...)]** ou dans les scénarios les plus couramment utilisés.

Pour plus d’informations à ce sujet, consultez [cette page](defining-the-email-content.md).

## Personnalisation {#personalization}

Pour améliorer l’expérience de vos destinataires et les inciter à ouvrir votre email, Adobe Campaign vous permet de personnaliser vos messages.

Pour plus d’informations sur l’utilisation des champs de personnalisation dans Adobe Campaign, voir [cette section](personalization-fields.md).

Vous trouverez dans [cette section](design-and-personalize.md#optimize-personalization) un certain nombre de conseils pour optimiser la personnalisation lors de la création de votre contenu.

## Lien et formulaire d’opt-out {#opt-out}

Par défaut, une [règle de typologie](steps-validating-the-delivery.md#validation-process-with-typologies) vérifie au moment de l’analyse qu’un lien d’opt-out est bien présent dans le contenu d’une diffusion et génère un avertissement en cas d’absence. On peut éventuellement modifier le niveau d’alerte de cette règle afin qu’elle génère une erreur, de façon à ce qu’en aucun cas une diffusion ne puisse être démarrée sans ce lien.

Il faut vérifier du début à la fin le bon fonctionnement du lien d’opt-out avant chaque envoi. Par exemple, lors de l’envoi du BAT, vérifiez que le lien est valide, que le formulaire est en ligne et que sa validation change bien la valeur de **[!UICONTROL Ne plus contacter cette personne]** à **[!UICONTROL Oui]**. Cette vérification doit être systématique car on ne peut pas exclure une erreur humaine dans la saisie du lien ou dans la modification du formulaire.

Découvrez comment insérer un lien d&#39;opt-out [dans cette section](personalization-blocks.md#personalization-blocks-example).

Au cas où un problème empêchant l’exclusion ne serait détecté qu’après le démarrage de la diffusion, il sera toutefois possible d’exclure manuellement (à l’aide d’une mise à jour en masse, par exemple) les destinataires qui ont cliqué sur le lien d’opt-out, même s’ils n’ont pas pu confirmer ce choix.

Il est recommandé de ne pas empêcher les destinataires qui souhaitent s’exclure en les obligeant à remplir des champs tels que leur adresse e-mail ou leur nom, par exemple. Le formulaire ne doit comporter qu’un seul bouton de validation et la réconciliation ne doit être effectuée que sur l’identifiant chiffré.

Demander une confirmation supplémentaire n’est pas fiable, car un utilisateur peut disposer de deux adresses email redirigées vers la même boîte (par exemple : prénom.nom@club.com et prénom.nom@internet-club.com). Si le destinataire est capable de se souvenir uniquement de la première adresse et souhaite s’exclure via un message envoyé à l’autre, le formulaire refusera cette adresse, car l’identifiant chiffré et l’adresse email saisie ne correspondront pas.

## Inbox rendering {#message-responsiveness}

Avant d’envoyer votre message, vous pouvez tester sa réactivité en vérifiant son apparence sur différents appareils. Vous vous assurez ainsi que son affichage sera optimal sur divers clients web, webmails et appareils.

Pour vous aider, Adobe Campaign capture le rendu et le rend disponible dans un rapport dédié. Vous pouvez visualiser l&#39;affichage du message envoyé dans les différents contextes de réception.

Pour plus d&#39;informations, consultez la section [Inbox rendering](inbox-rendering.md).

## SpamAssassin {#spamassassin}

Adobe Campaign peut être configuré pour fonctionner avec SpamAssassin. Cela permet d&#39;attribuer un score aux emails afin de déterminer si un message risque d&#39;être considéré comme indésirable par les outils anti-spams utilisés à sa réception.

Avant qu’une diffusion ne soit lancée, l’onglet **[!UICONTROL Aperçu]** permet de visualiser les risques. Un message d’avertissement donne le résultat du test.

En savoir plus dans cette [section](spamassassin.md).
