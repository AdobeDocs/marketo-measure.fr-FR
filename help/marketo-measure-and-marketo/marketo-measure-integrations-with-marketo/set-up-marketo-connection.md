---
unique-page-id: 42762762
description: Configurer la connexion Marketo - [!DNL Marketo Measure]
title: Configuration de la connexion Marketo
exl-id: 11660539-1cc5-4768-8f22-d6f7cd0b94f3
feature: Integration
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 1%

---

# Configuration de la connexion Marketo {#set-up-marketo-connection}

Voici comment configurer votre connexion à Marketo.

>[!PREREQUISITES]
>
>[Créez un rôle d’utilisateur API uniquement](https://experienceleague.adobe.com/docs/marketo/using/product-docs/administration/users-and-roles/create-an-api-only-user.html) pour la connexion [!DNL Marketo Measure]/Marketo Engage.

1. Dans [!DNL Marketo Measure], cliquez sur la liste déroulante **[!UICONTROL Mon compte]** et sélectionnez **[!UICONTROL Paramètres]**.

   ![](assets/set-up-marketo-connection-1.png)

1. Sous [!UICONTROL Intégrations], cliquez sur **[!UICONTROL Connexions]**.

   ![](assets/set-up-marketo-connection-2.png)

1. Cliquez sur **[!UICONTROL Configurer une nouvelle connexion CRM]**.

   ![](assets/set-up-marketo-connection-3.png)

1. Cliquez sur le bouton **[!UICONTROL Se connecter]** en regard de Marketo.

   ![](assets/set-up-marketo-connection-4.png)

1. Dans un nouvel onglet, connectez-vous à votre compte de Marketo Engage. Allez à **Admin** > **Services web**. Faites défiler l’écran jusqu’à l’API REST. Mettez en surbrillance et enregistrez le point de terminaison et l’URL du service d’identité. Vous en avez besoin dans les étapes suivantes.

   ![](assets/set-up-marketo-connection-5.png)

1. Toujours en Marketo Engage, sélectionnez **LaunchPoint** dans l’arborescence de gauche. Recherchez le service personnalisé que vous souhaitez connecter à Marketo Measure et cliquez sur **Afficher les détails**.

   ![](assets/set-up-marketo-connection-6.png)

1. Mettez en surbrillance et enregistrez l’ID client et le secret client. Cliquez sur **Fermer**.

   ![](assets/set-up-marketo-connection-7.png)

1. De retour dans [!DNL Marketo Measure], renseignez les champs avec les données que vous avez collectées.

   ![](assets/set-up-marketo-connection-8.png)

1. Après avoir saisi les valeurs, cliquez sur **[!UICONTROL Authentifier]**. Votre compte de Marketo Engage est connecté à [!DNL Marketo Measure].

   ![](assets/set-up-marketo-connection-9.png)

   >[!NOTE]
   >
   >[!DNL Marketo Measure] appelle l’API Marketo en votre nom sans utiliser aucune de vos limites d’API Marketo. Il n’est donc pas nécessaire de vous soucier des limites et de l’attribution de crédit avec d’autres intégrations.
