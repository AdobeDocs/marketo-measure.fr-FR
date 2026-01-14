---
description: Création de conseils sur  [!DNL Marketo Measure]  profil pour les utilisateurs de Marketo Measure
title: 'Création d’un profil [!DNL Marketo Measure] '
exl-id: dab2e2cb-fbd3-464a-9bd7-e9bf153d9848
feature: Salesforce
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 3%

---

# Création d’un profil [!DNL Marketo Measure] {#creating-a-marketo-measure-profile}

Découvrez comment créer un profil de [!DNL Marketo Measure]. La création d’un profil [!DNL Marketo Measure] garantit que nous ne rencontrerons pas d’erreurs de validation lors de la publication de données vers votre CRM.

1. Créez un profil de [!DNL Marketo Measure] spécifique :

   * Attribuer le jeu d’autorisations d’administrateur [!DNL Marketo Measure]
   * Activer l’autorisation d’affichage et de modification des prospects convertis

   >[!NOTE]
   >
   >Ce profil peut être un clone d’un profil [!DNL System Admin]

1. Création d’un utilisateur [!DNL Marketo Measure] dédié :

   * Attribuer le nouveau profil [!DNL Marketo Measure] à cet utilisateur
   * Activez « Utilisateur marketing » en tant qu’autorisation de niveau utilisateur

1. Exclure ce profil de tous les déclencheurs, workflows et processus.
1. Connectez-vous à votre compte [!DNL Marketo Measure] et réautorisez la connexion [!DNL Salesforce] avec le nouvel utilisateur :

   * Accédez à [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"} et connectez-vous avec les nouvelles informations d’identification Salesforce de production de l’utilisateur
   * Sélectionnez « [!UICONTROL Settings] » dans le menu déroulant « [!UICONTROL My Account] » (Mon compte).
   * Sélectionnez « [!UICONTROL Connexions] » dans le groupe « [!UICONTROL Intégrations] »
   * Cliquez sur l’icône Clé à droite de la connexion [!DNL Salesforce] actuelle connectée et sélectionnez Réautoriser avec la production . Connectez-vous ensuite à nouveau avec les nouvelles informations d’identification de l’utilisateur si cela vous est demandé

   Terminé!

   Si vous avez des questions sur la création d’un profil de [!DNL Marketo Measure] dédié, contactez l’équipe du compte Adobe (votre gestionnaire de compte) ou l’assistance de [Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.
