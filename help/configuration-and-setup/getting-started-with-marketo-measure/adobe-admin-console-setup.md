---
description: Configuration de Adobe Admin Console - Marketo Measure - Documentation du produit
title: Configuration de Adobe Admin Console
feature: Installation
source-git-commit: 68eb5bf83d589c9161490b1772551ed46a9ce444
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 2%

---

# Configuration de Adobe Admin Console {#adobe-admin-console-setup}

La première étape de l’utilisation de [!DNL Marketo Measure] est de créer et de se connecter à votre Adobe Admin Console configuré. Si vous n’avez pas encore reçu l’e-mail contenant des instructions de connexion, contactez votre [!DNL Marketo Measure] Responsable de compte.

## Configuration de votre Adobe Admin Console et de votre fournisseur d’identité {#set-up-your-adobe-admin-console-and-identity-provider}

En tant que produit dans Adobe Suite, [!DNL Marketo Measure] tire parti de toutes les fonctionnalités de Adobe Admin Console pour Identity Management. Plus de ressources peuvent être [se trouve ici](https://helpx.adobe.com/fr/enterprise/using/admin-console.html).

Nous vous recommandons de passer en revue toutes les ressources, bonnes pratiques et options disponibles pour . [Identity Management](https://helpx.adobe.com/enterprise/using/set-up-identity.html).

Pour obtenir des conseils sur la configuration d’Identity Management dans Adobe Admin Console et les consulter, contactez votre [!DNL Marketo Measure] Responsable de compte.

Pour faciliter l’authentification et l’autorisation des utilisateurs avec votre [!DNL Marketo Measure] instances, les étapes suivantes sont requises dans Adobe Admin Console :

**Configuration de la variable [!DNL Marketo Measure] Product Card**

Lors de l’accès à Adobe Admin Console, le [!DNL Marketo Measure] Instance(s) de produit(s) présente(s) dans la section Aperçu .

![](assets/adobe-admin-console-setup-1.png)

Cliquez sur le bouton [!DNL Marketo Measure] La carte de produit vous montrera toutes vos [!DNL Marketo Measure] instances. Par défaut, chaque [!DNL Marketo Measure] L’instance possède son propre profil, précédé du préfixe &quot;[!DNL Marketo Measure]&#39;. Tous les administrateurs ou utilisateurs ajoutés à ce profil ou à tout autre profil de cette instance pourront se connecter à [!DNL Marketo Measure].

![](assets/adobe-admin-console-setup-2.png)

Aucune action n’est requise pour créer un profil dans la variable [!DNL Marketo Measure] Instance(s) de produit.

Pour commencer à ajouter des utilisateurs pouvant accéder à [!DNL Marketo Measure], reportez-vous au [Ajouter [!DNL Marketo Measure] Administrateurs et [!DNL Marketo Measure] Utilisateurs](#adding-marketo-measure-admins-and-marketo-measure-users) ci-dessous.

## Ajouter [!DNL Marketo Measure] Administrateurs et [!DNL Marketo Measure] Utilisateurs {#adding-marketo-measure-admins-and-marketo-measure-users}

L’étape suivante consiste à accorder l’accès à [!DNL Marketo Measure] en ajoutant des utilisateurs. Vous pouvez le faire dans le répertoire des administrateurs et des utilisateurs de la variable [!DNL Marketo Measure] carte produit.

| Type d&#39;utilisateur | Description |
|---|---|
| Administrateurs | il s’agit des administrateurs et des utilisateurs experts de la fonction [!DNL Marketo Measure] Application pleine capacité à mettre à jour et à gérer [!DNL Marketo Measure]Options de configuration spécifiques |
| Utilisateurs | il s’agit des utilisateurs standard de la variable [!DNL Marketo Measure] Application avec des autorisations de lecture seule dans [!DNL Marketo Measure] application |

Lors de l’ajout d’un utilisateur à son groupe respectif, les [Type d’identité répertorié](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/set-up-identity.ug.html).

>[!NOTE]
>
>Pour être un [!DNL Marketo Measure] administrateur (dans [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"}), un utilisateur doit être ajouté en tant qu’utilisateur _et_ d’un administrateur à n’importe quel [!DNL Marketo Measure] profil de produit dans la variable [!DNL Marketo Measure] carte produit.

**Connexion à[!DNL Marketo Measure]**

Une fois qu’un utilisateur a été ajouté à un profil de produit, il peut accéder à son [!DNL Marketo Measure] en choisissant la ou les instances **Connexion avec Adobe ID** à [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"}.

![](assets/adobe-admin-console-setup-3.png)

