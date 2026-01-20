---
unique-page-id: 18874771
description: Utilisation du chargeur de données pour mettre à jour  [!DNL Marketo Measure]  champ de montant personnalisé - [!DNL Marketo Measure]
title: Utilisation du chargeur de données pour mettre à jour le champ du montant personnalisé Marketo Measure
exl-id: 55e91ac4-a835-48e0-a6ce-1d85b32aeac0
feature: Custom Revenue Amount
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 2%

---

# Utilisation du chargeur de données pour mettre à jour [!DNL Marketo Measure] champ de montant personnalisé {#using-data-loader-to-update-marketo-measure-custom-amount-field}

[!DNL Marketo Measure] recommande d’utiliser le chargeur de données comme option pratique pour mettre à jour les valeurs d’opportunité lors de l’utilisation d’un champ de chiffre d’affaires personnalisé (nous utilisons le champ Montant prêt à l’emploi) dans [!DNL Marketo Measure]. Le chargeur de données est préférable à l’utilisation du script de mise à jour [!DNL Marketo Measure], car celui-ci exige des utilisateurs qu’ils désactivent toutes les règles de validation Salesforce pendant l’exécution du script [!DNL Marketo Measure].

## Utilisation du chargeur de données pour mettre à jour [!DNL Marketo Measure] champ de montant personnalisé{#using-data-loader-to-update-marketo-measure-custom-amount-field-1}

1. Créez une feuille Excel avec :

   * ID d’opportunité
   * Champ Personnalisé du montant de l’opportunité (champ de chiffre d’affaires préféré)
   * Champ [!DNL Marketo Measure] le montant de l’opportunité

1. Copiez et collez les valeurs de votre champ de chiffre d’affaires préféré dans le champ [!UICONTROL [!DNL Marketo Measure] le montant de l’opportunité &#x200B;] . Mettez ensuite à jour ces opportunités à l’aide du fichier .csv.

**_Vous pouvez également accéder à Salesforce et utiliser une vue de liste personnalisée pour modifier en masse toutes les opportunités..._**

1. Créer une vue Liste personnalisée pour toutes les opportunités.
1. Le champ Ajouter un filtre pour le chiffre d’affaires préféré n’est pas vide _et_ champ [!UICONTROL Marketo] Mesurer le montant de l’opportunité est vide.
1. Cliquez sur **[!UICONTROL Modification en masse]**, mais ne modifiez rien.
1. Cliquez sur **[!UICONTROL Enregistrer]**. Cela déclenchera le workflow pour renseigner les champs Montant de l’opportunité [!DNL Marketo Measure] avec le champ Chiffre d’affaires logiciel .
