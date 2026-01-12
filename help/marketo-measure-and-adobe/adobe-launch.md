---
description: Intégrations [!DNL Marketo Measure] à Adobe Launch -  [!DNL Marketo Measure]
title: Intégrations [!DNL Marketo Measure] avec Adobe Launch
exl-id: 316ee8a8-b2d3-42e9-9ee5-c9b1d91c2769
feature: Integration
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 3%

---


# Intégrations [!DNL Marketo Measure] avec Adobe Launch {#marketo-measure-integrations}

L’extension Adobe Launch est conçue pour les utilisateurs [!DNL Marketo Measure] qui utilisent déjà Adobe Launch sur leur site web. L’extension sert de solution de gestion des balises que vous pouvez utiliser pour configurer et charger dynamiquement des scripts sur vos pages en fonction de certains événements et conditions.

Une fois installée et configurée dans Adobe Launch, l’extension [!DNL Marketo Measure] charge le script Bizible.js sur les pages où le script Adobe Launch est présent. Cela permet aux professionnels du marketing d’ajouter Bizible.js par le biais de la configuration d’Adobe Launch, plutôt que de modifier explicitement la page web pour ajouter la balise de script Bizible.js.

## Configuration de l’extension Adobe Launch {#configure-the-adobe-launch-extension}

>[!PREREQUISITES]
>Consultez les liens suivants pour en savoir plus sur Adobe Launch et ses extensions :
> [[!DNL Marketo Measure] Extension ](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email/bizible.html#catalog){target="_blank"}
> [Présentation d’Adobe Launch](https://experienceleague.adobe.com/docs/platform-learn/implement-in-websites/overview.html?lang=fr){target="_blank"}
> [Présentation de l’extension Adobe Launch](https://experienceleague.adobe.com/docs/experience-platform/tags/extension-dev/overview.html){target="_blank"}

1. Créez une propriété en suivant les étapes [décrites dans cet article](https://experienceleague.adobe.com/docs/platform-learn/implement-in-websites/configure-tags/create-a-property.html#go-to-the-data-collection-interface){target="_blank"}.

1. Cliquez sur la propriété que vous avez créée.

   Écran de sélection des propriétés ![Adobe Launch affichant les propriétés disponibles](assets/marketo-measure-integrations-1.png)

1. Cliquez sur **[!UICONTROL Extensions]**.

   ![Onglet Extensions dans les paramètres de propriété Adobe Launch](assets/marketo-measure-integrations-2.png)

1. Cliquez sur l’onglet **[!UICONTROL Catalogue]** et recherchez « [!UICONTROL Bizible] ».

   ![Recherche dans le catalogue d’extensions présentant l’extension Bizible](assets/marketo-measure-integrations-3.png)

1. Dans le volet [!UICONTROL Analyses Bizible], cliquez sur **[!UICONTROL Installer]**.

   ![ Mosaïque d’extension Bizible Analytics avec bouton Installer ](assets/marketo-measure-integrations-4.png)

1. Dans le champ ID de compte Bizible, saisissez l’URL de votre site Web (par exemple, `adobe.com`).

   ![Configuration de l’extension Bizible avec le champ ID de compte](assets/marketo-measure-integrations-5.png)

1. Cliquez sur **[!UICONTROL Enregistrer]**

   ![Bouton Enregistrer pour la configuration de l’extension Bizible](assets/marketo-measure-integrations-6.png)

1. Cliquez sur **[!UICONTROL Règles]**, puis sélectionnez **[!UICONTROL Créer une règle]**.

   ![Onglet Règles avec le bouton Créer une règle](assets/marketo-measure-integrations-7.png)

1. Cliquez sur le bouton **[!UICONTROL Ajouter]** sous [!UICONTROL Événements].

   ![Bouton Ajouter dans la section Événements de la configuration des règles](assets/marketo-measure-integrations-8.png)

1. Dans la liste déroulante Extension , sélectionnez **[!UICONTROL Core]**. Ensuite, dans le menu déroulant Type d’événement , sélectionnez **[!UICONTROL Bibliothèque chargée (haut de page)]**. Si vous ne donnez pas de nom à votre événement, un nom par défaut est appliqué. Cliquez sur **[!UICONTROL Conserver les modifications]** lorsque vous avez terminé.

   ![ Boîte de dialogue de configuration d’événement avec l’extension Core et le type d’événement Library Loaded (Bibliothèque chargée)](assets/marketo-measure-integrations-9.png)

1. Cliquez sur le bouton **[!UICONTROL Ajouter]** sous Actions.

   ![Ajout d’un bouton dans la section Actions de la configuration des règles](assets/marketo-measure-integrations-10.png)

1. Dans le menu déroulant Extension , sélectionnez **[!UICONTROL Bizible Analytics]**. Ensuite, dans le menu déroulant Type d’action, sélectionnez **[!UICONTROL Initialiser]**. Si vous ne donnez pas de nom à votre action, une action par défaut est appliquée. Cliquez sur **[!UICONTROL Conserver les modifications]** lorsque vous avez terminé.

   ![Boîte de dialogue de configuration d’action avec l’extension Bizible Analytics et type d’action Initialiser](assets/marketo-measure-integrations-11.png)

1. Cliquez sur **[!UICONTROL Enregistrer]**

   ![Bouton Enregistrer pour la configuration des règles](assets/marketo-measure-integrations-12.png)

