---
title: Démarrage d’une nouvelle plate-forme avec Adobe Campaign Classic
description: En savoir plus sur la gestion de la délivrabilité lors du démarrage d’une nouvelle plateforme avec Adobe Campaign Classic.
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
translation-type: ht
source-git-commit: a1192bc804e752d13af869da66ba0505c077ed19
workflow-type: ht
source-wordcount: '499'
ht-degree: 100%

---


# Démarrer une nouvelle plate-forme {#starting-new-platform}

Il est essentiel de préserver la réputation de votre domaine et de votre adresse IP lors de la configuration d’une nouvelle plate-forme.

* Commencer l’envoi d’emails est une étape délicate, car la plate-forme ne possède ni historique d’envoi, ni réputation, lorsque les adresses IP d’envoi n’ont jamais été utilisées pour des emails.

* Or rien n&#39;est plus suspect pour un FAI qu&#39;une adresse IP qui n&#39;a jamais envoyé d&#39;emails et qui commence subitement à envoyer des messages en masse. En effet, les spammeurs utilisent généralement des adresses IP « inconnues » (qui n’ont jamais fait l’objet de blacklistage) pour envoyer un maximum de messages pendant le laps de temps où ils n’ont pas encore été détectés.

* On ne peut donc pas espérer atteindre le régime de croisière en termes de débit dès le début de la mise en production. De surcroît on ne doit pas essayer d&#39;envoyer les premiers messages avec un tel débit, car cela conduirait les FAI à bloquer d&#39;autant plus sévèrement les adresses IP d&#39;envoi et à compromettre gravement la poursuite du démarrage.

Vous trouverez ci-dessous la liste des principes essentiels applicables lors du démarrage d’une nouvelle plate-forme :

* Si vous disposez de ces informations, **importez des adresses non valides dans la table des quarantaines**.
Le démarrage d’une plate-forme s’accompagne souvent de l’utilisation d’une liste d’adresses inconnues jusqu’ici, qui n’est pas entièrement qualifiée. L’envoi de messages à des adresses non valides ou à des adresses servant de leurres contribuera à affaiblir la réputation de la plate-forme.

   * S’il existe une liste d’adresses non valides, il est préférable de l’importer dans la table des quarantaines (**[!UICONTROL Administration > Gestion de campagne > Gestion des NP@I > NP@I et Adresses]**) avant de réaliser les premiers envois.
   * Si on souhaite malgré tout requalifier les adresses invalides, il est nettement préférable de le faire une fois la réputation de la plate-forme établie et par petites parties afin de &quot;diluer&quot; dans le temps l&#39;usage des mauvaises adresses.
   Pour plus d’informations à ce sujet, voir la section [Optimisation de votre diffusion par le biais de quarantaines](../../delivery/using/understanding-quarantine-management.md#optimizing-your-delivery-through-quarantines).
* **Limitez le débit** en limitant le nombre de mtachilds. Pour plus d’informations sur la modification de ce paramètre technique, contactez votre administrateur Adobe Campaign.
* **Augmentez progressivement les volumes envoyés** pour éviter que les emails soient marqués comme spam. Ne ciblez pas l’ensemble de la base de données dès le début, mais ajoutez plutôt une partie supplémentaire de la liste à chaque envoi. Vous devriez ainsi pouvoir augmenter le volume à chaque étape tout en réduisant le taux global d’adresses non valides. Pour un développement fluide de la phase de démarrage, vous pouvez utiliser des vagues. Pour plus d’informations à ce sujet, voir la section [Envoyer en plusieurs vagues](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves).
* **Effectuez régulièrement des envois**. Dans une certaine mesure, il est préférable de réaliser de petits envois fréquents plutôt que des envois volumineux et sporadiques.
* **Accordez de l’attention aux rapports de diffusion**. La présence d’indicateurs d’erreur élevés peut révéler un paramètre technique mal configuré. Voir à ce propos la section [Suivre une diffusion](../../delivery/using/monitoring-a-delivery.md).

**Rubriques connexes** :
* [Augmentez la réputation de vos emails grâce au rodage des adresses IP](https://helpx.adobe.com/campaign/kb/increase-email-rep-ip-warming.html)
* [En savoir plus sur les pièges anti-spam](https://helpx.adobe.com/campaign/kb/spam-traps.html)