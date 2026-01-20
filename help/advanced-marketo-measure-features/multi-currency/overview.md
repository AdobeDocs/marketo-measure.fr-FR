---
unique-page-id: 27656735
description: Présentation - [!DNL Marketo Measure]
title: Vue d’ensemble
exl-id: 2076521c-b579-457c-ab1c-263b1da4dd89
feature: Multi-Currency
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 1%

---

# Vue d’ensemble {#overview}

Aujourd’hui, l’application [!DNL Marketo Measure] ne prend en charge qu’une seule devise (supposée être le dollar américain), alors que nous savons et savons que nous avons des clients dans le monde entier qui doivent créer des rapports sur leurs propres devises d’entreprise et d’utilisateur. Cette fonctionnalité permet aux utilisateurs de basculer entre les mêmes devises que celles utilisées dans leur CRM lors de l’affichage des dépenses déclarées ou des recettes de vente en [!DNL Marketo Measure].

## Disponibilité {#availability}

Niveau 2 et supérieur.

## Exigences {#requirements}

[!DNL Marketo Measure] extraira automatiquement le paramètre de devise du CRM du client. Une configuration manuelle dans [!DNL Marketo Measure] pour correspondre au CRM n’est plus nécessaire. Le paramètre de devise se trouve dans la page « Général » sous « CRM ».

En [!DNL Salesforce], le client doit avoir activé « Activer plusieurs devises ». Le client peut également sélectionner « Oui, je souhaite activer la gestion avancée des devises ».

Dans Dynamics, le client peut définir des taux de change statiques dans ses paramètres pour plusieurs devises. Il n&#39;existe aucun concept de « gestion avancée des devises » dans Dynamics.

## Conditions {#terms}

| **Terme** | Description |
|---|---|
| **Devise avancée** | La gestion avancée des devises et les devises multiples sont activées pour le client, ce qui signifie qu&#39;il peut avoir des taux de conversion différents pour différentes périodes. |
| **Devise de l’entreprise** | Il s’agit des différentes devises répertoriées et déclarées par une organisation dans le CRM, toutes avec des taux de conversion. [!DNL Marketo Measure] importera ces valeurs et mettra ces devises à la disposition des utilisateurs au sein de notre produit. |
| **Paramètre régional de devise** | Devise unique utilisée pour une organisation, définie sur la page Informations sur l’entreprise. |
| **Devise locale (ou devise de l’utilisateur)** | Devise définie pour un seul utilisateur sur le profil utilisateur, afin qu’il puisse afficher n’importe quel montant dans sa propre devise locale. L’organisation devra déclarer et configurer la devise avant qu’un utilisateur puisse sélectionner sa devise locale. |
| **Monnaie unique** | Utilisé pour les clients qui n’utilisent pas plusieurs devises dans le CRM, mais dont l’organisation s’exécute dans une autre devise, afin d’avoir un « paramètre régional de devise ». Il s’agit toujours d’une devise unique pour l’organisation, mais sans conversion. |
| **Devise simple** | Plusieurs devises est activée pour le client, mais il dispose d’un taux de conversion statique par devise. |
