---
unique-page-id: 37356027
description: "[!DNL Marketo Measure] Intégration CRM sans package - [!DNL Marketo Measure]"
title: "[!DNL Marketo Measure] Intégration CRM sans package"
exl-id: a4f31d82-63ec-4bb2-bc8b-d3495e61af4f
feature: Integration
source-git-commit: 1a274c83814f4d729053bb36548ee544b973dff5
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 1%

---

# Intégration CRM de [!DNL Marketo Measure] sans package {#marketo-measure-crm-packageless-integration}

Toutes les équipes marketing ne souhaitent pas (ou n’ont pas accès) exécuter les rapports marketing en dehors du CRM, que ce soit en raison d’un accès limité, de la propriété CRM, d’un temps de valorisation plus long ou d’implications juridiques. En suivant le chemin de [!DNL Marketo Measure] Démarrage rapide vous permet de mettre en oeuvre et d’exécuter efficacement. [!DNL Marketo Measure] avec le moins de confiance possible dans le CRM.

## Standard [!DNL Marketo Measure] Installation {#standard-marketo-measure-installation}

Par le biais du standard [!DNL Marketo Measure] installation, vous devez installer une [!DNL Salesforce] Module ou [!DNL Microsoft Dynamics] Solution gérée. L’installation comprend des objets/entités personnalisés et des champs personnalisés ajoutés au CRM qui [!DNL Marketo Measure] peut alors écrire des données sur .

Une intégration sans package avec [!DNL Marketo Measure] est destiné aux clients qui ne souhaitent pas créer d’objets/d’entités personnalisés ou de champs personnalisés dans votre CRM. Il s’agit également d’une bonne option pour les clients qui utilisent un Data Warehouse externe.

## Permissions {#permissions}

A [!DNL Marketo Measure] L&#39;intégration des packages CRM nécessite toujours l&#39;accès aux objets CRM standard tels que Leads et Contacts. Il est recommandé qu’un utilisateur dédié serve d’utilisateur connecté, car il dispose des privilèges d’accès aux données appropriés.

Pour vous assurer que toutes les données sont correctement extraites de votre CRM, nous avons besoin des paramètres de sécurité et d’accessibilité suivants : Afficher toutes les données pour le profil de l’utilisateur dédié. Ce jeu d’autorisations donne [!DNL Marketo Measure] l’accès nécessaire pour télécharger des données à partir d’objets standard. Ce jeu d’autorisations se trouve au niveau du profil.

## Configuration de votre fournisseur d’identité et de vos connexions aux données {#setup-your-identity-provider-and-data-connections}

Dans les guides ci-dessous, ignorez les étapes d’installation du [!DNL Salesforce] package ou [!DNL Microsoft Dynamics] Solution gérée et suivez uniquement les instructions d’autorisation et d’intégration.

[!DNL Salesforce] clic sur les clients [here](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-salesforce-package-installation-and-set-up.md).

[!DNL Microsoft Dynamics] clic sur les clients [here](/help/marketo-measure-and-dynamics/getting-started-with-marketo-measure-and-dynamics/microsoft-dynamics-crm-installation-guide.md).

Une fois ces étapes terminées, l’intégration doit être opérationnelle. Si vous rencontrez des problèmes, contactez votre [!DNL Marketo Measure] représentant ou [Prise en charge de Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.

>[!NOTE]
>
>Si vous commencez par la variable [!DNL Marketo Measure] Intégration de package CRM que vous pouvez installer ultérieurement le package Salesforce ou la solution gérée Microsoft Dynamics.
