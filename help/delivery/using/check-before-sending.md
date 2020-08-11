---
title: Vérifier avant envoi
seo-title: Vérifier avant envoi
page-status-flag: never-activated
uuid: a540efc7-105d-4c7f-a2ee-ade4d22b3445
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
discoiquuid: 0cbc4e92-482f-4dac-a1fb-b738e7127938
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 5e6ecd636ee0b2199808c03b2fd898a194f0c1ea
workflow-type: tm+mt
source-wordcount: '874'
ht-degree: 75%

---


# Effectuer toutes les vérifications avant d’envoyer {#perform-all-checks}

Une fois que votre message est prêt, vérifiez que le contenu s&#39;affiche correctement sur tous les appareils et qu&#39;il ne contient aucune erreur, comme des liens rompus ou une personnalisation incorrecte.

Avant d’envoyer votre message, vérifiez également que les paramètres et la configuration sont cohérents par rapport à la diffusion.

## Pourquoi la validation est-elle essentielle ? {#validation-is-key}

Avant d&#39;envoyer une diffusion, vous devez vous assurer que vos destinataires recevront le message que vous souhaitez réellement leur envoyer. Pour cela, vous devez valider le contenu du message et les paramètres de diffusion.

Cette étape vous permet de détecter les éventuelles erreurs et de les corriger avant l’envoi à la cible principale.

Les étapes de validation d&#39;une diffusion sont présentées [dans cette section](../../delivery/using/steps-validating-the-delivery.md).

## Inbox rendering {#inbox-and-email-rendering}

L&#39;inbox rendering vous permet de prévisualiser vos messages sur les principaux clients de messagerie, de surveiller le contenu et votre réputation, et de découvrir comment les destinataires lisent vos messages.

**Conseils**:

* Vous pouvez visualiser l&#39;affichage du message envoyé dans les différents contextes de réception : webmail, service de messagerie, mobile, etc.

* Les fonctionnalités d&#39;inbox rendering sont essentielles pour déterminer si vos campagnes email réussissent à passer les filtres des principaux FAI et des services webmail. Les outils de ce type envoient une copie de vérification d&#39;un email à un réseau de boîtes de réception de test pour que vous puissiez voir comment le message s&#39;affichera à travers ces différents services. Ils peuvent également inclure des rapports et des options de correction de code qui vous permettent d&#39;identifier rapidement les problèmes et de les corriger afin d&#39;améliorer la délivrabilité.

Learn more [in this section](../../delivery/using/inbox-rendering.md).

## Messages de BAT {#proof-messages}

L&#39;envoi de BAT permet de vérifier le lien de désinscription (opt-out), la page miroir et d&#39;autres liens, de valider le message, de vérifier le bon affichage des images, de détecter les erreurs possibles, etc. Vous souhaitez peut-être également vérifier votre conception et le rendu sur différents appareils.

Learn more [in this section](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

## Configurer des diffusions avec test A/B {#a-b-testing-deliveries}

Si vous disposez de plusieurs contenus pour une diffusion email, vous pouvez utiliser des tests A/B pour déterminer quelle version aura le plus d&#39;impact sur la population ciblée.

**Conseils**:

* Envoyez les différentes versions à une partie de vos destinataires

* Choisissez la version qui a eu le plus de succès et envoyez-la au reste de vos destinataires

Learn more [in this section](../../workflow/using/a-b-testing.md).

## Vérifiez que votre message est bien délivré {#make-sure-your-message-is-delivered}

En dernier lieu, tirez parti des fonctionnalités d’Adobe Campaign Classic et augmentez les chances que votre message soit délivré aux bons destinataires.

### Suivre un processus de validation

Vous pouvez définir un processus de validation complet, impliquant des opérateurs et des groupes Adobe Campaign, afin de valider la cible et le contenu du message. Cela permettra d&#39;assurer un suivi et un contrôle complets des divers processus de la campagne : ciblage, contenu, budget, extraction et envoi d’un BAT. En fonction de leurs permissions, les utilisateurs seront avertis, ils recevront les BAT et ils pourront valider ou refuser le message. Learn more [in this section](../../campaign/using/marketing-campaign-approval.md#approval-process).

### Utiliser des vagues

Vous pouvez augmenter progressivement le volume envoyé à l&#39;aide de vagues. Vous éviterez ainsi que vos messages ne soient signalés comme étant des messages indésirables ou que vous souhaitiez limiter le nombre de messages par jour. Grâce aux vagues, vous pouvez répartir les envois en plusieurs lots au lieu d’envoyer de gros volumes de messages en même temps. Learn more [in this section](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves).

### Définir la priorité des messages

Vous pouvez définir l&#39;ordre d&#39;envoi de vos diffusions en indiquant leur niveau de priorité. Pour ce faire :

1. Editez les propriétés de la diffusion et sélectionnez l&#39;onglet **[!UICONTROL Diffusion]**.

1. Définissez le niveau de priorité de la diffusion sur une échelle allant de **[!UICONTROL Très basse]** à **[!UICONTROL Très haute]**.

>[!NOTE]
>
>Il n&#39;est pas possible de définir l&#39;ordre d&#39;envoi des messages à partir d&#39;une diffusion.

### Configuration des Affinités IP

Pour mieux contrôler le trafic SMTP sortant, vous pouvez gérer les affinités en définissant les adresses IP spécifiques pouvant être utilisées avec chaque affinité. Ainsi, il est possible de limiter l’envoi d’emails pour des diffusions spécifiques, vers certaines machines ou adresses de sortie. Vous pouvez, par exemple, utiliser une affinité par pays ou sous-domaine. Vous pouvez ensuite créer une typologie par pays et associer chaque affinité à la typologie correspondante.

Vous pouvez ainsi :

* Définissez les affinités IP dans le fichier de configuration serverConf.xml. [En savoir plus](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities)

* Pour chaque élément IPAfinity, déclarez les adresses IP qui peuvent être utilisées. [En savoir plus](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

* In the [typology](../../campaign/using/about-campaign-typologies.md) of your choice, use the **[!UICONTROL Managing affinities with IP addresses]** field to link deliveries to the delivery server (MTA) which manages the said affinity. [En savoir plus](../../campaign/using/applying-rules.md#control-outgoing-smtp-traffic).

* Une fois que l&#39;email a été envoyé, contrôlez l&#39;en-tête pour vérifier l&#39;adresse IP à partir de laquelle la diffusion a été envoyée. L&#39;administrateur de messagerie peut vous aider à obtenir les informations d&#39;en-tête.

>[!NOTE]
>
>La plupart de ces étapes ne peuvent être effectuées que par un utilisateur expert.

### Utiliser des typologies

Vous pouvez utiliser des règles de typologie pour exclure une partie de la cible en fonction de critères spécifiques. Elles permettent de s’assurer que les messages envoyés répondent le mieux possible aux attentes ou aux besoins du client, dans le respect des stratégies de communication de l’entreprise. Vous pouvez, par exemple, filtrer les destinataires mineurs du public cible de votre newsletter. En savoir plus [dans cet exemple](../../campaign/using/filtering-rules.md).

### Eviter les pièces jointes

Les pièces jointes restent l’un des vecteurs les plus courants de la prolifération des logiciels malveillants, surtout lorsqu’elles sont envoyées en masse. Incluez un lien sécurisé vers le document au lieu de le joindre au message. Ceci garantit une couche supplémentaire de sécurité afin d’éviter une redistribution involontaire, et réduit considérablement les risques que le message soit rejeté sur les passerelles de messagerie entrantes pour des raisons de taille ou de sécurité du message.
