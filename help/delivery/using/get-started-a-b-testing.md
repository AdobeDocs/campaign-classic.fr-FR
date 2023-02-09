---
product: campaign
title: Prise en main des tests A/B
description: En savoir plus sur les tests A/B dans Campaign Classic.
feature: A/B Testing
exl-id: ae046ef6-d850-4222-b82c-8ef5b3da7037
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 100%

---

# Prise en main des tests A/B {#get-started-a-b-testing}

![](../../assets/common.svg)

Les tests A/B vous permettent de comparer plusieurs versions d’une diffusion les unes par rapport aux autres, afin d’identifier celle qui aura le plus grand impact sur la population ciblée.

Pour ce faire, vous devez d’abord définir plusieurs variantes de la diffusion. Chaque variante est ensuite envoyée à des échantillons de population afin de déterminer laquelle fonctionne le mieux selon les critères de votre choix (ouvertures, plaintes pour spam, clics sur un lien spécifique, etc.)

Dans l&#39;exemple ci-dessous, la cible de diffusion a été divisée en deux groupes, représentant chacun 50 % de la population ciblée. Chaque groupe reçoit deux versions de la diffusion avec deux offres promotionnelles différentes. Une fois la diffusion envoyée, il est conclu que la variante A a obtenu de meilleurs résultats, en fonction du nombre de clics sur les offres promotionnelles.

![](assets/a-b-testing-schema.png)

Avec Campaign Classic, les tests A/B sont implémentés via des workflows, où vous spécifiez la population à cibler ainsi que les groupes qui recevront chaque variante (voir [Configuration des tests A/B](configuring-a-b-testing.md)).

Les étapes principales sont les suivantes :

1. **Cibler** la population désirée.
1. **Diviser la population** en sous-ensembles sur lesquels vous allez tester les variantes de votre diffusion.

   Par exemple, vous pouvez envoyer une version d’une diffusion à une petite partie de la population ciblée et une autre version à la population restante. Vous pouvez ainsi tester une nouvelle version d’une diffusion par rapport à la diffusion généralement envoyée à vos clients. Vous pouvez également diviser la population ciblée en 3 groupes afin de lui envoyer trois versions différentes d’une diffusion.

1. **Créer plusieurs versions** de la diffusion correspondant à chaque sous-ensemble. La variante à tester peut être l&#39;objet, le contenu du message, le nom de l&#39;expéditeur, etc.
1. Démarrez le workflow, puis utilisez les **logs de diffusion** pour analyser le comportement des sous-ensembles avec chaque variante.

>[!NOTE]
>
>Les workflows vous permettent également d&#39;automatiser vos processus en identifiant automatiquement la variante de diffusion qui a obtenu de meilleurs résultats, puis en l&#39;envoyant à la population restante. Voir à ce propos le [cas pratique](a-b-testing-use-case.md) dédié.
