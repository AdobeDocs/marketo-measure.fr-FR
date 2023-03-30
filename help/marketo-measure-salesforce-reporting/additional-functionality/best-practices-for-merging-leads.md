---
unique-page-id: 18874734
description: Bonnes pratiques de fusion de pistes - [!DNL Marketo Measure] - Documentation du produit
title: Bonnes pratiques de fusion des prospects
exl-id: d9293ed7-a794-4e52-a269-20a7fb36ce50
source-git-commit: 51397a02872035fef41d308c1f855bcaecc29c4e
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 4%

---

# Bonnes pratiques de fusion des prospects {#best-practices-for-merging-leads}

Lorsqu’il s’agit de fusionner des pistes dans [!DNL Salesforce], il est toujours préférable d’être prudent pour s’assurer qu’aucune donnée n’est perdue.

À titre de référence, voici la répartition des [Comment fusionner les pistes](https://help.salesforce.com/HTViewHelpDoc?id=leads_merge.htm&amp;language=en_US) de [!DNL Salesforce] Assistance.

Où [!DNL Marketo Measure] apparaît lorsqu’il est temps de sélectionner des champs qui seront renseignés sur l’enregistrement fusionné. Lors de la sélection de l’enregistrement de Principal, validez la variable [!DNL Marketo Measure] sont sélectionnés pour être reportés vers le nouvel enregistrement.

S’il existe plusieurs enregistrements avec [!DNL Marketo Measure] , assurez-vous que les champs sélectionnés de l’enregistrement de Principal pour le prospect qui a été créé en premier. Additional [!DNL Marketo Measure] Les données seront présentes dans la section Statistiques . Assurez-vous également que l’adresse électronique de la piste trackée est l’adresse électronique conservée, car elle nous permettra de continuer à mettre à jour cette piste avec toute nouvelle donnée d’attribution.

A partir de là, vous devriez être libre de fusionner les Leads et [!DNL Marketo Measure] les données seront transférées vers le nouvel enregistrement.

Si vous avez des questions, n’hésitez pas à contacter l’équipe de compte d’Adobe (votre gestionnaire de compte) ou [Prise en charge de Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.

![](assets/1.jpg)
