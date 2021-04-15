---
solution: Campaign Classic
product: campaign
title: Dernière version
description: Dernière version de Campaign Classic       Notes
feature: Vue d’ensemble
role: Business Practitioner
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
translation-type: tm+mt
source-git-commit: abd5c7430c3f7a1a056a014ad46a0b94157e259f
workflow-type: tm+mt
source-wordcount: '921'
ht-degree: 97%

---

# Dernière version{#latest-release}

Cette page répertorie les nouvelles fonctionnalités, les améliorations et les correctifs de la **dernière version Release Candidate de Campaign Classic**.

>[!NOTE]
>
>Les versions de **disponibilité générale de Campaign** sont les suivantes : [[!DNL Gold Standard] 11 version](../../rn/using/gold-standard.md#gs-11) et [Campaign 20.2.5 version](../../rn/using/release--20-2.md).

## ![](assets/do-not-localize/blue_2.png) Version 21.1.2 - Build 9282 {#release-21-1-2-build-9282}

_15 avril 2021_

* La gestion des mots de passe a été améliorée pour optimiser la sécurité.
* Correction d’un problème qui pouvait provoquer des blocages MTA.

## ![](assets/do-not-localize/red_2.png) Version 21.1.1 - Build 9277 {#release-21-1-1-build-9277}

_22 février 2021_

**Améliorations de la sécurité**

* Le mécanisme d&#39;authentification de la console a été amélioré pour optimiser la sécurité. (NEO-26944)
* Correction d&#39;un problème de sécurité afin de renforcer la protection contre les problèmes SSRF (Server Side Request Forgery). (NEO-28532)

**Mises à jour de compatibilité**

Les systèmes suivants sont désormais pris en charge avec Campaign :

* L&#39;API Salesforce version 49 est désormais prise en charge lors de l&#39;utilisation du compte externe Salesforce CRM.

**Fonctionnalités obsolètes**

Le rapport de **supervision de la délivrabilité technique** est désormais obsolète.

En savoir plus dans la page [Fonctionnalités obsolètes et supprimées](../../rn/using/deprecated-features.md).

**Améliorations**

**Le service de commentaires par email (EFS)** est un service évolutif chargé de capturer directement les commentaires issus du MTA amélioré, contribuant ainsi à la précision des rapports. Cette fonctionnalité est disponible en version bêta privée et sera progressivement disponible pour tous les clients dans les prochaines versions.

* Toutes les catégories de commentaires sont maintenant capturées pour créer des rapports complets et précis.
* Le calcul de l&#39;indicateur Délivrés est désormais fondé sur les commentaires en temps réel du MTA amélioré, ce qui contribue à l&#39;amélioration de la précision et de la réactivité.
* Le service EFS résout le problème des retards grâce au reporting synchrone des soft bounces.

Pour plus d&#39;informations, consultez la [documentation détaillée](../../delivery/using/sending-with-enhanced-mta.md#efs).
Si vous souhaitez participer à cette version bêta privée, remplissez ce [formulaire](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4Rol2vQGupxItW9_BerXV6VUQTJPN1Q5WUI4OFNTWkYzQjg3WllUSDAxWi4u) et nous vous recontacterons.

**Autres changements**

* La vitesse de transfert a été améliorée pour les logs de tracking volumineux à l&#39;aide de la compression.
* La carte thermique des workflows a été améliorée afin d&#39;éviter les timeouts lors de l&#39;exécution de workflows avec plusieurs activités. (NEO-27423).
* Correction d&#39;un problème en raison duquel une offre pouvait être présentée même si sa date de fin était dépassée. Campaign Classic prend désormais en compte la date et l&#39;heure complètes de la date de fin plutôt que la date uniquement. (NEO-27590)
* Le lien Google+ a été supprimé du bloc de personnalisation **Liens de partage vers réseaux sociaux**.
* Correction d&#39;un problème après l&#39;implémentation d&#39;un correctif dans la dernière version. Une vérification a été ajoutée sur le nom d&#39;hôte lors de la connexion à l&#39;aide de SSL/TLS, ce qui a conduit à l&#39;échec des diffusions SMS. La vérification du nom d&#39;hôte a été désactivée pour la plupart des protocoles tels que POP3, SMS et HTTP avec proxy et la vérification du certificat pour le compte externe SMS a été améliorée avec trois valeurs (NEO-29581). [En savoir plus](../../delivery/using/sms-protocol.md#skip-tls)

**Correctifs**

* Correction d&#39;un problème en raison duquel les raccourcis clavier Tabulation, Entrée et Échap ne fonctionnaient pas sur le nouvel écran de connexion.
* Correction d&#39;un problème d&#39;actualisation en raison duquel le nom d&#39;un nouveau workflow était remplacé par la valeur par défaut après l&#39;enregistrement (NEO-26106).
* Correction d&#39;un problème survenant lors de l&#39;exécution de workflows où un nouveau champ a été ajouté dans le cadre d&#39;une activité **Enrichissement** avant une activité **Diffusion** à l&#39;aide d&#39;un mapping de ciblage **Fichier externe** : des champs indésirables ont été ajoutés au mapping de ciblage **Fichier externe**. (NEO-27687)
* Correction d&#39;un problème en raison duquel certains caractères du code source étaient modifiés lors de la réouverture d&#39;une application web précédemment créée et enregistrée. (NEO-27597)
* Correction d&#39;un problème qui pouvait se produire lors de la mise à niveau vers un build incluant le nouveau mécanisme de signature pour les liens de tracking (depuis la version 19.1.4 et Campaign 20.2) : lorsque plusieurs modèles étaient associés à un événement, la mise à niveau pouvait entraîner la sélection d&#39;un modèle incorrect lors de l&#39;envoi du message transactionnel. (NEO-28326)
* Correction d&#39;un problème en raison duquel le MTA ne réagissait pas et ne pouvait pas traiter les diffusions sauf s&#39;il était redémarré. (NEO-27455)
* Correction d&#39;un problème de la base de données MSSQL lié à la gestion de la date et de l&#39;heure lors des opérations de chargement en masse pour une colonne de type datetime.
* Correction d&#39;un problème de requête de workflow lors de l&#39;utilisation des fonctions xtk Redshift. Les fonctions SubDays, SubSeconds, SubMinutes et SubHours acceptent désormais les deux types de date et d&#39;heure Redshift (NEO-24962).
* Correction d&#39;un problème en raison duquel un message d&#39;erreur de script s&#39;affichait lors de la tentative de prévisualisation d&#39;un rapport avec accès anonyme. (NEO-27081)
* Correction d&#39;un problème qui pouvait réduire l&#39;utilisation de la mémoire sur le serveur lors de l&#39;analyse des diffusions.
* Correction d&#39;un problème en raison duquel l&#39;instance ne fonctionnait pas lors de l&#39;exécution de requêtes complexes spécifiques.
* Correction d&#39;un problème qui empêchait l&#39;exécution du workflow technique **Synchronisation des pages Twitter**. (NEO-28634)
* Correction d&#39;un problème qui pouvait afficher un message d&#39;erreur lié à la fonction decryptPassword lors de la tentative de publication sur Twitter à l&#39;aide du modèle de diffusion **Tweet (twitter)**. (NEO-28216)
* Correction d&#39;un problème survenant lors de l&#39;utilisation d&#39;une activité **JavaScript** pour effectuer une requête HTTP dans un workflow. Après avoir défini le numéro de port dans le nom d&#39;hôte, l&#39;appel échouait avec l&#39;erreur suivante (NEO-29146) :

```
IOB-090020 Error in SSL library: 'IOB-090013 error:14090086:SSL routines:ssl3_get_server_certificate:certificate verify failed (code 336134278)'
```

* Correction d’un problème qui empêchait l’envoi de nouvelles diffusions avec la personnalisation des données de la cible (NEO-30323).
* Correction d&#39;un problème en raison duquel plusieurs blocages se produisaient dans l&#39;instance marketing générant les fichiers principaux.
* Correction d&#39;un problème en raison duquel le workflow **Suivi** échouait avec l&#39;erreur suivante (NEO-25206) :

```
There is no index on the sourceId field of the 'NmsTrackingLogRcp' table required for the current Web tracking mode. Please add this index.
```

* Correction d&#39;un problème survenant lors de la création et de l&#39;enregistrement d&#39;une diffusion dans l&#39;onglet **Ciblage et workflow** d&#39;une campagne : la prévisualisation échouait avec l&#39;erreur suivante (NEO-29440) :

```
XTK-170024 The temporary 'temp:deliveryEmail-all' schema is not defined in the current context
```

* Correction d&#39;une erreur qui se produisait lors de la configuration d&#39;un compte externe entre une instance marketing et une instance Adobe Campaign Standard ou une instance de mid-sourcing Campaign Classic à l&#39;aide de l&#39;option &quot;DisableFOH2=1&quot;. Lors de l&#39;utilisation de l&#39;option &quot;DisableFOH2=1&quot; dans le compte externe, les connexions n&#39;étaient pas correctement fermées et s&#39;empilaient, provoquant l&#39;erreur suivante (NEO-26258) :

```
The maximum number of connections has been reached (50) by connections pool 'nms:extAccount:acsDefaultRelayAccount XXX'. The server is overloaded. Please try again later.
```

* Correction d&#39;une erreur de SMS lors de problèmes de connexion entre le serveur et le fournisseur. La connexion était alors automatiquement désactivée par l&#39;enfant MTA. Adobe Campaign Classic ne tentait pas de se connecter à cette connexion défaillante tant qu&#39;un nouvel enfant n&#39;avait pas été démarré.
