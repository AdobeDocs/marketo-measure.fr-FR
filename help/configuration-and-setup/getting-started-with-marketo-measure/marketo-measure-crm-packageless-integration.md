---
description: Intégration sans package [!DNL Marketo Measure] CRM -  [!DNL Marketo Measure]
title: Intégration CRM de [!DNL Marketo Measure] sans package
exl-id: a4f31d82-63ec-4bb2-bc8b-d3495e61af4f
feature: Integration
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 2%

---


# Intégration CRM de [!DNL Marketo Measure] sans package {#marketo-measure-crm-packageless-integration}

Toutes les équipes marketing ne souhaitent pas (ou n’ont pas accès) à exécuter les rapports marketing à partir du CRM, que ce soit en raison d’un accès limité, de la propriété du CRM, d’un délai de valorisation plus long ou d’implications juridiques. Le fait de suivre le chemin [!DNL Marketo Measure] démarrage rapide vous permet d’implémenter et d’exécuter efficacement des [!DNL Marketo Measure] avec le moins de dépendance possible vis-à-vis du CRM.

## Installation de [!DNL Marketo Measure] standard {#standard-marketo-measure-installation}

Par le biais de l’installation [!DNL Marketo Measure] standard, vous devez installer un package [!DNL Salesforce] ou une solution gérée par [!DNL Microsoft Dynamics]. L’installation comprend des objets/entités et des champs personnalisés qui sont ajoutés au CRM dans lequel [!DNL Marketo Measure] pouvez ensuite écrire des données.

Une intégration sans package à [!DNL Marketo Measure] est destinée aux clients qui ne souhaitent pas créer d’objets/entités ou de champs personnalisés dans votre CRM. Il s’agit également d’une bonne option pour les clients qui utilisent un Data Warehouse externe.

## Autorisations {#permissions}

Une intégration CRM sans package [!DNL Marketo Measure] nécessite toujours l’accès aux objets CRM standard tels que les leads et les contacts. Il est recommandé qu’un utilisateur dédié serve d’utilisateur connecté, car il dispose des privilèges d’accès aux données appropriés.

Pour nous assurer que toutes les données sont correctement extraites de votre CRM, nous avons besoin des paramètres de sécurité et d’accessibilité suivants : Afficher toutes les données pour le profil de l’utilisateur dédié. Ce jeu d’autorisations [!DNL Marketo Measure] donne l’accès nécessaire pour télécharger des données à partir d’objets standard. Ce jeu d’autorisations se trouve au niveau du profil.

## Configurer votre fournisseur d’identité et les connexions aux données {#setup-your-identity-provider-and-data-connections}

Dans les guides ci-dessous, ignorez les étapes pour installer le package [!DNL Salesforce] ou [!DNL Microsoft Dynamics] solution gérée et suivez uniquement les autorisations et les instructions d’intégration.

[!DNL Salesforce] clients cliquent [ici](/help/configuration-and-setup/marketo-measure-and-salesforce/install-set-up.md).

[!DNL Microsoft Dynamics] clients cliquent [ici](/help/marketo-measure-and-dynamics/microsoft-dynamics-crm-installation-guide.md).

Une fois ces étapes terminées, l’intégration doit être opérationnelle. Si vous rencontrez des problèmes, contactez votre représentant [!DNL Marketo Measure] ou l’assistance Marketo [](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.

>[!NOTE]
>Si vous commencez avec l’intégration sans package [!DNL Marketo Measure] CRM, vous pourrez installer le package Salesforce ou la solution gérée Microsoft Dynamics ultérieurement.
