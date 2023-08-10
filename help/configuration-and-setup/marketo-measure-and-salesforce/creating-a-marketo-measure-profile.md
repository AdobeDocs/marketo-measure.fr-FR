---
unique-page-id: 18874698
description: Création d’un [!DNL Marketo Measure] Profile - [!DNL Marketo Measure] - Documentation du produit
title: Création d’un profil [!DNL Marketo Measure]
exl-id: dab2e2cb-fbd3-464a-9bd7-e9bf153d9848
feature: Salesforce
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 24%

---

# Création d’un profil[!DNL Marketo Measure] {#creating-a-marketo-measure-profile}

Découvrez comment créer une [!DNL Marketo Measure] profile. Création d’un [!DNL Marketo Measure] profile permet de s’assurer que nous ne rencontrons pas d’erreurs de validation lors de la transmission de données vers votre CRM.

1. Création d’un [!DNL Marketo Measure] profile:

   * Attribuez le [!DNL Marketo Measure] Jeu d’autorisations de l’administrateur
   * Autorisation d’afficher et de modifier les pistes converties

   >[!NOTE]
   >
   >Ce profil peut être un clone d’un [!DNL System Admin] profile

1. Création d’un [!DNL Marketo Measure] user :

   * Attribuez le nouveau profil [!DNL Marketo Measure] à cet utilisateur
   * Activez l’autorisation « Utilisateur marketing » au niveau de l’utilisateur

1. Excluez ce profil de tous les déclencheurs, workflows et processus.
1. Connectez-vous à [!DNL Marketo Measure] Compte et réautorisation de la variable [!DNL Salesforce] connexion avec le nouvel utilisateur :

   * Accédez à [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"} et connectez-vous avec les informations d’identification Salesforce de production du nouvel utilisateur.
   * Sélectionnez &quot;[!UICONTROL Paramètres]&quot; dans le[!UICONTROL Mon compte]Liste déroulante
   * Sélectionnez &quot;[!UICONTROL Connexions]&quot; dans le[!UICONTROL Intégrations]Groupement
   * Cliquez sur l’icône de clé à droite de la connexion [!DNL Salesforce] actuelle, puis sélectionnez Autoriser à nouveau en production. Connectez-vous à nouveau à l’aide des nouvelles informations d’identification de l’utilisateur si vous y êtes invité.

   Fait!

   Si vous avez des questions sur la création d’un dédié [!DNL Marketo Measure] , contactez l’équipe de compte Adobe (votre gestionnaire de compte) ou [Prise en charge de Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.
