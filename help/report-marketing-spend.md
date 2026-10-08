---
description: Conseils sur les dépenses de marketing des rapports pour les utilisateurs de Marketo Measure
title: Rapport sur les dépenses marketing
exl-id: 46b0f81c-acd1-47a5-bf75-6a943edb9009
feature: Reporting, Spend Management
product_v2:
  - id: e6fc4016-a972-4f36-8c30-a6a5f82ad0c8
    internal-label: Marketo Measure
feature_v2:
  - id: d24e0b99-7796-5c7d-831d-d71a1d725f01
    internal-label: Reporting
  - id: e3b4b95f-0bb9-5cb3-a479-9dcb943dca3f
    internal-label: Spend Management
source-git-commit: 940fee4abd0e09b6bf513b5e7526d3c242bd31c7
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 1%
---
# Rapport sur les dépenses marketing {#report-marketing-spend}

## Tableau des dépenses marketing {#marketing-spend-table}

Le tableau Dépenses marketing contient une nouvelle colonne pour afficher la devise de chaque ligne de canal, de sous-canal et de campagne. Cette nouvelle colonne s’affiche pour tous les clients, même si l’option Plusieurs devises n’est pas activée.

Le tableau contient un mélange de différentes devises. Reportez-vous au tableau de bord des dépenses marketing pour obtenir la somme de tous les canaux, sous-canaux ou campagnes dans une seule devise.

## Coûts de chargement {#upload-costs}

Lorsqu’un utilisateur télécharge le fichier de coûts, le fichier contient également une nouvelle colonne avec la devise de chaque ligne. Les seules devises acceptables sont celles qui ont été définies et stockées dans le CRM. Vous devez connaître le code abrégé de 3 lettres de votre devise (USD, CAD, JPY, EUR) et si un fichier est chargé avec une devise non reconnue, le chargement du fichier échoue.

## Coûts des intégrations publicitaires {#costs-from-ad-integrations}

Lorsque [!DNL Marketo Measure] importe le coût à partir de plateformes connectées telles qu&#39;AdWords, Bing, Facebook ou Doubleclick, nous utilisons également la devise déclarée. La devise s’affiche à côté du canal, du sous-canal et de la campagne lorsqu’elle s’affiche dans le tableau Dépenses marketing .

Si la devise du fournisseur de publicités ne correspond pas à une devise extraite du CRM, une erreur « Devises mixtes » peut s’afficher dans [!DNL Marketo Measure Discover]. Pour corriger ce problème, l’administrateur CRM doit ajouter une conversion pour la devise inconnue.

## Migrer vers les dépenses marketing converties {#migrate-to-converted-marketing-spend}

Comme les dépenses marketing n’ont été historiquement effectuées que dans une seule devise (USD), une petite quantité de travail est nécessaire pour convertir toutes les dépenses déclarées dans la nouvelle devise. Même si les devises multiples ne sont pas activées sur votre compte, si vous avez une devise d’entreprise autre qu’USD, vous devez effectuer cette migration.

1. Télécharger le fichier de dépenses actuel au format CSV
1. La colonne devise affiche «  » comme devise supposée. Vous pouvez remplacer manuellement toutes les occurrences de «  » ou utiliser Rechercher+Remplacer pour remplacer toutes les instances « [!UICONTROL USD] » par la devise de votre entreprise, telle que « [!UICONTROL EUR] » ou « [!UICONTROL GBP] ».
1. Enregistrez le fichier, puis chargez-le à nouveau dans [!DNL Marketo Measure].
1. Tous vos coûts déclarés s’afficheront désormais dans la nouvelle devise.
