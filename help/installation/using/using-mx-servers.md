---
product: campaign
title: Utilisation de serveurs MX avec Campaign
description: Découvrez le fonctionnement des serveurs MX avec Adobe Campaign Classic.
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
badge-v7-prem: label="On-premise et hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"
audience: installation
content-type: reference
topic-tags: additional-configurations
hidefromtoc: true
exl-id: 47f50bf5-4d5b-4c07-af71-de4390177cf5
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '839'
ht-degree: 100%

---

# Utilisation de serveurs MX avec Campaign {#using-mx-servers}



Découvrez le fonctionnement des serveurs MX avec Adobe Campaign Classic.

## Serveurs MX {#mx-servers}

### Qu’est-ce qu’un serveur MX ?

Un enregistrement d’échangeur de messagerie (enregistrement MX) est un type d’enregistrement de ressource du DNS (Domain Name System) qui spécifie un serveur de messagerie responsable de l’acceptation des emails pour le compte d’un domaine.

### Comment fonctionne un serveur MX ?

Lorsque vous envoyez un email, le serveur de logiciels établit une connexion avec le serveur de domaine du destinataire. La communication entre les deux serveurs utilise le langage SMTP et un domaine peut avoir plusieurs serveurs MX. La connexion à ce domaine débute par la priorité la plus élevée (valeur la plus petite) et les autres serveurs sont appelés serveurs de « secours ». Le protocole de connexion doit être respecté.

### Comment fonctionne un serveur MX avec Adobe Campaign ?

Avec le protocole de connexion, les règles doivent être respectées pour empêcher la production de spam et la monopolisation des serveurs. Les règles les plus importantes sont les suivantes :

* **Nombre maximum de connexions autorisées** : lorsque ce nombre est respecté, les adresses IP ne sont pas sur la liste bloquée et les emails ne sont pas refusés en raison de connexions supplémentaires.
* **Nombre maximum de messages** : en cours de connexion, il est nécessaire de définir le nombre de messages dont l’envoi est autorisé. Si ce nombre n’est pas défini, le serveur effectue autant d’envois que possible. Cela se traduit par l’identification d’un spammeur et l’ajout de celui-ci à la liste bloquée par le fournisseur de services Internet.
* **Messages par heure** : pour assurer votre e-réputation, Adobe Campaign contrôle le nombre d’emails que vos adresses IP peuvent envoyer par heure. Ce système vous protège contre les refus d’emails et/ou les listes bloquées.

## Mails rebonds

### Qu’est-ce qu’un mail rebond ?

Il s’agit du processus utilisé par Adobe Campaign pour traiter les erreurs lors des communications du serveur.

### Comment fonctionne un mail rebond ?

L’adresse d’erreur traite les retours renvoyés par les FAI. Le processus analyse différents codes d’erreur SMTP et applique l’action appropriée, conformément à la norme RegEx.

Par exemple, une adresse email provoque un retour « 550 Utilisateur inconnu » envoyé par un FAI. Ce code d’erreur est traité par l’adresse d’erreur Adobe Campaign (adresse de chemin de retour). Cette erreur est ensuite comparée à la norme RegEx et la règle appropriée est appliquée. L’email est considéré comme une *erreur hard* (correspondant au type), avec un *utilisateur inconnu* (correspondant à la raison). Il est ensuite envoyé en quarantaine après la première boucle dans le système.

### Comment Adobe Campaign gère-t-il la situation ?

Adobe Campaign gère ce processus en établissant une correspondance entre un type d’erreur et une raison :

* **[!UICONTROL Utilisateur inconnu]** : adresse correcte du point de vue syntaxique, mais inexistante. Cette erreur est catégorisée comme une erreur hard et conduit à une mise en quarantaine dès la première erreur.
* **[!UICONTROL Boîte pleine]** : boîte aux lettres qui a atteint sa capacité maximale. Cette erreur peut également indiquer que l’utilisateur n’utilise plus cette boîte aux lettres. L’erreur est catégorisée comme une erreur soft et conduit à une mise en quarantaine à la troisième erreur et à une suppression dans la quarantaine suite à une période de 30 jours.
* **[!UICONTROL Utilisateur inactif]** : la boîte aux lettres a été désactivée par le fournisseur d’accès à Internet, car l’utilisateur a été inactif au cours des 6 derniers mois. Cette erreur est catégorisée comme une erreur soft et conduit à une mise en quarantaine à la troisième erreur.
* **[!UICONTROL Domaine invalide]** : le domaine de l’adresse email n’existe pas. Cette erreur est catégorisée comme une erreur soft et conduit à une mise en quarantaine à la troisième erreur.
* **[!UICONTROL Refusé]** : Le FAI a refusé de remettre l’email à ses utilisateurs. Cette erreur est classée comme une erreur soft et n’aboutit pas à une mise en quarantaine, car elle n’est pas liée à l’adresse email mais à l’adresse IP ou à la réputation d’un domaine.

>[!NOTE]
>
>Pour en savoir plus sur les types et les raisons d’un échec des diffusions, consultez cette [section](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons).

## Instance de délivrabilité {#deliveratbility-env}

Une mise à jour quotidienne des règles MX et des règles de rebond est gérée par un workflow spécifique dans l’instance client qui est connectée au propriétaire de l’instance de délivrabilité de ces règles.

Cette mise à jour quotidienne s’applique à tous les clients qui souhaitent garder leur instance à jour par le biais d’un processus de transparence.

Les règles MX comportent 6 niveaux de débit différents, principalement utilisés au cours de la phase de démarrage :

![](assets/mx-rules-throughput.png)

Le mode personnalisé est destiné aux clients avancés qui souhaitent définir leurs propres règles MX. Lorsque le mode personnalisé est activé, le client ne sera pas mis à jour par l’instance de délivrabilité, car la synchronisation sera désactivée.

## Exemples de rebonds

* **Utilisateur inconnu** (erreur hard) : 550 5.1.1 ... L’utilisateur est inconnu {mx003}
* **Boîte pleine** (erreur soft) : 550 5.2.2 Dépassement du quota d’utilisateurs
* **Boîte aux lettres inactive** (erreur soft) : 550 5.7.1 : adresse du destinataire refusée : boîte aux lettres inactive, non affichée pendant plus de 6 mois
* **Domaine invalide** (erreur soft) : échec de la requête DNS pour ’ourdan.com’
* **Refusé** (erreur soft) : retour de mail entrant (la règle ’Feedback_loop_Hotmail’ correspond à ce retour)
* **Inatteignable** (erreur soft) : 421 4.16.55 [TS01] Messages de x.x.x.x reportés temporairement en raison de plaintes excessives de l’utilisateur

**Rubriques connexes :**
* [Configuration des MX](../../installation/using/email-deliverability.md#mx-configuration)
* [Configuration technique des emails](../../installation/using/email-deliverability.md)
* [Présentation des diffusions en échec](../../delivery/using/understanding-delivery-failures.md)
* [Campaign Classic - Recommandations techniques](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/campaign/acc-technical-recommendations.html?lang=fr)
