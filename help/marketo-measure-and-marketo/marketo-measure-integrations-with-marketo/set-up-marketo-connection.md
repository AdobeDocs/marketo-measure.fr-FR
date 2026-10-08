---
unique-page-id: 42762762
description: Configuration De La Connexion Marketo - [!DNL Marketo Measure]
title: Configurer la connexion Marketo
exl-id: 11660539-1cc5-4768-8f22-d6f7cd0b94f3
feature: Integration
TQID: 'https://experienceleague.adobe.com/IQhZzu6iqS-5BdooPRA6-A8BoJtQ936NRFJHPGu3Xp4'
product_v2:
  - id: e6fc4016-a972-4f36-8c30-a6a5f82ad0c8
    internal-label: Marketo Measure
feature_v2:
  - id: c8f57308-7e33-4e41-a385-b55041c78939
    internal-label: Integrations
  - id: 7da342c5-06ee-5869-b3e8-b73d5bf75a9d
    internal-label: Integration
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
    internal-label: Reporting
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
source-git-commit: 940fee4abd0e09b6bf513b5e7526d3c242bd31c7
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%
---
# Configurer la connexion Marketo {#set-up-marketo-connection}

Voici comment configurer votre connexion à Marketo.

>[!PREREQUISITES]
>
>[Créez un rôle Utilisateur API uniquement](https://experienceleague.adobe.com/docs/marketo/using/product-docs/administration/users-and-roles/create-an-api-only-user.html?lang=fr){target="_blank"} pour la connexion [!DNL Marketo Measure]/Marketo Engage.

1. Dans [!DNL Marketo Measure], cliquez sur la liste déroulante **[!UICONTROL Mon compte]** et sélectionnez **[!UICONTROL Paramètres]**.

   ![](assets/set-up-marketo-connection-1.png)

1. Sous [!UICONTROL Intégrations], cliquez sur **[!UICONTROL Connexions]**.

   ![](assets/set-up-marketo-connection-2.png)

1. Cliquez sur **[!UICONTROL Configurer une nouvelle connexion CRM]**.

   ![](assets/set-up-marketo-connection-3.png)

1. Cliquez sur le bouton **[!UICONTROL Connexion]** en regard de Marketo.

   ![](assets/set-up-marketo-connection-4.png)

1. Dans un nouvel onglet, connectez-vous à votre compte Marketo Engage. Accédez à **Admin** > **Services web**. Faites défiler jusqu’à API REST. Mettez en surbrillance et enregistrez le point d’entrée et l’URL du service d’identités. Vous en avez besoin pour les étapes suivantes.

   ![](assets/set-up-marketo-connection-5.png)

1. Toujours dans Marketo Engage, sélectionnez **LaunchPoint** dans l’arborescence de gauche. Recherchez le service personnalisé que vous souhaitez connecter à Marketo Measure et cliquez sur **Afficher les détails**.

   ![](assets/set-up-marketo-connection-6.png)

1. Mettez en surbrillance et enregistrez l’ID client et le secret client. Cliquez sur **Fermer**.

   ![](assets/set-up-marketo-connection-7.png)

1. De retour en [!DNL Marketo Measure], renseignez les champs avec les données que vous avez collectées.

   ![](assets/set-up-marketo-connection-8.png)

1. Après avoir saisi les valeurs, cliquez sur **[!UICONTROL Authentifier]**. Votre compte Marketo Engage est connecté à [!DNL Marketo Measure].

   ![](assets/set-up-marketo-connection-9.png)

   >[!NOTE]
   >
   >[!DNL Marketo Measure] effectue des appels à l’API Marketo en votre nom sans utiliser aucune de vos limites d’API Marketo. Vous n’avez donc pas à vous soucier des limites et de l’affectation de crédit avec d’autres intégrations.
