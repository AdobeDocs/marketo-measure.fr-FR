---
unique-page-id: 18874698
description: Création d’un [!DNL Marketo Measure] Profile - [!DNL Marketo Measure]
title: Création d’un profil [!DNL Marketo Measure]
exl-id: dab2e2cb-fbd3-464a-9bd7-e9bf153d9848
feature: Salesforce
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 3%

---

# Création d’un [!DNL Marketo Measure] Profil {#creating-a-marketo-measure-profile}

Découvrez comment créer une [!DNL Marketo Measure] profile. Création d’un [!DNL Marketo Measure] profile permet de s’assurer que nous ne rencontrons pas d’erreurs de validation lors de la transmission de données vers votre CRM.

1. Création d’un [!DNL Marketo Measure] profile:

   * Attribuez le [!DNL Marketo Measure] Jeu d’autorisations de l’administrateur
   * Autorisation d’afficher et de modifier les pistes converties

   >[!NOTE]
   >
   >Ce profil peut être un clone d’un [!DNL System Admin] profile

1. Création d’un [!DNL Marketo Measure] user :

   * Attribuer le nouveau [!DNL Marketo Measure] Profil vers cet utilisateur
   * Activer l’autorisation &quot;Utilisateur marketing&quot; au niveau de l’utilisateur

1. Excluez ce profil de tous les déclencheurs, workflows et processus.
1. Connectez-vous à [!DNL Marketo Measure] Compte et réautorisation [!DNL Salesforce] connexion avec le nouvel utilisateur :

   * Accédez à [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"} et connectez-vous avec les informations d’identification Salesforce de production du nouvel utilisateur.
   * Sélectionnez &quot;[!UICONTROL Paramètres]&quot; dans le[!UICONTROL Mon compte]Liste déroulante
   * Sélectionnez &quot;[!UICONTROL Connexions]&quot; dans le[!UICONTROL Intégrations]Groupement
   * Cliquez sur l’icône de clé à droite de la connexion actuelle. [!DNL Salesforce] et sélectionnez pour Réautoriser avec Production. Connectez-vous à nouveau à l’aide des nouvelles informations d’identification de l’utilisateur si vous y êtes invité.

   Terminé!

   Si vous avez des questions sur la création d’un dédié [!DNL Marketo Measure] , contactez l’équipe de compte Adobe (votre gestionnaire de compte) ou [Prise en charge de Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.
