---
description: '[!DNL Marketo Measure] Intégrations à Adobe Launch - [!DNL Marketo Measure]'
title: '''[!DNL Marketo Measure] Intégrations à Adobe Launch'
exl-id: 316ee8a8-b2d3-42e9-9ee5-c9b1d91c2769
feature: Integration
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 2%

---

# Intégrations [!DNL Marketo Measure] avec Adobe Launch {#marketo-measure-integrations-with-adobe-launch}

L’extension Adobe Launch est conçue pour les [!DNL Marketo Measure] utilisateurs qui utilisent déjà Adobe Launch sur leur site web. L’extension sert de solution de gestion des balises que vous pouvez utiliser pour configurer et charger dynamiquement des scripts sur vos pages en fonction de certains événements et conditions.

Une fois installé et configuré dans Adobe Launch, la variable [!DNL Marketo Measure] l’extension charge le script bizible.js sur les pages où se trouve le script Adobe Launch. Cela permet aux marketeurs d’ajouter bizible.js via la configuration Adobe Launch, plutôt que de modifier explicitement la page web pour ajouter la balise de script bizible.js.

## Configuration de l’extension Adobe Launch {#configure-the-adobe-launch-extension}

>[!PREREQUISITES]
>
>Consultez les liens suivants pour en savoir plus sur Adobe Launch et ses extensions :
>
>* [[!DNL Marketo Measure] Extension](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email/bizible.html#catalog){target="_blank"}
>* [Présentation d’Adobe Launch](https://experienceleague.adobe.com/docs/platform-learn/implement-in-websites/overview.html){target="_blank"}
>* [Présentation de l’extension Adobe Launch](https://experienceleague.adobe.com/docs/experience-platform/tags/extension-dev/overview.html){target="_blank"}

1. Créez une propriété en suivant les étapes [dans cet article](https://experienceleague.adobe.com/docs/platform-learn/implement-in-websites/configure-tags/create-a-property.html#go-to-the-data-collection-interface){target="_blank"}.

1. Cliquez sur la propriété que vous avez créée.

   ![](assets/marketo-measure-integrations-with-adobe-launch-1.png)

1. Cliquez sur **[!UICONTROL Extensions]**.

   ![](assets/marketo-measure-integrations-with-adobe-launch-2.png)

1. Cliquez sur le bouton **[!UICONTROL Catalogue]** et recherchez &quot;[!UICONTROL Bizible].&quot;

   ![](assets/marketo-measure-integrations-with-adobe-launch-3.png)

1. Dans le [!UICONTROL Bizible Analytics] mosaïque, cliquez **[!UICONTROL Installer]**.

   ![](assets/marketo-measure-integrations-with-adobe-launch-4.png)

1. Dans le champ Bizible AccountId , saisissez l’URL de votre site web (par exemple : `adobe.com`).

   ![](assets/marketo-measure-integrations-with-adobe-launch-5.png)

   >[!NOTE]
   >
   >Ce champ n’est pas l’&quot;ID de compte&quot; dans la table Business_Prod.Business . Toutes les activités web à partir de l’URL donnée (par exemple, `adobe.com`) sont mappés à la variable [!DNL Marketo Measure] client.

1. Cliquez sur **[!UICONTROL Enregistrer]**.

   ![](assets/marketo-measure-integrations-with-adobe-launch-6.png)

1. Cliquez sur **[!UICONTROL Règles]**, puis sélectionnez **[!UICONTROL Créer une règle]**.

   ![](assets/marketo-measure-integrations-with-adobe-launch-7.png)

1. Cliquez sur le bouton **[!UICONTROL Ajouter]** bouton sous [!UICONTROL Événements].

   ![](assets/marketo-measure-integrations-with-adobe-launch-8.png)

1. Dans la liste déroulante Extension , sélectionnez **[!UICONTROL Core]**. Ensuite, dans la liste déroulante Type d’événement , sélectionnez **[!UICONTROL Bibliothèque chargée (Haut de page)]**. Si vous ne donnez pas de nom à votre événement, un nom par défaut est appliqué. Cliquez sur **[!UICONTROL Conserver les modifications]** une fois terminé.

   ![](assets/marketo-measure-integrations-with-adobe-launch-9.png)

1. Cliquez sur le bouton **[!UICONTROL Ajouter]** sous Actions.

   ![](assets/marketo-measure-integrations-with-adobe-launch-10.png)

1. Dans la liste déroulante Extension , sélectionnez **[!UICONTROL Bizible Analytics]**. Ensuite, dans la liste déroulante Type d’action , sélectionnez **[!UICONTROL Initialiser]**. Si vous ne donnez pas de nom à votre action, une valeur par défaut est appliquée. Cliquez sur **[!UICONTROL Conserver les modifications]** une fois terminé.

   ![](assets/marketo-measure-integrations-with-adobe-launch-11.png)

1. Cliquez sur **[!UICONTROL Enregistrer]**.

   ![](assets/marketo-measure-integrations-with-adobe-launch-12.png)
