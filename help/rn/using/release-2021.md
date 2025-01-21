---
product: campaign
title: Versions de Campaign Classic 2021
description: En savoir plus sur les versions de Campaign Classic 2021
feature: Release Notes
role: User
level: Beginner
hidefromtoc: true
exl-id: 0cd6bf20-da72-4cf0-9f5d-d4e8acdd324d
source-git-commit: a1dbef3e1feca1e3347de013db8bd7809d315016
workflow-type: tm+mt
source-wordcount: '2586'
ht-degree: 100%

---

# Versions 2021{#release-2021}

## Version 7.1 (21.1)

>[!CAUTION]
>Utilisez le menu **[!UICONTROL Aide > À propos…]** pour vérifier votre [numéro de version et de build](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version) d’Adobe Campaign. Notez toutefois que pour toutes les builds entre 9277 et 9343 répertoriées sur cette page, le numéro de version indique 7.0 au lieu de 7.1.
> 

### Version 21.1.4 - Build 9343 {#release-21-1-4-build-9343}

[!BADGE Obsolète]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=fr#rn-statuses" tooltip="Obsolète"}

_8 octobre 2021_

**Correctifs**

* Amélioration du correctif pour le workflow de facturation disponible dans la version 9342, qui nécessitait un redémarrage manuel du workflow afin dʼêtre appliqué. Désormais, le postupgrade redémarre automatiquement le workflow.

* Correction dʼun problème qui pouvait entraîner le fonctionnement incorrect de la gestion des offres lors de lʼutilisation du module **Interaction** avec lʼoption [Power Booster](../../installation/using/power-booster-and-power-cluster.md) déployée. (NEO-39263)

* Correction dʼune erreur « Lʼaffinité IP xxx est introuvable sur le serveur MID xxx » qui pouvait se produire lors de lʼenvoi dʼune diffusion comportant plusieurs affinités IP sur une instance multi-midsourcing. (NEO-37514)

### Version 21.1.4 - Build 9342 {#release-21-1-4-build-9342}

[!BADGE Obsolète]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=fr#rn-statuses" tooltip="Obsolète"}

_7 septembre 2021_

**Amélioration de la sécurité**

* Correction d’un problème de sécurité afin de renforcer la protection contre les attaques par traversée de répertoires. (NEO-28547)

**Améliorations**

* Après sa fin de vie, Flash a été supprimé de toutes les fonctionnalités et composants de Campaign associés, et remplacé par HTML5. Le type de graphique **Jauge** a été supprimé. (NEO-30330) [En savoir plus](../../reporting/using/creating-a-chart.md)
* Lors de l’installation de la console cliente sous Windows, le programme d’installation vérifie maintenant s’il existe un nœud de registre parent et en crée un s’il n’en existe pas. Cela évite les problèmes potentiels lors du lancement de la console. (NEO-34854)
* La fonctionnalité de signature de tracking a été améliorée afin d’éviter les erreurs liées à la façon dont les outils tiers (clients de messagerie, navigateurs internet, etc.) gèrent les caractères spéciaux. Les paramètres d’URL sont désormais chiffrés.

**Autres changements**

* Correction d’une régression introduite dans la version 21.1.3 avec le nouveau mécanisme de sécurisation du workflow de facturation. Le workflow de facturation a été exécuté sur des instances incorrectes et sʼest bloqué lors de la tentative dʼenvoi du rapport de facturation, qui n’avait pas été généré. Vous devez redémarrer manuellement le workflow pour que le correctif soit appliqué.
* Les connecteurs Microsoft CRM (déploiements Office 365 et On-premise) précédemment obsolètes ont été supprimés de l’interface. [En savoir plus](../../platform/using/crm-ms-dynamics.md#configure-acc-for-microsoft)
* Suite à la migration vers Tomcat 8, le script de configuration IIS a été mis à jour afin de corriger les problèmes d&#39;intégration IIS. (NEO-31019)
* L&#39;identification de la source de données a été améliorée dans les onglets de données et de schéma de la fenêtre **Visualiser la population** des transitions de workflow.
* Des index de base de données manquants ont été ajoutés aux schémas suivants afin d’éviter des problèmes de mise à jour de la base de données : xtk:rights, nms:dlvExclusion, nms:seedMember, nms:trackingUrl

**Correctifs**

* Correction d’un problème qui empêchait le fonctionnement du rapport Position des clics lorsque des offres étaient liées à la diffusion. (NEO-26295)
* Correction d’un problème lié à l’activité **Sous-workflow** lorsque son exécution ne générait pas de table de sortie. (NEO-36242)
* Correction de divers problèmes lors de l’exportation du rapport **Analyse descriptive** au format PDF. (NEO-25847)
* Correction d’un problème qui entraînait l’échec des diffusions lors de l’utilisation d’une diffusion par courrier externe. (NEO-37435)
* Correction d&#39;une erreur lors de la connexion à Microsoft CRM à l&#39;aide de l&#39;API web. Le message d’erreur a été supprimé, car les fonctionnalités n’ont pas été affectées.
* Correction d’un problème de déduplication des logs de tracking lorsque le serveur mid-sourcing était défini comme relais entre les serveurs de tracking et marketing. (NEO-36285)
* Correction d’une régression qui empêchait Vault d’être utilisé comme entrepôt de code spécifique.
* Correction d’un problème qui empêchait l’utilisation de variables dans une activité de workflow **Enrichissement** lorsque la transition entrante provenait d’une source de données FDA.
* Correction d’un problème qui entraînait des URL rompues dans les e-mails.

### Version 21.1.3 - Build 9330 {#release-21-1-3-build-9330}

[!BADGE Obsolète]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=fr#rn-statuses" tooltip="Obsolète"}

_5 juin 2021_

**Nouveautés**


<table>
<thead>
<tr>
<th><strong>Nouvelle activité de workflow : Modifier la source de données</strong><br/></th>
</tr>
</thead>
<tbody>
<tr>
<td>
<p>La nouvelle activité de workflow <b>Modifier la source de données</b> permet de modifier la source de données de la table de travail d’un workflow. Cela offre plus de flexibilité pour la gestion des données entre différentes sources de données (FDA et base de données locale).</p>
<p>Dans les workflows Adobe Campaign, les données sont gérées à l’aide de tables de travail (ou temporaires). Au fur et à mesure de l’exécution d’un workflow, les tables de travail partagent les données entre les activités du workflow. Par défaut, les tables de travail sont créées dans la même base de données que la source des données sur lesquelles nous effectuons des requêtes.</p>
<p>Pour plus d'informations, consultez la <a href="../../workflow/using/change-data-source.md">documentation détaillée</a>.</p>
</td>
</tr>
</tbody>
</table>

<table>
<thead>
<tr>
<th><strong>Intégration avec Adobe Journey Orchestration</strong><br/></th>
</tr>
</thead>
<tbody>
<tr>
<td>
<p>L’intégration entre Journey Orchestration et Adobe Campaign Classic est maintenant en disponibilité générale (GA). Cette intégration permet à Journey Orchestration d’envoyer des e-mails, des notifications push et des SMS à l’aide des fonctionnalités de messagerie transactionnelle d’Adobe Campaign Classic.</p>
<p>La connexion entre les instances Journey Orchestration et Campaign Classic est configurée par Adobe au moment de l’approvisionnement.</p>
<p>Pour plus d'informations, consultez la <a href="https://experienceleague.adobe.com/docs/journeys/using/action-journeys/acc-action.html?lang=fr">documentation Journey Orchestration </a>. Un cas pratique étape par étape est présenté dans cette <a href="https://experienceleague.adobe.com/docs/journeys/using/use-cases-journeys/campaign-classic-use-case.html?lang=fr">section</a></p>
</td>
</tr>
</tbody>
</table>

<table> 
<thead>
<tr> 
<th> <strong>Améliorations du canal LINE</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>Les améliorations suivantes ont été apportées au canal LINE :
</p>
<ul> 
<li><p>Prise en charge du type de message vidéo LINE</p></li>
<li><p>Prise en charge de l’API d’enregistrement de partenaire LINE</p></li>
<li><p>Prise en charge des reprises d’envoi de messages en cas d’erreur côté serveur LINE ou d’expiration du réseau</p></li>
</ul>
<p>Pour plus d’informations, consultez la <a href="../../delivery/using/line-channel.md">documentation détaillée</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead>
<tr> 
<th> <strong>Connecteur FDA Vertica Analytics</strong><br/> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>Vous pouvez maintenant connecter votre instance Adobe Campaign Classic à votre base de données externe Vertica. Cette connexion est gérée à l’aide d’un nouveau compte externe.</p>
<p>Pour plus d’informations, consultez la <a href="../../installation/using/configure-fda-vertica.md">documentation détaillée</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead>
<tr> 
<th> <strong>Connecteur FDA Google BigQuery</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>Vous pouvez maintenant connecter votre instance Adobe Campaign Classic à votre base de données externe Google BigQuery. Cette connexion est gérée à l’aide d’un nouveau compte externe.
</p>
<p>Pour plus d’informations, consultez la <a href="../../installation/using/configure-fda-google-big-query.md">documentation détaillée</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

**Améliorations de la sécurité**

* L’accès à la méthode d’API **xtk:session#GetCnxInfo** renvoyant les détails complets de la connexion à la base de données est maintenant limité aux utilisateurs administrateurs uniquement. (NEO-27779)
* La fonction decryptString obsolète a été remplacée par decryptPassword dans les fichiers JavaScript liés au CRM.
* La fonctionnalité de signature de tracking a été améliorée afin de réduire le risque d&#39;erreurs de redirection lors de la modification du lien suivi par des outils tiers (clients de messagerie, navigateurs Internet, outils de sécurité des liens).
* Correction d’un problème qui empêchait le fonctionnement des URL suivies lorsqu’elles contenaient des caractères majuscules. Le mécanisme de signature des URL suivies respecte maintenant la casse. (NEO-28414)

**Mises à jour de compatibilité**

Les systèmes suivants sont désormais pris en charge avec Campaign :
* Connecteur FDA Google BigQuery
* Connecteur FDA Vertica Analytics
* PostgreSQL 13

En savoir plus sur la [Matrice de compatibilité de Campaign](../../rn/using/compatibility-matrix.md).

**Fonctionnalités obsolètes**

* À compter de la version 21.1 de Campaign, le connecteur de données Adobe Analytics est obsolète. Si vous utilisez ce connecteur, vous devez adapter en conséquence votre implémentation au nouveau connecteur Adobe Analytics.
* La prise en charge de Debian 8 est maintenant obsolète.
* Suite à la dépréciation d&#39;Oracle CRM dans la version 20.3, le compte externe associé a été supprimé de l’interface.

En savoir plus dans la page [Fonctionnalités obsolètes et supprimées](../../rn/using/deprecated-features.md).

**Améliorations**

* Des vérifications supplémentaires ont été ajoutées lors de l’enregistrement d’un workflow pour s’assurer que les noms des activités sont uniques et que les transitions sont toujours suivies d’une activité.
* Le workflow technique **Facturation (billing)** comprend maintenant les tâches effectuées à l’origine par le workflow **Comptage des profils actifs** (billingActiveContactCount), qui a été supprimé. Le rapport sur les emails envoyé chaque mois par le workflow fournit désormais des informations sur le nombre de profils actifs sur l&#39;instance. [En savoir plus](../../workflow/using/about-technical-workflows.md).
* Un nouvel attribut **_keyOnMData** a été ajouté pour pouvoir utiliser une clé pour les opérations sur les données de mémo.

**Autres modifications**

* Un mécanisme de sécurisation a été ajouté pour permettre uniquement l’exécution du [workflow technique de facturation](../../production/using/monitoring-processes.md#billing-report) sur l’instance marketing.
* Le tiers openssl pour Windows a été mis à jour vers la version 1.1.1h.
* Dans la description du package Debian, nlserver a été changé en serveur Adobe Campaign Classic.

**Correctifs**

* Correction d’un problème lors de la modification du timeout de session afin de déconnecter les utilisateurs après une durée spécifique (les utilisateurs restaient connectés même après la durée définie).
* Correction d’un problème en raison duquel les diffusions s’affichaient en lecture seule mais pouvaient toujours être modifiées dans les propriétés des diffusions.
* Correction d&#39;une erreur qui entraînait la disparition de la barre d&#39;outils d&#39;édition lors de la conception d&#39;une application web.
* Correction d&#39;une erreur qui affichait la version texte d&#39;un email avec des en-têtes Adobe Campaign Classic lors de l&#39;ajout d&#39;un lien vers un email. (NEO-29211
* Lors de l’utilisation de la connexion FDA via HTTPS, le workflow **Mid-sourcing (logs de diffusion)** (defaultMidSourcingLog) était bloqué dans le délai défini par l’option **NmsMidSourcing_LogsPeriodHour**. Cela empêchait la mise à jour des enregistrements avec les données produites après cette période définie. (NEO-30833)
* Correction d’un problème qui se produisait après l’exécution du workflow de synchronisation de Message Center. Chaque fois qu’un dossier d’objets de diffusion était déplacé vers un dossier personnalisé, le workflow déplaçait les diffusions vers le dossier **Historique des messages transactionnels** générique. (NEO-27445)
* Correction d’un problème qui affichait un message d’erreur lors de l’affichage des rapports **Statistiques de diffusion**, **Indicateurs de tracking** et **Statistiques des activités de partage**.
* L&#39;activité de workflow **Oracle On Demand** a été supprimée de l&#39;interface suite à la dépréciation du connecteur CRM Oracle.
* Correction d’un problème qui arrêtait l’exécution des workflows de traitement après le redémarrage quotidien du module de serveur de workflows (wfserver). (NEO-30047)
* Correction d’un problème qui empêchait la mise à jour du document de gestion des MX, ce qui pouvait avoir un impact négatif sur la réputation des adresses IP. (NEO-29897)
* Correction de problèmes qui entraînaient des blocages de processus web lors de la réception d’un appel SOAP. (NEO-28796) (NEO-29600)
* Correction d’un problème en raison duquel la création de l’index FDA SAP HANA échouait. (NEO-29664)
* Correction d’un problème qui entraînait le maintien des messages transactionnels dans l’état **En attente** lors de l’exécution d’appels SOAP contenant un en-tête. (NEO-28737)
* Correction d’un problème qui se produisait lors de l’utilisation du connecteur FDA Teradata : toutes les tables temporaires étaient créées sur un seul nœud du cluster, ce qui pouvait consommer tout l’espace du spool et provoquer le blocage de Teradata. Les tables temporaires sont maintenant générées sur de nombreux nœuds. (NEO-28230)
* Correction d’un problème lors de l’utilisation d’applications web en raison duquel les balises de tracking généraient des clés primaires incorrectes dans le schéma **nms:trackingURL**. (NEO-27931)
* La compatibilité avec ODBC 3.x a été améliorée pour garantir la précision des messages d’erreur.
* Correction d’un problème qui entraînait des blocages de console lors de l’utilisation de modèles de contenu personnalisés dans des diffusions email. (NEO-31547)
* Correction d’un problème qui empêchait Tomcat d’envoyer des réponses valides en raison d’une connexion lente ou d’une taille de réponse importante. (NEO-30858)
* Correction d’un problème qui se produisait lors de la lecture de la valeur UUID à partir d’une base de données PostgreSQL.
* Correction d’une erreur qui entraînait des problèmes de performances lors de la recherche de données de proposition liées aux offres. (NEO-27554)
* Correction d’un problème en raison duquel le processus web ne répondait pas lorsque le service IMS était activé, mais ne répondait pas.
* Correction d’un problème qui empêchait l’envoi d’une diffusion avec un groupe de BAT en raison d’un mécanisme d’association spécifique qui faisait échouer la personnalisation de la diffusion. (NEO-14391)
* Correction d’un problème qui empêchait l’envoi d’une alerte avec l’activité d’alerte si une requête et une activité d’enrichissement ciblaient la table de diffusions. (NEO-25157)

### Version 21.1.2 - Build 9282 {#release-21-1-2-build-9282}

[!BADGE Obsolète]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=fr#rn-statuses" tooltip="Obsolète"}

_15 avril 2021_

* La gestion des mots de passe a été améliorée pour optimiser la sécurité.
* Correction d&#39;un problème qui pouvait provoquer des blocages de MTA.

### Version 21.1.1 - Build 9277 {#release-21-1-1-build-9277}

[!BADGE Obsolète]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=fr#rn-statuses" tooltip="Obsolète"}

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

**Le service de retour d&#39;e-mail (EFS - Email Feedback Service)** est un service évolutif chargé de capturer directement les retours du MTA amélioré, contribuant ainsi à la précision des rapports.
Cette fonctionnalité est disponible en version bêta privée et sera progressivement disponible pour tous les clients dans les prochaines versions.

* Toutes les catégories de commentaires sont maintenant capturées pour créer des rapports complets et précis.
* Le calcul de l&#39;indicateur Délivrés est désormais fondé sur les commentaires en temps réel du MTA amélioré, ce qui contribue à l&#39;amélioration de la précision et de la réactivité.
* EFS résout le problème des retards grâce au reporting synchrone des rebonds temporaires.


**Autres changements**

* La vitesse de transfert a été améliorée pour les logs de tracking volumineux à l&#39;aide de la compression.
* La carte thermique des workflows a été améliorée afin d&#39;éviter les timeouts lors de l&#39;exécution de workflows avec plusieurs activités. (NEO-27423).
* Correction d&#39;un problème en raison duquel une offre pouvait être présentée même si sa date de fin était dépassée. Campaign Classic prend désormais en compte la date et l&#39;heure complètes de la date de fin plutôt que la date uniquement. (NEO-27590)
* Le lien Google+ a été supprimé du bloc de personnalisation **Liens de partage vers réseaux sociaux**.
* Correction d&#39;un problème après l&#39;implémentation d&#39;un correctif dans la dernière version. Une vérification a été ajoutée sur le nom d&#39;hôte lors de la connexion à l&#39;aide de SSL/TLS, ce qui a conduit à l&#39;échec des diffusions SMS. La vérification du nom d&#39;hôte a été désactivée pour la plupart des protocoles tels que POP3, SMS et HTTP avec proxy et la vérification du certificat pour le compte externe SMS a été améliorée avec trois valeurs (NEO-29581). [En savoir plus](../../delivery/using/sms-protocol.md#skip-tls)

**Correctifs**

* Correction du défaut de fonctionnement des raccourcis clavier Tabulation, Entrée et Echap sur le nouvel écran de connexion.
* Correction d&#39;un problème d&#39;actualisation en raison duquel le nom d&#39;un nouveau workflow était remplacé par la valeur par défaut après l&#39;enregistrement (NEO-26106).
* Correction d&#39;un problème survenant lors de l&#39;exécution de workflows où un nouveau champ a été ajouté dans le cadre d&#39;une activité **Enrichissement** avant une activité **Diffusion** à l&#39;aide d&#39;un mapping de ciblage **Fichier externe** : des champs indésirables ont été ajoutés au mapping de ciblage **Fichier externe**. (NEO-27687)
* Correction d&#39;un problème en raison duquel certains caractères du code source étaient modifiés lors de la réouverture d&#39;une application web précédemment créée et enregistrée. (NEO-27597)
* Correction d&#39;un problème qui pouvait se produire lors de la mise à niveau vers un build incluant le nouveau mécanisme de signature pour les liens de tracking (depuis la version 19.1.4 et Campaign 20.2) : lorsque plusieurs modèles étaient associés à un événement, la mise à niveau pouvait entraîner la sélection d&#39;un modèle incorrect lors de l&#39;envoi du message transactionnel. (NEO-28326)
* Correction d’un problème en raison duquel le MTA ne réagissait pas et ne pouvait traiter les diffusions qu’après son redémarrage. (NEO-27455)
* Correction dʼun problème dans la base de données MSSQL lié à la gestion des fuseaux horaires lors des opérations de chargement en masse pour une colonne de type datetime. (NEO-27375)
* Correction d&#39;un problème de requête de workflow lors de l&#39;utilisation des fonctions xtk Redshift. Les fonctions SubDays, SubSeconds, SubMinutes et SubHours acceptent désormais les deux types de date et d&#39;heure Redshift (NEO-24962).
* Correction d&#39;un problème en raison duquel un message d&#39;erreur de script s&#39;affichait lors de la tentative de prévisualisation d&#39;un rapport avec accès anonyme. (NEO-27081)
* Correction d&#39;un problème qui pouvait réduire l&#39;utilisation de la mémoire sur le serveur lors de l&#39;analyse des diffusions.
* Correction d&#39;un problème en raison duquel l&#39;instance ne fonctionnait pas lors de l&#39;exécution de requêtes complexes spécifiques.
* Correction d&#39;un problème qui empêchait l&#39;exécution du workflow technique **Synchronisation des pages Twitter**. (NEO-28634)
* Correction d’un problème qui pouvait afficher un message d’erreur lié à la fonction decryptPassword lors de la tentative de publication sur X (anciennement Twitter) à l’aide du modèle de diffusion **Tweet (Twitter)**. (NEO-28216)
* Correction d&#39;un problème survenant lors de l&#39;utilisation d&#39;une activité **JavaScript** pour effectuer une requête HTTP dans un workflow. Après avoir défini le numéro de port dans le nom d’hôte, l’appel échouait avec l’erreur suivante (NEO-29146) :

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

* Correction d’une erreur qui se produisait lors de la configuration d’un compte externe entre une instance marketing et une instance Adobe Campaign Standard ou une instance de midsourcing Campaign Classic à l’aide de l’option &quot;DisableFOH2=1&quot;. Lors de l&#39;utilisation de l&#39;option &quot;DisableFOH2=1&quot; dans le compte externe, les connexions n&#39;étaient pas correctement fermées et s&#39;empilaient, provoquant l&#39;erreur suivante (NEO-26258) :

```
The maximum number of connections has been reached (50) by connections pool 'nms:extAccount:acsDefaultRelayAccount XXX'. The server is overloaded. Please try again later.
```

* Correction d&#39;une erreur de SMS lors de problèmes de connexion entre le serveur et le fournisseur. La connexion était alors automatiquement désactivée par l’enfant MTA. Adobe Campaign Classic ne tentait pas de se connecter à cette connexion défaillante tant qu’un nouvel enfant n’avait pas été démarré.
