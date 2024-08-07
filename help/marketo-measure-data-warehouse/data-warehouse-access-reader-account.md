---
description: Accès des Data Warehouse - Compte de Reader - Documentation du produit
title: Accès à Data Warehouse - Compte en lecture seule
exl-id: 2aa73c41-47ab-4f11-96d8-dafb642308fc
feature: Data Warehouse
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 2%

---

# Accès à Data Warehouse - Compte en lecture seule {#data-warehouse-access-reader-account}

## Lien d’accès Snowflake {#snowflake-access-link}

Pour accéder à l’entrepôt de données de votre Snowflake, vous devez accéder à l’URL spécifique de votre compte de Snowflake. Vous pouvez trouver ce lien d’accès en vous connectant à [!DNL Marketo Measure] et en suivant les étapes ci-dessous pour accéder à la page d’informations du Data Warehouse.

1. Dans [!DNL Marketo Measure], en haut de la page, cliquez sur **[!UICONTROL Mon compte]** > **[!UICONTROL Paramètres]**.

   ![](assets/data-warehouse-access-reader-account-1.png)

1. Dans le menu de gauche, sous Sécurité, cliquez sur **[!UICONTROL Data Warehouse]**.

   ![](assets/data-warehouse-access-reader-account-2.png)

1. Cette page contient le lien vers votre entrepôt de données de Snowflake et votre nom d’utilisateur.

   ![](assets/data-warehouse-access-reader-account-3.png)

   >[!NOTE]
   >
   >Il s’agit d’un compte en lecture seule disponible pour votre organisation, et pas seulement pour un utilisateur individuel. Tout utilisateur de votre entreprise ayant accès à [!DNL Marketo Measure] peut utiliser ce compte pour se connecter au compte de lecteur du Data Warehouse de Snowflake.

1. Cliquez sur le lien fourni dans l’URL du Snowflake. Vous accédez alors à la page de connexion du Snowflake dans laquelle vous saisissez votre nom d’utilisateur et votre mot de passe. _Si vous n&#39;avez pas votre mot de passe, reportez-vous aux étapes ci-dessous pour le réinitialiser_.

   ![](assets/data-warehouse-access-reader-account-4.png)

1. Une fois connecté, cliquez sur **[!UICONTROL Feuilles de calcul]** en haut de la page.

   ![](assets/data-warehouse-access-reader-account-5.png)

1. Les objets de base de données BIZIBLE_ROI_V3 se trouvent sur le côté gauche de l’écran. Saisissez l’entrepôt, la base de données et le schéma dans les options de liste déroulante situées en haut de la fenêtre de requête. Il ne doit y avoir qu’une seule option pour chacune d’elles. Vous êtes maintenant prêt à exécuter des requêtes dans l’éditeur de requêtes du Snowflake.

   ![](assets/data-warehouse-access-reader-account-6.png)

## Réinitialiser votre mot de passe {#reset-your-password}

[!DNL Marketo Measure] n’a pas accès à votre mot de passe de connexion de Snowflake. Si vous devez réinitialiser votre mot de passe, cliquez sur le bouton [!UICONTROL Réinitialiser le mot de passe] sur la page d’informations du Data Warehouse, puis suivez les instructions. Un mot de passe temporaire s’affiche immédiatement dans l’interface utilisateur. Vous serez invité à créer votre propre mot de passe lors de la prochaine connexion à l’entrepôt de données.

>[!NOTE]
>
>* La réinitialisation du mot de passe le réinitialise pour tous les utilisateurs [!DNL Marketo Measure] de votre entreprise, et pas seulement pour l’utilisateur actuellement connecté.
>* Le mot de passe temporaire s’affiche uniquement dans l’interface utilisateur. Un email ne sera pas envoyé.

![](assets/data-warehouse-access-reader-account-7.png)

![](assets/data-warehouse-access-reader-account-8.png)

## Connexion à Snowflake via des outils tiers {#connecting-to-snowflake-via-third-party-tools}

Vous devez saisir quelques informations pour connecter votre entrepôt de données de Snowflake à un outil tiers.

>[!NOTE]
>
>Chaque outil a des exigences de connexion différentes. Il est recommandé de consulter la documentation de l’outil spécifique que vous essayez de connecter.

* **URI** (toujours requis)
   * Il s’agit du nom de domaine du compte du Snowflake. Il est contenu dans une partie du lien de connexion du Snowflake.
* **Nom d’utilisateur** (toujours requis)
   * Le nom d’utilisateur est répertorié sur la page d’informations du Data Warehouse dans [!DNL Marketo Measure].
* **Mot de passe** (toujours requis)
   * Il s’agit du mot de passe que vous définissez la première fois que vous vous connectez à votre compte de Snowflake. Pour réinitialiser votre mot de passe, reportez-vous aux étapes décrites ci-dessus.
* **Nom de la base de données** (pas toujours requis)
   * La base de données est ce qui stocke les données en Snowflake. Il s’agit de la ressource de stockage. Le nom de la base de données est répertorié sur la page d’informations du Data Warehouse dans [!DNL Marketo Measure].
* **Nom de l’entrepôt** (pas toujours requis)
   * L’entrepôt est celui qui exécute les requêtes en Snowflake. C&#39;est la ressource calculée. Le nom de l’entrepôt est répertorié sur la page d’informations du Data Warehouse dans [!DNL Marketo Measure].

  ![](assets/data-warehouse-access-reader-account-9.png)
