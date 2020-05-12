---
title: Ajout de pièces jointes aux messages transactionnels avec Adobe Campaign Classic
description: Découvrez comment envoyer des e-mails transactionnels avec des pièces jointes individuelles et/ou personnalisées à l’aide d’Adobe Campaign Classic
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
source-git-commit: 24a50fcaad4d9081e5504652eb5b73aa7db1e65f
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 24%

---


# Cas d’utilisation : Envoi de courriers électroniques transactionnels avec des pièces jointes{#transactional-email-with-attachments}

L&#39;objectif de ce cas pratique est d&#39;ajouter des pièces jointes d&#39;emails à la volée aux envois sortants.

## Principales étapes {#key-steps}

Dans ce scénario, vous apprendrez à envoyer des e-mails transactionnels avec des pièces jointes individuelles et/ou personnalisées. Les pièces jointes ne seront pas préchargées sur le serveur de messagerie transactionnelle : au lieu de cela, ils seront générés à la volée.

Lorsque vous capturez les interactions ou les détails des clients, vous devrez peut-être renvoyer ces informations au client à la fin du processus, par exemple dans un fichier PDF joint à un courrier électronique.

Voici les principales étapes de ce scénario :

1. Le client accède au site web et trouve le produit qu&#39;il souhaite acheter.
1. Il sélectionne le produit et personnalise certaines options.
1. Il termine la transaction.
1. Un courrier électronique est envoyé au client pour confirmer la transaction. Etant donné qu’il n’est pas recommandé d’envoyer des informations d’identification personnelle dans le courrier électronique, un fichier PDF sécurisé est généré et joint au courrier électronique.
1. Le client reçoit le courrier électronique et sa pièce jointe contenant les données pertinentes.

Dans ce scénario, les pièces jointes ne sont pas créées à l’avance, mais ajoutées à la volée aux courriers électroniques sortants, ce qui offre les avantages suivants :

* Cela vous permet de personnaliser le contenu de la pièce jointe.
* Si la pièce jointe est associée à une transaction (comme dans l&#39;exemple de scénario décrit ci-dessus), elle peut contenir des données dynamiques générées pendant le processus client.
* L’ajout de fichiers PDF optimise la sécurité lorsque vous pouvez les chiffrer et les envoyer via HTTPS.

## Recommandations {#important-notes}

Avant de mettre en oeuvre ce scénario, lisez attentivement les directives ci-dessous :

* Les instances de messagerie transactionnelle ne doivent pas être utilisées pour stocker, exporter ou télécharger des fichiers ou des données. Ils ne peuvent être utilisés que pour les données de événement et les informations connexes. Ils ne doivent pas être considérés comme un système d&#39;enregistrement de fichiers.
* Comme il n&#39;existe aucun accès direct aux instances de messagerie transactionnelle ou aux serveurs à l&#39;extérieur d&#39;Adobe, il n&#39;y a aucun moyen standard de transférer ces fichiers sur ces serveurs (pas d&#39;accès FTP).
* Il n&#39;est pas correct par contrat d&#39;utiliser l&#39;espace disque sur les instances de messagerie transactionnelle pour stocker des fichiers de n&#39;importe quel type, pas même pour les pièces jointes.
* Vous devez utiliser un autre système de disque en ligne pour héberger ces fichiers. Vous avez besoin d&#39;un accès FTP à ce système et vous devez pouvoir écrire et supprimer des fichiers.

## Mise en oeuvre {#implementation}

Le diagramme ci-dessous montre les différentes étapes de la mise en oeuvre de ce scénario :

![](assets/message-center-uc1.png)

Pour ajouter une pièce jointe à un message transactionnel à la volée, procédez comme suit :

1. Début en concevant votre pièce jointe. Voir à ce propos [cette section](../../delivery/using/attaching-files.md#attach-a-personalized-file).

   Cela vous permet de joindre les fichiers à un courrier électronique, même s’ils ne sont pas hébergés sur l’instance d&#39;exécution.

1. Vous pouvez envoyer des emails via un déclencheur de message SOAP. Un appel SOAP contient un paramètre d&#39;URL (attachmentURL).

   Pour plus d&#39;informations sur les requêtes SOAP, voir la section [Description des événements](../../message-center/using/event-description.md).

1. Lors de la conception de votre courrier électronique, cliquez sur **[!UICONTROL Pièce jointe]**.

1. Dans l’écran Définition **[!UICONTROL de la]** pièce jointe, saisissez le paramètre de pièce jointe SOAP :

   ```
   <%= rtEvent.ctx.attachementUrl %>
   ```

1. Une fois le message traité, le système obtient le fichier à partir de l&#39;emplacement distant (serveur tiers) et le joint au message individuel.

   Comme ce paramètre peut être une variable, il doit accepter la variable d&#39;URL distante entièrement formée de votre fichier, envoyée via l&#39;appel SOAP.

   ![](assets/message-center-uc2.png)
