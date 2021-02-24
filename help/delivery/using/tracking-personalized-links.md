---
solution: Campaign Classic
product: campaign
title: Commencer avec le suivi des liens personnalisés
description: Découvrez comment écrire des liens dans des courriels qui peuvent être personnalisés et prendre en charge le suivi en Campaign Classic.
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: 151667637a12667f5eda1590e64e01de493be9ce
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---


# Commencez avec le suivi des liens personnalisés {#tracking-personalized-links}

Les liens contenus dans le contenu des courriels qui contiennent la personnalisation doivent faire l’objet d’un suivi syntaxique spécifique.

L’utilisation de JavaScript dans le contenu des courriers électroniques (HTML ou Texte) vous permet de générer et d’envoyer du contenu dynamique aux destinataires, avec deux restrictions :

* Le script ne peut pas accéder directement à la base de données (la fonction SQL et les fonctions API ne sont pas disponibles),
* Adobe Campaign doit être en mesure de détecter les URL afin que les liens puissent être suivis (objectif de ce document).

Pour la détection du suivi, Adobe Campaign incorpore [Tidy](http://www.html-tidy.org/) pour analyser la source HTML et détecter le modèle. Il liste toutes les URL du contenu afin qu’elles puissent être suivies individuellement. Adobe Campaign utilise à nouveau Tidy pour remplacer l’URL (`http://myurl.com`) par une URL pointant vers le serveur de redirection Adobe Campaign.

Par exemple, dans le contenu initial : `http://myurl.com/a.php?name=<%=escapeUrl(recipient.lastName)%>` est remplacé pour un destinataire particulier par : `http://emailing.customer.com/r/?id=h617791,71ffa3,71ffa8&p1=CustomerName`

Où :

* &quot;h&quot; signifie contenu HTML (ou &quot;t&quot; pour le contenu de texte).
* 617791 est l’identifiant du message / identifiant du journal large (hexadécimal).
* 71ffa3 est l&#39;identifiant NmsDelivery (hexadécimal).
* 71ffa8 est l&#39;identifiant NmsTrackingUrl (hexadécimal).
* p1, p2, etc., sont tous les paramètres à remplacer dans l’URL.
