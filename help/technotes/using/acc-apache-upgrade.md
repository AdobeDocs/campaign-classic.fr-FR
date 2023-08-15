---
product: campaign
title: Note technique - Adobe Campaign - Mise à jour de sécurité de la version Apache
description: Adobe Campaign - Mise à jour de sécurité de la version Apache
feature: Technote, Upgrade
hide: true
hidefromtoc: true
exl-id: 3d2f5d1d-4b31-4cc6-b6fb-13589856e00c
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 100%

---

# Adobe Campaign - Mise à jour de sécurité de la version Apache {#apache-update}

>[!CAUTION]
>Cet article s’applique aux : clients de **Campaign Classic v7 Managed Services**, de **Campaign v8** et de **Campaign Standard**.

Adobe Campaign fonctionne avec des outils tiers, qui bénéficient de mises à jour de compatibilité fréquentes. Ainsi, seules les versions prises en charge dotées des derniers correctifs et améliorations sont implémentées.

Adobe Campaign comprend Apache Tomcat, qui agit comme point d’entrée dans le serveur d’applications via HTTP et est intégré au serveur web Apache. L’Apache Software Foundation a publié le serveur HTTP Apache 2.4.53. Cette version corrige des vulnérabilités qui peuvent permettre à une personne malveillante de prendre le contrôle d’un système affecté. En savoir plus sur la page d’[Annonce d’Apache 2.4.53](https://downloads.apache.org/httpd/Announcement2.4.html){target="_blank"}.

L’équipe d’Adobe Campaign procédera à la mise à niveau de sécurité de la version Apache d’ici le **15 juin 2022**. Celle-ci permettra d’atténuer cette vulnérabilité Apache et de rendre votre environnement d’instance plus sûr. Cette mise à niveau s’applique à tous les clients de Campaign Classic v7 Managed Services, de Campaign v8 et de Campaign Standards qui s’exécutent sur une version vulnérable du serveur HTTP Apache. Si vous êtes concerné, Adobe vous a déjà contacté pour vous informer de cette mise à niveau.

Cette mise à niveau s’exécutera automatiquement en dehors de vos heures de bureau normales, afin que vous puissiez continuer à utiliser le service Campaign sans aucune interruption.

Vos instances hors production seront d&#39;abord mises à niveau par Adobe, suivies de vos instances de production. Comme il s’agit d’un processus de mise à niveau automatique relevant d’Adobe, aucune action n’est requise de votre part. Contactez l’[Assistance clientèle d’Adobe](https://experienceleague.adobe.com/?support-solution=Campaign#support) pour tout problème rencontré.


>[!NOTE]
>Cette mise à niveau nécessite le redémarrage du serveur web Apache. Le temps d’arrêt ne dépassera pas 10 minutes dans le créneau horaire mentionné ci-dessous.
> 

## Forum aux questions {#apache-faq}

* **Pourquoi cette mise à niveau est-elle obligatoire ?**

  La version actuelle d’Apache est vulnérable et présente une menace potentielle pour la sécurité. Il est important que votre ou vos instances Campaign soient mises à niveau vers la dernière version d’Apache applicable pour éviter tout risque de sécurité.

* **Quels sont les clients concernés par les mises à niveau de sécurité ?**

  Tous les clients utilisant des environnements Campaign implémentés sur d’anciennes versions d’Apache sont mis à niveau vers la dernière version d’Apache applicable.

* **Quel est le temps d’arrêt prévu ?**

  Le temps d’arrêt prévu est inférieur à 10 minutes.

* **Le client doit-il prendre des mesures pour cette mise à niveau de sécurité ?**

  Aucune action n’est requise, car la mise à jour de sécurité s’exécutera automatiquement.

* **Quel est l’impact sur les campagnes/workflows en cours d’exécution pendant la période de maintenance ?**

  Pendant la période de maintenance, le workflow et les services de messagerie seront arrêtés, et les activités planifiées ne seront pas exécutées. Les activités en cours ou les processus en cours d’exécution seront interrompus pendant les temps d’arrêt jusqu’au redémarrage du serveur. Une fois l’activité terminée et le serveur redémarré, tous les services reprendront.

* **Le client doit-il effectuer des validations ?**

  Aucun test spécifique n’est nécessaire pour cette mise à niveau de sécurité. Contactez l’[Assistance clientèle d’Adobe](https://experienceleague.adobe.com/?support-solution=Campaign#support) pour tout problème rencontré..


* **Puis-je demander un changement de date/heure du créneau prévu pour la mise à niveau de sécurité ?**

  Comme il s’agit d’un correctif de sécurité, nous vous recommandons vivement de vous conformer au calendrier existant.


Pour toute autre question, contactez l’[Assistance clientèle d’Adobe](https://experienceleague.adobe.com/?support-solution=Campaign#support).
