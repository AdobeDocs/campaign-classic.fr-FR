---
product: campaign
title: Composants web de Campaign et version 100 dans les navigateurs Chrome et Firefox
description: Composants web de Campaign et version 100 dans les navigateurs Chrome et Firefox
hide: true
hidefromtoc: true
source-git-commit: 68049d1905524b644794799348bd6387b2afed0d
workflow-type: tm+mt
source-wordcount: '618'
ht-degree: 0%

---

# Composants web de Campaign et version 100 dans les navigateurs Chrome et Firefox {#version-100}

## What {#what-version-100}

Google et Mozilla avertissent que Chrome et Firefox pourraient interrompre certains sites web en raison de leurs versions à 3 chiffres à venir.
Le changement de numéro de version de 2 à 3 chiffres peut entraîner des problèmes lors de la visite de sites web qui ne sont pas préparés à ce changement. Certaines pages web peuvent ne plus s’afficher correctement dans ces nouvelles versions du navigateur.

Mozilla et Google testent à l’avance la compatibilité des principaux sites web. S’il existe des problèmes avec les sites qu’ils ne peuvent pas résoudre avant la publication de ces versions, les deux sites disposent de plans de sauvegarde prêts à l’emploi pour s’assurer qu’ils ne sont pas affectés.

## Pourquoi {#why-version-100}

Les problèmes potentiels ou la perte de fonctionnalités sur le site web proviennent de la chaîne de l’agent utilisateur que les navigateurs envoient aux sites web que vous visitez : l’agent utilisateur est une chaîne envoyée par le navigateur au site web pour informer le site du navigateur et de la version que vous utilisez, ainsi que de la technologie associée. Lorsque votre navigateur envoie une demande à un site web, il s’identifie avec la chaîne de l’agent utilisateur avant de récupérer le contenu que vous avez demandé. Les données contenues dans la chaîne de l’agent utilisateur aident le site web à diffuser le contenu dans un format adapté à votre navigateur. La version de l’agent utilisateur est incrémentée de manière à correspondre au numéro de version du navigateur. Le passage de 2 à 3 chiffres peut entraîner des problèmes.

## When {#when-version-100}

Chrome v100 est défini pour la version sur **29 mars 2022** et Firefox v100 sous **3 mai 2022**.

## Où {#where-version-100}

Adobe vous recommande de tester vos applications web Campaign, notamment les formulaires web et enquêtes, ainsi que les pages miroir d&#39;email, afin de vous assurer qu&#39;elles fonctionneront correctement avec ces nouvelles versions de navigateur.

Cette recommandation s’applique à toutes les applications web, en particulier si vous avez inclus du code JavaScript.

Vous devez vérifier avec Firefox et Chrome, mobile et bureau.

## Comment {#how-version-100}

Dans Chrome et Firefox de nuit, vous pouvez configurer le navigateur de sorte qu’il signale la version 100 dès maintenant et corrige tous les problèmes que vous rencontrez.

### Firefox 100{#test-firefox-100}

Pour tester vos pages web avec Mozilla Firefox 100, vous pouvez simuler la modification prochaine de l’agent utilisateur sur vos applications web en modifiant manuellement la chaîne de votre agent utilisateur.

1. Ouvrez Firefox, saisissez `about:config` dans la barre d’adresse, puis appuyez sur entrée.
1. Rechercher `general.useragent.override`.
1. Sélectionnez &quot;Chaîne&quot;, puis cliquez sur le signe plus (+).

   ![](assets/force-user-agent-firefox.png)

1. Saisissez le texte suivant dans le champ :

   ```
   Mozilla/5.0 (Windows NT 10.0; rv:100.0) Gecko/20100101 Firefox/100.0
   ```

1. Cliquez sur la coche bleue pour enregistrer le paramètre.
1. Fermez et relancez le navigateur.

Avec ces paramètres, le navigateur envoie la nouvelle chaîne de l’agent utilisateur aux sites web, indiquant que le navigateur est Firefox 100. Si vous rencontrez des problèmes avec vos formulaires web, vous devez créer un nouveau rapport de bogue pour Mozilla. Envisagez de reconstruire ces formulaires web avant que cette modification ne soit disponible dans l’ensemble.

Pour rétablir la valeur par défaut de votre agent utilisateur, revenez simplement à `about:config` et recherchez `general.useragent.override` à nouveau.  Lorsqu’il apparaît, cliquez sur l’icône de corbeille pour supprimer le paramètre, puis relancez le navigateur.

### Chrome 100{#test-chrome-100}

Pour tester l’agent utilisateur Google Chrome 100 sur vos propres applications web, vous pouvez activer ce test en procédant comme suit :

1. Ouvrez Chrome, saisissez `chrome://flags` dans la barre d’adresse, puis appuyez sur entrée.
1. Rechercher `Force major version to 100 in User-Agent` dans le champ de recherche, puis activez-le comme illustré ci-dessous.

   ![](assets/force-user-agent-chrome.png)

1. Fermez et relancez le navigateur.
1. Fermez la `chrome://flags` écran.

Avec ces paramètres, le navigateur envoie la nouvelle chaîne de l’agent utilisateur aux sites web, indiquant que le navigateur est Chrome 100. Si vous rencontrez des problèmes avec les sites web que vous visitez, vous devez créer un nouveau rapport de bogue pour Google. Envisagez de reconstruire ces formulaires web avant que cette modification ne soit disponible dans l’ensemble.

Pour rétablir la valeur par défaut de l’agent utilisateur, procédez comme suit et modifiez le paramètre de l’indicateur en `Default` et relancez le navigateur.
