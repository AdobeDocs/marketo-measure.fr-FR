---
description: '[!DNL Marketo Measure] Intégrations avec Adobe Launch - [!DNL Marketo Measure]'
title: '[!DNL Marketo Measure] Intégrations avec Adobe Launch'
exl-id: 316ee8a8-b2d3-42e9-9ee5-c9b1d91c2769
feature: Integration
source-git-commit: 6aaf6fd26f19e9382cc559e54558e1c5d84cfd6d
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 2%

---

# Intégrations [!DNL Marketo Measure] avec Adobe Launch {#marketo-measure-integrations-with-adobe-launch}

L’extension Adobe Launch est conçue pour les utilisateurs [!DNL Marketo Measure] existants qui utilisent déjà Adobe Launch sur leur site web. L’extension sert de solution de gestion des balises que vous pouvez utiliser pour configurer et charger dynamiquement des scripts sur vos pages en fonction de certains événements et conditions.

Lorsqu’elle est installée et configurée dans Adobe Launch, l’extension [!DNL Marketo Measure] charge le script bizible.js sur les pages où se trouve le script Adobe Launch. Cela permet aux marketeurs d’ajouter bizible.js via la configuration Adobe Launch, plutôt que de modifier explicitement la page web pour ajouter la balise de script bizible.js.

## Configuration de l’extension Adobe Launch {#configure-the-adobe-launch-extension}

>[!PREREQUISITES]
>
>Consultez les liens suivants pour en savoir plus sur Adobe Launch et ses extensions :
>
>* [[!DNL Marketo Measure] Extension](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email/bizible.html?lang=fr#catalog){target="_blank"}
>* [Aperçu du lancement par Adobe](https://experienceleague.adobe.com/docs/platform-learn/implement-in-websites/overview.html?lang=fr){target="_blank"}
>* [Aperçu de l’extension Adobe Launch](https://experienceleague.adobe.com/docs/experience-platform/tags/extension-dev/overview.html?lang=fr){target="_blank"}

1. Créez une propriété suivant les étapes [de cet article](https://experienceleague.adobe.com/docs/platform-learn/implement-in-websites/configure-tags/create-a-property.html?lang=fr#go-to-the-data-collection-interface){target="_blank"}.

1. Cliquez sur la propriété que vous avez créée.

   ![](assets/marketo-measure-integrations-with-adobe-launch-1.png)

1. Cliquez sur **[!UICONTROL Extensions]**.

   ![](assets/marketo-measure-integrations-with-adobe-launch-2.png)

1. Cliquez sur l’onglet **[!UICONTROL Catalogue]** et recherchez &quot;[!UICONTROL Bizible]&quot;.

   ![](assets/marketo-measure-integrations-with-adobe-launch-3.png)

1. Dans la mosaïque [!UICONTROL Bizible Analytics], cliquez sur **[!UICONTROL Installer]**.

   ![](assets/marketo-measure-integrations-with-adobe-launch-4.png)

1. Dans le champ Bizible AccountId , saisissez l’URL de votre site web (par exemple, `adobe.com`).

   ![](assets/marketo-measure-integrations-with-adobe-launch-5.png)

1. Cliquez sur **[!UICONTROL Enregistrer]**.

   ![](assets/marketo-measure-integrations-with-adobe-launch-6.png)

1. Cliquez sur **[!UICONTROL Rules]**, puis sélectionnez **[!UICONTROL Create New Rule]**.

   ![](assets/marketo-measure-integrations-with-adobe-launch-7.png)

1. Cliquez sur le bouton **[!UICONTROL Ajouter]** sous [!UICONTROL Événements].

   ![](assets/marketo-measure-integrations-with-adobe-launch-8.png)

1. Dans la liste déroulante Extension , sélectionnez **[!UICONTROL Core]**. Ensuite, dans la liste déroulante Type d’événement , sélectionnez **[!UICONTROL Bibliothèque chargée (Haut de page)]**. Si vous ne donnez pas de nom à votre événement, un nom par défaut est appliqué. Cliquez sur **[!UICONTROL Conserver les modifications]** une fois terminé.

   ![](assets/marketo-measure-integrations-with-adobe-launch-9.png)

1. Cliquez sur le bouton **[!UICONTROL Ajouter]** sous Actions.

   ![](assets/marketo-measure-integrations-with-adobe-launch-10.png)

1. Dans la liste déroulante Extension , sélectionnez **[!UICONTROL Bizible Analytics]**. Ensuite, dans la liste déroulante Type d’action , sélectionnez **[!UICONTROL Initialize]**. Si vous ne donnez pas de nom à votre action, une valeur par défaut est appliquée. Cliquez sur **[!UICONTROL Conserver les modifications]** une fois terminé.

   ![](assets/marketo-measure-integrations-with-adobe-launch-11.png)

1. Cliquez sur **[!UICONTROL Enregistrer]**.

   ![](assets/marketo-measure-integrations-with-adobe-launch-12.png)

