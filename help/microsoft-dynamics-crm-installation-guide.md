---
description: Guide détaillé pour l’installation et la configuration du package Marketo Measure dans Microsoft Dynamics CRM
title: Guide d’installation CRM [!DNL Microsoft Dynamics]
exl-id: bc422c98-60bb-49ea-9bd1-c4149ae628b1
feature: Installation, Microsoft Dynamics
hidefromtoc: true
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '979'
ht-degree: 96%

---

# Guide d’installation CRM [!DNL Microsoft Dynamics] {#microsoft-dynamics-crm-installation-guide}

>[!NOTE]
>
>Des instructions spécifiant « [!DNL Marketo Measure] » peuvent s’afficher dans la documentation tandis que votre CRM mentionne « Bizible ». Nous nous efforçons de mettre cela à jour. Notre nouvelle identité de marque (rebranding) sera bientôt répercutée dans votre CRM.

## Versions prises en charge {#supported-versions}

[!DNL Marketo Measure] prend en charge les versions suivantes de [!DNL Microsoft Dynamics CRM] :

* [!DNL Microsoft Dynamics 2016] (en ligne et On-Premise)
* [!DNL Microsoft Dynamics 365] (en ligne et On-Premise)

Pour la connexion et l’authentification, [!DNL Marketo Measure] prend en charge les versions suivantes d’Active Directory Federated Services (ADFS) :

* ADFS 4.0 - [!DNL Windows Server 2016]
* ADFS 5.0 - [!DNL Windows Server 2019]

## Installer la solution gérée {#install-the-managed-solution}

[Téléchargez et installez](assets/marketo-measure-dynamics-extension.zip) le fichier ZIP dans Dynamics CRM.

**[!UICONTROL Paramètres]** > **[!UICONTROL Personnalisations]** > **[!UICONTROL Solutions]** > **[!UICONTROL Importer]** (bouton) > **[!UICONTROL Choisir un fichier]**.

>[!NOTE]
>
>Les deux captures d’écran suivantes peuvent être légèrement différentes de votre affichage, car elles ont été prises lors d’une mise à niveau de la solution.

## Créer un utilisateur ou une utilisatrice [!DNL Marketo Measure] {#creating-a-marketo-measure-user}

Il est recommandé de créer un profil d’utilisateur ou d’utilisatrice Marketo Measure dédié en tant qu’« utilisateur ou utilisatrice d’application » dans Dynamics pour exporter et importer des données afin d’éviter tout problème avec d’autres utilisateurs et utilisatrices dans votre CRM. Prenez note du nom d’utilisateur ou d’utilisatrice et du mot de passe, ainsi que de l’URL du point d’entrée, car ils sont utilisés lors de la création du compte [!DNL Marketo Measure].

## Rôles de sécurité {#security-roles}

Si votre organisation utilise des rôles de sécurité Dynamics, assurez-vous que le profil d’utilisateur ou d’utilisatrice connecté ou que le profil [!DNL Marketo Measure] dédié dispose d’autorisations de lecture/écriture suffisantes pour les entités requises.

Les rôles de sécurité se trouvent ici : **[!UICONTROL Paramètres]** > **[!UICONTROL Sécurité]** > **[!UICONTROL Rôles de sécurité]**.

Pour les entités personnalisées [!DNL Marketo Measure], des autorisations complètes sont requises pour toutes nos entités.

Des autorisations de création de campagne (« Créer ») sont également requises, en plus des autorisations en lecture/écriture pour les entités standard.

>[!NOTE]
>
>Les utilisateurs et utilisatrices qui clôturent des opportunités doivent également disposer d’une autorisation complète.

Pour les entités Dynamics standard, reportez-vous au document de schéma Dynamics [!DNL Marketo Measure]. À un niveau élevé, [!DNL Marketo Measure] lit certaines entités pour recueillir les données appropriées et écrire dans des champs personnalisés installés avec la solution gérée. Les enregistrements standard ne sont pas créés et les champs standard ne sont pas mis à jour.

## Inclure des points de contact (touchpoints) dans les dispositions des pages : {#include-touchpoints-on-page-layouts}

1. Pour chaque entité, accédez à l’éditeur de formulaire. Vous pouvez y accéder dans **[!UICONTROL Paramètres]** > **[!UICONTROL Personnalisations]** > **[!UICONTROL Personnaliser le système]** > `[Entity]` > **[!UICONTROL Formulaires]**. Vous pouvez également y accéder dans les paramètres lorsque vous consultez un enregistrement.

   * Voici les entités à configurer : Compte, Opportunité, Contact, Prospect et Campagne.

   * Pour configurer les campagnes, vous devez activer l’option « Synchronisation des campagnes » dans **[!UICONTROL CRM]** > **[!UICONTROL Campagnes]**.

1. Dispositions des pages : ajoutez d’abord une tuile « [!UICONTROL Une colonne] » dans la section où vous voulez que les points de contact (touchpoints) soient placés. Dans cette nouvelle colonne, il est nécessaire d’ajouter une sous-grille à chaque formulaire dans vos entités Compte, Opportunité, Contact et Prospect.

1. Sélectionnez l’objet (Buyer Attribution Touchpoints ou Buyer Touchpoints) qui doit être rendu dans la sous-grille, en fonction de la relation de l’objet. Vous pouvez également modifier les colonnes qui s’affichent en cliquant sur le bouton Modifier. La disposition par défaut est définie par la solution gérée.

   Sous-grille Buyer Attribution Touchpoint - Comptes, opportunités et contact
Sous-grille Buyer Touchpoint - Leads et contacts

1. Une fois que vous avez terminé de mettre à jour le formulaire, publiez et enregistrez vos modifications.

## Éléments à prendre en compte relatifs au schéma {#schema-related-considerations}

### Recettes

[!DNL Marketo Measure] renvoie par défaut au champ standard Revenus réels. Si vous n’utilisez pas ce champ, expliquez à votre personne responsable de l’ingénierie des solutions ou à celle responsable du succès comment vous communiquez vos revenus, car un workflow personnalisé sera nécessaire.

### Date de fermeture

[!DNL Marketo Measure] pointe par défaut vers le champ Date de clôture réelle. Si vous n’utilisez pas ce champ ou si vous utilisez également le champ Date de clôture estimée, expliquez votre méthode à votre personnes responsable de l’ingénierie des solutions ou à celle responsable du succès. Un workflow personnalisé peut être nécessaire pour prendre en compte les deux champs.

## Configurer vos connexions et vos fournisseurs de données {#configuring-your-connections-and-data-providers}

Lorsque la connexion à l’application [!DNL Marketo Measure] est effective et que vous êtes utilisateur ou utilisatrice d’Adobe Admin Console, vous devez configurer vos différentes connexions de données.

**CRM en tant que fournisseur de données**

1. Dans votre compte [!DNL Marketo Measure], cliquez sur le menu déroulant **[!UICONTROL Mon compte]** et sélectionnez **[!UICONTROL Paramètres]**.

1. Sous [!UICONTROL Intégrations] dans le menu de navigation de gauche, cliquez sur **[!UICONTROL Connexions]**.

1. Cliquez sur le bouton **[!UICONTROL Configurer une nouvelle connexion CRM]**.

1. À côté de [!UICONTROL CRM Microsoft Dynamics], cliquez sur le bouton **[!UICONTROL Connecter]**.

1. Sélectionnez [!UICONTROL Informations d’identification] ou [!UICONTROL OAuth].

   >[!NOTE]
   >
   >Pour plus d’informations sur OAuth, consultez [cet article](/help/oauth-with-azure-active-directory-for-dynamics-crm.md). Pour toute question sur le processus, contactez votre personne représentante de compte [!DNL Marketo Measure].

1. Dans cet exemple, nous avons choisi Informations d’identification. Saisissez vos informations d’identification et cliquez sur **[!UICONTROL Suivant]**.

Après la connexion, les détails de votre connexion Dynamics s’affichent dans la liste des connexions CRM/MAP.

**Connexions de compte publicitaire**

Pour connecter vos comptes publicitaires à [!DNL Marketo Measure], commencez par consulter l’onglet [!UICONTROL Connexions] dans l’application [!DNL Marketo Measure].

1. Suivez les étapes 1 et 2 de la section _CRM en tant que fournisseur de données_ ci-dessus.

1. Cliquez sur le bouton **[!UICONTROL Configurer une nouvelle connexion CRM]**.

1. Sélectionnez la plateforme de votre choix.

Javascript **[!DNL Marketo Measure]**

Pour que [!DNL Marketo Measure] puisse suivre vos activités sur le web, plusieurs étapes de configuration sont nécessaires.

1. Cliquez sur le menu déroulant **[!UICONTROL Mon compte]** et sélectionnez **[!UICONTROL Configuration du compte]**.

1. Saisissez votre numéro de téléphone. Pour Site web, entrez votre domaine racine principal qui est utilisé pour le suivi de [!DNL Marketo Measure] sur votre site web. Cliquez sur **[!UICONTROL Enregistrer]** lorsque vous avez terminé.

   >[!NOTE]
   >
   >Pour ajouter plusieurs domaines racine, contactez votre personne représentante de compte [!DNL Marketo Measure].

1. Le code [[!DNL Marketo Measure] JavaScript](/help/marketo-measure-tracking/adding-marketo-measure-script.md) doit ensuite être placé sur l’ensemble du site et des pages de destination. Nous vous recommandons de coder le script en dur dans l’en-tête de vos pages de destination ou de l’ajouter par le biais d’un système de gestion des balises, tel que [Google Tag Manager](/help/marketo-measure-tracking/adding-marketo-measure-script-via-google-tag-manager.md).

   >[!NOTE]
   >
   >Par défaut, [!DNL Marketo Measure] exporte 200 enregistrements par crédit d’API chaque fois qu’une tâche envoie des données à votre CRM. Pour la majeure partie de la clientèle, cela permet d’obtenir un équilibre optimal entre les crédits d’API consommés par [!DNL Marketo Measure] et les exigences en matière de ressources du processeur sur le CRM. Toutefois, pour la clientèle disposant de configurations CRM complexes, comme les workflows et les triggers, une taille de lot réduite peut se révéler utile pour améliorer les performances CRM. À cette fin, [!DNL Marketo Measure] permet à la clientèle de configurer la taille du lot d’export CRM. Ce paramètre est disponible à la page Paramètres > CRM > Général de l’application web [!DNL Marketo Measure]. Il est ainsi possible de choisir entre des tailles de lot de 200 (par défaut), 100, 50 ou 25.
   >
   >Lorsque vous modifiez ce paramètre, gardez à l’esprit que des tailles de lots plus petites consomment davantage de crédits d’API de votre CRM. Il est conseillé de réduire la taille des lots uniquement en cas de temporisation du processeur ou d’une charge élevée de ce dernier dans votre CRM.

   >[!NOTE]
   >
   >Lorsque vous désactivez l’export de données de Marketo Measure vers Dynamics, aucune donnée existante n’est supprimée. Pour obtenir de l’aide sur la suppression des données existantes, contactez l’assistance de Dynamics.

   >[!MORELIKETHIS]
   >
   >[Notifications d’erreur](/help/configuration-and-setup/error-notifications.md){target="_blank"}
