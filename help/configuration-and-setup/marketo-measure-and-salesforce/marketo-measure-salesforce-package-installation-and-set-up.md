---
description: "[!DNL Marketo Measure] Installation et configuration du package Salesforce - [!DNL Marketo Measure]"
title: « Installation et configuration du package [!DNL Marketo Measure] [!DNL Salesforce]  »
exl-id: ed58bc1e-cfb0-48db-aa53-96204e12de2e
feature: Installation, Salesforce
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 62%

---

# Installation et configuration du package [!DNL Marketo Measure] pour Salesforce {#marketo-measure-salesforce-package-installation-and-set-up}

Avant d’installer le [!DNL Marketo Measure] [!DNL Salesforce] package de base, vous devez déterminer si vous l’installez d’abord dans une [!DNL Salesforce] sandbox avant de passer à votre instance de production Salesforce.

>[!NOTE]
>
>Une fois votre compte [!DNL Marketo Measure] connecté à une instance de production [!DNL Salesforce], vous ne pouvez pas revenir en arrière et vous connecter à une instance sandbox. En outre, un compte [!DNL Marketo Measure] ne peut être connecté qu’à une seule instance de production [!DNL Salesforce].

Le package de base [!DNL Marketo Measure] contient les éléments suivants :

* 7 objets [!DNL Marketo Measure] personnalisés
* Champs [!DNL Marketo Measure] personnalisés
* 25 rapports [!DNL Stock]

[!DNL Marketo Measure] est capable de lire les objets, les champs et les enregistrements dans [!DNL Salesforce], mais [!DNL Marketo Measure] ne mettra jamais à jour les données et n’en ajoutera jamais de nouvelles. Toutes les données collectées par la variable [!DNL Marketo Measure] JavaScript sera affiché dans la variable [!DNL Marketo Measure] Objets et champs personnalisés.

Pour installer le package de base [!DNL Marketo Measure Salesforce], suivez les étapes ci-dessous.

1. Dans un navigateur incognito, accédez à la [AppExchange Salesforce](https://appexchange.salesforce.com/appxListingDetail?listingId=a0N3000000B3KLuEAN){target="_blank"} et se connecter.

1. Installez le package [!DNL Marketo Measure] dans un environnement sandbox ou en production.

1. Connectez-vous à [!DNL Salesforce] en tant qu’administrateur.

1. Sélectionnez **[!UICONTROL Installation] pour tous les utilisateurs**.

   ![](assets/marketo-measure-salesforce-package-installation-and-set-up-1.png)

1. Une fois l’installation terminée, vous pouvez la visualiser.

   ![](assets/marketo-measure-salesforce-package-installation-and-set-up-2.png)

Une fois l’installation terminée, vous pouvez mettre à jour vos dispositions de page [[!DNL Salesforce] ](/help/configuration-and-setup/marketo-measure-and-salesforce/page-layout-instructions.md){target="_blank"} avec les champs [!DNL Marketo Measure], si vous le souhaitez.

>[!NOTE]
>
>En savoir plus sur les [!DNL Marketo Measure] Jeux d’autorisations créés et [leur utilisation](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-permission-sets.md){target="_blank"}.

## Création d’un profil et d’un utilisateur [!DNL Marketo Measure] {#creating-a-marketo-measure-profile-and-user}

[!DNL Marketo Measure] envoie et reçoit des données par l’intermédiaire d’un utilisateur [!DNL Salesforce] connecté à l’application [!DNL Marketo Measure].

Pour envoyer des données de point de contact vers vos [!DNL Salesforce] , l’utilisateur connecté doit avoir accès à [!DNL Marketo Measure] des objets personnalisés (par exemple, point de contact d’achat et point de contact d’attribution d’achat), ainsi que des objets standard ; [!DNL Salesforce] des objets tels que Leads et Contacts.

Créez un profil [!DNL Marketo Measure] pour vous assurer que vous ne rencontrerez pas d’erreurs de validation lors de la transmission de données vers Salesforce.

Étape 1 : créez un profil [!DNL Marketo Measure].

1. Attribuez-lui les autorisations suivantes :

* « Jeu d’autorisations administrateur [!DNL Marketo Measure] »
   * Ce jeu d’autorisations géré permet à un administrateur SFDC de créer, lire, écrire et supprimer des enregistrements depuis les objets [!DNL Marketo Measure].
* « Jeu d’autorisations d’affichage et de modification des prospects convertis »
   * Ces autorisations permettent à [!DNL Marketo Measure] de décorer les prospects après leur conversion en contacts. Si ce jeu d’autorisations n’est pas activé, il peut y avoir d’importants écarts de suivi des données.

>[!NOTE]
>
>Ce profil peut être un clone d’un administrateur système.

Étape 2 : créez un utilisateur [!DNL Marketo Measure] afin que vous puissiez suivre l’impact de [!DNL Marketo Measure] sur votre instance [!DNL Salesforce].

1. Attribuez le nouveau profil [!DNL Marketo Measure] à cet utilisateur.

1. Activez l’autorisation « Utilisateur marketing » au niveau de l’utilisateur.

* La case à cocher [!UICONTROL Utilisateur marketing] permet à l’utilisateur de créer des campagnes, mais aussi d’utiliser les assistants d’importation de campagne. Si cette option n’est pas sélectionnée, l’utilisateur peut uniquement afficher les campagnes et la configuration avancée de la campagne, modifier l’historique des campagnes pour un seul prospect ou contact et exécuter des rapports de campagne. [!DNL Marketo Measure] doit être capable de lire et d’écrire dans l’objet campaign.

Étape 3 : excluez ce profil de tous les déclencheurs, workflows et processus.

Étape 4 : connectez-vous à votre [!DNL Marketo Measure] Compte et réautorisation [!DNL Salesforce] connexion avec le nouvel utilisateur

1. Accédez à apps.bizible.com et connectez-vous avec les informations d’identification correspondant au nouvel utilisateur dans l’environnement de production [!DNL Salesforce].

1. Sélectionnez **[!UICONTROL Paramètres]** dans le menu déroulant **[!UICONTROL Mon compte]**.

1. Dans le regroupement **[!UICONTROL Intégrations]**, sélectionnez **[!UICONTROL Connexions]**.

1. Cliquez sur l’icône de clé à droite de la connexion actuelle. [!DNL Salesforce] se connecter et sélectionner **Réautoriser avec production**. Connectez-vous à nouveau à l’aide des informations d’identification du nouvel utilisateur (le cas échéant).

>[!MORELIKETHIS]
>
>[Configuration d’Adobe Admin Console](/help/configuration-and-setup/getting-started-with-marketo-measure/adobe-admin-console-setup.md){target="_blank"}
