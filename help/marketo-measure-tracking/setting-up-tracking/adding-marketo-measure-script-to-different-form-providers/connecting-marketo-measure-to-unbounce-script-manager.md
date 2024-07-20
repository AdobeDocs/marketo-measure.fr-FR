---
unique-page-id: 18874743
description: Connexion de  [!DNL Marketo Measure]  au gestionnaire de script de débounce - [!DNL Marketo Measure]
title: Connexion de  [!DNL Marketo Measure]  au gestionnaire de script Unbounce
exl-id: c3212bc3-1d8f-4da5-bb2d-11ffd2fb4e98
feature: Tracking
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 5%

---

# Connexion de [!DNL Marketo Measure] à Unbounce Script Manager {#connecting-marketo-measure-to-unbounce-script-manager}

[!DNL Marketo Measure] s’intègre directement avec Unbounce, ce qui vous permet de suivre la source de marketing numérique des conversions de vos landing pages directement dans [!DNL Salesforce]. Pour établir la connexion, ajoutez simplement le script [!DNL Marketo Measure] à votre Gestionnaire de script de débounce. Voici comment.

1. Connectez-vous à votre compte [!DNL Unbounce].
1. Cliquez sur **[!UICONTROL Settings]** > **[!UICONTROL Script Manager]** > **[!UICONTROL Add Script]**.
1. Dans la fenêtre contextuelle, sélectionnez [!UICONTROL Script personnalisé] et nommez-le &quot;[!DNL Marketo Measure Marketing Analytics]&quot;. Cliquez sur **[!UICONTROL Ajouter des détails de script]**.
1. Sélectionnez l’emplacement dans l’en-tête. Incluez le script sur la page d’entrée principale et la boîte de dialogue de confirmation de formulaire. Collez le script [!DNL Marketo Measure] ci-dessous dans la zone.

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

1. Cliquez sur **[!UICONTROL Enregistrer]**.

L&#39;intégration [!DNL Marketo Measure] fonctionne sur les landing pages Unbounce tant qu&#39;elles sont hébergées sur votre domaine (par exemple, landing.mysite.com) et non sur celles qui utilisent le domaine unbounce.com.
