---
product: campaign
title: Composants web de Campaign et version 100 dans les navigateurs Chrome Firefox et Edge
description: Composants web de Campaign et version 100 dans les navigateurs Chrome, Firefox et Edge
exl-id: 2016279a-7b02-4399-b2ed-9a15456de816
source-git-commit: b8329e24f07ec8b3dd89f655b47699f130266008
workflow-type: tm+mt
source-wordcount: '634'
ht-degree: 0%

---

# Impact de la version de navigateur à 3 chiffres sur les composants web de Campaign {#version-100}

Google et Mozilla avertissent que Chrome et Firefox pourraient interrompre certains sites web en raison de leurs versions à 3 chiffres à venir.

Chrome v100 est défini pour la version sur **29 mars 2022** et Firefox v100 sous **3 mai 2022**.

Microsoft a lancé Edge v100 en mars 2022.

Le changement de numéro de version de 2 à 3 chiffres peut entraîner des problèmes lors de la visite de sites web qui ne sont pas préparés à ce changement. Certaines pages web peuvent ne plus s’afficher correctement dans ces nouvelles versions du navigateur.

La compatibilité des principaux sites web a été testée à l’avance. En cas de problèmes avec des sites qui ne peuvent pas être corrigés avant la publication de ces versions, les entreprises disposent de plans de sauvegarde prêts à s’assurer que les sites ne sont pas affectés.

Les problèmes potentiels ou la perte de fonctionnalités sur le site web proviennent de la chaîne de l’agent utilisateur que les navigateurs envoient aux sites web que vous visitez : l’agent utilisateur est une chaîne envoyée par le navigateur au site web pour informer le site du navigateur et de la version que vous utilisez, ainsi que de la technologie associée. Lorsque votre navigateur envoie une demande à un site web, il s’identifie avec la chaîne de l’agent utilisateur avant de récupérer le contenu que vous avez demandé. Les données contenues dans la chaîne de l’agent utilisateur aident le site web à diffuser le contenu dans un format adapté à votre navigateur. La version de l’agent utilisateur est incrémentée de manière à correspondre au numéro de version du navigateur. Le passage de 2 à 3 chiffres peut entraîner des problèmes.

## Cela vous concerne-t-il ?{#version-100-impact}

Adobe vous recommande de tester vos applications web Campaign, notamment vos formulaires web et enquêtes, afin de vous assurer qu&#39;elles fonctionneront correctement avec ces nouvelles versions de navigateur.

Cette recommandation s’applique à toutes les applications web, en particulier si vous avez inclus du code JavaScript.

Vous devez vérifier avec tous les navigateurs, mobiles et de bureau.

## Comment tester ?{#version-100-test}

Vous pouvez maintenant configurer vos navigateurs pour qu’ils signalent la version 100, puis signaler et corriger les problèmes rencontrés.

Avec ces paramètres, le navigateur envoie la nouvelle chaîne de l’agent utilisateur aux sites web, indiquant que le navigateur est v100. Si vous rencontrez des problèmes avec vos formulaires web, vous devez créer un bogue pour l’éditeur de navigateur. Envisagez de reconstruire ces formulaires web avant que ces mises à jour ne soient disponibles dans l’ensemble.

### Test avec Firefox 100{#test-firefox-100}

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

Pour rétablir la valeur par défaut de votre agent utilisateur, revenez simplement à `about:config` et recherchez `general.useragent.override` à nouveau.  Lorsqu’il apparaît, cliquez sur l’icône de corbeille pour supprimer le paramètre, puis relancez le navigateur.

### Test avec Chrome 100{#test-chrome-100}

Pour tester l’agent utilisateur Google Chrome 100 sur vos propres applications web, vous pouvez activer ce test en procédant comme suit :

1. Ouvrez Chrome, saisissez `chrome://flags` dans la barre d’adresse, puis appuyez sur entrée.
1. Rechercher `Force major version to 100 in User-Agent` dans le champ de recherche, puis activez-le comme illustré ci-dessous.

   ![](assets/force-user-agent-chrome.png)

1. Redémarrez le navigateur.
1. Fermez la `chrome://flags` .

Pour rétablir la valeur par défaut de l’agent utilisateur, procédez comme suit et modifiez le paramètre de l’indicateur en `Default` et redémarrez le navigateur.


### Test avec Microsoft Edge 100{#test-ms-edge-100}

À partir de la version 97, les propriétaires de site peuvent émuler cette version en activant l’indicateur de l’expérience.  `#force-major-version-to-100` in `edge://flags`.

1. Ouvrez Microsoft Edge, puis saisissez `edge://flags` dans la barre d’adresse, puis appuyez sur entrée.
1. Rechercher `force-major-version-to-100` et activez-la, comme illustré ci-dessous.

   ![](assets/force-user-agent-edge.png)

1. Redémarrez le navigateur.
1. Fermez la `edge://flags` .

Pour rétablir la valeur par défaut de l’agent utilisateur, procédez comme suit et modifiez le paramètre de l’indicateur en `Default` et redémarrez le navigateur.
