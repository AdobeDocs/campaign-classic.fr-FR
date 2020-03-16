---
title: Dernière version
description: Dernière version
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: defbe3793be531eeb5c7aab913607ff094a624c7

---


# Dernière version{#latest-release}

[Créer une mise à niveau](https://helpx.adobe.com/campaign/kb/acc-build-upgrade.html) | Versions [du](https://docs.adobe.com/content/help/en/control-panel/using/release-notes.html) Panneau de configuration| Mises à jour [de la documentation](../../rn/using/documentation-updates.md) | Versions [précédentes](../../rn/using/release--19-2.md) | Fonctions [obsolètes](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)

<table> 
 <tbody> 
  <tr> 
   <td><img src="assets/green3.png"/><strong>Disponibilité générale</strong></td>
   <td><img src="assets/blue3.png"/><strong>Candidat à la libération</strong></td> 
   <td><img src="assets/orange3.png"/><strong>Plus disponible</strong></td> 
   <td><img src="assets/red3.png"/><strong>Obsolète</strong></td> 
  </tr> 
   <tr> 
   <td>Dernière version stable disponible. Création validée en production.<br> </td>
   <td>Génération validée par Adobe. En attente de vérification de la production.<br> </td>
   <td>Version plus récente disponible avec correctifs de bogues. La mise à jour est requise.<br> </td>
   <td>Contient des régressions connues. La mise à jour est obligatoire.<br> </td>
  </tr> 
 </tbody> 
</table>

La **dernière version** stable est 9032 (205c981c3). Click [here](../../rn/using/release--19-1.md#release-19-1-4-build-9032)

## Version 20.1.2 - Version 9123 {#release-20-1-2-build-9123}

* Correction d’un problème qui empêchait le déploiement de la version sur le serveur Red Hat 7. (NEO-23332)

## ![](assets/blue_2.png) Version 20.1 - Version 9122 {#release-20-1-build-9122}

_17 février 2020_

**Nouveautés**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Connecteur de Snowflake</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Snowflake est un entrepôt de données de cloud entièrement géré, conçu pour évoluer à la fois au niveau de l’ et au niveau de l’ordinateur. Avec ce nouveau connecteur,  Adobe Campaign peut désormais exploiter la puissance de Snowflake pour effectuer la segmentation Big Data. Ce connecteur est disponible pour tous les clients, y compris les clients hébergés par Adobe.</p>
    <p>For more information, refer to the <a href="../../platform/using/specific-configuration-database.md#configure-access-to-snowflake">detailed documentation</a> and <a href="https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/administrating/fda/big-data-segmentation-on-snowflake.html">tutorial video</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Améliorations apportées au connecteur  Hadoop</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Hadoop Connector a été amélioré pour prendre en charge Hadoop 3.0 ainsi que Cloudera.</p>
    <p>Pour plus d'informations, consultez la <a href="../../platform/using/specific-configuration-database.md#configure-access-to-hadoop-3">documentation détaillée</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

**Améliorations de la sécurité**

* Amélioration de la sécurité dans la configuration des rapports afin de protéger les utilisateurs contre le cliquage. Cela s’applique aux nouveaux rapports. Pour les anciens rapports, vous devez les republier pour appliquer les modifications. (NEO-13282)

* Correction d’un petit problème de mémoire dans cryptString. (NÉO-20071)

* Amélioration du JSP du moniteur afin de corriger une divulgation d’IP interne. (NEO-16821)

* Correction d’un problème en raison duquel les informations de suivi de pile pouvaient être affichées pour les utilisateurs non administrateurs. (NEO-12388)

* Amélioration de la gestion des données mises en cache des sessions précédentes. (NEO-17039)

* Correction d’un problème qui empêchait le fichier logins.log d’enregistrer les tentatives de connexion réussies via IMS. (NEO-11004)

**Améliorations**

* iOS 13 est désormais pris en charge avec le connecteur HTTP2.

* Amélioration de la gestion des  et du nettoyage des tables utilisées par la fonction de notification Push (nms:address et nms:appSubscriptionRcp). Pour iOS (connecteur HTTP2 uniquement), les jetons désactivés sont désormais gérés de la même manière que pour Android. L’indicateur disable est maintenant défini dans la table NmsAppSubscriptionRcp. [En savoir plus](../../production/using/database-cleanup-workflow.md#subscription-cleanup--nmac-)

* Une nouvelle option a été ajoutée dans le code **** JavaScript et le flux de travail du code **JavaScript** avancé  le pour définir une période d’expiration. Cela évite que la phase d’exécution de JavaScript ne s’exécute trop longtemps. Si le délai d’expiration s’écoule, le flux de travaux est arrêté. Le délai d’expiration par défaut est de 1 heure. [En savoir plus](../../workflow/using/sql-code-and-javascript-code.md)

* L’  est maintenant arrêté lorsqu’aucun de correspondant n’est trouvé sur le serveur de l’, le message d’erreur correspondant étant affiché.

* Le basculement de base de données pour les publications est maintenant pris en charge : lorsque le serveur de base de données se bloque et redémarre, Campaign se reconnecte désormais automatiquement.

* Le  **en attente**  a été ajouté au noeud Administration > Audit > Etat de l’. Cela vous permet de surveiller tous les  de votre instance qui attendent d’être démarrés par le processus **operationMgt** . Ce est fourni avec le package des campagnes marketing. [En savoir plus](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

**Autres changements**

* Sous Linux, le démarrage du service nlserver utilise désormais une unité système au lieu du script /etc/init.d/nlserver6. La migration vers le nouveau modèle de démarrage est effectuée automatiquement lorsque vous installez le package 20.1. Le serveur /etc/init.d/nlserver6 est toujours fourni, mais pour interagir avec le service nlserver (, redémarrage, arrêt, etc.), nous vous recommandons d’utiliser directement la commande systemctl.

* Les tables personnalisées les plus consommatrices ont été déplacées de la séquence **xtkNewId** vers des séquences dédiées. [En savoir plus](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)

* Amélioration des performances  du, qui pourraient être affectées par des connexions inutiles à la base de données.

* Amélioration des performances de l’assistant de mise à jour de la base de données.

* La gestion des enregistrements de base de données a été améliorée.

* La robustesse du pool de connexions a été améliorée, ce qui peut empêcher des échecs de connexion inattendus de se produire trop souvent.

* Les règles de validation d’adresse électronique pour envoyer une adresse au en cas d’erreur logicielle ont été améliorées. [En savoir plus](../../delivery/using/understanding-quarantine-management.md#soft-error-management)

* Pour Debian, Campaign utilise maintenant les bibliothèques PCRE système lorsqu&#39;elles sont disponibles.

* Campaign permet désormais d&#39;utiliser une bibliothèque système ODBC plus récente.

* Un délai d’expiration a été ajouté à la servlet LINE lors de l’ouverture d’une connexion pour charger une image enrichie. Si le chargement de l’image prend trop de temps, la servlet arrête la connexion pour éviter un goulot d’étranglement.

**Correctifs**

* Correction d’un problème de chiffrement des clés de compte lors de l’utilisation du connecteur Hadoop.

* Correction d’un problème de régression en raison de l’implémentation de la certification SSL, en raison duquel la connexion de l’utilisateur échouait sur le serveur Windows. (NÉO-20629)

* Correction d’un problème avec l’ incrémentiel  en cas d’ID de flux de travail négatifs. (NEO-19779)

* Correction d’un problème de codage lors de l’exécution du via le connecteur de Netezza. (NEO-19594)

* Correction d’un problème qui entraînait une erreur lors de l’utilisation de la méthode POST dans le de flux de travaux Téléchargement **** Web  .

* Correction d’un problème lié à la génération de  de. (NEO-18176)

* Correction d’un problème d’affichage du pied de page lors de l’utilisation du modèle de formulaire Web d’acquisition.

* Correction d’un problème lors de l’analyse des URL dans le contenu des  continues, qui pouvait entraîner un blocage. (NEO-16910)

* Correction d’un problème en raison duquel les champs **de** et de **fin** n’étaient pas calculés lors de la création d’une campagne.

* Correction d’un problème lié au flux de travail Téléchargement **de** fichiers   lors de l’utilisation d’une URL.

* Correction d’un problème lors de la prévisualisation d’un  de importé dans un  de  d’un rapport. (NEO-13119)

* Correction d’un problème qui affichait une image obsolète lors de la sélection du bloc de personnalisation **Optimisé par Campaign** dans l’éditeur de courrier électronique.

* La communication réseau entre le client et le serveur a été améliorée.

* Correction d’un problème en raison duquel trop de  de étaient créés dans la même campagne. Vous ne pouvez pas créer plus de 28 . Un avertissement s’affiche.

* Correction d’un problème lors de l’utilisation de l’option **Une sélection de l’option de rapprochement des colonnes** dans un **** de flux de travail .

* Correction d’un problème de plantage de la console qui pouvait se produire lors de l’utilisation d’un  endommagé dans un flux de travail. (NEO-18096)

* Correction de divers problèmes de plantage de la console qui pouvaient se produire dans les  de (NEO-18010, NEO-18032)

* Correction d’un problème en raison duquel l’exécution d’un flux de travail de signal **** externe  le était autorisée même lorsqu’il était désactivé. (NEO-17524)

* Correction d’un problème lors de la création d’un  de.

* Correction d’un problème de suivi lors de l’envoi de messages SMS. (NEO-19595)

* Correction d’un problème qui affichait un nombre  de  ciblé incorrect dans les indicateurs de .

* Correction d’un problème qui affichait des pourcentages incorrects lors de la génération d’un rapport descriptif via un flux de travail  . (NEO-14314)

* Correction d’un problème en raison duquel le rapport de débit  affichait des nombres différents lorsque le paramètre  de de temps. (NEO-11783)

* Correction d’un problème qui empêchait la mise à jour des indicateurs de suivi des  par le processus de suivi. (NEO-17770)

* Correction d’un problème de régression en raison duquel le processus Web se bloquait et redémarrait lors de la demande d’un  via SOAP. (NEO-19482)

* Correction d’un problème qui empêchait le transfert des données vers le si le répertoire de téléchargement était un emplacement partagé distant. (NEO-19361)

* Correction d’un problème en raison duquel le **Importer  à partir du flux de travail technique d’Adobe Experience Cloud** échouait constamment. (NEO-18463)

* Correction d’un problème qui empêchait l’envoi des  de lors de l’utilisation de modèles importés d’Experience Manager. (NEO-17540)

* Correction d’un problème qui survenait après la mise à niveau vers la version 9032 et qui empêchait l’instance de se connecter au serveur FTP via le protocole SSL. (NÉO-20498)

* Correction d’un problème qui se produisait lors de la suppression, de l’insertion ou de la mise à jour d’une grande quantité de données avec le **Mettre à jour les données**  dans un flux de travail à l’aide d’un de de en tant que. (NEO-13280)

* Correction d’un problème qui empêchait l’envoi des courriers électroniques lors de l’utilisation de l’instruction &quot;if&quot; en dehors de la `body` balise .

* Correction d’un problème qui se produisait lors de l’affichage du  du à partir du  d’un message envoyé. (NEO-17976)

* Correction d’un problème qui empêchait l’affichage du bloc de personnalisation **Lien vers****dans l’onglet Contenu** **texte après avoir cliqué sur** Importer du code HTMLdans un . (NEO-17568)

* Le message d’erreur s’affichait lorsque vous cliquiez sur un lien pointant vers un dont l’expiration a été clarifiée. (NEO-17340)

* Correction d’un problème qui empêchait l’utilisation de certains boutons dans l’écran de création de distribution **des** données.

* Correction d’un problème qui se produisait lors de la planification d’un   de dans une instance avec Asie/Calcutta comme fuseau horaire. (NÉO-2001)

* Une erreur s’affiche maintenant lorsqu’un  de présente un problème  de configuration de l’.

* Correction d’un problème qui affichait un numéro de balise de version incorrect dans le menu **À propos** .

* Correction d’un problème qui se produisait lors de la tentative de mise à jour du compte  à partir de propriétés de récurrentes dans un flux de travail. (NEO-18684)

* Correction d’un problème survenant lors de la connexion à l’instance via le module de redirection, qui empêchait le nettoyage correct de la connexion une fois fermée.
