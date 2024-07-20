---
unique-page-id: 37356027
description: "[!DNL Marketo Measure] Intégration sans package CRM - [!DNL Marketo Measure]"
title: "[!DNL Marketo Measure] Intégration sans package CRM"
exl-id: a4f31d82-63ec-4bb2-bc8b-d3495e61af4f
feature: Integration
source-git-commit: 1a274c83814f4d729053bb36548ee544b973dff5
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 1%

---

# Intégration CRM de [!DNL Marketo Measure] sans package {#marketo-measure-crm-packageless-integration}

Toutes les équipes marketing ne souhaitent pas (ou n’ont pas accès) exécuter les rapports marketing en dehors du CRM, que ce soit en raison d’un accès limité, de la propriété CRM, d’un temps de valorisation plus long ou d’implications juridiques. En suivant le chemin de [!DNL Marketo Measure] Quick Start, vous pouvez implémenter et exécuter efficacement [!DNL Marketo Measure] en ne vous reposant que très peu sur le CRM.

## Installation standard [!DNL Marketo Measure] {#standard-marketo-measure-installation}

Par le biais de l&#39;installation standard de [!DNL Marketo Measure], vous devez installer un package [!DNL Salesforce] ou une solution [!DNL Microsoft Dynamics] gérée. L’installation comprend des objets/entités personnalisés et des champs personnalisés ajoutés au CRM dans lequel [!DNL Marketo Measure] peut ensuite écrire des données.

Une intégration sans package avec [!DNL Marketo Measure] est destinée aux clients qui ne souhaitent pas créer d’objets/d’entités personnalisés ou de champs personnalisés dans votre CRM. Il s’agit également d’une bonne option pour les clients qui utilisent un Data Warehouse externe.

## Permissions {#permissions}

Une intégration sans package CRM [!DNL Marketo Measure] nécessite toujours l&#39;accès aux objets CRM standard tels que Leads et Contacts. Il est recommandé qu’un utilisateur dédié serve d’utilisateur connecté, car il dispose des privilèges d’accès aux données appropriés.

Pour vous assurer que toutes les données sont correctement extraites de votre CRM, nous avons besoin des paramètres de sécurité et d’accessibilité suivants : Afficher toutes les données pour le profil de l’utilisateur dédié. Ce jeu d’autorisations donne à [!DNL Marketo Measure] l’accès nécessaire pour télécharger des données à partir d’objets standard. Ce jeu d’autorisations se trouve au niveau du profil.

## Configuration de votre fournisseur d’identité et de vos connexions aux données {#setup-your-identity-provider-and-data-connections}

Dans les guides ci-dessous, ignorez les étapes d’installation du package [!DNL Salesforce] ou de la solution gérée [!DNL Microsoft Dynamics] et suivez uniquement les instructions d’autorisation et d’intégration.

[!DNL Salesforce] clients cliquent sur [ici](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-salesforce-package-installation-and-set-up.md).

[!DNL Microsoft Dynamics] clients cliquent sur [ici](/help/marketo-measure-and-dynamics/getting-started-with-marketo-measure-and-dynamics/microsoft-dynamics-crm-installation-guide.md).

Une fois ces étapes terminées, l’intégration doit être opérationnelle. Si vous rencontrez des problèmes, contactez votre représentant [!DNL Marketo Measure] ou le [support Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.

>[!NOTE]
>
>Si vous commencez avec l’intégration [!DNL Marketo Measure] sans package CRM, vous pouvez installer le package Salesforce ou la solution gérée Microsoft Dynamics ultérieurement.
