---
title: Définir l’audience appropriée
seo-title: Définir l’audience appropriée
page-status-flag: never-activated
uuid: a540efc7-105d-4c7f-a2ee-ade4d22b3445
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
discoiquuid: 0cbc4e92-482f-4dac-a1fb-b738e7127938
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 5e6ecd636ee0b2199808c03b2fd898a194f0c1ea
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 52%

---


# Définir l’audience appropriée {#define-the-right-audience}

La population ciblée est essentielle : créez soigneusement vos listes, testez vos emails sur les clients de messagerie et les appareils mobiles les plus utilisés et vérifiez que vos listes email sont à jour (sans adresses inconnues ou obsolètes). Vous pouvez également envoyer des bons à tirer permettant de configurer un cycle de validation complet.

En savoir plus sur les populations de cibles [dans cette section](../../delivery/using/steps-defining-the-target-population.md)

## Cible de l&#39;audience appropriée {#target-the-right-audience}

Lorsque votre contenu est prêt, vous devez soigneusement définir qui recevra votre message.

Pour réussir votre diffusion, vous souhaitez envoyer le contenu personnalisé le plus pertinent aux bons destinataires. Adobe Campaign vous permet de créer la cible la plus précise qui soit : vous pouvez sélectionner les destinataires selon leur âge, leur emplacement géographique, leurs achats ou selon qu’ils ont cliqué ou non sur un lien dans une diffusion précédente, par exemple. Avec Adobe Campaign, vous pouvez également définir des profils de test, des Populations témoins et des adresses de contrôle pour vous assurer que votre cible est correcte.

## Mappings de ciblage {#target-mappings}

En Campaign Classic, par défaut, modèle de diffusion cible **Destinataires**. Adobe Campaign propose d’autres mappings de ciblage pour vos diffusions, que vous pouvez modifier selon vos besoins.

Vous pouvez, par exemple, diffuser des données aux visiteurs dont les profils ont été collectés via les réseaux sociaux ou aux visiteurs abonnés à un service d&#39;information.

Ces mappages sont présentés [dans cette section](../../delivery/using/selecting-a-target-mapping.md).

Vous pouvez également créer et utiliser un mapping de ciblage personnalisé. Voir à ce propos [cette section](../../configuration/using/target-mapping.md).

## Destinataires externes {#external-recipients}

Vous pouvez fournir aux destinataires qui sont stockés dans un fichier externe plutôt que enregistrés dans la base de données. Learn more [in this section](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients).

## Envoyer à vos abonnés {#send-to-subscribers}

Pour envoyer des messages aux abonnés d&#39;un bulletin d&#39;information, vous pouvez directement les cible au service d&#39;information correspondant. Learn more [in this section](../../delivery/using/managing-subscriptions.md#delivering-to-the-subscribers-of-a-service).


## Testez les destinataires et les adresses de contrôle {#test-recipients-seed-addresses}

Pour tester votre diffusion, utilisez des bons à tirer avant l&#39;envoi à la cible principale.

Veillez à sélectionner les destinataires BAT appropriés, car ils valident le formulaire et le contenu du message. Les étapes de définition des destinataires BAT sont présentées [dans cette section](../../delivery/using/steps-defining-the-target-population.md#selecting-the-proof-target).

Les adresses de contrôle permettent de cibler des destinataires qui ne correspondent pas aux critères de ciblage définis afin de tester une diffusion avant l’envoi à la cible principale. Ils sont présentés [dans cette section](../../delivery/using/about-seed-addresses.md).

## Dédupliquez les adresses {#deduplicate-addresses}

Il est important d&#39;éviter d&#39;avoir des adresses email en double, car cela peut avoir un impact sur votre cible.

* Un même message peut être envoyé plusieurs fois lorsqu&#39;une une cible est partagée.

* Si une personne se désinscrit suite à la réception d&#39;un message, son profil en double recevra toujours les prochains messages.

Pour garantir votre réputation et assurer une bonne gestion des quarantaines, dédupliquez les adresses.

En savoir plus [sur ce cas](../../workflow/using/deduplication.md#example--identify-the-duplicates-before-a-delivery)d&#39;utilisation.

## Adresse électronique d’index {#index-addresses}

Pour optimiser les performances des requêtes SQL utilisées dans l&#39;application, un index peut être déclaré à partir de l&#39;élément principal du schéma de données.

Les étapes permettant d’ajouter un index à l’adresse électronique sont présentées [dans cette section](../../configuration/using/database-mapping.md#indexed-fields).
