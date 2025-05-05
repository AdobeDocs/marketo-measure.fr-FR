---
description: Accès Data Warehouse - Compte de Reader - Documentation du produit
title: Accès à Data Warehouse - Compte en lecture seule
exl-id: 2aa73c41-47ab-4f11-96d8-dafb642308fc
feature: Data Warehouse
source-git-commit: e9861f8032475d3e60a3bb3ebf67dfee520bbb75
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 2%

---

# Accès à Data Warehouse - Compte en lecture seule {#data-warehouse-access-reader-account}

## Lien d’accès au Snowflake {#snowflake-access-link}

Pour accéder à l’entrepôt de données de votre Snowflake, vous devez accéder à l’URL spécifique de votre compte de Snowflake. Pour obtenir ce lien d’accès, connectez-vous à [!DNL Marketo Measure] et suivez les étapes ci-dessous pour accéder à la page d’informations du Data Warehouse.

1. Dans [!DNL Marketo Measure], en haut de la page, cliquez sur **[!UICONTROL Mon compte]** > **[!UICONTROL Paramètres]**.

   ![](assets/data-warehouse-access-reader-account-1.png)

1. Dans le menu de gauche, sous Sécurité, cliquez sur **[!UICONTROL Data Warehouse]**.

   ![](assets/data-warehouse-access-reader-account-2.png)

1. Cette page contient le lien vers l’entrepôt de données de votre Snowflake et votre nom d’utilisateur.

   ![](assets/data-warehouse-access-reader-account-3.png)

   >[!NOTE]
   >
   >Il s’agit d’un compte en lecture seule disponible pour votre entreprise et pas seulement pour un utilisateur individuel. Tout utilisateur de votre organisation ayant accès à [!DNL Marketo Measure] peut utiliser ce compte pour se connecter au compte de lecteur du Data Warehouse du Snowflake.

1. Cliquez sur le lien fourni dans l’URL du Snowflake pour accéder à la page de connexion du Snowflake où vous saisissez votre nom d’utilisateur et votre mot de passe. _Si vous ne disposez pas de votre mot de passe, suivez les étapes ci-dessous pour le réinitialiser_.

   ![](assets/data-warehouse-access-reader-account-4.png)

1. Une fois connecté, cliquez sur **[!UICONTROL Feuilles de calcul]** en haut de la page.

   ![](assets/data-warehouse-access-reader-account-5.png)

1. Les objets de base de données BIZIBLE_ROI_V3 se trouvent sur le côté gauche de l’écran. Saisissez l’entrepôt de données, la base de données et le schéma dans les options de liste déroulante en haut de la fenêtre de requête. Il ne doit y avoir qu’une seule option pour chacune. Vous êtes maintenant prêt à exécuter des requêtes dans l’éditeur de requêtes du Snowflake.

   ![](assets/data-warehouse-access-reader-account-6.png)

## Réinitialiser votre mot de passe {#reset-your-password}

[!DNL Marketo Measure] n’a pas accès à votre mot de passe de connexion de Snowflake. Si vous devez réinitialiser votre mot de Data Warehouse, cliquez sur le bouton [!UICONTROL &#x200B; Réinitialiser le mot de passe &#x200B;] sur la page d’informations du mot de passe, puis suivez les instructions. Un mot de passe temporaire s’affiche immédiatement dans l’interface utilisateur. Vous serez invité à créer votre propre mot de passe lors de votre prochaine connexion à l’entrepôt de données.

>[!NOTE]
>
>* La réinitialisation du mot de passe le réinitialise pour tous les utilisateurs [!DNL Marketo Measure] de votre entreprise, et pas seulement pour l’utilisateur actuellement connecté.
>* Nous n’affichons que le mot de passe temporaire dans l’interface utilisateur. Aucun e-mail ne sera envoyé.

![](assets/data-warehouse-access-reader-account-7.png)

![](assets/data-warehouse-access-reader-account-8.png)

## Connexion à Snowflake via des outils tiers {#connecting-to-snowflake-via-third-party-tools}

Vous devez saisir quelques informations pour connecter votre entrepôt de données de Snowflake à un outil tiers.

>[!NOTE]
>
>Chaque outil a des exigences de connexion différentes. Il est recommandé de consulter la documentation de l’outil spécifique que vous essayez de connecter.

* **URI** (toujours requis)
   * Il s’agit du nom de domaine du compte du Snowflake. Il se trouve dans une partie du lien de connexion du Snowflake.
* **Nom d’utilisateur** (toujours requis)
   * Le nom d’utilisateur est répertorié dans la page d’informations du Data Warehouse de [!DNL Marketo Measure].
* **Mot de passe** (toujours obligatoire)
   * Il s’agit du mot de passe défini lors de la première connexion à votre compte de Snowflake. Pour réinitialiser votre mot de passe, reportez-vous aux étapes décrites ci-dessus.
* **Nom de la base de données** (pas toujours obligatoire)
   * C’est la base de données qui stocke les données dans Snowflake. Il s’agit de la ressource de stockage. Le nom de la base de données est indiqué sur la page d&#39;informations du Data Warehouse dans [!DNL Marketo Measure].
* **Nom de l’entrepôt de données** (pas toujours obligatoire)
   * C’est l’entrepôt qui exécute les requêtes en Snowflake. Il s’agit de la ressource calculée. Le nom de l&#39;entrepôt de données est indiqué sur la page d&#39;informations du Data Warehouse dans [!DNL Marketo Measure].

  ![](assets/data-warehouse-access-reader-account-9.png)
