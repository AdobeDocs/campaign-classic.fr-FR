---
product: campaign
title: Agir sur les rapports
description: Agir sur les rapports
audience: reporting
content-type: reference
topic-tags: creating-new-reports
exl-id: b30cdeaf-4ad6-473d-bdbc-91984755b609
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: ht
source-wordcount: '573'
ht-degree: 100%

---

# Agir sur les rapports{#actions-on-reports}

![](../../assets/common.svg)

Lorsque vous visualisez un rapport, la barre d&#39;outils vous permet d&#39;effectuer certaines actions. Elles sont présentées ci-après.

![](assets/s_ncs_advuser_report_wizard_2.png)

La barre d&#39;outils vous permet d&#39;exporter, imprimer, créer un historique ou afficher le rapport dans un navigateur web par exemple.

![](assets/s_ncs_advuser_report_wizard_04.png)

## Exporter un rapport {#exporting-a-report}

Choisissez le format vers lequel vous souhaitez exporter votre rapport dans la liste déroulante (.xls, .pdf ou .ods).

![](assets/s_ncs_advuser_report_wizard_06.png)

Lorsqu&#39;un rapport contient plusieurs pages, vous devez répéter l&#39;opération pour chacune des pages.

Vous pouvez paramétrer votre rapport en vue de son export au format PDF, Excel ou OpenOffice. Ouvrez l&#39;explorateur Adobe Campaign et sélectionnez le rapport concerné.

Les options d&#39;export sont accessibles depuis la ou les activité(s) **[!UICONTROL Page]** du rapport, dans l&#39;onglet **[!UICONTROL Avancé]**.

Modifiez les paramètres **[!UICONTROL Papier]** et **[!UICONTROL Marges]** selon vos besoins. Vous pouvez également n&#39;autoriser l&#39;export d&#39;une page qu&#39;au format PDF. Pour cela, dé-sélectionnez l&#39;option **[!UICONTROL Activer l&#39;export OpenOffice/ Microsoft Excel]**.

![](assets/s_ncs_advuser_report_wizard_021.png)

### Exporter dans Microsoft Excel {#exporting-into-microsoft-excel}

Dans les rapports de type **[!UICONTROL Liste avec groupement]** destinés à être exportés au format Excel, les recommandations et limitations sont les suivantes:

* Ces rapports ne doivent pas contenir de ligne vide.

   ![](assets/export_limitations_remove_empty_line.png)

* La légende de la liste doit être cachée.

   ![](assets/export_limitations_hide_label.png)

* Les rapports ne doivent pas utiliser de formatage spécifique défini au niveau des cellules. Il est préférable d&#39;utiliser le **[!UICONTROL Rendu des formulaires]** pour définir le format des cellules du tableau. Le **[!UICONTROL Rendu des formulaires]** est accessible depuis **[!UICONTROL Administration > Paramétrage > Rendu des formulaires]**.
* Il est recommandé de ne pas insérer de contenu HTML.
* Lorsqu&#39;un rapport contient plusieurs éléments de type tableaux, graphiques, etc., ils seront exportés les uns en-dessous des autres.
* Vous pouvez forcer le retour à la ligne dans les cellules : cette configuration sera conservée dans Excel. Voir à ce sujet la section [Définir le format des cellules](../../reporting/using/creating-a-table.md#defining-cell-format).

### Retarder l&#39;export {#postpone-the-export}

Vous pouvez retarder l&#39;export d&#39;un rapport, par exemple pour attendre des appels asynchrones. Pour cela, saisissez le paramètre suivant dans le script d&#39;initialisation de la page :

```
document.nl_waitBeforeRender = true;
```

Pour activer l&#39;export et lancer la conversion en PDF, utilisez la fonction **document.nl_renderToPdf()** sans paramètre.

### Allocation de mémoire {#memory-allocation}

Lors de l&#39;export de certains rapports volumineux, il peut se produire des erreurs d&#39;allocation de mémoire.

Dans certaines instances, la valeur par défaut **maxMB** (**SKMS** pour les instances hébergées) du JavaScript indiquée dans le fichier de configuration **serverConf.xml** est fixée à 64 MB. Si vous rencontrez des erreurs de mémoire insuffisante quand vous exportez un rapport, il peut être recommandé d&#39;augmenter ce chiffre à 512 MB :

```
<javaScript maxMB="512" stackSizeKB="8"/>
```

Pour appliquer les changements apportés à la configuration, un redémarrage du service **nlserver** est nécessaire.

Pour en savoir plus sur le fichier **serverConf.xml**, consultez [cette section](../../production/using/configuration-principle.md).

Pour en savoir plus sur le fichier **nlserver**, consultez [cette section](../../production/using/administration.md).

## Imprimer un rapport {#printing-a-report}

Vous pouvez imprimer votre rapport : pour cela, cliquez sur l&#39;icône d&#39;impression. La boîte de dialogue d&#39;impression s&#39;ouvre.

Pour un meilleur résultat, éditez les options d&#39;impression d&#39;Internet Explorer et sélectionnez l&#39;option **[!UICONTROL Imprimer les couleurs et les images d&#39;arrière-plan]**.

![](assets/s_ncs_advuser_report_print_options.png)

## Créer des historiques de rapports {#creating-report-archives}

L&#39;historisation d&#39;un rapport vous permet de créer une vue du rapport à différentes périodes. Cela peut être pour faire apparaître des statistiques à un instant donné.

Pour créer un historique, ouvrez le rapport concerné puis cliquez sur l&#39;icône de création d&#39;historique.

![](assets/s_ncs_advuser_report_wizard_07.png)

Vous pouvez masquer ou afficher les historiques existants en cliquant sur l&#39;icône d&#39;affichage/dissimulation.

![](assets/s_ncs_advuser_report_history_06.png)

La ou les dates d&#39;historiques s&#39;affichent sous l&#39;icône d&#39;affichage/dissimulation. Cliquez sur un historique pour le visualiser.

![](assets/s_ncs_advuser_report_history_04.png)

Vous avez la possibilité de supprimer l&#39;historique d&#39;un rapport. Pour cela, positionnez-vous dans l&#39;arborescence d&#39;Adobe Campaign au niveau du noeud où se trouvent vos rapports. Cliquez sur l&#39;onglet **[!UICONTROL Historiques]**, sélectionnez l&#39;historique voulu et cliquez sur **[!UICONTROL Supprimer]**.

![](assets/s_ncs_advuser_report_history_01.png)
