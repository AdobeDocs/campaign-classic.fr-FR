---
product: campaign
title: Notes de mise à jour de Campaign 18.6
description: Notes de mise à jour de Campaign 18.6
audience: rn
content-type: reference
topic-tags: latest-release-notes
feature: Vue d’ensemble
role: User
level: Beginner
exl-id: a849ce10-0972-4c42-b10e-67a81c79bc65
source-git-commit: 6c28e6cd78ce7a8ee5c0dc7e671de780787b9f57
workflow-type: tm+mt
source-wordcount: '816'
ht-degree: 100%

---

# Version 18.6{#release-18-6}

## Version 18.6.2 - Build 8949{#release-18-6-3-build-8949}

22 août 2018

>[!CAUTION]
>
>Ce build a été rappelé. Effectuez une [mise à niveau vers le dernier build](../../production/using/build-upgrade.md) ou contactez l&#39;[Assistance clientèle Adobe](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

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
   <td> Query banding<br /> </td> 
   <td> <p>Lorsque plusieurs utilisateurs de Campaign se connectent à un même compte externe Teradata FDA, vous pouvez désormais transmettre une Query band (paires clé/valeur) spécifique à chaque utilisateur. Chaque fois qu'un utilisateur de Campaign effectue une requête sur la base de données Teradata, Adobe Campaign peut désormais envoyer des métadonnées associées à l'utilisateur. Ces données, qui consistent en une liste de clés et de valeurs, peuvent ensuite être utilisées par les administrateurs de Teradata à des fins d'audit ou pour gérer les droits d'accès, par exemple.</p><p>Pour plus d’informations, consultez la <a href="../../installation/using/external-accounts.md">documentation détaillée</a>.</p> </td>
  </tr> 
 </tbody> 
</table>

**Améliorations**

* Les logs d&#39;archivage des emails ont été améliorés, ce qui permet de vérifier plus facilement et plus clairement quels emails ont été diffusés avec succès ou non via l&#39;archivage Cci. (NEO-10675)
* Correction d&#39;une erreur qui entraînait l&#39;affichage des adresses IP des équilibreurs de charge au lieu de celles des clients dans les broadlogs de tracking. (NEO-11295)
* Correction d&#39;une erreur aléatoire qui entraînait le remplacement incorrect des propriétés d&#39;une diffusion. (NEO-11015)
* Correction d&#39;une erreur de syntaxe lors du tri des résultats d&#39;une activité d&#39;enrichissement. (NEO-11394)
* Correction d&#39;une erreur lors de l&#39;utilisation de champs calculés dans une activité de workflow **[!UICONTROL Réponses au questionnaire]**. (NEO-11382)
* Mise à jour de Tomcat pour éviter l&#39;exploitation de vulnérabilités. (NEO-11503)
* Correction d&#39;une erreur liée au codage LATIN1 lors de l&#39;utilisation d&#39;une connexion FDA à une base de données PostgreSQL.(NEO-11299)
* Correction d&#39;une erreur qui se produisait lors de l&#39;utilisation de l&#39;option de diffusion **[!UICONTROL Préparer les données de personnalisation avec un workflow.]** (NEO-11047)
* Correction d&#39;une erreur de postupgrade qui empêchait l&#39;envoi de SMS lors de l&#39;utilisation d&#39;un connecteur étendu.
* Amélioration de l&#39;import/export de package (ajout de log et de région dans l&#39;interface).
* Correction d&#39;un problème qui affichait des erreurs inutiles dans le log de postupgrade lorsqu&#39;une activité de workflow **[!UICONTROL Réponses au questionnaire]** n&#39;était pas entièrement configurée.

**Evolutions techniques**

Query banding

Une clé spécifique (PROXYUSER ou PROXYROLE) est utilisée pour associer un utilisateur ou un rôle Teradata à un utilisateur Campaign. Une nouvelle permission a été ajoutée pour utiliser ce rôle/utilisateur proxy. Vous devez ajouter le droit d&#39;accès GRANT CONNECT THROUGH au compte de base de données (celui défini dans le compte externe Teradata).

Un nouvel onglet a été ajouté dans les comptes externes de Teradata. L’onglet **[!UICONTROL Query banding]** comprend les options suivantes :

* **[!UICONTROL Activer]** : cochez cette case pour activer la fonctionnalité.
* **[!UICONTROL Par défaut]** : saisissez un query banding par défaut qui sera utilisé si un utilisateur n’a aucun query banding associé. Si aucun query banding par défaut n’est défini, les utilisateurs sans query banding associé ne pourront pas utiliser Teradata.
* **[!UICONTROL Utilisateurs]** : pour chaque utilisateur, spécifiez un query banding. Vous pouvez ajouter autant de paires clé/valeur que nécessaire. Par exemple : ’priority=1;workload=high;’

Pour plus d’informations sur query banding, référez-vous à ces articles :

* [https://docs.teradata.com/reader/cY5B~oeEUFWjgN2kBnH3Vw/a5G1iz~ve68yTMa24kVjVw](https://docs.teradata.com/reader/cY5B%7EoeEUFWjgN2kBnH3Vw/a5G1iz%7Eve68yTMa24kVjVw)
* [https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ)

## Version 18.6 - Build 8947{#release-18-6-build-8947}

25 juin 2018

>[!CAUTION]
>
>Ce build a été rappelé. Effectuez un [upgrade vers le dernier build](../../production/using/build-upgrade.md) ou contactez le [support technique](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

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
   <td> Amélioration de la sécurité<br /> </td> 
   <td> Nous avons ajouté une série d'améliorations de sécurité à Campaign Classic. Les améliorations et les corrections sont répertoriées ci-dessous.<br /> </td> 
  </tr> 
  <tr> 
   <td> Prise en charge de Windows Server 2016<br /> </td> 
   <td> Adobe Campaign est maintenant compatible avec Windows Server 2016. Consultez la <a href="https://helpx.adobe.com/campaign/kb/compatibility-matrix.html">matrice de comptabilité de Campaign Classic</a>.<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Améliorations de la sécurité**

decryptString

La fonction **decryptString** est obsolète. Reportez-vous à l’article [Fonctionnalités obsolètes et supprimées](https://helpx.adobe.com/fr/campaign/kb/deprecated-and-removed-features.html).

Pour les nouveaux clients, cette fonction n’est plus utilisée que pour déchiffrer l’ID crypté du destinataire dans les landing pages. Pour déchiffrer les mots de passe stockés dans un compte externe, utilisez la nouvelle fonction **decryptPassword**.

Pour les clients existants, le comportement de cette fonction reste inchangée mais nous vous recommandons d’utiliser **decryptPassword** au lieu de **decryptString**. L’option de compatibilité **XtkSecurity_Unsafe_DecryptString** est ajoutée par le postupgrade et activée par défaut, ce qui vous permet de continuer à utiliser la fonction. Si vous souhaitez désactiver **decryptString**, désactivez l’option.

decryptPassword

La fonction **decryptPassword** a été ajoutée. Elle vous permet de déchiffrer un mot de passe stocké dans un compte externe. Reportez-vous à la documentation [JSAPI](https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix.html) pour plus d’informations.

API de fichier

Pour les nouvelles installations, l’accès aux dossiers via les API de fichier est limité aux dossiers **var**, **sftp** et temporaires d’Adobe Campaign.

Pour les clients existants, les API de fichier ne peuvent plus accéder au dossier **conf** d’Adobe Campaign. L’option de compatibilité **XtkSecurity_Disable_JSFileSandboxing** est ajoutée par le postupgrade et activée par défaut, ce qui vous permet de maintenir l’accès aux autres dossiers. Si vous souhaitez limiter l’accès aux dossiers **var**, **sftp** et temporaires d’Adobe Campaign, désactivez l’option.

**Correctif**

* Correction d&#39;une erreur qui pouvait altérer la performance des messages transactionnels par SMS. (NEO-9812)
