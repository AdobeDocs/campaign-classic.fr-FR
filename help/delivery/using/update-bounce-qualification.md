---
product: campaign
title: Mise à jour de la qualification des rebonds après la panne d’Apple en 2021
description: Découvrez comment mettre à jour la qualification des rebonds après la panne dʼApple en 2021.
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
feature: Deliverability
exl-id: 34be23f7-17fa-475e-9663-2e353d76b172
source-git-commit: 62ab16b206563aa25b8943e606d03a3184eb00db
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 98%

---

# Mettre à jour les erreurs hard incorrectes après une panne d’Apple {#update-bounce-qualification.md}

## Contexte

Le 26 avril 2021, suite à un problème mondial chez Apple, l’envoi de certains e-mails à des adresses e-mail Apple valides a entraîné des rebonds définitifs incorrects. Ces adresses e-mail ont été considérées comme non valides par les serveurs Apple, avec la réponse de rebond suivante : « 550 5.1.1 &quot;adresse e-mail&quot;: user lookup success but no user record found » (l’utilisateur a été trouvé, mais aucun enregistrement d’utilisateur trouvé).

Ce problème s&#39;est produit le 26 avril et a duré de 7 h à 13 h EST. 

>[!NOTE]
>
>Vous pouvez vérifier le tableau de bord d&#39;état du système Apple sur [cette page](https://www.apple.com/fr/support/systemstatus/).

En cas de panne d&#39;un fournisseur d&#39;accès à Internet, les emails envoyés par la biais de Campaign ne peuvent pas être correctement envoyés à leur destinataire : ils seront incorrectement marqués comme mails rebonds.

Selon la logique standard de gestion des rebonds, Adobe Campaign a automatiquement ajouté ces destinataires à la liste de quarantaine avec un paramètre **[!UICONTROL Statut]** de **[!UICONTROL Quarantaine]**. Pour corriger ce problème, vous devez mettre à jour votre table de quarantaines dans Campaign en recherchant et en supprimant ces destinataires ou en basculant leur **[!UICONTROL Statut]** sur **[!UICONTROL Valide]** afin que le processus de nettoyage de nuit les supprime.

Pour trouver les destinataires qui ont été affectés par ce problème , ou au cas où cela se reproduirait avec un autre FAI, référez-vous aux instructions ci-dessous.

## Processus de mise à jour

Vous devrez exécuter une requête sur votre table de quarantaine pour filtrer tous les destinataires Apple qui ont été potentiellement affectés par la panne (qui incluent @icloud.com, @me.com, @mac.com), afin qu&#39;ils puissent être supprimés de la liste de quarantaine et inclus dans les futures diffusions d&#39;emails de Campaign.

En fonction du calendrier de l&#39;incident, voici les instructions recommandées pour cette requête.

>[!IMPORTANT]
>
>Ces dates/heures sont basées sur le fuseau horaire standard de l&#39;Est (EST). Configurez le fuseau horaire de votre instance.

* Pour les instances Campaign contenant des informations de réponse de rebond SMTP dans le champ **[!UICONTROL Texte d’erreur]** de la liste de quarantaine :

   * **Le texte d’erreur (texte de quarantaine)** contient « l’utilisateur a été trouvé, mais pas l’enregistrement d’utilisateur » **ET le texte d’erreur (texte de quarantaine)** contient « support.apple.com ».
   * **Mise à jour du statut (@lastModified)** le ou après le 26/04/2021 à 07:00:00
   * **Mise à jour du statut (@lastModified)** le ou avant le 26/04/2021 à 13:00:00

* Pour les instances Campaign contenant des informations de règles d&#39;email entrant dans le champ **[!UICONTROL Texte d&#39;erreur]** de la liste de quarantaine :

   * Le **texte d’erreur (texte de la quarantaine)** contenant « Momen_Code10_InvalidRecipient ».
   * **Domaine d&#39;e-mail (@domaine)** égal à icloud.com OU **domaine d&#39;e-mail (@domaine)** égal à me.com OU **domaine d&#39;e-mail (@domaine)** égal à mac.com
   * **Mise à jour du statut (@lastModified)** le ou après le 26/04/2021 à 07:00:00
   * **Mise à jour du statut (@lastModified)** le ou avant le 26/04/2021 à 13:00:00

Une fois que vous disposez de la liste des destinataires concernés, vous pouvez soit leur attribuer l&#39;état **[!UICONTROL Valide]** afin qu&#39;ils soient supprimés de la liste de quarantaine par le processus de **[!UICONTROL nettoyage de la base de données]**, soit simplement les supprimer de la table.

**Rubriques connexes :**
* [Présentation des diffusions en échec](delivery-failures-quarantine.md)
* [Qualification des e-mails rejetés](delivery-failures-quarantine.md#bounce-mail-qualification)
