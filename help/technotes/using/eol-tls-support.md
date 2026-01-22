---
product: campaign
title: Fin de vie de la prise en charge du protocole TLS 1.0 et 1.1
description: Fin de vie de la prise en charge du protocole TLS 1.0 et 1.1
feature: Technote
audience: delivery
content-type: reference
topic-tags: tracking-messages
hide: true
hidefromtoc: true
exl-id: e18d43b6-2a77-4881-85e7-ca36248d4634
source-git-commit: 19b40f0b827c4b5b7b6484fe4953aebe61d00d1d
workflow-type: ht
source-wordcount: '860'
ht-degree: 100%

---

# Fin de vie de la prise en charge du protocole TLS 1.0 et 1.1{#eol-tls-support}



Adobe ne prend plus en charge les systèmes utilisateur et les systèmes client qui ne sont pas conformes au protocole TLS (Transport Layer Security) 1.2. Si vous continuez à utiliser des versions plus anciennes du protocole TLS, vous risquez de perdre l’accès à tous les produits et services Adobe.

## Pourquoi est-ce que je vois cette page ?

Si le message suivant s’affiche : **Cette page ne peut pas être affichée.**, cela signifie que les applications, pages web ou services d’Adobe auxquels vous essayez d’accéder nécessitent une connexion réseau plus sécurisée avec votre navigateur web, votre système d’exploitation ou votre application. Il est obligatoire d’utiliser **TLS 1.2** pour une communication réseau sécurisée et un échange de données entre les systèmes utilisateurs et les applications et services web Adobe.

Adobe a mis fin à la prise en charge des versions antérieures de TLS (notamment TLS 1.0 et 1.1). Pour les détails techniques concernant le protocole TLS 1.2, consultez le [Forum aux questions](#faq).

## Que puis-je faire pour reprendre le service ?

Les navigateurs web modernes prennent en charge TLS 1.2. La mise à niveau de votre navigateur peut vous permettre d’accéder à ces applications et services.

Vous pouvez télécharger et installer l’un des navigateurs populaires suivants :

* [Google Chrome](https://www.google.com/chrome/)
* [Apple Safari](https://www.apple.com/safari/)
* [Firefox](https://www.mozilla.org/fr/firefox/new/)
* [Microsoft Edge](https://www.microsoft.com/fr-fr/edge)

Si vous utilisez un autre navigateur, assurez-vous qu’il prend en charge TLS 1.2.

Votre système d’exploitation et les structures d’application doivent également prendre en charge TLS 1.2. Si la mise à niveau de votre navigateur ne résout pas votre problème, assurez-vous que votre ordinateur répond à la configuration requise répertoriée dans la section [Matrice de compatibilité Campaign](../../rn/using/compatibility-matrix.md).

## Forum aux questions{#faq}

* **Qu’est-ce que le protocole TLS (Transport Layer Security) ?**

  [Transport Layer Security](https://fr.wikipedia.org/wiki/Transport_Layer_Security) (TLS) est un protocole de sécurité qui assure la confidentialité et l’intégrité des données entre deux applications qui communiquent entre elles. Il est largement déployé pour les navigateurs web et les autres applications qui nécessitent un échange sécurisé de données sur un réseau.

  Selon la spécification du protocole, TLS inclut deux couches, le protocole d’enregistrement TLS et le protocole de négociation TLS. Le protocole d’enregistrement assure la sécurité de la connexion. Le protocole de négociation permet au serveur et au client de s’authentifier mutuellement et de négocier les algorithmes de chiffrement et les clés cryptographiques avant l’échange de données.

* **Quel est l&#39;impact ?**

  Les normes de conformité en matière de sécurité d’Adobe exigent l’obsolescence des protocoles plus anciens à compter de mai 2018 et exigent l’utilisation de TLS 1.2 comme version à jour. Si votre système n’est pas compatible avec TLS 1.2, l’accès à certains services et applications Adobe est limité.

* **En quoi TLS vous affecte-t-il ?**

  Vous pouvez uniquement interagir avec certains services et applications Adobe par le biais d’une connexion réseau sécurisée. TLS permet de s’assurer que la connexion entre votre navigateur et ces applications et services web est sécurisée et fiable.

  À mesure que de nouveaux navigateurs et de nouveaux systèmes d’exploitation sont commercialisés, les normes de sécurité sont mises à niveau afin de garantir des niveaux plus élevés de confidentialité et d’intégrité des données. Toutefois, les anciennes versions de ces navigateurs ou systèmes d’exploitation ne sont pas mises à jour pour inclure les dernières normes.

  À mesure que le niveau de sécurité acceptable augmente, ces versions et applications de navigateur plus anciennes et moins sécurisées sont abandonnées.

  Pour vous connecter à des sites sécurisés, mettez à jour les versions du système d’exploitation et du navigateur.

* **TLS est-il vulnérable aux hackers ?**

  Il y a eu des attaques documentées contre TLS 1.0 à l’aide d’une ancienne méthode de chiffrement et les versions plus anciennes sont plus vulnérables que TLS 1.2. Pour plus d’informations, consultez la section Attaques contre TLS/SSL.

* **Pourquoi Adobe désactive-t-il la prise en charge de TLS 1.0 et 1.1 ?**

  Adobe applique des normes de conformité en matière de sécurité qui nécessitent la désactivation de la prise en charge des anciens protocoles. Une telle norme garantit la conformité avec l’industrie des cartes de paiement (PCI). Le serveur d’adaptation PCI est un ensemble de normes de sécurité qui exigent des entreprises qui acceptent, traitent, stockent ou transmettent des informations de carte de crédit pour conserver un environnement sécurisé.

  La conformité PCI rend obligatoire l’utilisation de TLS 1.1 ou version ultérieure à partir de mai 2018.

* **Pourquoi Adobe rend-il obligatoire l’utilisation de TLS 1.2 plutôt que d&#39;autoriser TLS 1.1 ou TLS 1.0 ?**

  La plupart des demandes d&#39;applications et de services web Adobe proviennent de systèmes utilisateurs compatibles TLS 1.2, le trafic provenant de systèmes TLS 1.1 étant faible.

  Adobe a migré vers TLS 1.2 afin que l’accès à ses applications et services web soit plus sécurisé.

* **Quelle est la dernière date à laquelle je peux utiliser une ancienne version de TLS ?**

  Adobe encourage les utilisateurs à abandonner rapidement les anciennes versions pour éviter toute vulnérabilité aux failles de sécurité. Pour plus d’informations, contactez l’Assistance clientèle d’Adobe ou votre Customer Success Manager.

* **Quel message d’erreur s’affiche si j’utilise un navigateur qui n’est pas configuré pour TLS 1.2 ?**

  Cela dépend du navigateur que vous utilisez. Tous les navigateurs mentionnés dans la section [Matrice de compatibilité Campaign](../../rn/using/compatibility-matrix.md) sont configurés pour utiliser TLS 1.2. Si vous utilisez un navigateur ou une version qui ne figure pas dans la liste, mettez à jour votre navigateur.

  Adobe ne contrôle pas les messages d’erreur générés par la couche de communications SSL. Le navigateur génère ces messages avant de se connecter aux applications et services Adobe. Voici un exemple d’erreur qui peut se produire avec Internet Explorer 11 sous Windows 7 :

  ![](assets/do-not-translate/page-not-displayed.png)

  TLS 1.2 est activé par défaut sur Internet Explorer 11, mais s’il est désactivé, vous pouvez l’activer. Dans ce cas, activez TLS 1.2 à partir de la boîte de dialogue des paramètres avancés plutôt que d’utiliser d’autres options. D’autres erreurs, telles que les suivantes, peuvent également se produire :

   * Impossible de se connecter au service
   * Service non disponible
   * Erreur lors de la connexion
