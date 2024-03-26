---
product: campaign
title: Autres paramètres de tracking web
description: En savoir plus sur les paramètres de tracking web
feature: Configuration, Instance Settings
role: Data Engineer, Developer
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
exl-id: d14d94fd-b078-4893-be84-31d37a1d50f5
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 100%

---

# Autres paramètres de tracking web{#additional-parameters}

## Définition des paramètres {#definition-of-parameters}

Votre plateforme Adobe Campaign propose en standard deux paramètres relatifs au tracking Web de type TRANSACTION :

* **amount** : représente le montant d&#39;une transaction,
* **article** : représente le nombre d&#39;articles d&#39;une transaction.

Ces paramètres sont définis dans le schéma **nms:webTrackingLog** et font partie des indicateurs visibles dans le reporting.

Si vous souhaitez définir des paramètres supplémentaires, vous devrez étendre ce schéma.

**Exemple**:

```
<srcSchema extendedSchema="nms:webTrackingLog" label="Web Tracking"
           mappingType="sql" name="webTrackingLog" 
           namespace="cus" xtkschema="xtk:srcSchema">

  <element name="webTrackingLog">
    <attribute desc="Payment method" label="Payment method" length="10" name="mode" type="string"/>
    <attribute desc="Offer code" label="Offer code" length="5" name="code" type="string"/>
  </element>
</srcSchema>
```

Vous pourrez afficher les valeurs de ces paramètres en configurant la liste des logs de tracking (d&#39;une diffusion ou d&#39;un destinataire).

## Paramétrage du serveur de redirection {#redirection-server-configuration}

Dans la configuration du serveur, vous pouvez définir le nombre maximum de caractères que vous souhaitez prendre en compte pour vos paramètres de tracking Web.

>[!IMPORTANT]
>
>Augmenter le nombre de caractères à prendre en compte peut avoir une influence sur les performances de tracking web de votre plateforme.

Pour ce faire, modifiez l’attribut **webTrackingParamSize** de l’élément **`<trackinglogd>`** dans le fichier **serverConf.xml**. Ce fichier est enregistré dans le sous-répertoire **conf** du répertoire d’installation d’Adobe Campaign.

**Exemple**:

La valeur par défaut est de 64 caractères. Cette valeur permet de prendre en compte les paramètres standards **amount** et **article** (&quot;amount=xxxxxxxx&amp;article=xxxxxxxx&quot;).

En prenant en compte les deux paramètres (taille du nom + taille de la valeur) indiqués dans le schéma d&#39;extension d&#39;exemple ci-dessus, vous pouvez modifier la configuration pour prendre en compte 100 caractères (&quot;amount=xxxxxxxx&amp;article=xxxxxxxx&amp;mode=xxxxxxxxxx&amp;code=xxxxx&quot;).

```
<trackinglogd args="" autoStart="false" initScript="" maxCreateFileRetry="5" maxLogsSizeOnDiskMb="500"
maxProcessMemoryAlertMb="1800" maxProcessMemoryWarningMb="1600" maxSharedLogs="25000"
processRestartTime="06:00:00" purgeLogsPeriod="50000" runLevel="10"
webTrackingParamSize="64"/>
```

Une fois la configuration modifiée, vous devez :

* Arrêter le serveur Web qui héberge le module de redirection (Apache, IIS, ou autre),
* Arrêter le serveur Adobe Campaign : **net stop nlserver6** sous Windows, **/etc/init.d/nlserver6 stop** sous Linux,

  >[!NOTE]
  >
  >À compter de la version 20.1, nous vous recommandons d’utiliser plutôt la commande suivante (pour Linux) : **systemctl stop nlserver**

* Sous Linux, supprimer les segments de mémoire partagée via la commande **ipcrm**,
* Redémarrer le serveur Adobe Campaign : **net start nlserver6** sous Windows, **/etc/init.d/nlserver6 start** sous Linux,

  >[!NOTE]
  >
  >À compter de la version 20.1, nous vous recommandons d’utiliser plutôt la commande suivante (pour Linux) : **systemctl start nlserver**

* Redémarrer le serveur Web.

**Exemple** : prise en compte de la configuration sous Linux.

```
adobe@selma:~$ systemctl stop nlserver
adobe@selma:~$ systemctl stop apache2
adobe@selma:~$ ipcs shm

------ Shared Memory Segments --------
key        shmid      owner      perms      bytes      nattch     status      
0x52020679 2097153    adobe   666        93608      8                       

------ Semaphore Arrays --------
key        semid      owner      perms      nsems     
0x52020678 4227081    adobe   666        1         

------ Message Queues --------
key        msqid      owner      perms      used-bytes   messages    

adobe@selma:~$ ipcrm shm 2097153                             
1 resource(s) deleted
adobe@selma:~$ systemctl start nlserver
adobe@selma:~$ systemctl start apache2
```

>[!NOTE]
>
>Pour Linux, si vous augmentez la taille des paramètres **webTrackingParamSize** ou **maxSharedLogs**, vous devrez peut-être augmenter la taille de la mémoire partagée (SHM).
