---
product: campaign
title: Détection des URL de tracking
description: En savoir plus sur le modèle recommandé pour suivre les URL
feature: Monitoring
role: User, Developer
exl-id: 7611d6a1-6c55-4ba3-b905-58426c944991
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: ht
source-wordcount: '297'
ht-degree: 100%

---

# Détection des URL de tracking

## Exemple de non-détection

`<%= getURL("http://mynewsletter.com") %>` fonctionne et envoie le contenu de la page web par email aux destinataires. Mais aucun des liens n&#39;est tracké. La raison en est que le MTA exécute `"<%=getURL(..."` pour chaque email avant de l’envoyer. Cela peut être différent pour chaque destinataire, de sorte qu’Adobe Campaign ne peut pas connaître les URL de tracking et leur attribuer un identifiant de balise.

Lorsque la page à télécharger est identique pour tous les destinataires, il est recommandé d’effectuer les opérations suivantes :

`<%@ include url="http://mynewsletter.com" %>`

Dans ce cas, la page est téléchargée pendant l’analyse, avant la détection du tracking. Adobe Campaign peut ainsi découvrir les liens, attribuer un identifiant de balise et les tracké.

## Modèle recommandé

Après avoir traité les instructions `<%@`, l’URL à tracker possède la syntaxe suivante : `<a href="http://myurl.com/a.php?param1=aaa&param2=<%=escapeUrl(recipient.xxx)%>&param3=<%=escapeUrl(recipient.xxx)%>">`

>[!IMPORTANT]
>
>Tous les autres modèles ne sont pas pris en charge par Adobe et doivent être évités afin d&#39;éviter les éventuelles lacunes en matière de sécurité.

## Modèle non sécurisé

Lorsque vous ajoutez des liens personnalisés à votre contenu, évitez toujours toute personnalisation dans la partie de nom d’hôte de l’URL afin d’éviter des failles de sécurité potentielles. En savoir plus sur [cette page](../../installation/using/privacy.md#url-personalization).

Par exemple, la syntaxe `<a href="http://<%=myURL%>">` n’est **pas sécurisée** et doit être évitée.

* L’utilisation de cette syntaxe peut entraîner des problèmes de sécurité si le lien généré par Adobe Campaign contient un ou plusieurs paramètres.
* Tidy peut incorrectement corriger certains liens, ce qui peut se produire de manière aléatoire. Le symptôme typique est une portion de code HTML visible dans les BAT d&#39;email mais pas dans la prévisualisation.
* L’échappement de l’URL est problématique, certains caractères de l’URL peuvent poser des problèmes.
* Un paramètre nommé ID ne peut pas entrer en conflit avec un paramètre dans l’URL de redirection.
* L’intérêt du tracking est alors limité aux statistiques de la diffusion, car Adobe Campaign tracke indifféremment toutes les valeurs possibles de « myURL ».
