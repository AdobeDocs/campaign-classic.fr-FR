---
product: campaign
title: Version 20.1
description: Version 20.1
feature: Vue d’ensemble
role: Business Practitioner
level: Beginner
exl-id: 7e4234c9-3d8f-4014-a870-75e91cfad725
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: ht
source-wordcount: '1560'
ht-degree: 100%

---

# Version 20.1{#release-20-1}

## ![](assets/do-not-localize/limited_2.png) Version 20.1.4 - Build 9126 {#release-20-1-4-build-9126}

_15 avril 2021_

* Correction d&#39;une régression de la console cliente qui provoquait des messages d&#39;erreur persistants sur l&#39;écran de connexion IMS. (NEO-34821)

**La mise à niveau de la console uniquement est obligatoire. Aucune mise à niveau du serveur n’est requise.**

>[!NOTE]
>
> Connectez-vous à la [distribution logicielle Adobe](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) pour télécharger la nouvelle version. Découvrez comment proposer la mise à jour de la console à tous les utilisateurs finaux [sur cette page](../../installation/using/client-console-availability-for-windows.md).

_22 mars 2021_

* Correction d’une régression qui empêchait l’utilisation de certains composants de la console, tels que le sélecteur de date et la gestion des images dans les diffusions. (NEO-31453, NEO-31454)

**La mise à niveau de la console uniquement est obligatoire. Aucune mise à niveau du serveur n’est requise.**

>[!NOTE]
>
> Connectez-vous à la [distribution logicielle Adobe](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) pour télécharger la nouvelle version. Découvrez comment proposer la mise à jour de la console à tous les utilisateurs finaux [sur cette page](../../installation/using/client-console-availability-for-windows.md).

_23 décembre 2020_

>[!CAUTION]
>
> * Cette version s’accompagne d’un nouveau protocole de connexion : si vous vous connectez à Campaign via Adobe Identity Service (IMS), une mise à niveau est obligatoire pour que le serveur Campaign et la console client puissent se connecter après le **30 juin 2021**.
>
> * Cette version s’accompagne d’un [correctif de sécurité](https://helpx.adobe.com/security/products/campaign/apsb21-04.html) : la mise à niveau est obligatoire pour renforcer la sécurité de votre environnement.


* Le protocole de connexion a été mis à jour pour suivre le nouveau mécanisme dʼauthentification IMS.
* Correction d’un problème de sécurité afin de renforcer la protection contre les problèmes SSRF (Server Side Request Forgery). (NEO-27777)

## ![](assets/do-not-localize/red_2.png) Version 20.1.3 - Build 9124{#release-20-1-3-build-9124}

_mercredi 6 mai 2020_

* Correction d’un problème avec l’activité de **transfert de fichier** qui empêchait le fonctionnement de l’authentification par clé SFTP sur Debian 9. (NEO-23183)

## ![](assets/do-not-localize/red_2.png) Version 20.1.2 - Build 9123{#release-20-1-2-build-9123}

_13 mars 2020_

* Correction d’une erreur qui empêchait le déploiement de la version sur les serveurs Red Hat 7. (NEO-23332)

## ![](assets/do-not-localize/red_2.png) Version 20.1 - Build 9122{#release-20-1-build-9122}

_17 février 2020_

**Nouveautés**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Connecteur Snowflake FDA</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Snowflake est un entrepôt de données dans le cloud entièrement géré, conçu pour être évolutif en termes de stockage et de puissance de calcul. Grâce à ce nouveau connecteur, Adobe Campaign peut maintenant exploiter la puissance de Snowflake pour segmenter les mégadonnées (Big Data). Ce connecteur est disponible pour tous les clients, notamment les clients hébergés par Adobe.</p>
    <p>Pour plus d’informations, consultez la <a href="../../installation/using/configure-fda-snowflake.md">documentation détaillée</a> et regardez le <a href="https://docs.adobe.com/content/help/fr-FR/campaign-classic-learn/tutorials/administrating/fda/big-data-segmentation-on-snowflake.html">tutoriel vidéo</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Améliorations apportées au connecteur Hadoop FDA</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Le connecteur Hadoop FDA a été amélioré pour prendre en charge Hadoop 3.0 ainsi que Cloudera.</p>
    <p>Pour plus d’informations, consultez la <a href="../../installation/using/configure-fda-hadoop.md">documentation détaillée</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

**Améliorations de la sécurité**

* Amélioration de la sécurité de la configuration des rapports pour protéger les utilisateurs contre le détournement de clic (clickjacking). Cette amélioration s’applique aux nouveaux rapports. Pour les anciens rapports, vous devez les republier pour appliquer les modifications. (NEO-13282)

* Correction d’un petit problème de mémoire dans cryptString. (NEO-20071)

* Amélioration de la fonction monitor JSP pour corriger une divulgation de propriété intellectuelle interne. (NEO-16821)

* Correction d’un problème en raison duquel les informations de traçage de pile pouvaient être affichées pour des utilisateurs non administrateurs. (NEO-12388)

* Amélioration de la gestion des données mises en cache des sessions précédentes. (NEO-17039)

* Correction d’un problème qui empêchait le fichier logins.log d’enregistrer les tentatives de connexion réussies via IMS. (NEO-11004)

**Améliorations**

* iOS 13 est maintenant pris en charge avec le connecteur HTTP2.

* Amélioration de la gestion des quarantaines et du nettoyage des tables utilisées par la fonction de notification push (nms:address et nms:appSubscriptionRcp). Pour iOS (connecteur HTTP2 uniquement), les jetons désactivés sont maintenant gérés de la même manière que pour Android. Le drapeau disable est maintenant défini dans la table NmsAppSubscriptionRcp. [En savoir plus](../../production/using/database-cleanup-workflow.md#subscription-cleanup--nmac-)

* Une nouvelle option a été ajoutée dans les activités de workflow **Code JavaScript** et **Code JavaScript avancé** pour définir un délai d’expiration. Cela permet d&#39;éviter une phase d’exécution JavaScript trop longue. Une fois le délai d’expiration écoulé, le workflow est arrêté. Le délai d’expiration par défaut est d’une heure. [En savoir plus](../../workflow/using/sql-code-and-javascript-code.md)

* L’analyse de diffusion est désormais arrêtée lorsqu’aucune affinité correspondante n’a été trouvée sur le serveur de mid-sourcing. Le message d’erreur associé est ensuite affiché.

* Le basculement de base de données pour Postgres est maintenant pris en charge : lorsque le serveur de base de données se bloque et redémarre, Campaign se reconnecte désormais automatiquement.

* La vue **Démarrage en attente** a été ajoutée au nœud Administration > Suivi > Statut des workflows. Il est ainsi possible de surveiller tous les workflows de votre instance qui attendent d’être démarrés par le processus **operationMgt**. Cette vue est proposée avec le package des campagnes marketing. [En savoir plus](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

**Autres changements**

* Sous Linux, le démarrage du service nlserver utilise maintenant une unité systemd au lieu du script /etc/init.d/nlserver6. La migration vers le nouveau schéma de démarrage est effectuée automatiquement lors de l’installation du package 20.1. Le serveur /etc/init.d/nlserver6 est encore fourni, mais pour interagir avec le service nlserver (démarrage, redémarrage, arrêt, etc.), nous vous recommandons d’utiliser directement la commande systemctl.

* Les tables personnalisées les plus consommatrices ont été déplacées de la séquence **xtkNewId** vers des séquences dédiées. [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)

* Amélioration des performances des requêtes, qui pourraient être affectées par des connexions inutiles à la base de données.

* Amélioration des performances de l&#39;assistant de mise à jour de la base de données afin de réduire le nombre d&#39;instructions SQL dans le but d&#39;optimiser le temps de réponse.

* La gestion des enregistrements de la base de données a été améliorée.

* La robustesse du pool de connexions a été améliorée, ce qui peut empêcher des échecs de connexion inattendus trop fréquents.

* Les règles de validation des adresses email pour envoyer une adresse en quarantaine en cas d’erreur soft ont été améliorées. [En savoir plus](../../delivery/using/understanding-quarantine-management.md#soft-error-management)

* Pour Debian, Campaign utilise maintenant les bibliothèques PCRE système lorsqu’elles sont disponibles.

* Campaign permet désormais d’utiliser une bibliothèque système ODBC plus récente.

* Un délai d’expiration a été ajouté à la servlet LINE lors de l’ouverture d’une connexion pour charger une image enrichie. Si le chargement de l’image prend trop de temps, la servlet arrête la connexion pour éviter un goulot d’étranglement.

**Correctifs**

* Correction d’un problème de chiffrement des clés de compte lors de l’utilisation du connecteur Hadoop.

* Correction d’un problème de régression lié à l’implémentation de la certification SSL, en raison duquel la connexion de l’utilisateur échouait sur Windows Server. (NEO-20629)

* Correction d’un problème lié à l’activité de requête incrémentale en cas d’ID de workflow négatifs. (NEO-19779)

* Correction d’un problème de codage lors de l’exécution de requêtes via le connecteur Netezza FDA. (NEO-19594)

* Correction d’un problème qui entraînait une erreur lors de l’utilisation de la méthode POST dans l’activité d’événement de workflow **Téléchargement Web**.

* Correction d’un problème lié à la génération de propositions d’offres. (NEO-18176)

* Correction d’un problème d’affichage du pied de page lors de l’utilisation du modèle de formulaire web d’acquisition.

* Correction d’un problème lors de l’analyse des URL dans le contenu des diffusions au fil de l’eau, qui pouvait entraîner un blocage. (NEO-16910)

* Correction d’un problème en raison duquel les champs **Début** et **Fin** n’étaient pas calculés lors de la création d’une campagne.

* Correction d’un problème lié à l’activité de workflow **Réception de fichier** lors de l’utilisation d’une adresse URL.

* Correction d’un problème lors de la prévisualisation d’une liste importée dans une activité de rapport. (NEO-13119)

* Correction d’un problème qui provoquait l’affichage d’une image obsolète lors de la sélection du bloc de personnalisation **Powered by Campaign** dans l’éditeur d’email.

* La communication réseau entre le client et le serveur a été améliorée.

* Correction d’un problème résultant de la création d’un trop grand nombre de workflows dans la même campagne. Vous ne pouvez maintenant pas en créer plus de 28. Un avertissement s’affiche.

* Correction d’un problème lors de l’utilisation de l’option de réconciliation **Une sélection de colonnes** dans une activité de workflow **Union**.

* Correction d’un problème de blocage de la console qui se produisait lors de l’utilisation d’une liste d’enrichissement endommagée dans un workflow. (NEO-18096)

* Correction de différents problèmes de blocage de la console qui se produisaient dans les workflows (NEO-18010, NEO-18032)

* Correction d’un problème qui autorisait l’exécution d’une activité de workflow **Signal externe** même lorsqu’elle était désactivée. (NEO-17524)

* Correction d’un problème lors de la création d’un nouveau schéma.

* Correction d’un problème de tracking lors de l’envoi de messages SMS. (NEO-19595)

* Correction d’un problème qui affichait un nombre incorrect d’audiences ciblées dans les indicateurs de diffusion.

* Correction d’un problème qui affichait des pourcentages incorrects lors de la génération d’un rapport descriptif via une activité de workflow. (NEO-14314)

* Correction d’un problème en raison duquel le rapport de débit des diffusions affichait des nombres différents selon le paramètre d’affichage de l’heure. (NEO-11783)

* Correction d’un problème qui empêchait la mise à jour des indicateurs de tracking des messages transactionnels par le workflow de tracking. (NEO-17770)

* Correction d’un problème de régression en raison duquel le processus web se bloquait et redémarrait lors de la demande d’une offre via SOAP. (NEO-19482)

* Correction d’un problème qui empêchait le chargement des données vers des ressources publiques si le répertoire de chargement était un emplacement partagé distant. (NEO-19361)

* Correction d’un problème en raison duquel le workflow technique **Import d’audiences depuis Adobe Experience Cloud** échouait constamment. (NEO-18463)

* Correction d’un problème qui empêchait l’envoi des diffusions lors de l’utilisation de modèles importés à partir d’Experience Manager. (NEO-17540)

* Correction d’un problème qui se produisait après un upgrade vers le build 9032 et qui empêchait l’instance de se connecter au serveur FTP à l’aide du protocole SSL. (NEO-20498)

* Correction d’un problème qui se produisait lors de la suppression, de l’insertion ou de la mise à jour d’une grande quantité de données avec l’activité de **mise à jour des données** dans un workflow à l’aide d’un schéma FDA servant de dimension de ciblage. (NEO-13280)

* Correction d&#39;un problème qui empêchait l&#39;envoi d&#39;emails lorsque du code JavaScript se trouvait en dehors de la balise de contenu HTML. (NEO-18628)

* Correction d’un problème qui se produisait lors de l’affichage de la page miroir depuis les logs de diffusion d’un message envoyé. (NEO-17976)

* Correction d’un problème qui empêchait l’affichage du bloc de personnalisation **Lien vers la page miroir** de l’onglet **Contenu texte** après avoir cliqué sur **Importer le HTML** dans une diffusion. (NEO-17568)

* Clarification du message d’erreur affiché après un clic sur un lien vers une page miroir ayant dépassé le délai d’expiration. (NEO-17340)

* Correction d’un problème qui empêchait l’utilisation de certains boutons dans l’écran de création de **répartition des données**.

* Correction d’un problème qui se produisait lors de la planification d’une activité de diffusion dans une instance dont le fuseau horaire était Asie/Calcutta. (NEO-20001)

* Une erreur s’affiche maintenant lorsqu’une diffusion rencontre un problème de configuration de l’affinité.

* Correction d’un problème qui affichait un numéro de balise de version incorrect dans le menu **À propos**.

* Correction d’un problème qui se produisait lors d’une tentative de mise à jour du compte de routage à partir des propriétés de diffusion récurrente dans un workflow. (NEO-18684)

* Correction d’un problème qui se produisait lors de la connexion à l’instance via le module de redirection. Celui-ci empêchait le nettoyage correct de la connexion une fois fermée.
