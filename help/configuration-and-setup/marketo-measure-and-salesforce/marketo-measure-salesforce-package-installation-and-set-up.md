---
description: « Installation et configuration du package [!DNL Marketo Measure] pour Salesforce - [!DNL Marketo Measure] - Documentation du produit »
title: « Installation et configuration du package [!DNL Marketo Measure] [!DNL Salesforce]  »
exl-id: ed58bc1e-cfb0-48db-aa53-96204e12de2e
feature: Installation, Salesforce
source-git-commit: a2a7657e8377fd5c556d38f6eb815e39d2b8d15e
workflow-type: ht
source-wordcount: '543'
ht-degree: 100%

---

# Installation et configuration du package [!DNL Marketo Measure] pour Salesforce {#marketo-measure-salesforce-package-installation-and-set-up}

Avant d’installer le package de base [!DNL Marketo Measure] pour [!DNL Salesforce], vous devez déterminer si vous allez d’abord l’installer dans une instance sandbox de [!DNL Salesforce] avant de passer à votre instance de production.

>[!NOTE]
>
>Une fois votre compte [!DNL Marketo Measure] connecté à une instance de production [!DNL Salesforce], vous ne pouvez pas revenir en arrière et vous connecter à une instance sandbox. En outre, un compte [!DNL Marketo Measure] ne peut être connecté qu’à une seule instance de production [!DNL Salesforce].

Le package de base [!DNL Marketo Measure] contient les éléments suivants :

* 7 objets [!DNL Marketo Measure] personnalisés
* Champs [!DNL Marketo Measure] personnalisés
* 25 rapports [!DNL Stock]

[!DNL Marketo Measure] est capable de lire les objets, les champs et les enregistrements dans [!DNL Salesforce], mais [!DNL Marketo Measure] ne mettra jamais à jour les données et n’en ajoutera jamais de nouvelles. Toutes les données collectées par le code JavaScript [!DNL Marketo Measure] apparaissent dans les objets et les champs personnalisés [!DNL Marketo Measure].

Pour installer le package de base [!DNL Marketo Measure Salesforce], suivez les étapes ci-dessous.

1. À l’aide d’un navigateur en mode navigation privée, accédez à la [Salesforce AppExchange](https://appexchange.salesforce.com/appxListingDetail?listingId=a0N3000000B3KLuEAN){target="_blank"} et connectez-vous.

1. Installez le package [!DNL Marketo Measure] dans un environnement sandbox ou en production.

1. Connectez-vous à [!DNL Salesforce] en tant qu’administrateur.

1. Sélectionnez **[!UICONTROL Installation] pour tous les utilisateurs**.

   ![](assets/marketo-measure-salesforce-package-installation-and-set-up-1.png)

1. Une fois l’installation terminée, vous pouvez la visualiser.

   ![](assets/marketo-measure-salesforce-package-installation-and-set-up-2.png)

Une fois l’installation terminée, vous pouvez mettre à jour vos dispositions de page [[!DNL Salesforce] ](/help/configuration-and-setup/marketo-measure-and-salesforce/page-layout-instructions.md){target="_blank"} avec les champs [!DNL Marketo Measure], si vous le souhaitez.

>[!NOTE]
>
>Pour en savoir plus sur les autorisations créées dans [!DNL Marketo Measure] et la façon dont elles seront utilisées, [cliquez ici](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-permission-sets.md){target="_blank"}.

## Installation du package de tableau de bord [!DNL Marketo Measure] {#install-marketo-measure-dashboard-package}

Le package d’extension [!UICONTROL Tableau de bord] contient trois tableaux prédéfinis. Nous vous recommandons d’installer ce package [!UICONTROL dans] l’environnement de production pour tous les utilisateurs.

1. Installez le package à partir de [[!DNL Salesforce] AppExchange](https://login.salesforce.com/packaging/installPackage.apexp?p0=04t610000001jI6){target="_blank"}.

1. Sélectionnez **[!UICONTROL Installation pour tous les utilisateurs]**.

   ![](assets/marketo-measure-salesforce-package-installation-and-set-up-3.png)

## Création d’un profil et d’un utilisateur [!DNL Marketo Measure] {#creating-a-marketo-measure-profile-and-user}

[!DNL Marketo Measure] envoie et reçoit des données par l’intermédiaire d’un utilisateur [!DNL Salesforce] connecté à l’application [!DNL Marketo Measure].

Pour transmettre les données relatives aux points de contact à votre instance [!DNL Salesforce], l’utilisateur connecté doit avoir accès aux objets personnalisés [!DNL Marketo Measure] (par exemple, les points de contact acheteur et d’attribution acheteur), ainsi qu’aux objets standard [!DNL Salesforce], tels que les prospects et les contacts.

Créez un profil [!DNL Marketo Measure] pour vous assurer que vous ne rencontrerez pas d’erreurs de validation lors de la transmission de données vers Salesforce.

Étape 1 : créez un profil [!DNL Marketo Measure].

1. Attribuez-lui les autorisations suivantes :

* « Jeu d’autorisations administrateur [!DNL Marketo Measure] »
   * Ce jeu d’autorisations géré permet à un administrateur SFDC de créer, lire, écrire et supprimer des enregistrements depuis les objets [!DNL Marketo Measure].
* « Jeu d’autorisations d’affichage et de modification des prospects convertis »
   * Ces autorisations permettent à [!DNL Marketo Measure] de décorer les prospects après leur conversion en contacts. Si ce jeu d’autorisations n’est pas activé, d’importants écarts de suivi des données peuvent survenir.

>[!NOTE]
>
>Ce profil peut être un clone d’un administrateur système.

Étape 2 : créez un utilisateur [!DNL Marketo Measure] afin que vous puissiez suivre l’impact de [!DNL Marketo Measure] sur votre instance [!DNL Salesforce].

1. Attribuez le nouveau profil [!DNL Marketo Measure] à cet utilisateur.

1. Activez l’autorisation « Utilisateur marketing » au niveau de l’utilisateur.

* La case à cocher [!UICONTROL Utilisateur marketing] permet à l’utilisateur de créer des campagnes, mais aussi d’utiliser les assistants d’importation de campagne. Si cette case n’est pas cochée, l’utilisateur peut uniquement afficher les campagnes et leur configuration avancée, modifier leur historique pour un seul prospect ou contact et générer des rapports de campagne. [!DNL Marketo Measure] doit pouvoir lire et écrire dans les campagnes.

Étape 3 : excluez ce profil de tous les déclencheurs, workflows et processus.

Étape 4 : connectez-vous à votre compte [!DNL Marketo Measure] et autorisez à nouveau la connexion [!DNL Salesforce] avec le nouvel utilisateur.

1. Accédez à apps.bizible.com et connectez-vous avec les informations d’identification correspondant au nouvel utilisateur dans l’environnement de production [!DNL Salesforce].

1. Sélectionnez **[!UICONTROL Paramètres]** dans le menu déroulant **[!UICONTROL Mon compte]**.

1. Dans le regroupement **[!UICONTROL Intégrations]**, sélectionnez **[!UICONTROL Connexions]**.

1. Cliquez sur l’icône de clé à droite de la connexion [!DNL Salesforce] actuelle, puis sélectionnez **Autoriser à nouveau en production**. Connectez-vous à nouveau à l’aide des informations d’identification du nouvel utilisateur (le cas échéant).
