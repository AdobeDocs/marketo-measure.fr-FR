---
unique-page-id: 27656737
description: Signaler les dépenses marketing - [!DNL Marketo Measure]
title: Rapport sur les dépenses marketing
exl-id: 46b0f81c-acd1-47a5-bf75-6a943edb9009
feature: Reporting, Spend Management
source-git-commit: 1a274c83814f4d729053bb36548ee544b973dff5
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 1%

---

# Rapport sur les dépenses marketing {#report-marketing-spend}

## Tableau des dépenses marketing {#marketing-spend-table}

Le tableau Dépenses marketing contient une nouvelle colonne pour afficher la devise de chaque canal, sous-canal et ligne Campagne. Cette nouvelle colonne s’affiche pour tous les clients, même si l’option Plusieurs devises n’est pas activée.

Le tableau contient un mélange de différentes devises. Consultez le tableau de bord des dépenses marketing pour obtenir la somme de tous les canaux, sous-canaux ou campagnes dans une seule devise.

## Chargement des coûts {#upload-costs}

Lorsqu’un utilisateur télécharge le fichier de coûts, le fichier contient également une nouvelle colonne avec la devise de chaque ligne. Les seules devises acceptables sont celles qui ont été définies et stockées dans le CRM. Vous devez connaître le code abrégé à 3 lettres de votre devise (USD, CAD, JPY, EUR). Si un fichier est chargé avec une devise non reconnue, le téléchargement du fichier échoue.

## Coûts des intégrations publicitaires {#costs-from-ad-integrations}

When [!DNL Marketo Measure] importe le coût des plateformes connectées telles que AdWords, Bing, Facebook ou Doubleclick ; nous utilisons également la devise rapportée. La devise s’affiche à côté du canal, du sous-canal et de la campagne lorsqu’elle est affichée dans le tableau Dépenses marketing .

Si la devise du fournisseur de publicités ne correspond pas à une devise extraite du CRM, une erreur &quot;Devises mixtes&quot; peut s’afficher dans la variable [!DNL Marketo Measure Discover]. Pour corriger ce problème, l’administrateur CRM doit ajouter une conversion pour la devise inconnue.

## Migration vers les dépenses marketing converties {#migrate-to-converted-marketing-spend}

Dans la mesure où les dépenses marketing n’ont historiquement été effectuées que dans une seule devise (USD), il reste peu de travail à faire pour remplacer toutes les dépenses signalées par la nouvelle devise. Même si plusieurs devises ne sont pas activées pour votre compte, si vous disposez d’une seule devise d’entreprise autre que le dollar américain, vous devez effectuer cette migration.

1. Télécharger le fichier de dépenses actuel au format CSV
1. La colonne de devise affiche &quot;[!UICONTROL USD]&quot; comme devise utilisée. Vous pouvez remplacer manuellement toutes les occurrences de &quot;[!UICONTROL USD]&quot; ou utilisez Rechercher+Remplacer pour modifier tous les &quot;[!UICONTROL USD]&quot; à votre propre devise d’entreprise, telle que &quot;[!UICONTROL EUR]&quot; ou &quot;[!UICONTROL GBP]&quot;.
1. Enregistrez le fichier, puis rechargez-le dans [!DNL Marketo Measure].
1. Tous les coûts signalés s’afficheront désormais comme la nouvelle devise.
