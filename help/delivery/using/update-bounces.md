---
product: campaign
title: Mettre à jour la qualification des rebonds après une panne d’un FAI
description: Découvrez comment mettre à jour la qualification des retours après une panne dʼun fournisseur dʼaccès à Internet
feature: Deliverability
hide: true
hidefromtoc: true
exl-id: 7a9afe0a-0219-40f1-9fe2-6374db8d555c
source-git-commit: 165797105affc9b5d4e4332f7f158031579bf91c
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 37%

---

# Mise à jour de hard bounces incorrects après une panne de FAI {#update-bounces}

![](../../assets/common.svg)

## Contexte{#update-bounce-context}

En cas de panne d’un fournisseur d’accès à Internet, les emails envoyés par la biais de Campaign ne peuvent pas être correctement envoyés à leur destinataire : ils seront incorrectement marqués comme mails rebonds.

Des problèmes globaux dans Apple ou Gmail, par exemple, peuvent entraîner l’envoi incorrect par les serveurs de FAI de certains emails envoyés à des adresses email Apple ou Gmail valides en tant qu’adresses email incorrectes rebonds par les bounces suivants :

* &quot;550 5.1.1 &#39;adresse email&#39; : succès de la recherche d’utilisateur, mais aucun enregistrement d’utilisateur trouvé.&quot;

* &quot;550 &#39;adresse email&#39; du destinataire rejeté&quot;

Notez que si le report des bounces avec le message &quot;452 request action aborted : try again later&quot; (réessayer plus tard) sont observées ; elles sont automatiquement reprises et aucune action n’est nécessaire. Ils devraient s’améliorer à mesure que le FAI récupère la pleine capacité.

>[!NOTE]
>
>Vous pouvez vérifier le tableau de bord de l’état du système Apple sur [cette page](https://www.apple.com/fr/support/systemstatus/){_blank}.
>
>Vous pouvez vérifier le tableau de bord État de l’espace de travail Google sur [cette page](https://www.google.com/appsstatus#hl=fr&amp;v=status){_blank}.

## Impact{#update-bounce-impact}

En cas de panne d&#39;un fournisseur d&#39;accès à Internet, les emails envoyés par la biais de Campaign ne peuvent pas être correctement envoyés à leur destinataire : ils seront incorrectement marqués comme mails rebonds.

Selon la logique standard de gestion des bounces, Adobe Campaign a automatiquement ajouté ces destinataires à la liste de quarantaine avec un **[!UICONTROL Statut]** de **[!UICONTROL Quarantaine]**. Pour corriger ce problème, vous devez mettre à jour votre table de quarantaines dans Campaign en recherchant et en supprimant ces destinataires ou en basculant leur **[!UICONTROL Statut]** sur **[!UICONTROL Valide]** afin que le processus de nettoyage de nuit les supprime.

Pour trouver les destinataires qui ont été affectés par ce problème, consultez les instructions ci-dessous.

## Processus de mise à jour{#update-bounce-update}

Vous devez exécuter une requête sur votre table des quarantaines pour filtrer tous les destinataires concernés (par exemple, pour Apple, les adresses qui incluent, @icloud.com, @me.com, @mac.com) qui ont été potentiellement affectés par la panne afin qu&#39;ils puissent être supprimés de la liste de quarantaine et inclus dans les prochaines diffusions email de Campaign.

En fonction du délai de l’incident et du FAI, les directives recommandées pour cette requête sont les suivantes.

* Pour les environnements Campaign avec les informations de règle de courrier électronique entrant dans la variable **[!UICONTROL Texte de l’erreur]** champ de la liste de quarantaine :

   * **Texte d&#39;erreur (texte de la quarantaine)** contenant « Momen_Code10_InvalidRecipient »
   * **Domaine de l&#39;email (@domain)** égal à domain1.com OU **Domaine de l&#39;email (@domain)** égal à domain2.com OU **Domaine de l&#39;email (@domain)** égal à domain3.com
   * **Mise à jour du statut (@lastModified)** sur ou après MM/JJ/AAAA HH:MM:SS AM
   * **Mise à jour du statut (@lastModified)** sur ou avant MM/JJ/AAAA HH:MM:SS PM

* Pour les environnements Campaign contenant les informations de réponse SMTP rebond dans **[!UICONTROL Texte de l’erreur]** champ de la liste de quarantaine :

   * **Texte de l&#39;erreur (texte des quarantaines)** contient &quot;550-5.1.1&quot; ET **Texte de l&#39;erreur (texte des quarantaines)** contient &quot;support.ISP.com&quot;

      où &quot;support.ISP.com&quot; peut être : &quot;support.apple.com&quot; ou &quot;support.google.com&quot;, par exemple

   * **Mise à jour du statut (@lastModified)** sur ou après MM/JJ/AAAA HH:MM:SS AM
   * **Mise à jour du statut (@lastModified)** sur ou avant MM/JJ/AAAA HH:MM:SS PM


Une fois que vous disposez de la liste des destinataires concernés, vous pouvez soit leur attribuer l’état **[!UICONTROL Valide]** afin qu’ils soient supprimés de la liste de quarantaine par le processus de **[!UICONTROL nettoyage de la base de données]**, soit simplement les supprimer de la table.

**Rubriques connexes :**
* [Présentation des diffusions en échec](understanding-delivery-failures.md)
* [Qualification des emails bounce   ](understanding-delivery-failures.md#bounce-mail-qualification)
