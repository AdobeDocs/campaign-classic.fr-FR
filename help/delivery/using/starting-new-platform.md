---
title: Démarrage d’une nouvelle plateforme avec Adobe Campaign Classic
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
source-git-commit: 68756f920fbc8658cff552615adbf023b4c5e3aa

---


# Démarrer une nouvelle plate-forme {#starting-new-platform}

Le maintien de la réputation de votre domaine et de votre adresse IP est essentiel. Vous trouverez ci-dessous quelques conseils pour la configuration d&#39;une nouvelle plateforme.

Démarrer l&#39;envoi d&#39;emails sur une nouvelle plate-forme est une étape délicate car la plate-forme ne possède aucun historique d&#39;envoi, aucune réputation (dans le cas où les IP d&#39;envoi n&#39;ont jamais été utilisées à des fins d&#39;envoi d&#39;emails). Or rien n&#39;est plus suspect pour un FAI qu&#39;une adresse IP qui n&#39;a jamais envoyé d&#39;emails et qui commence subitement à envoyer des messages en masse. En effet, les spammeurs utilisent généralement des adresses IP &quot;inconnues&quot; (c&#39;est-à-dire qui n&#39;ont jamais fait l&#39;objet de blacklistage) pour envoyer un maximum de messages pendant le laps de temps où ils n&#39;ont pas encore été détectés.

On ne peut donc pas espérer atteindre le régime de croisière en termes de débit dès le début de la mise en production. De surcroît on ne doit pas essayer d&#39;envoyer les premiers messages avec un tel débit, car cela conduirait les FAI à bloquer d&#39;autant plus sévèrement les adresses IP d&#39;envoi et à compromettre gravement la poursuite du démarrage.

Le démarrage d&#39;une plate-forme peut aller de pair avec le premier usage d&#39;une liste d&#39;adresses, c&#39;est-à-dire une liste potentiellement mal qualifiée. Or l&#39;envoi à des adresses invalides ou à des adresses pièges contribue à abaisser la réputation de la plate-forme. If you have a list of invalid addresses, it is in your best interests to import it into the quarantine table (**[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**) before sending for the first times. Si on souhaite malgré tout requalifier les adresses invalides, il est nettement préférable de le faire une fois la réputation de la plate-forme établie et par petites parties afin de &quot;diluer&quot; dans le temps l&#39;usage des mauvaises adresses.

Pour résumer les principes à respecter lors d&#39;un démarrage :

* Si on dispose de l&#39;information, import des adresses invalides dans la table des quarantaines
* Limitation du débit d&#39;envoi (réglage technique : limitation du nombre de mtachilds)
* Augmentation progressive des volumes d&#39;envoi : ne pas cibler toute la base dès le début, mais à chaque envoi ajouter une fraction de plus par rapport à l&#39;envoi précédent ; cela permet d&#39;augmenter le volume à chaque étape tout en diminuant le taux d&#39;adresses invalides globalement
* Diffuser régulièrement : dans une certaine mesure il est préférable de réaliser de petits envois fréquents que des envois volumineux et sporadiques
* Surveiller de près les rapports de diffusion : un indicateur d&#39;erreur élevé peut signifier qu&#39;un paramétrage technique est mal configuré.