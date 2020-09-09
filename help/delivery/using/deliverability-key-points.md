---
title: Points clés de la gestion de la délivrabilité dans Adobe Campaign Classic
description: Quels sont les points clés à vérifier lors de la gestion de la délivrabilité dans Adobe Campaign Classic ?
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
source-git-commit: 24d2dded38ddb922891a7264d9efea02cb448323
workflow-type: ht
source-wordcount: '623'
ht-degree: 100%

---


# Points clés de la délivrabilité{#deliverability-key-points}

Afin d’optimiser la délivrabilité de vos emails Adobe Campaign, nous vous recommandons de suivre les bonnes pratiques répertoriées ci-dessous. Les problèmes de délivrabilité sont généralement liés à des mesures de protection contre les spams mises en place par les fournisseurs d’accès à internet et les administrateurs de serveurs de messagerie.

**La délivrabilité des emails désigne l’ensemble des caractéristiques qui déterminent la capacité d’un message à atteindre sa destination, par l’intermédiaire d’une adresse email personnelle, dans un délai court, et avec la qualité attendue en termes de contenu et de format.**

Ces caractéristiques appartiennent à quatre catégories principales :
* Qualité des données
* Message et contenu
* Infrastructure d’envoi
* Réputation

Ensemble, ils forment la base d’un programme de délivrabilité des emails réussi.

Le **taux de délivrabilité** est le nombre d’emails envoyés qui ont été délivrés avec succès aux destinataires.

Le taux de délivrabilité dépend de nombreux facteurs et notamment :
* le bon paramétrage de vos instances
* la réputation de vos adresses IP
* la qualité des adresses ciblées
* le faible taux de plaintes
* le contenu de vos messages
* l&#39;authentification des messages (SPF, DKIM, DMARC)
* la réputation de l&#39;expéditeur

La liste de points clés à vérifier ci-dessous permet d’assurer une bonne délivrabilité.

## Vérification de la configuration réseau {#network-configuration}

Les spammeurs cherchent à cacher leur véritable identité et par conséquent rendent leurs serveurs d&#39;envoi difficilement identifiables. Une configuration réseau correcte, qui ne cherche pas à cacher d&#39;information, est un préalable à tout envoi en masse.

## Envoi à des adresses valides {#valid-addresses}

Les spammeurs utilisent parfois des générateurs d&#39;adresses basés sur des listes de prénoms et de noms fréquents ; d&#39;autre part, ils traitent rarement les notifications techniques renvoyées par les serveurs de messagerie. Un taux d&#39;adresses invalides élevé dans une diffusion est souvent interprété comme la marque d&#39;un spammeur. Une inscription par double opt-in et une gestion rigoureuse des rebonds techniques permet d&#39;éviter cela.

## Réduction des plaintes et des taux de rebonds {#reduce-complaint-rates}

Les FAI ont systématisé la mise à disposition d&#39;une fonction &quot;Ceci est un spam&quot; pour permettre aux utilisateurs de rapporter les emails non sollicités et en déduire les envoyeurs. Une gestion honnête des demandes, une diffusion régulière sur sa liste, la vérification des inscriptions par double opt-in, la facilité de désinscription et son temps de prise en compte et surtout la mise en place de boucles de rétro-action ou &quot;feedback loop&quot; permettent de diminuer les taux de plaintes.

## Envoi à des adresses pièges {#honeypot-addresses}

Les FAI et d’autres organisations (voir le site web [Project Honey Pot](https://www.projecthoneypot.org/)) créent des boîtes mails ne correspondant à aucune personne physique dans le but de piéger les spammeurs. Ces adresses piège ou &quot;honey pots&quot; sont publiées sur le web dans le but qu&#39;elles soient trouvées par les robots collecteurs d&#39;adresses des spammeurs et pour ainsi en déduire les expéditeurs illégitimes. Un mécanisme de double opt-in empêche totalement l&#39;ajout de ce genre d&#39;adresses. Quand on utilise une liste fournie par un tiers, il faut être sûr des méthodes employées par ce dernier.

## Adaptation du contenu du message {#message-content}

Dans une moindre mesure, le contenu des messages peut amener certains filtres à détecter un spam. L&#39;emploi de certains mots, l&#39;usage de points d&#39;exclamation dans le corps ou le sujet du message doit être mesuré. Une parade temporaire des spammeurs a consisté à remplacer le texte interdit par des images dont le texte ne peut pas être examiné automatiquement par les filtres anti-spam. En réponse à cela, un message (au format HTML) contenant une trop forte proportion d&#39;images peut désormais être bloqué, de même qu&#39;un message embarquant les images en pièces-jointes.

## Travail sur la réputation {#reputation}

Les spammeurs font des envois ponctuels pour maintenir leur réputation dans le temps. Il est parfois nécessaire d&#39;adapter son plan marketing pour répondre aux exigences des bonnes pratiques imposées par les FAI et donc, après la phase de montée en réputation (ram-up), paramétrer des envois réguliers.

## Bonnes pratiques {#best-practices}

Découvrez les meilleures pratiques en matière de délivrabilité avec Adobe Campaign. Utilisez les liens ci-dessous pour parcourir les rubriques et trouver des conseils.

<table>
<tr>
  <td>
    <a href="starting-new-platform.md">
      <img alt="Démarrer" src="assets/do-not-localize/start.svg" width="60px"/>
    </a>
    <div>
      <a href="starting-new-platform.md">
    <strong>Début</strong>
    </a>
    </div>
    <p>
    <em>Démarrer une nouvelle plate-forme</em>
    <p>
  </td>
   <td>
    <a href="control-message-content.md">
      <img alt="Conception" src="assets/do-not-localize/design.svg" width="60px"/>
    </a>
    <div>
      <a href="control-message-content.md">
    <strong>Conception</strong>
    </a>
    </div>
    <p>
    <em>Contrôler le contenu du message</em>
    <p>
  </td>
  <td>
    <a href="improve-reputation.md">
      <img alt="Conception" src="assets/do-not-localize/check.svg" width="60px"/>
    </a>
    <div>
      <a href="improve-reputation.md">
    <strong>Envoyer</strong>
    </a>
    </div>
    <p>
    <em>Améliorez votre réputation</em>
    <p>
  </td>
</tr>
<tr>
  <td>
    <a href="technical-recommendations.md">
      <img alt="Optimisation" src="assets/do-not-localize/optimize.svg" width="60px"/>
    </a>
    <div>
      <a href="technical-recommendations.md">
    <strong>Optimiser</strong>
    </a>
    </div>
    <p>
    <em>Recommandations techniques</em>
    <p>
  </td>
   <td>
    <a href="monitoring-deliverability.md">
      <img alt="Vérifier" src="assets/do-not-localize/monitor.svg" width="60px"/>
    </a>
    <div>
      <a href="monitoring-deliverability.md">
    <strong>Surveiller</strong>
    </a>
    </div>
    <p>
    <em>Outils de monitoring</em>
    <p>
  </td>
  <td>
    <a href="deliverability-faq.md">
      <img alt="Optimisation" src="assets/do-not-localize/troubleshoot.svg" width="60px"/>
    </a>
    <div>
      <a href="deliverability-faq.md">
    <strong>Résolution des problèmes</strong>
    </a>
    </div>
    <p>
    <em>Résoudre les problèmes</em>
    <p>
  </td>
</tr>
</table>
