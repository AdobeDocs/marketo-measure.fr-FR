---
unique-page-id: 18874771
description: Utilisation du chargeur de données à mettre à jour [!DNL Marketo Measure] Champ de montant personnalisé - [!DNL Marketo Measure] - Documentation du produit
title: Utilisation du chargeur de données pour mettre à jour le champ Montant personnalisé de Marketo Measure
exl-id: 55e91ac4-a835-48e0-a6ce-1d85b32aeac0
feature: Custom Revenue Amount
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 9%

---

# Utilisation d’un chargeur de données pour mettre à jour un champ de montant personnalisé dans[!DNL Marketo Measure] {#using-data-loader-to-update-marketo-measure-custom-amount-field}

[!DNL Marketo Measure] recommande d’utiliser Data Loader comme option pratique pour mettre à jour les valeurs d’opportunité lors de l’utilisation d’un champ de recettes personnalisé (nous utilisons le champ Montant prêt à l’emploi) dans [!DNL Marketo Measure]. Le chargeur de données est préférable à l’utilisation de [!DNL Marketo Measure] mettre à jour le script, car les utilisateurs doivent désactiver toutes les règles de validation Salesforce pendant que la fonction [!DNL Marketo Measure] s’exécute.

## Utilisation d’un chargeur de données pour mettre à jour un champ de montant personnalisé dans[!DNL Marketo Measure]{#using-data-loader-to-update-marketo-measure-custom-amount-field-1}

1. Créez une feuille Excel avec :

   * ID opportunité
   * Champ Montant de l&#39;opportunité personnalisée (votre champ de chiffre d&#39;affaires préféré)
   * [!DNL Marketo Measure] Champ Montant de l&#39;opportunité

1. Copiez et collez les valeurs du champ des recettes de votre choix dans le champ [!UICONTROL [!DNL Marketo Measure] Montant de l’opportunité] champ . Mettez ensuite à jour ces opérations à l’aide du fichier .csv .

**_Vous pouvez également accéder à Salesforce et utiliser une vue de liste personnalisée pour modifier en masse toutes les opportunités..._**

1. Créez une vue Liste personnalisée pour toutes les opportunités.
1. Ajouter un filtre pour le champ des recettes préférées n’est pas vide _et_ [!UICONTROL Marketo] Le champ Mesurer le montant de l’opportunité est vide.
1. Cliquez sur **[!UICONTROL Modification en masse]**, mais ne changez rien.
1. Cliquez sur **[!UICONTROL Enregistrer]**. Cela déclenche le workflow pour renseigner la variable [!DNL Marketo Measure] Champs Montant de l’opportunité avec le champ Recettes logicielles.
