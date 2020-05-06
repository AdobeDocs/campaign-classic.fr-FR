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
translation-type: tm+mt
source-git-commit: a1192bc804e752d13af869da66ba0505c077ed19
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 31%

---


# Démarrer une nouvelle plate-forme {#starting-new-platform}

Il est essentiel de préserver la réputation de votre domaine et de votre adresse IP lors de la configuration d’une nouvelle plateforme.

* Commencer à envoyer des courriers électroniques est une étape délicate car la plateforme n&#39;a aucun historique d&#39;utilisation et, lorsque les adresses IP d&#39;envoi n&#39;ont jamais été utilisées à cette fin, aucune réputation.

* Or rien n&#39;est plus suspect pour un FAI qu&#39;une adresse IP qui n&#39;a jamais envoyé d&#39;emails et qui commence subitement à envoyer des messages en masse. En effet, les spammeurs utilisent généralement des adresses IP &quot;inconnues&quot; (adresses qui n&#39;ont jamais été blacklistées) pour envoyer le plus grand nombre possible de messages avant leur détection.

* On ne peut donc pas espérer atteindre le régime de croisière en termes de débit dès le début de la mise en production. De surcroît on ne doit pas essayer d&#39;envoyer les premiers messages avec un tel débit, car cela conduirait les FAI à bloquer d&#39;autant plus sévèrement les adresses IP d&#39;envoi et à compromettre gravement la poursuite du démarrage.

Vous trouverez ci-dessous la liste des principaux principes à suivre lors de la création d&#39;une nouvelle plateforme :

* Si vous disposez de ces informations, **importez des adresses non valides dans la table**de quarantaine.
Le démarrage d&#39;une plateforme se produit souvent lors de l&#39;utilisation d&#39;une liste d&#39;adresses pour la première fois et qui peut ne pas être entièrement qualifiée. Si vous envoyez des messages à des adresses non valides ou à des adresses huppées, cela diminuera la réputation de la plateforme.

   * If you have a list of invalid addresses, it is in your best interests to import it into the quarantine table (available through the **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]** menu) before sending for the first times.
   * Si on souhaite malgré tout requalifier les adresses invalides, il est nettement préférable de le faire une fois la réputation de la plate-forme établie et par petites parties afin de &quot;diluer&quot; dans le temps l&#39;usage des mauvaises adresses.
   Pour plus d’informations à ce sujet, voir [Optimisation de votre diffusion par le biais de quarantaines](../../delivery/using/understanding-quarantine-management.md#optimizing-your-delivery-through-quarantines).
* **Limitez le débit** en limitant le nombre de mini-familles. Pour plus d’informations sur la modification de ce paramètre technique, contactez votre administrateur Adobe Campaign.
* **Augmentez progressivement les volumes envoyés** pour éviter d&#39;être marqués comme spam. Ne cible pas toute la base de données du début même, mais ajoutez plutôt une fraction supplémentaire de la liste à chaque envoi. Cela devrait vous permettre d&#39;augmenter le volume à chaque étape tout en réduisant le taux global d&#39;adresses non valides. Pour assurer un développement sans heurt de la phase de début vers le haut, vous pouvez utiliser le vagues. Pour plus d’informations à ce sujet, voir [Envoi de plusieurs vagues](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves).
* **Envoyez-les régulièrement**. Dans une certaine mesure, il est préférable d&#39;envoyer régulièrement des petits plans plutôt que des campagnes de grande envergure de manière sporadique.
* **Sois attentif aux rapports de diffusion**. Des indicateurs d&#39;erreur élevés peuvent signifier qu&#39;un paramètre technique est mal configuré. Voir à ce propos la section [Suivre une diffusion](../../delivery/using/monitoring-a-delivery.md).

**Rubriques connexes** :
* [Augmenter votre réputation de courriel grâce au réchauffement de l&#39;adresse IP](https://helpx.adobe.com/campaign/kb/increase-email-rep-ip-warming.html)
* [Tout sur les pièges de spam](https://helpx.adobe.com/campaign/kb/spam-traps.html)