---
product: campaign
title: Tester la migration
description: Tester la migration
feature: Upgrade
audience: migration
content-type: reference
topic-tags: migration-procedure
hide: true
hidefromtoc: true
exl-id: 228ee9e4-46a0-4d82-b8ba-b019bc0e7cac
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 100%

---

# Tests de migration{#testing-the-migration}



## Procédure générale {#general-procedure}

Les tests de migration peuvent être effectués de différentes manières, en fonction de votre configuration.

Vous devez disposer d’un environnement de test/développement pour effectuer les tests de migration. Les environnements Adobe Campaign sont soumis à une licence : vérifiez votre contrat de licence ou contactez votre représentant Adobe.

1. Arrêtez tous les développements en cours et reportez-les sur l&#39;environnement de production.
1. Effectuez une sauvegarde de la base de données correspondant à l&#39;environnement de développement.
1. Arrêtez tous les processus Adobe Campaign sur l&#39;instance de développement.
1. Effectuez une sauvegarde de la base de données de l&#39;environnement de production et restaurez-la en tant qu&#39;environnement de développement.
1. Avant de redémarrer les services Adobe Campaign, exécutez le script de cautérisation **freezeInstance.js** permettant de nettoyer la base de données de tous les objets qui étaient en cours d&#39;exécution au moment de la sauvegarde :

   ```
   nlserver javascript nms:freezeInstance.js -instance:<instance> -arg:<run|dry>
   ```

   >[!NOTE]
   >
   >Par défaut la commande se lance en mode **dry**, et liste l&#39;ensemble des requêtes qui seront exécutées par la commande, mais sans les lancer. Pour exécuter les requêtes de cautérisation, utilisez l&#39;argument **run** dans la commande.

1. Assurez-vous que vos sauvegardes sont intègres en tentant de les restaurer. Vérifiez que vous avez bien accès à votre base de données, vos tables, vos données, etc.
1. Testez la procédure de migration sur l&#39;environnement de développement.
1. Si la migration de l&#39;environnement de développement s&#39;est effectuée sans erreur, migrez l&#39;environnement de production.

>[!CAUTION]
>
>En raison de modifications effectuées sur la structure des données, l&#39;import et l&#39;export de packages de données entre une plateforme v5 et une plateforme v7 ne sont pas possibles.


## Outils d&#39;aide à la migration {#migration-tools}

Plusieurs options permettent de mesurer les impacts d&#39;une migration et d&#39;identifier les problèmes potentiels. Ces options sont à exécuter :

* dans la commande **config** :

  ```
  nlserver.exe config <option> -instance:<instance-name>
  ```

* ou au niveau du postupgrade :

  ```
  nlserver.exe config -postupgrade <option> -instance:<instance-name>
  ```

>[!NOTE]
>
>* Vous devez utiliser l’option **-instance:`<instanceame>`**. Il est déconseillé d’utiliser l’option  **-allinstances**.
>* La commande de mise à jour d’Adobe Campaign (**postupgrade**) permet de synchroniser les ressources, et de mettre à jour les schémas et la base de données. Cette opération ne peut être effectuée qu&#39;une seule fois et uniquement sur le serveur applicatif. Suite à la synchronisation des ressources, la commande **postupgrade** permet de détecter si la synchronisation génère des erreurs ou des avertissements.

### Objets non standard ou manquants

* L&#39;option **-showCustomEntities** affiche la liste de tous les objets non-standards :

  ```
  nlserver.exe config -showCustomEntities -instance:<instance-name>
  ```

  Exemple de message renvoyé :

  ```
  xtk_migration:opsecurity2 xtk:entity
  ```

* L&#39;option **-showDeletedEntities** affiche la liste de tous les objets standards manquants dans la base de données ou le système de fichiers. Pour chaque objet manquant, le chemin est indiqué.

  ```
  nlserver.exe config -showDeletedEntities -instance:<instance-name>
  ```

  Exemple de message renvoyé :

  ```
  Out of the box object 'nms:deliveryCustomizationMdl' belonging to the 'xtk:srcSchema' schema has not been found in the file system.
  ```

### Processus de vérification {#verification-process}

Intégré en standard dans la commande de postupgrade, ce processus permet d&#39;afficher les avertissements et erreurs qui pourraient faire échouer la migration. **Si des erreurs s’affichent, la migration n’a pas été exécutée.** Si cela se produit, corrigez toutes les erreurs, puis relancez l’opération de postupgrade.

Il est possible de lancer la vérification seule (sans migration) à l&#39;aide de la commande :

```
nlserver.exe config -postupgrade -check -instance:<instance-name>
```

>[!NOTE]
>
>Vous pouvez ignorer tous les avertissements et erreurs avec le code JST-310040.

Les expressions suivantes sont recherchées (sensibilité à la casse) :

<table> 
 <thead> 
  <tr> 
   <th> Expression<br /> </th> 
   <th> Code erreur<br /> </th> 
   <th> Type de log<br /> </th> 
   <th> Commentaires<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> .@<br /> </td> 
   <td> PU-0001<br /> </td> 
   <td> Avertissement<br /> </td> 
   <td> Ce type de syntaxe n’est plus pris en charge dans la personnalisation de la diffusion. <br /> </td> 
  </tr> 
  <tr> 
   <td> common.js<br /> </td> 
   <td> PU-0002<br /> </td> 
   <td> Avertissement<br /> </td> 
   <td> Cette librairie ne doit pas être utilisée.<br /> </td> 
  </tr> 
  <tr> 
   <td> logon(<br /> </td> 
   <td> PU-0003<br /> </td> 
   <td> Avertissement<br /> </td> 
   <td> Cette méthode de connexion ne doit plus être utilisée.<br /> </td> 
  </tr> 
  <tr> 
   <td> new SoapMethodCall(<br /> </td> 
   <td> PU-0004<br /> </td> 
   <td> Avertissement<br /> </td> 
   <td> Cette fonction est supportée uniquement lorsqu'elle est utilisée dans du code Javascript exécuté depuis une zone de sécurité en mode <strong>sessionTokenOnly</strong>.<br /> </td> 
  </tr> 
  <tr> 
   <td> sql=<br /> </td> 
   <td> PU-0005<br /> </td> 
   <td> Erreur<br /> </td> 
   <td> Ce type d’erreur entraîne un échec de la migration.<br /> </td> 
  </tr> 
  <tr> 
   <td> crmDeploymentType="onpremise"<br /> </td> 
   <td> PU-0007<br /> </td> 
   <td> Erreur<br /> </td> 
   <td> Ce type de déploiement n’est plus pris en charge. Le type de déploiement connecteur Microsoft CRM On-premise et Office 365 est désormais obsolète. 
   </br>Si vous utilisez l’un de ces types de déploiement obsolètes dans un compte externe, ce compte externe doit être supprimé et vous devez par la suite exécuter la commande <b>postupgrade</b>. 
   </br>Pour passer au déploiement des API Web, voir la section <a href="../../platform/using/crm-ms-dynamics.md#configure-acc-for-microsoft" target="_blank">Applications Web</a>.<br /> </td>
  </tr> 
  <tr> 
   <td> CRM v1(mscrmWorkflow/sfdcWorkflow)<br /> </td> 
   <td> PU-0008<br /> </td> 
   <td> Erreur<br /> </td> 
   <td> Les activités d’action Microsoft CRM, Salesforce, Oracle CRM On Demand ne sont plus disponibles. Pour paramétrer la synchronisation des données entre Adobe Campaign et un système CRM, vous devez utiliser l’activité de ciblage du <a href="../../workflow/using/crm-connector.md" target="_blank">Connecteur CRM</a>.<br /> </td>
  </tr> 
 </tbody> 
</table>

Une vérification de la cohérence de la base de données et des schémas est également effectuée.

### Option de restauration {#restoration-option}

Cette option permet de restaurer les objets d&#39;usine dans le cas où ceux-ci auraient été modifiés. Pour chaque objet restauré, une sauvegarde de vos modifications est conservée dans le dossier choisi :

```
nlserver.exe config -postupgrade -restoreFactory:<backupfolder> -instance:<instance-name>
```

>[!NOTE]
>
>Nous vous recommandons fortement d&#39;utiliser des chemins de dossiers absolus et de conserver l&#39;arborescence de dossiers. Par exemple : backupFolder\nms\srcSchema\billing.xml

### Reprise de la migration {#resuming-migration}

Si vous relancez l’opération de postupgrade à la suite d’un échec de migration, celle-ci reprend là où elle s’était arrêtée.
