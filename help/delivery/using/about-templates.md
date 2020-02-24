---
title: Modèles
seo-title: Modèles
description: Modèles
seo-description: null
page-status-flag: never-activated
uuid: 13b5ad3a-aded-43b8-ae4d-c23aa7bc17bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-delivery-templates
discoiquuid: 22e289d0-c33c-4daa-a893-b292e523f30b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# Modèles{#about-templates}

Le paramétrage d&#39;une diffusion peut être sauvegardé dans un modèle de diffusion afin d&#39;être réutilisé. Le modèle peut contenir un paramétrage complet ou partiel de la diffusion.

Le modèle de diffusion peut être exécuté manuellement, c&#39;est le cas décrit dans ce chapitre, ou exécuté selon un événement (lancement à heure fixe, à l&#39;arrivée d&#39;un fichier sur un serveur, etc.). Les opérations de configuration d&#39;un modèle de diffusion sont effectuées à partir du noeud **[!UICONTROL Ressources>Modèles>Modèles de diffusion]** de l&#39;arborescence.

![](assets/s_user_template_list.png)

Il existe deux types de modèles :

1. Les modèles de diffusion natifs d&#39;Adobe Campaign

   On parle de modèles natifs car ils NE DOIVENT PAS être supprimés du système et ils proposent un paramétrage minimal pour chaque canal de diffusion. L&#39;administrateur peut cependant restreindre certaines fonctionnalités ou proposer aux utilisateurs des valeurs par défaut (activation du tracking, adresses email expéditeur, etc.). Les modèles de diffusion natifs apparaissent en gras dans la liste des modèles. Ils doivent être dupliqués pour être modifiés.

1. Les modèles de diffusion prédéfinis

   L&#39;administrateur Adobe Campaign peut créer de nouveaux modèles de diffusion. Ils pourront être réutilisés par les opérateurs (s&#39;ils possèdent les droits d&#39;accès adéquats) ou automatiquement par les processus serveur. Par exemple, vous pouvez paramétrer un modèle de diffusion par email et lorsque l&#39;utilisateur créé une diffusion à partir de ce modèle, il n&#39;a plus qu&#39;à saisir le contenu texte ou HMTL puis diffuser, les autres choix ayant été préalablement définis par l&#39;administrateur.

>[!NOTE]
>
>Les modèles disponibles dépendent de vos droits d’accès, de la configuration de votre instance et du contexte. Par exemple, lorsque vous créez un service d’informations, vous pouvez lier un modèle de remise pour les messages de confirmation : vous pouvez alors accéder uniquement aux modèles dont le mappage cible est le mappage d’abonnement. Pour plus d’informations, reportez-vous aux sections [Sélection d’un mappage](../../delivery/using/selecting-a-target-mapping.md) cible et [À propos des services et des abonnements](../../delivery/using/about-services-and-subscriptions.md).
