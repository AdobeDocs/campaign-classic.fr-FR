---
title: Points clés de la gestion de la délivrabilité dans Adobe Campaign Classic
description: Quels sont les points clés à vérifier lors de la gestion de la délivrabilité dans Adobe Campaign Classic ?
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
source-git-commit: 963aaa81971a8883b944bfcf4d1a00d729627916

---


# Points clés de la délivrabilité{#deliverability-key-points}

La délivrabilité consiste à mesurer le succès de vos campagnes dans la boîte de réception de vos destinataires sans rebondir ni être marquée comme indésirable.

Pour optimiser la délivrabilité de vos courriers électroniques Adobe Campaign, nous vous recommandons d’utiliser les meilleures pratiques répertoriées ci-dessous. Les problèmes de délivrabilité sont généralement liés aux mesures de protection contre le spam mises en oeuvre par les fournisseurs de services Internet et les administrateurs de serveurs de messagerie.

La délivrabilité des courriers électroniques désigne l&#39;ensemble des caractéristiques qui déterminent la capacité d&#39;un message à atteindre sa destination, par l&#39;intermédiaire d&#39;une adresse électronique personnelle, dans un délai court, et avec la qualité attendue en termes de contenu et de format.

Ces caractéristiques se répartissent en quatre catégories principales :
* Qualité des données
* Message et contenu
* Envoi de l&#39;infrastructure
* Réputation

Ensemble, ils forment la base d&#39;un programme de livraison de courriels réussi.

Le taux de délivrabilité est le nombre d&#39;emails envoyés qui ont été délivrés avec succès aux destinataires.

Le taux de délivrabilité dépend de nombreux facteurs et notamment :
* le bon paramétrage de vos instances
* la réputation de vos adresses IP
* la qualité des adresses ciblées
* le faible taux de plaintes
* le contenu de vos messages
* l&#39;authentification des messages (SPF, DKIM, DMARC)
* la réputation de l&#39;expéditeur

Voici une liste de points clés à vérifier pour assurer une bonne délivrabilité.

## Vérifier la configuration du réseau {#network-configuration}

Les spammeurs cherchent à cacher leur véritable identité et par conséquent rendent leurs serveurs d&#39;envoi difficilement identifiables. Une configuration réseau correcte, qui ne cherche pas à cacher d&#39;information, est un préalable à tout envoi en masse.

## Send to valid addresses {#valid-addresses}

Les spammeurs utilisent parfois des générateurs d&#39;adresses basés sur des listes de prénoms et de noms fréquents ; d&#39;autre part, ils traitent rarement les notifications techniques renvoyées par les serveurs de messagerie. Un taux d&#39;adresses invalides élevé dans une diffusion est souvent interprété comme la marque d&#39;un spammeur. Une inscription par double opt-in et une gestion rigoureuse des rebonds techniques permet d&#39;éviter cela.

## Réduire les plaintes et les taux de rebonds {#reduce-complaint-rates}

Les FAI ont systématisé la mise à disposition d&#39;une fonction &quot;Ceci est un spam&quot; pour permettre aux utilisateurs de rapporter les emails non sollicités et en déduire les envoyeurs. Une gestion honnête des demandes, une diffusion régulière sur sa liste, la vérification des inscriptions par double opt-in, la facilité de désinscription et son temps de prise en compte et surtout la mise en place de boucles de rétro-action ou &quot;feedback loop&quot; permettent de diminuer les taux de plaintes.

## Send to honeypot addresses {#honeypot-addresses}

Les FAI et d&#39;autres organisations (voir le site https://www.projecthoneypot.org/) créent des boîtes mails ne correspondant à aucune personne physique dans le but de piéger les spammeurs. Ces adresses piège ou &quot;honey pots&quot; sont publiées sur le web dans le but qu&#39;elles soient trouvées par les robots collecteurs d&#39;adresses des spammeurs et pour ainsi en déduire les expéditeurs illégitimes. Un mécanisme de double opt-in empêche totalement l&#39;ajout de ce genre d&#39;adresses. Quand on utilise une liste fournie par un tiers, il faut être sûr des méthodes employées par ce dernier.

## Adapter le contenu du message {#message-content}

Dans une moindre mesure, le contenu des messages peut amener certains filtres à détecter un spam. L&#39;emploi de certains mots, l&#39;usage de points d&#39;exclamation dans le corps ou le sujet du message doit être mesuré. Une parade temporaire des spammeurs a consisté à remplacer le texte interdit par des images dont le texte ne peut pas être examiné automatiquement par les filtres anti-spam. En réponse à cela, un message (au format HTML) contenant une trop forte proportion d&#39;images peut désormais être bloqué, de même qu&#39;un message embarquant les images en pièces-jointes.

## Travailler sur votre réputation {#reputation}

Les spammeurs font des envois ponctuels pour maintenir leur réputation dans le temps. Il est parfois nécessaire d&#39;adapter son plan marketing pour répondre aux exigences des bonnes pratiques imposées par les FAI et donc, après la phase de montée en réputation (ram-up), paramétrer des envois réguliers.