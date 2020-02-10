---
title: Rendez-vous
seo-title: Rendez-vous
description: Rendez-vous
seo-description: null
page-status-flag: never-activated
uuid: 8234d6cd-0e9b-4187-9ddf-9e1f86aa1b9a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: 075206aa-ff7b-4fa8-a05d-14a29fb119ba
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Rendez-vous{#and-join}

Un rendez-vous ne déclenche sa transition sortante qu&#39;une fois toutes les transitions entrantes activées, donc quand toutes les activités précédentes sont terminées. Cela permet de s&#39;assurer que certaines activités sont bien terminées avant de continuer l&#39;exécution du workflow.

La population transmise en sortie de l&#39;activité est déterminée par le choix d&#39;un ensemble principal parmi les transitions entrantes dans l&#39;activité.

La transition sortante ne peut contenir que l&#39;une des populations des transitions entrantes. Si l&#39;activité n&#39;est pas paramétrée, la transition sortante contiendra aléatoirement l&#39;une des populations entrantes.
