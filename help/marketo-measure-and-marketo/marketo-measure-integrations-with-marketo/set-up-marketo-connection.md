---
unique-page-id: 42762762
description: Configuration de la connexion Marketo - [!DNL Marketo Measure]
title: Configuration de la connexion Marketo
exl-id: 11660539-1cc5-4768-8f22-d6f7cd0b94f3
feature: Integration
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 1%

---

# Configuration de la connexion Marketo {#set-up-marketo-connection}

Voici comment configurer votre connexion à Marketo.

>[!PREREQUISITES]
>
>[Création d’un rôle d’utilisateur API uniquement](https://experienceleague.adobe.com/docs/marketo/using/product-docs/administration/users-and-roles/create-an-api-only-user.html) pour le [!DNL Marketo Measure]/connexion du Marketo Engage.

1. Dans [!DNL Marketo Measure], cliquez sur le **[!UICONTROL Mon compte]** et sélectionnez **[!UICONTROL Paramètres]**.

   ![](assets/set-up-marketo-connection-1.png)

1. Sous [!UICONTROL Intégrations], cliquez sur **[!UICONTROL Connexions]**.

   ![](assets/set-up-marketo-connection-2.png)

1. Cliquez sur **[!UICONTROL Configurer une nouvelle connexion CRM]**.

   ![](assets/set-up-marketo-connection-3.png)

1. Cliquez sur le bouton **[!UICONTROL Connexion]** en regard de Marketo.

   ![](assets/set-up-marketo-connection-4.png)

1. Dans un nouvel onglet, connectez-vous à votre compte de Marketo Engage. Accédez à **Administration** > **Services web**. Faites défiler l’écran jusqu’à l’API REST. Mettez en surbrillance et enregistrez le point de terminaison et l’URL du service d’identité. vous en aurez besoin dans un peu.

   ![](assets/set-up-marketo-connection-5.png)

1. Toujours en Marketo Engage, sélectionnez **LaunchPoint** dans l&#39;arbre à gauche. Recherchez le service personnalisé auquel vous souhaitez vous connecter et cliquez sur **Afficher les détails**.

   ![](assets/set-up-marketo-connection-6.png)

1. Mettez en surbrillance et enregistrez l’ID client et le secret client. Cliquez sur **Fermer**.

   ![](assets/set-up-marketo-connection-7.png)

1. Retour à [!DNL Marketo Measure], renseignez les champs avec les données que vous venez de collecter.

   ![](assets/set-up-marketo-connection-8.png)

1. Après avoir saisi les valeurs, cliquez sur **[!UICONTROL Authentification]**. Votre compte de Marketo Engage sera alors connecté à [!DNL Marketo Measure].

   ![](assets/set-up-marketo-connection-9.png)

   >[!NOTE]
   >
   >[!DNL Marketo Measure] lancera des appels à l’API Marketo en votre nom sans utiliser aucune de vos limites d’API Marketo. Il n’est donc pas nécessaire de vous soucier des limites et de l’attribution de crédit avec d’autres intégrations.
