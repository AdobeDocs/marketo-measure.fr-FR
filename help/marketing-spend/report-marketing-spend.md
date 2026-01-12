---
description: Rapport sur les dépenses marketing
title: Rapport sur les dépenses marketing
exl-id: 46b0f81c-acd1-47a5-bf75-6a943edb9009
feature: Reporting, Spend Management
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 2%

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

Étant donné que les dépenses de marketing n’étaient historiquement libellées qu’en une seule devise (USD), une petite quantité de travail est nécessaire pour remplacer toutes les dépenses déclarées par la nouvelle devise. Même si les devises multiples ne sont pas activées sur votre compte, si vous avez une devise d’entreprise unique autre que le dollar américain, vous devez effectuer cette migration.

1. Télécharger le fichier de dépenses actuel au format CSV
1. La colonne devise affiche « [!UICONTROL USD] » comme devise supposée. Vous pouvez remplacer manuellement toutes les occurrences de « [!UICONTROL USD] » ou utiliser Rechercher+Remplacer pour remplacer toutes les instances de « [!UICONTROL USD] » par la devise de votre entreprise, telle que « [!UICONTROL EUR] » ou « [!UICONTROL GBP] ».
1. Enregistrez le fichier, puis chargez-le à nouveau dans [!DNL Marketo Measure].
1. Tous vos coûts déclarés s’afficheront désormais dans la nouvelle devise.
