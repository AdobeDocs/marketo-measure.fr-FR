---
unique-page-id: 18874769
description: "[!DNL Marketo Measure] Configuration des statistiques - [!DNL Marketo Measure] - Documentation du produit"
title: "[!DNL Marketo Measure] Configuration des statistiques"
exl-id: f6fe296b-d22a-43f2-b124-5d4b2f74d67a
source-git-commit: b910e5aedb9e178058f7af9a6907a1039458ce7a
workflow-type: tm+mt
source-wordcount: '117'
ht-degree: 0%

---

# [!DNL Marketo Measure] Configuration des statistiques {#marketo-measure-insights-configuration}

Le [!DNL Marketo Measure] L’application du canevas de statistiques doit être ajoutée à la mise en page de la page de piste, mais elle nécessite une configuration supplémentaire dans la section Applications connectées de votre [!DNL Salesforce] Configuration. Suivez ces instructions pour vous assurer que l’application Canvas dispose des autorisations appropriées.

1. Accédez à [!DNL Salesforce] Configurez et cliquez sur **[!UICONTROL Applications connectées]** sous le [!UICONTROL Gestion des applications] .

1. Sélectionnez la [!DNL Marketo Measure Insights] de la liste qui s’affiche.

1. Sous , [!UICONTROL OAuth] Stratégies , remplacez le paramètre Utilisateurs autorisés par &quot;Admin les utilisateurs approuvés sont préautorisés&quot;. Une fenêtre contextuelle s’affiche, cliquez sur **[!UICONTROL OK]** puis **[!UICONTROL Enregistrer]**.

   ![](assets/1-1.png)

1. Une fois la page enregistrée, vous pouvez cliquer sur le bouton **[!UICONTROL Gestion des profils]** bouton .

   ![](assets/2-1.png)

1. Sélectionnez tous les profils auxquels vous devez avoir accès. [!DNL Marketo Measure] Statistiques et clic **[!UICONTROL Enregistrer]**.
