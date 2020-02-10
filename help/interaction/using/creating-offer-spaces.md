---
title: Créer des emplacements d'offres
seo-title: Créer des emplacements d'offres
description: Créer des emplacements d'offres
seo-description: null
page-status-flag: never-activated
uuid: 2ad38697-db14-4dc0-abb8-9b71d57e0e35
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: managing-environments
discoiquuid: 0fae2149-0980-466d-ac9e-8afec2e278be
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 215e4d1ca78938b38b53cae0357612deebf7727b

---


# Créer des emplacements d&#39;offres{#creating-offer-spaces}

La création des emplacements ne peut être effectuée que par un **administrateur technique** qui a accès au sous-dossier des emplacements. Elle ne s&#39;effectue que dans l&#39;environnement en édition. Les emplacements sont automatiquement dupliqués dans l&#39;environnement en ligne lors de la validation des offres.

Le contenu des offres de catalogue est configuré dans les espaces d’offre. Par défaut, le contenu peut inclure les champs suivants : **[!UICONTROL Title]**, **[!UICONTROL Destination URL]**, **[!UICONTROL Image URL]**, **[!UICONTROL HTML content]** et **[!UICONTROL Text content]**. La séquence de champs est configurée dans l’espace d’offre.

Les paramètres avancés vous permettent de spécifier une clé d’identification des contacts (qui peut être composée de différents éléments, le nom et le champ de courrier électronique en même temps, par exemple). For more on this, refer to the [Presenting an identified offer](../../interaction/using/integration-via-javascript--client-side-.md#presenting-an-identified-offer) section.

Le rendu HTML ou XML est créé via une fonction de rendu. L&#39;ordre des champs définis dans la fonction de rendu doit être identique à celui paramétré dans le contenu.

![](assets/offer_space_create_009.png)

Pour créer un nouvel emplacement, procédez comme suit :

1. Go to the list of offer spaces and click **[!UICONTROL New]**.

   ![](assets/offer_space_create_001.png)

1. Sélectionnez le canal de votre choix et modifiez le libellé de l&#39;emplacement.

   ![](assets/offer_space_create_002.png)

1. Check the **[!UICONTROL Enable unitary mode]** box if one of the following cases applies to you:

   * utilisation d&#39;Interaction avec Message Center
   * si vous utilisez le mode unitaire d&#39;Interaction (interactions entrantes)

1. Accédez à la **[!UICONTROL Content field]** fenêtre et cliquez sur **[!UICONTROL Add]**.

   ![](assets/offer_space_create_003.png)

1. Accédez au **[!UICONTROL Content]** noeud et sélectionnez les champs dans l’ordre suivant : **[!UICONTROL Title]**, alors **[!UICONTROL Image URL]**, **[!UICONTROL HTML content]**, alors **[!UICONTROL Destination URL]**.

   ![](assets/offer_space_create_004.png)

1. Check the **[!UICONTROL Required]** box to make each field mandatory.

   >[!NOTE]
   >
   >Ce paramètre est utilisé lors de la prévisualisation et rend les emplacements invalides à la mise en ligne si l&#39;un des éléments obligatoires est manquant dans l&#39;offre concernée. Cependant, si une offre est déjà en ligne sur un emplacement, ce critère n&#39;est pas pris en compte.

   ![](assets/offer_space_create_005.png)

1. Cliquez sur **[!UICONTROL Edit functions]** pour créer une fonction de rendu.

   Ces fonctions sont utilisées pour générer la représentation des offres sur un emplacement. Plusieurs formats sont possibles : le HTML ou le texte pour les interactions sortantes et le XML pour les interactions entrantes.

   ![](assets/offer_space_create_006.png)

1. Accédez à l’ **[!UICONTROL HTML rendering]** onglet et sélectionnez **[!UICONTROL Overload the HTML rendering function]**.
1. Insérez votre fonction de rendu.

   ![](assets/offer_space_create_007.png)

Si nécessaire, vous pouvez surcharger les fonctions de rendu XML pour les interactions entrantes. Vous pouvez également surcharger les fonctions de rendu HTML et texte pour les interactions sortantes. For more on this, refer to [About inbound channels](../../interaction/using/about-inbound-channels.md).

## Etats d&#39;une proposition d&#39;offre {#offer-proposition-statuses}

Une proposition d&#39;offre peut avoir différents états en fonction des interactions avec la population ciblée. Interaction fournit d&#39;usine un ensemble de valeurs qui peuvent être appliquées à la proposition d&#39;offre tout au long de son cycle de vie. Vous devez cependant paramétrer la plateforme afin que l&#39;état soit modifié lorsque la proposition d&#39;offre est créée, puis acceptée.

>[!NOTE]
>
>La mise à jour de l&#39;état des propositions d&#39;offre n&#39;est pas immédiate. Elle est réalisée par le workflow de tracking qui se déclenche toutes les heures.

### Liste des états {#status-list}

Interaction fournit d&#39;usine les valeurs suivantes qui peuvent être utilisées pour marquer l&#39;état d&#39;une proposition d&#39;offre :

* **[!UICONTROL Accepted]**.
* **[!UICONTROL Scheduled]**.
* **[!UICONTROL Generated]**.
* **[!UICONTROL Interested]**.
* **[!UICONTROL Presented]**.
* **[!UICONTROL Rejected]**.

Ces valeurs ne sont pas appliquées par défaut et doivent donc être paramétrées.

>[!NOTE]
>
>Le statut d&#39;une proposition d&#39;offre est automatiquement changée en &quot;Présentée&quot; si l&#39;offre est associée à une diffusion avec le statut &quot;Envoyé&quot;.

### Paramétrer l&#39;état à la création de la proposition {#configuring-the-status-when-the-proposition-is-created}

Lorsqu’une proposition d’offre est créée par le moteur d’interaction, son état est modifié, qu’il s’agisse d’une interaction entrante ou sortante. Le choix entre ces deux valeurs dépend de la configuration des espaces d’offre dans l’ **[!UICONTROL Design]** environnement.

Pour chaque emplacement, vous pouvez paramétrer l&#39;état que vous souhaitez appliquer lors de la création de la proposition, selon l&#39;information que vous voulez voir apparaître dans les rapports d&#39;offre.

Pour cela :

1. Go to the **[!UICONTROL Storage]** tab of the desired space.
1. Sélectionnez l&#39;état que vous souhaitez voir s&#39;appliquer lors de la création de la proposition.

   ![](assets/offer_update_status_001.png)

### Paramétrer l&#39;état à l&#39;acceptation de la proposition d&#39;offre {#configuring-the-status-when-the-proposition-is-accepted}

Lorsqu&#39;une proposition d&#39;offre est acceptée, vous pouvez utiliser une des valeurs fournies par défaut pour configurer le nouvel état de la proposition. La mise à jour est effective lorsqu&#39;un destinataire clique sur un lien contenu dans l&#39;offre, ce qui a pour effet d&#39;appeler le moteur d&#39;interaction.

Pour cela :

1. Go to the **[!UICONTROL Storage]** tab of the desired space.
1. Sélectionnez l&#39;état que vous souhaitez appliquer à la proposition lorsqu&#39;elle est acceptée.

   ![](assets/offer_update_status_002.png)

**Interaction entrante**

L’ **[!UICONTROL Storage]** onglet vous permet de définir des états pour les propositions d’offre **proposées** et **acceptées** uniquement. Pour une interaction entrante, l’état des propositions d’offre doit être spécifié directement dans l’URL pour appeler le moteur d’offre, plutôt que par l’intermédiaire de l’interface. Ainsi, vous pourrez spécifier le statut à appliquer dans d’autres cas, par exemple si une proposition d’offre est rejetée.

```
<BASE_URL>?a=UpdateStatus&p=<PRIMARY_KEY_OF_THE_PROPOSITION>&st=<NEW_STATUS_OF_THE_PROPOSITION>&r=<REDIRECT_URL>
```

Par exemple, la proposition (identifiant **40004**) correspondant à l&#39;offre **Assurance habitation** et diffusée sur la page du site **Neobank** contient l&#39;URL suivante :

```
<BASE_URL>?a=UpdateStatus&p=<40004>&st=<3>&r=<"http://www.neobank.com/insurance/subscribe.html">
```

As soon as a visitor clicks the offer, and therefore the URL, the **[!UICONTROL Accepted]** status (value **3**) is applied to the proposition and the visitor is redirected to a new page of the **Neobank** site to take out the insurance contract.

>[!NOTE]
>
>Si vous souhaitez spécifier un autre état dans l’URL (par exemple, si une proposition d’offre est rejetée), utilisez la valeur correspondant à l’état souhaité. Exemple : **[!UICONTROL Rejected]** = &quot;5&quot;, **[!UICONTROL Presented]** = &quot;1&quot;, etc.
>
>Les états et leurs valeurs peuvent être récupérés dans le schéma de **[!UICONTROL Offer propositions (nms)]** données. Voir à ce propos [cette page](../../configuration/using/data-schemas.md).

**Interaction sortante**

En cas d’interaction sortante, vous pouvez appliquer automatiquement l’ **[!UICONTROL Interested]** état à une proposition d’offre lorsque la remise contient un lien. Ajoutez simplement la valeur **_urlType=&quot;11&quot;** au lien :

```
<a _urlType="11" href="<DEST_URL>">Link inserted into the delivery</a>
```

## Prévisualisation des offres par emplacement {#offer-preview-per-space}

Dans cet onglet vous pouvez visualiser les offres auxquelles un destinataire est éligible sur un emplacement choisi. Dans l&#39;exemple ci-dessous, le destinataire est éligible à trois propositions d&#39;offres sur l&#39;emplacement courrier.

![](assets/offer_space_overview_002.png)

Dans le cas où le destinataire n&#39;est éligible à aucune offre, la prévisualisation vous permet d&#39;en faire la vérification.

![](assets/offer_space_overview_001.png)

L’aperçu peut ignorer les contextes lorsqu’ils sont limités à un espace. C’est le cas lorsque le schéma d’interaction a été étendu pour ajouter des champs référencés dans un espace à l’aide d’un canal entrant (pour plus d’informations, reportez-vous à l’exemple [d’](../../interaction/using/extension-example.md)extension).
