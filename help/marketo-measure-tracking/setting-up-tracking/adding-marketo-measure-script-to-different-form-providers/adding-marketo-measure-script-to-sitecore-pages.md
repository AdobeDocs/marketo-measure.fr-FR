---
unique-page-id: 18874747
description: Ajout de [!DNL Marketo Measure] Script aux pages de magasin de sites - [!DNL Marketo Measure]
title: Ajout d’un script  [!DNL Marketo Measure]  à des pages Sitecore
exl-id: 87ce1857-7532-45a7-8c39-255c6118b50a
feature: Tracking
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 3%

---

# Ajout d’un script [!DNL Marketo Measure] aux pages de magasin de sites {#adding-marketo-measure-script-to-sitecore-pages}

Les systèmes de gestion de contenu peuvent nécessiter des étapes supplémentaires au-delà de l’implémentation de script standard pour [!DNL Marketo Measure] afin de reconnaître les envois de formulaire. Le processus ci-dessous explique comment ajouter le code JavaScript [!DNL Marketo Measure] à vos pages [!DNL Sitecore].

Pour les sites avec des pages Sitecore :

1. Connectez-vous à Sitecore et accédez à votre site web. Recherchez le dossier [!UICONTROL Configuration] situé au même niveau que votre élément [!UICONTROL Home] et le dossier [!UICONTROL Metadata] .
1. Cliquez sur **[!UICONTROL +]** en regard du dossier [!UICONTROL Configuration] .
1. Cliquez sur **[!UICONTROL +]** en regard du dossier [!UICONTROL Tools].
1. Sélectionnez l’élément [!UICONTROL Javascript] .
1. Dans l’onglet [!UICONTROL Contenu] , cliquez sur le lien **[!UICONTROL Verrouiller et modifier]** pour déverrouiller l’élément à modifier.
1. Recherchez la section [!UICONTROL &#39;JavaScript&#39;] . S’il n’est pas déjà développé, cliquez sur **[!UICONTROL +]**.
1. Entrez notre script : `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js"async=""></script>`
1. Cliquez sur **[!UICONTROL Enregistrer]** dans le coin supérieur gauche.
