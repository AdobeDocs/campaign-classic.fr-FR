---
product: campaign
title: Créer un rapport
description: Découvrez les étapes principales pour créer un rapport
feature: Reporting
exl-id: 4c2aad47-0e2d-4d0b-8898-b437f4a05e11
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: ht
source-wordcount: '0'
ht-degree: 100%

---

# Création d’un rapport{#creating-a-new-report}



Pour créer un rapport, les étapes sont les suivantes :

1. Ouvrez l&#39;Explorateur Adobe Campaign et, depuis le nœud **[!UICONTROL Administration > Paramétrage]**, sélectionnez le dossier **[!UICONTROL Rapports]**.
1. Cliquez sur le bouton **[!UICONTROL Nouveau]** situé au-dessus de la liste des rapports.
1. Choisissez **[!UICONTROL Créer un nouveau rapport depuis un modèle]** et cliquez sur **[!UICONTROL Suivant]**.

   ![](assets/s_ncs_advuser_report_wizard_new_01.png)

1. Choisissez le modèle de rapport dans la liste déroulante.

   * Le modèle **[!UICONTROL Rapport étendu]** permet de créer un rapport paramétré à l&#39;aide d&#39;un diagramme.
   * Le rapport **[!UICONTROL Distribution qualitative]** permet de faire des statistiques sur tous types de données (ex. nom d&#39;une société, domaine d&#39;email, etc.).
   * Le rapport **[!UICONTROL Distribution quantitative]** permet de faire des statistiques sur des données qui peuvent être mesurées ou comptées (ex. montant d&#39;une facture, âge d&#39;un destinataire).

   Pour plus d&#39;informations sur ces modèles de rapport, consultez [cette section](../../reporting/using/about-descriptive-analysis.md).

1. Saisissez le nom du rapport et sa description dans les champs correspondants. Indiquez le **[!UICONTROL schéma]** sur lequel s&#39;appliquera le rapport.

   ![](assets/s_ncs_advuser_report_wizard_020.png)

1. Enregistrez ce rapport.

## Modélisation du graphique {#modelizing-the-chart}

Après avoir enregistré votre rapport, ce dernier s&#39;affiche. Vous pouvez désormais construire le diagramme de votre rapport.

![](assets/s_ncs_user_report_wizard_021.png)

Le diagramme de construction du rapport est constitué d&#39;un enchaînement linéaire d&#39;activités.

![](assets/s_ncs_advuser_report_wizard_031.png)

Les activités sont reliées les unes aux autres par des transitions, représentées par des flèches.

![](assets/s_ncs_advuser_report_wizard_032.png)

Pour construire votre rapport, selon sa nature et son contexte d&#39;utilisation, vous devez identifier les éléments utiles et modéliser leur enchaînement logique.

1. Utilisez l&#39;activité **[!UICONTROL Début]** pour matérialiser le premier traitement à effectuer pour construire le rapport. Vous ne pouvez positionner qu&#39;une seule activité de ce type dans un même rapport.

   Elle est obligatoire lorsque le diagramme contient une boucle.

1. Ajoutez un ou plusieurs activités **[!UICONTROL Requête]** pour collecter les données utiles à la construction du rapport. Les données peuvent être collectées directement via une requête sur un schéma de la base de données, ou au travers d&#39;une liste importée, ou via un Cube existant.

   Pour plus dʼinformations, consultez la section [Collecte des données à analyser](../../reporting/using/collecting-data-to-analyze.md).

   Ces données seront affichées ou non dans le rapport, selon la configuration des pages.

1. Positionnez une ou plusieurs activités **[!UICONTROL Page]** pour définir la présentation graphique des données collectées. Vous pouvez y insérer des tableaux, graphiques, champs de saisie, et conditionner l&#39;affichage d&#39;une ou plusieurs pages, ou de certains éléments de la page. Le contenu affiché est entièrement paramétrable.

   Voir à ce sujet la section [Éléments statiques](#static-elements).

1. Utilisez une activité **[!UICONTROL Test]** pour définir des conditions d&#39;affichage ou d&#39;accès à certaines données.

   Voir à ce sujet la section [Conditionner l&#39;affichage d&#39;une page](../../reporting/using/defining-a-conditional-content.md#conditioning-page-display).

1. Au besoin, ajoutez des scripts personnalisés via l&#39;activité **[!UICONTROL Script]**, par exemple pour calculer le nom d&#39;un rapport, filtrer l&#39;affichage du résultat dans un contexte précis, etc.

   Voir à ce sujet la section [Activité Script](../../reporting/using/advanced-functionalities.md#script-activity).

1. Enfin, vous pouvez simplifier la lisibilité des rapports complexes en y insérant une ou plusieurs activités de type **[!UICONTROL Saut]** : elles permettent de passer d&#39;une activité à l&#39;autre sans matérialiser la transition sur le rapport. L&#39;activité **[!UICONTROL Saut]** peut également être utilisée pour afficher un autre rapport.

   Voir à ce sujet la section [Activité Saut](../../reporting/using/advanced-functionalities.md#jump-activity).

Le mode d&#39;exécution d&#39;un rapport n&#39;est pas celui d&#39;un workflow. Typiquement, vous ne pouvez pas exécuter plusieurs branches en parallèle. Ainsi, un rapport construit comme suit ne sera pas opérationnel :

![](assets/reporting_graph_sample_ko.png)

Par contre, il est possible de positionner plusieurs branches. Une seule d&#39;entre elles sera exécutée :

![](assets/reporting_graph_sample_ok.png)

## Création d’une page {#creating-a-page}

Le contenu est paramétré au travers des activités positionnées dans le diagramme. Pour plus dʼinformations, consultez la section [Modélisation du graphique](#modelizing-the-chart).

Pour paramétrer chaque activité, double-cliquez sur son icône.

Le contenu affiché est défini dans les activités de type **Page**.

Un rapport peut contenir une ou plusieurs pages. Les pages sont créées à travers un éditeur dédié qui permet d&#39;y insérer, dans une arborescence, des zones de saisie, des champs de sélection, des éléments statiques, des graphiques ou des tableaux. La mise en page de ces éléments est réalisée au travers de conteneurs. Voir à ce sujet la section [Mettre en page des éléments](../../reporting/using/element-layout.md).

Pour ajouter un composant dans la page, utilisez les icônes situées dans la section gauche de la barre d&#39;outils.

![](assets/reporting_add_component_in_page.png)

Vous pouvez également cliquer avec le bouton droit sur le noeud dans lequel vous souhaitez l&#39;insérer et le choisir parmi ceux disponibles.

![](assets/s_ncs_advuser_report_wizard_09.png)

>[!CAUTION]
>
>Si le rapport est destiné à être exporté au format Excel, il est recommandé de ne pas utiliser de formatage complexe en HTML. Pour plus dʼinformations, consultez la section [Exportation dʼun rapport](../../reporting/using/actions-on-reports.md#exporting-a-report).

Une **[!UICONTROL Page]** peut contenir les éléments suivants :

* Des **[!UICONTROL Graphiques]** de type Histogramme, Secteurs, Courbes, etc.
* Des **[!UICONTROL Tableaux]** de type Tableau croisé dynamique, Liste avec groupement ou Répartition.
* Des **[!UICONTROL Contrôles de saisie]** de type Texte ou Nombre.
* Des **[!UICONTROL Contrôles de sélection]** de type Liste déroulante, Case à cocher, Bouton radio, Choix multiples, Dates ou Matrice.
* Des **[!UICONTROL Contrôles avancés]** de type Editeur de lien, Constante, Choix de dossier.
* Des **[!UICONTROL Eléments statiques]** de type Valeur, Lien, HTML, Image, etc.
* Des **[!UICONTROL Conteneur]** pour assurer la mise en page des composants.

Le mode de paramétrage d&#39;une page et de ses composants est présenté dans [cette section](../../web/using/about-web-forms.md).

La barre d&#39;outils vous permet d&#39;ajouter ou supprimer les contrôles et d&#39;organiser l&#39;ordre dans lequel ils doivent apparaître dans la ou les pages de votre rapport.

![](assets/s_ncs_advuser_report_wizard_08.png)

### Eléments statiques {#static-elements}

Les éléments statiques vous permettent d&#39;afficher des informations dans le rapport, des éléments graphiques ou des scripts, avec lequel l&#39;utilisateur n&#39;aura pas d&#39;interaction. Pour plus d&#39;informations, consultez [cette section](../../web/using/static-elements-in-a-web-form.md#inserting-html-content).

![](assets/s_advuser_report_page_activity_03.png)

### Filtrage des informations dans un rapport {#filtering-information-in-a-report}

Les contrôles de saisie et de sélection permettent de filtrer les informations affichées dans le rapport. Pour plus d&#39;informations sur la mise en œuvre de ce type de filtrage, consultez [Options de filtrage dans les requêtes](../../reporting/using/collecting-data-to-analyze.md#filtering-options-in-the-queries).

Pour plus d&#39;informations sur la création et le paramétrage des champs de saisie et des champs de sélection, consultez [cette section](../../web/using/about-web-forms.md).

Vous pouvez intégrer un ou plusieurs contrôles de saisie dans vos rapports. Ce type de contrôle vous permet par exemple de filtrer les informations affichées en fonction d&#39;une valeur saisie.

![](assets/reporting_control_text.png)

Vous pouvez intégrer un ou plusieurs contrôles de sélection dans vos rapports. Ce type de contrôle vous permet de filtrer les informations contenues dans le rapport selon la ou les valeurs sélectionnées, par exemple :

* via des boutons radio ou des cases à cocher :

   ![](assets/reporting_radio_buttons.png)

* via une liste déroulante :

   ![](assets/reporting_control_list.png)

* via un calendrier :

   ![](assets/reporting_control_date.png)

Enfin, vous pouvez intégrer un ou plusieurs contrôles avancés dans vos rapports. Ce type de contrôle offre la possibilité d&#39;insérer un lien, une constante ou de sélectionner un dossier.

Ici, vous pouvez filtrer les données du rapport pour n&#39;afficher que celles d&#39;un des dossiers de l&#39;arborescence :

![](assets/reporting_control_folder.png)
