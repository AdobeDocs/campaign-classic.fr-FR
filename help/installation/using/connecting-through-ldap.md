---
title: Connexion par LDAP
seo-title: Connexion par LDAP
description: Connexion par LDAP
seo-description: null
page-status-flag: never-activated
uuid: 13a426bc-7c34-49e5-ac8e-26d830845f28
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: 1563db7c-ccb6-46b3-9299-67ec0aedaca0
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# Connexion par LDAP{#connecting-through-ldap}

## Configuration Campaign et LDAP {#configuring-campaign-and-ldap}

>[!NOTE]
>
>La configuration LDAP est uniquement possible pour les installations de type on-premise ou hybride.

La configuration LDAP est effectuée dans l’assistant de déploiement. L’ **[!UICONTROL LDAP integration]** option doit être sélectionnée lors de la première étape de configuration. Reportez-vous à [l’assistant](../../installation/using/deploying-an-instance.md#deployment-wizard)de déploiement.

La fenêtre correspondante permet de configurer l&#39;identification des utilisateurs Adobe Campaign via l&#39;annuaire LDAP spécifié.

![](assets/s_ncs_install_deployment_wiz_ldap_01.png)

* Indiquez l’adresse du serveur LDAP dans le **[!UICONTROL LDAP server]** champ. Vous pouvez ajouter le numéro de port. Par défaut, le port utilisé est 389.
* Sélectionnez dans la liste déroulante le mécanisme d&#39;authentification des utilisateurs :

   * Mot de passe crypté (**md5**)

      Mode par défaut.

   * Mot de passe en clair + SSL (**TLS**)

      Toute la procédure d&#39;authentification (mot de passe compris) est cryptée. Le port sécurisé 636 ne doit pas être utilisé dans ce mode : Adobe Campaign passe automatiquement en mode sécurisé.

      Lorsque vous utilisez ce mode d&#39;authentification, sous Linux, le certificat est vérifié par la bibliothèque client openLDAP. Nous vous recommandons d&#39;utiliser un certificat SSL valide afin que la procédure d&#39;authentification soit cryptée. Dans le cas contraire, les informations seront passées en clair.

      Le certificat est également vérifié sous Windows.

   * Windows NT LAN Manager (**NTLM**)

      Authentification Windows exclusive. Le **[!UICONTROL Unique identifier]** paramètre est utilisé uniquement pour le nom de domaine.

   * Distributed Password Authentication (**DPA**)

      Authentification Windows exclusive. Le **[!UICONTROL Unique identifier]** paramètre est utilisé pour le nom de domaine uniquement (domaine.com).

   * Mot de passe en clair (plain text)

      Aucun cryptage (utiliser en test uniquement).

* Sélectionnez le mode d’authentification de l’utilisateur : **[!UICONTROL Automatically compute the unique user identifier]** (voir étape [Calcul](#distinguished-name-calculation)du nom unique) ou **[!UICONTROL Search the unique user identifier in the directory]** (voir étape [Recherche d’identifiants](#searching-for-identifiers)).

## Compatibilité {#compatibility}

Les systèmes compatibles dépendent du mécanisme d&#39;authentification sélectionné. Le tableau suivant liste les compatibilités en fonction du système d&#39;exploitation du serveur Adobe Campaign et du type de serveur LDAP utilisé.

<table> 
 <thead> 
  <tr> 
   <th> </th> 
   <th> OpenLDAP<br /> </th> 
   <th> Active Directory<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> md5<br /> </td> 
   <td> Windows, Linux<br /> </td> 
   <td> Linux<br /> </td> 
  </tr> 
  <tr> 
   <td> TLS<br /> </td> 
   <td> Linux<br /> </td> 
   <td> Windows, Linux<br /> </td> 
  </tr> 
  <tr> 
   <td> NTLM &amp; DPA<br /> </td> 
   <td> </td> 
   <td> Windows<br /> </td> 
  </tr> 
  <tr> 
   <td> plain text<br /> </td> 
   <td> Windows, Linux<br /> </td> 
   <td> Windows, Linux<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Calcul de l&#39;identifiant unique {#distinguished-name-calculation}

Si vous choisissez de calculer l&#39;identifiant unique (DN), l&#39;étape suivante de l&#39;assistant de déploiement permet de paramétrer le mode de calcul.

![](assets/s_ncs_install_deployment_wiz_ldap_02.png)

* Indiquez l&#39;identifiant unique de l&#39;utilisateur dans l&#39;annuaire ( - DN) dans le champ **[!UICONTROL Distinguished Name]** Identifiant unique (DN).

   **[!UICONTROL (login)]** sera remplacé par l&#39;identifiant de l&#39;opérateur Adobe Campaign.

   >[!CAUTION]
   >
   >Le paramètre **[!UICONTROL dc]** doit être en minuscules.

* Sélectionnez l’option **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** afin de synchroniser le groupe et les associations d’utilisateurs dans l’annuaire LDAP, ainsi que le groupe et les associations d’utilisateurs dans Adobe Campaign.

   Lorsque vous sélectionnez cette option, les options **[!UICONTROL Application level DN used for the search]** et **[!UICONTROL Password of the application login]** sont activées.

   Si vous renseignez ces deux champs. Adobe Campaign se connectera alors au serveur LDAP avec son propre login et mot de passe. S&#39;ils sont vides, Adobe Campaign se connectera au serveur de manière anonyme.

## Recherche des identifiants {#searching-for-identifiers}

Si vous choisissez de faire une recherche sur l&#39;identifiant, l&#39;assistant de déploiement permet de paramétrer la recherche.

* Dans les champs **[!UICONTROL Application level DN used for the search]** et **[!UICONTROL Password of the application login]** , indiquez l’identifiant et le mot de passe avec lesquels Adobe Campaign se connectera pour rechercher l’identifiant. S’ils sont vides, Adobe Campaign se connecte anonymement au serveur.
* Specify the **[!UICONTROL Base identifier]** and **[!UICONTROL Search scope]** fields in order to determine a subset of the LDAP directory to start the search from.

   Sélectionnez le mode voulu dans la liste déroulante :

   ![](assets/s_ncs_install_deployment_wiz_ldap_03.png)

   1. **[!UICONTROL Recursive (default mode)]**.

      La recherche s&#39;effectue sur toute l&#39;arborescence de l&#39;annuaire LDAP, à partir d&#39;un niveau donné.

   1. **[!UICONTROL Limited to the base]**.

      La recherche s&#39;effectue sur tous les attributs de l&#39;arborescence.

   1. **[!UICONTROL Limited to the first sub-level of the base]**.

      La recherche s&#39;effectue sur tous les attributs de l&#39;arborescence et le premier sous-niveau de l&#39;attribut.

* The **[!UICONTROL Filter]** field enables you to specify an element to refine the scope of the search.

## Configuration des autorisations LDAP {#configuring-ldap-authorizations}

Cette fenêtre s’affiche lorsque vous sélectionnez l’ **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** option.

![](assets/s_ncs_install_deployment_wiz_ldap_04.png)

Vous devez fournir plusieurs paramètres pour retrouver le ou les groupes auxquels appartient l&#39;utilisateur et les autorisations dont il dispose par extension, à savoir :

* le **[!UICONTROL Database identifier]** champ,
* le **[!UICONTROL Search scope]** champ,

   >[!NOTE]
   >
   >If you have chosen to search for the DN, you can select **[!UICONTROL Reuse the DN search parameters]** in order to carry over the selected values for the DN and search scope from the previous screen.

* the **[!UICONTROL Rights search filter]** field, based on the login and the user&#39;s distinguished name,
* le **[!UICONTROL Attribute containing the group or authorization name]** champ concernant l&#39;utilisateur,
* le **[!UICONTROL Association mask]** champ permettant d’extraire le nom du groupe dans Adobe Campaign et ses droits associés. Vous pouvez utiliser des expressions régulières pour rechercher le nom.
* Sélectionnez **[!UICONTROL Enable the connection of users declared in the LDAP directory if the operator is not declared in Adobe Campaign]** cette option pour que l’utilisateur bénéficie automatiquement des droits d’accès lors de la connexion.

Click **[!UICONTROL Save]** to finish configuring the instance.

## Gestion des opérateurs {#managing-operators}

Une fois le paramétrage validé, vous devez définir quels opérateurs Adobe Campaign seront gérés via l&#39;annuaire LDAP.

Pour utiliser l’annuaire LDAP pour authentifier un opérateur, modifiez le profil correspondant et cliquez sur le **[!UICONTROL Edit the access parameters]** lien. Sélectionnez l’ **[!UICONTROL Use LDAP for authentication]** option : Le **[!UICONTROL Password]** champ est grisé pour cet opérateur.

![](assets/s_ncs_install_operator_in_ldap.png)

## Cas pratiques {#use-cases}

Cette section propose quelques cas pratiques simples afin de réaliser les paramétrages les mieux adaptés à vos besoins.

1. Un utilisateur existe dans l&#39;annuaire LDAP mais n&#39;a pas été créé dans Adobe Campaign.

   Adobe Campaign peut être configuré de manière à ce que l’utilisateur accède à la plateforme par le biais de son authentification LDAP. Adobe Campaign doit pouvoir contrôler la validité de la combinaison ID/mot de passe dans l’annuaire LDAP, de sorte que l’opérateur puisse être créé à la volée dans Adobe Campaign. Pour ce faire, cochez l’ **[!UICONTROL Enable the connection of users declared in the LDAP directory if the operator is not declared in Adobe Campaign]** option. Dans ce cas, la synchronisation de groupes doit également être configurée : l’ **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** option doit être sélectionnée.

1. Un utilisateur existe dans Adobe Campaign mais n&#39;a pas été créé dans l&#39;annuaire LDAP.

   Il ne pourra alors pas se connecter à Adobe Campaign.

1. Un groupe n&#39;existe pas dans Adobe Campaign mais seulement dans l&#39;annuaire LDAP.

   Ce groupe ne sera pas créé dans Adobe Campaign. Vous devez créer le groupe et synchroniser les groupes pour activer une correspondance via l’ **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** option.

1. Des groupes existent dans Adobe Campaign et l&#39;utilisation de l&#39;annuaire LDAP est activée a posteriori : les groupes d&#39;utilisateurs côté Adobe Campaign ne sont pas remplacés automatiquement par le contenu des groupes LDAP. De même, si un groupe n&#39;existe que dans Adobe Campaign, aucun utilisateur LDAP ne peut y être ajouté avant que le groupe ne soit créé et synchronisé côté LDAP.

   Les groupes ne sont jamais créés à la volée, ni côté Adobe Campaign, ni côté LDAP. Ils doivent être créés unitairement à la fois dans Adobe Campaign et dans l&#39;annuaire LDAP.

   Les noms des groupes dans l&#39;annuaire LDAP doivent correspondre aux noms des groupes dans Adobe Campaign. Leur masque d&#39;association est défini dans la dernière étape de configuration de l&#39;assistant de déploiement, par exemple : Adobe Campaign_(.*).

