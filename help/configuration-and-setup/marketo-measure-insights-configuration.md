---
description: Configuration d’[!DNL Marketo Measure] Insights - [!DNL Marketo Measure]
title: Configuration des analyses [!DNL Marketo Measure]
exl-id: f6fe296b-d22a-43f2-b124-5d4b2f74d67a
feature: Reporting
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 4%

---

# Configuration des analyses [!DNL Marketo Measure] {#marketo-measure-insights-configuration}

L’application Zone de travail [!DNL Marketo Measure] Insights doit être ajoutée à la mise en page de la page de prospect, mais elle nécessite une configuration supplémentaire dans la section Applications connectées de votre configuration de [!DNL Salesforce]. Suivez ces instructions pour vous assurer que l’application Canvas dispose des autorisations appropriées.

1. Accédez à [!DNL Salesforce] Configuration et cliquez sur **[!UICONTROL Applications connectées]** sous l’onglet [!UICONTROL Gérer les applications].

1. Sélectionnez le [!DNL Marketo Measure Insights] dans la liste qui s’affiche.

1. Dans la section [!UICONTROL Politiques OAuth] , définissez le paramètre Utilisateurs autorisés sur « Les utilisateurs approuvés par l’administrateur sont préautorisés ». Un pop-up s’affiche, cliquez sur **[!UICONTROL OK]** puis **[!UICONTROL Enregistrer]**.

   ![1. Sous la section Politiques OAuth , modifiez le paramètre Utilisateurs autorisés &#x200B;](assets/marketo-app-1.png)

1. Une fois la page enregistrée, vous pouvez cliquer sur le bouton **[!UICONTROL Gérer les profils]**.

   ![1. Une fois la page enregistrée, vous pouvez cliquer sur l’icône &#x200B;](assets/marketo-app-2.png)

1. Sélectionnez tous les profils qui doivent avoir accès à [!DNL Marketo Measure] Insights et cliquez sur **[!UICONTROL Enregistrer]**.
