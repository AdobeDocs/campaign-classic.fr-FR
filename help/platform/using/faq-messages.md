---
product: campaign
title: FAQ sur les tests et les envois
description: FAQ Campaign Classic
feature: Troubleshooting
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 7fc24ef2-b021-440b-b1f2-8c77e2425328
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: ht
source-wordcount: '742'
ht-degree: 100%

---

# Validation, envoi et tracking des messages {#validate-send-track}



## Tests et validation {#test-and-validate-before-sending}

Apprenez à effectuer les étapes de test et de validation avant d&#39;envoyer des messages dans Adobe Campaign.

### Qu&#39;est-ce que l&#39;analyse de la diffusion ? {#what-is-the-delivery-analysis-}

L&#39;analyse correspond à l&#39;étape de calcul de la population cible et de préparation du contenu de la diffusion. Une fois l&#39;analyse terminée, la diffusion sera prête à être envoyée. Consultez les logs pour vérifier que tout est correct.

[Pour en savoir plus, cliquez ici](../../delivery/using/steps-validating-the-delivery.md).

### Pourquoi créer des bons à tirer ? {#why-should-i-create-proofs-}

Adobe recommande vivement de créer des BAT pour tester votre diffusion auprès d’un groupe de validation avant l’envoi à la cible principale. Vous pouvez ensuite valider le contenu des messages, la personnalisation et les paramètres de la diffusion.

[Pour en savoir plus, cliquez ici](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### Comment utiliser les adresses de contrôle dans Adobe Campaign ? {#how-to-use-seed-addresses-in-adobe-campaign-}

Les adresses de contrôle permettent de cibler des destinataires qui ne correspondent pas aux critères de ciblage définis. Elles sont ajoutées à la cible : elles peuvent être importées ou créées directement au niveau de la diffusion ou de l&#39;opération. Pour les diffusions courrier, elles sont ajoutées au moment de l&#39;extraction et mixées dans le document de sortie.

Les avantages sont notamment les suivants :

* Substitution aléatoire des champs avec des données issues des profils des destinataires : vous pouvez ainsi renseigner seulement l&#39;adresse email par exemple au niveau des adresses de contrôle,
* Dans un contexte de workflow avec utilisation des fonctionnalités de Data management, les données additionnelles exploitées dans les diffusions peuvent être renseignées au niveau des adresses de contrôle afin d&#39;en forcer la valeur : on s&#39;affranchit ainsi de la substitution aléatoire des valeurs.

[Cliquez ici pour en savoir plus sur les adresses de contrôle](../../delivery/using/about-seed-addresses.md).

### Comment configurer un processus de validation avant l&#39;envoi des messages ? {#how-can-i-set-up-an-approval-process-before-sending-messages-}

Afin de détecter les éventuelles erreurs de paramétrage de vos messages, Adobe recommande vivement de mettre en place un cycle de validation de vos diffusions. Pour cela, faites-en valider le contenu autant de fois que nécessaire en envoyant des bons à tirer auprès de destinataires test. Un BAT doit être envoyé afin de valider le contenu après chaque modification.

[Pour en savoir plus, cliquez ici](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### Qu&#39;est-ce qu&#39;une règle de typologie ? {#what-is-a-typology-rule-}

Pour éviter les conflits entre les campagnes, Adobe Campaign peut tester différentes combinaisons en appliquant des règles de contrainte spécifiques. Elles permettent de s’assurer que les messages envoyés répondent le mieux possible aux attentes ou aux besoins du client, dans le respect des politiques de communication de l’entreprise.

[Pour en savoir plus, cliquez ici](../../campaign-opt/using/about-campaign-typologies.md).

## Envoyer vos messages {#send-your-messages}

Apprenez à envoyer des messages sur différents canaux avec Adobe Campaign.

### Comment envoyer des emails par vagues ? {#how-can-i-send-emails-in-waves-}

Avant d&#39;envoyer une diffusion à une population importante, vous pouvez [configurer des vagues](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves) pour répartir les envois en plusieurs lots et équilibrer la charge.

### Quelles sont les principales étapes pour créer un email dans Campaign ? {#which-are-the-key-steps-to-create-an-email-in-campaign-}

Une fois la diffusion de l’email créée et validée, vous pouvez l’envoyer. Vous pouvez choisir d’envoyer immédiatement l’email à la cible principale ou de planifier une diffusion à une date ultérieure. Au besoin, vous pouvez au préalable également estimer la population cible.

[Pour en savoir plus, cliquez ici](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### Comment planifier une diffusion ? {#how-to-schedule-a-delivery-}

Vous pouvez différer la diffusion des messages pour planifier l&#39;envoi ou pour gérer la pression commerciale afin de ne pas sur-solliciter une population.

[Pour en savoir plus, cliquez ici](../../delivery/using/steps-sending-the-delivery.md#scheduling-the-delivery-sending).

### Est-il possible d&#39;ajouter une pièce jointe aux emails ? {#can-i-add-an-attachment-to-emails-}

Avec Campaign Classic, vous pouvez ajouter des pièces jointes personnalisées à vos emails.

[Cliquez ici pour en savoir plus sur les pièces jointes aux emails](../../delivery/using/attaching-files.md).

## Effectuer un tracking de vos messages et mesurer leur impact {#track-your-messages-and-measure-their-impact}

Une fois vos messages envoyés, apprenez à suivre et mesurer leur impact avec Adobe Campaign.

### Comment configurer des liens suivis dans une diffusion d&#39;email ? {#how-can-i-configure-tracked-links-in-an-email-delivery-}

La réception des messages ainsi que l&#39;activation des liens insérés dans le contenu des messages peuvent être suivis pour chaque diffusion. Vous pouvez ainsi assurer un tracking du comportement des destinataires suite aux actions de diffusion dont ils ont été la cible.

Pour chaque URL du message, vous pouvez choisir d&#39;activer ou non le tracking, de modifier le libellé du lien et de regrouper les liens par catégories à des fins de reporting par exemple.

[Cliquez ici pour en savoir plus](../../delivery/using/about-message-tracking.md) sur la façon de suivre vos messages dans Campaign Classic.

### Où se trouvent les logs de diffusion et de tracking ? {#where-can-i-access-delivery-and-tracking-logs-}

Découvrez comment effectuer un tracking de vos diffusions et comprendre le comportement des destinataires [sur cette page](../../delivery/using/delivery-dashboard.md).

### Où obtenir des rapports de diffusion ? {#where-can-i-get-delivery-reports-}

Adobe Campaign contient un ensemble de rapports qui permettent de contrôler les diffusions et de tracker vos messages.

[Cliquez ici pour en savoir plus sur les rapports intégrés](../../reporting/using/delivery-reports.md).

### Comment Adobe Campaign qualifie-t-il et gère-t-il les adresses en quarantaine ? {#how-does-adobe-campaign-qualify-and-manage-quarantine-addresses-}

Adobe Campaign gère une liste d&#39;adresses en quarantaine. Les destinataires dont l&#39;adresse est en quarantaine sont par défaut exclus lors de l&#39;analyse d&#39;une diffusion : ils ne seront pas ciblés. Une adresse email peut être mise en quarantaine par exemple lorsque la boîte de messagerie est pleine ou si l&#39;adresse n&#39;existe pas.

[Cliquez ici pour en savoir plus sur la gestion des quarantaines](../../delivery/using/understanding-quarantine-management.md).
