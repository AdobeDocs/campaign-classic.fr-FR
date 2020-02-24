---
title: À propos de la délivrabilité dans Adobe Campaign Classic
description: En savoir plus sur la gestion de la délivrabilité dans Adobe Campaign Classic.
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
source-git-commit: 68756f920fbc8658cff552615adbf023b4c5e3aa

---


# Contrôle du contenu de votre message{#control-message-content}

Pour améliorer le taux de remise des courriers électroniques et veiller à ce que vos courriers électroniques parviennent à vos destinataires, vous devez respecter un certain nombre de règles détaillées ci-dessous.

## Adresse d&#39;expéditeur {#sender-address}

Certains FAI vérifient la validité de l&#39;adresse d&#39;expéditeur (From) avant d&#39;accepter les messages. Une adresse erronée peut causer un refus de la part du serveur receveur. You must make sure a correct address is given at the instance level (menu **[!UICONTROL Tools > Advanced > Deployment wizard...]**) or in the most frequently-used scenarios.

## Lien et formulaire de désinscription {#opt-out}

Par défaut, une règle de typologie vérifie au moment de l&#39;analyse qu&#39;un lien de désinscription est bien présent dans le contenu d&#39;une diffusion et génère un avertissement en cas d&#39;absence. On peut éventuellement modifier le niveau d&#39;alerte de cette règle afin qu&#39;elle génère une erreur, de façon à ce qu&#39;en aucun cas une diffusion ne puisse être démarrée sans ce lien.

Il faut vérifier du début à la fin le bon fonctionnement du lien de désinscription avant chaque envoi. Par exemple, lors de l&#39;envoi du BAT, vérifiez que le lien est valide, que le formulaire est en ligne et que sa validation change bien la valeur de **[!UICONTROL Ne plus contacter cette personne]** à **[!UICONTROL Oui]**. Cette vérification doit être systématique car on ne peut pas exclure une erreur humaine dans la saisie du lien ou dans la modification du formulaire.

Au cas où un problème empêchant la désinscription ne serait détecté qu&#39;après le démarrage de la diffusion, il sera toutefois possible de désinscrire manuellement (à l&#39;aide d&#39;une mise à jour en masse, par exemple) les destinataires qui ont cliqué sur le lien de désinscription, même s&#39;ils n&#39;ont pas pu ou voulu confirmer ce choix.

Sauf dans des cas bien particuliers, il ne faut pas tenter de freiner la désinscription en demandant à l&#39;utilisateur de remplir certains champs comme l&#39;email, le nom, etc. Le formulaire ne devra comprendre qu&#39;un seul bouton de validation et la réconciliation ne se fera que sur l&#39;identifiant crypté. Demander une confirmation supplémentaire de l&#39;email n&#39;est pas fiable : il se peut qu&#39;une même personne possède deux adresses emails redirigées vers la même boîte (par exemple prenom.nom@club.fr et prenom.nom@club-internet.fr). Si cette personne ne se souvient que de la première adresse et qu&#39;elle souhaite se désinscrire via un message envoyé à la seconde, le formulaire refusera la modification car l&#39;identifiant crypté et l&#39;email saisi ne correspondent pas.

## SpamAssassin {#spamassassin}

Adobe Campaign peut être configuré pour fonctionner avec SpamAssassin. Cela permet d&#39;attribuer un score aux emails afin de déterminer si un message risque d&#39;être considéré comme indésirable par les outils anti-spams utilisés à sa réception.

Avant qu&#39;une diffusion ne soit lancée, l&#39;onglet Aperçu permet de visualiser les risques. Un message d’avertissement indique le résultat du test.

En savoir plus dans cette [section](../../delivery/using/spamassassin.md).