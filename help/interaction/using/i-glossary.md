---
product: campaign
title: Glossaire d’Interaction de Campaign
description: Glossaire d’Interaction de Campaign
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: interaction-overview
exl-id: 9e199b7c-9307-4797-bf86-7940388555bc
TQID: https://experienceleague.adobe.com/d6fevvmNur-4TC1KFM-09o68GnPFEM6S6SaFICwyCsw
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: b6fcaf36-3bc4-4604-94f3-81b5d3f41ecf
subfeature_v2: []
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 1128
ht-degree: 100%

---

# Glossaire d’Interaction de Campaign{#i-glossary}



Voici la définition des éléments principaux d&#39;Interaction.

* **Environnement** : ensemble comprenant un catalogue d’offres et des points d’extension (emplacements).Vous devez créer un environnement par dimension de ciblage.Il existe deux types d’environnements :

   * **Environnement en édition** : environnement dans lequel les offres sont créées et/ou les règles de typologie sont définies (règles qui déterminent les offres à présenter ou non à une personne ciblée). La table des individus qui seront ciblés par les offres et la table destinée à stocker toutes les propositions d&#39;offres y sont également définies. Le nœud **[!UICONTROL Environnement en édition]** contient des sous-dossiers d&#39;emplacements, des filtres prédéfinis et des catégories d&#39;offres. Pour chaque **[!UICONTROL Environnement en édition]**, il existe un **[!UICONTROL Environnement en ligne]** correspondant, généré à partir de ce même **[!UICONTROL Environnement en édition]**.
   * **Environnement en ligne** : environnement associé à un **[!UICONTROL Environnement en édition]**. Il contient des offres en lecture seule dont le contenu et l’éligibilité ont été approuvés via l’**[!UICONTROL Environnement en édition]**. Elles sont destinées à être sélectionnées pour être présentées sur un site web ou insérées dans un message.

* Un **emplacement** désigne un dossier définissant l’emplacement d’exposition de l’offre. La définition d&#39;un emplacement permet à la fois d&#39;indiquer le canal utilisé, de spécifier s&#39;il est possible ou non de l&#39;utiliser en mode unitaire (par défaut : uniquement en mode batch), de construire le contenu de l&#39;offre par l&#39;intermédiaire de fonctions de rendu et de spécifier le thème des offres présentées. Un emplacement est une interface entre le canal et le moteur d&#39;offres.

  >[!IMPORTANT]
  >
  >Un emplacement n’est pas un canal de communication, il correspond à un lieu d’exposition sur le canal.Par exemple, les offres exposées sur un site web peuvent occuper deux emplacements sur la même page.Dans ce cas, nous aurons alors deux espaces pour le même canal.
  >
  >Les emplacements doivent être définis dans le cahier des charges et ne doivent pas être modifiés en cours de projet.

* **Catalogue d’offres** : ensemble d’offres définies dans Adobe Campaign qui peuvent être sélectionnées lors d’une interaction.Le catalogue est organisé de manière hiérarchique avec chaque nœud correspondant à une catégorie.
* **Catégorie** : dossier lié au catalogue d’offres dans un environnement, qui organise les offres par nature, date d’éligibilité et thème d’application.Une catégorie peut contenir des sous-catégories qui héritent de toutes les caractéristiques de la catégorie parente.Des règles d’éligibilité peuvent être définies pour une catégorie, de manière à les partager avec plusieurs offres.
* **Thèmes d&#39;application** : mots-clés définis au niveau de la catégorie qui permettent de filtrer les offres au moment de leur présentation sur un canal sortant ou entrant en restreignant la sélection des offres à une ou plusieurs catégorie(s).

  >[!NOTE]
  >
  >Les catégories enfants héritent des thèmes définis au niveau de la catégorie parent.

* **Règles d’éligibilité** : contraintes appliquées à un environnement, une catégorie ou une offre, liées à la période de validité, à la cible et au poids.Elles vous permettent de vous assurer qu’une offre est en phase avec le contact ciblé.

  Au niveau des environnements, les règles d&#39;éligibilité comprennent les règles de présentation appliquées aux offres et les personnes à cibler.

  Dans les catégories, les règles d’éligibilité vous permettent de limiter la validité de la catégorie dans le temps, de définir des thèmes d’application et de déterminer les personnes à cibler.Elles peuvent également comporter un poids multiplicateur pour une période donnée.Ainsi, les opérateurs peuvent partager les règles relatives aux offres d’autres catégories et ainsi simplifier leur gestion.

  Au niveau des offres, les règles d&#39;éligibilité permettent de limiter la validité des offres dans le temps et de déterminer les personnes à cibler.

* **Arbitrage** : sélection des offres qui seront affichées dans un environnement (offres éligibles).Le principe de l’arbitrage permet de classer les offres par priorité en fonction des critères définis dans les catégories, les offres et les offres contextuelles.
* **Contact** : contact provenant d’une interaction entrante.Lors du traitement des appels au moteur, le contact est associé à une dimension de ciblage.Il existe deux types de contacts :

   * **[!UICONTROL Contact identifié]** : contact s’étant volontairement identifié sur le canal.Dans les interactions sortantes, le contact est systématiquement identifié.
   * **[!UICONTROL Contact anonyme]** : contact qui ne s’est pas volontairement inscrit sur le canal mais qui peut être identifié implicitement au moyen d’un cookie.Cette terminologie n’a lieu d’être que dans le cadre d’interactions entrantes.

     >[!NOTE]
     >
     >Les contacts anonymes non identifiés sont rattachés à la dimension de ciblage des visiteurs.

* **Interaction sortante** : appel vers le moteur dʼinteractions à partir dʼune liste de contacts (utilisée pour la diffusion dʼe-mails, de publipostage direct, etc.).Les mêmes règles et processus sont appliqués à chaque contact. Ce type d&#39;interaction est généralement traité en mode batch.
* **Interaction entrante** : interaction faisant suite à un appel entrant généré par l’action d’un contact sur le canal. Ce type d&#39;interaction est généralement traité en mode unitaire.
* **Mode Lot** : le mode Lot permet de sélectionner la meilleure offre pour un ensemble de contacts. Les règles d&#39;éligibilité/priorisation sont appliquées à tous les contacts de l&#39;ensemble. Ce mode est généralement utilisé pour les interactions sortantes.
* **Mode unitaire** : un seul contact est traité à la fois. Ce mode est généralement utilisé pour les interactions entrantes et les messages transactionnels.
* **Mode d&#39;identification** : il se réfère au statut d&#39;un contact.

   * **[!UICONTROL explicite]** : le contact est identifié, il s’est authentifié sur l’interface du canal.
   * **[!UICONTROL implicite]** : le contact a été identifié par un cookie (permanent ou de session).Ils peuvent être traités comme des contacts anonymes ou identifiés.
   * **[!UICONTROL anonyme]** : le contact n&#39;a pas pu être identifié.

* **Offre éligible** : offre répondant à des contraintes définies en amont pouvant être proposée de façon cohérente à une cible.
* **Règles de présentation** : règles de typologie référencées au niveau de l&#39;environnement d&#39;offres permettant d&#39;exclure certaines offres en tenant compte de l&#39;historique des propositions.
* **Poids** : formules vous permettant de calculer de manière précise la pertinence d’une offre, afin de sélectionner l’offre la plus pertinente.Les poids sont définis dans les offres. Les offres éligibles sont prises en compte dans l’ordre de poids décroissant.
* **Fonction de rendu** : fonction définie au niveau de l’emplacement afin de construire son rendu de l’offre en fonction des attributs définis dans l’offre.Il existe trois modes de fonction de rendu différents : HTML, XML et texte.
* **Proposition d’offre** : résultat de l’action qui consiste à présenter une ou plusieurs offres à un contact sur un emplacement donné (une bannière sur un site web, un e-mail ou un SMS, par exemple).Ce résultat est stocké dans la table des propositions d’offre.Il n’est cependant pas obligatoire d’enregistrer les propositions.
* **Simulation** : module permettant de tester la présentation d&#39;offres auprès des personnes à cibler avant de procéder à la véritable présentation.
* **Prévisualisation** : prévisualisation de l’offre telle qu’elle s’affiche dans son dossier.Elle est accessible à partir de la fenêtre des paramètres des offres ou du profil du contact.
* **Filtres prédéfinis** : règles de filtrage prédéfinies pouvant prendre en compte des paramètres d’offre (par exemple, un code d’offre).Ils peuvent être réutilisés après la création des offres.
* **Rendu de l’offre** : information utilisée par le canal pour afficher l’offre.La représentation de l’offre peut être construite à partir de la fonction de rendu de l’emplacement sur lequel l’offre est représentée ou saisie directement dans l’interface (par exemple, dans le bloc HTML). Une offre peut être représentée par emplacement.
* **Processus de basculement** : processus activé dans un environnement identifié, chargé de diriger l&#39;appel vers un environnement anonyme si le contact n&#39;a pas pu être identifié explicitement et/ou implicitement.
