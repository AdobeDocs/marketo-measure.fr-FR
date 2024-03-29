---
description: Configuration d’Adobe Admin Console - Marketo Measure - Documentation du produit
title: Configuration d’Adobe Admin Console
feature: Installation
exl-id: f9edacae-79e0-408c-ac37-bbe67c185f2d
source-git-commit: 1a274c83814f4d729053bb36548ee544b973dff5
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 34%

---

# Configuration d’Adobe Admin Console {#adobe-admin-console-setup}

La première étape de l’utilisation de [!DNL Marketo Measure] est de créer et de se connecter à votre Adobe Admin Console configuré. Si vous n’avez pas reçu le courrier électronique contenant les instructions de connexion, contactez votre [!DNL Marketo Measure] Responsable de compte.

## Configurer votre Adobe Admin Console et votre fournisseur d’identité {#set-up-your-adobe-admin-console-and-identity-provider}

En tant que produit dans Adobe Suite, [!DNL Marketo Measure] utilise toutes les fonctionnalités de Adobe Admin Console pour Identity Management. Vous trouverez plus de ressources [ici](https://helpx.adobe.com/fr/enterprise/using/admin-console.html).

Il est recommandé de consulter les ressources, les bonnes pratiques et les options disponibles pour [Identity Management](https://helpx.adobe.com/enterprise/using/set-up-identity.html).

Pour obtenir des conseils sur la configuration d’Identity Management dans Adobe Admin Console, contactez votre [!DNL Marketo Measure] Responsable de compte.

Pour faciliter l’authentification et l’autorisation des utilisateurs avec votre [!DNL Marketo Measure] , les étapes suivantes sont requises dans Adobe Admin Console :

**Configurer la fiche produit de [!DNL Marketo Measure]**

Lors de l’accès à Adobe Admin Console, le [!DNL Marketo Measure] Instances de produit présentes dans la section Aperçu .

![](assets/adobe-admin-console-setup-1.png)

Cliquez sur le bouton [!DNL Marketo Measure] La carte de produit vous montre tous vos [!DNL Marketo Measure] instances. Par défaut, chaque instance [!DNL Marketo Measure] possède son propre profil, précédé du préfixe « [!DNL Marketo Measure] ». Tous les administrateurs, administratrices, utilisateurs ou utilisatrices ajoutés à ce profil ou à tout autre profil de cette instance pourront se connecter à [!DNL Marketo Measure].

![](assets/adobe-admin-console-setup-2.png)

Aucune action n’est requise pour créer un profil dans la variable [!DNL Marketo Measure] Instance(s) de produit.

Pour commencer à ajouter des utilisateurs pouvant accéder à [!DNL Marketo Measure], reportez-vous au [Ajouter [!DNL Marketo Measure] Administrateurs et [!DNL Marketo Measure] Utilisateurs](#adding-marketo-measure-admins-and-marketo-measure-users) ci-dessous.

## Ajouter des administratreurs et administratrices [!DNL Marketo Measure] et des utilisateurs et utilisatrices [!DNL Marketo Measure] {#adding-marketo-measure-admins-and-marketo-measure-users}

L’étape suivante consiste à accorder l’accès à l’application [!DNL Marketo Measure] en ajoutant des utilisateurs et des utilisatrices. Vous pouvez le faire dans le répertoire des administrateurs et administratrices et des utilisateurs et utilisatrices de la fiche produit de [!DNL Marketo Measure].

| Type d’utilisateur ou d’utilisatrice | Description |
|---|---|
| Administrateurs et administratrices | Il s’agit des administrateurs, administratrices, utilisateurs et utilisatrices expérimentés de l’application [!DNL Marketo Measure] avec la capacité de mettre à jour et gérer les options de configuration spécifiques de [!DNL Marketo Measure]. |
| Utilisateurs et utilisatrices | il s’agit des utilisateurs standard de la variable [!DNL Marketo Measure] Application avec autorisations en lecture seule dans la variable [!DNL Marketo Measure] application |

Lors de l’ajout d’un utilisateur à son groupe respectif, les [Type d’identité répertorié](https://helpx.adobe.com/enterprise/using/set-up-identity.html).

>[!NOTE]
>
>Être [!DNL Marketo Measure] administrateur (dans [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"}), un utilisateur doit être ajouté en tant qu’utilisateur _et_ d’un administrateur à n’importe quel [!DNL Marketo Measure] profil de produit dans la variable [!DNL Marketo Measure] carte produit.

**Se connecter à[!DNL Marketo Measure]**

Une fois qu’un utilisateur a été ajouté à un profil de produit, il peut accéder à son [!DNL Marketo Measure] en choisissant la variable **Connexion avec Adobe ID** à [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"}.

![](assets/adobe-admin-console-setup-3.png)
