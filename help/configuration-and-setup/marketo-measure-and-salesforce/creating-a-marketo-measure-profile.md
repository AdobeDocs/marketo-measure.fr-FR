---
unique-page-id: 18874698
description: Création d’un  [!DNL Marketo Measure] profil - [!DNL Marketo Measure]
title: Création d’un profil [!DNL Marketo Measure]
exl-id: dab2e2cb-fbd3-464a-9bd7-e9bf153d9848
feature: Salesforce
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 3%

---

# Création d’un profil [!DNL Marketo Measure] {#creating-a-marketo-measure-profile}

Découvrez comment créer un profil [!DNL Marketo Measure]. La création d’un profil [!DNL Marketo Measure] permet de s’assurer que nous ne rencontrons pas d’erreurs de validation lors de la transmission de données vers votre CRM.

1. Créez un profil [!DNL Marketo Measure] spécifique :

   * Attribuer le jeu d’autorisations d’administrateur [!DNL Marketo Measure]
   * Autorisation d’afficher et de modifier les pistes converties

   >[!NOTE]
   >
   >Ce profil peut être un clone d&#39;un profil [!DNL System Admin]

1. Création d’un utilisateur [!DNL Marketo Measure] dédié :

   * Attribuer le nouveau profil [!DNL Marketo Measure] à cet utilisateur
   * Activer l’autorisation &quot;Utilisateur marketing&quot; au niveau de l’utilisateur

1. Excluez ce profil de tous les déclencheurs, workflows et processus.
1. Connectez-vous à votre compte [!DNL Marketo Measure] et réautorisez la connexion [!DNL Salesforce] avec le nouvel utilisateur :

   * Accédez à [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"} et connectez-vous avec les nouvelles informations d’identification Salesforce de production de l’utilisateur.
   * Sélectionnez &quot;[!UICONTROL Settings]&quot; dans la liste déroulante &quot;[!UICONTROL My Account]&quot;
   * Sélectionnez &quot;[!UICONTROL Connexions]&quot; dans le regroupement &quot;[!UICONTROL Intégrations]&quot;.
   * Cliquez sur l’icône de clé à droite de la connexion [!DNL Salesforce] actuelle et sélectionnez Réautoriser avec production. Connectez-vous à nouveau à l’aide des nouvelles informations d’identification de l’utilisateur si vous y êtes invité.

   Terminé!

   Si vous avez des questions sur la création d’un profil [!DNL Marketo Measure] dédié, contactez l’équipe du compte d’Adobe (votre gestionnaire de compte) ou l’[assistance Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.
