---
product: campaign
title: Définition de lʼaudience appropriée
description: Découvrez les bonnes pratiques lors de la sélection de votre audience
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
feature: Audiences
role: User
hide: true
hidefromtoc: true
exl-id: c0533148-b027-4158-9b95-8d2df769e963
source-git-commit: aa78a51ebea49f98ef7edad7e87a99a680f02b69
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 100%

---

# Définition de l&#39;audience appropriée {#define-the-right-audience}

La population ciblée est essentielle : créez soigneusement vos listes, testez vos emails sur les clients de messagerie et les appareils mobiles les plus utilisés et vérifiez que vos listes email sont à jour (sans adresses inconnues ou obsolètes). Vous pouvez également envoyer des bons à tirer permettant de configurer un cycle de validation complet.

En savoir plus sur les populations ciblées [dans cette section](steps-defining-the-target-population.md)

## Cibler la bonne audience {#target-the-right-audience}

Lorsque votre contenu est prêt, vous devez soigneusement définir qui recevra votre message.

Pour réussir votre diffusion, vous devez envoyer le contenu personnalisé le plus pertinent aux bons destinataires. Adobe Campaign vous permet de créer la cible la plus précise qui soit : vous pouvez sélectionner les destinataires selon leur âge, leur emplacement géographique, leurs achats ou selon qu’ils ont cliqué ou non sur un lien dans une diffusion précédente, par exemple. Avec Adobe Campaign, vous pouvez également définir des profils de test, des populations témoins et des adresses de contrôle pour vérifier que votre cible est correcte.

## Mappings de ciblage {#target-mappings}

Par défaut, dans Campaign Classic, les modèles de diffusion ciblent les **Destinataires**. Adobe Campaign propose d’autres mappings de ciblage pour vos diffusions, que vous pouvez modifier selon vos besoins.

Vous pouvez, par exemple, envoyer votre diffusion à des visiteurs dont le profil a été collecté par le biais des réseaux sociaux ou à des visiteurs qui se sont abonnés à un service d&#39;information.

Ces mappings sont présentés [dans cette section](selecting-a-target-mapping.md).

Vous pouvez également créer et utiliser un mapping de ciblage personnalisé. Pour plus d’informations, consultez [cette section](../../configuration/using/target-mapping.md).

## Destinataires externes {#external-recipients}

Vous pouvez effectuer une diffusion aux destinataires qui sont stockés dans un fichier externe plutôt qu&#39;enregistrés dans la base de données. En savoir plus dans [cette section](steps-defining-the-target-population.md#selecting-external-recipients).

## Envoyer des messages à vos abonnés {#send-to-subscribers}

Pour envoyer des messages aux abonnés d&#39;une newsletter, vous pouvez directement cibler les abonnés du service d&#39;information correspondant. En savoir plus dans [cette section](managing-subscriptions.md#delivering-to-the-subscribers-of-a-service).


## Tester les destinataires et les adresses de contrôle {#test-recipients-seed-addresses}

Pour tester votre diffusion, utilisez des bons à tirer avant l&#39;envoi à la cible principale.

Veillez à sélectionner les destinataires du BAT appropriés, car ils valident le formulaire et le contenu du message. Les étapes de définition des destinataires du BAT sont présentées [dans cette section](steps-defining-the-target-population.md#selecting-the-proof-target).

Les adresses de contrôle permettent de cibler des destinataires qui ne correspondent pas aux critères de ciblage définis afin de tester une diffusion avant l’envoi à la cible principale. Elles sont présentées [dans cette section](about-seed-addresses.md).

## Dédupliquer les adresses {#deduplicate-addresses}

Il est important d&#39;éviter d&#39;avoir des adresses email en double, car cela peut avoir un impact sur votre cible.

* Un même message peut être envoyé plusieurs fois lorsqu&#39;une une cible est partagée.

* Si une personne se désabonne suite à la réception d&#39;un message, son profil en double recevra toujours les prochains messages.

Pour garantir votre réputation et assurer une bonne gestion des quarantaines, dédupliquez les adresses.

**Rubriques connexes :**

* [Activité Déduplication](../../workflow/using/deduplication.md).
* [Cas pratique : utilisation de la fonctionnalité de fusion de l’activité Déduplication](../../workflow/using/deduplication-merge.md)

## Adresses email d’index {#index-addresses}

Pour optimiser les performances des requêtes SQL utilisées dans l&#39;application, un index peut être déclaré à partir de l&#39;élément principal du schéma de données.

Les étapes permettant d’ajouter un index à l’adresse email sont présentées [dans cette section](../../configuration/using/database-mapping.md#indexed-fields).
