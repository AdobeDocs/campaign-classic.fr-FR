---
solution: Campaign Classic
product: campaign
title: Mettre à jour la qualification des rebonds après une panne d’un FAI
description: Découvrez comment mettre à jour la qualification des rebonds après une panne d’un fournisseur d’accès à Internet.
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
hidefromtoc: true
exl-id: 34be23f7-17fa-475e-9663-2e353d76b172
translation-type: tm+mt
source-git-commit: 7c161862a4ce2e86e7968fd61af6b8ca28d6623f
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 60%

---

# Mettre à jour les rebonds durs incorrects après une panne d’Apple {#update-bounce-qualification.md}

## Contexte

Le 26 avril 2021, un problème mondial chez Apple a entraîné l’envoi incorrect de certains messages électroniques envoyés à des adresses électroniques Apple valides, rebondissant de manière irréversible en tant qu’adresses électroniques non valides par les serveurs Apple, avec le rebond suivant :  &quot;550 5.1.1 <email address>: succès de la recherche d&#39;utilisateur, mais aucun enregistrement d&#39;utilisateur n&#39;a été trouvé.&quot;

Ce problème s&#39;est produit le 26/4 et a duré de 7h à 1h heure normale de l&#39;Est.

En cas de panne d’un fournisseur d’accès à Internet, les emails envoyés par la biais de Campaign ne peuvent pas être correctement envoyés à leur destinataire : ils seront incorrectement marqués comme mails rebonds.

>[!NOTE]
>
>Vous pouvez vérifier le Tableau de bord d’état du système Apple sur [cette page](https://www.apple.com/support/systemstatus/).

Selon la logique standard de gestion des retours, Adobe Campaign a automatiquement ajouté ces destinataires à la liste de quarantaine avec un paramètre **[!UICONTROL Statut]** de **[!UICONTROL Quarantaine]**. Pour corriger ce problème, vous devez mettre à jour votre table de quarantaines dans Campaign en recherchant et en supprimant ces destinataires ou en basculant leur **[!UICONTROL Statut]** sur **[!UICONTROL Valide]** afin que le processus de nettoyage de nuit les supprime.

Pour trouver les destinataires qui ont été affectés par ce problème , ou au cas où cela se reproduirait avec un autre FAI, référez-vous aux instructions ci-dessous.

## Processus de mise à jour

Vous devrez exécuter une requête sur votre table de quarantaine pour filtrer tous les destinataires Apple - y compris, @icloud.com, @me.com, @mac.com - qui ont été potentiellement affectés par la panne pour pouvoir être retirés de la liste de quarantaine, et inclus dans les futures diffusions de messagerie Campaign.

En fonction du calendrier de l’incident, voici les instructions recommandées pour cette requête.

>[!IMPORTANT]
>
>Ces dates/heures sont basées sur le fuseau horaire standard de l’Est (EST). Configurez le fuseau horaire de votre instance.

* Pour les instances Campaign contenant des informations de réponse de retour SMTP dans le champ **[!UICONTROL Texte d’erreur]** de la liste de quarantaine :

   * **Le texte d’erreur (texte de la quarantaine)** contient &quot;succès de la recherche d’utilisateur, mais aucun enregistrement d’utilisateur trouvé&quot; ET le texte d’ **erreur (texte de la quarantaine)** contient &quot;support.apple.com&quot;
   * **État de la mise à jour (@lastModified)** le ou après le 26/4/2021 07:00:00
   * **Etat de la mise à jour (@lastModified)** le ou avant le 26/04/2021 01:00:00 PM

* Pour les instances Campaign contenant des informations de règles d’email entrant dans le champ **[!UICONTROL Texte d’erreur]** de la liste de quarantaine :

   * **Texte d’erreur (texte de la quarantaine)** contenant « Momen_Code10_InvalidRecipient »
   * **Domaine de courriel (@domain)** égal à icloud.com&quot; OU domaine de courriel (@domain) égal à me.com&quot; OU domaine de courriel (@domain) égal à mac.com&quot;
   * **État de la mise à jour (@lastModified)** le ou après le 26/4/2021 07:00:00
   * **Etat de la mise à jour (@lastModified)** le ou avant le 26/04/2021 01:00:00 PM

Une fois que vous disposez de la liste des destinataires concernés, vous pouvez soit leur attribuer l’état **[!UICONTROL Valide]** afin qu’ils soient supprimés de la liste de quarantaine par le processus de nettoyage de la base de données ****, soit simplement les supprimer de la table.

**Rubriques connexes :**
* [Présentation des diffusions en échec](../../delivery/using/understanding-delivery-failures.md)
* [Qualification des mails rebonds](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification)
