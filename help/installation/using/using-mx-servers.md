---
solution: Campaign Classic
product: campaign
title: Utilisation de serveurs MX avec Campaign
description: Découvrez comment les serveurs MX fonctionnent avec Adobe Campaign Classic.
audience: installation
content-type: reference
topic-tags: additional-configurations
hidefromtoc: true
translation-type: tm+mt
source-git-commit: 0c93193ff30737870803f9fb25019f3162dcc96d
workflow-type: tm+mt
source-wordcount: '815'
ht-degree: 0%

---


# Utilisation de serveurs MX avec Campaign {#using-mx-servers}

Découvrez comment les serveurs MX fonctionnent avec Adobe Campaign Classic.

## Serveurs MX {#mx-servers}

### Qu&#39;est-ce qu&#39;un serveur MX ?

Un enregistrement d&#39;échangeur de messagerie (enregistrement MX) est un type d&#39;enregistrement de ressource dans le DNS (Domain Name System) qui spécifie un serveur de messagerie responsable de l&#39;acceptation de messages électroniques pour le compte d&#39;un domaine.

### Comment fonctionne un serveur MX ?

Lorsque vous envoyez un courrier électronique, le serveur de logiciels établit une connexion avec le serveur de domaine du destinataire. La communication entre les deux serveurs utilise le langage SMTP et un domaine peut avoir plusieurs serveurs MX. La connexion à ce domaine sera début à partir de la priorité la plus élevée (figure la plus petite) et d&#39;autres serveurs sont appelés serveurs de sauvegarde. Le protocole de connexion doit être respecté.

### Comment fonctionne un serveur MX avec Adobe Campaign ?

Dans le protocole de connexion, les règles doivent être respectées pour empêcher le spamming et la monopolisation des serveurs. Les plus importants sont les suivants :

* **Nombre maximal de connexions autorisées** : Lorsque ce numéro est respecté, les adresses IP ne sont pas sur la liste bloquée et les courriels ne sont pas refusés en raison de connexions supplémentaires.
* **Nombre maximal de messages** : Pendant la connexion, le nombre de messages autorisés à être envoyés doit être défini. Si ce nombre n&#39;est pas défini, le serveur envoie autant que possible. Cela se traduit par l’identification d’un spammeur et l’ajout de celui-ci à la liste bloquée par le fournisseur de services Internet.
* **Messages par heure** : Afin de correspondre à votre e-réputation, Adobe Campaign contrôlera le nombre de courriers électroniques que vos adresses IP peuvent envoyer par heure. Ce système vous protègera contre les refus de courrier électronique ou/ou les listes bloquées.

## Courriers électroniques de rebonds

### Qu’est-ce qu’un courriel de rebonds ?

Il s’agit du processus utilisé par Adobe Campaign pour traiter les erreurs lors des communications du serveur.

### Comment fonctionne un courriel de rebonds ?

L&#39;adresse d&#39;erreur traitera les rebonds envoyés par les FAI. Le processus analysera différents codes d&#39;erreur SMTP et appliquera l&#39;action appropriée conformément à la norme RegEx.

Par exemple, une adresse électronique comporte un commentaire &quot;550 Utilisateur inconnu&quot; envoyé par un FAI. Ce code d’erreur est traité par l’adresse d’erreur Adobe Campaign (adresse de chemin de retour). Cette erreur est ensuite comparée à la norme RegEx et la règle appropriée sera appliquée. Le courrier électronique est considéré comme un *rebond net* (correspondant au type), puis *utilisateur inconnu* (correspondant à la raison) et envoyé en quarantaine après la première boucle dans le système.

### Comment Adobe Campaign s&#39;en sort-il ?

Adobe Campaign gère ce processus avec une correspondance entre un type d’erreur et une raison :

* **[!UICONTROL Utilisateur inconnu]** : Adresse qui est correcte d’un point de vue syntaxique mais qui n’existe pas. Cette erreur est catégorisée comme un rebond dur et envoyée en quarantaine dans la première erreur.
* **[!UICONTROL Boîte aux lettres pleine]** : Boîte aux lettres qui a atteint la capacité maximale. Cette erreur peut également indiquer que l&#39;utilisateur n&#39;utilise plus cette boîte aux lettres. Cette erreur est catégorisée comme un rebond souple et mise en quarantaine dans la troisième erreur et supprimée de la quarantaine après une période de 30 jours.
* **[!UICONTROL Utilisateur]** inactif : La boîte aux lettres a été désactivée par le fournisseur de services Internet en raison d&#39;un utilisateur inactif au cours des 6 derniers mois. Cette erreur est catégorisée comme un rebond souple et mise en quarantaine dans la troisième erreur.
* **[!UICONTROL Domaine invalide]** : Le domaine de l&#39;adresse électronique n&#39;existe pas. Cette erreur est catégorisée comme un rebond souple et mise en quarantaine dans la troisième erreur.
* **[!UICONTROL Refusé]** : Le FAI a refusé de livrer le courriel à ses utilisateurs. Cette erreur est classée comme un rebond logiciel et n’est pas mise en quarantaine car elle n’est pas liée à l’adresse électronique mais à l’adresse IP ou à la réputation d’un domaine.

>[!NOTE]
>
>Pour en savoir plus sur les types et les raisons d&#39;échec des diffusions, consultez cette [section](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons).

## Instance de délivrabilité

Une mise à jour quotidienne des règles MX et des règles de rebonds est gérée par un workflow spécifique dans l’instance client qui est connecté au propriétaire de l’instance de délivrabilité de ces règles.

Cette mise à jour quotidienne est en cours d’exécution pour tous les clients qui souhaitent garder leur instance à jour grâce à un processus de transparence.

Les règles MX comportent 6 niveaux de débit différents, qui sont principalement utilisés pendant le processus de progression :

![](assets/mx-rules-throughput.png)

Le mode Personnalisé est destiné aux clients avancés qui souhaitent définir leurs propres règles MX. Lorsque le mode personnalisé est activé, le client ne sera pas mis à jour par l&#39;instance de délivrabilité, car la synchronisation sera désactivée.

## Exemples de rebond

* **Utilisateur inconnu**  (rebond dur) : 550 5.1.1 ... L&#39;utilisateur est inconnu {mx003}
* **Boîte aux lettres pleine**  (rebond en douceur) : 550 5.2.2 Dépassement du quota d&#39;utilisateurs
* **Boîte aux lettres**  inactive (rebond progressif) : 550 5.7.1 : Adresse du destinataire refusée : Boîte de réception inactive, non affichée pendant plus de 6 mois
* **Domaine non valide**  (rebond logiciel) : Échec de la requête DNS pour &quot;ourdan.com&quot;
* **Refused**  (soft bounce) : Rebonds de courrier électronique entrant (la règle &#39;Feedback_loop_Hotmail&#39; correspond à ce rebonds)
* **Inatteignable**  (rebond progressif) : 421 4.16.55  [TS01] Messages de x.x.x.x reportés temporairement en raison de plaintes excessives de l&#39;utilisateur

**Rubriques connexes :**
* [Configuration des MX](../../installation/using/email-deliverability.md#mx-configuration)
* [Configuration technique des courriers électroniques](../../installation/using/email-deliverability.md)
* [Comprendre les échecs de Diffusion](../../delivery/using/understanding-delivery-failures.md)
* [Campaign Classic - Recommendations technique](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/product-specific-resources/campaign/acc-technical-recommendations.html)