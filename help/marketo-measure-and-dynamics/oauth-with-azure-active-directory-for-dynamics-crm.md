---
description: OAuth avec [!DNL Azure Active Directory] pour Dynamics CRM - [!DNL Marketo Measure]
title: OAuth avec [!DNL Azure Active Directory] pour Dynamics CRM
exl-id: 0a2f6b29-541d-4965-a460-e6f19b934edb
feature: Microsoft Dynamics
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '894'
ht-degree: 0%

---


# OAuth avec [!DNL Azure Active Directory] pour Dynamics CRM {#oauth-with-azure-active-directory-for-dynamics-crm}

## Qui est affecté {#who-s-affected}

Cette configuration est destinée aux nouveaux clients [!DNL Marketo Measure] qui utilisent Dynamics CRM avec un compte [!DNL Azure Active Directory] (AAD) ou aux clients qui souhaitent migrer de leur nom d’utilisateur et mot de passe hérités vers [!DNL Azure Active Directory] avec OAuth.

>[!NOTE]
>Pour ces deux scénarios, AAD est configuré ici pour faciliter la connexion de votre instance Dynamics dans [!DNL Marketo Measure] en tant que fournisseur de données.

## Configurer une nouvelle application {#set-up-new-application}

1. Connectez-vous à votre [Portail Azure](https://portal.azure.com/#home).

1. Sélectionnez le client Azure AD en cliquant sur votre compte dans le coin supérieur droit de la page, puis cliquez sur la navigation Switch Directory et sélectionnez le client approprié. Ignorez cette étape si vous n’avez qu’un seul client Azure AD sous votre compte ou si vous avez déjà sélectionné le client Azure AD approprié.

   ![Menu déroulant de sélection de client Azure Portal](assets/setup-2.png)

1. Recherchez « [!DNL Azure Active Directory] » dans la barre de recherche et cliquez sur le nom à ouvrir.

   ![Résultats de la recherche dans le portail Azure affichant Azure Active Directory](assets/setup-3.png)

1. Cliquez sur **[!UICONTROL Enregistrements des applications]** dans le menu de gauche.

   ![Menu de navigation Azure Active Directory avec Enregistrements des applications](assets/setup-4.png)

1. Cliquez sur **[!UICONTROL Nouvel enregistrement]** dans la partie supérieure.

   ![Page Enregistrements des applications avec le bouton Nouvel enregistrement](assets/setup-5.png)

1. Suivez les invites et créez une application. Qu’il s’agisse d’une application web ou d’une application cliente publique (mobile et de bureau), peu importe. Si vous souhaitez des exemples spécifiques pour les applications web ou les applications clientes publiques, consultez les [démarrages rapides](https://learn.microsoft.com/en-us/azure/active-directory/develop/v2-overview).\
   a. Nom est le nom de l’application et décrit votre application aux utilisateurs finaux.\
   b. Sous Types de compte pris en charge, sélectionnez Comptes dans n’importe quel annuaire organisationnel et comptes Microsoft personnels.\
   c. Fournissez l’URI de redirection. Pour les applications web, il s’agit de l’URL de base de votre application à laquelle les utilisateurs peuvent se connecter. Par exemple : `http://localhost:12345`. Pour les clients publics (mobiles et de bureau), Azure AD l’utilise pour renvoyer les réponses de jeton. Saisissez une valeur spécifique à votre application. Par exemple : `http://MyFirstAADApp`.

1. Une fois l’enregistrement terminé, Azure AD attribue à votre application un identifiant client unique (l’identifiant de l’application). Cette valeur est nécessaire dans la section suivante. Copiez-la donc depuis la page de l&#39;application.

1. Pour trouver votre application sur le portail Azure, cliquez sur **[!UICONTROL Enregistrements des applications]**, puis sur **[!UICONTROL Toutes les applications]**. Ouvrez l’application nouvellement créée

1. Cliquez sur **[!UICONTROL Authentification]** dans le menu de gauche.

   ![Menu Application avec option Authentification mise en surbrillance](assets/setup-9.png)

1. Ajoutez les URL de redirection [!DNL Marketo Measure] : `https://apps.bizible.com/OAuth2` et `https://apps.bizible.com/OAuth2?identityOnly=true` à la liste des URL de redirection.

   ![Paramètres d’authentification affichant les URL de redirection Marketo Measure](assets/setup-10.png)

1. Accédez à l’onglet Autorisations d’API et assurez-vous que les autorisations appropriées sont attribuées à l’application.

   ![Onglet Autorisations d’API affichant les autorisations attribuées](assets/setup-10a.png)

1. À partir de là, saisissez « [!UICONTROL entreprise] » dans la zone de recherche, puis cliquez sur **[!UICONTROL Applications d’entreprise]**.

   ![Recherche sur le portail Azure affichant les applications d’entreprise](assets/setup-11.png)

1. Là encore, recherchez et ouvrez votre nouvelle application à partir de la liste des applications.

1. Dans l’onglet Autorisations , cliquez sur **[!UICONTROL Accorder le consentement administrateur pour (nom de l’instance)]**.

   ![&#x200B; Onglet Autorisations avec le bouton Accorder le consentement administrateur &#x200B;](assets/setup-13a.png)

1. Cliquez sur **[!UICONTROL Accepter]**.

   ![Boîte de dialogue de confirmation de consentement de l’administrateur avec le bouton Accepter](assets/setup-13b.png)

1. Dans l’onglet « [!UICONTROL Utilisateurs et groupes] », assurez-vous que les « Utilisateurs et groupes » valides sont affectés à l’application.

   ![Onglet Utilisateurs et groupes affichant les utilisateurs affectés](assets/setup-14.png)

## Création d&#39;un utilisateur d&#39;application {#creating-an-application-user}

Une fois l’enregistrement de l’application terminé, un utilisateur de l’application peut être créé.

1. Accédez à votre environnement de service commun de données (`https://[org].crm.dynamics.com`).

1. Accédez à **[!UICONTROL Paramètres]** > **[!UICONTROL Sécurité]** > **[!UICONTROL Utilisateurs]**.

1. Choisissez **[!UICONTROL Utilisateurs de l’application]** dans le filtre d’affichage.

1. Sélectionnez **[!UICONTROL + Nouveau]**.

1. Dans le formulaire Utilisateur de l&#39;application, saisissez les informations requises.

   >[!NOTE]
   > Les informations sur le nom d’utilisateur ne doivent pas correspondre à un utilisateur existant dans le [!DNL Azure Active Directory].
   > Dans le champ ID de l’application , saisissez l’ID de l’application que vous avez enregistrée précédemment dans Azure AD.

1. Si la configuration est correcte, après avoir sélectionné **[!UICONTROL Enregistrer]**, les champs **[!UICONTROL URI d’ID de l’application]** et **[!UICONTROL ID d’objet Azure AD]** sont automatiquement renseignés avec les valeurs correctes.

1. Avant de quitter le formulaire utilisateur, choisissez **[!UICONTROL Gérer les rôles]** et attribuez un rôle de sécurité à cet utilisateur de l’application afin qu’il puisse accéder aux données de l’organisation souhaitées.

## Connexion de votre instance Dynamics via OAuth {#connecting-your-dynamics-instance-via-oAuth}

1. Lors de la première configuration de votre connexion Dynamics, suivez les étapes 1 à 5 de la section « CRM en tant que fournisseur de données » dans [cet article](/help/marketo-measure-and-dynamics/microsoft-dynamics-crm-installation-guide.md).

1. Lorsque vous êtes invité à fournir des informations d’identification OAuth, renseignez l’ID client, le secret client et l’URI d’ID d’application configurés dans la section ci-dessus.

a. L’ID client est l’ID de l’étape #7 dans la section ci-dessus. Si vous ne l&#39;avez pas noté, l&#39;ID de l&#39;application est affiché dans les paramètres de l&#39;enregistrement de l&#39;application.

b. Le secret client est le secret d’application créé sur le portail Azure pour votre application sous Certificats et secrets.

![Page Certificats et secrets affichant la valeur du secret client](assets/creating-2e.png)

c. L’URI d’ID de l’application est l’URL de l’API web cible (ressource sécurisée). Pour trouver l’URL de l’ID d’application, dans le portail Azure, cliquez sur [!DNL Azure Active Directory], sur Enregistrements des applications, ouvrez la page Paramètres de l’application, puis cliquez sur Propriétés. Il peut également s’agir d’une ressource externe comme `https://graph.microsoft.com`. Il s’agit normalement de l’URL de l’instance Dynamics.

1. Après avoir cliqué sur **[!UICONTROL Envoyer]**, vous serez invité à vous connecter avec [!DNL Azure Active Directory]. Une fois l’authentification réussie, votre compte Dynamics est connecté en tant que fournisseur de données dans [!DNL Marketo Measure].

## Réauthentification de votre compte Dynamics {#re-authenticating-your-dynamics-account}

1. Lorsque vous vous trouvez dans l’application [!DNL Marketo Measure], accédez à **[!UICONTROL Mes paramètres]** > **[!UICONTROL Paramètres]** > **[!UICONTROL Connexions]**.

1. Cliquez sur l’icône clé dans la section CRM en regard de la connexion Dynamics.

1. Lorsque l’utilisateur clique sur la clé, un pop-up s’affiche et vous êtes invité à saisir l’ID client, le secret client et l’URI d’ID d’application, comme pour le flux d’inscription.

   ![Boîte de dialogue de réauthentification avec les champs d’informations d’identification OAuth](assets/re-authenticating-3.png)

1. Après avoir cliqué sur **[!UICONTROL Envoyer]**, vous serez invité à vous connecter avec [!DNL Azure Active Directory]. Une fois l’authentification réussie, votre compte Dynamics est réautorisé dans [!DNL Marketo Measure].
