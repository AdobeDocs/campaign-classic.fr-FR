---
solution: Campaign Classic
product: campaign
title: À propos de ce cas d'utilisation
description: Découvrez comment effectuer des tests A/B à l’aide d’un cas d’utilisation spécifique.
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: 50a10e16f320a67cb4ad0e31c1cbe8a9365b7887
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 30%

---


# À propos de ce cas d&#39;utilisation {#about-use-case}

Dans ce cas pratique, vous allez comparer deux contenus de diffusion par email via un workflow de ciblage. Le message et le texte sont identiques dans les deux diffusions. Seules les présentations diffèrent.

La population ciblée est divisée en trois : deux groupes d&#39;essai et la population restante. Une version différente de la diffusion est envoyée à chaque groupe de tests.

Après la diffusion, une période d’attente de 5 jours est configurée avant de collecter les résultats des meilleurs tarifs ouverts. Le contenu de la diffusion dont le score est le plus élevé est alors récupéré par un script et envoyé à la population qui n’a pas été utilisée comme groupe de test.

Il est à noter que le critère qui doit déterminer la diffusion à retenir peut varier selon vos besoins. Il peut s&#39;agir du taux d&#39;ouverture, du taux de clics, du taux d&#39;inscription, de la réactivité etc.

De plus, le test détaillé dans ce cas d&#39;utilisation ne concernait que deux diffusions, mais vous pouvez tester autant de versions que nécessaire. Ajoutez simplement des activités au processus.

Les étapes principales pour effectuer cette utilisation sont les suivantes :

* [Étape 1 : Création d’un processus de ciblage](../../delivery/using/a-b-testing-uc-targeting-workflow.md)
* [Étape 2 : Configurer des exemples de population](../../delivery/using/a-b-testing-uc-population-samples.md)
* [Étape 3 : Créer deux modèles de diffusion](../../delivery/using/a-b-testing-uc-delivery-templates.md)
* [Étape 4 : Configuration des diffusions dans le processus](../../delivery/using/a-b-testing-uc-configuring-deliveries.md)
* [Étape 5 : Création du script](../../delivery/using/a-b-testing-uc-script.md)
* [Étape 6 : Définir la diffusion finale](../../delivery/using/a-b-testing-uc-final-delivery.md)
* [Étape 7 : Début du processus](../../delivery/using/a-b-testing-uc-start-workflow.md)
* [Étape 8 : Analyser le résultat](../../delivery/using/a-b-testing-uc-analyzing.md)

**Rubriques connexes :**

* [Commencer avec les tests A/B](../../delivery/using/get-started-a-b-testing.md)
* [Configuration des tests A/B](../../delivery/using/configuring-a-b-testing.md)
