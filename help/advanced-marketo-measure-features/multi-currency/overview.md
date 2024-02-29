---
unique-page-id: 27656735
description: Présentation - [!DNL Marketo Measure]
title: Vue d’ensemble
exl-id: 2076521c-b579-457c-ab1c-263b1da4dd89
feature: Multi-Currency
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 1%

---

# Vue d’ensemble {#overview}

Aujourd’hui, la [!DNL Marketo Measure] L’application ne prend en charge qu’une seule devise (en supposant qu’il s’agisse d’un dollar américain), alors que nous savons et sommes conscients que, dans le monde entier, des clients doivent déclarer leurs propres devises d’entreprise et d’utilisateur. Cette fonctionnalité permet aux utilisateurs de basculer entre les mêmes devises utilisées dans leur CRM lors de l’affichage des dépenses signalées ou des recettes de ventes dans [!DNL Marketo Measure].

## Disponibilité {#availability}

Niveau 2 et supérieur.

## Exigences {#requirements}

[!DNL Marketo Measure] extrait automatiquement le paramètre de devise du CRM du client. Configuration manuelle dans [!DNL Marketo Measure] pour correspondre au CRM n’est plus nécessaire. Le paramètre de devise se trouve dans la page &quot;Général&quot; sous &quot;CRM&quot;.

Dans [!DNL Salesforce], &quot;Activer plusieurs devises&quot; doit être activé pour le client. En option, le client peut également sélectionner &quot;Oui, je souhaite activer la gestion avancée des devises&quot;.

Dans Dynamics, le client peut définir des taux de change statiques dans ses Paramètres pour plusieurs devises. Il n’existe aucun concept de &quot;gestion avancée des devises&quot; dans Dynamics.

## Conditions {#terms}

| **Terme** | Description |
|---|---|
| **Devise avancée** | La gestion avancée des devises et les devises multiples sont activées pour le client, ce qui signifie qu’il peut y avoir différents taux de conversion pour différentes périodes. |
| **Devise de l’entreprise** | Il s’agit des différentes devises répertoriées et déclarées par une organisation dans le CRM, toutes avec des taux de conversion. [!DNL Marketo Measure] importera ces valeurs et mettra ces devises à la disposition des utilisateurs dans notre produit. |
| **Paramètres régionaux de devise** | La devise unique utilisée pour une organisation, définie sur la page Informations de la société . |
| **Devise locale (ou devise utilisateur)** | Devise définie pour un utilisateur unique sur le profil utilisateur, de sorte qu’il puisse afficher n’importe quel montant dans sa propre devise locale. L’organisation devra déclarer et configurer la devise avant qu’un utilisateur ne puisse sélectionner sa devise locale. |
| **Monétaire unique** | Utilisé pour les clients qui n’utilisent pas plusieurs devises dans le CRM, mais que leur organisation s’exécute dans une devise différente, ils disposent donc d’un &quot;paramètre régional de devise&quot;. Il s’agit toujours d’une devise unique pour l’organisation, mais sans conversion. |
| **Devise simple** | Plusieurs devises sont activées pour le client, mais leur taux de conversion par devise est statique. |
