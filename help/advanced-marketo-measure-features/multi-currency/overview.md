---
unique-page-id: 27656735
description: Présentation - [!DNL Marketo Measure] - Documentation du produit
title: APERÇU
exl-id: 2076521c-b579-457c-ab1c-263b1da4dd89
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 2%

---

# APERÇU {#overview}

Aujourd’hui, la [!DNL Marketo Measure] L’application ne prend en charge qu’une seule devise (en supposant qu’il s’agisse d’un dollar américain), alors que nous savons et sommes conscients que des clients dans le monde entier doivent déclarer leurs devises d’entreprise et d’utilisateur. Cette fonctionnalité permet aux utilisateurs de basculer entre différentes devises lorsqu’ils examinent les dépenses signalées ou les recettes de vente.

## Disponibilité {#availability}

Niveau 2 et supérieur.

## Exigences {#requirements}

Dans [!DNL Salesforce], &quot;Activer plusieurs devises&quot; doit être activé pour le client. Le client peut également sélectionner &quot;Oui, je souhaite activer la gestion avancée des devises&quot;.

Dans Dynamics, le client peut définir des taux de change statiques dans ses Paramètres pour plusieurs devises. Il n’existe aucun concept de &quot;gestion avancée des devises&quot; dans Dynamics.

## Conditions {#terms}

| **Terme** | Description |
|---|---|
| **Devise avancée** | La gestion avancée des devises et les devises multiples sont activées pour le client, ce qui signifie qu’il peut y avoir différents taux de conversion pour différentes périodes. |
| **Devise d’entreprise** | Il s’agit des différentes devises répertoriées et déclarées par une organisation dans le CRM, toutes avec des taux de conversion. [!DNL Marketo Measure] importera ces valeurs et mettra ces devises à la disposition des utilisateurs dans notre produit. |
| **Paramètres régionaux de devise** | La devise unique utilisée pour une organisation, définie sur la page Informations de la société . |
| **Devise locale (ou devise utilisateur)** | Devise définie pour un utilisateur unique sur le profil utilisateur, de sorte qu’il puisse afficher n’importe quel montant dans sa propre devise locale. L’organisation devra déclarer et configurer la devise avant qu’un utilisateur ne puisse sélectionner sa devise locale. |
| **Monétaire unique** | Utilisé pour les clients qui n’utilisent pas plusieurs devises dans le CRM, mais que leur organisation s’exécute dans une devise différente, ils disposent donc d’un &quot;paramètre régional de devise&quot;. Il s’agit toujours d’une devise unique pour l’organisation, mais sans conversion. |
| **Devise simple** | Plusieurs devises sont activées pour le client, mais leur taux de conversion par devise est statique. |
