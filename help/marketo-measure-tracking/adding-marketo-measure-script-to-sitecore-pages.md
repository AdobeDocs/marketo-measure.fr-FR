---
description: Ajout  [!DNL Marketo Measure]  script aux pages Sitecore - [!DNL Marketo Measure]
title: Ajout d’un script  [!DNL Marketo Measure]  à des pages Sitecore
exl-id: 87ce1857-7532-45a7-8c39-255c6118b50a
feature: Tracking
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 3%

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
