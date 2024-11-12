---
product: campaign
title: Vérification avant envoi
description: Une fois que votre message est prêt, effectuez toutes les vérifications avant de l’envoyer.
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
feature: Deliverability
role: User
hide: true
hidefromtoc: true
exl-id: 50d326b0-3c23-4dbf-9df6-d32b48e30f69
source-git-commit: aa78a51ebea49f98ef7edad7e87a99a680f02b69
workflow-type: tm+mt
source-wordcount: '911'
ht-degree: 100%

---

# Effectuer toutes les vérifications avant d’envoyer {#perform-all-checks}

Une fois que votre message est prêt, vérifiez que le contenu s&#39;affiche correctement sur tous les appareils et qu&#39;il ne contient aucune erreur, comme des liens rompus ou une personnalisation incorrecte.

Avant d’envoyer votre message, vérifiez également que les paramètres et la configuration sont cohérents par rapport à la diffusion.

## Pourquoi la validation est-elle essentielle ?  {#validation-is-key}

Avant d&#39;envoyer une diffusion, vous devez vous assurer que vos destinataires recevront le message que vous souhaitez réellement leur envoyer. Pour cela, vous devez valider le contenu du message et les paramètres de diffusion.

Cette étape vous permet de détecter les éventuelles erreurs et de les corriger avant l’envoi à la cible principale.

Les étapes de validation d&#39;une diffusion sont présentées [dans cette section](steps-validating-the-delivery.md).

## Inbox rendering {#inbox-and-email-rendering}

L&#39;inbox rendering vous permet de prévisualiser vos messages sur les principaux clients de messagerie, de surveiller le contenu et votre réputation, et de découvrir comment les destinataires lisent vos messages.

**Conseils** :

* Vous pouvez visualiser l&#39;affichage du message envoyé dans les différents contextes de réception : webmail, service de messagerie, mobile, etc.

* Les fonctionnalités d’inbox rendering sont essentielles pour déterminer si vos campagnes par e-mail réussissent à passer les filtres des principaux FAI et des services webmail. Les outils de ce type envoient une copie de vérification d’un e-mail à un réseau de boîtes de réception de test pour que vous puissiez voir comment le message s’affichera à travers ces différents services. Ils peuvent également inclure des rapports et des options de correction de code qui vous permettent d’identifier rapidement les problèmes et de les corriger afin d’améliorer la délivrabilité.

En savoir plus [dans cette section](inbox-rendering.md).

## Messages de BAT {#proof-messages}

L&#39;envoi de BAT permet de vérifier le lien de désinscription (opt-out), la page miroir et d&#39;autres liens, de valider le message, de vérifier le bon affichage des images, de détecter les erreurs possibles, etc. Vous souhaiterez peut-être également vérifier votre conception et le rendu sur différents appareils.

En savoir plus à ce sujet dans [cette section](steps-validating-the-delivery.md#sending-a-proof).

## Configurer des diffusions avec test A/B {#a-b-testing-deliveries}

Si vous disposez de plusieurs contenus pour une diffusion email, vous pouvez utiliser des tests A/B pour déterminer quelle version aura le plus d&#39;impact sur la population ciblée.

**Conseils** :

* Envoyez les différentes versions à une partie de vos destinataires.

* Choisissez la version qui a eu le plus de succès et envoyez-la au reste de vos destinataires.

En savoir plus à ce sujet dans [cette section](get-started-a-b-testing.md).

## Vérifiez que votre message est bien délivré.  {#make-sure-your-message-is-delivered}

En dernier lieu, tirez parti des fonctionnalités d’Adobe Campaign Classic et augmentez les chances que votre message soit délivré aux bons destinataires.

### Suivre un processus de validation

Vous pouvez définir un processus de validation complet, impliquant des opérateurs et des groupes Adobe Campaign, afin de valider la cible et le contenu du message. Cela assurera une surveillance et un contrôle complet des différents traitements de l&#39;opération : ciblage, contenu, budget, extraction et envoi d&#39;un BAT. En fonction de leurs autorisations, les utilisateurs seront avertis, ils recevront les BAT et ils pourront valider ou refuser le message. En savoir plus à ce sujet dans [cette section](../../campaign/using/marketing-campaign-approval.md).

### Utiliser des vagues

Vous pouvez augmenter progressivement le volume envoyé à l&#39;aide de vagues. Cela évitera que les emails soient marqués comme spam ou pour limiter le nombre de messages par jour. Grâce aux vagues, vous pouvez répartir les envois en plusieurs lots au lieu d’envoyer de gros volumes de messages en même temps. En savoir plus à ce sujet dans [cette section](steps-sending-the-delivery.md#sending-using-multiple-waves).

### Définir la priorité des messages

Vous pouvez définir l&#39;ordre d&#39;envoi de vos diffusions en indiquant leur niveau de priorité. Pour ce faire :

1. Modifiez les propriétés de la diffusion et sélectionnez l&#39;onglet **[!UICONTROL Diffusion]**.

1. Définissez le niveau de priorité de la diffusion sur une échelle allant de **[!UICONTROL Très basse]** à **[!UICONTROL Très haute]**.

>[!NOTE]
>
>Il n&#39;est pas possible de définir l&#39;ordre d&#39;envoi des messages au sein d&#39;une diffusion.

### Configurer les affinités IP

Pour mieux contrôler le trafic SMTP sortant, vous pouvez gérer les affinités en définissant les adresses IP spécifiques pouvant être utilisées avec chaque affinité. Ainsi, il est possible de limiter l’envoi d’emails pour des diffusions spécifiques, vers certaines machines ou adresses de sortie. Vous pouvez, par exemple, utiliser une affinité par pays ou sous-domaine. Vous pouvez ensuite créer une typologie par pays et associer chaque affinité à la typologie correspondante.

Vous pouvez ainsi :

* Définir les affinités IP dans le fichier de configuration serverConf.xml. [En savoir plus](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities)

* Pour chaque élément IPAffinity, déclarer les adresses IP qui peuvent être utilisées. [En savoir plus](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

* Dans la [typologie](../../campaign-opt/using/about-campaign-typologies.md) de votre choix, utiliser le champ **[!UICONTROL Gestion des affinités avec les adresses IP]** pour associer les diffusions vers le serveur de diffusion (MTA) qui gère l’affinité en question. [En savoir plus](../../campaign-opt/using/applying-rules.md#control-outgoing-smtp-traffic).

* Une fois que l&#39;email a été envoyé, contrôler l&#39;en-tête pour vérifier l&#39;adresse IP à partir de laquelle la diffusion a été envoyée. L&#39;administrateur de messagerie peut vous aider à obtenir les informations d&#39;en-tête.

* Pour les diffusions SMS, assurez-vous que le canal SMS a une affinité dédiée limitée à **un** conteneur du serveur d’applications. [En savoir plus](../../installation/using/configure-delivery-settings.md#managing-outbound-smtp-traffic-with-affinities)

>[!NOTE]
>
>La plupart de ces étapes ne peuvent être effectuées que par un utilisateur expert.

### Utiliser des typologies

Vous pouvez utiliser des règles de typologie pour exclure une partie de la cible en fonction de critères spécifiques. Elles permettent de s’assurer que les messages envoyés répondent le mieux possible aux attentes ou aux besoins du client, dans le respect des politiques de communication de l’entreprise. Vous pouvez, par exemple, filtrer les destinataires mineurs du public cible de votre newsletter. En savoir plus [dans cet exemple](../../campaign-opt/using/filtering-rules.md).

### Éviter les pièces jointes

Les pièces jointes restent l’un des vecteurs les plus courants de la prolifération des logiciels malveillants, surtout lorsqu’elles sont envoyées en masse. Incluez un lien sécurisé vers le document au lieu de le joindre au message. Une couche de sécurité supplémentaire est ainsi garantie pour empêcher toute redistribution involontaire. De plus, les risques que le message soit rejeté au niveau des passerelles de messagerie entrantes pour des raisons de taille ou de sécurité sont considérablement réduits.
