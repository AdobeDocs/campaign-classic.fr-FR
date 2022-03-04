---
product: campaign
title: Prise en main du tracking des liens personnalisés
description: Découvrez comment écrire des liens dans des emails qui peuvent être personnalisés et prendre en charge le tracking dans Campaign Classic.
feature: Personalization
exl-id: d0e00b40-e7dd-4484-b37c-fd3f3ac70fda
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 100%

---

# Prise en main du tracking des liens personnalisés {#tracking-personalized-links}

![](../../assets/common.svg)

Les liens inclus dans le contenu des emails qui comportent des éléments de personnalisation ont besoin d&#39;une syntaxe spécifique pour être suivis.

L’utilisation de JavaScript dans le contenu des emails (HTML ou Texte) vous permet de générer et d&#39;envoyer du contenu dynamique aux destinataires, avec deux restrictions :

* Le script ne peut pas accéder directement à la base de données (la fonction SQL et les fonctions API ne sont pas disponibles),
* Adobe Campaign doit être en mesure de détecter les URL afin que les liens puissent être suivis. [En savoir plus](detecting-tracking-urls.md)

Vous pouvez ajouter des instructions de pré-traitement spécifiques pour effectuer le script et le suivi de l’URL. [En savoir plus](pre-processing-instructions.md)

Pour la détection du tracking, Adobe Campaign incorpore [Tidy](https://www.html-tidy.org/) pour analyser la source HTML et détecter le modèle. Il répertorie toutes les URL du contenu afin qu’elles puissent être suivies individuellement. Adobe Campaign utilise à nouveau Tidy pour remplacer l&#39;URL (`http://myurl.com`) par une URL pointant vers le serveur de redirection d&#39;Adobe Campaign.

Par exemple, dans le contenu initial : `http://myurl.com/a.php?name=<%=escapeUrl(recipient.lastName)%>` est remplacé pour un destinataire particulier par : `http://emailing.customer.com/r/?id=h617791,71ffa3,71ffa8&p1=CustomerName`

Où :

* « h » signifie du contenu HTML (ou « t » pour le contenu texte).
* 617791 correspond à l&#39;identifiant du message/identifiant du broadLog (hexadécimal).
* 71ffa3 correspond à l&#39;identifiant NmsDelivery (hexadécimal).
* 71ffa8 correspond à l&#39;identifiant NmsTrackingUrl (hexadécimal).
* p1, p2, etc., sont tous les paramètres à remplacer dans l&#39;URL.
