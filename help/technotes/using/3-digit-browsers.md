---
product: campaign
title: Composants web Campaign et version 100 dans les navigateurs Chrome, Firefox et Edge
description: Composants web Campaign et version 100 dans les navigateurs Chrome, Firefox et Edge
feature: Technote
exl-id: 2016279a-7b02-4399-b2ed-9a15456de816
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: ht
source-wordcount: '644'
ht-degree: 100%

---

# Impacts de la version de navigateur à 3 chiffres sur les composants web Campaign {#version-100}

Google et Mozilla avertissent que Chrome et Firefox pourraient empêcher certains sites web de s&#39;afficher en raison de leurs prochaines versions à 3 chiffres.

Chrome v100 doit être lancé le **29 mars 2022** et Firefox v100 le **3 mai 2022**.

Microsoft a lancé Edge v100 en mars 2022.

Le passage d&#39;un numéro de version de 2 à 3 chiffres peut entraîner des problèmes lors de la visite de sites web qui ne sont pas préparés à ce changement. Certaines pages web sont susceptibles de ne plus s&#39;afficher correctement dans ces nouvelles versions de navigateur.

La compatibilité des principaux sites web a été testée à l&#39;avance. En cas de problèmes avec des sites ne pouvant être corrigés avant la sortie de ces versions, les entreprises disposent de plans de sauvegarde visant à s&#39;assurer que les sites ne sont pas affectés.

Les problèmes ou pertes de fonctionnalité potentiels rencontrés sur un site web proviennent de la chaîne de l&#39;agent utilisateur que les navigateurs envoient aux sites web visités. L&#39;agent utilisateur est une chaîne que le navigateur envoie au site web afin de lui indiquer le navigateur et la version utilisés, ainsi que la technologie associée. Lorsque votre navigateur envoie une demande à un site web, il s&#39;identifie avec la chaîne de l&#39;agent utilisateur avant de récupérer le contenu que vous avez demandé. Les données contenues dans la chaîne de l&#39;agent utilisateur permettent au site web de diffuser le contenu dans un format adapté à votre navigateur. La version de l&#39;agent utilisateur est incrémentée de manière à correspondre au numéro de version du navigateur. Le passage de 2 à 3 chiffres peut entraîner des problèmes.

## Cela vous concerne-t-il ?{#version-100-impact}

Adobe vous recommande de tester vos applications web Campaign, notamment vos formulaires et enquêtes web, afin de vous assurer de leur bon fonctionnement avec ces nouvelles versions de navigateur.

Cette recommandation s&#39;applique à toutes les applications web, en particulier si vous avez inclus du code JavaScript.

Vous devez les vérifier sur tous les navigateurs, dans les versions pour appareils mobiles et postes de travail.

## Comment effectuer ce test ?{#version-100-test}

Vous pouvez dès maintenant configurer vos navigateurs pour qu&#39;ils signalent la version 100, puis signaler et corriger les problèmes rencontrés.

Avec ces paramètres, le navigateur envoie la nouvelle chaîne de l&#39;agent utilisateur aux sites web, indiquant que le numéro de version du navigateur est 100. Si vous rencontrez des problèmes avec vos formulaires web, vous devez créer un bug pour l&#39;éditeur du navigateur. Envisagez de reconstruire ces formulaires web avant que ces mises à jour ne soient plus largement disponibles.

### Tester avec Firefox 100{#test-firefox-100}

Pour tester vos pages web avec Mozilla Firefox 100, vous pouvez simuler la modification prochaine de l&#39;agent utilisateur sur vos applications web en modifiant manuellement la chaîne de votre agent utilisateur.

1. Ouvrez Firefox, saisissez `about:config` dans la barre d&#39;adresse, puis appuyez sur Entrée.
1. Recherchez `general.useragent.override`.
1. Sélectionnez « Chaîne », puis cliquez sur le signe plus (+).

   ![](assets/force-user-agent-firefox.png)

1. Saisissez le texte suivant dans le champ :

   ```
   Mozilla/5.0 (Windows NT 10.0; rv:100.0) Gecko/20100101 Firefox/100.0
   ```

1. Cliquez sur la coche bleue pour enregistrer le paramètre.
1. Fermez et relancez le navigateur.

Pour rétablir la valeur par défaut de votre agent utilisateur, revenez simplement à `about:config` et recherchez à nouveau le paramètre `general.useragent.override`.  Lorsque ce paramètre apparaît, cliquez sur l&#39;icône de corbeille pour le supprimer, puis relancez le navigateur.

### Tester avec Chrome 100{#test-chrome-100}

Pour tester l&#39;agent utilisateur Google Chrome 100 sur vos propres applications web, vous pouvez exécuter ce test en procédant comme suit :

1. Ouvrez Chrome, saisissez `chrome://flags` dans la barre d&#39;adresse, puis appuyez sur Entrée.
1. Recherchez `Force major version to 100 in User-Agent` dans le champ de recherche, puis activez-le comme illustré ci-dessous.

   ![](assets/force-user-agent-chrome.png)

1. Redémarrez le navigateur.
1. Fermez l&#39;onglet `chrome://flags`.

Pour rétablir la valeur par défaut de lagent utilisateur, suivez simplement ce processus et remplacez le paramètre de lindicateur par `Default`, puis redémarrez le navigateur.


### Tester avec Microsoft Edge 100{#test-ms-edge-100}

À partir de la version 97, les propriétaires de sites peuvent émuler cette version en activant l&#39;indicateur d&#39;expérience `#force-major-version-to-100` dans `edge://flags`.

1. Ouvrez Microsoft Edge, saisissez `edge://flags` dans la barre d&#39;adresse, puis appuyez sur Entrée.
1. Recherchez le champ `force-major-version-to-100` et activez-le, comme illustré ci-dessous.

   ![](assets/force-user-agent-edge.png)

1. Redémarrez le navigateur.
1. Fermez l&#39;onglet `edge://flags`.

Pour rétablir la valeur par défaut de lagent utilisateur, suivez simplement ce processus et remplacez le paramètre de lindicateur par `Default`, puis redémarrez le navigateur.
