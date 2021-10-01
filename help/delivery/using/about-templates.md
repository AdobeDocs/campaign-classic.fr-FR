---
product: campaign
title: À propos des modèles
description: À propos des modèles
audience: delivery
content-type: reference
topic-tags: using-delivery-templates
exl-id: d943898c-06fe-451d-aa28-8a95665f4112
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: ht
source-wordcount: '279'
ht-degree: 100%

---

# À propos des modèles{#about-templates}

![](../../assets/common.svg)

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
>Les modèles disponibles dépendent de vos droits d’accès, du paramétrage de votre instance et du contexte dans lequel ils sont appelés. Lorsque vous créez un service d’information, vous pouvez y associer un modèle de diffusion pour les messages de confirmation : vous ne pourrez accéder qu’aux modèles dont le mapping de ciblage est celui des abonnements. Voir à ce sujet les sections [Choisir un mapping de ciblage](selecting-a-target-mapping.md) et [À propos des services et des abonnements](about-services-and-subscriptions.md).
