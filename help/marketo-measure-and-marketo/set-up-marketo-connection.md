---
description: Configurer La Connexion Marketo - [!DNL Marketo Measure]
title: Configurer la connexion Marketo
exl-id: 11660539-1cc5-4768-8f22-d6f7cd0b94f3
feature: Integration
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---


# Configurer la connexion Marketo {#set-up-marketo-connection}

Voici comment configurer votre connexion à Marketo.

>[!PREREQUISITES]
>
>[Créez un rôle Utilisateur API uniquement](https://experienceleague.adobe.com/docs/marketo/using/product-docs/administration/users-and-roles/create-an-api-only-user.html?lang=fr){target="_blank"} pour la connexion [!DNL Marketo Measure]/Marketo Engage.

1. Dans [!DNL Marketo Measure], cliquez sur la liste déroulante **[!UICONTROL Mon compte]** et sélectionnez **[!UICONTROL Paramètres]**.

   ![Menu déroulant Mon compte de Marketo Measure avec l’option Paramètres &#x200B;](assets/set-up-marketo-connection-1.png)

1. Sous [!UICONTROL Intégrations], cliquez sur **[!UICONTROL Connexions]**.

   ![Menu Intégrations avec l’option Connexions](assets/set-up-marketo-connection-2.png)

1. Cliquez sur **[!UICONTROL Configurer une nouvelle connexion CRM]**.

   ![Bouton Configurer une nouvelle connexion CRM](assets/set-up-marketo-connection-3.png)

1. Cliquez sur le bouton **[!UICONTROL Connexion]** en regard de Marketo.

   ![Bouton Se connecter en regard de l’option d’intégration de Marketo](assets/set-up-marketo-connection-4.png)

1. Dans un nouvel onglet, connectez-vous à votre compte Marketo Engage. Accédez à **Admin** > **Services web**. Faites défiler jusqu’à API REST. Mettez en surbrillance et enregistrez le point d’entrée et l’URL du service d’identités. Vous en avez besoin pour les étapes suivantes.

   ![Page des services web Marketo affichant les URL de point d’entrée de l’API REST et d’identité](assets/set-up-marketo-connection-5.png)

1. Toujours dans Marketo Engage, sélectionnez **LaunchPoint** dans l’arborescence de gauche. Recherchez le service personnalisé que vous souhaitez connecter à Marketo Measure et cliquez sur **Afficher les détails**.

   ![Menu LaunchPoint avec service personnalisé et option Afficher les détails](assets/set-up-marketo-connection-6.png)

1. Mettez en surbrillance et enregistrez l’ID client et le secret client. Cliquez sur **Fermer**.

   ![Détails du service LaunchPoint affichant l’ID client et le secret client](assets/set-up-marketo-connection-7.png)

1. De retour en [!DNL Marketo Measure], renseignez les champs avec les données que vous avez collectées.

   ![Formulaire de connexion Marketo avec champs de point d’entrée et d’informations d’identification](assets/set-up-marketo-connection-8.png)

1. Après avoir saisi les valeurs, cliquez sur **[!UICONTROL Authentifier]**. Votre compte Marketo Engage est connecté à [!DNL Marketo Measure].

   ![Message de confirmation de connexion Marketo réussie](assets/set-up-marketo-connection-9.png)

   >[!NOTE]
   >[!DNL Marketo Measure] effectue des appels à l’API Marketo en votre nom sans utiliser aucune de vos limites d’API Marketo. Vous n’avez donc pas à vous soucier des limites et de l’affectation de crédit avec d’autres intégrations.
