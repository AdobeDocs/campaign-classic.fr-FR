---
product: campaign
title: Cas d’utilisation des tests AB
description: Découvrez comment effectuer des tests A/B à l’aide d’un cas d’utilisation spécifique.
audience: delivery
content-type: reference
topic-tags: a-b-testing
exl-id: 4eb139a0-5342-4084-9f6d-d736e05bf1c6
source-git-commit: 895aa2fd4fa9c7c71c0073e9be33c12d4e92c9fa
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 98%

---

# À propos de ce cas d&#39;utilisation {#about-use-case}

Dans ce cas pratique, vous allez comparer deux contenus de diffusion par email via un workflow de ciblage. Le message et le texte sont identiques dans les deux diffusions. Seules les présentations diffèrent.

La population ciblée est divisée en trois : deux groupes de test et la population restante. Une version différente de la diffusion est envoyée à chaque groupe de test.

Après la diffusion, une période d’attente de 5 jours est configurée avant de collecter les résultats des meilleurs taux d’ouverture. Le contenu de la diffusion dont le score est le plus élevé est alors récupéré par un script et envoyé à la population qui n’a pas été utilisée comme groupe de test.

Il est à noter que le critère qui doit déterminer la diffusion à retenir peut varier selon vos besoins. Il peut s&#39;agir du taux d&#39;ouverture, du taux de clics, du taux d&#39;inscription, de la réactivité etc.

De plus, le test détaillé dans ce cas pratique ne concernait que deux diffusions, mais vous pouvez tester autant de versions que nécessaire. Il suffit d’ajouter des activités au workflow.

Les étapes principales pour réaliser ce cas pratique sont les suivantes :

* [Étape 1 : créer un workflow de ciblage](../../delivery/using/a-b-testing-uc-targeting-workflow.md)
* [Étape 2 : paramétrer les échantillons de population](../../delivery/using/a-b-testing-uc-population-samples.md)
* [Étape 3 : créer deux modèles de diffusions](../../delivery/using/a-b-testing-uc-delivery-templates.md)
* [Étape 4 : paramétrer les diffusions dans le workflow](../../delivery/using/a-b-testing-uc-configuring-deliveries.md)
* [Étape 5 : créer le script](../../delivery/using/a-b-testing-uc-script.md)
* [Étape 6 : définir la diffusion finale](../../delivery/using/a-b-testing-uc-final-delivery.md)
* [Étape 7 : lancer le workflow](../../delivery/using/a-b-testing-uc-start-workflow.md)
* [Étape 8 : analyser le résultat](../../delivery/using/a-b-testing-uc-analyzing.md)

**Rubriques connexes :**

* [Prise en main des tests A/B](../../delivery/using/get-started-a-b-testing.md)
* [Configuration des tests AB](../../delivery/using/configuring-a-b-testing.md)
