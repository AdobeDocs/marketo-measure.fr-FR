---
description: '[!DNL Marketo Measure] Intégrations avec Adobe Launch - [!DNL Marketo Measure]'
title: '''[!DNL Marketo Measure] Intégrations avec Adobe Launch »'
exl-id: 316ee8a8-b2d3-42e9-9ee5-c9b1d91c2769
feature: Integration
source-git-commit: 6aaf6fd26f19e9382cc559e54558e1c5d84cfd6d
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 2%

---

# Intégrations [!DNL Marketo Measure] avec Adobe Launch {#marketo-measure-integrations-with-adobe-launch}

L’extension Adobe Launch est conçue pour les [!DNL Marketo Measure] utilisateurs qui utilisent déjà Adobe Launch sur leur site web. L’extension sert de solution de gestion des balises que vous pouvez utiliser pour configurer et charger dynamiquement des scripts sur vos pages en fonction de certains événements et conditions.

Une fois installé et configuré dans Adobe Launch, le [!DNL Marketo Measure] L’extension charge le script bizible.js sur les pages où le script Adobe Launch est présent. Cela permet aux spécialistes du marketing d’ajouter Bizible.js par le biais de la configuration Adobe Launch, plutôt que de modifier explicitement la page web pour ajouter la balise de script Bizible.js.

## Configuration de l’extension Adobe Launch {#configure-the-adobe-launch-extension}

>[!PREREQUISITES]
>
>Consultez les liens ci-dessous pour en savoir plus sur Adobe Launch et ses extensions :
>
>* [[!DNL Marketo Measure] Extension](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email/bizible.html#catalog){target="_blank"}
>* [Présentation d’Adobe Launch](https://experienceleague.adobe.com/docs/platform-learn/implement-in-websites/overview.html){target="_blank"}
>* [Présentation de l’extension Adobe Launch](https://experienceleague.adobe.com/docs/experience-platform/tags/extension-dev/overview.html){target="_blank"}

1. Créez une propriété en suivant ces étapes [dans cet article](https://experienceleague.adobe.com/docs/platform-learn/implement-in-websites/configure-tags/create-a-property.html#go-to-the-data-collection-interface){target="_blank"}.

1. Cliquez sur la propriété que vous avez créée.

   ![](assets/marketo-measure-integrations-with-adobe-launch-1.png)

1. Clic **[!UICONTROL Extensions]**.

   ![](assets/marketo-measure-integrations-with-adobe-launch-2.png)

1. Cliquez sur le lien **[!UICONTROL Catalogue]** et recherchez «[!UICONTROL Bizible]. »

   ![](assets/marketo-measure-integrations-with-adobe-launch-3.png)

1. Dans le [!UICONTROL Analyses Bizible] vignette, cliquez sur **[!UICONTROL Installer]**.

   ![](assets/marketo-measure-integrations-with-adobe-launch-4.png)

1. Dans le champ ID de compte Bizible, saisissez l’URL de votre site Web (par exemple, `adobe.com`).

   ![](assets/marketo-measure-integrations-with-adobe-launch-5.png)

1. Cliquez sur **[!UICONTROL Enregistrer]**.

   ![](assets/marketo-measure-integrations-with-adobe-launch-6.png)

1. Clic **[!UICONTROL Règles]**, puis sélectionnez **[!UICONTROL Créer une règle]**.

   ![](assets/marketo-measure-integrations-with-adobe-launch-7.png)

1. Cliquez sur le lien **[!UICONTROL Ajouter]** bouton sous [!UICONTROL Événements].

   ![](assets/marketo-measure-integrations-with-adobe-launch-8.png)

1. Dans le menu déroulant Extension , sélectionnez **[!UICONTROL Core]**. Ensuite, dans le menu déroulant Type d’événement , sélectionnez **[!UICONTROL Bibliothèque chargée (haut de page)]**. Si vous ne donnez pas de nom à votre événement, un nom par défaut est appliqué. Clic **[!UICONTROL Conserver les modifications]** une fois cette opération terminée.

   ![](assets/marketo-measure-integrations-with-adobe-launch-9.png)

1. Cliquez sur le lien **[!UICONTROL Ajouter]** sous Actions.

   ![](assets/marketo-measure-integrations-with-adobe-launch-10.png)

1. Dans la liste déroulante Extension , sélectionnez **[!UICONTROL Analyses Bizible]**. Ensuite, dans la liste déroulante Type d’action , sélectionnez **[!UICONTROL Initialiser]**. Si vous ne donnez pas de nom à votre action, une action par défaut est appliquée. Clic **[!UICONTROL Conserver les modifications]** une fois cette opération terminée.

   ![](assets/marketo-measure-integrations-with-adobe-launch-11.png)

1. Cliquez sur **[!UICONTROL Enregistrer]**.

   ![](assets/marketo-measure-integrations-with-adobe-launch-12.png)

