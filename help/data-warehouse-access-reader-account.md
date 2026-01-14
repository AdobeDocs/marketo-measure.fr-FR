---
description: Décrit comment configurer et utiliser un compte de lecteur pour accéder à l’entrepôt de données Marketo Measure
title: Accès à Data Warehouse - Compte en lecture seule
exl-id: 2aa73c41-47ab-4f11-96d8-dafb642308fc
feature: Data Warehouse
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '603'
ht-degree: 3%

---

# Accès à Data Warehouse - Compte en lecture seule {#data-warehouse-access-reader-account}

## Lien d’accès Snowflake {#snowflake-access-link}

Pour accéder à votre entrepôt de données Snowflake, vous devez accéder à l’URL spécifique à votre compte Snowflake. Pour obtenir ce lien d’accès, connectez-vous à [!DNL Marketo Measure] et suivez les étapes ci-dessous pour accéder à la page d’informations de Data Warehouse.

1. Dans [!DNL Marketo Measure], en haut de la page, cliquez sur **[!UICONTROL Mon compte]** > **[!UICONTROL Paramètres]**.

   ![1. Dans Marketo Measure, en haut de la page, cliquez sur &#x200B;](assets/data-account-7.png)

1. Dans le menu de gauche, sous Sécurité, cliquez sur **[!UICONTROL Data Warehouse]**.

   ![1. Dans le menu de gauche, sous Sécurité, cliquez sur Data Warehouse.](assets/data-account-8.png)

1. Cette page contient le lien vers votre entrepôt de données Snowflake et votre nom d’utilisateur.

   ![1. Cette page contient le lien vers votre entrepôt de données Snowflake et &#x200B;](assets/data-account-9.png)

   >[!NOTE]
   >
   >Il s’agit d’un compte en lecture seule disponible pour votre entreprise et pas seulement pour un utilisateur individuel. Tout utilisateur de votre organisation ayant accès à [!DNL Marketo Measure] peut utiliser ce compte pour se connecter au compte de lecteur Snowflake Data Warehouse.

1. Cliquez sur le lien fourni dans l’URL de Snowflake pour accéder à la page de connexion de Snowflake, où vous saisissez votre nom d’utilisateur et votre mot de passe. _Si vous ne disposez pas de votre mot de passe, suivez les étapes ci-dessous pour le réinitialiser_.

   ![1. Cliquez sur le lien fourni dans l’URL de Snowflake pour accéder à &#x200B;](assets/data-account-5.png)

1. Une fois connecté, cliquez sur **[!UICONTROL Feuilles de calcul]** en haut de la page.

   ![1. Une fois la connexion effectuée, cliquez sur Feuilles de calcul en haut de l’](assets/data-account-6.png)

1. Les objets de base de données BIZIBLE_ROI_V3 se trouvent sur le côté gauche de l’écran. Saisissez l’entrepôt de données, la base de données et le schéma dans les options de liste déroulante en haut de la fenêtre de requête. Il ne doit y avoir qu’une seule option pour chacune. Vous êtes maintenant prêt à exécuter des requêtes dans l’éditeur de requêtes de Snowflake.

   ![1. Les objets de base de données BIZIBLEROIV3 se trouvent sur le côté gauche de la &#x200B;](assets/data-account-4.png)

## Réinitialiser votre mot de passe {#reset-your-password}

[!DNL Marketo Measure] n’a pas accès à votre mot de passe de connexion Snowflake. Si vous devez réinitialiser votre mot de passe, cliquez sur le bouton [!UICONTROL Réinitialiser le mot de passe] sur la page d’informations de Data Warehouse, puis suivez les instructions. Un mot de passe temporaire s’affiche immédiatement dans l’interface utilisateur. Vous serez invité à créer votre propre mot de passe lors de votre prochaine connexion à l’entrepôt de données.

>[!NOTE]
>
>* La réinitialisation du mot de passe le réinitialise pour tous les utilisateurs [!DNL Marketo Measure] de votre entreprise, et pas seulement pour l’utilisateur actuellement connecté.
>* Nous n’affichons que le mot de passe temporaire dans l’interface utilisateur. Aucun e-mail ne sera envoyé.

![Nous n’affichons que le mot de passe temporaire dans l’interface utilisateur. Un e-mail &#x200B;](assets/data-account-3.png)

![Nous n’affichons que le mot de passe temporaire dans l’interface utilisateur. Un e-mail &#x200B;](assets/data-account-1.png)

## Connexion à Snowflake via des outils tiers {#connecting-to-snowflake-via-third-party-tools}

Vous devez saisir quelques informations pour connecter votre entrepôt de données Snowflake à un outil tiers.

>[!NOTE]
>
>Chaque outil a des exigences de connexion différentes. Il est recommandé de consulter la documentation de l’outil spécifique que vous essayez de connecter.

* **URI** (toujours requis)
   * Il s’agit du nom de domaine du compte Snowflake. Il se trouve dans une partie du lien de connexion Snowflake.
* **Nom d’utilisateur** (toujours requis)
   * Le nom d’utilisateur est répertorié dans la page d’informations de Data Warehouse dans [!DNL Marketo Measure].
* **Mot de passe** (toujours obligatoire)
   * Il s’agit du mot de passe que vous avez défini la première fois que vous vous êtes connecté à votre compte Snowflake. Pour réinitialiser votre mot de passe, reportez-vous aux étapes décrites ci-dessus.
* **Nom de la base de données** (pas toujours obligatoire)
   * C’est la base de données qui stocke les données dans Snowflake. Il s’agit de la ressource de stockage. Le nom de la base de données est répertorié dans la page d’informations Data Warehouse de [!DNL Marketo Measure].
* **Nom de l’entrepôt de données** (pas toujours obligatoire)
   * C’est l’entrepôt qui exécute les requêtes dans Snowflake. Il s’agit de la ressource calculée. Le nom de l’entrepôt de données est répertorié dans la page d’informations Data Warehouse de [!DNL Marketo Measure].

  ![C’est l’entrepôt qui exécute les requêtes dans Snowflake. Il s’agit du calculé](assets/data-account-2.png)
