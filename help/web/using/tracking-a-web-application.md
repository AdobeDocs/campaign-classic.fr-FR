---
title: Tracking d’une application web
seo-title: Tracking d’une application web
description: Tracking d’une application web
seo-description: null
page-status-flag: never-activated
uuid: c087b40c-fd14-440f-8f38-33f5f68120a9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-applications
discoiquuid: 8e52f927-dadd-44c8-a51d-f717bc083eef
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 36beb1eca48c698634c7548e0f931ab3fe17c021
workflow-type: ht
source-wordcount: '416'
ht-degree: 100%

---


# Tracking d’une application web{#tracking-a-web-application}

Adobe Campaign permet de suivre et de mesurer les visites sur les pages des applications Web en insérant des balises de tracking. Il est possible d&#39;utiliser cette fonctionnalité pour tous les types d&#39;applications Web (formulaires, enquêtes en ligne, pages Web créées à l&#39;aide de DCE, etc.).

Vous pouvez ainsi définir plusieurs chemins de navigation et en évaluer le succès. Les mesures ainsi effectuées sont répertoriées dans les rapports disponibles au niveau de chaque application.

Les principales fonctionnalités proposées dans cette version sont les suivantes :

* Possibilité d&#39;insérer plusieurs balises de tracking sur une même page, afin de faciliter la définition de chemins de navigation (ex : achat, inscription, retour, etc.).
* Visualisation des chemins de navigation et des balises de tracking des différentes pages depuis le tableau de bord de l&#39;application Web.

   ![](assets/trackers_1.png)

* Génération d&#39;un rapport de tracking complet.

   ![](assets/trackers_5.png)

   Les principaux indicateurs sont les suivants :

   * **Taux de conversion** : nombre de personnes qui ont parcouru toutes les étapes d&#39;un chemin de navigation.
   * **Taux de rebond** : nombre de personnes qui n&#39;ont affiché que la première étape.
   * **Tunnel de conversion** : taux de perte entre chacune des étapes.

   En complément, un graphique de type **Secteur** représente la population en fonction de son origine.

## Identification de la source du trafic {#identifying-the-traffic-source}

Deux modes différents permettent d&#39;identifier l&#39;origine du visiteur lors de l&#39;accès à une application Web :

1. Envoyer une diffusion spécifique pour donner accès aux pages de l&#39;application Web : dans ce cas, la source de trafic est cette diffusion,
1. Associer l&#39;application Web à une source de trafic dédiée : dans ce cas, il doit s&#39;agir d&#39;une diffusion externe de type &#39;traffic source&#39;. Le choix est effectué dans les propriétés de l&#39;application Web ou du mapping de ciblage.

   ![](assets/trackers_6.png)

Afin d&#39;identifier la source de trafic sur une application Web, Adobe Campaign recherche successivement les informations suivantes :

1. l&#39;identifiant de la diffusion source, si elle existe (cookie nlId),
1. l&#39;identifiant de la diffusion externe définie dans les propriétés de l&#39;application Web, si elle existe,
1. l&#39;identifiant de la diffusion externe définie au niveau du mapping de ciblage, si elle existe.

>[!NOTE]
>
>Pour rappel, le tracking anonyme n&#39;est possible que si cette option a été activée dans l&#39;assistant de déploiement.
>
>Voir à ce propos le [Guide d&#39;installation](../../installation/using/deploying-an-instance.md).

## Applications web conçues avec Digital Content Editor (DCE) {#web-applications-designed-with-digital-content-editor--dce-}

Lorsqu&#39;une application web est créée en utilisant l&#39;éditeur de contenus HTML - **Digital Content Editor (DCE)** -, les balises de tracking sont insérées depuis le sous-onglet **[!UICONTROL Propriétés]** de l&#39;éditeur. Pour plus d&#39;informations sur le Digital Content Editor (DCE), consultez [cette section](../../web/using/about-campaign-html-editor.md).

![](assets/trackers_2.png)

Lorsque l&#39;opérateur utilise l&#39;interface Web, les balises de tracking doivent être insérées depuis les propriétés de la page.

![](assets/trackers_3.png)

L&#39;icône **[!UICONTROL Afficher les blocs]** permet de visualiser le nombre de balises de tracking configurées pour la page.

![](assets/trackers_4.png)

