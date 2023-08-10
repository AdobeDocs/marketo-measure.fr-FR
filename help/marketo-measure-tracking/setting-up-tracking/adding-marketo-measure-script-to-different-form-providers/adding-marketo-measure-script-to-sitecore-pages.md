---
unique-page-id: 18874747
description: Ajouter [!DNL Marketo Measure] Script pour les pages de magasin de sites - [!DNL Marketo Measure] - Documentation du produit
title: Ajout d’un script  [!DNL Marketo Measure]  à des pages Sitecore
exl-id: 87ce1857-7532-45a7-8c39-255c6118b50a
feature: Tracking
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 7%

---

# Ajout d’un script [!DNL Marketo Measure] à des pages Sitecore {#adding-marketo-measure-script-to-sitecore-pages}

Les systèmes de gestion de contenu peuvent nécessiter des étapes supplémentaires au-delà de l’implémentation de script standard pour [!DNL Marketo Measure] pour reconnaître les envois de formulaire. Le processus ci-dessous indique comment ajouter la variable [!DNL Marketo Measure] javascript pour votre [!DNL Sitecore] pages.

Pour les sites avec des pages Sitecore :

1. Connectez-vous à Sitecore et accédez à votre site web. Recherchez la variable [!UICONTROL Configuration] qui se trouve au même niveau que votre [!UICONTROL Accueil] item et [!UICONTROL Métadonnées] dossier.
1. Cliquez sur le bouton **[!UICONTROL +]** en regard de [!UICONTROL Configuration] dossier.
1. Cliquez sur le bouton **[!UICONTROL +]** en regard de [!UICONTROL Outils] dossier.
1. Sélectionnez la variable [!UICONTROL Javascript] élément .
1. Dans le [!UICONTROL Contenu] , cliquez sur l’onglet **[!UICONTROL Verrouillage et modification]** lien pour déverrouiller l’élément à modifier.
1. Recherchez le [!UICONTROL &quot;JavaScript&quot;] . Si ce n’est pas déjà fait, cliquez sur le bouton **[!UICONTROL +]**.
1. Saisissez notre script : `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js"async=""></script>`
1. Cliquez sur **[!UICONTROL Enregistrer]** dans le coin supérieur gauche.
