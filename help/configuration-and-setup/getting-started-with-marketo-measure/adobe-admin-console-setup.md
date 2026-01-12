---
description: Configuration d’Adobe Admin Console
title: Configuration d’Adobe Admin Console
feature: Installation
exl-id: f9edacae-79e0-408c-ac37-bbe67c185f2d
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 79%

---


# Configuration d’Adobe Admin Console {#adobe-admin-console-setup}

La première étape pour utiliser [!DNL Marketo Measure] consiste à créer un compte Adobe Admin Console et à s’y connecter. Si vous n’avez pas encore reçu l’e-mail contenant les instructions de connexion, contactez la personne responsable de votre compte [!DNL Marketo Measure].

## Configurer votre Adobe Admin Console et votre fournisseur d’identité {#set-up-your-adobe-admin-console-and-identity-provider}

En tant que produit de la suite Adobe, [!DNL Marketo Measure] tire parti de toutes les fonctionnalités d’Adobe Admin Console pour Identity Management. Vous trouverez plus de ressources [ici](https://helpx.adobe.com/fr/enterprise/using/admin-console.html).

Nous vous recommandons de passer en revue toutes les ressources, bonnes pratiques et options disponibles pour [Identity Management](https://helpx.adobe.com/fr/enterprise/using/set-up-identity.html).

Pour obtenir des conseils sur la configuration d’Identity Management dans Adobe Admin Console et la vérifier, contactez la personne responsable de votre compte [!DNL Marketo Measure].

Pour faciliter l’authentification et l’autorisation des utilisateurs et utilisatrices sur vos instances [!DNL Marketo Measure], vous devez réaliser les étapes suivantes dans Adobe Admin Console :

**Configurer la fiche produit de [!DNL Marketo Measure]**

Lorsque vous accédez à Adobe Admin Console, vous pouvez voir vos instances produits [!DNL Marketo Measure] présentes dans la section Vue d’ensemble.

![Adobe Admin Console affichant la fiche produit Marketo Measure](assets/adobe-admin-console-setup-1.png)

Cliquez sur la fiche produit de [!DNL Marketo Measure] pour afficher toutes vos instances [!DNL Marketo Measure]. Par défaut, chaque instance [!DNL Marketo Measure] possède son propre profil, précédé du préfixe « [!DNL Marketo Measure] ». Tous les administrateurs, administratrices, utilisateurs ou utilisatrices ajoutés à ce profil ou à tout autre profil de cette instance pourront se connecter à [!DNL Marketo Measure].

![Liste des profils de produit Adobe Admin Console pour les instances Marketo Measure](assets/adobe-admin-console-setup-2.png)

Aucune action n’est requise pour créer un profil dans la ou les instances produits [!DNL Marketo Measure].

Pour commencer à ajouter des utilisateurs et utilisatrices pouvant accéder à [!DNL Marketo Measure], reportez-vous à la section [Ajouter [!DNL Marketo Measure]  des administrateurs et administratrices et des  [!DNL Marketo Measure] utilisateurs et utilisatrices](#adding-marketo-measure-admins-and-marketo-measure-users) ci-dessous.

## Ajouter des administratreurs et administratrices [!DNL Marketo Measure] et des utilisateurs et utilisatrices [!DNL Marketo Measure] {#adding-marketo-measure-admins-and-marketo-measure-users}

L’étape suivante consiste à accorder l’accès à l’application [!DNL Marketo Measure] en ajoutant des utilisateurs et des utilisatrices. Vous pouvez le faire dans le répertoire des administrateurs et administratrices et des utilisateurs et utilisatrices de la fiche produit de [!DNL Marketo Measure].

| Type d’utilisateur ou d’utilisatrice | Description |
|---|---|
| Administrateurs et administratrices | Il s’agit des administrateurs, administratrices, utilisateurs et utilisatrices expérimentés de l’application [!DNL Marketo Measure] avec la capacité de mettre à jour et gérer les options de configuration spécifiques de [!DNL Marketo Measure]. |
| Utilisateurs et utilisatrices | il s’agit des utilisateurs et utilisatrices standard de l’application [!DNL Marketo Measure] ayant des autorisations en lecture seule dans l’application [!DNL Marketo Measure] |

Lors de l’ajout d’un utilisateur ou d’une utilisatrice à son groupe respectif, vous verrez le [type d’identité répertorié](https://helpx.adobe.com/fr/enterprise/using/set-up-identity.html) de la personne.

>[!NOTE]
>Pour être un administrateur [!DNL Marketo Measure] (dans [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"}), un utilisateur doit être ajouté en tant qu’utilisateur _et_ en tant qu’administrateur à un profil de produit [!DNL Marketo Measure] dans la fiche produit [!DNL Marketo Measure].

**Se connecter à[!DNL Marketo Measure]**

Une fois qu’un utilisateur a été ajouté à un profil de produit, il peut accéder à ses instances [!DNL Marketo Measure] en sélectionnant l’option **Se connecter avec Adobe ID** à l’adresse [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"}.

Écran de connexion à ![Marketo Measure avec l’option Se connecter avec Adobe ID ](assets/adobe-admin-console-setup-3.png)
