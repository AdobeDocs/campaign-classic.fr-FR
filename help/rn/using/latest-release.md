---
solution: Campaign Classic
product: campaign
title: Dernière version
description: Dernière version de Campaign Classic      Notes
audience: rns
content-type: reference
topic-tags: latest-release-notes
translation-type: tm+mt
source-git-commit: 5b5aae1b8c19e9fed5f3172d796b0f25022b6d58
workflow-type: tm+mt
source-wordcount: '903'
ht-degree: 18%

---


# Dernière version{#latest-release}

Cette page répertorie les nouvelles fonctionnalités, les améliorations et les correctifs de la **dernière version Release Candidate de Campaign Classic**.

Pour la version Gold Standard de Campaign Classic (dernier build GA), [reportez-vous à cette page](../../rn/using/gold-standard.md).

## ![](assets/do-not-localize/blue_2.png) Version 21.1.1 - Build 9277 {#release-21-1-1-build-9277}

_22 février 2021_

**Améliorations de la sécurité**

* Le mécanisme d&#39;authentification de la console a été amélioré pour optimiser la sécurité. (NEO-26944)
* Correction d’un problème de sécurité afin de renforcer la protection contre les problèmes SSRF (Server Side Request Forgery). (NEO-28532)

**Mises à jour de compatibilité**

Les systèmes suivants sont désormais pris en charge avec Campaign :

* L’API Salesforce version 49 est désormais prise en charge lors de l’utilisation du compte externe de gestion de la relation client Salesforce.

**Fonctionnalités obsolètes**

Le rapport **Analyse de la délivrabilité technique** est désormais obsolète.

En savoir plus dans la page [Fonctionnalités obsolètes et supprimées](../../rn/using/deprecated-features.md).

**Améliorations**

**Le service de commentaires par courriel (EFS)** est un service évolutif qui capture directement les commentaires des MTA amélioré, améliorant ainsi la précision des rapports. Cette fonctionnalité est disponible en version bêta privée et sera progressivement disponible pour tous les clients dans les prochaines versions.

* Toutes les catégories de commentaires sont maintenant capturées pour créer des rapports complets et précis.
* Le calcul de l’indicateur Délivrés est désormais fondé sur les commentaires en temps réel du MTA amélioré, ce qui contribue à l’amélioration de la précision et de la réactivité.
* Le service EFS résout le problème des retards grâce au reporting synchrone des soft bounces.

Pour plus d’informations, consultez la [documentation détaillée](../../delivery/using/sending-with-enhanced-mta.md#efs).
Si vous souhaitez participer à cette version bêta privée, remplissez ce [formulaire](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4Rol2vQGupxItW9_BerXV6VUQTJPN1Q5WUI4OFNTWkYzQjg3WllUSDAxWi4u) et nous vous répondrons.

**Autres changements**

* La vitesse de transfert a été améliorée pour les logs de tracking volumineux par compression.
* Le Heatmap du flux de travail a été amélioré afin d’éviter les dépassements de délai lors de l’exécution de workflows avec plusieurs activités. (NEO-27423).
* Correction d’un problème en raison duquel une offre pouvait être présentée même si sa date de fin était dépassée. Le Campaign Classic prend désormais en compte l’horodatage complet de la date de fin plutôt que la date uniquement. (NEO-27590)
* Le lien Google+ a été supprimé du bloc de personnalisation **Liens de partage de réseau social**.
* Correction d’un problème après l’implémentation d’un correctif dans la dernière version. Une vérification a été ajoutée sur le nom d&#39;hôte lors de la connexion à l&#39;aide de SSL/TLS, ce qui a conduit à l&#39;échec des diffusions SMS. La vérification du nom d&#39;hôte a été désactivée pour la plupart des protocoles tels que POP3, SMS et HTTP avec proxy et la vérification du certificat pour le compte externe SMS a été améliorée avec trois valeurs (NEO-29581). [En savoir plus](../../delivery/using/sms-protocol.md#skip-tls)

**Correctifs**

* Correction d’un problème en raison duquel les raccourcis clavier Tabulation, Entrée et Echap ne fonctionnaient pas sur le nouvel écran de connexion.
* Correction d’un problème d’actualisation en raison duquel le nom d’un nouveau flux de travail était remplacé par la valeur par défaut après l’enregistrement (NEO-26106).
* Correction d’un problème survenant lors de l’exécution de workflows où un nouveau champ a été ajouté dans le cadre d’une activité **Enrichissement** avant une activité **Diffusion** à l’aide d’un mapping de ciblage **Fichier externe** : des champs indésirables ont été ajoutés au mapping de ciblage **Fichier externe**. (NEO-27687)
* Correction d’un problème en raison duquel certains caractères du code source étaient modifiés lors de la réouverture d’une application Web précédemment créée et enregistrée. (NEO-27597)
* Correction d’un problème qui pouvait se produire lors de la mise à niveau vers une version incluant le nouveau mécanisme de signature pour le suivi des liens (depuis la version 19.1.4 et Campaign 20.2) : lorsque plusieurs modèles étaient associés à un événement, la mise à niveau pouvait entraîner la sélection d’un modèle incorrect lors de l’envoi du message transactionnel. (NEO-28326)
* Correction d’un problème en raison duquel la MTA ne réagissait pas et ne pouvait pas traiter les diffusions sauf si elle était redémarrée. (NEO-27455)
* Correction d’un problème de la base de données MSSQL lié à la gestion de l’horodatage lors des opérations de chargement en masse pour une colonne de type datetime.
* Correction d’un problème de requête de processus lors de l’utilisation des fonctions xtk de Redshift. Les sous-jours, sous-secondes, sous-minutes et sous-heures acceptent désormais les deux types d&#39;horodatage de décalage (NEO-24962).
* Correction d’un problème en raison duquel un message d’erreur de script s’affichait lors de la tentative de prévisualisation d’un rapport avec accès anonyme. (NEO-27081)
* Correction d’un problème qui pouvait réduire l’utilisation de la mémoire sur le serveur lors de l’analyse des diffusions.
* Correction d’un problème en raison duquel l’instance ne fonctionnait pas lors de l’exécution de requêtes complexes spécifiques.
* Correction d’un problème qui empêchait l’exécution du processus technique **Synchronisation des pages Twitter**. (NEO-28634)
* Correction d’un problème qui pouvait afficher un message d’erreur lié à la fonction decryptPassword lors de la tentative de publication sur Twitter à l’aide du modèle de diffusion **Tweet (twitter)**. (NEO-28216)
* Correction d’un problème survenant lors de l’utilisation d’une activité **JavaScript** pour effectuer une requête HTTP dans un flux de travail. Après avoir défini le numéro de port dans le nom d’hôte, l’appel échoue avec l’erreur suivante (NEO-29146) :

```
IOB-090020 Error in SSL library: 'IOB-090013 error:14090086:SSL routines:ssl3_get_server_certificate:certificate verify failed (code 336134278)'
```

* Correction d’un problème qui empêchait l’envoi de nouvelles diffusions avec la personnalisation des données de cible.
* Correction d’un problème en raison duquel plusieurs blocages se produisaient dans l’instance marketing, causant des fichiers principaux.
* Correction d’un problème en raison duquel le flux de travail **Suivi** échouait avec l’erreur suivante (NEO-25206) :

```
There is no index on the sourceId field of the 'NmsTrackingLogRcp' table required for the current Web tracking mode. Please add this index.
```

* Correction d’un problème survenant lors de la création et de l’enregistrement d’une diffusion dans l’onglet **Ciblage et flux de travail** d’une campagne : la prévisualisation échouerait avec l’erreur suivante (NEO-29440) :

```
XTK-170024 The temporary 'temp:deliveryEmail-all' schema is not defined in the current context
```

* Correction d’une erreur qui se produisait lors de la configuration d’un compte externe entre une instance marketing et une instance Adobe Campaign Standard ou une instance de midsourcing Campaign Classic à l’aide de l’option &quot;DésactiverFOH2=1&quot;. Lors de l’utilisation de l’option &quot;DisableFOH2=1&quot; dans le compte externe, les connexions n’étaient pas correctement fermées et s’empilaient, provoquant l’erreur suivante (NEO-26258) :

```
The maximum number of connections has been reached (50) by connections pool 'nms:extAccount:acsDefaultRelayAccount XXX'. The server is overloaded. Please try again later.
```

* Correction d’une erreur SMS en cas de problèmes de connexion entre le serveur et le fournisseur. La connexion serait alors automatiquement désactivée par l’enfant MTA. Adobe Campaign Classic ne tenterait pas de se connecter à cette connexion défaillante tant qu&#39;un nouvel enfant n&#39;aurait pas été démarré.
