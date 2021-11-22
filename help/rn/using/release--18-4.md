---
product: campaign
title: Notes de mise à jour de Campaign 18.4
description: Notes de mise à jour de Campaign 18.4
exl-id: bbad81ba-a09f-4d67-9309-628ea7a08c9b
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '2289'
ht-degree: 100%

---

# Version 18.4{#release-18-4}

![](../../assets/v7-only.svg)

## Version 18.4.5 - Build 8937{#release-18-4-5-build-8937}

21 novembre 2018

**Améliorations**

* Correction de divers problèmes lors de l&#39;exécution des workflows utilisant MySQL sur FDA. (NEO-11652)
* Correction d&#39;un problème qui faisait qu&#39;une partie de la population de diffusion restait en état d&#39;attente dans des cas spécifiques. (NEO-11336)
* Correction d&#39;un problème intermittent avec la réponse automatique SMS. (NEO-11811)
* Correction d&#39;un problème d&#39;épuisement des ID lors de l&#39;utilisation d&#39;adresses de contrôle dans une diffusion. (NEO-11842)
* Correction d&#39;une erreur de syntaxe lors du tri dans une activité de workflow d&#39;enrichissement. (NEO-11394)
* Correction d&#39;un problème qui pouvait provoquer le blocage du serveur web lors du redémarrage d&#39;IIS. (NEO-10862)
* Correction d&#39;un problème qui pouvait entraîner l&#39;échec du workflow de tracking après une mise à niveau de build (FDA - SQL). (NEO-11635)
* Correction d&#39;un problème qui pouvait entraîner la perte des données de liste de workflow. (NEO-11696)
* Correction d&#39;un problème de performances lors de l&#39;envoi de notifications push. (NEO-11787)
* Correction d’un problème qui empêchait le bon fonctionnement du tracking web pour les domaines &quot;com.au&quot; (NEO-4385).
* Correction d&#39;un problème de blocage du client qui pouvait survenir lors de l&#39;utilisation de workflows complexes. (NEO-11847)
* Correction d&#39;une erreur Oracle lors de l&#39;enregistrement d&#39;une nouvelle diffusion après avoir sélectionné un élément d&#39;un schéma spécifique (NEO-11682).
* Correction d&#39;un problème lors de l&#39;interrogation d&#39;un champ contenant des caractères avec accents (FDA/Teradata). Le compte externe vous permet désormais de modifier le codage utilisé pour communiquer avec le pilote Teradata. (NEO-11818).
* Correction d&#39;un problème de tracking lors de la transmission d&#39;URL dans des variables supplémentaires dans une notification push qui pouvait entraîner la réception de données mal formatées ou incorrectes par l&#39;application mobile. (NEO-11468, NEO-11960)
* Correction d&#39;un problème d&#39;affichage lors de l&#39;utilisation d&#39;une distribution de valeurs avec un lien 1:N. (NEO-11820)
* Correction d’une erreur qui empêchait le bon fonctionnement du chargement en masse sur Teradata 16.
* Augmentation de la taille du tampon pour l&#39;horodatage sur Teradata afin d&#39;éviter les problèmes de liaison avec le pilote 15.10.
* Amélioration de la gestion des index aux noms longs qui pouvait créer des problèmes lors du postupgrade.
* Amélioration du temps disponible de la mémoire partagée lors du traitement des enfants morts (MTA).
* Correction d’un blocage potentiel dans Apache (tracking).

## Version 18.4.4 - Build 8936{#release-18-4-4-build-8936}

1er août 2018

**Améliorations**

* Les logs d&#39;archivage des emails ont été améliorés, ce qui permet de vérifier plus facilement et plus clairement quels emails ont été diffusés avec succès ou non via l&#39;archivage Cci. (NEO-10675)
* Correction d&#39;une erreur qui entraînait l&#39;affichage des adresses IP des équilibreurs de charge au lieu de celles des clients dans les broadlogs de tracking. (NEO-11295)
* Correction d&#39;une erreur liée au codage LATIN1 lors de l&#39;utilisation d&#39;une connexion FDA à une base de données PostgreSQL.(NEO-11299)
* Correction dʼune erreur qui se produisait lors de lʼutilisation de lʼoption de diffusion **[!UICONTROL Préparer les données de personnalisation avec un workflow]**. (NEO-11047, NEO-11301)
* Correction d&#39;une erreur aléatoire qui entraînait le remplacement incorrect des propriétés d&#39;une diffusion. (NEO-11015)
* Correction d&#39;une erreur lors de l&#39;utilisation de champs calculés dans une activité de workflow **[!UICONTROL Réponses au questionnaire]**. (NEO-11382)
* Correction d’un problème lors de l’utilisation de données stockées en XML dans une activité de workflow **[!UICONTROL Réponses au questionnaire]**. (NEO-10816)
* Correction d’un problème lors de l’upgrade du serveur avec le build 8935.
* Correction d&#39;un problème qui affichait des erreurs inutiles dans le log de postupgrade lorsqu&#39;une activité de workflow **[!UICONTROL Réponses au questionnaire]** n&#39;était pas entièrement configurée.
* FDA Teradata : correction d’un problème lié aux champs et aux index auto-incrémentés dans les tables SQL.

## Version 18.4.3 - Build 8935{#release-18-4-3-build-8935}

22 juin 2018

**Améliorations**

* Correction d’une erreur d’encodage du suivi avec Microsoft Edge et Internet Explorer. (NEO-11257)
* Correction d’une erreur avec la personnalisation du lien de l’image dans les diffusions LINE. (NEO-11077)
* Correction d’une erreur qui empêchait le bon fonctionnement du mécanisme de génération de séquence d’identifiants. (NEO-11115)
* Correction d’une erreur qui empêchait les demandes d’accès à des informations personnelles (RGPD) de fonctionner lors de l’utilisation d’un espace de noms personnalisé avec une clé de réconciliation de type entier. (NEO-11123)
* Correction d’une erreur qui pouvait survenir lors de l’utilisation de l’option **[!UICONTROL Répartition des valeurs]** dans les activités de workflow **[!UICONTROL Requête]**. (NEO-10958)
* Correction d’une erreur lors de la synchronisation des emplacements de l’instance marketing vers l’instance d’interaction. (NEO-11162)
* Amélioration de la gestion des index aux noms longs lors du postupgrade.

## Version 18.4.2 - Build 8932{#release-18-4-2-build-8932}

22 mai 2018

**Améliorations**

* Correction d’une erreur qui empêchait Windows Server d’être mis à jour correctement.
* Correction d’une erreur dans l’activité **[!UICONTROL Résultat du questionnaire]** lors de l’utilisation de données stockées en XML. Le rapport ne s’affichait pas correctement. (NEO-10816)
* Correction d’un problème de performance qui pouvait se produire avec le processus inMail lors de l’utilisation d’un serveur de mails rebonds. (NEO-10641)
* Correction d’un problème de mise à niveau de la base de données qui pouvait survenir lors de la mise à niveau de plus de 1 000 schémas.

## Version 18.4 - Build 8931{#release-18-4-build-8931}

24 avril 2018

**Nouveautés**

<table> 
 <thead> 
  <tr> 
   <th> Fonctionnalités<br /> </th> 
   <th> Description<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Règlement général sur la protection des données (RGPD) de l’UE<br /> </td> 
   <td> <p>Le RGPD, qui entrera en vigueur le 25 mai 2018, est la nouvelle loi de l’Union européenne (UE) sur la protection de la vie privée. Il harmonise et modernise les exigences en matière de protection des données. Il s’applique aux clients Adobe Campaign qui détiennent des données pour des titulaires de données résidant dans l’UE.</p> <p>Outre les fonctionnalités de protection des données déjà disponibles dans Adobe Campaign (notamment la gestion du consentement, les paramètres de conservation des données et les rôles utilisateur), nous incluons, en qualité de responsable du traitement des données, d'autres fonctionnalités pour faciliter votre préparation en tant que contrôleur de données à certaines demandes RGPD:</p> 
    <ul> 
     <li> <p>Droit d’accès : permet au titulaire de données de recevoir une copie de ses données personnelles collectées par les contrôleurs de données, notamment les données éventuellement stockées dans Adobe Campaign.</p> </li> 
     <li> <p>Droit de suppression : autorise le titulaire de données à demander la suppression de ses données personnelles collectées par les contrôleurs de données, notamment les données éventuellement stockées dans Adobe Campaign.</p> </li> 
    </ul> Pour plus d'informations, consultez la <a href="https://helpx.adobe.com/fr/campaign/kb/acc-privacy.html">documentation détaillée</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> Profils actifs<br /> </td> 
   <td> <p>Adobe Campaign fournit désormais la liste des profils actifs, mise à jour tous les mois via un workflow dédié.</p> <p>Pour plus d'informations, consultez la <a href="../../platform/using/about-profiles.md#active-profiles">documentation détaillée</a>.</p> </td> 
  </tr> 
  <tr> 
   <td> Amélioration du connecteur push Android<br /> </td> 
   <td> <p>Le connecteur Android a été amélioré afin de prendre en charge un débit supérieur. </p> <p>Pour plus d'informations, consultez la <a href="../../delivery/using/configuring-the-mobile-application.md">documentation détaillée</a>.</p> </td> 
  </tr> 
 </tbody> 
</table>

**Améliorations de la sécurité**

* L&#39;extension des entités externes est désormais désactivée pour prévenir les attaques potentielles d&#39;utilisateurs non authentifiés. (NEO-10173)
* Autorisations renforcées pour empêcher les utilisateurs standard de modifier les paramètres de configuration d&#39;instance, tels que les URL d&#39;accès aux applications, la configuration LDAP, etc. (NEO-10171)
* Correction d&#39;un problème qui pouvait révéler des informations sensibles via des traces de pile. Les détails d&#39;erreur sont maintenant consignés en back-end à un emplacement inaccessible à partir du réseau externe. (NEO-10176)
* Autorisations renforcées pour empêcher les utilisateurs standard d&#39;afficher les documents téléchargés et/ou les packages exportés par un administrateur. (NEO-10170)

**Améliorations**

* **Canal LINE - amélioration de l&#39;architecture** : à l&#39;instar de tous les autres canaux d&#39;Adobe Campaign, le canal LINE est désormais pris en charge dans tous les types de déploiement : hébergé, hybride et on-premise.
* **Génération automatique de séquence** : le mécanisme de génération d&#39;identifiants a été amélioré pour augmenter la durée de vie des instances Campaign avec des volumes d&#39;objets importants. Pour plus d&#39;informations, reportez-vous à cette [technote](https://helpx.adobe.com/fr/campaign/kb/sequence_auto_generation.html).

**Autres changements**

* Un nouveau mode est disponible pour l&#39;import de packages à l&#39;aide d&#39;une ligne de commande. Il permet les dépendances circulaires (non recommandé pour les packages volumineux). Pour plus d&#39;informations, consultez la section Evolutions techniques. (NEO-8979)
* Amélioration des performances pour le chargement de grandes quantités de données dans Teradata et correction d&#39;une erreur qui empêchait l&#39;affichage de la valeur correcte des données traitées dans le log. (NEO-10429)
* L&#39;import d&#39;audiences depuis Audience Manager est désormais possible avec des fichiers partagés. Auparavant, seul le dernier fichier du segment était importé par le workflow technique importSharedAudience. (NEO-10156)
* Sous Windows, le chemin d’installation par défaut du serveur Campaign a changé. Lors du lancement du programme d’installation de la version 64 bits, le chemin d’installation par défaut est désormais **C:\Program Files\Adobe\Adobe Campaign Classic v7\** au lieu de **C:\Program Files (x86)\Adobe\Adobe Campaign Classic v7**
* Les règles MX par défaut ont été améliorées pour inclure davantage de domaines et optimiser le débit.
* Application des restrictions d&#39;accès sur l&#39;appel SOAP de l&#39;assistant de déploiement (xtk:serverOptions#SaveOptions).
* La bibliothèque obsolète weka.jar a été supprimée et la bibliothèque OpenSSL a été mise à jour pour optimiser la sécurité.
* Amélioration du workflow technique de facturation pour sécuriser les performances des instances.
* Les administrateurs peuvent à nouveau définir ou réinitialiser le mot de passe des opérateurs. Pour cela, cliquez avec le bouton droit sur un opérateur, sélectionnez **[!UICONTROL Actions]** > **[!UICONTROL Réinitialiser le mot de passe]**, puis définissez le nouveau mot de passe de l&#39;opérateur. Nous recommandons aux opérateurs de changer leur mot de passe lors de leur première reconnexion. Pour plus d&#39;informations, consultez la [documentation détaillée](../../production/using/lost-password.md).
* Pour prendre en charge la nouvelle fonctionnalité multi-tenant d&#39;Adobe Target, un nouveau paramètre &quot;at_property&quot; peut maintenant être ajouté aux URL lors de la configuration des options et des comptes externes pour l&#39;intégration avec Target. La valeur à utiliser pour ce paramètre figure dans Adobe Target et sera utilisée par Campaign lors des appels à Target. Pour plus d&#39;informations, consultez la [documentation détaillée](../../integrations/using/inserting-a-dynamic-image.md).
* Vous pouvez maintenant spécifier l&#39;ouverture d&#39;une landing page par défaut lors d&#39;un clic sur une image fournie par Adobe Target. Auparavant, un clic sur cette image affichait l&#39;image par défaut définie lors de la création de l&#39;email. Pour plus d&#39;informations, consultez la [documentation détaillée](../../integrations/using/inserting-a-dynamic-image.md).
* Ajout de la case à cocher **Activer les traces SMPP** dans le compte externe pour forcer la sortie des traces. Pour plus d&#39;informations, consultez la [documentation détaillée](../../delivery/using/sms-set-up.md#creating-an-smpp-external-account).

**Evolutions techniques**

queryDef

queryDef a été modifié en ce qui concerne la clause &quot;orderBy&quot;. Avant le changement, la clé primaire de la table interrogée aurait été implicitement ajoutée aux clauses &quot;orderBy&quot;. Sur certains moteurs de base de données (postgresql), il empêche l&#39;utilisation d&#39;index (tous les champs de la clause orderBy doivent être couverts par le même index). Si vous étiez dépendant de ce comportement, vous devrez ajouter explicitement la clé primaire dans votre clause &quot;orderBy&quot;.

Par exemple, si vous avez la requête suivante :

```
<queryDef operation="select" schema="xtk:job" startPath="/" xtkschema="xtk:queryDef">
  <select>
     <node expr="@id"/>
   </select>
   <orderBy>
     <node expr="@logDate"/>
   </orderBy>
</queryDef>`
```

elle est implicitement gérée en tant que (avant les modifications de la version 18.4) :

```
<queryDef operation="select" schema="xtk:job" startPath="/" xtkschema="xtk:queryDef">
  <select>
     <node expr="@id"/>
   </select>
   <orderBy>
      <node expr="@logDate"/>
      <node expr="@id"/> <!-- implicitly added before 18.4, you can add it manually on your query, if you relied on this implicit order clauses --!>
   </orderBy>
</queryDef>
```

Fonction urlEncode

La fonction JavaScript &#39;urlEncode&#39; ne fonctionnait pas correctement pour les caractères non-ASCII. Elle a été corrigée et fonctionne maintenant avec tous les caractères Unicode (y compris les caractères japonais). Si vous dépendiez du comportement de &#39;urlEncode&#39; pour un caractère non-ASCII, vous devez adapter votre code.

Nouveau mode pour l&#39;import de package

Un nouveau mode est disponible pour l&#39;import de packages à l&#39;aide d&#39;une ligne de commande. Il permet les dépendances circulaires (non recommandé pour les packages volumineux). La fonctionnalité existante est conservée. Pour ces packages avec des dépendances circulaires, un nouveau flag **-usejs** a été ajouté à la ligne de commande pour l&#39;import du package. Lorsqu&#39;il est exécuté, il utilise JSEngine comme lorsque l&#39;import est effectué à partir de l&#39;interface.

```
nlserver package -instance:fresh -import:sup-packInstallTest.xml -verbose -usejs
```

**Correctifs**

* Correction d&#39;une erreur de synchronisation lors de la réplication des logs de diffusion et de tracking d&#39;Adobe Campaign Standard vers Adobe Campaign Classic. (NEO-10023)
* Correction d&#39;une erreur liée à la gestion des tables d&#39;erreurs et de logs dans Teradata lorsqu&#39;un workflow ETL reprenait après l&#39;échec d&#39;une opération de chargement rapide. Les tables d&#39;erreurs et de logs sont désormais supprimées correctement chaque fois que le workflow reprend. (NEO-10672)
* Correction d&#39;une erreur de postupgrade qui permet d&#39;installer automatiquement le package Hive (nécessaire pour Hadoop) si le package FDA est installé. (NEO-10592)
* Correction d&#39;une erreur qui traitait les domaines non valides comme une erreur **Non définie**. (NEO-10248)
* Correction d&#39;une erreur qui entraînait la duplication des logs dans la table deliveryLogStats lors de l&#39;envoi de diffusions push Android. (NEO-10234)
* Correction d’une erreur qui empêchait la lecture de certains formats de code-barres par les lecteurs de code-barres. (NEO-10125)
* Correction d&#39;une erreur liée à la fonction JavaScript &#39;urlEncode&#39; lors de l&#39;utilisation de caractères non-ASCII. Pour plus d&#39;informations, consultez la section Evolutions techniques. (NEO-10123)
* Correction d&#39;une erreur lors de l&#39;exécution d&#39;une requête incluant des fonctions sha256 sur des bases de données Teradata. (NEO-10119)
* Correction des erreurs de mémoire de workflow qui se produisaient dans l&#39;activité SalesForce lors de l&#39;utilisation de tables SalesForce très volumineuses. (NEO-9900)
* Correction d&#39;une erreur liée à l&#39;option **Générer le complémentaire** dans les activités de workflow de ciblage lors de l&#39;utilisation de FDA. (NEO-9878)
* Correction d&#39;une erreur qui empêchait la mise à jour des mesures **Traités** et **Succès** sur l&#39;instance marketing lors de l&#39;utilisation du mid-sourcing. (NEO-9454)
* Correction des règles de non-reproposition d&#39;Interaction lorsque plus de 10 000 offres se trouvent sur la plateforme. (NEO-9352)
* Correction d&#39;une erreur qui empêchait la spécification de la cible d&#39;une diffusion lors de l&#39;utilisation d&#39;un fichier externe XML. (NEO-9312)
* Correction d&#39;un problème pouvant entraîner des erreurs de workflow lors de l&#39;exécution d&#39;une hypothèse sur une offre et de la mise à jour du statut de la proposition. (NEO-9304)
* Correction des erreurs qui se produisaient pendant l&#39;analyse des diffusions lorsque des règles de pression basées sur un attribut du mapping de diffusion Android étaient utilisées. (NEO-9202)
* Correction d&#39;un problème qui entraînait des problèmes de performances lors du tri des colonnes de la liste des destinataires. Pour plus d&#39;informations sur les modifications de queryDef, consultez la section Evolutions techniques ci-dessus. (NEO-9042)
* Correction d&#39;un problème en raison duquel les liens d&#39;un email de validation pointaient vers une URL de connexion incorrecte, en particulier lors de l&#39;utilisation d&#39;un type de connexion Federated ID. (NEO-9011)
* Correction d&#39;une erreur qui entraînait l&#39;affichage de dates erronées dans les sélecteurs de date des rapports pour certains fuseaux horaires. (NEO-9007)
* Correction d&#39;une erreur qui empêchait l&#39;affichage de la cible d&#39;une sortie lors de l&#39;utilisation d&#39;une base de données SQL FDA. (NEO-8924)
* Correction d&#39;une erreur qui empêchait le connecteur MS Dynamics CRM d&#39;extraire des données pour les 7 premiers jours du mois. (NEO-8803)
* Correction d&#39;une erreur liée à l&#39;intégration d&#39;Analytics qui empêchait les utilisateurs d&#39;inclure des caractères internationaux. (NEO-8719)
* Correction d&#39;une erreur qui permettait l&#39;édition de workflows sans les droits adéquats. (NEO-8708)
* Correction d&#39;une erreur liée à FDA via HTTPs lors de l&#39;utilisation de Message Center dans une architecture hybride, entraînant une perte de connexion (timeout). (NEO-8438)
* Correction des erreurs de workflow se produisant dans les activités de requête incrémentale pour les identifiants négatifs. (NEO-8229)
* Correction d&#39;une erreur qui entraînait l&#39;affichage de deux barres de défilement dans certains écrans. (NEO-8208)
* Correction d&#39;une erreur qui entraînait l&#39;affichage d&#39;un message d&#39;erreur lors de l&#39;exécution de l&#39;assistant de mise à jour de la structure de la base de données. Le postupgrade exécute une opération d&#39;attribution de nouveaux noms aux index dont les noms comportent plus de 30 caractères. Pour les tables volumineuses, le remplacement des index prend du temps. (NEO-7983)
* Correction d&#39;une erreur qui entraînait une synchronisation incorrecte des logs de tracking de l&#39;instance d&#39;exécution de Message Center vers l&#39;instance de pilotage. (NEO-7286)
* Correction d&#39;un problème de performance lié à l&#39;activité d&#39;enrichissement des offres. (NEO-7263)
* Correction d&#39;un problème empêchant l&#39;utilisation de la fonction DaysAgo lors de l&#39;interrogation d&#39;une base de données Redshift via FDA. (NEO-7099)
* Correction d&#39;une régression dans Data Management qui empêchait la création d&#39;index sur les activités de workflow de type Enrichissement.
* Correction d&#39;un problème qui se produisait lors de la création de ressources externes avec le titre @id.
* Correction d&#39;un problème qui se produisait lors du téléchargement de fichiers compressés via un serveur FTP ou du téléchargement de fichiers dont le nom comportait des caractères génériques.
* Correction d&#39;un problème lié aux énumérations de type base longues dans les ressources personnalisées externes créées dans Campaign Standard.
* Correction d&#39;un problème qui entraînait l&#39;envoi de SMS même lorsque la connexion avec le fournisseur échouait, entraînant des pertes de SMS.
* Correction d&#39;une erreur qui entraînait le blocage indéfini d&#39;une connexion SMTP.
* Correction d&#39;une erreur liée aux règles de typologie de pression durant la préparation des messages lors de l&#39;utilisation d&#39;un mapping LINE ou lorsque les schémas de filtrage et de ciblage diffèrent.
