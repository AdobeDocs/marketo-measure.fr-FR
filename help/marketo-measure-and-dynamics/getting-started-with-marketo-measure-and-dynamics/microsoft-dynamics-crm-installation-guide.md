---
unique-page-id: 18874763
description: "[!DNL Microsoft Dynamics] Guide d’installation CRM - Marketo Measure - Documentation du produit"
title: "[!DNL Microsoft Dynamics] Guide d'installation CRM"
exl-id: bc422c98-60bb-49ea-9bd1-c4149ae628b1
feature: Installation, Microsoft Dynamics
source-git-commit: 1a274c83814f4d729053bb36548ee544b973dff5
workflow-type: tm+mt
source-wordcount: '954'
ht-degree: 9%

---

# [!DNL Microsoft Dynamics] Guide d&#39;installation CRM {#microsoft-dynamics-crm-installation-guide}

>[!NOTE]
>
>Vous pouvez voir des instructions spécifiant &quot;[!DNL Marketo Measure]&quot; dans la documentation, mais consultez toujours &quot;Bizible&quot; dans votre CRM. Nous nous efforçons de mettre à jour cette version. Notre nouvelle identité (rebranding) sera bientôt répercutée dans votre CRM.

## Versions prises en charge {#supported-versions}

[!DNL Marketo Measure] prend en charge les éléments suivants : [!DNL Microsoft Dynamics CRM] versions :

* [!DNL Microsoft Dynamics 2016] (En ligne et On-Premise)
* [!DNL Microsoft Dynamics 365] (En ligne et On-Premise)

Pour la connexion et l&#39;authentification, [!DNL Marketo Measure] prend en charge les versions suivantes d’Active Directory Federated Services (ADFS) :

* ADFS 4.0 - [!DNL Windows Server 2016]
* ADFS 5.0 - [!DNL Windows Server 2019]

## Installation de la solution gérée {#install-the-managed-solution}

[Télécharger et installer](assets/marketo-measure-dynamics-extension.zip) le fichier zip dans Dynamics CRM.

**[!UICONTROL Paramètres]** > **[!UICONTROL Personnalisations]** > **[!UICONTROL Solutions]** > **[!UICONTROL Importer]** (bouton) > **[!UICONTROL Choisir un fichier]**.

![](assets/1.png)

>[!NOTE]
>
>Les deux captures d’écran suivantes peuvent légèrement différer de la vôtre, car elles ont été réalisées lors d’une mise à niveau de solution.

![](assets/2.png)

![](assets/3.png)

## Création d’un [!DNL Marketo Measure] Utilisateur {#creating-a-marketo-measure-user}

Il est recommandé de créer un utilisateur Marketo Measure dédié en tant qu’&quot;utilisateur de l’application&quot; dans Dynamics pour exporter et importer des données via afin d’éviter tout problème avec d’autres utilisateurs dans votre CRM. Prenez note du nom d’utilisateur et du mot de passe, ainsi que de l’URL du point de terminaison, car ils sont utilisés lors de la création de la variable [!DNL Marketo Measure] compte .

## Rôles de sécurité {#security-roles}

Si votre organisation utilise des rôles de sécurité Dynamics, assurez-vous que l’utilisateur connecté ou le [!DNL Marketo Measure] L’utilisateur dispose des autorisations de lecture/écriture suffisantes pour les entités requises.

Les rôles de sécurité se trouvent ici : **[!UICONTROL Paramètres]** > **[!UICONTROL Sécurité]** > **[!UICONTROL Rôles de sécurité]**.

Pour [!DNL Marketo Measure] entités personnalisées, nous avons besoin d’autorisations complètes sur toutes nos entités.

>[!NOTE]
>
>Les utilisateurs qui ferment des opportunités ont également besoin d’une autorisation complète.

![](assets/4.png)

Pour les entités Dynamics standard, voir [!DNL Marketo Measure] Document de schéma Dynamics. à un niveau élevé, [!DNL Marketo Measure] lit dans certaines entités pour rassembler les données appropriées et écrire dans des champs personnalisés installés avec la solution gérée. Les enregistrements standard ne sont pas créés et les champs standard ne sont pas mis à jour.

## Inclure les points de contact sur les mises en page : {#include-touchpoints-on-page-layouts}

1. Pour chaque entité, accédez à l’éditeur de formulaire. Vous pouvez le trouver sous **[!UICONTROL Paramètres]** > **[!UICONTROL Personnalisations]** > **[!UICONTROL Personnalisation du système]** > `[Entity]` > **[!UICONTROL Forms]**. Vous pouvez également le trouver dans les paramètres pendant que vous affichez un enregistrement.

   * Les entités à configurer : Compte, Opportunité, Contact, Piste et Campagne.

   * Pour configurer les campagnes, vous devez activer l’option &quot;Synchronisation des campagnes&quot; dans **[!UICONTROL CRM]** > **[!UICONTROL Campagnes]**.

   ![](assets/5.png)

1. Mise en page : commencez par ajouter un[!UICONTROL Une colonne]&quot; dans la section que vous souhaitez que les points de contact soient actifs. Dans cette nouvelle colonne, une sous-grille doit être ajoutée à chaque formulaire dans vos entités Compte, Opportunité, Contact et Prospère.

   ![](assets/6.png)

   ![](assets/7.png)

1. Sélectionnez l’objet (points de contact d’attribution de l’achat ou points de contact de l’achat) qui doit être rendu dans la sous-grille, qui dépend de la relation de l’objet. Vous pouvez éventuellement modifier les colonnes affichées en cliquant sur le bouton Modifier . La mise en page par défaut est définie par la solution gérée.

   Sous-grille Point de contact d’attribution de l’achat - Comptes, opportunités et contacts\
   Sous-grille Point de contact de l’acheteur - Pistes et contacts

   ![](assets/8.png)

1. Une fois la mise à jour du formulaire terminée, publiez et enregistrez vos modifications.

## Considérations relatives aux schémas {#schema-related-considerations}

**Recettes**

[!DNL Marketo Measure] pointe par défaut vers le champ Recettes réelles standard. Si vous n’utilisez pas cette méthode, expliquez comment vous signalez les recettes à votre ingénieur de solutions ou à votre gestionnaire de succès en tant que processus personnalisé nécessaire.

**Date de fermeture**

[!DNL Marketo Measure] pointe vers le champ Date de fermeture réelle prêt à l’emploi. Si vous n’utilisez pas ce paramètre ou si vous utilisez également le champ Date de fermeture estimée, expliquez votre processus à votre ingénieur de solutions ou à votre responsable de succès. Un workflow personnalisé peut être nécessaire pour tenir compte des deux champs.

## Configuration des connexions et des fournisseurs de données {#configuring-your-connections-and-data-providers}

Après vous être connecté à la variable [!DNL Marketo Measure] et qui ont été configurés en tant qu’utilisateur dans Adobe Admin Console, l’étape suivante consiste à configurer vos différentes connexions de données.

**CRM en tant que fournisseur de données**

1. Dans votre [!DNL Marketo Measure] , cliquez sur **[!UICONTROL Mon compte]** et sélectionnez **[!UICONTROL Paramètres]**.

   ![](assets/microsoft-dynamics-crm-installation-guide-16.png)

1. Sous [!UICONTROL Intégrations] dans le volet de navigation de gauche, cliquez sur **[!UICONTROL Connexions]**.

   ![](assets/microsoft-dynamics-crm-installation-guide-17.png)

1. Cliquez sur le bouton **[!UICONTROL Configurer une nouvelle connexion CRM]** bouton .

   ![](assets/microsoft-dynamics-crm-installation-guide-18.png)

1. Suivant [!UICONTROL Microsoft Dynamics CRM], cliquez sur le **[!UICONTROL Connexion]** bouton .

   ![](assets/microsoft-dynamics-crm-installation-guide-19.png)

1. Sélectionner [!UICONTROL Informations d’identification] ou [!UICONTROL OAuth].

   ![](assets/microsoft-dynamics-crm-installation-guide-20.png)

   >[!NOTE]
   >
   >Pour plus d’informations sur OAuth, consultez [cet article](/help/marketo-measure-and-dynamics/getting-started-with-marketo-measure-and-dynamics/oauth-with-azure-active-directory-for-dynamics-crm.md). Si vous avez des questions sur le processus, contactez votre [!DNL Marketo Measure] Gestionnaire de compte.

1. Dans cet exemple, nous avons choisi Credentials (Informations d’identification). Saisissez vos informations d’identification, puis cliquez sur **[!UICONTROL Suivant]**.

Une fois la connexion établie, les détails de votre connexion Dynamics s’affichent dans la liste Connexions CRM/MAP .

**Connexions à un compte publicitaire**

Pour connecter vos comptes publicitaires à [!DNL Marketo Measure], commencez par consulter le [!UICONTROL Connexions] dans la [!DNL Marketo Measure] application.

1. Suivez les étapes 1 et 2 ci-dessus. _CRM en tant que fournisseur de données_ .

1. Cliquez sur le bouton **[!UICONTROL Configurer une nouvelle connexion CRM]** bouton .

   ![](assets/microsoft-dynamics-crm-installation-guide-21.png)

1. Sélectionnez la plateforme souhaitée.

   ![](assets/microsoft-dynamics-crm-installation-guide-22.png)

**[!DNL Marketo Measure]Javascript**

Pour [!DNL Marketo Measure] pour effectuer le suivi de vos activités web, plusieurs étapes sont nécessaires pour la configuration.

1. Cliquez sur le bouton **[!UICONTROL Mon compte]** et sélectionnez **[!UICONTROL Configuration du compte]**.

   ![](assets/microsoft-dynamics-crm-installation-guide-23.png)

1. Saisissez votre numéro de téléphone. Pour le site Web, saisissez le domaine racine principal utilisé pour [!DNL Marketo Measure] suivi sur votre site web. Cliquez sur **[!UICONTROL Enregistrer]** une fois terminé.

   ![](assets/microsoft-dynamics-crm-installation-guide-24.png)

   >[!NOTE]
   >
   >Pour ajouter plusieurs domaines racine, contactez votre [!DNL Marketo Measure] Responsable de compte.

1. La variable [[!DNL Marketo Measure] JavaScript](/help/marketo-measure-tracking/setting-up-tracking/adding-marketo-measure-script.md) doit ensuite être placé sur l’ensemble du site et des landing pages. Nous vous recommandons de coder en dur le script dans l’en-tête de vos landing pages ou de l’ajouter via un système Tag Management tel que [Gestionnaire de balises de Google](/help/marketo-measure-tracking/setting-up-tracking/adding-marketo-measure-script-via-google-tag-manager.md).

   >[!NOTE]
   >
   >Par défaut, [!DNL Marketo Measure] exporte 200 enregistrements par crédit d’API chaque fois qu’une tâche envoie des données à votre CRM. Pour la majeure partie de la clientèle, cela permet d’obtenir un équilibre optimal entre les crédits d’API consommés par [!DNL Marketo Measure] et les exigences en matière de ressources du processeur sur le CRM. Toutefois, pour la clientèle disposant de configurations CRM complexes, comme les workflows et les triggers, une taille de lot réduite peut se révéler utile pour améliorer les performances CRM. À cette fin, [!DNL Marketo Measure] permet à la clientèle de configurer la taille du lot d’export CRM. Ce paramètre est disponible sur la page Paramètres > CRM > Général de la [!DNL Marketo Measure] l’application web et les clients peuvent choisir entre des tailles de lot de 200 (par défaut), 100, 50 ou 25.
   >
   >Lorsque vous modifiez ce paramètre, gardez à l’esprit que les tailles de lots plus petites consomment plus de crédits d’API de votre gestion de la relation client. Il est conseillé de réduire la taille du lot uniquement si vous rencontrez un délai d’expiration du processeur ou une charge élevée du processeur dans votre CRM.

   >[!NOTE]
   >
   >Lorsque vous désactivez Marketo Measure pour exporter des données vers Dynamics, cela ne supprime aucune donnée existante. Pour obtenir de l’aide sur la suppression des données existantes, contactez le support Dynamics.

   >[!MORELIKETHIS]
   >
   >[Notifications d’erreur](/help/configuration-and-setup/getting-started-with-marketo-measure/error-notifications.md){target="_blank"}
