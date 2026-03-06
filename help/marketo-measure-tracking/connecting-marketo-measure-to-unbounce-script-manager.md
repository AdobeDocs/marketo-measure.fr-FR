---
description: Conseils sur la connexion  [!DNL Marketo Measure]  gestionnaire de scripts Unbounce pour les utilisateurs de Marketo Measure
title: Connexion de  [!DNL Marketo Measure]  au gestionnaire de script Unbounce
exl-id: c3212bc3-1d8f-4da5-bb2d-11ffd2fb4e98
feature: Tracking
source-git-commit: 7a4661c8d42214d32e5360dc45d6d880b08ef37c
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 6%

---


# Connexion de [!DNL Marketo Measure] au gestionnaire de scripts Unbounce {#connecting-marketo-measure-to-unbounce-script-manager}

[!DNL Marketo Measure] s’intègre directement à Unbounce, ce qui vous permet de suivre la source de marketing numérique de vos conversions de pages de destination directement dans [!DNL Salesforce]. Pour établir la connexion, ajoutez simplement le script [!DNL Marketo Measure] à votre gestionnaire de scripts Unbounce. Voici comment faire.

1. Connectez-vous à votre compte [!DNL Unbounce].
1. Cliquez sur **[!UICONTROL Paramètres]** > **[!UICONTROL Gestionnaire de scripts]** > **[!UICONTROL Ajouter un script]**.
1. Dans la fenêtre contextuelle, sélectionnez [!UICONTROL Script personnalisé] et nommez-le « [!DNL Marketo Measure Marketing Analytics] ». Cliquez sur **[!UICONTROL Ajouter des détails de script]**.
1. Sélectionnez l’emplacement dans la tête. Inclure le script sur la page de destination principale et la boîte de dialogue de confirmation de formulaire. Collez le script [!DNL Marketo Measure] ci-dessous dans la zone .

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

1. Cliquez sur **[!UICONTROL Enregistrer]**

L’intégration [!DNL Marketo Measure] fonctionne sur les pages de destination Unbounce tant qu’elles sont hébergées sur votre domaine (par exemple, landing.mysite.com) et non sur celles qui utilisent le domaine unbounce.com.
