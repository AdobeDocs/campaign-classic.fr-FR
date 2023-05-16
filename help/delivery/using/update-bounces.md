---
product: campaign
title: Mettre à jour la qualification des rebonds après une panne d’un FAI
description: Découvrez comment mettre à jour la qualification des retours après une panne dʼun fournisseur dʼaccès à Internet
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Deliverability
hide: true
hidefromtoc: true
exl-id: 7a9afe0a-0219-40f1-9fe2-6374db8d555c
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 100%

---

# Mettre à jour les erreurs hard incorrectes après une panne d’un FAI {#update-bounces}



## Contexte{#update-bounce-context}

En cas de panne d’un fournisseur d’accès à Internet, les emails envoyés par la biais de Campaign ne peuvent pas être correctement envoyés à leur destinataire : ils seront incorrectement marqués comme mails rebonds.

Des problèmes globaux chez Apple ou Gmail, par exemple, peuvent entraîner l’envoi de certains e-mails à des adresses e-mail Apple ou Gmail valides, mais qui seront considérés comme non valides par les serveurs du fournisseur des FAI, avec les réponses de rebond suivantes :

* « “adresse email” 550 5.1.1 : utilisateur trouvé, mais aucun enregistrement d’utilisateur trouvé. »

* « “adresse email” 550 du destinataire rejetée »

Notez que si des bounces de report affichant le message « 452 action demandée abandonnée : réessayez ultérieurement » sont observés, les envois sont automatiquement repris et aucune action n’est nécessaire. Ils devraient s’améliorer à mesure que le FAI retrouve sa pleine capacité.

>[!NOTE]
>
>Vous pouvez vérifier le tableau de bord de statut du système Apple sur [cette page](https://www.apple.com/fr/support/systemstatus/){_blank}..
>
>Vous pouvez vérifier le tableau de bord de statut de Google Workspace sur [cette page](https://www.google.com/appsstatus#hl=fr&amp;v=status){_blank}.

## Impact{#update-bounce-impact}

En cas de panne d&#39;un fournisseur d&#39;accès à Internet, les emails envoyés par la biais de Campaign ne peuvent pas être correctement envoyés à leur destinataire : ils seront incorrectement marqués comme mails rebonds.

Selon la logique standard de gestion des bounces, Adobe Campaign a automatiquement ajouté ces destinataires à la liste de quarantaine avec un **[!UICONTROL Statut]** de **[!UICONTROL Quarantaine]**. Pour corriger ce problème, vous devez mettre à jour votre table de quarantaines dans Campaign en recherchant et en supprimant ces destinataires ou en basculant leur **[!UICONTROL Statut]** sur **[!UICONTROL Valide]** afin que le processus de nettoyage de nuit les supprime.

Pour trouver les destinataires qui ont été affecté(e)s par ce problème, consultez les instructions ci-dessous.

## Processus de mise à jour{#update-bounce-update}

Vous devez exécuter une requête sur votre table de quarantaine pour filtrer tous et toutes les destinataires Apple qui ont été potentiellement affectés par la panne (par exemple, les adresses incluant @icloud.com, @me.com, @mac.com), afin qu’ils puissent être supprimés de la liste de quarantaine et inclus dans les futures diffusions d’emails de Campaign.

En fonction du calendrier de l’incident et du FAI, voici les instructions recommandées pour cette requête.

* Pour les environnements Campaign contenant des informations de règles d’e-mail entrant dans le champ **[!UICONTROL Texte d’erreur]** de la liste de quarantaine :

   * **Texte d’erreur (texte de la quarantaine)** contenant « Momen_Code10_InvalidRecipient »
   * **Domaine d’e-mail (@domain)** égal à domain1.com OU **domaine d’email (@domain)** égal à domain2.com OU **domaine d’email (@domain)** égal à domain3.com
   * **Mise à jour du statut (@lastModified)** le ou après le JJ/MM/AAAA à HH:MM:SS AM
   * **Mise à jour du statut (@lastModified)** le ou avant le JJ/MM/AAAA à HH:MM:SS PM

* Pour les environnements Campaign contenant des informations de réponse de rebond SMTP dans le champ **[!UICONTROL Texte d’erreur]** de la liste de quarantaine :

   * **Le texte d’erreur (texte de quarantaine)** contient « 550-5.1.1 » ET **Le texte d’erreur (texte de quarantaine)** contient « support.ISP.com »,

      où « ISP.com » peut être « support.apple.com » ou « support.google.com », par exemple.

   * **Mise à jour du statut (@lastModified)** le ou après le JJ/MM/AAAA à HH:MM:SS AM
   * **Mise à jour du statut (@lastModified)** le ou avant le JJ/MM/AAAA à HH:MM:SS PM


Une fois que vous disposez de la liste des destinataires concernés, vous pouvez soit leur attribuer l’état **[!UICONTROL Valide]** afin qu’ils soient supprimés de la liste de quarantaine par le processus de **[!UICONTROL nettoyage de la base de données]**, soit simplement les supprimer de la table.

**Rubriques connexes :**
* [Présentation des diffusions en échec](understanding-delivery-failures.md)
* [Qualification des emails bounce   ](understanding-delivery-failures.md#bounce-mail-qualification)
