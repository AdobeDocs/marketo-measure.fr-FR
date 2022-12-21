---
unique-page-id: 18874743
description: Connexion [!DNL Marketo Measure] pour Unbounce Script Manager - [!DNL Marketo Measure] - Documentation du produit
title: Connexion [!DNL Marketo Measure] pour annuler le rebond du gestionnaire de script
exl-id: c3212bc3-1d8f-4da5-bb2d-11ffd2fb4e98
source-git-commit: ae5b77744d523606ce6cfcf48d7e8d5049d5ccb7
workflow-type: tm+mt
source-wordcount: '124'
ht-degree: 0%

---

# Connexion [!DNL Marketo Measure] pour annuler le rebond du gestionnaire de script {#connecting-marketo-measure-to-unbounce-script-manager}

[!DNL Marketo Measure] s’intègre directement avec Unbounce, ce qui vous permet de suivre la source marketing numérique des conversions de vos landing pages directement dans [!DNL Salesforce]. Pour établir la connexion, il vous suffit d’ajouter la variable [!DNL Marketo Measure] à votre Gestionnaire de script de débounce. Voici comment.

1. Connectez-vous à [!DNL Unbounce] compte .
1. Cliquez sur **[!UICONTROL Paramètres]** > **[!UICONTROL Gestionnaire de script]** > **[!UICONTROL Ajouter un script]**.
1. Dans la fenêtre contextuelle, sélectionnez [!UICONTROL Script personnalisé] et nommez-le &quot;[!DNL Marketo Measure Marketing Analytics].&quot; Cliquez sur **[!UICONTROL Ajout de détails de script]**.
1. Sélectionnez l’emplacement dans l’en-tête. Incluez le script sur la page d’entrée principale et la boîte de dialogue de confirmation de formulaire. Collez le [!DNL Marketo Measure] script ci-dessous dans la boîte.

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

1. Cliquez sur **[!UICONTROL Enregistrer]**.

Le [!DNL Marketo Measure] l’intégration fonctionne sur les landing pages Unbounce tant qu’elles sont hébergées sur votre domaine (par exemple, landing.mysite.com) et non sur celles qui utilisent le domaine unbounce.com.
