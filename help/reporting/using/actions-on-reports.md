---
product: campaign
title: Agir sur les rapports
description: Agir sur les rapports
feature: Reporting, Monitoring
badge-v7: label="v7" type="Informative" tooltip="S’applique à Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="S’applique également à Campaign v8"
exl-id: b30cdeaf-4ad6-473d-bdbc-91984755b609
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 80%

---

# Agir sur les rapports{#actions-on-reports}



Lorsque vous visualisez un rapport, la barre d&#39;outils vous permet d&#39;effectuer certaines actions. Elles sont présentées ci-après.

![](assets/s_ncs_advuser_report_wizard_2.png)

La barre d&#39;outils vous permet d&#39;exporter, imprimer, créer un historique ou afficher le rapport dans un navigateur web par exemple.

![](assets/s_ncs_advuser_report_wizard_04.png)

## Exportation dʼun rapport {#exporting-a-report}

Choisissez le format vers lequel vous souhaitez exporter votre rapport dans la liste déroulante (.xls, .pdf ou .ods).

![](assets/s_ncs_advuser_report_wizard_06.png)

Lorsqu&#39;un rapport contient plusieurs pages, vous devez répéter l&#39;opération pour chacune des pages.

Vous pouvez paramétrer votre rapport en vue de son export au format PDF, Excel ou OpenOffice. Ouvrez l&#39;explorateur Adobe Campaign et sélectionnez le rapport concerné.

Les options d&#39;export sont accessibles depuis la ou les activité(s) **[!UICONTROL Page]** du rapport, dans l&#39;onglet **[!UICONTROL Avancé]**.

Modification des paramètres de **[!UICONTROL Papier]** et **[!UICONTROL Marges]** à vos besoins. Vous pouvez également n&#39;autoriser l&#39;export d&#39;une page qu&#39;au format PDF. Pour ce faire, décochez la case **[!UICONTROL Activer l’exportation OpenOffice/Microsoft Excel]** .

![](assets/s_ncs_advuser_report_wizard_021.png)

### Exportation dans Microsoft Excel {#exporting-into-microsoft-excel}

Dans les rapports de type **[!UICONTROL Liste avec groupement]** destinés à être exportés au format Excel, les recommandations et limitations sont les suivantes:

* Ces rapports ne doivent pas contenir de ligne vide.

  ![](assets/export_limitations_remove_empty_line.png)

* La légende de la liste doit être cachée.

  ![](assets/export_limitations_hide_label.png)

* Les rapports n’ont pas besoin d’utiliser une mise en forme spécifique définie au niveau des cellules. Il est préférable d’utiliser **[!UICONTROL Rendu du formulaire]** pour définir le format des cellules du tableau. La variable **[!UICONTROL Rendu du formulaire]** accessible via **[!UICONTROL Administration > Configuration > Rendus des formulaires]**.
* Il est recommandé de ne pas insérer de contenu HTML.
* Lorsqu&#39;un rapport contient plusieurs éléments de type tableaux, graphiques, etc., ils seront exportés les uns en-dessous des autres.
* Vous pouvez forcer le retour à la ligne dans les cellules : cette configuration sera conservée dans Excel. Pour plus d’informations, consultez [cette section](../../reporting/using/creating-a-table.md#defining-cell-format).

### Retarder l&#39;export {#postpone-the-export}

Vous pouvez retarder l&#39;export d&#39;un rapport, par exemple pour attendre des appels asynchrones. Pour cela, saisissez le paramètre suivant dans le script d&#39;initialisation de la page :

```
document.nl_waitBeforeRender = true;
```

Pour activer l&#39;export et lancer la conversion en PDF, utilisez la fonction **document.nl_renderToPdf()** sans paramètre.

### Allocation de mémoire {#memory-allocation}

Lors de l&#39;export de certains rapports volumineux, il peut se produire des erreurs d&#39;allocation de mémoire.

Dans certaines instances, la valeur par défaut **maxMB** (**SKMS** pour les instances hébergées) du JavaScript indiquée dans le fichier de configuration **serverConf.xml** est fixée à 64 MB. Si vous rencontrez des erreurs de mémoire insuffisante quand vous exportez un rapport, il peut être recommandé d&#39;augmenter ce chiffre à 512 MB :

```
<javaScript maxMB="512" stackSizeKB="8"/>
```

Pour appliquer les changements apportés à la configuration, un redémarrage du service **nlserver** est nécessaire.

Pour en savoir plus sur le fichier **serverConf.xml**, consultez [cette section](../../production/using/configuration-principle.md).

Pour en savoir plus sur le fichier **nlserver**, consultez [cette section](../../production/using/administration.md).

## Impression dʼun rapport {#printing-a-report}

Vous pouvez imprimer votre rapport : pour cela, cliquez sur l’icône d’impression. La boîte de dialogue d’impression s’ouvre.

Pour un meilleur résultat, éditez les options d’impression d’Explorer et sélectionnez l’option **[!UICONTROL Imprimer les couleurs et les images d’arrière-plan]**.

![](assets/s_ncs_advuser_report_print_options.png)

## Création dʼhistoriques de rapports {#creating-report-archives}

L&#39;historisation d&#39;un rapport vous permet de créer une vue du rapport à différentes périodes. Cela peut être pour faire apparaître des statistiques à un instant donné.

Pour créer un historique, ouvrez le rapport concerné puis cliquez sur l&#39;icône de création d&#39;historique.

![](assets/s_ncs_advuser_report_wizard_07.png)

Vous pouvez masquer ou afficher les historiques existants en cliquant sur l&#39;icône d&#39;affichage/dissimulation.

![](assets/s_ncs_advuser_report_history_06.png)

La ou les dates d&#39;historiques s&#39;affichent sous l&#39;icône d&#39;affichage/dissimulation. Cliquez sur un historique pour le visualiser.

![](assets/s_ncs_advuser_report_history_04.png)

Il est possible de supprimer une archive de rapport. Pour ce faire, accédez au noeud Adobe Campaign où sont stockés vos rapports. Cliquez sur le bouton **[!UICONTROL Archives]** , sélectionnez celle que vous souhaitez supprimer, puis cliquez sur **[!UICONTROL Supprimer]**.

![](assets/s_ncs_advuser_report_history_01.png)
