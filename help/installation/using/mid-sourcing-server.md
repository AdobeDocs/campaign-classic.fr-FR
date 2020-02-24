---
title: Installation d’un serveur de moyenne source dans Adobe Campaign Classic
description: Cette section décrit l’installation et la configuration d’un serveur de mi-génération dans Adobe Campaign Classic.
page-status-flag: never-activated
uuid: 9b891a64-d75e-44d2-8de2-17334e1b8dca
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: 34ee3d99-4ffb-4279-b994-5ab7abc7cf06
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 25ae29490f8b4c58dad499669f5bccff43de8b7a

---


# Serveur de mid-sourcing{#mid-sourcing-server}

Cette section présente les étapes d&#39;installation et de configuration d&#39;un serveur de mid-sourcing ainsi que les étapes de déploiement d&#39;une instance permettant à des tiers de soumettre des messages en mode **mid-sourcing**.

The &quot;mid-sourcing&quot; architecture is presented in [Mid-sourcing deployment](../../installation/using/mid-sourcing-deployment.md).

L&#39;installation d&#39;un serveur de mid-sourcing est identique à celle d&#39;une instance classique (se référer à la configuration standard). Il s&#39;agit d&#39;une instance autonome avec sa propre base de données, sur laquelle il est possible de lancer des diffusions. Elle contient simplement une configuration supplémentaire permettant à des instances distantes de lui déléguer des envois à effectuer en mode mid-sourcing.

## Etapes d&#39;installation et de configuration d&#39;une instance {#steps-for-installing-and-configuring-an-instance}

### Prerequisites for installing and configuring an instance {#prerequisites-for-installing-and-configuring-an-instance}

* JDK sur le serveur applicatif.
* Accès à un serveur de base de données sur le serveur applicatif.
* Configuration du firewall pour l&#39;ouverture du port HTTP (80) ou HTTPS (443) vers le serveur de mid-sourcing.

La procédure ci-dessous présente une configuration utilisant un seul serveur de mid-sourcing. Il est également possible de faire appel en parallèle à plusieurs serveurs de mid-sourcing, ainsi que de configurer l&#39;envoi de certains messages en mode normal (pour les notifications de workflow, par exemple).

### Installer et configurer le serveur applicatif pour un déploiement en mid-sourcing {#installing-and-configuring-the-application-server-for-mid-sourcing-deployment}

La procédure d’installation est identique à celle de l’instance autonome. Reportez-vous à [Installation et configuration (machine unique)](../../installation/using/standalone-deployment.md#installing-and-configuring--single-machine-).

Toutefois, vous devez appliquer les spécificités suivantes :

* A l&#39;étape **5**, vous devez désactiver les modules **mta** (diffusion) et **inMail** (mails rebonds). Au contraire, le module **wfserver** (workflow) doit rester activé.

   ```
   <?xml version='1.0'?>
   <serverconf>  
     <shared>    
       <!-- add lang="eng" to dataStore to force English for the instance -->    
       <dataStore hosts="console.campaign.net*">      
         <mapping logical="*" physical="default"/>    
       </dataStore>  </shared>  
       <mta autoStart="false"/>  
       <wfserver autoStart="true"/>  
       <inMail autoStart="false"/>  
       <sms autoStart="false"/>  
       <listProtect autoStart="false"/>
   </serverconf>
   ```

   For more on this, refer to [Enabling processes](../../installation/using/campaign-server-configuration.md#enabling-processes).

* Les étapes **6**,**9** et **10** ne sont pas nécessaires.
* Lors des étapes **12** et **13**, vous devez indiquer le port 8080 dans l&#39;URL de connexion (car la console communique directement avec Tomcat sans passer par le serveur Web). L&#39;URL devient [http://console.campaign.net:8080](http://console.campaign.net). A l&#39;étape **13**, sélectionnez le package **[!UICONTROL Emission vers Mid-Sourcing]**, en complément des packages à installer.

   ![](assets/s_ncs_install_midsourcing02.png)

   >[!CAUTION]
   >
   >Le routage par défaut des diffusions techniques est automatiquement remplacé par le routage email via Mid-sourcing.

### Installer et configurer le serveur de mid-sourcing {#installing-and-configuring-the-mid-sourcing-server}

A partir de la console client, recherchez le routage des **courriels à l’aide du compte de milieu de gamme d’approvisionnement** intermédiaire (dans le dossier **/Administration/Comptes externes/** ). Renseignez les paramètres **URL du serveur**, du **compte**, du **mot de passe** **et de l’URL de la page de mise en miroir avec les informations fournies par le fournisseur du serveur hébergeant le serveur de sources intermédiaires.** Tester la connexion.

>[!NOTE]
>
>L&#39;option **Emission vers Mid-sourcing** crée deux workflows **Mid-sourcing**. Il s&#39;agit d&#39;un traitement, planifié par défaut toutes les heures et 20 minutes, qui effectue la collecte des informations d&#39;envoi sur le serveur de mid-sourcing.

## Déploiement d&#39;un serveur de mid-sourcing {#deploying-a-mid-sourcing-server}

1. Installation du serveur applicatif :

   >[!CAUTION]
   >
   >Si vous installez un serveur de mid-sourcing et que vous souhaitez installer des modules Adobe Campaign supplémentaires, il est déconseillé de choisir le module Campaign. Préférez le module Delivery.

   Suivez la même procédure que pour un déploiement standard en sélectionnant uniquement l&#39;option **[!UICONTROL Plate-forme de Mid-sourcing]**.

   ![](assets/s_ncs_install_midsourcing01.png)

1. Configuration de la réception du mid-sourcing :

   Définissez le mot de passe du compte d’envoi : Dans le dossier **/Mid-sourcing/Access Management/Operators/** , l’opérateur **mid** est utilisé par l’instance distante pour les envois en mode mid-sourcing. Vous devez définir un mot de passe pour cet opérateur et le donner à l’administrateur de l’instance d’envoi.

   L&#39;option **Plate-forme de Mid-sourcing** crée les dossiers par défaut dans lesquels seront stockées les diffusions soumises et l&#39;opérateur par défaut pour effectuer les soumissions.

## Multiplexage du serveur de mid-sourcing {#multiplexing-the-mid-sourcing-server}

>[!CAUTION]
>
>Le multiplexage est uniquement pris en charge pour les environnements sur site.

Il est possible de mutualiser une instance de mid-sourcing pour plusieurs instances de soumission. Chaque instance pouvant effectuer des soumissions sera associée à un opérateur dans la base de mid-sourcing. Pour créer un second compte sur le serveur de mid-sourcing :

1. Créez un dossier sous le nœud **[!UICONTROL Mid-sourcing > Diffusions]** qui sera associé au compte mid-sourcing par défaut (par exemple : prod).
1. Créez un dossier sous le nœud **[!UICONTROL Mid-sourcing > Diffusions]** qui aura le même nom que le compte (par exemple : recette).

   ![](assets/mid_recette_account.png)

1. Créez un nouveau compte depuis le noeud **[!UICONTROL Mid-sourcing > Gestion des accès > Opérateurs]**.

   ![](assets/mid_recette_user_create.png)

1. Dans l&#39;onglet **[!UICONTROL Droits d&#39;accès]**, attribuez à cet opérateur les droits du groupe **Soumissions mid-sourcing**. Ce droit d&#39;accès est accessible sous **[!UICONTROL Mid-sourcing > Gestion des accès > Groupes d&#39;opérateurs]**.

   ![](assets/mid_recette_user_rights.png)

1. Sélectionnez l&#39;option **[!UICONTROL Restreindre aux données présentes dans les sous-dossiers de]** et séléctionnez le dossier Diffusions pour restreindre l&#39;accès de cet opérateur au répertoire de diffusions mid-sourcing.

   ![](assets/mid_recette_user_restrictions.png)

1. Redémarrez le module technique web par la commande suivante : **nlserver restart web**.

Vous devez modifier le paramétrage du serveur de mid-sourcing à partir du fichier serverConf.xml. La ligne suivante doit être ajoutée dans la section &quot;Gestion des affinités avec les adresses IP&quot;, sous la ligne existante :

```
<IPAffinity IPMask="" localDomain="" name=""/>
```

L&#39;attribut &#39;@name&#39; doit respecter les règles suivantes :

**&#39;marketing_account_operation_name&#39;.&#39;affinité_name&#39;.&#39;affinité_group&#39;**

&#39;nom_du_compte_de_l&#39;opérateur_marketing&#39; correspond au nom interne du compte de l&#39;opérateur mid-sourcing déclaré dans l&#39;instance mid-sourcing.

&#39;affinity_name&#39; relates to the arbitrary name given to the affinity. This name must be unique. Authorized characters are `[a-z]``[A-Z]``[0-9]`. The aim is to declare a group of public IP addresses.

&#39;groupe_d&#39;affinité&#39; est lié à la sous-affinité déclarée dans le mapping de ciblage utilisé dans chacune des diffusions. La dernière partie incluant le &#39;.&#39; est ignorée en l&#39;absence de sous-affinité. Les caractères autorisés sont `[a-z]``[A-Z]``[0-9]`.

Vous devez arrêter et redémarrer le serveur pour que cette modification soit prise en compte.

## Configuration du tracking sur un serveur de mid-sourcing {#configuring-tracking-on-a-mid-sourcing-server}

**Paramétrage du serveur de mid-sourcing**

1. Positionnez-vous au niveau des opérateurs et sélectionnez l&#39;opérateur **[!UICONTROL mid]**.
1. Dans l&#39;onglet **[!UICONTROL Serveurs frontaux]** complétez les paramètres de connexion au serveur de tracking.

   Pour créer une instance de tracking, indiquez l&#39;URL du serveur de tracking, le mot de passe du compte internal du serveur de tracking, ainsi que le nom de l&#39;instance, son mot de passe et les masques DNS qui lui sont associés.

   ![](assets/s_ncs_install_midsourcing_tracking02.png)

1. Lorsque vous avez complété les paramètres de connexion, cliquez sur **[!UICONTROL Valider le paramétrage]**.
1. Si besoin est, définissez l&#39;emplacement où seront stockées les images contenues dans les diffusions. Pour cela, choisissez un des modes de publication disponible dans la liste déroulante.

   ![](assets/s_ncs_install_midsourcing_tracking03.png)

   Si vous choisissez l&#39;option **[!UICONTROL Serveur(s) de tracking]**, les images seront forcément copiées sur le serveur de mid-sourcing.

**Paramétrage de la plateforme cliente**

1. Positionnez-vous sur le compte externe de routage en mid-sourcing.
1. Dans l&#39;onglet **[!UICONTROL Mid-Sourcing]**, indiquez les paramètres de connexion au serveur de mid-sourcing.

   ![](assets/s_ncs_install_midsourcing_tracking06.png)

1. Validez votre paramétrage en cliquant sur **[!UICONTROL Tester la connexion]**.
1. Déclarez l&#39;instance de tracking référencée sur le serveur de mid-sourcing :

   Cliquez sur le lien **[!UICONTROL Utiliser cette plate-forme comme proxy pour accéder aux serveurs de tracking]**,

   Indiquez le nom de l&#39;instance de tracking, puis validez la connexion avec le serveur de tracking.

   ![](assets/s_ncs_install_midsourcing_tracking05.png)

Si l&#39;envoi de messages doit être géré par plusieurs serveurs de mid-sourcing, sélectionnez l&#39;option **[!UICONTROL Routage avec alternance des comptes mid-sourcing utilisés]** et indiquez les différents serveurs.

![](assets/s_ncs_install_midsourcing_tracking04.png)

