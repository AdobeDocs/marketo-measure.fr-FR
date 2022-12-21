---
unique-page-id: 18874734
description: Bonnes pratiques de fusion de pistes - [!DNL Marketo Measure] - Documentation du produit
title: Bonnes pratiques de fusion de pistes
exl-id: d9293ed7-a794-4e52-a269-20a7fb36ce50
source-git-commit: f13e55f009f33140ff36523212ed8b9ed5449a4d
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---

# Bonnes pratiques de fusion de pistes {#best-practices-for-merging-leads}

Lorsqu’il s’agit de fusionner des pistes dans [!DNL Salesforce], il est toujours préférable d’être prudent pour s’assurer qu’aucune donnée n’est perdue.

À titre de référence, voici la répartition des [Comment fusionner les pistes](https://help.salesforce.com/HTViewHelpDoc?id=leads_merge.htm&amp;language=en_US) de [!DNL Salesforce] Assistance.

Où [!DNL Marketo Measure] apparaît lorsqu’il est temps de sélectionner des champs qui seront renseignés sur l’enregistrement fusionné. Lors de la sélection de l’enregistrement de Principal, validez la variable [!DNL Marketo Measure] sont sélectionnés pour être reportés vers le nouvel enregistrement.

S’il existe plusieurs enregistrements avec [!DNL Marketo Measure] , assurez-vous que les champs sélectionnés de l’enregistrement de Principal pour le prospect qui a été créé en premier. Additional [!DNL Marketo Measure] Les données seront présentes dans la section Statistiques . Assurez-vous également que l’adresse électronique de la piste trackée est l’adresse électronique conservée, car elle nous permettra de continuer à mettre à jour cette piste avec toute nouvelle donnée d’attribution.

A partir de là, vous devriez être libre de fusionner les Leads et [!DNL Marketo Measure] les données seront transférées vers le nouvel enregistrement.

Si vous avez des questions, n’hésitez pas à contacter votre responsable du succès client ou [Prise en charge de Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target=&quot;_blank&quot;}.

![](assets/1.jpg)
