---
unique-page-id: 18874769
description: Configuration d’[!DNL Marketo Measure] Insights - [!DNL Marketo Measure]
title: Configuration des analyses [!DNL Marketo Measure]
exl-id: f6fe296b-d22a-43f2-b124-5d4b2f74d67a
feature: Reporting
TQID: https://experienceleague.adobe.com/5i-eUsazdk6Ahr91VhW31gynWc42FF-TMOs-3PDIZs0
product_v2: id: e6fc4016-a972-4f36-8c30-a6a5f82ad0c8
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: 9ceb54139bfa9b6ce7c2c5fbb4e25e649f5708a3
workflow-type: tm+mt
source-wordcount: 116
ht-degree: 3%

---

# Configuration des analyses [!DNL Marketo Measure] {#marketo-measure-insights-configuration}

L’application Zone de travail [!DNL Marketo Measure] Insights doit être ajoutée à la mise en page de la page de prospect, mais elle nécessite une configuration supplémentaire dans la section Applications connectées de votre configuration de [!DNL Salesforce]. Suivez ces instructions pour vous assurer que l’application Canvas dispose des autorisations appropriées.

1. Accédez à [!DNL Salesforce] Configuration et cliquez sur **[!UICONTROL Applications connectées]** sous l’onglet [!UICONTROL Gérer les applications].

1. Sélectionnez le [!DNL Marketo Measure Insights] dans la liste qui s’affiche.

1. Dans la section [!UICONTROL Politiques OAuth] , définissez le paramètre Utilisateurs autorisés sur « Les utilisateurs approuvés par l’administrateur sont préautorisés ». Un pop-up s’affiche, cliquez sur **[!UICONTROL OK]** puis **[!UICONTROL Enregistrer]**.

   ![](assets/1-1.png)

1. Une fois la page enregistrée, vous pouvez cliquer sur le bouton **[!UICONTROL Gérer les profils]**.

   ![](assets/2-1.png)

1. Sélectionnez tous les profils qui doivent avoir accès à [!DNL Marketo Measure] Insights et cliquez sur **[!UICONTROL Enregistrer]**.
