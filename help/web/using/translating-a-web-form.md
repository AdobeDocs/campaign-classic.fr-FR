---
title: Traduire un formulaire web
seo-title: Traduire un formulaire web
description: Traduire un formulaire web
seo-description: null
page-status-flag: never-activated
uuid: 3de2b021-ce1e-4597-8099-7fbef3279170
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-forms
discoiquuid: 145c26cc-c868-4b7b-904d-6af577fbcb83
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Traduire un formulaire web{#translating-a-web-form}

Il est possible de localiser une seule application Web dans plusieurs langues.

Vous pouvez effectuer des traductions directement dans la console Adobe Campaign (voir [Gérer les traductions dans l&#39;éditeur](#managing-translations-in-the-editor)) ou exporter et importer des chaînes pour externaliser la traduction (voir [Externaliser les traductions](#externalizing-translation)).

La liste des langues de traduction disponibles par défaut est présentée dans la section [Changer la langue d&#39;affichage des formulaires](#changing-forms-display-language).

L&#39;application web est construite dans une langue d&#39;édition : c&#39;est la langue de référence dans laquelle sont saisis les libellés et autres contenus de la page qui feront ensuite l&#39;objet d&#39;une traduction.

La langue par défaut est la langue dans laquelle sera affichée l&#39;application web si aucun paramètre de langue n&#39;est ajouté dans son URL d&#39;accès.

>[!NOTE]
>
>Par défaut, la langue d&#39;édition et la langue par défaut correspondent toutes les deux à celle de la console.

## Choisir les langues de traduction {#choosing-languages}

Pour définir une ou plusieurs langues de traduction, cliquez sur le **[!UICONTROL Properties]** bouton de l&#39;application Web, puis sur l&#39; **[!UICONTROL Localization]** onglet. Cliquez sur le **[!UICONTROL Add]** bouton pour définir une nouvelle langue de traduction pour l&#39;application Web.

>[!NOTE]
>
>Cet écran vous permet également de modifier la langue par défaut et la langue d&#39;édition.

![](assets/s_ncs_admin_survey_add_lang.png)

When you add translation languages for a Web application (or when the default language and the editing language are different), a **[!UICONTROL Translation]** sub-tab is added to the **[!UICONTROL Edit]** tab to manage translations.

Adobe Campaign intègre un outil de traduction et de suivi des traductions multilingues. Cet éditeur permet de visualiser les termes à traduire ou à valider, de saisir les traductions directement dans l&#39;interface, ou d&#39;importer/exporter les chaînes de caractères afin d&#39;externaliser la traduction.

## Gérer les traductions dans l&#39;éditeur {#managing-translations-in-the-editor}

### Collecter les chaînes {#collecting-strings}

The **[!UICONTROL Translations]** tab lets you enter translations for the character strings that make up the Web application.

La première fois que vous ouvrez cet onglet, il ne contient aucune donnée. Cliquez sur le **[!UICONTROL Collect the strings to translate]** lien pour mettre à jour les chaînes dans l&#39;application Web.

Adobe Campaign collects labels of fields and strings defined in the **[!UICONTROL Texts]** tabs of all static elements: HTML blocks, Javascript, etc. Les éléments statiques sont présentés dans la section [Elements statiques dans un formulaire web](../../web/using/static-elements-in-a-web-form.md).

![](assets/s_ncs_admin_survey_trad_tab.png)

>[!CAUTION]
>
>Cette opération peut durer plusieurs minutes, selon le volume de données à traiter.
> 
>Si un message d&#39;avertissement apparaît vous informant que certaines traductions sont manquantes dans le dictionnaire système, reportez-vous à la section [Traduire les chaînes système](#translating-the-system-strings).

Chaque fois qu&#39;une chaîne est traduite, sa traduction est ajoutée dans le dictionnaire de traduction.

Lorsque le processus de collecte détecte qu’une traduction existe déjà, elle s’affiche dans la **[!UICONTROL Text]** colonne de la chaîne. L’état de la chaîne est activé **[!UICONTROL Translated]**.

For characters strings which have never been translated, the **[!UICONTROL Text]** field is empty and the status is **[!UICONTROL To translate]**.

### Filtrer les chaînes {#filtering-strings}

Par défaut, chaque langue de traduction de l&#39;application Web s&#39;affiche. Il existe deux filtres par défaut : langue et état. Cliquez sur le **[!UICONTROL Filters]** bouton, puis sur **[!UICONTROL By language or status]** pour afficher les listes déroulantes correspondantes. Vous pouvez également créer un filtre avancé. Voir à ce propos [cette page](../../platform/using/creating-filters.md#creating-an-advanced-filter).

![](assets/s_ncs_admin_survey_trad_tab_en.png)

Go to the **[!UICONTROL Language]** drop-down box to select the translation language.

Pour afficher uniquement les chaînes non traduites, sélectionnez **[!UICONTROL To translate]** dans la **[!UICONTROL Status]** liste déroulante. Vous pouvez également afficher uniquement les chaînes traduites ou approuvées.

### Traduire les chaînes {#translating-strings}

1. Pour traduire un terme, double-cliquez sur la ligne correspondante dans la liste des chaînes.

   ![](assets/s_ncs_admin_survey_trad_tab_add_term.png)

   La chaîne source apparaît dans la partie supérieure de la fenêtre.

1. Entrez sa traduction dans la section inférieure. Pour l’approuver, cochez l’ **[!UICONTROL Translation approved]** option.

   >[!NOTE]
   >
   >La validation d&#39;une traduction est optionnelle et donc non bloquante.

   Non-approved translations are displayed as **[!UICONTROL Translated]**. Approved translations are displayed as **[!UICONTROL Approved]**.

## Externaliser les traductions {#externalizing-translation}

Vous pouvez exporter et importer les chaînes de caractères afin de les traduire en utilisant un outil externe à Adobe Campaign.

>[!CAUTION]
>
>Lorsque vous exportez les chaînes, n&#39;effectuez plus aucune traduction via l&#39;éditeur intégré. Celles-ci seraient perdues au moment de l&#39;import en cas de conflit.

### Exporter les fichiers {#exporting-files}

1. Sélectionnez les applications Web dont vous voulez importer les chaînes, cliquez avec le bouton droit de la souris, puis sélectionnez **[!UICONTROL Actions > Export strings for translation...]**

   ![](assets/s_ncs_admin_survey_trad_export.png)

1. Select an **[!UICONTROL Export strategy]** :

   * **[!UICONTROL One file per language]**: l’exportation génère un fichier par langue de traduction. Chaque fichier sera commun à toutes les applications Web sélectionnées.
   * **[!UICONTROL One file per Web application]**: l&#39;exportation génère un fichier par application Web sélectionnée. Chaque fichier contiendra toutes les langues de traduction.

      >[!NOTE]
      >
      >Ce type d&#39;export n&#39;est pas disponible pour l&#39;export en XLIFF.

   * **[!UICONTROL One file per language and per Web application]**: l’exportation génère plusieurs fichiers. Chaque fichier contiendra une langue de traduction par application Web.
   * **[!UICONTROL One file for all]**: l&#39;exportation génère un fichier multilingue unique pour toutes les applications Web. Il contiendra toutes les langues de traduction pour toutes les applications Web sélectionnées.

      >[!NOTE]
      >
      >Ce type d&#39;export n&#39;est pas disponible pour l&#39;export en XLIFF.

1. Then chose the **[!UICONTROL Target folder]** where files will be recorded.
1. Select the file format ( **[!UICONTROL CSV]** or **[!UICONTROL XLIFF]** ) and click **[!UICONTROL Start]**.

![](assets/s_ncs_admin_survey_trad_export_start.png)

>[!NOTE]
>
>Les noms des fichiers d’exportation sont générés automatiquement. Si vous effectuez plusieurs fois la même exportation, vous remplacerez les fichiers existants par les nouveaux fichiers. Si vous devez conserver les fichiers précédents, modifiez le **[!UICONTROL Target folder]** , puis cliquez **[!UICONTROL Start]** de nouveau pour exécuter l’exportation.

Lorsque vous exportez des fichiers au **format CSV**, chaque langue est associée à un état et à un état de validation. La colonne **Valider ?** vous permet de valider une traduction. Cette colonne peut contenir les valeurs **Oui** ou **Non**. Comme dans l&#39;éditeur intégré (voir [Gérer les traductions dans l&#39;éditeur](#managing-translations-in-the-editor)), la validation d&#39;une traduction est optionnelle donc non bloquante.

### Importer les fichiers {#importing-files}

Un fois la traduction externe terminée, vous pouvez importer les fichiers traduits.

1. Accédez à la liste des applications Web, cliquez avec le bouton droit de la souris, puis sélectionnez **[!UICONTROL Actions > Import translated strings...]**

   >[!NOTE]
   >
   >Il n&#39;est pas nécessaire de sélectionner les applications web concernées par la traduction. Vous pouvez vous positionner sur n&#39;importe quelle ligne dans la liste des applications web.

   ![](assets/s_ncs_admin_survey_trad_import.png)

1. Select the file to import, then click **[!UICONTROL Upload]**.

   ![](assets/s_ncs_admin_survey_trad_import_start.png)

>[!NOTE]
>
>Une traduction externe a toujours la priorité sur une traduction interne. En cas de conflit, la traduction interne sera donc remplacée par la traduction externe.

## Changer la langue d&#39;affichage des formulaires {#changing-forms-display-language}

Les formulaires Web sont affichés dans la langue par défaut spécifiée dans l&#39; **[!UICONTROL Localization]** onglet des propriétés de l&#39;application Web. Pour changer de langue, vous devez ajouter les caractères suivants à la fin de l’URL (où **xx** est le symbole de la langue) :

```
?lang=xx
```

si la langue est le premier ou le seul paramètre de l&#39;URL. Par exemple : **https://myserver/webApp/APP34?lang=en**

```
&lang=xx
```

lorsque d&#39;autres paramètres précèdent celui de la langue dans l&#39;URL. Par exemple : **https://myserver/webApp/APP34?status=1&amp;lang=en**

Les langues de traduction et les dictionnaires disponibles par défaut sont répertoriés ci-dessous.

**Dictionnaire système par défaut** : certaines langues incluent par défaut un dictionnaire contenant la traduction des chaînes système. Voir à ce sujet la section [Traduire les chaînes système](#translating-the-system-strings).

**Gestion des calendriers** : les pages d&#39;une application web peuvent intégrer un calendrier permettant de saisir une date. Par défaut, ce calendrier est adapté dans plusieurs langues (traduction des noms de jours, format de la date).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Langue (symboles)</strong><br /> </td> 
   <td> <strong>Dictionnaire système par défaut</strong><br /> </td> 
   <td> <strong>Gestion des calendriers</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Allemand (de)<br /> </td> 
   <td> oui<br /> </td> 
   <td> oui<br /> </td> 
  </tr> 
  <tr> 
   <td> Anglais (en)<br /> </td> 
   <td> oui<br /> </td> 
   <td> oui<br /> </td> 
  </tr> 
  <tr> 
   <td> Anglais (Etats-Unis) (en_US)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Anglais (Royaume-Uni) (en_GB)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Arabe (ar)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Chinois (zh)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Coréen (ko)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Danois (da)<br /> </td> 
   <td> oui<br /> </td> 
   <td> oui<br /> </td> 
  </tr> 
  <tr> 
   <td> Espagnol (es)<br /> </td> 
   <td> oui<br /> </td> 
   <td> oui<br /> </td> 
  </tr> 
  <tr> 
   <td> Estonien (et)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Finnois (fi)<br /> </td> 
   <td> </td> 
   <td> oui<br /> </td> 
  </tr> 
  <tr> 
   <td> Français (fr)<br /> </td> 
   <td> oui<br /> </td> 
   <td> oui<br /> </td> 
  </tr> 
  <tr> 
   <td> Français (Belgique) (fr_BE)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Français (France) (fr_FR)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Grec (el)<br /> </td> 
   <td> </td> 
   <td> oui<br /> </td> 
  </tr> 
  <tr> 
   <td> Hébreu (he)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Hongrois (hu)<br /> </td> 
   <td> </td> 
   <td> oui<br /> </td> 
  </tr> 
  <tr> 
   <td> Indonésien (id)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Irlandais (ga)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Italien (it)<br /> </td> 
   <td> oui<br /> </td> 
   <td> oui<br /> </td> 
  </tr> 
  <tr> 
   <td> Italien (Italie) (it_IT)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Italien (Suisse) (it_CH)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Japonais (ja)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Letton (lv)<br /> </td> 
   <td> </td> 
   <td> oui<br /> </td> 
  </tr> 
  <tr> 
   <td> Lituanien (lt)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Maltais (mt)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Néerlandais (nl)<br /> </td> 
   <td> </td> 
   <td> oui<br /> </td> 
  </tr> 
  <tr> 
   <td> Néerlandais (Belgique) (nl_BE)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Néerlandais (Pays-Bas) (nl_NL)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Norvégien (Norvège) (no_NO)<br /> </td> 
   <td> </td> 
   <td> oui<br /> </td> 
  </tr> 
  <tr> 
   <td> Polonais (pl)<br /> </td> 
   <td> </td> 
   <td> oui<br /> </td> 
  </tr> 
  <tr> 
   <td> Portugais (pt)<br /> </td> 
   <td> </td> 
   <td> oui<br /> </td> 
  </tr> 
  <tr> 
   <td> Portugais (Brésil) (pt_BR)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Portugais (Portugal) (pt_PT)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Russe (ru)<br /> </td> 
   <td> </td> 
   <td> oui<br /> </td> 
  </tr> 
  <tr> 
   <td> Slovène (sl)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Slovaque (sk)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Suédois (sv)<br /> </td> 
   <td> oui<br /> </td> 
   <td> oui<br /> </td> 
  </tr> 
  <tr> 
   <td> Suédois (Finlande) (sv_FI)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Suédois (Suède) (sv_SE)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Tchèque (cs)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Thaï (th)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Vietnamien (vi)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Wallon (wa)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Pour ajouter d&#39;autres langues que celles proposées par défaut, reportez-vous à la section [Ajouter une langue de traduction](#adding-a-translation-language)

## Exemple : afficher une application web dans plusieurs langues {#example--displaying-a-web-application-in-several-languages}

Le formulaire Web suivant est disponible en quatre langues : anglais, français, allemand et espagnol. Les chaînes de caractères ont toutes été traduites via l’ **[!UICONTROL Translation]** onglet du formulaire Web. La langue par défaut étant l&#39;anglais, lorsque l&#39;enquête est publiée, utilisez l&#39;URL standard pour l&#39;afficher en anglais.

![](assets/s_ncs_admin_survey_trad_sample_fr.png)

Ajoutez les caractères **?lang=en** à la fin de l&#39;URL pour l&#39;afficher en anglais.

>[!NOTE]
>
>La liste des symboles de chaque langue est présentée dans la section [Changer la langue d&#39;affichage des formulaires](#changing-forms-display-language).

![](assets/s_ncs_admin_survey_trad_sample_en.png)

Vous pouvez ajouter les caractères **?lang=es** ou **?lang=de** pour l&#39;afficher en espagnol ou en allemand.

>[!NOTE]
>
>Si d&#39;autres paramètres sont déjà utilisés pour cette application web, ajoutez les caractères **&amp;lang=**.\
>Par exemple : **https://myserver/webApp/APP34?status=1&amp;lang=en**

## Configuration avancée de traduction {#advanced-translation-configuration}

>[!CAUTION]
>
>Cette section est réservée à des utilisateurs experts uniquement.

### Traduire les chaînes système {#translating-the-system-strings}

Les chaînes système sont des chaînes de caractères prêtes à l’emploi utilisées par toutes les applications Web. Par exemple : **[!UICONTROL Next]** , **[!UICONTROL Previous]**, **[!UICONTROL Approve]** boutons, **[!UICONTROL Loading]** messages, etc. Par défaut, certaines langues contiennent un dictionnaire avec des traductions pour ces chaînes. La liste de ces langues est présentée dans la section [Changer la langue d&#39;affichage des formulaires](#changing-forms-display-language).

Si vous traduisez votre application web vers une langue dans laquelle le dictionnaire système n&#39;est pas traduit, un message d&#39;avertissement vous informera que certaines traductions sont manquantes.

![](assets/s_ncs_admin_survey_trad_error.png)

Pour ajouter une langue, procédez comme suit :

1. Accédez à l’arborescence Adobe Campaign et cliquez sur **[!UICONTROL Administration > Configuration > Global dictionary > System dictionary]** .
1. In the upper section of the window, select the system string to translate, then click **[!UICONTROL Add]** in the lower section.

   ![](assets/s_ncs_admin_survey_trad_system_translation.png)

1. Sélectionnez la langue de traduction et saisissez une traduction pour la chaîne. Vous pouvez approuver la traduction en cochant l’ **[!UICONTROL Translation validated]** option.

   ![](assets/s_ncs_admin_survey_trad_system_translation2.png)

   >[!NOTE]
   >
   >La validation d&#39;une traduction est optionnelle et donc non bloquante.

>[!CAUTION]
>
>Ne supprimez pas les chaînes système d&#39;usine.

### Ajouter une langue de traduction {#adding-a-translation-language}

Pour traduire vos applications web dans d&#39;autres langues que celles proposées par défaut (voir [Changer la langue d&#39;affichage des formulaires](#changing-forms-display-language)), vous devez ajouter une nouvelle langue de traduction.

1. Cliquez sur le **[!UICONTROL Administration > Platform > Itemized lists]** noeud de l’arborescence Adobe Campaign et sélectionnez **[!UICONTROL Languages available for translation]** dans la liste. La liste des traductions disponibles s’affiche dans la section inférieure de la fenêtre.

   ![](assets/s_ncs_admin_survey_trad_new_itemized_list_1.png)

1. Cliquez sur le **[!UICONTROL Add]** bouton, puis saisissez l’ **[!UICONTROL Internal name]****[!UICONTROL Label]** identifiant et l’identifiant de l’image (indicateur). Pour ajouter une nouvelle image, contactez votre administrateur.

   ![](assets/s_ncs_admin_survey_trad_new_itemized_list_2.png)

