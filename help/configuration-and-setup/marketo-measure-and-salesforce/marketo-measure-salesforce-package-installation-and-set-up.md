---
description: "[!DNL Marketo Measure] Installation et configuration du package Salesforce - [!DNL Marketo Measure] - Documentation du produit"
title: "[!DNL Marketo Measure] [!DNL Salesforce] Installation et configuration du package"
exl-id: ed58bc1e-cfb0-48db-aa53-96204e12de2e
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 0%

---

# [!DNL Marketo Measure] Installation et configuration du package Salesforce {#marketo-measure-salesforce-package-installation-and-set-up}

Avant d’installer le [!DNL Marketo Measure] [!DNL Salesforce] package de base, vous devez déterminer si vous allez d’abord l’installer dans un [!DNL Salesforce] sandbox avant de passer à votre instance de production Salesforce.

>[!NOTE]
>
>Une fois votre [!DNL Marketo Measure] est connecté à un compte [!DNL Salesforce] instance de production, vous ne pouvez pas revenir en arrière et vous connecter à un environnement de test. En outre, une [!DNL Marketo Measure] ne peut être connecté qu’à un seul compte [!DNL Salesforce] instance de production.

Le [!DNL Marketo Measure] Le package de base contient :

* 7 personnalisés [!DNL Marketo Measure] Objets
* Personnalisé [!DNL Marketo Measure] Champs
* 25 [!DNL Stock] Rapports

[!DNL Marketo Measure] est capable de lire les [!DNL Salesforce] Cependant, les objets, les champs et les enregistrements, [!DNL Marketo Measure] ne mettra jamais à jour ou ne leur enverra jamais de données. Toutes les données collectées par la variable [!DNL Marketo Measure] Le code JavaScript apparaît dans la variable [!DNL Marketo Measure] Objets et champs personnalisés.

Suivez les étapes ci-dessous pour installer le [!DNL Marketo Measure Salesforce] package de base.

1. À l’aide d’un navigateur incognito, accédez à la [Salesforce Appexchange](https://appexchange.salesforce.com/appxListingDetail?listingId=a0N3000000B3KLuEAN){target="_blank"} et connectez-vous.

1. Installez dans le [!DNL Marketo Measure] module en environnement de test ou en production.

1. Connectez-vous à [!DNL Salesforce] en tant qu’administrateur.

1. Sélectionner **[!UICONTROL Installer] pour tous les utilisateurs**.

   ![](assets/marketo-measure-salesforce-package-installation-and-set-up-1.png)

1. Une fois l&#39;installation terminée, vous pouvez la visualiser.

   ![](assets/marketo-measure-salesforce-package-installation-and-set-up-2.png)

Une fois l’installation terminée, vous pouvez mettre à jour votre [[!DNL Salesforce] dispositions de page](/help/configuration-and-setup/marketo-measure-and-salesforce/page-layout-instructions.md){target="_blank"} avec le [!DNL Marketo Measure] si vous le souhaitez.

>[!NOTE]
>
>En savoir plus sur les [!DNL Marketo Measure] Jeux d’autorisations créés et [leur utilisation](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-permission-sets.md){target="_blank"}.

## Installer [!DNL Marketo Measure] Package de tableau de bord {#install-marketo-measure-dashboard-package}

Le [!UICONTROL Tableau de bord] Le module d’extension contient trois tableaux de bord prédéfinis. Nous vous recommandons d’installer [!UICONTROL dans] Production pour tous les utilisateurs.

1. Installez le module à partir du [[!DNL Salesforce] Appexchange](https://login.salesforce.com/packaging/installPackage.apexp?p0=04t610000001jI6){target="_blank"}.

1. Sélectionner **[!UICONTROL Installation pour tous les utilisateurs]**.

   ![](assets/marketo-measure-salesforce-package-installation-and-set-up-3.png)

## Création d’un [!DNL Marketo Measure] Profil et utilisateur {#creating-a-marketo-measure-profile-and-user}

[!DNL Marketo Measure] envoie et reçoit des données par l’intermédiaire d’un [!DNL Salesforce] dans la fonction [!DNL Marketo Measure] application.

Pour transmettre des données de point de contact à votre [!DNL Salesforce] , l’utilisateur connecté doit avoir accès à [!DNL Marketo Measure] des objets personnalisés (par exemple, point de contact de l’acheteur et point de contact d’attribution de l’acheteur), ainsi que des objets standard ; [!DNL Salesforce] tels que Leads et Contacts.

Créez un [!DNL Marketo Measure] pour vous assurer que vous ne rencontrerez pas d’erreurs de validation lors de la publication de données vers Salesforce.

Étape 1 : Création d’un [!DNL Marketo Measure] profile

1. Attribuez les autorisations suivantes :

* &quot;[!DNL Marketo Measure] Jeu d’autorisations de l’administrateur&quot;
   * L’ensemble d’autorisations géré permet à un administrateur SFDC de créer, lire, écrire et supprimer des enregistrements depuis [!DNL Marketo Measure] objets.
* &quot;Afficher et modifier le jeu d’autorisations de pistes converties&quot;
   * Cela permet [!DNL Marketo Measure] pour décorer les pistes après leur conversion en contacts. Si ce jeu d’autorisations n’est pas activé, il peut y avoir d’importants écarts de suivi des données.

>[!NOTE]
>
>Ce profil peut être un clone d’un profil d’administrateur système.

Étape 2 : Créer un [!DNL Marketo Measure] afin que vous puissiez suivre l’impact de [!DNL Marketo Measure] sur votre [!DNL Salesforce] instance

1. Attribuer le nouveau [!DNL Marketo Measure] Profil vers cet utilisateur.

1. Activez l’autorisation &quot;Utilisateur marketing&quot; au niveau de l’utilisateur.

* Le [!UICONTROL Utilisateur marketing] permet à l’utilisateur de créer des campagnes et d’utiliser les assistants d’importation de campagne. Si cette option n’est pas sélectionnée, l’utilisateur peut uniquement afficher les campagnes et la configuration avancée de la campagne, modifier l’historique des campagnes pour un seul prospect ou contact et exécuter des rapports de campagne. [!DNL Marketo Measure] doit pouvoir lire et écrire dans l’objet campaign.

Étape 3 : Exclure ce profil de tous les déclencheurs, workflows et processus

Étape 4 : Connectez-vous à votre [!DNL Marketo Measure] Compte et réautorisation de la variable [!DNL Salesforce] connexion avec le nouvel utilisateur

1. Accédez à apps.bizible.com et connectez-vous avec la nouvelle production utilisateur. [!DNL Salesforce] informations d’identification.

1. Sélectionner **[!UICONTROL Paramètres]** dans le **[!UICONTROL Mon compte]** menu déroulant.

1. Sélectionner **[!UICONTROL Connexions]** dans le **[!UICONTROL Intégrations]** regroupement.

1. Cliquez sur l’icône de clé à droite de la connexion actuelle. [!DNL Salesforce] se connecter et sélectionner **Réautorisation avec production**. Connectez-vous à nouveau à l’aide des nouvelles informations d’identification de l’utilisateur (si vous y êtes invité).
