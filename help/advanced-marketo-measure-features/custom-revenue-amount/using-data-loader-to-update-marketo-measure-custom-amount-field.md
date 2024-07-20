---
unique-page-id: 18874771
description: Utilisation du chargeur de données pour mettre à jour [!DNL Marketo Measure] Champ Quantité Personnalisé - [!DNL Marketo Measure]
title: Utilisation du chargeur de données pour mettre à jour le champ Montant personnalisé de Marketo Measure
exl-id: 55e91ac4-a835-48e0-a6ce-1d85b32aeac0
feature: Custom Revenue Amount
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 2%

---

# Utilisation du chargeur de données pour mettre à jour le champ Montant personnalisé [!DNL Marketo Measure] {#using-data-loader-to-update-marketo-measure-custom-amount-field}

[!DNL Marketo Measure] recommande d’utiliser Data Loader comme option pratique pour mettre à jour les valeurs d’opportunité lors de l’utilisation d’un champ de recettes personnalisé (nous utilisons le champ Montant prêt à l’emploi) dans [!DNL Marketo Measure]. Le chargeur de données est préférable à l’utilisation du script de mise à jour [!DNL Marketo Measure], car le script oblige les utilisateurs à désactiver toutes les règles de validation Salesforce pendant l’exécution du script [!DNL Marketo Measure].

## Utilisation du chargeur de données pour mettre à jour le champ Montant personnalisé [!DNL Marketo Measure]{#using-data-loader-to-update-marketo-measure-custom-amount-field-1}

1. Créez une feuille Excel avec :

   * ID opportunité
   * Champ Montant de l&#39;opportunité personnalisée (votre champ de chiffre d&#39;affaires préféré)
   * [!DNL Marketo Measure] Champ Montant de l’opportunité

1. Copiez et collez les valeurs de votre champ de recettes préféré dans le champ [!UICONTROL [!DNL Marketo Measure] Montant de l’opportunité] . Mettez ensuite à jour ces opérations à l’aide du fichier .csv .

**_Vous pouvez également accéder à Salesforce et utiliser une vue de liste personnalisée pour modifier en masse toutes les opportunités.._**

1. Créez une vue Liste personnalisée pour toutes les opportunités.
1. Ajoutez un filtre pour le champ de recettes préféré qui n’est pas vide _et le champ_ [!UICONTROL Marketo] Mesurer le montant de l’opportunité est vide.
1. Cliquez sur **[!UICONTROL Édition en masse]**, mais ne modifiez rien.
1. Cliquez sur **[!UICONTROL Enregistrer]**. Cela déclenchera le workflow pour renseigner les champs [!DNL Marketo Measure] Montant de l’opportunité avec le champ Recettes du logiciel .
