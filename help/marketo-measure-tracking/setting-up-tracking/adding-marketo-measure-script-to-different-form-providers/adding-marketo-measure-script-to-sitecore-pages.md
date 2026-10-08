---
unique-page-id: 18874747
description: Ajout d’[!DNL Marketo Measure] script aux pages Sitecore - [!DNL Marketo Measure]
title: Ajout d’un script [!DNL Marketo Measure] aux pages Sitecore
exl-id: 87ce1857-7532-45a7-8c39-255c6118b50a
feature: Tracking
TQID: 'https://experienceleague.adobe.com/sXO-rCY3NbxX0AztYt-o3f-tpJFlrncLIb7-NvEjZO0'
product_v2:
  - id: e6fc4016-a972-4f36-8c30-a6a5f82ad0c8
    internal-label: Marketo Measure
feature_v2:
  - id: dcbeff6e-0253-5a4b-9ac2-1b67cc4a6286
    internal-label: Tracking
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
    internal-label: Metadata
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
source-git-commit: 940fee4abd0e09b6bf513b5e7526d3c242bd31c7
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%
---
# Ajout d’un script [!DNL Marketo Measure] aux pages Sitecore {#adding-marketo-measure-script-to-sitecore-pages}

Les systèmes de gestion de contenu peuvent nécessiter des étapes supplémentaires en plus de l’implémentation de script standard pour que les [!DNL Marketo Measure] puissent reconnaître les envois de formulaire. Le processus ci-dessous décrit comment ajouter le javascript [!DNL Marketo Measure] à vos pages [!DNL Sitecore].

Pour les sites comportant des pages Sitecore :

1. Connectez-vous à Sitecore et accédez à votre site web. Recherchez le dossier [!UICONTROL Configuration] qui réside au même niveau que votre élément [!UICONTROL Accueil] et votre dossier [!UICONTROL Métadonnées].
1. Cliquez sur le signe **[!UICONTROL +]** en regard du dossier [!UICONTROL Configuration].
1. Cliquez sur le signe **[!UICONTROL +]** en regard du dossier [!UICONTROL Outils].
1. Sélectionnez l’élément [!UICONTROL Javascript].
1. Dans l’onglet [!UICONTROL Contenu], cliquez sur le lien **[!UICONTROL Verrouiller et modifier]** pour déverrouiller l’élément à modifier.
1. Recherchez la section [!UICONTROL &#39;JavaScript&#39;]. S’il n’est pas déjà développé, cliquez sur le **[!UICONTROL +]**.
1. Entrez notre script : `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js"async=""></script>`
1. Cliquez sur **[!UICONTROL Enregistrer]** dans le coin supérieur gauche.
