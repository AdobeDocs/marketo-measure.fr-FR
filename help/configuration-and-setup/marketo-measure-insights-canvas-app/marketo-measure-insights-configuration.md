---
unique-page-id: 18874769
description: "[!DNL Marketo Measure] Insights Configuration - [!DNL Marketo Measure]"
title: "[!DNL Marketo Measure] Insights Configuration"
exl-id: f6fe296b-d22a-43f2-b124-5d4b2f74d67a
feature: Reporting
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '114'
ht-degree: 1%

---

# Configuration des analyses [!DNL Marketo Measure] {#marketo-measure-insights-configuration}

L’application de canevas de statistiques [!DNL Marketo Measure] doit être ajoutée à la mise en page de la page de piste, mais elle nécessite une configuration supplémentaire dans la section Applications connectées de votre configuration [!DNL Salesforce]. Suivez ces instructions pour vous assurer que l’application Canvas dispose des autorisations appropriées.

1. Accédez à [!DNL Salesforce] Configuration et cliquez sur **[!UICONTROL Applications connectées]** sous l’onglet [!UICONTROL Gérer les applications].

1. Sélectionnez le [!DNL Marketo Measure Insights] dans la liste qui s&#39;affiche.

1. Dans la section des stratégies [!UICONTROL OAuth] , remplacez le paramètre Utilisateurs autorisés par &quot;Admin les utilisateurs approuvés sont préautorisés&quot;. Une fenêtre contextuelle s’affiche, cliquez sur **[!UICONTROL OK]**, puis sur **[!UICONTROL Enregistrer]**.

   ![](assets/1-1.png)

1. Une fois la page enregistrée, vous pouvez cliquer sur le bouton **[!UICONTROL Gérer les profils]** .

   ![](assets/2-1.png)

1. Sélectionnez tous les profils qui doivent avoir accès à [!DNL Marketo Measure] Insights et cliquez sur **[!UICONTROL Enregistrer]**.
