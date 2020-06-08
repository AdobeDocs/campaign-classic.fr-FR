---
title: Ajout de pièces jointes aux messages transactionnels avec Adobe Campaign Classic
description: Découvrez comment envoyer des emails transactionnels avec des pièces jointes individuelles et/ou personnalisées à l’aide d’Adobe Campaign Classic
page-status-flag: never-activated
uuid: 4452d839-318a-49d8-8abb-4ba04c803e9f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: use-case
discoiquuid: 7b8ab9d6-e47e-46d8-99df-da793486654c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 22d0e70f77eb3759632e05ab1cb0d8ee53adfac9
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 89%

---


# Cas pratique : envoi d’emails transactionnels avec des pièces jointes{#transactional-email-with-attachments}

L&#39;objectif de ce cas pratique est d&#39;ajouter des pièces jointes d&#39;emails à la volée aux envois sortants.

## Principales étapes {#key-steps}

Dans ce scénario, vous allez apprendre à envoyer des emails transactionnels avec des pièces jointes individuelles et/ou personnalisées. Les pièces jointes ne seront pas préchargées sur le serveur de messagerie transactionnelle, mais générées à la volée.

Lorsque vous capturez des interactions ou des détails sur un client, vous devrez peut-être lui renvoyer ces informations à la fin du processus, par exemple dans un fichier PDF joint à un email.

Voici les étapes générales de ce scénario :

1. Le client accède au site web et trouve le produit qu&#39;il souhaite acheter.
1. Il sélectionne le produit et personnalise certaines options.
1. Il termine la transaction.
1. Un email est envoyé au client pour confirmer la transaction. L’envoi de PII dans un email n’étant pas recommandé, un fichier PDF sécurisé est généré et joint à cet email.
1. Le client reçoit l’email et la pièce jointe contenant toutes les données nécessaires.

Dans ce scénario, les pièces jointes ne sont pas créées à l’avance, mais ajoutées à la volée aux emails sortants, avec les avantages suivants :

* Vous pouvez personnaliser le contenu de la pièce jointe.
* Si elle est associée à une transaction (comme dans l’exemple de scénario ci-dessus), elle peut contenir des données dynamiques générées pendant le processus client.
* L’ajout de fichiers PDF optimise la sécurité lorsque vous pouvez les crypter et les envoyer via HTTPS.

>[!NOTE]
>
>Pour éviter tout problème de performances, si vous incluez des images téléchargées à la volée depuis une URL personnalisée en tant que pièce jointe, chaque taille d’image ne doit pas dépasser 100 000 octets par défaut. Ce seuil recommandé peut être configuré à partir [de la liste des options](../../installation/using/configuring-campaign-options.md#delivery)Campaign Classic.

## Recommandations {#important-notes}

Avant de mettre en œuvre ce scénario, lisez attentivement les directives suivantes :

* Les instances de messagerie transactionnelle ne doivent pas être utilisées pour stocker, exporter ou charger des fichiers ou des données. Elles ne peuvent être utilisées que pour les données d’événements et les informations s’y rapportant. Elles ne doivent pas être considérées comme un système de stockage de fichiers.
* Comme il n&#39;existe aucun accès direct aux instances de messagerie transactionnelle ou aux serveurs à l&#39;extérieur d&#39;Adobe, il n&#39;y a aucun moyen standard de transférer ces fichiers sur ces serveurs (pas d&#39;accès FTP).
* D’un point de vue contractuel, il n’est pas correct d’utiliser l’espace disque sur l’instance de messagerie transactionnelle pour stocker des fichiers, quels qu’ils soient, même pour les pièces jointes.
* Pour héberger ces fichiers, vous devez utiliser un autre système de disque en ligne. Vous avez besoin d’un accès FTP à ce système et vous devez pouvoir écrire et supprimer des fichiers.

>[!NOTE]
>
>Pour éviter tout problème de performances, il est recommandé de ne pas inclure plus d’une pièce jointe par courrier électronique. Le seuil recommandé peut être configuré à partir [de la liste des options](../../installation/using/configuring-campaign-options.md#delivery)Campaign Classic.

## Mise en œuvre {#implementation}

Le diagramme suivant montre les différentes étapes pour mettre en œuvre ce scénario :

![](assets/message-center-uc1.png)

Pour ajouter à la volée une pièce jointe à un message transactionnel, procédez comme suit :

1. Commencez par créer votre pièce jointe. Voir à ce propos [cette section](../../delivery/using/attaching-files.md#attach-a-personalized-file).

   Vous pouvez ainsi joindre les fichiers à un email, même s’ils ne sont pas hébergés sur l’instance d’exécution.

1. Vous pouvez envoyer des emails via un déclencheur de message SOAP. Un appel SOAP contient un paramètre d&#39;URL (attachmentURL).

   Pour plus d&#39;informations sur les requêtes SOAP, voir la section [Description des événements](../../message-center/using/event-description.md).

1. Lors de la conception de votre email, cliquez sur **[!UICONTROL Pièce jointe]**.

1. Dans l’écran **[!UICONTROL Définition d’un fichier attaché]**, saisissez le paramètre de pièce jointe SOAP :

   ```
   <%= rtEvent.ctx.attachementUrl %>
   ```

1. Lorsque le message est traité, le système extrait le fichier de l’emplacement distant (serveur tiers) et le joint au message.

   Comme ce paramètre peut être une variable, il doit accepter la variable d&#39;URL distante entièrement formée de votre fichier, envoyée via l&#39;appel SOAP.

   ![](assets/message-center-uc2.png)
