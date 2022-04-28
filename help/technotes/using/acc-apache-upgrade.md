---
product: campaign
title: Note technique - Adobe Campaign - Mise à jour de la sécurité des versions d’Apache
description: Adobe Campaign - Mise à jour de la sécurité des versions d’Apache
hide: true
hidefromtoc: true
source-git-commit: 41aa16e3ac6f150b9a048a22729b4cc4b9ccc10a
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 6%

---

# Adobe Campaign - Mise à jour de la sécurité des versions d’Apache {#apache-update}

Campaign Classic fonctionne avec des outils tiers. La compatibilité est régulièrement mise à jour afin de mettre en oeuvre les versions prises en charge uniquement et de bénéficier des correctifs et améliorations les plus récents.

Adobe Campaign inclut Apache Tomcat qui agit comme point d’entrée dans le serveur applicatif via HTTP et est intégré au serveur web Apache. Apache Software Foundation a publié Apache HTTP Server 2.4.53. Cette version corrige les vulnérabilités qui peuvent permettre à un attaquant distant de prendre le contrôle d’un système affecté. En savoir plus dans [Annonce Apache 2.4.53](https://downloads.apache.org/httpd/Announcement2.4.html){target=&quot;_blank&quot;}.

L’équipe Adobe Campaign mènera l’activité de mise à niveau de sécurité de version Apache en procédant comme suit : **31 mai 2022** pour atténuer cette vulnérabilité Apache et sécuriser votre environnement d’instance. Cette mise à niveau s’applique à tous les clients Managed Services s’exécutant sur une version vulnérable du serveur Apache HTTP. Si vous êtes concerné, Adobe vous a déjà contacté pour vous informer de cette mise à niveau.

Cette mise à niveau est censée s’exécuter automatiquement en dehors de vos heures de bureau normales pour que vous puissiez continuer à utiliser le service Campaign sans interruption.

Vos instances hors production seront d’abord mises à niveau par nos équipes avant de mettre à niveau vos instances de production. Puisqu’il s’agit d’un processus de mise à niveau automatique détenu par Adobe, aucune action n’est requise de votre côté. Cependant, si vous rencontrez des problèmes, veuillez contacter [Assistance clientèle Adobe](https://experienceleague.adobe.com/?support-solution=Campaign#support).


>[!NOTE]
>Cette mise à niveau nécessite le redémarrage du serveur web Apache. Le temps d’arrêt ne dépassera pas 10 minutes dans l’intervalle mentionné ci-dessous.

## Forum aux questions {#apache-faq}

* **Pourquoi s’agit-il d’une mise à niveau obligatoire ?**

   La version actuelle d’Apache est vulnérable et présente une menace potentielle pour la sécurité. Il est important que votre ou vos instances Campaign soient mises à niveau vers la dernière version d’Apache applicable afin de répondre aux risques de sécurité.


* **Quels clients sont ciblés pour les mises à niveau de sécurité ?**

   Tous les clients qui utilisent des environnements Campaign implémentés sur des versions plus anciennes d’Apache sont mis à niveau vers la dernière version d’Apache applicable.

* **Quel est le temps d’arrêt attendu ?**

   Le temps d’arrêt attendu est inférieur à 10 minutes.


* **Des actions sont-elles requises par le client pour cet upgrade de sécurité ?**

   Aucune action n’est requise, car l’upgrade de sécurité s’exécute automatiquement.


* **Quelles validations doivent être exécutées par les clients ?**

   Aucun test spécifique n’est nécessaire pour cette mise à niveau de sécurité. Si un problème est observé, veuillez contacter [Assistance clientèle Adobe](https://experienceleague.adobe.com/?support-solution=Campaign#support)


* **Puis-je demander un changement de date/heure dans l’emplacement de mise à niveau de sécurité planifiée ?**

   Puisqu’il s’agit d’un correctif de sécurité, nous vous recommandons vivement de vous adapter au planning existant.


Pour toute autre question, contactez l’[Assistance clientèle d’Adobe](https://experienceleague.adobe.com/?support-solution=Campaign#support).
